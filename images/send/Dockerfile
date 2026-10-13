# Send (https://gitlab.com/timvisee/send) reconstruit sur un Node maintenu.
#
# L'image amont tourne sur node:16.13-alpine3.13, sans correctifs de sécurité depuis 2023, et
# Send n'a plus de release depuis juillet 2025. Le serveur n'utilise que des dépendances en
# JavaScript pur : il tourne ici sur Node 24. Seul le build du front (webpack 4.38, qui exige
# l'OpenSSL de Node 16) reste en Node 16, dans une étape jetable jamais exposée.

# renovate: datasource=gitlab-tags depName=timvisee/send
ARG SEND_VERSION=v3.4.27

# Source au tag. Le .git reste : le build du front y lit la version (git-rev-sync).
FROM node:24.21.0-alpine@sha256:ebfe2f90462722a7a4de65e91990e97fe0d401c70e0e762c5b53302f905ec1c1 AS source
ARG SEND_VERSION
RUN apk add --no-cache git && \
    git clone --depth 1 --branch "${SEND_VERSION}" https://gitlab.com/timvisee/send.git /src

# Front : webpack 4.38 ne démarre pas au-delà de Node 16 (ERR_OSSL_EVP_UNSUPPORTED).
FROM node:16.20.2-alpine@sha256:a1f9d027912b58a7c75be7716c97cfbc6d3099f3a97ed84aa490be9dee20e787 AS front
RUN apk add --no-cache git
WORKDIR /src
COPY --from=source /src .
RUN PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true npm ci && npm run build

# Dépendances de production, installées par le Node qui les exécutera. git : configstore est
# tiré d'un dépôt GitHub.
FROM node:24.21.0-alpine@sha256:ebfe2f90462722a7a4de65e91990e97fe0d401c70e0e762c5b53302f905ec1c1 AS deps
RUN apk add --no-cache git
WORKDIR /app
COPY --from=source /src/package.json /src/package-lock.json ./
RUN npm ci --omit=dev && npm cache clean --force

FROM node:24.21.0-alpine@sha256:ebfe2f90462722a7a4de65e91990e97fe0d401c70e0e762c5b53302f905ec1c1
WORKDIR /app
COPY --from=deps /app/node_modules node_modules
COPY --from=source /src/package.json ./
COPY --from=source /src/app app
COPY --from=source /src/common common
COPY --from=source /src/public/locales public/locales
COPY --from=source /src/server server
COPY --from=front /src/dist dist
RUN ln -s dist/version.json version.json

# Utilisateur node de l'image (uid 1000), celui que platform/transfert/send.yaml déclare.
USER node
ENV NODE_ENV=production PORT=1443
EXPOSE 1443
CMD ["node", "server/bin/prod.js"]

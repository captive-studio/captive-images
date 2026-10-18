FROM ghcr.io/captive-studio/node-ci:24.22.0@sha256:2bb3afc1bc50472f50bfc8fbc638f2add3ccb4891ce48e653512c2769538018f

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs : Renovate la repère
# grâce au commentaire ci-dessous (customManagers de preset.json).
# renovate: datasource=npm depName=playwright
ARG PLAYWRIGHT_VERSION=1.64.1
RUN npx --yes playwright@${PLAYWRIGHT_VERSION} install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

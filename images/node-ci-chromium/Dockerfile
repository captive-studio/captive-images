FROM ghcr.io/captive-studio/node-ci:24.22.1@sha256:4ba3b88b99c44ce8ed2b8fcc771b59fe14c98d1679a1c4fcf0ca9b9da62bc3c4

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs : Renovate la repère
# grâce au commentaire ci-dessous (customManagers de preset.json).
# renovate: datasource=npm depName=playwright
ARG PLAYWRIGHT_VERSION=1.64.1
RUN npx --yes playwright@${PLAYWRIGHT_VERSION} install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

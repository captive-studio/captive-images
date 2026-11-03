FROM ghcr.io/captive-studio/node-ci:26.13.0@sha256:1350c8740b42b5273651a0a38da5d344ef5dec8f78ed8b8934aed2287828f2f2

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs : Renovate la repère
# grâce au commentaire ci-dessous (customManagers de preset.json).
# renovate: datasource=npm depName=playwright
ARG PLAYWRIGHT_VERSION=1.64.1
RUN npx --yes playwright@${PLAYWRIGHT_VERSION} install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

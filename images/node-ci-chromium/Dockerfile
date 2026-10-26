FROM ghcr.io/captive-studio/node-ci:24.22.1@sha256:a96b64545a0b1c8f5ce16dd0f1fbef792cf7f33d508f1c5f0ee7306b82b5fd2c

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs : Renovate la repère
# grâce au commentaire ci-dessous (customManagers de preset.json).
# renovate: datasource=npm depName=playwright
ARG PLAYWRIGHT_VERSION=1.64.1
RUN npx --yes playwright@${PLAYWRIGHT_VERSION} install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

FROM ghcr.io/captive-studio/node-ci:24.21.0@sha256:f1af241d301ea062d5750bacf6a192a0940f2d5b7d55c1990343c8aae28206e2

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs (gérée par Renovate).
RUN npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

FROM ghcr.io/captive-studio/node-ci:24.21.0@sha256:a8729ea83ad487616de71c70ce944dc1a2e50ed8f1821c3911ce603f9dcd4cc7

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs (gérée par Renovate).
RUN npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

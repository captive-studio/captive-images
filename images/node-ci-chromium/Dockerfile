FROM ghcr.io/captive-studio/node-ci:24.21.0@sha256:d6ac2a965b406c83cd47ef2595e7354ab44ba134f13d764d7dc314d0a3ec1ae0

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs (gérée par Renovate).
RUN npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

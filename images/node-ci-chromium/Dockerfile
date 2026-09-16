FROM ghcr.io/captive-studio/node-ci:24.21.0@sha256:109345c2c11edde13ef31d909c66991c21a5bc3c54728eeedea60fd0a4579d73

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs (gérée par Renovate).
RUN npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

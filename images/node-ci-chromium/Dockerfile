FROM ghcr.io/captive-studio/node-ci:24.21.0@sha256:57c32db9aa15d15ad9e574b8fee9a68c99ab2f73ce8045e39e16416fad2b8f99

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs (gérée par Renovate).
RUN npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

FROM ghcr.io/captive-studio/node-ci:24.21.0@sha256:313ba37a08d6a83a387df27abca403ea83ccdc30cbdb3c0b122c7eba6ef9f3f4

# Les outils CI sont hérités de node-ci ; ses mises à jour passent par Renovate.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs (gérée par Renovate).
RUN npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

FROM node:24.21.0-bookworm-slim@sha256:2fe369e969550cde8e867afc3fe370b260140cab4a23d467074295b42163d553 AS base

# Socle partagé : les outils CI sont déclarés une seule fois dans l'Aptfile.
COPY images/node-ci/Aptfile /tmp/Aptfile
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile && \
    node --version && npm --version && git --version && curl --version && \
    zstd --version && command -v unzip && command -v ps

# La cible finale conserve le navigateur attendu par les utilisateurs de node-ci.
FROM base AS browser
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Cette version doit suivre celle des projets consommateurs (gérée par Renovate).
RUN npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

FROM node:26.13.0-bookworm-slim@sha256:add5c17c14752c54d2f3d519ec46a3815684d41c33f198bcb09fb998f7dcbf68

# Node ne livre plus corepack depuis la 25 : les projets en ont besoin pour lancer
# le gestionnaire de paquets déclaré par leur champ packageManager.
# renovate: datasource=npm depName=corepack
ARG COREPACK_VERSION=0.36.0

# Socle partagé : les outils CI sont déclarés une seule fois dans l'Aptfile.
COPY images/node-ci/Aptfile /tmp/Aptfile
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    npm install -g corepack@${COREPACK_VERSION} && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile /root/.npm && \
    node --version && npm --version && git --version && curl --version && \
    zstd --version && command -v unzip && command -v ps && \
    corepack --version

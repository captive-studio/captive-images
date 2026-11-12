FROM node:26.13.1-bookworm-slim@sha256:5df79989ed685e09f0a98019db4cebfb22fb9df1a53c0161664a011f7ff6b0f1

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

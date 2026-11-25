FROM node:26.13.1-bookworm-slim@sha256:0042e17d232a87a2cd485be1da7900fca4d10a4ad11b29e9285da1d2e54798c9

# Le runner ARC transmet HTTP(S)_PROXY au conteneur de job, mais pas NODE_USE_ENV_PROXY :
# sans elle, Node 24 ignore le proxy et les actions JavaScript (create-github-app-token)
# refusent de démarrer. Sans proxy, la variable n'a aucun effet.
ENV NODE_USE_ENV_PROXY=1

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

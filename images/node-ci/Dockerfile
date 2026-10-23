FROM node:24.22.1-bookworm-slim@sha256:55fb5f5a527ea2c5c4a95f963e48ef90aa38c7b346054fdc8ee9957a2b55d205

# Socle partagé : les outils CI sont déclarés une seule fois dans l'Aptfile.
COPY images/node-ci/Aptfile /tmp/Aptfile
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile && \
    node --version && npm --version && git --version && curl --version && \
    zstd --version && command -v unzip && command -v ps

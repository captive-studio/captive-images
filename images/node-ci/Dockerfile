FROM node:24.22.1-bookworm-slim@sha256:be8204d4bd327363357f532187b752ff62759c31bedf98e9e18fc08c9cbd605c

# Socle partagé : les outils CI sont déclarés une seule fois dans l'Aptfile.
COPY images/node-ci/Aptfile /tmp/Aptfile
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile && \
    node --version && npm --version && git --version && curl --version && \
    zstd --version && command -v unzip && command -v ps

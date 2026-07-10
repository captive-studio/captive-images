FROM ghcr.io/captive-studio/ruby-ci:4.0.5@sha256:3bfc455e62bce2e63a9c9df2b2f59d46d6dabc65f5656b9b0ef06c448621f296

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

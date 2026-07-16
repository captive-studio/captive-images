FROM ghcr.io/captive-studio/ruby-ci:4.0.5@sha256:55104e5f27b19e9607a66277283b9ff19307f25095e8336861bb1aa2588aa171

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

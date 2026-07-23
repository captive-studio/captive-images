FROM ghcr.io/captive-studio/ruby-ci:4.0.6@sha256:f6cd6935a4a348887f8172b2f3ca1102d9b6940f2fafd6c1c17c6d80319d8804

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

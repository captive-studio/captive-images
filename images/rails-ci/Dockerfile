FROM ghcr.io/captive-studio/ruby-ci:4.0.6@sha256:ec4690a15ef8a1aa23b2c13e7cd3689256a24faece1f20a335b382f1f5797668

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

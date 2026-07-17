FROM ghcr.io/captive-studio/ruby-ci:4.0.6@sha256:5d13098838699256aedf425c65507702a835be24ecd35e22b174af769b5e6af8

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

FROM ghcr.io/captive-studio/ruby-ci:4.0.5@sha256:2bd9bd7943eb97da523dbc5e73e712dfaa168bce7450cbb1437986b86a581c97

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

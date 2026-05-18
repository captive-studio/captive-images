FROM cimg/ruby:4.0.3@sha256:081aa67ffaa2dcc8d60fdc1b8431dc8dcd764248d57068c91a76efe9cccb6ba6

COPY images/ruby-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

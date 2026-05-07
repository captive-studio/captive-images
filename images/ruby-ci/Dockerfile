FROM cimg/ruby:4.0.2@sha256:90f2756f90e5f94884e58a9012755bc6cd7a148e25498d405e02f00e6b500de4

COPY Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

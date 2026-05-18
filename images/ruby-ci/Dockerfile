FROM cimg/ruby:4.0.4@sha256:8830a50a65b28e07042751bf62cc13a8e3ca6a347f9649aeb9676d8f388dfe47

COPY images/ruby-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

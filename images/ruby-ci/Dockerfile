FROM cimg/ruby:4.0.5@sha256:7452096215e3d00bf02fcc871bb6417f126698919fbee52ef114fb53033599ca

COPY images/ruby-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

FROM ghcr.io/captive-studio/ruby-ci:4.0.8@sha256:d7151ee30872700c36c7c5efe620fd3a0d6ad5c633446429fc5c6b4cc596dfa7

COPY images/rails-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

COPY --chown=circleci:circleci \
  images/rails-ci/Gemfile \
  images/rails-ci/Gemfile.lock \
  /tmp/rails-ci-gems/

RUN cd /tmp/rails-ci-gems && \
    bundle config set frozen true && \
    bundle install && \
    brakeman --version && \
    rm -rf /tmp/rails-ci-gems

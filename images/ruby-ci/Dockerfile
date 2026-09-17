FROM cimg/ruby:4.0.7@sha256:7bd5440c2e6afd221a523fe9d3a126a9987cc7c7cc44e6052c154855855dd367

COPY images/ruby-ci/Aptfile /tmp/Aptfile

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

COPY --chown=circleci:circleci \
  images/ruby-ci/Gemfile \
  images/ruby-ci/Gemfile.lock \
  /tmp/ruby-ci-gems/

RUN cd /tmp/ruby-ci-gems && \
    bundle config set frozen true && \
    bundle install && \
    bundler-audit --version && \
    rubocop --version && \
    rm -rf /tmp/ruby-ci-gems

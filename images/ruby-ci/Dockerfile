FROM cimg/ruby:4.0.7@sha256:3c687b1462c8d062cb6db8ef2e28dba6c3c48c6c8d9fda0f727c2000a02d0c2c

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

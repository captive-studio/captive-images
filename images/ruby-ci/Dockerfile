FROM cimg/ruby:4.0.8@sha256:348adefa85a38d5d9e5650bd064209b43f61d4c5bbdb34fc6494b2ba687c10c5

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

FROM cimg/ruby:4.0.10@sha256:26187037bb690946eb920f0091ef19d575e2ea51e1b82fcdd8d4aa70474b3d9c

# Le runner ARC transmet HTTP(S)_PROXY au conteneur de job, mais pas NODE_USE_ENV_PROXY :
# sans elle, Node 24 ignore le proxy et les actions JavaScript (create-github-app-token)
# refusent de démarrer. Sans proxy, la variable n'a aucun effet.
ENV NODE_USE_ENV_PROXY=1

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

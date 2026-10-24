FROM ruby:4.0.8-slim@sha256:55d1710ff7d36fc88ce792c45b5e04145590c29ba220fb5f1e412b90766b19bf

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

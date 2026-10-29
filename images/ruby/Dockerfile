FROM ruby:4.0.9-slim@sha256:32fdd19c0a001077d1711f1afa6d8a0ac9d497c4eac20e47ae7e1c7f7a8c49df

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

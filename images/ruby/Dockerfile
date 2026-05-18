FROM ruby:4.0.3-slim@sha256:327406df0303d3de9d3f6b196c645511edaee360a46681a310d1c738bb9a2ad2

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

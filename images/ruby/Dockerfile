FROM ruby:4.0.4-slim@sha256:2f6614b6d259073d02a4c5ae3b42244fe791efec6536678777c8167cfc26bb79

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

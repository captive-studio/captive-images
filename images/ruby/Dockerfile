FROM ruby:4.0.10-slim@sha256:67fb5dbef860bb2205a3c69799f7f1c4f5b01c943ae089de436bc266ea8c102e

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

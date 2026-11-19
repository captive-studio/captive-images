FROM ruby:4.0.10-slim@sha256:a4b3e62bfe56bd267a3aeacc1b89aea96be919faa0c7d77c6346e2ac14f6c175

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

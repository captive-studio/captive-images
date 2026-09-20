FROM ruby:4.0.7-slim@sha256:d10bdb076bb10d2261773ea20eadf4cdbde3346fc8f8db409856608b2d01b9c9

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

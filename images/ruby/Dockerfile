FROM ruby:4.0.10-slim@sha256:dc488b2df1731a1523a24a845fc38627b3edde052473c4e7bef06ae4d649fd25

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

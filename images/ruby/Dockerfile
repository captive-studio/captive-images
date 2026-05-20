FROM ruby:4.0.4-slim@sha256:f24ee56af9b03cece6e840679fe0d64b22409613a490cf06733d3629e24e4add

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

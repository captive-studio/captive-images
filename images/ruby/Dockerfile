FROM ruby:4.0.7-slim@sha256:6c6b7b8c7d750604178aa60c2fa436890cd17c5695bdbd3213db2e4efbf98eb9

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

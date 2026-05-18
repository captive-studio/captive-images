FROM ruby:4.0.4-slim@sha256:3fc7a33fb84ba3c876ceccafffc4151c6f2cbbb0c4adf9fd4dbe505130988a8a

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

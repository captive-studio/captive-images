FROM ruby:4.0.9-slim@sha256:22cfdec4c490b9e7e4913527a126ddc34bf30cf5432711f70eb1aa4b3ac388a5

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

FROM ruby:4.0.3-slim@sha256:198547d3216e0efe6fb337997f22fa98eef4270b38033a697dad148d9d8b9b0d

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

FROM ruby:4.0-slim

# Install base packages
RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y curl libjemalloc2 libvips libheif1 postgresql-client imagemagick && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives

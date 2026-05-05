FROM ruby:4.0.2-slim

# Install runtime dependencies
RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      # HTTP utilities
      curl \
      # Memory allocator optimization for Ruby
      libjemalloc2 \
      # Image processing libraries
      libvips \
      libheif1 \
      imagemagick \
      # Database client
      postgresql-client \
      # Timezone data for proper time handling
      tzdata && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives

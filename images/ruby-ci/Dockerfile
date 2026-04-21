FROM cimg/ruby:4.0.1@sha256:3d2ef6af1a0b26e03b398cf48ffe54637c319bd0cd1d683321c4e2a42ca7cd1e

RUN sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
      build-essential \
      freetds-bin \
      freetds-dev \
      libheif-dev \
      libjpeg-turbo8-dev \
      libpng-dev \
      libpq-dev \
      libvips-dev \
      netcat-openbsd \
      pkg-config && \
    sudo rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*

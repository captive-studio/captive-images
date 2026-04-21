FROM cimg/ruby:4.0.1

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

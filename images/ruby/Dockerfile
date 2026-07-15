FROM ruby:4.0.5-slim@sha256:42ad5227a4b2758f32563b34b5967e1055e75c80243eef04e6d2572887d1dec4

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

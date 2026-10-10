FROM ruby:4.0.7-slim@sha256:ba6a00593739f9cb66de80ad2e395a93a52a13635867ee32918ba0ec083b1ff6

COPY images/ruby/Aptfile /tmp/Aptfile

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists /var/cache/apt/archives /tmp/Aptfile

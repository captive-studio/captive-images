FROM ghcr.io/falcondev-oss/actions-runner:2.338.1@sha256:6d8e4376dbff85372f11589f2087d719292452bc95124d2e4da1bd5b913d12d1

COPY images/actions-runner/Aptfile /tmp/Aptfile

USER root

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

USER runner

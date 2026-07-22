FROM ghcr.io/falcondev-oss/actions-runner:2.335.1@sha256:396bad82ba63cbf574293dccc3f936aae60ef55450721d58a11978abaebb7a89

COPY images/actions-runner/Aptfile /tmp/Aptfile

USER root

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

USER runner

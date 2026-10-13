FROM ghcr.io/falcondev-oss/actions-runner:2.338.0@sha256:3c4d939869cb1374cd61bfcb3abbe6c1444991f7b20c48cbb13708484ee0a8e1

COPY images/actions-runner/Aptfile /tmp/Aptfile

USER root

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

USER runner

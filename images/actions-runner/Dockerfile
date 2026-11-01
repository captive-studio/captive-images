FROM ghcr.io/falcondev-oss/actions-runner:2.338.2@sha256:462ebdbc95fabf0bdf264ffe02ff5182665c6d99ac0f870b67d7f649c1ef1746

COPY images/actions-runner/Aptfile /tmp/Aptfile

USER root

RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile

USER runner

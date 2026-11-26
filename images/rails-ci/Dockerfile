# Node ne sert qu'à lancer l'installeur Playwright : il est monté pendant le RUN,
# sans être copié, et ne reste donc pas dans l'image finale.
FROM node:26.13.1-bookworm-slim@sha256:0042e17d232a87a2cd485be1da7900fca4d10a4ad11b29e9285da1d2e54798c9 AS node

FROM ghcr.io/captive-studio/ruby-ci:4.0.10@sha256:ac8082601e2d9f9a4dc7581079c97ba39aad1abb0c201e2e666d91409c2ffa22

COPY --chown=circleci:circleci \
  images/rails-ci/Gemfile \
  images/rails-ci/Gemfile.lock \
  /tmp/rails-ci-gems/

RUN cd /tmp/rails-ci-gems && \
    bundle config set frozen true && \
    bundle install && \
    brakeman --version && \
    rm -rf /tmp/rails-ci-gems

# Le paquet apt chromium d'Ubuntu n'est qu'une transition vers snap, inutilisable
# sans snapd : Chromium vient donc de Playwright.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright
# Le dossier Playwright est versionné (chromium-XXXX) : Ferrum lit ce chemin fixe.
ENV BROWSER_PATH=/usr/local/bin/chromium

USER root

# Cette version suit celle de node-ci-chromium : Renovate la repère
# grâce au commentaire ci-dessous (customManagers de preset.json).
# renovate: datasource=npm depName=playwright
ARG PLAYWRIGHT_VERSION=1.65.1
RUN --mount=type=bind,from=node,source=/usr/local,target=/opt/node \
    export PATH=/opt/node/bin:$PATH && \
    npx --yes playwright@${PLAYWRIGHT_VERSION} install --with-deps chromium && \
    ln -s "$(find ${PLAYWRIGHT_BROWSERS_PATH} -path '*/chromium-*/chrome-linux*/chrome' -type f | head -n 1)" ${BROWSER_PATH} && \
    ${BROWSER_PATH} --version && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm /tmp/*

USER circleci

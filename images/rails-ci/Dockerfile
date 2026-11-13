# Node ne sert qu'à lancer l'installeur Playwright : il est monté pendant le RUN,
# sans être copié, et ne reste donc pas dans l'image finale.
FROM node:26.13.1-bookworm-slim@sha256:5df79989ed685e09f0a98019db4cebfb22fb9df1a53c0161664a011f7ff6b0f1 AS node

FROM ghcr.io/captive-studio/ruby-ci:4.0.9@sha256:350764ff36345a9666b0a5d0d9786aa8444c267aa65682006d907872f69b6d47

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
ARG PLAYWRIGHT_VERSION=1.65.0
RUN --mount=type=bind,from=node,source=/usr/local,target=/opt/node \
    export PATH=/opt/node/bin:$PATH && \
    npx --yes playwright@${PLAYWRIGHT_VERSION} install --with-deps chromium && \
    ln -s "$(find ${PLAYWRIGHT_BROWSERS_PATH} -path '*/chromium-*/chrome-linux*/chrome' -type f | head -n 1)" ${BROWSER_PATH} && \
    ${BROWSER_PATH} --version && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm /tmp/*

USER circleci

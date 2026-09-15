FROM node:24.21.0-bookworm-slim@sha256:2fe369e969550cde8e867afc3fe370b260140cab4a23d467074295b42163d553

# Chromium et ses dépendances système sont posés dans l'image plutôt qu'à chaque run : le
# job d'accessibilité d'alveole-js passait 1 min 11 par exécution à les installer, sur un
# pool de runners éphémères où rien ne survit d'un job à l'autre.
#
# La version de Playwright est volontairement figée ici et doit suivre celle du projet qui
# consomme l'image : Playwright refuse de démarrer un navigateur dont la révision ne
# correspond pas à celle qu'il attend. Renovate tient les deux alignées.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# La base `slim` plutôt que `bookworm` complète : 351 Mo contre 1,64 Go, ce qui ramène
# l'image de 2,99 Go à 1,92 Go. Les outils qu'elle retire et que `node:lts` fournissait
# sont rétablis depuis l'Aptfile, qui documente à quoi chacun sert.
COPY images/node-ci/Aptfile /tmp/Aptfile

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      $(grep -v '^#' /tmp/Aptfile | grep -v '^$' | tr '\n' ' ') && \
    npx --yes playwright@1.63.0 install --with-deps chromium && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/Aptfile /root/.npm

FROM node:24.21.0-bookworm-slim

# Chromium et ses dépendances système sont posés dans l'image plutôt qu'à chaque run : le
# job d'accessibilité d'alveole-js passait 1 min 11 par exécution à les installer, sur un
# pool de runners éphémères où rien ne survit d'un job à l'autre.
#
# La version de Playwright est volontairement figée ici et doit suivre celle du projet qui
# consomme l'image : Playwright refuse de démarrer un navigateur dont la révision ne
# correspond pas à celle qu'il attend. Renovate tient les deux alignées.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# La base `slim` plutôt que `bookworm` complète : 351 Mo contre 1,64 Go, ce qui ramène
# l'image de 2,99 Go à 1,92 Go. Elle n'embarque pas git, dont actions/checkout a besoin
# pour cloner autrement que par l'API REST, d'où sa réinstallation explicite.
RUN apt-get update \
    && apt-get install -y --no-install-recommends git ca-certificates \
    && npx --yes playwright@1.63.0 install --with-deps chromium \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /root/.npm

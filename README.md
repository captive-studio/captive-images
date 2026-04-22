# Images Captive
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
> Images Docker pour déploiements et CI

___

## Liste des images

## ![Ruby](https://img.shields.io/badge/ruby-%23CC342D.svg?style=for-the-badge&logo=ruby&logoColor=white)

### Ruby CI
> Image ruby pour la configuration des déploiements.
[📋 Documentation](https://github.com/Captive-Studio/captive-images/pkgs/container/ruby-ci)

___

## Ajouter une image

### Etape 1

Créer un dossier pour l'image dans `/images`

### Etape 2

Ajouter un fichier `Dockerfile` dans le dossier

### Etape 3

Ajouter une configuration de déploiement automatique via un fichier `publish-mon-image.yml` dans `.github/workflows`

### Etape 4

Configurer la publication de l'image :
- Le workflow doit écouter uniquement les changements du `Dockerfile` et du fichier `publish-mon-image.yml` sur `main`
- Le workflow doit extraire la version de l'image a publier. **Attention**: Il faut prendre en compte que Renovate va pin les images utilisée, par exemple si vous utilisez `cimg/ruby:4.0.2` renovate le transformera en `cimg/ruby:4.0.2@sha256:XXXXXXXXX` mais on veut extraire uniquement `4.0.2`.
- Le workflow doit extraire les metadata et définir l'image comme `latest`. On doit pouvoir récupérer l'image par sa version, son sha et latest.
- Le workflow doit plublier le package sur le repo

### Etape 5

Rendre publique le package créé. A la première publication, il faut rendre publique le package et donc les images qu'il contient pour faciliter la récupération.
Pour cela, rendez-vous dans les setting du package `https://github.com/orgs/Captive-Studio/packages/container/mon-image/settings` et définissez le package comme publique dans la `Danger zone`.

### A noter : 
Pour consommer votre package, il est préférable d'utiliser la version et non `latest` ou `sha-xxx` afin que Renovate tourne correctement dans votre projet cible.


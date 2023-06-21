---
title: Utilisation de plusieurs référentiels
description: Découvrez comment gérer plusieurs référentiels Git lorsque vous utilisez Cloud Manager.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 98%

---

# Utilisation de plusieurs référentiels {#working-with-multiple-source-git-repos}

Découvrez comment gérer plusieurs référentiels Git lorsque vous utilisez Cloud Manager.

## Synchronisation des référentiels Git gérés par le client {#syncing-customer-managed-git-repositories}

Au lieu d’utiliser directement le référentiel Git de Cloud Manager, les [clients peuvent utiliser un ou plusieurs référentiels Git](integrating-with-git.md) qu’ils détiennent. Dans ces cas, un processus de synchronisation automatique doit être configuré pour s’assurer que le référentiel Git de Cloud Manager soit toujours à jour.

Selon l’emplacement d’hébergement du référentiel Git du client ou de la cliente, il est possible d’utiliser une action GitHub ou une solution d’intégration continue comme Jenkins pour configurer l’automatisation. Lorsqu’une automatisation a été mise en place, il est possible de transférer automatiquement vers le référentiel Git de Cloud Manager les transmissions destinées à un référentiel Git détenu par le client ou la cliente.

Bien que cette automatisation d’un seul référentiel Git détenu par le client ou la cliente soit simple, la configuration de ce processus pour plusieurs référentiels nécessite une configuration initiale. Le contenu des différents référentiels Git doit être mappé avec différents répertoires dans le référentiel Git unique de Cloud Manager.  Le référentiel Git de Cloud Manager doit être configuré avec un `pom.xml` Maven racine qui répertorie les différents sous-projets dans la section Modules.

Voici un exemple de fichier `pom.xml` pour deux référentiels Git détenus par le client ou la cliente.

* Le premier projet est placé dans le répertoire nommé `project-a`.
* Le second projet est placé dans le répertoire nommé `project-b`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
  
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
  
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
  
</project>
```

Ce fichier `pom.xml` racine est placé dans une branche du référentiel Git de Cloud Manager. Les deux projets doivent être ensuite configurés pour transférer automatiquement les modifications vers le référentiel Git de Cloud Manager.

Une solution possible serait la suivante.

1. Une action GitHub peut être déclenchée par une notification push vers une branche du projet A.
1. L’action va extraire le projet A et le référentiel Git de Cloud Manager et copier tout le contenu du projet A dans le répertoire `project-a` du référentiel Git de Cloud Manager.
1. Ensuite, l’action va valider et effectuer le changement.

À titre d’exemple, une modification apportée à la branche principale du projet A est automatiquement répercutée sur la branche principale du référentiel Git de Cloud Manager. Bien entendu, il pourrait exister un mappage entre les branches, par exemple une transmission vers une branche nommée `dev` dans le projet A qui est transférée dans une branche nommée `development` dans le référentiel Git de Cloud Manager. Des étapes similaires sont requises pour le projet B.

Selon les workflows et la stratégie d’embranchement, il est possible de configurer la synchronisation pour différentes branches. Si le référentiel Git utilisé ne propose pas un concept similaire aux actions GitHub, une intégration via Jenkins (ou un outil similaire) est également possible. Dans ce cas, un webhook déclenche un traitement Jenkins chargé d’effectuer le travail.

Suivez les étapes ci-dessous pour ajouter une nouvelle source tierce ou un nouveau référentiel.

1. Ajoutez une nouvelle action GitHub dans le nouveau référentiel pour transférer les modifications de ce référentiel vers le référentiel Git de Cloud Manager.
1. Effectuez cette action au moins une fois afin de garantir la présence du code du projet dans le référentiel Git de Cloud Manager.
1. Dans le référentiel Git de Cloud Manager, ajoutez un nouveau répertoire au `pom.xml` Maven racine.

## Exemple d’action GitHub {#sample-github-action}

Voici un exemple d’action GitHub déclenchée par une transmission de type push vers la branche principale, puis vers un sous-répertoire du référentiel Git de Cloud Manager. Les actions GitHub doivent comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts vers le référentiel Git de Cloud Manager.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} ${MAIN_REPOSITORY} ${MAIN_BRANCH} 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf ${MAIN_BRANCH}/${PROJECT_DIR} 
          mv sub ${MAIN_BRANCH}/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C ${MAIN_BRANCH} add -f ${PROJECT_DIR}
          git -C ${MAIN_BRANCH} commit -F ../commit.txt
          git -C ${MAIN_BRANCH} push
```

L’utilisation d’une action GitHub est très flexible. Tout mappage entre les branches des référentiels Git peut être effectué, de même que tout mappage de projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>
>L’exemple de script utilise `git add` pour mettre à jour le référentiel. Cela suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, il peut être nécessaire de le remplacer par `git add --all`.

## Exemple de traitement Jenkins {#sample-jenkins-job}

Voici un exemple de script qui peut être utilisé dans un traitement Jenkins ou un traitement similaire et qui présente le flux suivant :

1. Le script est déclenché par une modification d’un référentiel Git.
1. Le traitement Jenkins extrait le dernier état de ce projet ou de cette branche.
1. Le traitement déclenche ensuite ce script.
1. Le script extrait ensuite le référentiel Git de Cloud Manager et valide le code du projet dans un sous-répertoire.

Le traitement Jenkins doit comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts vers le référentiel Git de Cloud Manager.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

L’utilisation d’un traitement Jenkins est très flexible. Tout mappage entre les branches des référentiels Git peut être effectué, de même que tout mappage de projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>
>L’exemple de script utilise `git add` pour mettre à jour le référentiel. Cela suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, il peut être nécessaire de le remplacer par `git add --all`.

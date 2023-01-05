---
title: Utilisation de plusieurs référentiels
description: Découvrez comment gérer plusieurs référentiels Git lorsque vous utilisez Cloud Manager.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
source-git-commit: 5ea5c3f03642ae2f7471165d4d0ee33c2cc31b6b
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 41%

---

# Utilisation de plusieurs référentiels {#working-with-multiple-source-git-repos}

Découvrez comment gérer plusieurs référentiels Git lorsque vous utilisez Cloud Manager.

## Synchronisation des référentiels Git gérés par le client {#syncing-customer-managed-git-repositories}

Au lieu de travailler directement avec le référentiel git de Cloud Manager, [les clients peuvent travailler avec leur propre référentiel git.](integrating-with-git.md) ou plusieurs référentiels git. Dans ce cas, un processus de synchronisation automatisée doit être configuré pour s’assurer que le référentiel git de Cloud Manager est toujours à jour.

Selon l’emplacement d’hébergement du référentiel git du client, une action GitHub ou une solution d’intégration continue telle que Jenkins peut être utilisée pour configurer l’automatisation. Une fois une automatisation en place, chaque notification push vers un référentiel git détenu par le client peut être automatiquement transférée vers le référentiel git de Cloud Manager.

Bien qu’une telle automatisation pour un seul référentiel git détenu par le client soit simple, la configuration de cette fonctionnalité pour plusieurs référentiels nécessite une configuration initiale. Le contenu de plusieurs référentiels Git doit être mappé à différents répertoires dans le seul référentiel Git de Cloud Manager.  Le référentiel git de Cloud Manager doit être configuré avec un Maven racine. `pom.xml`, répertoriant les différents sous-projets dans la section modules .

Voici un exemple : `pom.xml` pour deux référentiels git détenus par le client.

* Le premier projet sera placé dans le répertoire nommé `project-a`.
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

Ce `pom.xml` racine est placé dans une branche du référentiel Git de Cloud Manager. Ensuite, les deux projets doivent être configurés pour transférer automatiquement les modifications vers le référentiel git de Cloud Manager.

Une solution possible serait la suivante.

1. Une action GitHub peut être déclenchée par une notification push vers une branche du projet A.
1. L’action va extraire le projet A et le référentiel git de Cloud Manager et copier tout le contenu du projet A dans le répertoire . `project-a` dans le référentiel git de Cloud Manager.
1. Ensuite, l’action validera et poussera le changement.

À titre d’exemple, une modification apportée à la branche principale du projet A est automatiquement répercutée sur la branche principale du référentiel Git de Cloud Manager. Bien entendu, il pourrait exister un mappage entre les branches, par exemple une transmission vers une branche nommée `dev` dans le projet A qui est transférée dans une branche nommée `development` dans le référentiel Git de Cloud Manager. Des étapes similaires sont requises pour le projet B.

Selon la stratégie et les workflows d’embranchement, il est possible de configurer la synchronisation pour différentes branches. Si le référentiel Git utilisé ne propose pas un concept similaire aux actions GitHub, une intégration via Jenkins (ou un outil similaire) est également possible. Dans ce cas, un webhook déclenche une tâche Jenkins qui effectue le travail.

Pour ajouter une nouvelle source ou un référentiel tiers, procédez comme suit.

1. Ajoutez une nouvelle action GitHub dans le nouveau référentiel pour transférer les modifications de ce référentiel vers le référentiel Git de Cloud Manager.
1. Effectuez cette action au moins une fois afin de garantir la présence du code du projet dans le référentiel Git de Cloud Manager.
1. Dans le référentiel Git de Cloud Manager, ajoutez un nouveau répertoire au `pom.xml` Maven racine.

## Exemple d’action GitHub {#sample-github-action}

Il s’agit d’un exemple d’action GitHub déclenchée par une notification push vers la branche principale, puis vers un sous-répertoire du référentiel git de Cloud Manager. Les actions GitHub doivent comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts vers le référentiel Git de Cloud Manager.

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

Il s’agit d’un exemple de script qui peut être utilisé dans une tâche Jenkins ou similaire et qui présente le flux suivant :

1. Le script est déclenché par une modification d’un référentiel Git.
1. Le traitement Jenkins extrait le dernier état de ce projet ou de cette branche.
1. La tâche déclenche ensuite ce script.
1. Ce script extrait ensuite le référentiel git de Cloud Manager et valide le code du projet dans un sous-répertoire.

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

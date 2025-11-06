---
title: Utiliser plusieurs référentiels
description: Découvrez comment gérer plusieurs référentiels Git lorsque vous utilisez Cloud Manager.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 31%

---

# Utilisation de plusieurs référentiels {#working-with-multiple-source-git-repos}

Découvrez comment gérer plusieurs référentiels Git lorsque vous utilisez Cloud Manager.

## Synchroniser les référentiels Git privés {#syncing-customer-managed-git-repositories}

Au lieu d’utiliser directement le référentiel Git de Cloud Manager, les clients [ peuvent utiliser leur propre référentiel Git privé](integrating-with-git.md) ou plusieurs de leurs propres référentiels Git. Dans ce cas, configurez un processus de synchronisation automatisée pour vous assurer que le référentiel Git de Cloud Manager est toujours tenu à jour.

Selon l’emplacement d’hébergement du référentiel Git du client ou de la cliente, il est possible d’utiliser une action GitHub ou une solution d’intégration continue telle que Jenkins pour configurer l’automatisation. Si une automatisation a été mise en place, chaque notification push vers un référentiel Git détenu par le client peut être automatiquement transférée vers le référentiel Git Cloud Manager.

Bien qu’une telle automatisation pour un seul référentiel Git détenu par le client soit simple, sa configuration pour plusieurs référentiels nécessite une configuration initiale. Le contenu de plusieurs référentiels Git doit être mappé à différents répertoires dans le référentiel Git Cloud Manager unique. Le référentiel Git de Cloud Manager doit être configuré avec un `pom.xml` Maven racine qui répertorie les différents sous-projets dans la section des modules.

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

Ce fichier `pom.xml` racine est transmis vers une branche du référentiel Git de Cloud Manager. Ensuite, les deux projets doivent être configurés pour transférer automatiquement les modifications vers le référentiel Git de Cloud Manager.

Une solution possible serait la suivante.

1. Déclenchez une action GitHub en effectuant un transfert vers une branche du projet A.
1. L’action extrait le projet A et le référentiel Git de Cloud Manager. Il copie ensuite tout le contenu du projet A dans le répertoire `project-a` du référentiel Git de Cloud Manager.
1. Ensuite, l’action valide et envoie la modification.

Par exemple, une modification apportée à la branche principale du projet A est automatiquement transférée vers la branche principale du référentiel Git de Cloud Manager. Il peut y avoir un mappage entre les branches, par exemple une transmission vers une branche nommée `dev` dans le projet A qui est transférée dans une branche nommée `development` dans le référentiel Git de Cloud Manager. Des étapes similaires sont requises pour le projet B.

Selon les workflows et la stratégie d’embranchement, il est possible de configurer la synchronisation pour différentes branches. Si le référentiel Git utilisé ne propose pas de concept similaire aux actions GitHub, une intégration via Jenkins (ou un outil similaire) est également possible. Dans ce cas, un webhook déclenche un traitement Jenkins, qui effectue le travail.

Pour ajouter une nouvelle source tierce ou un nouveau référentiel, procédez comme suit.

1. Ajoutez une action GitHub dans le nouveau référentiel pour transférer les modifications de ce référentiel vers le référentiel Git Cloud Manager.
1. Effectuez cette action au moins une fois pour vous assurer que le code du projet se trouve dans le référentiel Git de Cloud Manager.
1. Dans le référentiel Git de Cloud Manager, ajoutez une référence au nouveau répertoire dans le `pom.xml` Maven racine.



## Exemple d’action GitHub {#sample-github-action}

Voici un exemple d’action GitHub déclenchée par un transfert vers la branche principale. Effectuez ensuite une exportation vers un sous-répertoire du référentiel Git de Cloud Manager. Les actions GitHub doivent comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts vers le référentiel Git de Cloud Manager.

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

L’utilisation d’une action GitHub est flexible. Tout mappage entre les branches des référentiels Git peut être effectué, de même que tout mappage des projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>
>L’exemple de script utilise `git add` pour mettre à jour le référentiel. Le script suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, il doit être remplacé par `git add --all`.

## Exemple de traitement Jenkins {#sample-jenkins-job}

Voici un exemple de script pouvant être utilisé dans un traitement Jenkins ou un traitement similaire et ayant le flux suivant :

1. Il est déclenché par une modification dans un référentiel Git.
1. Le traitement Jenkins extrait le dernier état de ce projet ou de cette branche.
1. Le traitement déclenche ensuite ce script.
1. Ce script extrait ensuite le référentiel Git de Cloud Manager et valide le code du projet dans un sous-répertoire.

Le traitement Jenkins doit comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts vers le référentiel Git Cloud Manager.

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

L’utilisation d’un traitement Jenkins est flexible. Tout mappage entre les branches des référentiels Git peut être effectué, de même que tout mappage des projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>
>L’exemple de script utilise `git add` pour mettre à jour le référentiel. Le script suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, il doit être remplacé par `git add --all`.

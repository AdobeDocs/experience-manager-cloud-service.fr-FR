---
title: Utilisation de plusieurs référentiels Git source
description: Utilisation de plusieurs référentiels Git source – Cloud Services
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
source-git-commit: 21669a29fbfd1072b637f407f5220825c4d1edbb
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 100%

---

# Utilisation de plusieurs référentiels Git source {#working-with-multiple-source-git-repos}


## Synchronisation des référentiels Git gérés par le client {#syncing-customer-managed-git-repositories}

Au lieu de travailler directement avec le référentiel Git de Cloud Manager, les clients peuvent travailler avec un ou plusieurs référentiels Git qu’ils détiennent. Dans ce cas, un processus de synchronisation automatique doit être configuré pour s’assurer que le référentiel Git de Cloud Manager soit toujours à jour. Selon l’emplacement d’hébergement du référentiel Git du client, il est possible d’utiliser une action GitHub ou une solution d’intégration continue comme Jenkins pour configurer l’automatisation. Si une automatisation a été mise en place, il est possible de transférer automatiquement vers le référentiel Git de Cloud Manager les transmissions destinées à un référentiel Git détenu par le client.

Bien que cette automatisation d’un seul référentiel Git détenu par le client soit simple, la configuration de ce processus pour plusieurs référentiels nécessite une configuration initiale. Le contenu des référentiels Git doit être mappé avec différents répertoires dans le référentiel Git unique de Cloud Manager.  Ce référentiel doit être mis en service avec un modèle pom Maven racine qui répertorie les différents sous-projets dans la section des modules.

Vous trouverez ci-dessous un exemple de modèle pom pour deux référentiels Git détenus par le client : le premier projet sera placé dans le répertoire `project-a`, le second dans le répertoire `project-b`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
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

Ce modèle pom racine est placé dans une branche du référentiel Git de Cloud Manager. Les deux projets doivent être ensuite configurés pour transférer automatiquement les modifications vers le référentiel Git de Cloud Manager.

Une action GitHub peut, par exemple, être déclenchée par un transfert (push) vers une branche du projet A. L’action va extraire le projet A et le référentiel Git de Cloud Manager, copier l’ensemble du contenu du projet A vers le répertoire `project-a` dans le référentiel Git de Cloud Manager, puis valider et transférer (commit-push) la modification. À titre d’exemple, une modification apportée à la branche principale du projet A est automatiquement répercutée sur la branche principale du référentiel Git de Cloud Manager. Bien sûr, il pourrait y avoir un mappage entre branches, par exemple un transfert vers une branche nommée « dev » dans le projet A, répercuté vers une branche nommée « development » dans le référentiel Git de Cloud Manager. Des étapes similaires sont nécessaires pour le projet B.

Selon la stratégie et les workflows d’embranchement, il est possible de configurer la synchronisation pour différentes branches. Si le référentiel Git utilisé ne propose pas un concept similaire aux actions GitHub, une intégration par le biais de Jenkins (ou de type similaire) est également possible. Dans ce cas, un webhook déclenche un traitement Jenkins chargé d’effectuer le travail.

Suivez les étapes ci-dessous pour ajouter une source ou un référentiel nouveaux (la ou le troisième) :

1. Ajoutez une nouvelle action GitHub dans le nouveau référentiel pour transférer les modifications de ce référentiel vers le référentiel Git de Cloud Manager.
1. Effectuez cette action au moins une fois pour vous assurer que le code du projet se trouve dans le référentiel Git de Cloud Manager.
1. Dans le référentiel Git de Cloud Manager, ajoutez une référence au nouveau répertoire dans le modèle pom Maven racine.


## Exemple d’action GitHub {#sample-github-action}

Il s’agit d’un exemple d’action GitHub déclenchée par un transfert vers la branche principale, puis vers un sous-répertoire du référentiel Git de Cloud Manager. Les actions GitHub doivent comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts (push) vers le référentiel Git de Cloud Manager.

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
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Comme indiqué ci-dessus, l’utilisation d’une action GitHub est très flexible. Il est possible d’effectuer un mappage quelconque entre branches des référentiels Git, ou des mappages de projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>Le script ci-dessus utilise `git add` pour mettre à jour le référentiel, en supposant que les suppressions sont incluses. Selon la configuration de Git par défaut, la commande doit être remplacée par `git add --all`.

## Exemple de traitement Jenkins {#sample-jenkins-job}

Il s’agit d’un exemple de script pouvant être utilisé dans un traitement Jenkins ou tout autre traitement similaire. Ce script est déclenché par une modification d’un référentiel Git. Le traitement Jenkins extrait l’état le plus récent de ce projet ou de cette branche, puis déclenche ce script.

Le script extrait ensuite le référentiel Git de Cloud Manager et valide le code du projet dans un sous-répertoire.

Le traitement Jenkins doit comporter deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et effectuer des transferts (push) vers le référentiel Git de Cloud Manager.

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

Comme indiqué ci-dessus, l’utilisation d’un traitement Jenkins est très flexible. Il est possible d’effectuer un mappage quelconque entre branches des référentiels Git, ou des mappages de projets Git distincts dans la disposition des répertoires du projet principal.

>[!NOTE]
>Le script ci-dessus utilise `git add` pour mettre à jour le référentiel, en supposant que les suppressions sont incluses. Selon la configuration de Git par défaut, la commande doit être remplacée par `git add --all`.

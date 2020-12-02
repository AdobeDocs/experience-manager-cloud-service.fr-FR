---
title: Utilisation de plusieurs référentiels Git source
description: Utilisation de plusieurs référentiels Git source - Cloud Services
translation-type: tm+mt
source-git-commit: 89429fcba3a1d4f5e5fe9c98ef235057b979ad60
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# Utilisation de plusieurs référentiels Git de source {#working-with-multiple-source-git-repos}


## Synchronisation des référentiels Git gérés par le client {#syncing-customer-managed-git-repositories}

Au lieu de travailler directement avec le référentiel Git de Cloud Manager, les clients peuvent travailler avec leur propre référentiel Git ou plusieurs référentiels Git. Dans ce cas, un processus de synchronisation automatisé doit être configuré pour s’assurer que le référentiel Git de Cloud Manager est toujours à jour. Selon l’emplacement d’hébergement du référentiel Git du client, une action GitHub ou une solution d’intégration continue telle que Jenkins peuvent être utilisées pour configurer l’automatisation. Avec une automatisation en place, chaque transmission vers un référentiel Git détenu par le client peut être automatiquement transférée vers le référentiel Git de Cloud Manager.

Bien qu&#39;une telle automatisation pour un référentiel Git détenu par un client unique soit directe, la configuration de cette automatisation pour plusieurs référentiels nécessite une configuration initiale. Le contenu de plusieurs référentiels Git doit être mappé à différents répertoires dans le référentiel Git de Cloud Manager unique.  Le référentiel Git de Cloud Manager doit être mis en service avec un pom Maven racine, répertoriant les différents sous-projets dans la section des modules.

Vous trouverez ci-dessous un exemple de module pour deux référentiels Git détenus par des clients : le premier projet sera placé dans le répertoire `project-a`, le second dans le répertoire `project-b`.

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

Une telle racine est placée dans une branche du référentiel Git de Cloud Manager. Ensuite, les deux projets doivent être configurés pour transférer automatiquement les modifications au référentiel Git de Cloud Manager.

Par exemple, une action GitHub peut être déclenchée par une action Push vers une branche du projet A. L&#39;action va extraire le projet A et le référentiel Cloud Manager Git et copier tout le contenu du projet A vers le répertoire `project-a` dans le référentiel Git de Cloud Manager, puis valider et pousser la modification. Par exemple, une modification apportée à la branche principale du projet A est automatiquement répercutée sur la branche principale dans le référentiel Git de Cloud Manager. Bien sûr, il pourrait y avoir un mappage entre des branches comme une poussée vers une branche nommée &quot;dev&quot; dans le projet A est envoyée à une branche nommée &quot;development&quot; dans le référentiel Git de Cloud Manager. Des étapes similaires sont nécessaires pour le projet B.

Selon la stratégie et les workflows d&#39;embranchement, la synchronisation peut être configurée pour différentes branches. Si le référentiel Git utilisé ne fournit pas un concept similaire aux actions GitHub, une intégration via Jenkins (ou similaire) est également possible. Dans ce cas, un webhook déclenche une tâche Jenkins qui effectue le travail.

Suivez les étapes ci-dessous pour ajouter une nouvelle (troisième) source ou référentiel :

1. Ajoutez une nouvelle action GitHub dans le nouveau référentiel qui envoie les modifications de ce référentiel vers le référentiel Git de Cloud Manager.
1. Effectuez cette action au moins une fois pour vous assurer que le code du projet se trouve dans le référentiel Git de Cloud Manager.
1. Ajoutez une référence au nouveau répertoire dans le répertoire Maven racine du référentiel Git de Cloud Manager.


## Annexe A : Exemple d&#39;action GitHub {#sample-github-action}

Il s’agit d’un exemple d’action GitHub déclenchée par une poussée vers la branche principale, puis dans un sous-répertoire du référentiel Git de Cloud Manager. Les actions GitHub doivent être dotées de deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et transmettre au référentiel Git de Cloud Manager.

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

Comme indiqué ci-dessus, l&#39;utilisation d&#39;une action GitHub est très flexible. Tout mappage entre les branches des référentiels Git peut être effectué ainsi que tout mappage des projets de git distincts dans la mise en page des répertoires du projet principal.

>[!NOTE]
>Le script ci-dessus utilise `git add` pour mettre à jour le référentiel qui suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, il doit être remplacé par `git add --all`.

## Annexe B : Exemple de travail Jenkins {#sample-jenkins-job}

Il s’agit d’un exemple de script pouvant être utilisé dans une tâche Jenkins ou une tâche similaire. Il est déclenché par une modification dans un référentiel Git. La tâche Jenkins extrait l&#39;état le plus récent de ce projet ou branche, puis déclenche ce script.

Ce script récupère ensuite le référentiel Git de Cloud Manager et valide le code du projet dans un sous-répertoire.

La tâche Jenkins doit être dotée de deux secrets, `MAIN_USER` et `MAIN_PASSWORD`, pour pouvoir se connecter et transmettre au référentiel Git de Cloud Manager.

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

Comme indiqué ci-dessus, l&#39;utilisation d&#39;une tâche Jenkins est très flexible. Tout mappage entre les branches des référentiels Git peut être effectué ainsi que tout mappage des projets Git distincts dans la mise en page des répertoires du projet principal.

>[!NOTE]
>Le script ci-dessus utilise `git add` pour mettre à jour le référentiel qui suppose que les suppressions sont incluses. Selon la configuration par défaut de Git, il doit être remplacé par `git add --all`.
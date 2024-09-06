---
title: Configuration des variables de pipeline
description: Découvrez comment utiliser les variables de pipeline dans Cloud Manager pour gérer des variables de configuration spécifiques pour votre version.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 20%

---

# Configuration des variables de pipeline {#configuring-pipeline-variables}

Votre processus de création peut dépendre de variables de configuration spécifiques qui ne seraient pas appropriées pour le référentiel git ou vous devrez peut-être les varier entre les exécutions de pipeline utilisant la même branche. Cloud Manager vous permet de gérer ces données en tant que variables de pipeline.

## Variables de pipeline {#pipeline-variables}

Cloud Manager vous permet de configurer des variables de pipeline de plusieurs manières différentes.

* [Via l’interface utilisateur de Cloud Manager](#ui)
* [Utilisation de l’interface de ligne de commande de Cloud Manager](#cli)
* [Utilisation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Les variables peuvent être stockées en texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de génération en tant que variable d’environnement qui peut ensuite être référencée à partir du fichier `pom.xml` ou d’autres scripts de génération.

### Conventions de dénomination des variables de pipeline {#naming-conventions}

Les noms de variables doivent respecter les conventions suivantes.

* Les variables ne peuvent contenir que des caractères alphanumériques et un trait de soulignement (`_`).
* Les noms doivent être en majuscules.
* Il existe une limite de 200 variables par pipeline.
* Chaque nom doit comporter 100 caractères ou moins.
* La valeur `string` de chaque variable doit comporter moins de 2 048 caractères.
* Chaque valeur de variable de type `secretString` doit comporter 500 caractères ou moins.

## Via l’interface utilisateur de Cloud Manager {#ui}

Les variables de pipeline peuvent être configurées et gérées via l’interface utilisateur de Cloud Manager. Vous devez disposer des autorisations nécessaires pour modifier le pipeline pour ajouter, modifier et supprimer des variables de pipeline.

Si un pipeline s’exécute, la gestion des variables est bloquée.

### Ajout de variables de pipeline {#add-ui}

1. Lorsque [vous gérez vos pipelines,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) appuyez ou cliquez sur le bouton représentant des points de suspension du pipeline pour lequel vous souhaitez créer des variables de pipeline et sélectionnez **Afficher/modifier des variables** dans le menu contextuel.

   ![Afficher/modifier des variables de pipeline](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. La fenêtre **Configuration des variables** s’ouvre. Saisissez les détails de la variable dans la première ligne du tableau et appuyez ou cliquez sur **Ajouter**.

   * **Nom de configuration** est un identifiant unique de votre variable, qui doit gérer les [conventions d’appellation des variables de pipeline](#naming-conventions).
   * **Value** est la valeur contenue par la variable.
   * **Étape appliquée** est l’étape du pipeline à laquelle la variable s’applique. Elle est requise.
      * **Build**
      * **Tests fonctionnels**
      * **Tests de l’interface utilisateur**
   * **Type** définit si la variable est en texte brut ou chiffrée en secret.

   ![Ajouter une variable](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. Le est ajouté au tableau. Ajoutez d’autres variables selon les besoins, puis appuyez ou cliquez sur **Enregistrer** pour enregistrer les variables que vous avez ajoutées au pipeline.

### Modification des variables de pipeline {#edit-ui}

1. Lorsque [vous gérez vos pipelines,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) appuyez ou cliquez sur le bouton représentant des points de suspension du pipeline pour lequel vous souhaitez créer des variables de pipeline et sélectionnez **Afficher/modifier des variables** dans le menu contextuel.

   ![Afficher/modifier des variables de pipeline](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. La fenêtre **Configuration des variables** s’ouvre. Appuyez ou cliquez sur le bouton représentant des points de suspension de la variable que vous souhaitez modifier, puis sélectionnez **Modifier**.

   ![Modifier la variable](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. Mettez à jour la valeur de la variable selon les besoins et appuyez ou cliquez sur **Appliquer** (coche à la fin de la ligne) pour appliquer la modification ou sur **Ignorer** (flèche vers l’arrière) pour annuler la modification.

   * Seule la valeur de la variable peut être modifiée.

   ![Modification d&#39;une variable](/help/implementing/cloud-manager/assets/pipeline-variables-edit-save.png)

1. Appuyez ou cliquez sur **Enregistrer** pour enregistrer les modifications que vous avez apportées aux variables dans le pipeline.

Si vous souhaitez supprimer une variable, sélectionnez **Supprimer** au lieu de **Modifier** dans le menu de points de suspension de la variable de pipeline dans la fenêtre **Configuration des variables**.

## Utilisation de l’interface de ligne de commande de Cloud Manager {#cli}

Cette commande d’interface de ligne de commande définit une variable.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Cette commande répertorie les variables.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

En cas d’utilisation dans un fichier `pom.xml` Maven, il est généralement utile de mapper ces variables aux propriétés Maven en utilisant une syntaxe similaire à celle-ci.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

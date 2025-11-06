---
title: Variables de pipeline dans Cloud Manager
description: Découvrez comment utiliser les variables de pipeline dans Cloud Manager pour gérer des variables de configuration spécifiques pour votre version.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 14%

---

# Variables de pipeline dans Cloud Manager {#configuring-pipeline-variables}

Votre processus de création peut dépendre de variables de configuration spécifiques qui ne doivent pas être stockées dans le référentiel Git. Vous pouvez également les ajuster entre les exécutions de pipeline sur la même branche. Cloud Manager vous permet de gérer ces paramètres en tant que variables de pipeline.

## À propos des variables de pipeline {#pipeline-variables}

Avec Cloud Manager, vous pouvez configurer les variables de pipeline de plusieurs manières différentes.

* [Utilisation de l’interface utilisateur de Cloud Manager](#ui)
* [Utilisation de l’interface de ligne de commande Cloud Manager](#cli)
* [Utilisation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Les variables peuvent être stockées en texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de création en tant que variable d’environnement qui peut ensuite être référencée depuis le fichier `pom.xml` ou d’autres scripts de création.

## Ajouter une variable de pipeline via Cloud Manager {#ui}

Les variables de pipeline peuvent être configurées et gérées via l’interface utilisateur de Cloud Manager. Ils permettent de rationaliser la gestion des pipelines, en particulier lorsque différentes configurations sont requises selon différentes étapes.

Vous devez disposer des autorisations de modification du pipeline pour ajouter, modifier et supprimer des variables de pipeline.

Si un pipeline est actif, la gestion des variables est bloquée.

**Pour ajouter une variable de pipeline via Cloud Manager :**

1. Lors de la [gestion de vos pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), cliquez sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) du pipeline pour lequel vous souhaitez créer des variables de pipeline.

1. Dans le menu déroulant, cliquez sur **Afficher/Modifier les variables**.

   ![Affichage/modification des variables de pipeline](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Dans la boîte de dialogue **Configuration des variables**, saisissez les détails dans la première ligne du tableau.

   | Champ | Description |
   | --- | --- |
   | Nom | Nom unique de la variable de configuration. Il identifie la variable spécifique utilisée dans le pipeline. Il doit respecter les conventions de dénomination suivantes :<ul><li>Les variables ne peuvent contenir que des caractères alphanumériques et le trait de soulignement (`_`).</li><li>Les noms doivent être en majuscules.</li><li>Il existe une limite de 200 variables par pipeline.</li><li>Chaque nom doit comporter 100 caractères ou moins.</li><li>La valeur `string` de chaque variable doit comporter moins de 2 048 caractères.</li><li>La valeur de chaque variable de type `secretString` doit comporter 500 caractères ou moins.</li></ul> |
   | Valeur | Valeur de la variable. |
   | Étape appliquée | Obligatoire. L’étape du pipeline à laquelle la variable s’applique :<ul><li>**Build** - La variable est appliquée pendant le processus de création.</li><li>**Tests fonctionnels** - La variable est utilisée pendant l’étape de test fonctionnel.</li><li>**Test de l’interface utilisateur** - La variable est utilisée pendant la phase de test de l’interface utilisateur.</li><li>**Déployer** - La variable est utilisée lors de l’étape de déploiement. Par exemple, utilisez cette variable pour les pipelines Edge Delivery Services.</li></ul> |
   | Type | Sélectionnez cette option si la variable est en texte brut ou chiffrée en tant que secret. |

   ![&#x200B; Ajouter une variable &#x200B;](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. Cliquez sur **Ajouter**.

   Ajoutez des variables supplémentaires si nécessaire.

1. Cliquez sur **Enregistrer**.

## Modification d’une variable de pipeline {#edit-ui}

1. Lors de la [gestion de vos pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), cliquez sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) du pipeline pour lequel vous souhaitez modifier les variables de pipeline.

1. Dans le menu déroulant, cliquez sur **Afficher/Modifier les variables**.

   ![Affichage/modification des variables de pipeline](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Dans la boîte de dialogue **Configuration des variables**, cliquez sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) de la variable à modifier.

1. Dans le menu déroulant, cliquez sur **Modifier**.

   ![Modifier la variable](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. Mettez à jour la valeur de la variable selon les besoins.

   Seule la valeur de la variable peut être modifiée.

1. Utilisez l’une des méthodes suivantes :

   * Cliquez sur ![Appliquer - Icône de coche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg) pour appliquer la modification.
   * Cliquez sur ![Icône Annuler](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg) pour annuler la modification.

1. Cliquez sur **Enregistrer**.


## Suppression d’une variable de pipeline {#delete-ui}

1. Lors de la [gestion de vos pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), cliquez sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) du pipeline pour lequel vous souhaitez supprimer des variables de pipeline.

1. Dans le menu déroulant, cliquez sur **Afficher/Modifier les variables**.

   ![Affichage/modification des variables de pipeline](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Dans la boîte de dialogue **Configuration des variables**, cliquez sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) de la variable à supprimer, puis cliquez sur **Supprimer**.

## Définir des variables de pipeline à l’aide de l’interface de ligne de commande Cloud Manager {#cli}

Cette commande de l’interface de ligne de commande (CLI) définit une variable.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Cette commande répertorie les variables.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Lorsqu’elles sont utilisées dans un fichier Maven `pom.xml`, il est souvent utile de lier ces variables aux propriétés Maven en utilisant une syntaxe similaire à l’exemple suivant :

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

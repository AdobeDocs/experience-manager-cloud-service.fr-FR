---
title: Configuration de pipelines hors production
description: Consultez cette page pour en savoir plus sur la configuration d’un pipeline hors production dans Cloud Manager
index: true
source-git-commit: 2ac65af4cf410491d1196b9e20f67647e0a1b4d1
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 30%

---


# Configuration de pipelines hors production {#configure-non-production-pipeline}

En plus du pipeline principal qui se déploie vers les environnements intermédiaire et de production, les clients peuvent configurer des pipelines supplémentaires, appelés Pipelines hors production.

Il existe deux types de pipelines hors production :

1. Qualité du code : Exécute des analyses de qualité du code sur le code d’une branche Git. Ce pipeline exécute les étapes de génération et de qualité de code.
1. Déploiement : Outre l’exécution des étapes de création et de qualité de code, ce pipeline déploie le code vers la non-production sélectionnée dans AEM environnement as a Cloud Service.

## Ajout d’un nouveau pipeline hors production {#adding-non-production-pipeline}

Sur l’écran d’accueil, ces pipelines sont répertoriés dans une nouvelle carte :

1. Accédez au **Pipelines** à partir de l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline hors production**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **Ajout d’un pipeline hors production**  s’affiche. Sélectionnez le type de pipeline que vous souhaitez créer, au choix : **Pipeline de qualité du code** ou **Pipeline de déploiement**.

   >[!NOTE]
   >Pour les pipelines de déploiement, vous devez sélectionner l’environnement de déploiement.

   En outre, vous pouvez également configurer **Déclencheur de déploiement** et **Comportement des échecs de mesure importants** de **Options de déploiement**. Cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

   Vous pouvez définir les déclencheurs de déploiement suivants pour démarrer le pipeline.

   * **Manuel** : l’utilisation de l’interface lance le pipeline manuellement.
   * **Lors des modifications Git** : démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Même si vous sélectionnez cette option, vous pouvez toujours démarrer le pipeline manuellement.

      Lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

      Cela s’avère utile pour les clients qui souhaitent davantage de processus automatisés. Les options disponibles sont les suivantes :
   Vous pouvez définir le comportement important des mesures d’échec pour démarrer le pipeline.

   * **Demander à chaque fois** : il s’agit du paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
   * **Échec immédiat** - Si cette option est sélectionnée, le pipeline sera annulé chaque fois qu’un échec important se produit. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** - Si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.


1. Sélectionner **[Code de pile complet](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** ou **[Code front-end](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**.

   Si vous avez sélectionné **Code front-end**, vous devez sélectionner la variable **Référentiel**, **Branche Git** et **Emplacement du code**, comme illustré dans la figure ci-dessous :

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-confignew1.png)

   Si vous avez sélectionné **Code de pile complet**, vous devez sélectionner la variable **Référentiel** et **Branche Git**, comme illustré dans la figure :
   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-fullstack1.png)

   >[!IMPORTANT]
   >Si un pipeline de code de pile complet existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

   >[!NOTE]
   >Avant de commencer à configurer les pipelines front-end, voir [parcours de création rapide de site](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites-journey/quick-site/overview.html) pour un workflow de bout en bout grâce à l’outil de création rapide de site d’AEM convivial. Ce site de documentation vous aidera à rationaliser le développement frontal de votre site AEM et à personnaliser rapidement votre site sans aucune connaissance AEM du serveur principal.

1. Le nouveau pipeline hors production s’affiche désormais dans la variable **Pipelines** carte.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-fullstack2.png)


   Le pipeline s’affiche sur la carte de l’écran d’accueil avec quatre actions, comme illustré ci-dessous :

   * **Ajouter** - permet d’ajouter un nouveau pipeline.
   * **Tout afficher** - permet à l’utilisateur d’afficher tous les pipelines.
   * **Accès aux informations sur le référentiel** - permet à l’utilisateur d’obtenir les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
   * **En savoir plus** : suivez ce lient pour en savoir plus sur les ressources de documentation du pipeline CI/CD.
---
title: Configuration des pipelines de production
description: Configuration des pipelines de production
index: false
source-git-commit: fe3bd08e32cef20403d3d2799d027b3ed03e6d36
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 46%

---


# Configuration d’un pipeline de production {#configure-production-pipeline}

Le responsable de déploiement est chargé de la configuration du pipeline de production.

>[!NOTE]
>Un pipeline de production ne peut être configuré que lorsqu’un programme a été créé, que si le référentiel Git comporte au moins une branche et que si un ensemble d’environnements de production et d’évaluation a été créé.

Avant de commencer le déploiement du code, vous devez configurer les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>Vous pouvez modifier les paramètres du pipeline après la configuration initiale.

## Ajout d’un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez au moins d’un environnement utilisant [!UICONTROL Cloud Manager] Dans l’interface utilisateur, vous êtes prêt à ajouter un pipeline de production.

Pour configurer le comportement et les préférences de votre pipeline de production, procédez comme suit :

1. Accédez au **Pipelines** de la carte **Aperçu du programme** page.
Cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline de production**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **Ajout d’un pipeline de production** s’affiche. Saisissez le nom du pipeline.

   En outre, vous pouvez également configurer **Déclencheur de déploiement** et **Comportement des échecs de mesure importants** de **Options de déploiement**. Cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-add2.png)


   Vous pouvez définir les déclencheurs de déploiement pour démarrer le pipeline.

   * **Manuel** : l’utilisation de l’interface lance le pipeline manuellement.
   * **Lors des modifications Git** : démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Même si vous sélectionnez cette option, vous pouvez toujours démarrer le pipeline manuellement.

      Lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

      Cela s’avère utile pour les clients qui souhaitent davantage de processus automatisés. Les options disponibles sont les suivantes :
   Vous pouvez définir le comportement important des mesures d’échec pour démarrer le pipeline.

   * **Demander à chaque fois** : il s’agit du paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
   * **Échec immédiat** - Si cette option est sélectionnée, le pipeline sera annulé chaque fois qu’un échec important se produit. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** - Si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.


1. Le **Ajout d’un pipeline de production** La boîte de dialogue comprend un second onglet intitulé **Code source**. Vous pouvez sélectionner **[Code de pile complet](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** ou **[Code front-end](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**. Vous pouvez choisir le **Référentiel** et le **Branche Git**. Sélectionnez les options de déploiement en production, comme expliqué ci-dessous. Cliquez sur **Continuer**.

   >[!IMPORTANT]
   >Si un pipeline de code de pile complet existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-fullstack1.png)

   >[!NOTE]
   >Avant de commencer à configurer les pipelines front-end, reportez-vous à la section Parcours de création de site rapide pour un workflow de bout en bout grâce à l’outil de création de site rapide AEM convivial. Ce site de documentation vous aidera à rationaliser le développement frontal de votre site AEM et à personnaliser rapidement votre site sans aucune connaissance AEM du serveur principal.

   Options de déploiement en production:

   * **Mettre en pause avant le déploiement en production**: Cette option permet de suspendre l’étape de déploiement avant la production.
   * **Planifié**: Cette option permet à l’utilisateur d’activer le déploiement en production planifié.

1. Le **Ajout d’un pipeline de production** La boîte de dialogue comprend un troisième onglet intitulé **Audit de l’expérience**. Cette option fournit un tableau pour les chemins d’URL qui doivent toujours être inclus dans le contrôle de l’expérience.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

   >[!IMPORTANT]
   >Vous devez cliquer sur **Ajouter une page** pour définir votre propre lien personnalisé. Le chemin de page doit commencer par `/`.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit2.png)


   Cliquez sur **Ajouter une nouvelle page** pour fournir un chemin d’URL à inclure dans le contrôle de l’expérience.

   Par exemple, si vous souhaitez inclure `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, entrez le chemin `/us/en/about-us.html` dans ce champ et cliquez sur **Sauvegarder**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

   L’URL qui apparaît dans le tableau présente les caractéristiques suivantes :

   `https://publish-p12361-e112003.adobeaemcloud.com/us/en/about-us.html`

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

   25 lignes au maximum peuvent être incluses. Si aucune page n’est envoyée par l’utilisateur dans cette section, la page d’accueil du site est incluse par défaut dans le contrôle de l’expérience.

   Pour plus d’informations, voir [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

   >[!NOTE]
   > Les pages configurées sont envoyées au service et évaluées en fonction des tests de performances, d’accessibilité, d’optimisation du moteur de recherche (SEO), de bonnes pratiques et d’application web progressive (PWA).

1. Cliquez sur **Enregistrer**. Le nouveau pipeline de production s’affiche désormais dans la variable **Pipelines** carte.

   Le pipeline s’affiche sur la carte de l’écran d’accueil avec trois actions, comme illustré ci-dessous :

   * **Ajouter** - permet d’ajouter un nouveau pipeline.
   * **Accès aux informations sur le référentiel** - permet à l’utilisateur d’obtenir les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
   * **En savoir plus** : suivez ce lient pour en savoir plus sur les ressources de documentation du pipeline CI/CD.



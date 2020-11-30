---
title: Configuration du pipeline CI/CD - Cloud Services
description: Configuration du pipeline CI/CD - Cloud Services
translation-type: tm+mt
source-git-commit: 4d5ad99e44446ac40d9798df1c7fabb862065495
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 100%

---


# Configuration du pipeline CI-CD {#configure-ci-cd-pipeline}

Dans Cloud Manager, il existe deux types de pipeline :

* **Pipeline de production** :

   Un pipeline de production ne peut être ajouté qu’une fois qu’un ensemble d’environnements de production et d’évaluation est créé.

   Pour plus d’informations, voir [Configuration d’un pipeline de production](configure-pipeline.md#setting-up-the-pipeline).

* **Pipeline hors production** :

   Vous pouvez ajouter un pipeline hors production à partir de la page **Aperçu** de l’interface utilisateur de Cloud Manager.

   Pour plus d’informations, consultez [Pipelines hors production et dédiés à la qualité du code](configure-pipeline.md#non-production-pipelines).

>[!NOTE]
>Pour configurer votre pipeline, vous devez :
> * définir le déclencheur qui le démarrera ;
> * définir les paramètres qui contrôlent le déploiement en production ;
> * configurer les paramètres de test de performance.


## Configuration d’un pipeline de production {#setting-up-production-pipeline}

Le responsable de déploiement est chargé de la configuration du pipeline de production.

>[!NOTE]
>Un pipeline de production ne peut être configuré que lorsqu’un programme a été créé, que si le référentiel Git comporte au moins une branche et que si un ensemble d’environnements de production et d’évaluation a été créé.

Avant de commencer le déploiement du code, vous devez configurer les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez modifier les paramètres du pipeline après la configuration initiale.

## Configuration des paramètres du pipeline à partir de [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

Une fois que vous avez configuré votre programme et que vous disposez au moins d’un environnement basé sur l’interface utilisateur de [!UICONTROL Cloud Manager], vous êtes prêt à configurer votre pipeline de déploiement.

Pour configurer le comportement et les préférences de votre pipeline, procédez comme suit :

1. Cliquez sur **Configurer un pipeline** pour configurer votre pipeline.

   ![](assets/set-up-pipeline1.png)

1. L’écran **Configurer un pipeline** s’affiche. Sélectionnez la branche, puis cliquez sur **Suivant**.

   ![](assets/setup-1.png)

1. Configurez vos options de déploiement.

   ![](assets/setup-2.png)

   Vous pouvez définir le déclencheur pour démarrer le pipeline :

   * **Manuel** : l’utilisation de l’interface lance le pipeline manuellement.
   * **Lors des modifications Git** : démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Même si vous sélectionnez cette option, vous pouvez toujours démarrer le pipeline manuellement.

   Lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

   Cela s’avère utile pour les clients qui souhaitent davantage de processus automatisés. Les options disponibles sont les suivantes :

   * **Demander à chaque fois** : il s’agit du paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
   * **Échec immédiatement** : si cette option est sélectionnée, le pipeline sera annulé chaque fois qu’un échec important se produira. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** : si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.


1. Les paramètres du pipeline de production comprennent un troisième onglet intitulé **Contrôle de l’expérience**. Cette option fournit un tableau pour les chemins d’URL qui doivent toujours être inclus dans le contrôle de l’expérience.

   >[!NOTE]
   >Vous devez cliquer sur **Ajouter une nouvelle page** pour définir votre propre lien personnalisé.

   ![](assets/setup-3.png)

   Cliquez sur **Ajouter une nouvelle page** pour fournir un chemin d’URL à inclure dans le contrôle de l’expérience.

   Par exemple, si vous souhaitez inclure `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, entrez le chemin `us/en/about-us.html` dans ce champ et cliquez sur **Sauvegarder**.

   ![](assets/exp-audit4.png)

   L’URL qui apparaît dans le tableau présente les caractéristiques suivantes :

   `https://publish-p14253-e43686.adobeaemcloud.com/us/en/about-us.html`

   ![](assets/exp-audit5.png)

   25 lignes au maximum peuvent être incluses. Si aucune page n’est envoyée par l’utilisateur dans cette section, la page d’accueil du site est incluse par défaut dans le contrôle de l’expérience.

   Pour plus d’informations, voir [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

   >[!NOTE]
   > Les pages configurées sont envoyées au service et évaluées en fonction des tests de performances, d’accessibilité, d’optimisation du moteur de recherche (SEO), de bonnes pratiques et d’application web progressive (PWA).

1. Cliquez sur **Enregistrer** dans l’écran **Modifier le pipeline**. La page **Aperçu** affiche désormais la carte **Déployer votre programme**. Cliquez sur le bouton **Déployer** pour déployer votre programme.

   ![](assets/configure-pipeline5.png)


## Pipelines hors production et dédiés à la qualité du code {#non-production-pipelines}

En plus du pipeline principal qui se déploie vers les environnements intermédiaire et de production, les clients peuvent configurer des pipelines supplémentaires, appelés **Pipelines hors production**. Ces pipelines exécutent toujours les étapes de génération et de qualité de code. Si besoin est, elles peuvent aussi déployer vers l’environnement Adobe Managed Services.

Sur l’écran d’accueil, ces pipelines sont répertoriés dans une nouvelle carte :

1. Accédez à la vignette **Pipelines hors production** depuis l’écran d’accueil de Cloud Manager.

   ![](assets/configure-pipeline6.png)

1. Cliquez sur le bouton **Ajouter** pour spécifier le nom du pipeline, le type de pipeline et la branche Git.

   Vous pouvez également configurer le déclencheur de déploiement et le comportement en cas d’échec important dans les options du pipeline.

   ![](assets/non-prod-pipe1.png)

1. Cliquez sur **Enregistrer** pour afficher le pipeline sur la carte de l’écran d’accueil avec trois actions, comme illustré ci-dessous :

   ![](assets/configure-pipeline8.png)

   * **Modifier** : permet de modifier les paramètres du pipeline.
   * **Compilation** : permet d’accéder à la page d’exécution, à partir de laquelle le pipeline peut être exécuté.
   * **Gérer Git** : permet à l’utilisateur d’obtenir les informations nécessaires pour accéder au référentiel Git de Cloud Manager.

## Étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous devez déployer votre code.

Pour plus d’informations, consultez [Déploiement de votre code](deploy-code.md).

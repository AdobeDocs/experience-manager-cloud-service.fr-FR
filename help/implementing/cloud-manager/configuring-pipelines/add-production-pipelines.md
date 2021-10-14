---
title: Ajout de pipelines de production
description: Ajout de pipelines de production
index: false
source-git-commit: 16e3280d7eaf53d8f944a60ec93b21c6676f0133
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 97%

---


# Création d’un pipeline de production {#create-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez au moins d’un environnement basé sur l’interface utilisateur de [!UICONTROL Cloud Manager], vous êtes prêt à configurer votre pipeline de déploiement.

Pour configurer le comportement et les préférences de votre pipeline, procédez comme suit :

1. Cliquez sur **Configurer un pipeline** pour configurer votre pipeline.

   ![](assets/set-up-pipeline1.png)

1. L’écran **Configurer un pipeline** s’affiche. Sélectionnez la branche, puis cliquez sur **Suivant**.

   ![](assets/setup-1.png)

1. Configurez vos options de déploiement.

   ![](assets/setup-pipeline.png)

   Vous pouvez définir le déclencheur pour démarrer le pipeline :

   * **Manuel** : l’utilisation de l’interface lance le pipeline manuellement.
   * **Lors des modifications Git** : démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Même si vous sélectionnez cette option, vous pouvez toujours démarrer le pipeline manuellement.

   Lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

   Cela s’avère utile pour les clients qui souhaitent davantage de processus automatisés. Les options disponibles sont les suivantes :

   * **Demander à chaque fois** : il s’agit du paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
   * **Annuler immédiatement** : si cette option est sélectionnée, le pipeline sera annulé chaque fois qu’un échec important se produira. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Approuver immédiatement** : si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.


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


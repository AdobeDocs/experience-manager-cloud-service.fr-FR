---
title: Ajout d’un pipeline de production
description: Découvrez comment ajouter un pipeline de production pour créer et déployer votre code dans les environnements de production.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '1314'
ht-degree: 39%

---


# Ajout d’un pipeline de production {#configure-production-pipeline}

Découvrez comment configurer des pipelines de production pour créer et déployer votre code dans des environnements de production. Un pipeline de production déploie d’abord le code dans l’environnement intermédiaire. Une fois approuvé, le même code est déployé dans l’environnement de production.

Un utilisateur doit disposer du rôle **[Responsable de déploiement](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer les pipelines de production.

>[!NOTE]
>
>Un pipeline de production ne peut pas être configuré tant que les événements suivants ne se sont pas produits :
>
>* Le programme est alors créé.
>* Le référentiel Git comporte au moins une branche.
>* Les environnements de production et d’évaluation sont créés.

Avant de commencer à déployer votre code, configurez les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez [modifier les paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajouter un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant l’interface utilisateur de [!UICONTROL Cloud Manager], vous êtes prêt à ajouter un pipeline production en suivant ces étapes.

>[!TIP]
>
>Avant de configurer un pipeline frontal, consultez le [Parcours de création de site rapide AEM](/help/journey-sites/quick-site/overview.md) pour obtenir un guide de bout en bout à l’aide de l’outil de création de site rapide AEM simple d’utilisation. Ce parcours peut vous aider à rationaliser le développement frontal de votre site AEM, ce qui vous permet de personnaliser rapidement votre site sans AEM connaissances principales.

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme** et cliquez sur **Ajouter** pour sélectionner **Ajouter un pipeline de production**.

   ![Carte Pipelines dans l’aperçu du Gestionnaire de programmes](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. La boîte de dialogue **Ajouter un pipeline de production** s’affiche. Fournissez une **Nom du pipeline** pour identifier votre pipeline avec les options suivantes. Cliquez sur **Continuer**.

   **Déclencheur de déploiement** - Vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

   * **Manuel** - Démarrez le pipeline manuellement.
   * **Lors des modifications Git** - Démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

   **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le **responsable de déploiement** peut définir le comportement du pipeline lorsqu’un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

   * **Demander à chaque fois** - Paramètre par défaut. Cela nécessite une intervention manuelle en cas d&#39;échec important.
   * **Défaillance immédiate** – Si cette option est sélectionnée, le pipeline sera interrompu dès qu’une défaillance importante aura lieu. Ce processus émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** - Si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Ce processus émule essentiellement l’approbation manuelle de chaque échec par un utilisateur.

   ![Configuration du pipeline de production](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Dans l’onglet **Code Source**, sélectionnez le type de code que le pipeline doit traiter.

   * **[Configuration d’un pipeline de code de pile complet](#full-stack-code)**
   * **[Configuration d’un pipeline de déploiement ciblé](#targeted-deployment)**

Voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour plus d’informations sur les types de pipelines.

Les étapes de création de votre pipeline de production varient en fonction du type de code source sélectionné. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de terminer la configuration de votre pipeline.

### Configuration d’un pipeline de code de pile complet {#full-stack-code}

Un pipeline de code à pile complète déploie simultanément les versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher.

>[!NOTE]
>
>Si un pipeline de code full stack existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

**Pour configurer un pipeline de code de pile complet :**

1. Dans l’onglet **Code Source** , définissez les options suivantes.

   * **Repository** - Définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir [Ajouter et gérer des référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Définit à partir de quelle branche le pipeline sélectionné doit récupérer le code.
Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouve les branches correspondantes pour vous aider à sélectionner.
   * **Ignorer la configuration de niveau Web** – Lorsque cette case est cochée, le pipeline ne déploie pas votre configuration de niveau web.
   * **Pause avant le déploiement en production** - Met le pipeline en pause avant le déploiement en production.
   * **Planifié** - Permet à l’utilisateur d’activer le déploiement en production planifié.

   ![Code full stack](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Cliquez sur **Continuer** pour accéder à l’onglet **contrôle de l’expérience** qui vous permet de définir les chemins qui doivent toujours être inclus dans le contrôle de l’expérience.

   ![Ajout d’un contrôle de l’expérience](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Indiquez les chemins à inclure dans le contrôle de l’expérience.

   * Voir [Test d’audit d’expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md#configuration) pour plus d’informations.

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

Lorsque le pipeline s’exécute, les chemins configurés pour le contrôle de l’expérience sont envoyés et évalués en fonction des performances, de l’accessibilité, de l’optimisation pour les moteurs de recherche, des bonnes pratiques et des tests du PWA. Pour plus d’informations, voir [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md).

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) dans le carte **Pipelines** dans la page **Aperçu du programme**.

### Configuration d’un pipeline de déploiement ciblé {#targeted-deployment}

Un déploiement ciblé déploie le code uniquement pour les parties sélectionnées de votre application AEM. Dans un tel déploiement, vous pouvez choisir d’**inclure** l’un des types de code suivants :

* **Config** - Configurez les paramètres de différentes fonctionnalités de votre environnement AEM.
   * Voir [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md) pour obtenir la liste des configurations prises en charge, notamment le transfert de journaux, les tâches de maintenance liées à la purge et diverses configurations du réseau de diffusion de contenu, et pour les gérer dans votre référentiel afin qu’elles soient déployées correctement.
   * Lors de l’exécution d’un pipeline de déploiement ciblé, les configurations sont déployées, à condition qu’elles aient été enregistrées dans l’environnement, le référentiel et la branche définis dans le pipeline.
   * À tout moment, il ne peut y avoir qu’un seul pipeline de configuration par environnement.
* **Code front-end** - Configurez JavaScript et CSS pour le front-end de votre application AEM.
   * Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.
   * Consultez le document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour connaître le fonctionnement de ce processus ainsi que certaines considérations à prendre en compte pour en tirer le meilleur parti.
* **Configuration de niveau web** - Configurez les propriétés Dispatcher pour stocker, traiter et diffuser des pages web au client.
   * Pour plus d’informations, consultez le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) .
   * Si un pipeline de code de niveau web existe pour l’environnement sélectionné, cette sélection est désactivée.
   * Si vous créez un pipeline de configuration de niveau web pour un environnement avec un pipeline de pile complète existant, la configuration de niveau web dans le pipeline de pile complète est ignorée. Cette modification affecte uniquement la configuration de niveau web dans cet environnement.

>[!NOTE]
>
>Les pipelines de niveau web et de configuration ne sont pas pris en charge pour les référentiels privés. Voir [Ajout de référentiels privés dans Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) pour plus d’informations et la liste complète des limites.

**Pour configurer un pipeline de déploiement ciblé :**

1. Choisissez le type de déploiement dont vous avez besoin.

![Options de déploiement ciblées](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

1. Définissez les **environnements de déploiement éligibles**.

   * Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.

1. Sous **Source Code**, définissez les options suivantes :

   * **Référentiel** – Cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Consultez [Ajout et gestion de référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** – Cette option définit à partir de quelle branche le pipeline sélectionné doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ. Elle trouve les branches correspondantes que vous pouvez sélectionner.
   * **Emplacement du code** - Cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
   * **Mettre en pause avant le déploiement en production** - Cette option met le pipeline en pause avant son déploiement en production.
   * **Planifié** - Permet à l’utilisateur d’activer le déploiement en production planifié. Disponible uniquement pour les déploiements ciblés de niveau web.

   ![Config pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) sur la carte **Pipelines** sur la page **Aperçu du programme**.

## Ignorer les modules Dispatcher {#skip-dispatcher-packages}

Pour créer des modules Dispatcher dans votre pipeline sans les publier pour créer du stockage, vous pouvez désactiver l’option de publication. Cela peut contribuer à réduire le temps d’exécution du pipeline.

La configuration suivante permettant de désactiver la publication des packages du Dispatcher doit être ajoutée via le fichier `pom.xml` de votre projet. Une variable d’environnement sert d’indicateur que vous définissez dans le conteneur de génération Cloud Manager pour déterminer quand ignorer les modules Dispatcher.

```xml
<profile>
  <id>only-include-dispatcher-when-it-isnt-ignored</id>
  <activation>
    <property>
      <name>env.IGNORE_DISPATCHER_PACKAGES</name>
      <value>!true</value>
    </property>
  </activation>
  <modules>
    <module>dispatcher</module>
  </modules>
</profile>
```

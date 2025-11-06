---
title: Ajout d’un pipeline de production
description: Découvrez comment ajouter un pipeline de production pour créer et déployer votre code dans les environnements de production.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 35%

---


# Ajout d’un pipeline de production {#configure-production-pipeline}

Découvrez comment configurer des pipelines de production pour créer et déployer votre code dans les environnements de production. Un pipeline de production déploie le code d’abord dans l’environnement intermédiaire. Lors de la validation, il déploie le même code dans l’environnement de production.

Un utilisateur doit disposer du rôle **[Responsable de déploiement](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer les pipelines de production.

>[!NOTE]
>
>Un pipeline de production ne peut pas être configuré tant que les conditions suivantes ne sont pas réunies :
>
>* Le programme est créé.
>* Le référentiel Git comporte au moins une branche.
>* Les environnements de production et d’évaluation sont créés.

Avant de commencer à déployer votre code, configurez les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez [modifier les paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajouter un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez au moins d’un environnement basé sur l’interface utilisateur de [!UICONTROL Cloud Manager], vous êtes prêt à ajouter un pipeline de production en suivant ces étapes.

>[!TIP]
>
>Avant de configurer un pipeline front-end, consultez le [Parcours de création rapide de site d’AEM](/help/journey-sites/quick-site/overview.md) pour obtenir un guide complet à travers l’outil de création rapide de site d’AEM, facile à utiliser. Ce parcours peut vous aider à rationaliser le développement front-end de votre site AEM, ce qui vous permet de personnaliser rapidement votre site sans aucune connaissance du serveur principal AEM.

1. Connectez-vous à Cloud Manager sur [experiece.adobe.com](https://experience.adobe.com).
1. Dans la section **Accès rapide**, cliquez sur **Experience Manager**.
1. Dans le panneau de gauche, cliquez sur **Cloud Manager**.
1. Sélectionnez l’organisation de votre choix.
1. Sur la console **Mes programmes**, cliquez sur un programme.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à la vignette **Pipelines** à partir de la page **Aperçu du programme** et cliquez sur **Ajouter** pour sélectionner **Ajouter un pipeline de production**.

   ![Carte Pipelines dans l’aperçu du Gestionnaire de programmes](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. La boîte de dialogue **Ajouter un pipeline de production** s’affiche. Fournissez une **Nom du pipeline** pour identifier votre pipeline avec les options suivantes. Cliquez sur **Continuer**.

   **Déclencheur de déploiement** - Vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

   * **Manuel** - Démarrez le pipeline manuellement.
   * **Lors des modifications Git** - Démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

   **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le **responsable de déploiement** peut définir le comportement du pipeline lorsqu’un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

   * **Demander à chaque fois** - Paramètre par défaut. Il nécessite une intervention manuelle lors de toute défaillance importante.
   * **Défaillance immédiate** – Si cette option est sélectionnée, le pipeline sera interrompu dès qu’une défaillance importante aura lieu. Ce processus émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Ce processus émule essentiellement la validation manuelle de chaque échec par un utilisateur.

   ![Configuration du pipeline de production](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Dans l’onglet **Code Source**, sélectionnez le type de code que le pipeline doit traiter.

   * **[Configurer un pipeline de code full stack](#full-stack-code)**
   * **[Configuration d’un pipeline de déploiement ciblé](#targeted-deployment)**

Voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour plus d’informations sur les types de pipelines.

Les étapes de création de votre pipeline de production varient en fonction du type de code source que vous avez sélectionné. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de terminer la configuration de votre pipeline.

### Configuration d’un pipeline de code full stack {#full-stack-code}

Un pipeline de code full stack déploie simultanément des versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher.

>[!NOTE]
>
>Si un pipeline de code full stack existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

**Pour configurer un pipeline de code de pile complète, procédez comme suit**

1. Dans l&#39;onglet **Code Source**, définissez les options suivantes.

   * **Référentiel** - Définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir [Ajouter et gérer des référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Définit à partir de quelle branche le pipeline sélectionné doit récupérer le code.
Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouve les branches correspondantes pour vous aider à les sélectionner.
   * **Ignorer la configuration de niveau Web** – Lorsque cette case est cochée, le pipeline ne déploie pas votre configuration de niveau web.
   * **Mettre en pause avant le déploiement en production** - Met le pipeline en pause avant son déploiement en production.
   * **Planifié** - Permet à l’utilisateur d’activer le déploiement en production planifié.

   ![Code full stack](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Cliquez sur **Continuer** pour accéder à l’onglet **Audit d’expérience** qui vous permet de définir les chemins qui doivent toujours être inclus dans l’audit d’expérience.

   ![Ajout d’un audit d’expérience](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Indiquez les chemins à inclure dans le contrôle de l’expérience.

   * Voir [&#x200B; Tests de contrôle de l’expérience](/help/implementing/cloud-manager/reports/report-experience-audit.md#configuration) pour plus d’informations.

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

Lorsque le pipeline s’exécute, les chemins configurés pour le contrôle de l’expérience sont envoyés et évalués en fonction des tests de performance, d’accessibilité, d’optimisation du moteur de recherche, des bonnes pratiques et de PWA. Pour plus d’informations, voir [&#x200B; Comprendre les résultats du contrôle de l’expérience &#x200B;](/help/implementing/cloud-manager/reports/report-experience-audit.md).

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) dans le carte **Pipelines** dans la page **Aperçu du programme**.

### Configuration d’un pipeline de déploiement ciblé {#targeted-deployment}

Un déploiement ciblé déploie le code uniquement pour les parties sélectionnées de votre application AEM. Dans un tel déploiement, vous pouvez choisir d’**Inclure** l’un des types de code suivants :

* **Config** - Configurez les paramètres des différentes fonctionnalités de votre environnement AEM.
   * Consultez la section [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md) pour obtenir une liste des configurations prises en charge, qui incluent le transfert de journal, les tâches de maintenance liées à la purge et diverses configurations de réseau CDN, ainsi que pour les gérer dans votre référentiel afin qu’elles soient correctement déployées.
   * Lors de l’exécution d’un pipeline de déploiement ciblé, les configurations sont déployées, à condition qu’elles soient enregistrées dans l’environnement, le référentiel et la branche définis dans le pipeline.
   * À tout moment, il ne peut y avoir qu’un seul pipeline de configuration par environnement.
* **Configurer le pipeline de configuration Edge Delivery Services** - Les pipelines de configuration Edge Delivery ne disposent pas d’environnements de développement, d’évaluation et de production distincts. Dans AEM as a Cloud Service, les modifications passent par les niveaux de développement, d’évaluation et de production. En revanche, un pipeline de configuration Edge Delivery applique sa configuration directement à tous les domaines Edge Delivery Sites enregistrés dans Cloud Manager. Pour en savoir plus, voir [Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).
* **Code front-end** - Configurez JavaScript et CSS pour le front-end de votre application AEM.
   * Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.
   * Consultez le document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour connaître le fonctionnement de ce processus ainsi que certaines considérations à prendre en compte pour en tirer le meilleur parti.
* **Configuration de niveau web** - Configurez les propriétés Dispatcher pour stocker, traiter et diffuser des pages web au client.
   * Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) pour plus d’informations.
   * Si un pipeline de code de niveau web existe pour l’environnement sélectionné, cette sélection est désactivée.
   * Si vous créez un pipeline de configuration de niveau web pour un environnement avec un pipeline full stack existant, la configuration de niveau web dans le pipeline full stack est ignorée. Cette modification affecte uniquement la configuration de niveau web dans cet environnement.

>[!NOTE]
>
>Les pipelines de niveau web et de configuration ne sont pas pris en charge pour les référentiels privés. Voir [Ajout de référentiels privés dans Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) pour plus d’informations et la liste complète des limitations.

**Pour configurer un pipeline de déploiement ciblé, procédez comme suit**

1. Choisissez le type de déploiement dont vous avez besoin.

![Options de déploiement ciblé](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

1. Définissez l’**Environnements de déploiement éligibles**.

   * Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.

1. Sous **Code Source**, définissez les options suivantes :

   * **Référentiel** – Cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Consultez [Ajout et gestion de référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** – Cette option définit à partir de quelle branche le pipeline sélectionné doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ. Elle trouve les branches correspondantes que vous pouvez sélectionner.
   * **Emplacement du code** - Cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
   * **Mettre en pause avant le déploiement en production** - Cette option met le pipeline en pause avant son déploiement en production.
   * **Planifié** - Permet à l’utilisateur d’activer le déploiement en production planifié. Disponible uniquement pour les déploiements ciblés de niveau web.

   ![Configurer le pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) sur la carte **Pipelines** sur la page **Aperçu du programme**.

## Ignorer les packages Dispatcher {#skip-dispatcher-packages}

Pour créer des packages Dispatcher dans votre pipeline sans les publier pour créer du stockage, vous pouvez désactiver l’option de publication. Cela peut contribuer à réduire le temps d’exécution du pipeline.

La configuration suivante permettant de désactiver la publication des packages du Dispatcher doit être ajoutée via le fichier `pom.xml` de votre projet. Une variable d’environnement sert d’indicateur que vous définissez dans le conteneur de création Cloud Manager pour déterminer quand ignorer les packages Dispatcher.

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

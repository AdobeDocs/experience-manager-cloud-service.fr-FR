---
title: Configuration des pipelines de production
description: Découvrez comment configurer des pipelines de production pour créer et déployer votre code dans les environnements de production.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 77%

---


# Configuration d’un pipeline de production {#configure-production-pipeline}

Découvrez comment configurer des pipelines de production pour créer et déployer votre code dans les environnements de production. Un pipeline de production déploie le code d’abord dans l’environnement intermédiaire, puis, une fois approuvé, déploie le même code dans l’environnement de production.

Un utilisateur doit disposer du rôle **[Responsable de déploiement](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer les pipelines de production.

>[!NOTE]
>
>Un pipeline de production ne peut pas être configuré tant que la création du programme n’est pas terminée, qu’un référentiel git ne comporte pas au moins une branche et qu’un ensemble d’environnements de production et d’évaluation n’est pas créé.

Avant de commencer le déploiement du code, vous devez configurer les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez [modifier les paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajout d’un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant l’interface utilisateur de [!UICONTROL Cloud Manager], vous êtes prêt à ajouter un pipeline production en suivant ces étapes.

>[!TIP]
>
>Avant de configurer un pipeline front-end, voir [Parcours de création rapide d’un site](/help/journey-sites/quick-site/overview.md) pour une présentation complète de son exécution grâce à l’outil de création rapide de site d’AEM, particulièrement simple d’utilisation. Ce parcours vous aidera à rationaliser le développement front-end de votre site AEM et à personnaliser rapidement votre site sans aucune connaissance AEM du serveur principal.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** page et clic **Ajouter** pour sélectionner **Ajout d’un pipeline de production**.

   ![Carte Pipelines dans l’aperçu du Gestionnaire de programmes](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. La boîte de dialogue **Ajouter un pipeline de production** s’affiche. Fournissez une **Nom du pipeline** pour identifier votre pipeline avec les options suivantes. Cliquez sur **Continuer**.

   **Déclencheur de déploiement** - Vous disposez des options suivantes pour définir les déclencheurs de déploiement pour démarrer le pipeline.

   * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline.
   * **Lors des modifications Git** - cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

   **Comportement en cas d’échecs de mesure importants** - lors de la configuration ou de la modification du pipeline, le **responsable de déploiement** peut définir le comportement du pipeline lorsqu’un échec important est rencontré à l’un des points de contrôle qualité. Les options disponibles sont les suivantes :

   * **Demander à chaque fois** - il s’agit du paramètre par défaut qui nécessite une intervention manuelle pour tout échec important.
   * **Défaillance immédiate** : si cette option est sélectionnée, le pipeline est interrompu chaque fois qu’une défaillance importante a lieu. Il s’agit essentiellement d’imiter un utilisateur qui rejetterait manuellement chaque échec.
   * **Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuivra automatiquement chaque fois qu’une défaillance importante se produira. Il s’agit essentiellement d’émuler un utilisateur approuvant manuellement chaque échec.

   ![Configuration du pipeline de production](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Sur le **Code source** vous devez sélectionner le type de code que le pipeline doit traiter.

   * **[Code full stack](#full-stack-code)**
   * **[Déploiement ciblé](#targeted-deployment)**

Voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour plus d’informations sur les types de pipelines.

Les étapes de création de votre pipeline de production varient en fonction du type de code source sélectionné. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de terminer la configuration de votre pipeline.

### Code full stack {#full-stack-code}

Un pipeline de code full stack déploie simultanément des versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher.

>[!NOTE]
>
>Si un pipeline de code full stack existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline de production de code full stack, procédez comme suit.

1. Dans l’onglet **Code source**, vous devez définir les options suivantes.

   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Consultez le document [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** : cette option définit à partir de quelle branche le pipeline doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouvera les branches correspondantes pour vous aider à les sélectionner.
   * **Ignorer la configuration de niveau Web** – Lorsque cette case est cochée, le pipeline ne déploie pas votre configuration de niveau web.
   * **Mettre en pause avant le déploiement en production** - Cette option met le pipeline en pause avant son déploiement en production.
   * **Planifié** : cette option permet à l’utilisateur d’activer le déploiement en production planifié.

   ![Code full stack](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Cliquez sur **Continuer** pour accéder à l’onglet **contrôle de l’expérience** qui vous permet de définir les chemins qui doivent toujours être inclus dans le contrôle de l’expérience.

   ![Ajout d’un contrôle de l’expérience](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Indiquer une à inclure dans le contrôle de l’expérience.

   * Les chemins d’accès doivent commencer par `/`.
   * Par exemple, si vous souhaitez inclure `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, saisissez le chemin d’accès `/us/en/about-us.html`.

   ![Définition d’un chemin pour le contrôle de l’expérience](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

1. Cliquez sur **Ajouter une page** et le chemin est renseigné automatiquement avec l’adresse de votre environnement, puis ajouté à la table des chemins.

   ![Enregistrement du chemin d’accès dans la table](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

1. Continuez à ajouter des chemins selon vos besoins en répétant les deux étapes précédentes.

   * Vous pouvez ajouter 25 chemins au maximum.
   * Si vous ne définissez aucun chemin, la page d’accueil du site sera incluse par défaut dans l’audit de l’expérience.

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

Les chemins configurés pour l’audit de l’expérience sont soumis au service et évalués en fonction des tests de performances, d’accessibilité, d’optimisation du moteur de recherche (SEO), de bonnes pratiques et de PWA (application web progressive) lors de l’exécution du pipeline. Pour plus d’informations, voir [Compréhension des résultats de l’audit de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) dans le carte **Pipelines** dans la page **Aperçu du programme**.

### Déploiement ciblé {#targeted-deployment}

Un déploiement ciblé déploie le code uniquement pour les parties sélectionnées de votre application AEM. Dans un tel déploiement, vous pouvez choisir **Inclure** l’un des types de code suivants :

* **[Config](#config)** - Configurez les paramètres de votre environnement AEM, les tâches de maintenance, les règles CDN, etc.
   * Voir le document [Règles de filtre de trafic incluant des règles WAF](/help/security/traffic-filter-rules-including-waf.md) pour savoir comment gérer les configurations de votre référentiel afin qu’elles soient déployées correctement.
* **[Code front-end](#front-end-code)** - Configurez JavaScript et CSS pour le front-end de votre application AEM.
   * Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.
   * Consultez le document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour connaître le fonctionnement de ce processus ainsi que certaines considérations à prendre en compte pour en tirer le meilleur parti.
* **[Configuration du niveau web](#web-tier-config)** - Configurez les propriétés du dispatcher pour stocker, traiter et diffuser des pages web au client.

>[!NOTE]
>
>* Si un pipeline de code de niveau web existe pour l’environnement sélectionné, cette sélection est désactivée.
>* Si vous disposez déjà d’un pipeline full stack se déployant vers un environnement, la création d’un pipeline de configuration de niveau web pour le même environnement entraîne l’exclusion de la configuration de niveau web existante dans le pipeline full stack.
> * À tout moment, il ne peut y avoir qu’un seul pipeline de configuration par environnement.

Les étapes de création de votre pipeline de déploiement ciblé en production sont les mêmes une fois que vous avez choisi un type de déploiement.

1. Choisissez le type de déploiement dont vous avez besoin.

![Options de déploiement ciblées](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

1. Définissez la variable **Environnements de déploiement éligibles**.

   * Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.

1. Sous **Code source**, définissez les options suivantes :

   * **Référentiel** – Cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Consultez [Ajout et gestion de référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** – Cette option définit à partir de quelle branche le pipeline sélectionné doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ. Elle trouve les branches correspondantes que vous pouvez sélectionner.
   * **Emplacement du code** - Cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
   * **Mettre en pause avant le déploiement en production** - Cette option met le pipeline en pause avant son déploiement en production.
   * **Planifié** : cette option permet à l’utilisateur d’activer le déploiement en production planifié. Disponible uniquement pour les déploiements ciblés de niveau web.

   ![Configuration du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) sur la carte **Pipelines** sur la page **Aperçu du programme**.

Lors de l’exécution d’un pipeline de déploiement ciblé, les configurations [telles que les configurations WAF ;](/help/security/traffic-filter-rules-including-waf.md) seront déployés, à condition qu’ils soient enregistrés dans l’environnement, le référentiel et la branche que vous avez définis dans le pipeline.

## Ignorer les packages du Dispatcher {#skip-dispatcher-packages}

Si vous souhaitez que les packages du Dispatcher soient créés dans le cadre de votre pipeline, mais que vous ne souhaitez pas qu’ils soient publiés pour créer du stockage, vous pouvez désactiver leur publication, ce qui peut réduire la durée d’exécution du pipeline.

La configuration suivante permettant de désactiver la publication des packages de Dispatcher doit être ajoutée via votre fichier `pom.xml` de projet. Elle est basée sur une variable d’environnement, qui sert d’indicateur que vous pouvez définir dans le conteneur de génération de Cloud Manager pour définir quand les packages du dispatcher doivent être ignorés.

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

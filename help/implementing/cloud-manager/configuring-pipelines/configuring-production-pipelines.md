---
title: Configuration des pipelines de production
description: Découvrez comment configurer des pipelines de production pour créer et déployer votre code dans les environnements de production.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
source-git-commit: 94e37ae6aef64ec61e633e4c034ceefe5e75c7c8
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 29%

---

# Configuration d’un pipeline de production {#configure-production-pipeline}

Découvrez comment configurer des pipelines de production pour créer et déployer votre code dans les environnements de production. Un pipeline de production déploie le code d’abord dans l’environnement d’évaluation, puis, une fois approuvé, déploie le même code dans l’environnement de production.

Un utilisateur doit disposer de la variable **[Responsable de déploiement](/help/onboarding/learn-concepts/cloud-manager-introduction.md#role-based-permissions)** rôle pour configurer les pipelines de production.

>[!NOTE]
>
>Un pipeline de production ne peut pas être configuré tant que la création du programme n’est pas terminée, qu’un référentiel git ne comporte pas au moins une branche et qu’un ensemble d’environnements de production et d’évaluation n’est pas créé.

Avant de commencer le déploiement du code, vous devez configurer les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez [modification des paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajouter un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant la variable [!UICONTROL Cloud Manager] Dans l’interface utilisateur, vous êtes prêt à ajouter un pipeline de production en procédant comme suit.

>[!TIP]
>
>Avant de configurer un pipeline front-end, reportez-vous à la section [parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) pour un guide de bout en bout grâce à l’outil de création rapide de site d’AEM simple d’utilisation. Ce parcours vous aidera à rationaliser le développement frontal de votre site AEM, ce qui vous permet de personnaliser rapidement votre site sans AEM connaissances principales.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur **Ajouter** pour sélectionner **Ajout d’un pipeline de production**.

   ![La carte Pipelines dans la présentation du Gestionnaire de programmes](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Le **Ajout d’un pipeline de production** s’affiche. Fournissez une **Nom du pipeline** pour identifier votre pipeline avec les options suivantes. Cliquez sur **Continuer**.

   **Déclencheur de déploiement** - Vous disposez des options suivantes lors de la définition des déclencheurs de déploiement pour démarrer le pipeline.

   * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline.
   * **Lors des modifications Git** - cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

   **Comportement en cas d’échecs de mesure importants****- lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline lorsqu&#39;un échec important est rencontré à l’un des points de contrôle qualité.** Les options disponibles sont les suivantes :

   * **Demander à chaque fois** - il s’agit du paramètre par défaut qui nécessite une intervention manuelle pour tout échec important.
   * **Défaillance immédiate** : si cette option est sélectionnée, le pipeline sera interrompu chaque fois qu’une défaillance importante aura lieu. Il s’agit essentiellement d’imiter un utilisateur qui rejetterait manuellement chaque échec.
   * **Continuer immédiatement** - si cette option est sélectionnée, le pipeline se poursuivra automatiquement chaque fois qu’une défaillance importante se produira. Il s’agit essentiellement d’émuler un utilisateur approuvant manuellement chaque échec.

   ![Configuration du pipeline de production](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Sur le **Code source** vous devez définir où le pipeline doit récupérer son code et quel type de code il est.

   * **[Code frontal](#front-end-code)**
   * **[Code de pile complète](#full-stack-code)**
   * **[Configuration de la couche web](#web-tier-config)**

Les étapes de création de votre pipeline de production varient en fonction de l’option pour **Code source** vous avez sélectionné. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de terminer la configuration de votre pipeline.

### Code frontal {#front-end-code}

Un pipeline de code frontal déploie les versions de code frontal contenant une ou plusieurs applications d’interface utilisateur côté client. Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour plus d’informations sur ce type de pipeline.

Pour terminer la configuration du pipeline de production de code frontal, procédez comme suit.

1. Sur le **Code source** , vous devez définir les options suivantes.

   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
   >[!TIP]
   > 
   >Voir le document [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouvera les branches correspondantes pour vous aider à sélectionner.
   * **Emplacement du code** - cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
   * **Mettre en pause avant le déploiement en production** - Cette option met le pipeline en pause avant son déploiement en production.

   ![Code frontal](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-frontend.png)

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

Le pipeline est enregistré et vous pouvez maintenant [gestion des pipelines](managing-pipelines.md) sur le **Pipelines** sur la carte **Aperçu du programme** page.

### Code de pile complète {#full-stack-code}

Un pipeline de code à pile complète déploie simultanément des builds de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher. Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) pour plus d’informations sur ce type de pipeline.

>[!NOTE]
>
>Si un pipeline de code à pile complète existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline de production de code de pile complète, procédez comme suit.

1. Sur le **Code source** , vous devez définir les options suivantes.

   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
   >[!TIP]
   > 
   >Voir le document [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouvera les branches correspondantes pour vous aider à sélectionner.
   * **Emplacement du code** - cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
   * **Mettre en pause avant le déploiement en production** - Cette option met le pipeline en pause avant son déploiement en production.
   * **Planifié** : cette option permet à l’utilisateur d’activer le déploiement en production planifié.

   ![Code de pile complet](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Cliquez sur **Continuer** pour accéder au **Audit de l’expérience** vous permettant de définir les chemins qui doivent toujours être inclus dans le contrôle de l’expérience.

   ![Ajout d’un audit d’expérience](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Indiquer une à inclure dans le contrôle de l’expérience.

   * Les chemins de page doivent commencer par `/`.
   * Par exemple, si vous souhaitez inclure `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, saisissez le chemin d’accès. `/us/en/about-us.html`.

   ![Définition d’un chemin pour le contrôle de l’expérience](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

1. Cliquez sur **Ajouter une page** et le chemin sera renseigné automatiquement avec l’adresse de votre environnement et ajouté à la table des chemins.

   ![Enregistrement du chemin d’accès au tableau](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

1. Continuez à ajouter des chemins selon vos besoins en répétant les deux étapes précédentes.

   * Vous pouvez ajouter 25 chemins au maximum.
   * Si vous ne définissez aucun chemin, la page d’accueil du site sera incluse par défaut dans le contrôle de l’expérience.

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

Les chemins configurés pour le contrôle de l’expérience seront soumis au service et évalués en fonction des tests de performances, d’accessibilité, d’optimisation du moteur de recherche (SEO), de bonnes pratiques et de PWA (application web progressive) lors de l’exécution du pipeline. Pour plus d’informations, voir [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

Le pipeline est enregistré et vous pouvez maintenant [gestion des pipelines](managing-pipelines.md) sur le **Pipelines** sur la carte **Aperçu du programme** page.

### Configuration de la couche web {#web-tier-config}

Un pipeline de configuration de niveau web déploie les configurations HTTPD/Dispatcher. Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) pour plus d’informations sur ce type de pipeline.

Pour terminer la configuration du pipeline de production de code de pile complète, procédez comme suit.

1. Sur le **Code source** , vous devez définir les options suivantes.

   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
   >[!TIP]
   > 
   >Voir le document [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouvera les branches correspondantes pour vous aider à sélectionner.
   * **Emplacement du code** - cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
      * Pour les pipelines de configuration de niveau web, il s’agit généralement du chemin contenant `conf.d`, `conf.dispatcher.d`, et `opt-in` répertoires.
      * Par exemple, si la structure du projet a été générée à partir de la variable [AEM Archétype de projet,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) le chemin serait `/dispatcher/src`.
   * **Mettre en pause avant le déploiement en production** - Cette option met le pipeline en pause avant son déploiement en production.
   * **Planifié** : cette option permet à l’utilisateur d’activer le déploiement en production planifié.

   ![Code de niveau web](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-webtier.png)

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

>[!NOTE]
>
>Si vous disposez déjà d’un pipeline de pile complète se déployant vers un environnement, la création d’un pipeline de configuration de niveau web pour le même environnement entraîne l’exclusion de la configuration de niveau web existante dans le pipeline de pile complète.

Le pipeline est enregistré et vous pouvez maintenant [gestion des pipelines](managing-pipelines.md) sur le **Pipelines** sur la carte **Aperçu du programme** page.

## Ignorer les modules de Dispatcher {#skip-dispatcher-packages}

Si vous souhaitez que les packages du dispatcher soient créés dans le cadre de votre pipeline, mais que vous ne souhaitez pas qu’ils soient publiés pour créer du stockage, vous pouvez désactiver leur publication, ce qui peut réduire la durée d’exécution du pipeline.

La configuration suivante pour désactiver la publication des packages Dispatcher doit être ajoutée via votre projet. `pom.xml` fichier . Elle est basée sur une variable d’environnement, qui sert d’indicateur que vous pouvez définir dans le conteneur de génération de Cloud Manager pour définir quand les modules du dispatcher doivent être ignorés.

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

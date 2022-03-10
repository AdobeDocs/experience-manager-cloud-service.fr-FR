---
title: Configurer des pipelines hors production
description: Découvrez comment configurer des pipelines hors production afin de tester la qualité de votre code avant le déploiement dans les environnements de production.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
source-git-commit: 428bba062fcfb44ebfbbf3c1d05ce1a4634fb429
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 33%

---

# Configurer des pipelines hors production {#configuring-non-production-pipelines}

Découvrez comment configurer des pipelines hors production afin de tester la qualité de votre code avant le déploiement dans les environnements de production.

## Pipelines hors production {#non-production-pipelines}

En complément de [pipelines de production](#configuring-production-pipelines.md) qui se déploie sur les environnements intermédiaires et de production, vous pouvez également configurer des pipelines hors production pour valider votre code.

Il existe deux types de pipelines hors production :

* **Pipelines de qualité du code** - ceux-ci exécutent des analyses de qualité du code sur le code dans une branche Git et exécutent les étapes de création et de qualité du code.
* **Pipelines de déploiement** - outre l’exécution des étapes de création et de qualité du code, telles que les pipelines de qualité du code, ces pipelines déploient le code dans un environnement hors production.

>[!NOTE]
>
>Vous pouvez [modification des paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajout d’un nouveau pipeline hors production {#adding-non-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant l’interface utilisateur de Cloud Manager, vous êtes prêt à ajouter un pipeline hors production en suivant ces étapes.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** depuis l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Sur le **Configuration** de l’onglet **Ajout d’un pipeline hors production** , sélectionnez le type de pipeline hors production que vous souhaitez ajouter, au choix : **Pipeline de qualité du code** ou **Pipeline de déploiement**.

   ![Boîte de dialogue Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Fournissez une **Nom du pipeline hors production** pour identifier votre pipeline avec les informations supplémentaires suivantes.

   * **Déclencheur de déploiement** - Vous disposez des options suivantes lors de la définition des déclencheurs de déploiement pour démarrer le pipeline.

      * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline.
      * **Lors des modifications Git** - cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

1. Cliquez sur **Continuer**.

1. Sur le **Code source** de l’onglet **Ajout d’un pipeline hors production** , vous devez sélectionner le type de code que le pipeline doit traiter.

   * **[Code frontal](#front-end-code)**
   * **[Code de pile complète](#full-stack-code)**
   * **[Configuration de la couche web](#web-tier-config)**

Les étapes pour terminer la création de votre pipeline hors production varient en fonction de l’option pour **Code source** vous avez sélectionné. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de terminer la configuration de votre pipeline.

### Code frontal {#front-end-code}

Un pipeline de code frontal déploie les versions de code frontal contenant une ou plusieurs applications d’interface utilisateur côté client. Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour plus d’informations sur ce type de pipeline.

Pour terminer la configuration du pipeline de code frontal hors production, procédez comme suit.

1. Sur le **Code source** , vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir le document [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
   * **Emplacement du code** - cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.

   ![Pipeline front-end](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-front-end.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gestion des pipelines](managing-pipelines.md) sur le **Pipelines** sur la carte **Aperçu du programme** page.

### Code de pile complète {#full-stack-code}

Un pipeline de code à pile complète déploie simultanément des builds de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher. Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) pour plus d’informations sur ce type de pipeline.

>[!NOTE]
>
>Si un pipeline de code à pile complète existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline de code de pile complète hors production, procédez comme suit.

1. Sur le **Code source** , vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir le document [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
   * **Ignorer la configuration de couche web** -

   ![Pipeline à pile complète](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gestion des pipelines](managing-pipelines.md) sur le **Pipelines** sur la carte **Aperçu du programme** page.

### Configuration de la couche web {#web-tier-config}

Un pipeline de configuration de niveau web déploie les configurations HTTPD/Dispatcher. Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) pour plus d’informations sur ce type de pipeline.

>[!NOTE]
>
>Si un pipeline de code de niveau web existe déjà pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline de code hors production de niveau web, procédez comme suit.

1. Sur le **Code source** , vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir le document [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
   * **Emplacement du code** - cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
      * Pour les pipelines de configuration de niveau web, il s’agit généralement du chemin contenant `conf.d`, `conf.dispatcher.d`, et `opt-in` répertoires.
      * Par exemple, si la structure du projet a été générée à partir de la variable [AEM Archétype de projet,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) le chemin serait `/dispatcher/src`.

   ![Pipeline de niveau web](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-web-tier.png)

1. Cliquez sur **Enregistrer**.

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

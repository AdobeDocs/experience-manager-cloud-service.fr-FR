---
title: Configuration de pipelines hors production
description: Découvrez comment configurer des pipelines hors production pour tester la qualité de votre code avant le déploiement dans les environnements de production.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1356'
ht-degree: 57%

---


# Configurer des pipelines hors production {#configuring-non-production-pipelines}

Découvrez comment configurer des pipelines hors production pour tester la qualité de votre code avant le déploiement dans les environnements de production.

## Pipelines hors production {#non-production-pipelines}

Outre les [pipelines de production](#configuring-production-pipelines.md) qui se déploient sur les environnements d’évaluation et de production, vous pouvez également configurer des pipelines hors production pour valider votre code.

Il existe deux types de pipelines hors production :

* **Pipelines de qualité du code** - ceux-ci exécutent des analyses de qualité du code sur le code dans une branche Git et exécutent les étapes de création et de qualité du code.
* **Pipelines de déploiement** - outre l’exécution des étapes de création et de qualité du code, telles que les pipelines de qualité du code, ces pipelines déploient le code dans un environnement hors production.

>[!NOTE]
>
>Vous pouvez [modifier les paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajout d’un nouveau pipeline hors production {#adding-non-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez d’au moins un environnement utilisant l’interface utilisateur de Cloud Manager, vous êtes prêt à ajouter un pipeline hors production en suivant ces étapes.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** depuis l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Sous l’onglet **Configuration** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez le type de pipeline hors production que vous souhaitez ajouter.

   * **Pipeline de qualité du code** – Créez un pipeline qui génère votre code, exécute des tests unitaires et évalue la qualité du code, mais ne le déploie PAS.
   * **Pipeline de déploiement** – Créez un pipeline qui génère votre code, exécute des tests unitaires, évalue la qualité du code et le déploie dans un environnement.

   ![Boîte de dialogue Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Fournissez un **Nom du pipeline hors production** pour identifier votre pipeline avec les informations supplémentaires suivantes.

   * **Déclencheur de déploiement** - vous disposez des options suivantes au moment de définir les déclencheurs de déploiement pour démarrer le pipeline.

      * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline.
      * **Lors des modifications Git** - Cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

1. Si vous choisissez de créer une **Pipeline de déploiement**, vous devez également définir la variable **Comportement des échecs de mesure importants**.

   * **Demander à chaque fois** - Ce comportement est le paramètre par défaut qui nécessite une intervention manuelle en cas d’échec important.
   * **Échec immédiat** - Si cette option est sélectionnée, le pipeline est annulé chaque fois qu’un échec important se produit. Il s’agit essentiellement d’émuler un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** - Si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Il s’agit essentiellement d’émuler un utilisateur approuvant manuellement chaque échec.

1. Cliquez sur **Continuer**.

1. Dans l’onglet **Code source** de la boîte de dialogue **Ajouter un pipeline hors production**, vous devez sélectionner le type de code que le pipeline doit traiter.

   * **[Code front-end](#front-end-code)**
   * **[Code full stack](#full-stack-code)**
   * **[Configuration de la couche web](#web-tier-config)**

Les étapes pour terminer la création de votre pipeline hors production varient en fonction de l’option que vous sélectionnez pour le **Code source**. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de pouvoir terminer la configuration de votre pipeline.

### Code front-end {#front-end-code}

Un pipeline de code front-end déploie les versions de code front-end contenant une ou plusieurs applications d’interface utilisateur côté client. Consultez le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour plus d’informations sur ce type de pipeline.

Pour terminer la configuration du pipeline hors production de code front-end, procédez comme suit.

1. Dans l’onglet **Code source**, vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** - Cette option définit à partir de quel référentiel git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) vous pouvez ainsi apprendre à ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Cette option définit à partir de quelle branche du pipeline sélectionné doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ. Il trouve les branches correspondantes que vous pouvez sélectionner.
   * **Emplacement du code** - Cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.

   ![Pipeline front-end](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-front-end.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) sur la carte **Pipelines** sur la page **Aperçu du programme**.

### Code full stack {#full-stack-code}

Un pipeline de code full stack déploie simultanément des versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher. Consultez le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) pour plus d’informations sur ce type de pipeline.

>[!NOTE]
>
>S’il existe un pipeline de code à pile complète pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline hors production de code full stack, procédez comme suit.

1. Dans l’onglet **Code source**, vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** - Cette option définit à partir de quel référentiel git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) vous pouvez ainsi apprendre à ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Cette option définit à partir de quelle branche du pipeline sélectionné doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ. Vous pouvez ainsi trouver les branches correspondantes que vous pouvez sélectionner.
   * **Ignorer la configuration de niveau Web** - Lorsque cette case est cochée, le pipeline ne déploie pas votre configuration de niveau web.

   * **Pipeline** – Si votre pipeline est un pipeline de déploiement, vous pouvez choisir d’exécuter une phase de test. Cochez les options que vous souhaitez activer dans cette phase. Si aucune des options n’est sélectionnée, la phase de test n’est pas affichée pendant l’exécution du pipeline.

      * **Tests fonctionnels du produit** – Exécutez des [tests fonctionnels du produit](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) dans l’environnement de développement.
      * **Tests fonctionnels personnalisés** – Exécutez des [tests fonctionnels personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) dans l’environnement de développement.
      * **Tests de l’interface utilisateur personnalisée** – Exécutez des [tests de l’interface utilisateur personnalisée](/help/implementing/cloud-manager/ui-testing.md) pour les applications personnalisées.

   ![Pipeline full stack](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) sur la carte **Pipelines** sur la page **Aperçu du programme**.

### Configuration de la couche web {#web-tier-config}

Un pipeline de configuration de niveau web déploie les configurations HTTPD/Dispatcher. Voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) pour plus d’informations sur ce type de pipeline.

>[!NOTE]
>
>S’il existe un pipeline de code de niveau web pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline hors production de code de la couche web, procédez comme suit.

1. Dans l’onglet **Code source**, vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** - Cette option définit à partir de quel référentiel git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Voir [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) vous pouvez ainsi apprendre à ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Cette option définit à partir de quelle branche du pipeline sélectionné doit récupérer le code.
   * **Emplacement du code** - Cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.
      * Pour les pipelines de configuration de niveau web, ce chemin d’accès contient généralement `conf.d`, `conf.dispatcher.d`, et `opt-in` répertoires.
      * Par exemple, si la structure du projet a été générée à partir de l’[Archétype de projet AEM,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) le chemin serait `/dispatcher/src`.

   ![Pipeline de couche web](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-web-tier.png)

1. Cliquez sur **Enregistrer**.

>[!NOTE]
>
>Si vous disposez déjà d’un pipeline full stack se déployant vers un environnement, la création d’un pipeline de configuration de niveau web pour le même environnement entraîne l’exclusion de la configuration de niveau web existante dans le pipeline full stack.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) dans la carte **Pipelines** dans la page **Aperçu du programme**.

## Développer des sites avec le pipeline front-end {#developing-with-front-end-pipeline}

Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.

Voir le document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour connaître le fonctionnement de ce processus, ainsi que quelques considérations à prendre en compte pour tirer pleinement parti de ce processus.

## Ignorer les packages du Dispatcher {#skip-dispatcher-packages}

Si vous souhaitez que les modules de Dispatcher soient créés dans le cadre de votre pipeline, mais ne souhaitez pas qu’ils soient publiés pour créer du stockage, vous pouvez désactiver leur publication, ce qui peut réduire la durée d’exécution du pipeline.

La configuration suivante pour désactiver la publication des packages de Dispatcher doit être ajoutée via votre projet. `pom.xml` fichier . Elle est basée sur une variable d’environnement, qui sert d’indicateur que vous pouvez définir dans le conteneur de génération Cloud Manager pour définir quand les modules de Dispatcher doivent être ignorés.

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

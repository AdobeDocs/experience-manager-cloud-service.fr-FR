---
title: Ajout d’un pipeline hors production
description: Découvrez comment ajouter un pipeline hors production pour tester la qualité de votre code avant le déploiement dans les environnements de production.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 500e1b78fb9688601848fc17f312fc23be83bcb0
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 71%

---


# Ajouter un pipeline hors production {#configuring-non-production-pipelines}

Découvrez comment configurer des pipelines hors production afin de tester la qualité de votre code avant le déploiement dans des environnements de production.

Un utilisateur doit disposer du rôle **[Deployment Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer des pipelines hors production.

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

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à la carte **Pipelines** depuis l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajouter un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Sous l’onglet **Configuration** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez le type de pipeline hors production que vous souhaitez ajouter.

   * **Pipeline de qualité du code** – Créez un pipeline qui génère votre code, exécute des tests unitaires et évalue la qualité du code, mais ne le déploie PAS.
   * **Pipeline de déploiement** – Créez un pipeline qui génère votre code, exécute des tests unitaires, évalue la qualité du code et le déploie dans un environnement.

   ![Boîte de dialogue Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Fournissez un **Nom du pipeline hors production** pour identifier votre pipeline avec les informations supplémentaires suivantes.

   * **Déclencheur de déploiement** - vous disposez des options suivantes au moment de définir les déclencheurs de déploiement pour démarrer le pipeline.

      * **Manuel** - utilisez cette option pour démarrer manuellement le pipeline.
      * **Lors des modifications Git** – Cette option démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

1. Si vous choisissez de créer un **pipeline de déploiement**, vous devez également définir le **comportement des échecs de mesure importants**.

   * **Demander à chaque fois** – Ce comportement est le paramètre par défaut qui nécessite une intervention manuelle lors de tout échec important.
   * **Défaillance immédiate** – Si cette option est sélectionnée, le pipeline sera interrompu dès qu’une défaillance importante aura lieu. Il s’agit essentiellement de l’émulation d’un utilisateur ou d’une utilisatrice qui rejette manuellement chaque échec.
   * **Continuer immédiatement** – Si cette option est sélectionnée, le pipeline se poursuivra automatiquement chaque fois qu’une défaillance importante se produira. Il s’agit essentiellement de l’émulation d’un utilisateur ou d’une utilisatrice qui approuve manuellement chaque échec.

1. Cliquez sur **Continuer**.

1. Dans l’onglet **Code source** de la boîte de dialogue **Ajouter un pipeline hors production**, vous devez sélectionner le type de code que le pipeline doit traiter.

   * **[Code full stack](#full-stack-code)**
   * **[Déploiement ciblé](#targeted-deployment)**

Voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour plus d’informations sur les types de pipelines.

Les étapes de création de votre pipeline hors production varient en fonction du type de code source sélectionné. Suivez les liens ci-dessus pour accéder à la section suivante de ce document afin de terminer la configuration de votre pipeline.

### Code full stack {#full-stack-code}

Un pipeline de code à pile complète déploie simultanément les versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher.

>[!NOTE]
>
>Si un pipeline de code full stack existe pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline hors production de code full stack, procédez comme suit.

1. Dans l’onglet **Code source**, vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** – Cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.

   >[!TIP]
   > 
   >Consultez [Ajout et gestion de référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** – Cette option définit à partir de quelle branche le pipeline sélectionné doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ. Vous pouvez ainsi trouver les branches correspondantes que vous pouvez sélectionner.
   * **Ignorer la configuration de niveau Web** – Lorsque cette case est cochée, le pipeline ne déploie pas votre configuration de niveau web.
   * **Pipeline** – Si votre pipeline est un pipeline de déploiement, vous pouvez choisir d’exécuter une phase de test. Cochez les options que vous souhaitez activer pour cette phase. Si aucune des options n’est sélectionnée, la phase de test n’est pas affichée pendant l’exécution du pipeline.

      * **Tests fonctionnels du produit** – Exécutez des [tests fonctionnels du produit](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) dans l’environnement de développement.
      * **Tests fonctionnels personnalisés** – Exécutez des [tests fonctionnels personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) dans l’environnement de développement.
      * **Tests de l’interface utilisateur personnalisée** – Exécutez des [tests de l’interface utilisateur personnalisée](/help/implementing/cloud-manager/ui-testing.md) pour les applications personnalisées.
      * **Audit De L’Expérience** - Exécuter [Audit De L’Expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md)

   ![Pipeline full stack](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) sur la carte **Pipelines** sur la page **Aperçu du programme**.

### Déploiement ciblé {#targeted-deployment}

Un déploiement ciblé déploie le code uniquement pour les parties sélectionnées de votre application AEM. Dans un tel déploiement, vous pouvez choisir d’**inclure** l’un des types de code suivants :

* **Config** - Configurez les paramètres de différentes fonctionnalités de votre environnement AEM.
   * Voir [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md) pour obtenir la liste des configurations prises en charge, notamment le transfert de journaux, les tâches de maintenance liées à la purge et diverses configurations du réseau de diffusion de contenu, et pour les gérer dans votre référentiel afin qu’elles soient déployées correctement.
   * Lors de l’exécution d’un pipeline de déploiement ciblé, les configurations sont déployées, à condition qu’elles soient enregistrées dans l’environnement, le référentiel et la branche que vous avez définis dans le pipeline.
   * À tout moment, il ne peut y avoir qu’un seul pipeline de configuration par environnement.
* **Code front-end** - Configurez JavaScript et CSS pour le front-end de votre application AEM.
   * Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.
   * Consultez le document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour connaître le fonctionnement de ce processus ainsi que certaines considérations à prendre en compte pour en tirer le meilleur parti.
* **Configuration de niveau web** - Configurez les propriétés du Dispatcher pour stocker, traiter et diffuser des pages web au client.
   * Pour plus d’informations, consultez le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) .
   * Si un pipeline de code de niveau web existe pour l’environnement sélectionné, cette sélection est désactivée.
   * Si vous disposez déjà d’un pipeline full stack se déployant vers un environnement, la création d’un pipeline de configuration de niveau web pour le même environnement entraîne l’exclusion de la configuration de niveau web existante dans le pipeline full stack.

>[!NOTE]
>
>Les pipelines de niveau web et de configuration ne sont pas pris en charge pour les référentiels privés. Voir [Ajout de référentiels privés dans Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) pour plus d’informations et la liste complète des limites.

Les étapes de création de votre pipeline de déploiement ciblé hors production sont les mêmes une fois que vous avez choisi un type de déploiement.

1. Choisissez le type de déploiement dont vous avez besoin.

![Options de déploiement ciblées](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

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
   * **Pipeline** - Pour les pipelines front-end hors production, vous avez la possibilité d’activer le **[contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md)**.

   ![Config pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)

1. Si vous avez activé le contrôle de l’expérience, appuyez ou cliquez sur **Continuer** pour accéder à l’onglet **Audit de l’expérience** où vous pouvez définir les chemins qui doivent toujours être inclus dans le contrôle de l’expérience.

   * Si vous avez activé le **contrôle de l’expérience**, consultez le document [ contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-dashboard.md) pour plus d’informations sur la configuration.
   * Si ce n’est pas le cas, ignorez cette étape.

1. Appuyez ou cliquez sur **Enregistrer** pour enregistrer le pipeline.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) dans le carte **Pipelines** dans la page **Aperçu du programme**.

## Ignorer les modules Dispatcher {#skip-dispatcher-packages}

Si vous souhaitez que les packages du Dispatcher soient créés dans le cadre de votre pipeline, mais que vous ne souhaitez pas qu’ils soient publiés pour créer du stockage, vous pouvez désactiver leur publication, ce qui peut réduire la durée d’exécution du pipeline.

La configuration suivante permettant de désactiver la publication des packages du Dispatcher doit être ajoutée via le fichier `pom.xml` de votre projet. Elle est basée sur une variable d’environnement, qui sert d’indicateur que vous pouvez définir dans le conteneur de génération de Cloud Manager pour définir quand les packages du Dispatcher doivent être ignorés.

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

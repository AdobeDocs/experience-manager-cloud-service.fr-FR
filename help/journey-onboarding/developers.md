---
title: Tâches du développeur et du responsable de déploiement
description: Une fois que l’administrateur système a configuré les ressources cloud nécessaires, découvrez comment les développeurs et les gestionnaires de déploiement peuvent accéder à git pour développer des applications et utiliser des pipelines pour les déployer.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 19%

---


# Tâches du développeur et du responsable de déploiement {#developer-deployment-manager}

Dans cette partie facultative de la fonction [parcours d&#39;intégration,](overview.md) vous découvrirez comment les développeurs et les gestionnaires de déploiement peuvent accéder à git pour développer des applications et utiliser des pipelines pour les déployer.

## Un peu d’histoire… {#story-so-far}

Vous avez fait beaucoup de chemin dans votre parcours d&#39;intégration ! Félicitations ! L’administrateur système a terminé le parcours d’intégration en configurant les ressources cloud nécessaires et en accordant l’accès dans le document. [Attribution de profils de produit AEM.](assign-profiles-aem.md)

À ce stade, vos développeurs et responsables de déploiement peuvent commencer à créer vos propres applications, tandis que vos utilisateurs AEM peuvent commencer à créer du contenu. En ce sens, votre intégration est terminée et il est maintenant temps d’utiliser votre nouveau système as a Cloud Service d’AEM, comme le montre ce document.

## Public {#audience}

Le présent document est donc rédigé du point de vue de la **développeur** et **responsable de déploiement**.

L’administrateur système peut également effectuer les mêmes tâches, mais en règle générale, ces rôles sont attribués à différents utilisateurs.

## Objectif {#objective}

Ce document complète le parcours d’intégration afin de présenter les tâches de base d’un développeur et d’un responsable de déploiement une fois que l’administrateur système a intégré tous les utilisateurs et créé les ressources cloud nécessaires.

Après avoir lu ce document, vous devriez :

* En tant que développeur, découvrez comment accéder à vos référentiels Git Cloud Manager et les gérer.
* En tant que responsable de déploiement, vous pouvez configurer des pipelines et déployer votre code dans Cloud Manager.

## Développeurs et responsables de déploiement {#roles}

Une fois que l’administrateur système a effectué les principales tâches d’intégration liées à la création d’utilisateurs et à la configuration des ressources cloud, les utilisateurs généralement les plus soucieux d’accéder au système sont les développeurs et les responsables de déploiement. En effet, il s’agit des utilisateurs responsables de la création de vos applications personnalisées sur AEM as a Cloud Service.

* **Développeurs** - Ces utilisateurs accèdent aux référentiels Git de Cloud Manager où ils gèrent le code de vos applications personnalisées AEM.
* **Responsables de déploiement** - Ces utilisateurs utilisent Cloud Manager pour créer et exécuter des pipelines qui déploient le code des référentiels Git vers vos environnements AEM en cours d’exécution.

Selon les besoins de votre entreprise, un ou plusieurs utilisateurs peuvent avoir les deux rôles.

## Prérequis {#prerequisites}

Avant de commencer les tâches décrites dans ce document en tant que développeur ou responsable de déploiement, assurez-vous que l’administrateur système a suivi toutes les étapes de ce parcours d’intégration. Cela signifie que :

* Votre administrateur système a affecté des développeurs et des responsables de déploiement à leurs profils de produit respectifs.
* Les développeurs doivent en outre être affectés à **Utilisateurs AEM** ou **Administrateurs AEM** profils de produit afin d’utiliser également AEM.
* Des ressources cloud ont été configurées.

## Accès à git {#accessing-git}

Vous pouvez accéder à vos référentiels Git et les gérer à l’aide de la gestion de compte Git en libre-service à partir de Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à **Pipelines** de votre **Aperçu du programme** et recherchez les **Accès aux informations sur le référentiel** pour accéder à votre référentiel git et le gérer.

   ![Bouton Accéder aux informations de Repo sur la carte Environnements](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Cliquez sur le bouton **Afficher les informations sur le référentiel** pour ouvrir une boîte de dialogue afin d’afficher :

   * URL vers le référentiel git de Cloud Manager.
   * Nom d’utilisateur Git.
   * Le mot de passe Git, dont la valeur s’affiche lorsque la variable **Générer un mot de passe** est sélectionné.

   ![Informations du référentiel](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

À l’aide de ces informations d’identification, l’utilisateur peut cloner une copie locale du référentiel et apporter des modifications à ce référentiel local. Une fois prêt, il peut valider toutes les modifications de code dans le référentiel de code distant dans Cloud Manager.

## Configuration du pipeline {#setup-pipeline}

Une fois que les développeurs ont ajouté leur code personnalisé à vos référentiels git, le responsable de déploiement peut créer et exécuter des pipelines pour déployer ce code dans vos environnements AEM.

Pour créer votre premier pipeline de déploiement hors production, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** depuis l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajout d’un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Sur le **Configuration** de l’onglet **Ajout d’un pipeline hors production** sélectionnez le type de pipeline hors production que vous souhaitez ajouter. Pour cet exemple, sélectionnez **Pipeline de déploiement**.

   ![Boîte de dialogue Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Fournissez un **Nom du pipeline hors production** pour identifier votre pipeline avec les informations supplémentaires suivantes.

1. Pour le **Déclencheur de déploiement** select **Manuel** afin que le pipeline s’exécute uniquement lorsque vous le démarrez.

1. Cliquez sur **Continuer**.

1. Dans l’onglet **Code source** de la boîte de dialogue **Ajouter un pipeline hors production**, vous devez sélectionner le type de code que le pipeline doit traiter. Pour cet exemple, sélectionnez **Code de pile complet**.

1. Dans l’onglet **Code source**, vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** - Vous devez choisir l’environnement sur lequel le pipeline doit être déployé.
   * **Référentiel** - cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
   * **Branche Git** - cette option définit à partir de quelle branche sélectionnée le pipeline doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouvera les branches correspondantes pour vous aider à sélectionner.

   ![Pipeline full stack](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Cliquez sur **Enregistrer**.

Vous avez maintenant créé votre premier pipeline. Les utilisateurs dotés du rôle de gestionnaire de déploiement peuvent désormais démarrer le pipeline à partir de l’interface utilisateur de Cloud Manager.

## Déploiement dʼ {#deploy}

Maintenant que les développeurs ont ajouté leur code personnalisé aux référentiels git et qu’un pipeline est créé pour déployer ce code, il est temps d’exécuter le pipeline pour déplacer réellement ce code de git vers votre environnement.

![Vignette de pipelines dans Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous avez créé dans la section précédente, puis sélectionnez **Exécuter** dans le menu.

1. L’exécution du pipeline démarre et est indiquée par la colonne **Statut**.

Pour afficher les détails de l’exécution, cliquez de nouveau sur le bouton représentant des points de suspension et sélectionnez **Afficher les détails**.

Félicitations ! Vous avez maintenant déployé du code de votre référentiel git vers un environnement hors production !

## Prochaines étapes {#whats-next}

Maintenant que vous avez lu ce document, vous devez :

* En tant que développeur, découvrez comment accéder à vos référentiels Git Cloud Manager et les gérer.
* En tant que responsable de déploiement, vous pouvez configurer des pipelines et déployer votre code dans Cloud Manager.

Vous avez atteint le terrain en tant que développeur ou responsable de déploiement avec non seulement des connaissances opérationnelles de Cloud Manager, mais aussi des environnements de travail, des référentiels et des pipelines ! Mais il y a plus à apprendre sur les puissants outils de CI/CD d&#39;AEM as a Cloud Service. Consultez la section [Ressources supplémentaires](#additional-resources) pour plus d’informations.

Si vous souhaitez savoir comment les auteurs de contenu accèdent à AEM as a Cloud Service et l’utilisent, passez à la dernière partie du parcours d’intégration, [AEM Tâches utilisateur.](aem-users.md)

>[!TIP]
>
>Maintenant que vous êtes intégré, vous pouvez [découvrir comment ajouter facilement le module complémentaire de démonstration de référence d’AEM](/help/journey-sites/demos-add-on/overview.md) à un environnement sandbox avec une configuration minimale d’AEM et être en mesure de tester les puissantes fonctionnalités d’AEM avec de riches exemples basés sur les bonnes pratiques.

## Ressources supplémentaires {#additional-resources}

* [Accès aux référentiels](/help/implementing/cloud-manager/managing-code/accessing-repos.md) - Découvrez comment accéder à votre référentiel git et le gérer à l’aide de la gestion de compte git en libre-service à partir de Cloud Manager.
* [Utilisation de git avec Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) - Découvrez comment utiliser les référentiels Git de Cloud Manager et comment intégrer votre propre référentiel Git géré par le client sur site à Cloud Manager.
* [Configuration de l’environnement de développement local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=fr) - Ce tutoriel vous guide tout au long de la configuration d’un environnement de développement local pour Adobe Experience Manager (AEM) à l’aide du SDK as a Cloud Service AEM.
* [Prise en main d’AEM Sites - Tutoriel WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr) - Ce tutoriel en plusieurs parties est conçu pour les développeurs qui découvrent Adobe Experience Manager (AEM). Ce tutoriel décrit la mise en oeuvre d’un site AEM pour une marque de style de vie fictive WKND. Le tutoriel aborde des sujets fondamentaux tels que la configuration de projet, les composants principaux, les modèles modifiables, les bibliothèques côté client et le développement de composants avec Adobe Experience Manager Sites.
* [Prise en main de SPA dans AEM avec React](/help/implementing/developing/hybrid/getting-started-react.md) - Cet article présente un exemple d’application SPA, explique comment elle est structurée et vous permet de prendre en main votre propre SPA rapidement à l’aide du framework React.
* [Prise en main de SPA dans AEM Utilisation d’Angular](/help/implementing/developing/hybrid/getting-started-angular.md) - Cet article présente un exemple d’application SPA, explique comment elle est structurée et vous permet de prendre en main votre propre SPA rapidement à l’aide de la structure d’Angular.
* [Parcours de développement sans tête](/help/journey-headless/developer/overview.md) - Démarrez ici pour suivre un cours guidé de développement d’applications sans interface avec AEM.

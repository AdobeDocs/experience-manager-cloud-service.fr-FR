---
title: Tâches du développeur et du responsable de déploiement
description: Une fois que l’administrateur système a configuré les ressources cloud nécessaires, découvrez comment les développeurs et les responsables de déploiement peuvent accéder à Git pour développer des applications et utiliser des pipelines pour les déployer.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '1397'
ht-degree: 100%

---


# Tâches du développeur et du responsable de déploiement {#developer-deployment-manager}

Dans cette partie facultative du [parcours d’intégration](overview.md), vous découvrirez comment l’équipe de développement et les personnes responsables du déploiement peuvent accéder à Git pour développer des applications et utiliser des pipelines pour les déployer.

## Un peu d’histoire... {#story-so-far}

Vous avez déjà fait du chemin dans votre parcours d’intégration ! Félicitations ! L’administrateur ou l’administratrice système a terminé le parcours d’intégration en configurant les ressources cloud nécessaires et en accordant l’accès dans le document [Attribution de profils de produits AEM](assign-profiles-aem.md).

À ce stade, vos développeurs et responsables de déploiement peuvent commencer à créer vos propres applications, tandis que vos utilisateurs AEM peuvent commencer à créer du contenu. En ce sens, votre intégration est terminée et il est maintenant temps d’utiliser votre nouveau système AEM as a Cloud Service, comme le montre ce document.

## Public {#audience}

Le présent document est donc rédigé du point de vue du **développeur** et du **responsable de déploiement**.

L’administrateur système peut également effectuer les mêmes tâches, mais en règle générale, ces rôles sont attribués à différents utilisateurs.

## Objectif {#objective}

Ce document complète le parcours d’intégration afin de présenter les tâches de base d’un développeur et d’un responsable de déploiement une fois que l’administrateur système a intégré tous les utilisateurs et créé les ressources cloud nécessaires.

Après avoir lu ce document, vous devriez :

* En tant que développeur, comprendre comment accéder à vos référentiels Git de Cloud Manager et les gérer.
* En tant que responsable de déploiement, être capable de configurer des pipelines et de déployer votre code dans Cloud Manager.

## Développeurs et responsables de déploiement {#roles}

Une fois que l’administrateur système a effectué les principales tâches d’intégration liées à la création d’utilisateurs et à la configuration des ressources cloud, les utilisateurs généralement les plus soucieux d’accéder au système sont les développeurs et les responsables de déploiement. En effet, il s’agit d’utilisateurs responsables de la création de vos applications personnalisées sur AEM as a Cloud Service.

* **Développeurs** : ces utilisateurs accèdent aux référentiels Git de Cloud Manager, où ils gèrent le code de vos applications AEM personnalisées.
* **Responsables de déploiement** : ces utilisateurs se servent de Cloud Manager pour créer et exécuter des pipelines qui déploient le code des référentiels Git vers vos environnements d’exécution AEM.

Selon les besoins de votre entreprise, un ou plusieurs utilisateurs peuvent avoir les deux rôles.

## Conditions préalables {#prerequisites}

Avant de commencer les tâches décrites dans ce document en tant que développeur ou responsable de déploiement, assurez-vous que l’administrateur système a terminé toutes les étapes de ce parcours d’intégration. Cela signifie que :

* Votre administrateur système a affecté des développeurs et des responsables de déploiement à leurs profils de produits respectifs.
* Les personnes en charge du développement doivent en outre être affectées aux profils de produits d’**utilisation AEM** ou d’**administration AEM** afin d’utiliser elles-mêmes AEM.
* Les ressources cloud ont été configurées.

## Accéder à Git {#accessing-git}

Vous pouvez accéder à vos référentiels Git et les gérer à l’aide de la gestion de compte Git en libre-service à partir de Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** à partir de votre page **Aperçu du programme** et recherchez le bouton **Accéder aux informations sur le référentiel** pour accéder à votre référentiel Git et le gérer.

   ![Bouton Accéder aux informations sur le référentiel de la vignette d’environnements](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Cliquez sur le bouton **Afficher les informations sur le référentiel** pour ouvrir une boîte de dialogue affichant les éléments suivants :

   * L’URL vers le référentiel Git de Cloud Manager.
   * Le nom d’utilisateur Git.
   * Le mot de passe Git, dont la valeur s’affiche lorsqu’on clique sur le bouton **Générer un mot de passe**.

   ![Informations sur le référentiel](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

À l’aide de ces informations d’identification, l’utilisateur peut cloner une copie locale du référentiel et apporter des modifications à ce référentiel local. Une fois prêt, il peut valider toutes les modifications de code vers le référentiel de code distant de Cloud Manager.

## Configuration du pipeline {#setup-pipeline}

Une fois que les développeurs ont ajouté leur code personnalisé à vos référentiels Git, le responsable de déploiement peut créer et exécuter des pipelines pour déployer ce code dans vos environnements AEM.

Pour créer votre premier pipeline de déploiement hors production, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** depuis l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajouter un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Sous l’onglet **Configuration** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez le type de pipeline hors production que vous souhaitez ajouter. Pour cet exemple, sélectionnez **Pipeline de déploiement**.

   ![Boîte de dialogue Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Fournissez un **Nom du pipeline hors production** pour identifier votre pipeline avec les informations supplémentaires suivantes.

1. Pour le **Déclencheur de déploiement**, sélectionnez **Manuel** afin que le pipeline s’exécute uniquement lorsque vous le démarrez.

1. Cliquez sur **Continuer**.

1. Sous l’onglet **Code source** de la boîte de dialogue **Ajouter un pipeline hors production**, vous devez sélectionner le type de code que le pipeline doit traiter. Pour cet exemple, sélectionnez **Code de pile pleine**.

1. Sous l’onglet **Code source**, vous devez définir les options suivantes.

   * **Environnements de déploiement éligibles** : vous devez sélectionner l’environnement dans lequel le pipeline doit être déployé.
   * **Référentiel** : cette option définit à partir de quel référentiel Git le pipeline doit récupérer le code.
   * **Branche Git** : cette option définit à partir de quelle branche le pipeline doit récupérer le code.
      * Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ trouvera les branches correspondantes pour vous aider à les sélectionner.

   ![Pipeline full stack](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Cliquez sur **Enregistrer**.

Vous avez créé votre premier pipeline ! Les utilisateurs dotés du rôle de responsable de déploiement peuvent désormais démarrer le pipeline à partir de l’interface utilisateur de Cloud Manager.

## Déployer {#deploy}

Maintenant que les développeurs ont ajouté leur code personnalisé aux référentiels Git et qu’un pipeline a été créé pour déployer ce code, il est temps d’exécuter le pipeline pour déplacer réellement ce code de Git vers votre environnement.

![Vignette de pipelines dans Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** à partir de la page **Vue d’ensemble du programme** et cliquez sur le bouton représentant des points de suspension à côté du pipeline que vous avez créé dans la section précédente, puis sélectionnez **Exécuter** dans le menu.

1. L’exécution du pipeline démarre et est indiquée par la colonne **Statut**.

Pour afficher les détails de l’exécution, cliquez de nouveau sur le bouton représentant des points de suspension et sélectionnez **Afficher les détails**.

Félicitations ! Vous avez déployé du code de votre référentiel Git vers un environnement hors production !

## Prochaines étapes {#whats-next}

Maintenant que vous avez lu ce document, vous devriez :

* En tant que développeur, comprendre comment accéder à vos référentiels Git de Cloud Manager et les gérer.
* En tant que responsable de déploiement, être capable de configurer des pipelines et de déployer votre code dans Cloud Manager.

En tant que développeur ou responsable de déploiement, vous pouvez immédiatement commencer à utiliser vos connaissances opérationnelles de Cloud Manager, mais aussi des environnements de travail, des référentiels et des pipelines ! Mais il y a plus à apprendre sur les puissants outils de CI/CD d’AEM as a Cloud Service. Consultez la section [Ressources supplémentaires](#additional-resources) pour plus d’informations.

Si vous souhaitez savoir comment les personnes chargées de la création de contenu accèdent à AEM as a Cloud Service et l’utilisent, passez à la dernière partie du parcours d’intégration, [Tâches d’utilisation d’AEM](aem-users.md).

>[!TIP]
>
>Maintenant que vous êtes intégré, vous pouvez [découvrir comment ajouter facilement le module complémentaire de démonstration de référence d’AEM](/help/journey-sites/demos-add-on/overview.md) à un environnement sandbox avec une configuration minimale d’AEM et être en mesure de tester les puissantes fonctionnalités d’AEM avec de riches exemples basés sur les bonnes pratiques.

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous des ressources facultatives supplémentaires si vous souhaitez aller au delà du contenu du parcours d’intégration.

* [Accéder aux référentiels](/help/implementing/cloud-manager/managing-code/accessing-repos.md) : découvrez comment accéder à votre référentiel Git et comment le gérer à l’aide de la gestion de compte Git en libre-service à partir de Cloud Manager.
* [Utiliser Git avec Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) : découvrez comment utiliser les référentiels Git de Cloud Manager et comment intégrer votre propre référentiel Git On-premise géré par le client avec Cloud Manager.
* [Configuration de l’environnement de développement local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=fr) : ce tutoriel vous guide tout au long de la configuration d’un environnement de développement local pour Adobe Experience Manager (AEM) à l’aide du SDK d’AEM as a Cloud Service.
* [Prise en main d’AEM Sites - Tutoriel WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr) : ce tutoriel en plusieurs parties est conçu pour les développeurs qui découvrent Adobe Experience Manager (AEM). Ce tutoriel décrit l’implémentation d’un site AEM pour une marque de style de vie fictive, WKND. Le tutoriel aborde des sujets fondamentaux tels que la configuration de projet, les composants principaux, les modèles modifiables, les bibliothèques côté client et le développement de composants avec Adobe Experience Manager Sites.
* [Prise en main des SPA dans AEM à l’aide de React](/help/implementing/developing/hybrid/getting-started-react.md) : cet article présente un exemple d’application SPA, en explique la structure et vous permet de prendre rapidement en main votre propre SPA à l’aide du framework React.
* [Prise en main des SPA dans AEM à l’aide d’Angular](/help/implementing/developing/hybrid/getting-started-angular.md) : cet article présente un exemple d’application SPA, en explique la structure et vous permet de prendre rapidement en main votre propre SPA à l’aide du framework Angular.
* [Parcours de développement découplé](/help/journey-headless/developer/overview.md) : démarrez ici un cours guidé sur le développement d’applications découplées avec AEM.

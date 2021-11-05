---
title: Récupération des informations d’accès au référentiel Git
description: Découvrez comment le développeur front-end utilise Cloud Manager pour accéder aux informations du référentiel git.
source-git-commit: 348e26a9af260d89841d19d00ce4102c00ae34ed
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 4%

---


# Récupération des informations d’accès au référentiel Git {#retrieve-access}

Découvrez comment le développeur front-end utilise Cloud Manager pour accéder aux informations du référentiel git.

>[!CAUTION]
>
>L’outil de création de site rapide est actuellement un aperçu technique. Il est mis à disposition à des fins de test et d’évaluation et n’est pas destiné à un usage en production sauf accord avec le support Adobe.

## Un peu d’histoire...  {#story-so-far}

Si vous êtes un développeur front-end uniquement responsable de la personnalisation du thème du site, vous n’avez pas besoin de connaître la configuration de l’AEM et pouvez passer à la [Objectif](#objective) de ce document.

Si vous jouez également le rôle d’administrateur de Cloud Manager ou d’AEM, ainsi que de développeur front-end, vous avez appris dans le document précédent du parcours de création rapide de site AEM, [Accorder l’accès au développeur front-end,](grant-access.md) comment embarquer le développeur front-end pour qu’il ait accès au référentiel git. vous devez maintenant savoir :

* Comment ajouter un développeur front-end en tant qu’utilisateur.
* Comment accorder les rôles requis au développeur front-end.

Cet article passe à l’étape suivante pour montrer comment le développeur front-end utilise l’accès Cloud Manager pour récupérer les informations d’identification afin d’accéder au référentiel git d’AEM.

Maintenant qu’un site est créé à partir d’un modèle, il existe un pipeline configuré, le développeur front-end est intégré et contient toutes les informations dont il a besoin, cet article déplace la perspective des administrateurs et exclusivement vers le rôle de développeur front-end.

## Objectif {#objective}

Ce document explique comment, en tant que développeur front-end, vous pouvez accéder à Cloud Manager et récupérer les informations d’identification d’accès au référentiel git d’AEM. Après lecture, vous serez amené à :

* Découvrez Cloud Manager à un haut niveau.
* Vous avez récupéré vos informations d’identification pour accéder au git d’AEM afin que vous puissiez valider vos personnalisations.

## Rôle responsable {#responsible-role}

Cette partie du parcours s’applique au développeur front-end.

## Conditions requises {#requirements}

L’outil de création rapide de site permet aux développeurs front-end de travailler indépendamment sans connaissance ni de l’AEM ni de la manière dont ils sont configurés. Toutefois, l’administrateur de Cloud Manager doit intégrer le développeur front-end à l’équipe de projet et l’administrateur AEM doit vous fournir certaines informations requises. Assurez-vous de disposer des informations suivantes avant de continuer.

* De l’administrateur AEM :
   * Fichiers source du thème à personnaliser
   * Chemin d’accès à une page d’exemple à utiliser comme base de référence
   * Informations d’identification de l’utilisateur du proxy pour tester vos personnalisations par rapport au contenu AEM actif
   * Exigences de conception front-end
* De l’administrateur de Cloud Manager :
   * Un e-mail de bienvenue de Cloud Manager vous informant de l’accès
   * Le nom du programme ou l’URL qui lui correspond dans Cloud Manager

Si l’un de ces éléments vous manque, contactez l’administrateur AEM ou l’administrateur Cloud Manager.

Il est supposé que le développeur front-end dispose d’une vaste expérience des workflows de développement front-end ainsi que des outils courants installés, notamment :

* git
* npm
* webpack
* Un éditeur préféré

## Présentation de Cloud Manager {#understanding-cloud-manager}

Cloud Manager permet aux entreprises de gérer elles-mêmes les AEM dans le cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité.

Pour le développeur front-end, il s’agit de la passerelle vers :

* Accédez aux informations AEM référentiel git afin de pouvoir valider vos personnalisations frontales.
* Démarrez le pipeline de déploiement pour déployer vos personnalisations.

L’administrateur de Cloud Manager vous a intégré en tant qu’utilisateur de Cloud Manager. Vous auriez dû recevoir un e-mail de bienvenue similaire à ce qui suit.

![Courriel de bienvenue](assets/welcome-email.png)

Si vous n’avez pas reçu cet e-mail, contactez l’administrateur de Cloud Manager.

## Accès à Cloud Manager {#access-cloud-manager}

1. Connectez-vous à Adobe Experience Cloud à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) ou cliquez sur le lien proposé dans l&#39;email de bienvenue.

1. Une fois connecté, vérifiez que vous vous trouvez dans la bonne organisation en la cochant dans le coin supérieur droit de l’écran. Si vous n’êtes membre que d’une seule organisation, cette étape n’est pas nécessaire. Ensuite, appuyez ou cliquez sur **Experience Manager**.

   ![Présentation de l’Experience Cloud](assets/experience-cloud-overview.png)

1. Sur la page suivante, appuyez ou cliquez sur l’icône **Launch** pour lancer le **Cloud Manager** application.

   ![Applications de Experience Manager](assets/experience-manager-apps.png)

1. La page suivante répertorie les différents programmes disponibles. Appuyez ou cliquez sur celui auquel vous devez accéder, comme fourni par l’administrateur de Cloud Manager. S’il s’agit de votre premier projet front-end pour AEMaaCS, il est probable qu’un seul programme soit disponible.

   ![Sélection d’un programme dans Cloud Manager](assets/cloud-manager-select-program.png)

Vous voyez maintenant un aperçu de Cloud Manager. Votre page sera différente, mais similaire à cet exemple.

![Présentation de Cloud Manager](assets/cloud-manager-overview.png)

## Récupération des informations d’accès au référentiel {#repo-access}

1. Dans le **Pipelines** de la page Cloud Manager, appuyez ou cliquez sur l’icône **Accès aux informations sur le référentiel** bouton .

   ![Pipelines](assets/pipelines-repo-info.png)

1. Le **Informations sur le référentiel** s’ouvre.

   ![Informations sur le référentiel](assets/repo-info.png)

1. Appuyez ou cliquez sur le bouton **Générer un mot de passe** pour créer un mot de passe.

1. Enregistrez le mot de passe généré dans un gestionnaire de mot de passe sécurisé. Le mot de passe ne s’affichera plus jamais.

1. Copiez également la variable **username** et **Ligne de commande Git** champs. Vous utiliserez ces informations ultérieurement pour accéder au référentiel.

1. Appuyez ou cliquez sur **Fermer**.

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de création rapide de site AEM, vous devez :

* Découvrez Cloud Manager à un haut niveau.
* Vous avez récupéré vos informations d’identification pour accéder au git d’AEM afin que vous puissiez valider vos personnalisations.

Tirez parti de ces connaissances et poursuivez votre parcours de création rapide de site AEM en consultant le document. [Personnaliser le thème du site,](customize-theme.md) où vous découvrirez comment le thème du site est créé, comment personnaliser et comment tester à l’aide de contenu d’AEM en direct.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de création de site rapide en consultant le document [Personnaliser le thème du site,](customize-theme.md) vous trouverez ci-dessous des ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours.

* [Documentation d’Adobe Experience Manager Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr) - Consultez la documentation de Cloud Manager pour en savoir plus sur ses fonctionnalités.

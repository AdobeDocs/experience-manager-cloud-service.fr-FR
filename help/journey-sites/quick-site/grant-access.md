---
title: Accorder l’accès au développeur front-end
description: Intégrez les développeurs front-end à Cloud Manager afin qu’ils aient accès au référentiel git et au pipeline de votre site AEM.
exl-id: 58e95c92-b859-4bb9-aa62-7766510486fd
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 4%

---

# Accorder l’accès au développeur front-end {#grant-fed-access}

Intégrez les développeurs front-end à Cloud Manager afin qu’ils aient accès au référentiel git et au pipeline de votre site AEM.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours de création rapide de site AEM, [Configuration de votre pipeline,](pipeline-setup.md) vous avez appris à créer un pipeline frontal pour gérer la personnalisation du thème de votre site. vous devez maintenant :

* Comprendre ce qu’est un pipeline frontal.
* Découvrez comment configurer un pipeline frontal dans Cloud Manager.

Vous devez maintenant accorder à votre développeur front-end l’accès à Cloud Manager par le biais du processus d’intégration afin que le développeur front-end puisse accéder au référentiel git d’AEM et au pipeline que vous avez créé.

## Objectif {#objective}

Le processus d’octroi de l’accès à Cloud Manager et d’affectation de rôles utilisateur à vos utilisateurs est appelé intégration. Ce document présente les étapes les plus importantes pour l’intégration d’un développeur front-end et, après lecture, vous connaissez :

* Comment ajouter un développeur front-end en tant qu’utilisateur.
* Comment accorder les rôles requis au développeur front-end.

>[!TIP]
>
>Il existe un parcours de documentation complet dédié à l’intégration de votre équipe à AEM as a Cloud Service, lié à dans [Section Ressources supplémentaires](#additional-resources) de ce document, si vous avez besoin de détails supplémentaires sur le processus.

## Rôle responsable {#responsible-role}

Cette partie du parcours s’applique à l’administrateur de Cloud Manager.

## Conditions requises {#requirements}

* Vous devez être membre de **Propriétaire de l’entreprise** dans Cloud Manager.
* Vous devez être un **Administrateur Sys** dans Cloud Manager.
* Vous devez avoir accès au Admin Console.

## Ajout du développeur front-end en tant qu’utilisateur {#add-fed-user}

Vous devez d’abord ajouter le développeur front-end en tant qu’utilisateur à l’aide du Admin Console .

1. Connectez-vous au Admin Console à l’adresse [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).

1. Une fois connecté, une page d’aperçu similaire à l’image suivante s’affiche.

   ![Présentation du Admin Console](assets/admin-console.png)

1. Vérifiez que vous vous trouvez dans l’organisation appropriée en cochant le nom de l’organisation dans le coin supérieur droit de l’écran.

   ![Vérifier le nom de l’organisation](assets/correct-org.png)

1. Sélectionner **Adobe Experience Manager as a Cloud Service** de la **Produits et services** carte.

   ![Sélectionner AEMaaCS](assets/select-aemaacs.png)

1. La liste des profils de produits Cloud Manager préconfigurés s’affiche. Si ces profils ne s’affichent pas, contactez votre administrateur Cloud Manager, car vous ne disposez peut-être pas des autorisations appropriées dans votre organisation.

   ![Profils de produit](assets/product-profiles.png)

1. Pour affecter le développeur front-end aux profils corrects, appuyez ou cliquez sur le bouton **Utilisateurs** puis l’onglet **Ajouter un utilisateur** bouton .

   ![Ajouter un utilisateur](assets/add-user.png)

1. Dans le **Ajout d’utilisateurs à votre équipe** , saisissez l’e-mail de l’utilisateur à ajouter. Pour le type d’identifiant, sélectionnez Adobe ID si le Federated ID des membres de votre équipe n’a pas encore été configuré.

   ![Ajout d’un utilisateur à l’équipe](assets/add-to-team.png)

1. Dans le **Produit** sélectionnez, appuyez ou cliquez sur le signe plus, puis sélectionnez **Adobe Experience Manager as a Cloud Service** et affectez la variable **Responsable de déploiement** et **Développeur** profils de produit pour l’utilisateur.

   ![Attribution de profils d’équipe](assets/assign-team.png)

1. Appuyez ou cliquez sur **Enregistrer** et un e-mail de bienvenue est envoyé au développeur front-end que vous avez ajouté en tant qu’utilisateur.

Le développeur front-end invité peut accéder à Cloud Manager en cliquant sur le lien contenu dans l’e-mail de bienvenue et en se connectant à l’aide de son Adobe ID.

## Transfert vers le développeur front-end {#handover}

Avec une invitation par courrier électronique à Cloud Manager en route vers le développeur front-end, vous et l’administrateur d’AEM pouvez désormais fournir au développeur front-end les informations nécessaires restantes pour commencer la personnalisation.

* A [chemin d’accès au contenu type](#example-page)
* La source du thème qui [que vous avez téléchargé](#download-theme)
* Le [informations sur les utilisateurs proxy](#proxy-user)
* Nom du programme ou URL qui lui correspond [copié à partir de Cloud Manager](pipeline-setup.md#login)
* Exigences de conception frontale

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de création rapide de site AEM, vous devez savoir :

* Comment ajouter un développeur front-end en tant qu’utilisateur.
* Comment accorder les rôles requis au développeur front-end.

Tirez parti de ces connaissances et poursuivez votre parcours de création rapide de site AEM en consultant le document. [Récupérer les informations d’accès au référentiel Git,](retrieve-access.md) qui bascule la perspective exclusivement vers le développeur front-end et explique comment le développeur front-end utilise Cloud Manager pour accéder aux informations du référentiel git.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de création de site rapide en consultant le document [Récupérez les informations d’identification du développeur front-end,](retrieve-access.md) vous trouverez ci-dessous des ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours.

* [Parcours d’intégration](/help/journey-onboarding/home.md) - Ce guide constitue votre point de départ pour vous assurer que vos équipes sont configurées et ont accès à AEM as a Cloud Service.

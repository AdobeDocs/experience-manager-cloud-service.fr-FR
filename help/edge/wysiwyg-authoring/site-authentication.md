---
title: Configuration de l’authentification de site pour la création de contenu
description: Découvrez comment AEM Live prend en charge l’authentification basée sur les jetons et comment configurer AEM pour utiliser l’authentification avec la création WYSIWYG.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: b2838da2-79c7-49b1-a101-15c21e80197e
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 2%

---

# Configuration de l’authentification de site pour la création de contenu {#site-authentication}

Découvrez comment AEM Live prend en charge l’authentification basée sur les jetons et comment configurer AEM pour utiliser l’authentification avec la création WYSIWYG.

## Vue d’ensemble {#overview}

AEM Live prend en charge l’authentification par jeton. L’authentification du site est généralement appliquée aux sites d’aperçu et de publication, mais peut également être configurée pour protéger uniquement l’un des deux sites individuellement.

>[!NOTE]
>
>Si vous choisissez d’activer l’authentification du site, vous devez également la configurer dans vos environnements de création AEM

## Conditions requises {#requirements}

Pour configurer l’authentification du site à utiliser avec la création de contenu, vous devez d’abord effectuer les tâches suivantes :

* Ce document suppose que vous avez déjà créé un site pour votre projet à partir du guide de prise en main [Developer Getting Started Guide for WYSIWYG Authoring with Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md).
* Vous devez avoir déjà [activé la fonction de réponse pour votre projet.](/help/edge/wysiwyg-authoring/repoless.md)

## Configurer l’authentification du site {#configure-authentication}

Consultez le document [Configuration de l’authentification de site](https://www.aem.live/docs/authentication-setup-site) pour plus d’informations sur la configuration de l’authentification de site.

Notez les informations suivantes lorsque vous configurez l’authentification :

* ID du compte technique
* Votre jeton d’authentification de site

Ces éléments sont nécessaires pour terminer la configuration de l’authentification du site pour votre environnement de création AEM.

## Configuration de l’environnement de création {#authoring-environment}

Une fois l’authentification du site configurée, vous pouvez l’activer dans votre environnement de création AEM.

1. Connectez-vous à l’instance d’auteur AEM et accédez à **Outils** -> **Services cloud** -> **Configuration Edge Delivery Services** et sélectionnez la configuration qui a été automatiquement créée pour votre site, puis appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre **Configuration de Edge Delivery Services**, sélectionnez l&#39;onglet **Authentification**, fournissez le **Jeton d&#39;authentification de site**, que vous avez copié précédemment.

   ![Configuration Edge Delivery Services](/help/edge/wysiwyg-authoring/assets/site-authentication/configure-aem-author.png)

1. Vérifiez que l’**ID de compte technique** correspond à celui que vous avez copié précédemment.

   * Ce champ est en lecture seule et prédéfini.
   * Le compte technique est le même pour tous les sites sur un seul environnement de création AEM.

1. Appuyez et cliquez sur **Enregistrer et fermer**.

---
title: Accès à Git
seo-title: Accès à Git
description: Cette page vous explique comment accéder au référentiel Git et le gérer.
seo-description: Consultez cette page pour découvrir comment accéder à votre référentiel Git et le gérer.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 100%

---

# Accès à Git {#accessing-git}

Vous pouvez accéder à votre référentiel Git et le gérer à l’aide de la gestion de compte Git en libre-service à partir de l’interface utilisateur de Cloud Manager.

## Utilisation de la gestion de compte Git en libre-service {#self-service-git}

Utilisez le bouton **Gérer Git** disponible dans l’interface utilisateur de Cloud Manager, bien en vue sur la carte du pipeline.

1. Accédez à la page *Aperçu du programme* et à la carte Pipelines.

1. L’option **Gérer Git** permettant d’accéder à votre référentiel Git et de le gérer est alors visible.

   ![](assets/manage-git1.png)

   Si vous sélectionnez l’onglet de pipeline **Hors production**, l’option **Gérer Git** est également disponible à cet endroit.

   ![](assets/manage-git-new2.png)

>[!NOTE]
>L’option **Gérer Git** est visible par les utilisateurs avec le rôle Développeur ou Gestionnaire de déploiement. Lorsque l’utilisateur clique sur ce bouton, il accède à une boîte de dialogue qui lui permet de trouver l’URL de son référentiel Git Cloud Manager, ainsi que son nom d’utilisateur et son mot de passe.

![](assets/manage-git3.png)

Les points importants à prendre en compte pour gérer votre Git dans Cloud Manager sont les suivants :

* **URL** : URL du référentiel
* **Nom d’utilisateur** : nom d’utilisateur
* **Mot de passe** : valeur affichée lorsque vous cliquez sur le bouton **Générer un mot de passe** .


>[!NOTE]
>
>Un utilisateur peut extraire une copie de son code et effectuer des modifications dans le référentiel de code local. Une fois prêt, l’utilisateur peut valider les modifications de code dans le référentiel de code distant dans Cloud Manager.

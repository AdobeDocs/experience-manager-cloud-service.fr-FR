---
title: Accès aux référentiels
seo-title: Accessing Repositories
description: Cette page vous explique comment accéder au référentiel Git et le gérer.
seo-description: Follow this page to learn how to access and manage your Git repository.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 3cdee254eebcf45762feff8fe081b006a803ef1b
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 97%

---

# Accès aux référentiels {#accessing-repos}

Vous pouvez accéder à votre référentiel Git et le gérer à l’aide de la gestion de compte Git en libre-service à partir de l’interface utilisateur de Cloud Manager.

## Utilisation de la gestion de compte de référentiels en libre-service {#self-service-repos}

Utilisez le bouton **Accéder aux informations sur le référentiel** disponible dans l’interface utilisateur de Cloud Manager, bien en vue sur la carte du pipeline.

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. L’option **Accéder aux informations sur le référentiel** permettant d’accéder à votre référentiel Git est alors visible.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

   Si vous sélectionnez l’onglet de pipeline **Hors production**, l’option **Accéder aux informations sur référentiel** est également disponible à cet endroit.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

   >[!NOTE]
   >L’option **Accéder aux informations sur le référentiel** est visible par les utilisateurs possédant le rôle Développeur ou Gestionnaire de déploiement. Lorsque l’utilisateur clique sur ce bouton, il accède à une boîte de dialogue qui lui permet de trouver l’URL de son référentiel Git Cloud Manager, ainsi que son nom d’utilisateur et son mot de passe.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

   Les points importants à prendre en compte pour gérer votre Git dans Cloud Manager sont les suivants :

   * **URL** : URL du référentiel
   * **Nom d’utilisateur** : nom d’utilisateur
   * **Mot de passe** : valeur affichée lorsque vous cliquez sur le bouton **Générer un mot de passe**.


      >[!NOTE]
      >Un utilisateur peut extraire une copie de son code et effectuer des modifications dans le référentiel de code local. Une fois prêt, l’utilisateur peut valider les modifications de code dans le référentiel de code distant dans Cloud Manager.

---
title: Connecter AEM Assets à Creative Cloud
description: Découvrez comment configurer et connecter AEM Assets à Creative Cloud. Connectez-vous à un droit de Creative Cloud qui est fourni à une autre organisation IMS pour utiliser facilement les dernières intégrations de Creative Cloud dans AEM Assets, y compris Express et Creative Cloud Libraries.
exl-id: 880200fe-94b3-49de-802c-34283f7c71bc
feature: Collaboration
role: User
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 72%

---

# Connecter AEM Assets à Creative Cloud  {#cross-org-entitlements}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Experience Manager Assets peut se connecter à un droit de Creative Cloud qui est configuré pour une autre organisation IMS afin d’utiliser facilement les dernières intégrations de Creative Cloud dans AEM Assets, y compris Express et Creative Cloud Libraries.

Si vos produits Creative Cloud et AEM Assets sont configurés pour des organisations IMS distinctes, vous pouvez vous connecter à une autre organisation Creative Cloud pour pouvoir exécuter des workflows intégrés entre les deux solutions.

## Conditions préalables {#prerequisites}

* Droits d’administration sur Experience Manager Assets

* Droit actif sur Creative Cloud pour le même ID d’utilisateur ou d’utilisatrice utilisé dans Creative Cloud et Experience Manager. Les droits sur les identifiants personnels et fédérés avec la même adresse e-mail sont traités comme des identifiants d’utilisateur ou d’utilisatrice différents.

## Se connecter à une nouvelle organisation Creative Cloud {#connect-to-creative-cloud-org}

Pour vous connecter à une nouvelle organisation Creative Cloud, exécutez les étapes suivantes :

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Creative Cloud]**.

1. Sélectionnez la nouvelle organisation Creative Cloud à l’aide de la liste déroulante **[!UICONTROL Sélectionner un nouvel ID d’organisation Creative Cloud]**. La liste affiche toutes les organisations auxquelles vous avez accès. Sélectionnez l’organisation disposant de droits Creative Cloud actifs.

1. Cliquez sur **[!UICONTROL Changer d’organisation]** pour passer à la nouvelle organisation.

   ![Droits inter-organisations](assets/cross-org-entitlements.png)

## Limites {#limitations}

* Vous pouvez connecter AEM Assets à une seule organisation Creative Cloud à la fois. La connexion simultanée à plusieurs organisations Creative Cloud n’est pas prise en charge.

* L’organisation Creative Cloud à laquelle vous vous connectez dans AEM Assets s’applique à tous les utilisateurs et utilisatrices de votre organisation.

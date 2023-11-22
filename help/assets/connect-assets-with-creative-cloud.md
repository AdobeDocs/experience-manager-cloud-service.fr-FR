---
title: Connexion d’AEM Assets à Creative Cloud
description: Découvrez comment configurer et connecter AEM Assets à Creative Cloud. Connectez-vous à un droit de Creative Cloud qui est fourni à une autre organisation IMS pour utiliser facilement les dernières intégrations de Creative Cloud dans AEM Assets, y compris les bibliothèques express et Creative Cloud.
exl-id: 880200fe-94b3-49de-802c-34283f7c71bc
source-git-commit: 237b4a8e01af74dbaac0ba1715b5fa95c931be7c
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Connexion d’AEM Assets à Creative Cloud  {#cross-org-entitlements}

Experience Manager Assets peut se connecter à un droit de Creative Cloud qui est configuré pour une autre organisation IMS afin d’utiliser facilement les dernières intégrations de Creative Cloud dans AEM Assets, y compris les bibliothèques express et Creative Cloud.

Si vos produits Creative Cloud et AEM Assets sont configurés pour séparer les organisations IMS, vous pouvez vous connecter à une autre organisation Creative Cloud pour pouvoir exécuter des workflows intégrés entre les deux solutions.

## Conditions préalables requises {#prerequisites}

* Droits d’administrateur vers Experience Manager Assets

* Droits actifs à Creative Cloud pour le même identifiant utilisateur utilisé dans Creative Cloud et Experience Manager. Les droits aux ID personnels et fédérés ayant la même adresse électronique sont traités comme des ID utilisateur différents.

## Connexion à une nouvelle organisation de Creative Cloud {#connect-to-creative-cloud-org}

Pour vous connecter à une nouvelle organisation de Creative Cloud, procédez comme suit :

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Creative Cloud]**.

1. Sélectionnez la nouvelle organisation du Creative Cloud à l’aide de la fonction **[!UICONTROL Sélectionner un nouvel ID d’organisation de Creative Cloud]** liste déroulante. La liste affiche toutes les organisations auxquelles vous avez accès. Sélectionnez l’organisation avec des droits de Creative Cloud actifs.

1. Cliquez sur **[!UICONTROL Changement d’organisation]** pour passer à la nouvelle organisation.

   ![Droits inter-organisations](assets/cross-org-entitlements.png)

## Limites {#limitations}

* Vous pouvez connecter AEM Assets à une organisation Creative Cloud à la fois. La connexion à plusieurs organisations de Creative Cloud à la fois n’est pas prise en charge.

* L’organisation de Creative Cloud à laquelle vous vous connectez dans AEM Assets s’applique à tous les utilisateurs de votre entreprise.

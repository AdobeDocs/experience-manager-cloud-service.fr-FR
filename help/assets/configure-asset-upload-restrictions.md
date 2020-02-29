---
title: Configuration des restrictions de chargement des ressources
description: Découvrez comment configurer Adobe Experience Manager (AEM) Assets de sorte que le type de ressources (fichiers) que les utilisateurs peuvent télécharger soit limité.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Configuration des restrictions de chargement des ressources {#configuring-asset-upload-restrictions}

Vous pouvez configurer Adobe Experience Manager (AEM) Assets de sorte que le type de ressources (fichiers) que les utilisateurs peuvent charger soit limité. Cette fonctionnalité permet d’éviter que les utilisateurs ne chargent des ressources dans un format indésirable ou qu’ils ne chargent des fichiers malveillants. The `Day CQ DAM Asset Upload Restriction` service enables you to control the type of files that users can upload. Par défaut, AEM Assets permet aux utilisateurs de charger des ressources quel que soit leur type MIME. Cependant, vous pouvez configurer le service pour empêcher les utilisateurs de charger des fichiers disposant de types MIME spécifiques.

1. Ouvrez la console Web Configuration Manager. Accès `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Day CQ DAM Asset Upload Restriction]** service in Edit mode. By default, the **Allow all MIME** option is selected, which allows users to upload files of all MIME types.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Pour empêcher les utilisateurs de charger des fichiers de certains types MIME uniquement, désélectionnez l’option **[!UICONTROL Autoriser tous les types MIME]** et spécifiez les types MIME autorisés dans les champs **[!UICONTROL Types MIME autorisés pour les ressources (regex)]** à l’aide d’expressions régulières.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Cliquez/appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications. Si vous spécifiez des chaînes MIME pour les types MIME autorisés, l’opération de transfert échoue pour tout fichier dont le type MIME ne correspond pas aux chaînes MIME configurées dans ces champs.

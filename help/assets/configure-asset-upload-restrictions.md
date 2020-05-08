---
title: Configuration des restrictions de chargement des ressources
description: Découvrez comment configurer Adobe Experience Manager (AEM) Assets de sorte que le type de ressources (fichiers) que les utilisateurs peuvent télécharger soit limité.
contentOwner: AG
translation-type: ht
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Configuration des restrictions de chargement des ressources {#configuring-asset-upload-restrictions}

Vous pouvez configurer Adobe Experience Manager (AEM) Assets de sorte que le type de ressources (fichiers) que les utilisateurs peuvent charger soit limité. Cette fonctionnalité permet d’éviter que les utilisateurs ne chargent des ressources dans un format indésirable ou qu’ils ne chargent des fichiers malveillants. Le service `Day CQ DAM Asset Upload Restriction` (Restriction de chargement des ressources de la gestion des ressources numériques Day CQ) permet de contrôler le type de fichiers que les utilisateurs peuvent charger. Par défaut, AEM Assets permet aux utilisateurs de charger des ressources quel que soit leur type MIME. Cependant, vous pouvez configurer le service pour empêcher les utilisateurs de charger des fichiers disposant de types MIME spécifiques.

1. Ouvrez la console web Configuration Manager. Accédez à l’adresse `https://[aem_server]:[port]/system/console/configMgr`.
1. Ouvrez le service **[!UICONTROL Day CQ DAM Asset Upload Restriction]** en mode d’édition. Par défaut, la case **Autoriser tous les MIME** est cochée, ce qui permet aux utilisateurs de charger des fichiers quel que soit leur type MIME.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Pour empêcher les utilisateurs de charger des fichiers disposant de certains types MIME, désactivez l’option **[!UICONTROL Allow all MIME]** et spécifiez les types MIME autorisés dans les champs **[!UICONTROL Allowed Asset MIMEs (regex)]** (MIME de ressources autorisés) à l’aide d’expressions régulières.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Cliquez ou appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications. Si vous spécifiez des chaînes MIME pour les types MIME autorisés, l’opération de chargement échoue pour toute ressource de type MIME qui ne correspond pas aux chaînes MIME configurées dans ces champs.

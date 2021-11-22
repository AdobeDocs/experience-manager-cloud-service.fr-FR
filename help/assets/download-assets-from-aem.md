---
title: Téléchargement de ressources
description: Téléchargez des ressources depuis [!DNL Adobe Experience Manager Assets] et activez ou désactivez la fonctionnalité de téléchargement.
contentOwner: AG
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: 8ec0ce3425e7cade0a6774a4452d4f47ab971375
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 97%

---

# Téléchargement de ressources depuis [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Vous pouvez télécharger des ressources, dont des rendus statiques et dynamiques. Vous pouvez également envoyer des liens vers des ressources par courrier électronique, directement depuis [!DNL Adobe Experience Manager Assets]. Les ressources téléchargées sont compressées dans un fichier ZIP. <!-- The compressed ZIP file has a maximum file size of 1 GB for the export job. A maximum of 500 total assets per export job are allowed. -->

>[!NOTE]
>
>Les destinataires du courrier électronique doivent être membres du groupe `dam-users` pour accéder au lien de téléchargement ZIP contenu dans le message. Pour télécharger les ressources, ils doivent disposer des autorisations de lancement des workflows qui déclenchent le téléchargement.

Les types de ressources Visionneuses d’images, Visionneuses à 360°, Visionneuses de supports variés et Visionneuses de carrousel ne peuvent pas être téléchargés.

Vous pouvez télécharger des ressources Experience Manager à l’aide des méthodes suivantes :

<!-- * [Link Share](#link-share-download) -->

* [Interface utilisateur d’Experience Manager](#download-assets)
* [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html?lang=fr)
* [Appli de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#download-assets)

## Téléchargement de ressources à l’aide de l’interface [!DNL Experience Manager]  {#download-assets}

Le service de téléchargement asynchrone fournit un framework permettant le téléchargement transparent de ressources de grande taille. Les fichiers plus petits sont téléchargés en temps réel depuis l’interface utilisateur. [!DNL Experience Manager] n’archive pas les téléchargements de ressources uniques où le fichier d’origine est téléchargé. Cette fonctionnalité permet des téléchargements plus rapides. Les fichiers volumineux sont téléchargés de manière asynchrone et [!DNL Experience Manager] notifie l’achèvement de l’opération par le biais de notifications dans la boîte de réception. Voir la section [comprendre la Boîte de réception [!DNL Experience Manager]  ](/help/sites-cloud/authoring/getting-started/inbox.md).

![Notification de téléchargement](assets/download-notification.png)

*Figure : Notification de téléchargement via la boîte de réception d’[!DNL Experience Manager].*

Les téléchargements asynchrones sont déclenchés dans l’un ou l’autre des cas suivants :

* S’il y a plus de 10 ressources ou plus de 100 Mo à télécharger.
* Si la préparation du téléchargement prend plus de 30 secondes.

Pour télécharger des ressources, procédez comme suit :

1. Dans l’interface utilisateur d’[!DNL Experience Manager], cliquez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Accédez aux ressources à télécharger. Sélectionnez le dossier ou une ou plusieurs ressources qu’il contient. Dans la barre d’outils, cliquez sur **[!UICONTROL Télécharger]**.

   ![Options disponibles lors du téléchargement de ressources à partir d’[!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

   *Figure : Options de la boîte de dialogue Télécharger.*

1. Dans la boîte de dialogue Télécharger, sélectionnez les options de téléchargement de votre choix.

   | Option de téléchargement | Description |
   |---|---|
   | **[!UICONTROL Créer un dossier distinct pour chaque ressource]** | Sélectionnez cette option pour inclure chaque ressource que vous téléchargez (y compris les ressources dans des dossiers enfants imbriqués sous le dossier parent de la ressource) dans un dossier sur votre ordinateur local. Lorsque cette option *n’est pas* sélectionnée, par défaut, la hiérarchie de dossiers est ignorée et toutes les ressources sont téléchargées dans un dossier de votre ordinateur local. |
   | **[!UICONTROL Courrier électronique]** | Sélectionnez cette option pour envoyer une notification par email au destinataire. Les modèles standard d’email sont disponibles aux emplacements suivants :<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> Les modèles que vous personnalisez lors du déploiement sont disponibles aux emplacements suivants : <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>Vous pouvez stocker des modèles personnalisés spécifiques au client à ces emplacements :<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Ressource(s)]** | Sélectionnez cette option pour télécharger la ressource dans son format d’origine sans aucun rendu.<br>L’option Sous-ressources est disponible si la ressource d’origine comporte des sous-ressources. |
   | **[!UICONTROL Rendu(s)]** | Un rendu est une représentation binaire d’une ressource. Les ressources possèdent une représentation principale, à savoir celle du fichier transféré. Elles peuvent avoir un nombre illimité de représentations. <br> Avec cette option, vous pouvez sélectionner les rendus que vous souhaitez télécharger. Les rendus disponibles dépendent de la ressource que vous avez sélectionnée. |
   | **[!UICONTROL Recadrages intelligents]** | Sélectionnez cette option pour télécharger tous les rendus de recadrage intelligent de la ressource sélectionnée depuis [!DNL Experience Manager]. Un fichier zip contenant les rendus de recadrage intelligent est créé et téléchargé sur votre ordinateur local. |
   | **[!UICONTROL Rendu(s) dynamique(s)]** | Sélectionnez cette option pour générer une série de rendus alternatifs en temps réel. Lorsque vous sélectionnez cette option, vous sélectionnez également les rendus à créer dynamiquement dans la liste [Paramètre d’image prédéfini](/help/assets/dynamic-media/image-presets.md). <br>De plus, vous pouvez sélectionner la taille, l’unité de mesure, le format, l’espace colorimétrique, la résolution, ainsi que les éventuels modificateurs d’image (pour inverser l’image, par exemple). Cette option n’est disponible que si vous avez activé [!DNL Dynamic Media]. |

1. Dans la boîte de dialogue, cliquez sur **[!UICONTROL Télécharger]**.

## Téléchargement de ressources partagées à l’aide du partage de liens {#link-share-download}

>[!NOTE]
>
>Cette fonctionnalité est disponible dans le canal de version préliminaire d’Experience Manager.

Le partage de ressources au moyen d’un lien est très pratique pour le mettre à disposition des personnes intéressées sans avoir besoin de se connecter au préalable à [!DNL Assets]. Pour générer une URL permettant de partager des ressources, utilisez la fonction [Partage de liens](/help/assets/share-assets.md#sharelink).

Lorsque les utilisateurs téléchargent des ressources à partir de liens partagés, [!DNL Assets] utilise un service asynchrone qui offre des téléchargements plus rapides et ininterrompus. Les ressources à télécharger sont placées en file d’attente en arrière-plan dans une boîte de réception dans les archives ZIP de taille de fichier gérable. Pour les téléchargements très volumineux, le téléchargement est divisé en fichiers de 100 Go.

La boîte de réception affiche l’état du traitement de chaque archive. Une fois le traitement terminé, vous pouvez télécharger les archives à partir de la boîte de réception.

![Boîte de réception de téléchargement](assets/download-inbox.png)

## Activation du servlet de téléchargement de ressources {#enable-asset-download-servlet}

Le servlet par défaut d’[!DNL Experience Manager] permet aux utilisateurs authentifiés d’émettre des demandes de téléchargement simultanées de grande taille et de taille arbitraire afin de créer des fichiers ZIP de ressources. La préparation des téléchargements peut avoir des conséquences sur les performances ou peut même surcharger le serveur et le réseau. Pour atténuer ces risques potentiels de déni de service, le composant OSGi `AssetDownloadServlet` est désactivé par défaut pour les instances de publication. Si vous n’avez pas besoin de la fonction de téléchargement sur les instances d’auteur, désactivez le servlet sur l’auteur.

Pour permettre le téléchargement de fichiers depuis votre DAM (par exemple, lorsque vous utilisez un élément comme Asset Share Commons ou une autre implémentation de type portail), activez manuellement le servlet via une configuration OSGi. Adobe recommande de définir la taille de téléchargement autorisée sur la valeur la plus basse possible sans affecter les exigences de téléchargement au quotidien. Une valeur élevée peut avoir une incidence sur les performances.

1. Créez un dossier avec une convention d’affectation de noms qui cible le mode d’exécution de publication, à savoir `config.publish` :

   `/apps/<your-app-name>/config.publish`

1. Dans le dossier de configuration, créez un fichier de type `nt:file` nommé `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Remplissez `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` avec les éléments suivants. Définit une taille maximale (en octets) pour le téléchargement en tant que valeur de `asset.download.prezip.maxcontentsize`. L’exemple ci-dessous configure la taille maximale du téléchargement ZIP pour qu’il ne dépasse pas 100 Ko.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Désactivation du servlet de téléchargement de ressources {#disable-asset-download-servlet}

Si vous n’avez pas besoin de la fonctionnalité de téléchargement, désactivez le servlet pour éviter tout risque de déni de service. Le `Asset Download Servlet` peut être désactivé sur les instances d’auteur et de publication d’[!DNL Experience Manager] en mettant à jour la configuration du Dispatcher afin de bloquer toute demande de téléchargement de ressources. Le servlet peut également être désactivé manuellement par l’intermédiaire de la console OSGi.

1. Pour bloquer les requêtes de téléchargement de ressources via une configuration de Dispatcher, modifiez la configuration `dispatcher.any` et ajoutez une nouvelle règle à la [section /filter](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#configuring).

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

## Conseils et restrictions {#tips-limitations}

* Si vous téléchargez un dossier vide, [!DNL Experience Manager] transmet un message de réussite sur la création d’une archive ZIP, mais l’archive n’est pas créée.

>[!MORELIKETHIS]
>
>* [Téléchargement de ressources protégées par DRM](drm.md)
>* [Téléchargement de ressources à l’aide de l’appli de bureau Experience Manager sur un poste de travail Windows ou Mac](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr)
>* [Téléchargement de ressources à l’aide d’Adobe Assets Link depuis les applications Adobe Creative Cloud prises en charge](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html)


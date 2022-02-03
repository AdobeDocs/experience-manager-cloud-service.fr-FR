---
title: Téléchargement de ressources
description: Téléchargez des ressources depuis [!DNL Adobe Experience Manager Assets] et activez ou désactivez la fonctionnalité de téléchargement.
contentOwner: Vishabh Gupta
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: ddc79a163e328d560912550900242cc089df3958
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 68%

---

# Téléchargement de ressources depuis [!DNL Adobe Experience Manager] {#download-assets-from-aem}

Vous pouvez télécharger des ressources, dont des rendus statiques et dynamiques. Vous pouvez également envoyer des liens vers des ressources par courrier électronique, directement depuis [!DNL Adobe Experience Manager Assets]. Les ressources téléchargées sont compressées dans un fichier ZIP. <!-- The compressed ZIP file has a maximum file size of 1 GB for the export job. A maximum of 500 total assets per export job are allowed. -->

<!--
>[!NOTE]
>
>Recipients of emails must be members of the `dam-users` group to access the ZIP download link in the email message. To be able to download the assets, the members must have permissions to launch workflows that trigger downloading of assets.
-->

Les types de ressources Visionneuses d’images, Visionneuses à 360°, Visionneuses de supports variés et Visionneuses de carrousel ne peuvent pas être téléchargés.

Vous pouvez télécharger des ressources Experience Manager à l’aide des méthodes suivantes :

<!-- * [Link Share](#link-share-download) -->

* [Interface utilisateur d’Experience Manager](#download-assets)
* [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html?lang=fr)
* [Appli de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#download-assets)

## Téléchargement de ressources à l’aide de l’interface [!DNL Experience Manager]  {#download-assets}

Le service de téléchargement asynchrone fournit un framework permettant le téléchargement transparent de ressources de grande taille. Les archives de téléchargement de plus de 100 Go se divisent en plusieurs archives zip d’une taille maximale de 100 Go chacune. Ils peuvent être téléchargés individuellement. Les fichiers plus petits sont téléchargés en temps réel à partir de l’interface utilisateur. [!DNL Experience Manager] n’archive pas les téléchargements de ressources uniques où le fichier d’origine est téléchargé. Cette fonctionnalité permet des téléchargements plus rapides.

Par défaut, [!DNL Experience Manager] déclenche une notification à la fin du processus de téléchargement. La notification de téléchargement apparaît dans la variable  [[!DNL Experience Manager] Boîte de réception](/help/sites-cloud/authoring/getting-started/inbox.md).

![Notification de boîte de réception](assets/inbox-notification-for-large-downloads.png)


### Activation des notifications par e-mail pour les téléchargements volumineux {#enable-emails-for-large-downloads}

>[!NOTE]
>
>Cette fonctionnalité est disponible dans le canal de version préliminaire. Voir [Documentation sur les canaux de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) pour plus d’informations sur l’activation de la fonctionnalité dans votre environnement.

Les téléchargements asynchrones sont déclenchés dans l’un des cas suivants :

* S’il y a plus de dix ressources
* Si la taille de téléchargement est supérieure à 100 Mo
* Si la préparation du téléchargement prend plus de 30 secondes

Bien que le téléchargement asynchrone s’exécute sur le serveur principal, l’utilisateur peut continuer à explorer et à travailler plus loin en Experience Manager. Un mécanisme prêt à l’emploi est nécessaire pour informer l’utilisateur une fois le processus de téléchargement terminé. Pour atteindre cet objectif, les administrateurs peuvent configurer le service de messagerie électronique en configurant un serveur SMTP. Voir [configurer le service de messagerie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#sending-email).

Une fois le service de messagerie configuré, les administrateurs et les utilisateurs peuvent activer les notifications électroniques à partir de l’interface du Experience Manager.

Pour activer les notifications par courrier électronique :

1. Connectez-vous à [!DNL Experience Manager Assets].
1. Cliquez sur l’icône de l’utilisateur dans le coin supérieur droit, puis cliquez sur **[!UICONTROL Mes préférences]**. La fenêtre Préférences utilisateur s’ouvre.
1. Sélectionnez la **[!UICONTROL Notifications électroniques de téléchargement de ressources]** , puis cliquez sur **[!UICONTROL Accepter]**.

   ![enable-email-notifications-for-big-downloads](/help/assets/assets/enable-email-for-large-downloads.png)


Pour télécharger des ressources, procédez comme suit :

1. Dans l’interface utilisateur d’[!DNL Experience Manager], cliquez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Accédez aux ressources à télécharger. Sélectionnez le dossier ou une ou plusieurs ressources qu’il contient. Dans la barre d’outils, cliquez sur **[!UICONTROL Télécharger]**.

   ![Options disponibles lors du téléchargement de ressources à partir d’[!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

1. Dans la boîte de dialogue Télécharger, sélectionnez les options de téléchargement de votre choix.

   | Option de téléchargement | Description |
   |---|---|
   | **[!UICONTROL Créer un dossier distinct pour chaque ressource]** | Sélectionnez cette option pour inclure chaque ressource que vous téléchargez (y compris les ressources dans des dossiers enfants imbriqués sous le dossier parent de la ressource) dans un dossier sur votre ordinateur local. Lorsque cette option *n’est pas* sélectionnée, par défaut, la hiérarchie de dossiers est ignorée et toutes les ressources sont téléchargées dans un dossier de votre ordinateur local. |
   | **[!UICONTROL Courrier électronique]** | Sélectionnez cette option pour envoyer une notification par e-mail (contenant un lien vers votre téléchargement) à un autre utilisateur. L’utilisateur du destinataire doit être membre de la `dam-users` groupe. Les modèles standard d’email sont disponibles aux emplacements suivants :<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> Les modèles que vous personnalisez lors du déploiement sont disponibles aux emplacements suivants : <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>Vous pouvez stocker des modèles personnalisés spécifiques au client à ces emplacements :<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Ressource(s)]** | Sélectionnez cette option pour télécharger la ressource dans son format d’origine sans aucun rendu.<br>L’option Sous-ressources est disponible si la ressource d’origine comporte des sous-ressources. |
   | **[!UICONTROL Rendu(s)]** | Un rendu est une représentation binaire d’une ressource. Les ressources possèdent une représentation principale, à savoir celle du fichier transféré. Elles peuvent avoir un nombre illimité de représentations. <br> Avec cette option, vous pouvez sélectionner les rendus que vous souhaitez télécharger. Les rendus disponibles dépendent de la ressource que vous avez sélectionnée. |
   | **[!UICONTROL Recadrages intelligents]** | Sélectionnez cette option pour télécharger tous les rendus de recadrage intelligent de la ressource sélectionnée depuis [!DNL Experience Manager]. Un fichier zip contenant les rendus de recadrage intelligent est créé et téléchargé sur votre ordinateur local. |
   | **[!UICONTROL Rendu(s) dynamique(s)]** | Sélectionnez cette option pour générer une série de rendus alternatifs en temps réel. Lorsque vous sélectionnez cette option, vous sélectionnez également les rendus à créer dynamiquement dans la liste [Paramètre d’image prédéfini](/help/assets/dynamic-media/image-presets.md). <br>De plus, vous pouvez sélectionner la taille, l’unité de mesure, le format, l’espace colorimétrique, la résolution, ainsi que les éventuels modificateurs d’image (pour inverser l’image, par exemple). Cette option n’est disponible que si vous avez activé [!DNL Dynamic Media]. |

1. Dans la boîte de dialogue, cliquez sur **[!UICONTROL Télécharger]**.

   Si la notification électronique est activée pour les téléchargements volumineux, un message électronique contenant l’URL de téléchargement du dossier zip archivé s’affiche dans votre boîte de réception. Cliquez sur le lien de téléchargement de l’e-mail pour télécharger le dossier zip.

   ![email-notifications-for-big-downloads](/help/assets/assets/email-for-large-notification.png)

   Vous pouvez également afficher la notification dans votre [!DNL Experience Manager] Boîte de réception.

   ![inbox-notifications-for-big-downloads](/help/assets/assets/inbox-notification-for-large-downloads.png)

## Téléchargement de ressources partagées à l’aide du partage de liens {#link-share-download}

Le partage de ressources à l’aide d’un lien est un moyen pratique de le mettre à la disposition des personnes intéressées sans qu’elles aient à se connecter à [!DNL Assets]. Voir [Fonctionnalité Partage de liens](/help/assets/share-assets.md#sharelink).

Lorsque les utilisateurs téléchargent des ressources à partir de liens partagés, [!DNL Assets] utilise un service asynchrone qui offre des téléchargements plus rapides et ininterrompus. Les ressources à télécharger sont placées en file d’attente en arrière-plan dans une boîte de réception dans les archives ZIP de taille de fichier gérable. Pour les téléchargements très volumineux, le téléchargement est divisé en fichiers de 100 Go.

Le [!UICONTROL Télécharger la boîte de réception] affiche l’état du traitement de chaque archive. Une fois le traitement terminé, vous pouvez télécharger les archives à partir de la boîte de réception.

![Boîte de réception de téléchargement](assets/link-sharing-download-inbox.png)

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


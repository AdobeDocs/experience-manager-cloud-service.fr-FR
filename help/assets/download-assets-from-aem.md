---
title: Téléchargement de ressources à partir d’AEM
description: Découvrez comment télécharger des ressources à partir d’AEM et activer ou désactiver la fonctionnalité de téléchargement.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c978be66702b7f032f78a1509f2a11315d1ed89f
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 98%

---


# Téléchargement de ressources à partir d’AEM {#download-assets-from-aem}

Vous pouvez télécharger des ressources, dont des rendus statiques et dynamiques. Les ressources téléchargées sont compressées dans un fichier ZIP. La taille maximale du fichier ZIP compressé est de 1 Go pour la tâche d’exportation. 500 ressources, au maximum, sont autorisées par tâche d’exportation.

>[!NOTE]
>
>Pour télécharger les ressources, ils doivent disposer des autorisations de lancement des workflows qui déclenchent le téléchargement.

Pour télécharger une ressource, vous devez y accéder, la sélectionner, puis appuyer/cliquer sur l’icône **[!UICONTROL Télécharger]** dans la barre d’outils. Spécifiez vos options de téléchargement dans la boîte de dialogue qui s’affiche.

Les types de ressources Visionneuses d’images, Visionneuses à 360°, Visionneuses de supports variés et Visionneuses de carrousel ne peuvent pas être téléchargés.

![Options disponibles lors du téléchargement de ressources à partir d’AEM Assets](assets/asset_download_dialog.png)

*Figure : Options disponibles lors du téléchargement de ressources à partir d’AEM Assets.*

Vous trouverez ci-dessous les options d’exportation/de téléchargement disponibles. Les rendus dynamiques sont propres à Dynamic Media et vous permettent de générer des rendus à la volée, en plus de la ressource que vous avez sélectionnée (cette option est uniquement disponible lorsque Dynamic Media est activé).

| Options d’exportation ou de téléchargement | Descriptions |
|---|---|
| [!UICONTROL Ressources] | Sélectionnez cette option pour télécharger la ressource dans son format d’origine sans aucun rendu. |
| [!UICONTROL Rendus] | Un rendu est une représentation binaire d’une ressource. Les ressources possèdent une représentation principale, à savoir celle du fichier transféré. Elles peuvent avoir un nombre illimité de représentations. <br> Avec cette option, vous pouvez sélectionner les rendus que vous souhaitez télécharger. Les rendus disponibles dépendent de la ressource sélectionnée. |
| [!UICONTROL Rendus dynamiques] | Un rendu dynamique génère d’autres rendus à la volée. Lorsque vous sélectionnez cette option, vous sélectionnez également les rendus à créer dynamiquement dans la liste de paramètres d’image prédéfinis. De plus, vous pouvez sélectionner la taille, l’unité de mesure, le format, l’espace colorimétrique, la résolution, ainsi que les éventuels modificateurs d’image (pour inverser l’image, par exemple). |
| [!UICONTROL Créer un dossier distinct pour chaque ressource] | Sélectionnez cette option pour préserver la hiérarchie des dossiers lors du téléchargement des ressources. Par défaut, la hiérarchie des dossiers est ignorée et toutes les ressources sont téléchargées dans un dossier de votre système local. |

L’option des rendus d’option est disponible si la ressource comporte des rendus. L’option Sous-ressources est disponible si la ressource comporte des sous-ressources.

Lorsque vous sélectionnez un dossier à télécharger, l’ensemble de la hiérarchie des ressources sous ce dossier est téléchargé. Pour inclure chaque ressource que vous téléchargez (dont les ressources dans les dossiers enfants imbriqués sous le dossier parent) dans un dossier individuel, sélectionnez **[!UICONTROL Créer un dossier distinct pour chaque ressource]**.

## Activation du servlet de téléchargement de ressources {#enable-asset-download-servlet}

Le servlet par défaut d’AEM permet aux utilisateurs authentifiés d’émettre des demandes de téléchargement simultanées de grande taille pour créer des fichiers ZIP de ressources visibles, susceptibles de surcharger le serveur et le réseau. Pour atténuer les risques d’attaques par déni de service, le composant OSGi `AssetDownloadServlet` est désactivé par défaut pour les instances de publication.

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

Le `Asset Download Servlet` peut être désactivé sur une instance AEM Publish en mettant à jour la configuration du dispatcher afin de bloquer toute demande de téléchargement de ressources. Le servlet peut également être désactivé manuellement par l’intermédiaire de la console OSGi.

1. Pour bloquer les requêtes de téléchargement de ressources via une configuration de Dispatcher, modifiez la configuration `dispatcher.any` et ajoutez une nouvelle règle à la [section /filter](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter).

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [Téléchargement de ressources protégées par DRM](drm.md)
>* [Téléchargement de ressources à l’aide de l’application de bureau AEM sur un poste de travail Windows/Mac](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app.html)
>* [Téléchargement de ressources à l’aide d’Adobe Assets Link depuis les applications Adobe Creative Cloud prises en charge](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html)


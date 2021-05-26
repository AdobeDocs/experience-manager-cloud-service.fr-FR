---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour spécifiques aux fonctionnalités obsolètes et supprimées dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 725cc82aa5794b53e5a43d95359fe1fd148b59ac
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 45%

---

# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Fonctionnalités obsolètes et supprimées dans AEM en tant que Cloud Service"
>abstract="AEM en tant que Cloud Service dispose d’un modèle de déploiement natif dans le cloud. Certaines fonctionnalités ont été remplacées par des homologues natifs du cloud et cet onglet affiche ces fonctionnalités."


Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante. En outre, comme [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] fournit un modèle de déploiement natif dans le cloud, certaines fonctionnalités ont été remplacées par des homologues natives dans le cloud.

Pour signaler la suppression ou le remplacement imminent de [!DNL Experience Manager] fonctionnalités, les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Les fonctionnalités obsolètes restent disponibles, mais ne sont pas améliorées.
1. Les fonctionnalités annoncées comme obsolètes sont supprimées au plus tôt dans la version majeure qui suit. La date cible réelle de la suppression est annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été signalées comme étant obsolètes dans [!DNL Experience Manager] sous la forme [!DNL Cloud Service]. En règle générale, les fonctionnalités à supprimer dans une version ultérieure sont d’abord définies comme obsolètes, avec une alternative fournie.

Il est conseillé aux clients d’évaluer s’ils utilisent la fonctionnalité dans leur déploiement actuel et d’envisager de modifier leur mise en oeuvre afin d’utiliser l’alternative proposée.

| Fonctionnalités | Fonctionnalité obsolète | Remplacement |
| ------------ | ------------------ | ----------- |
| [!DNL Assets] | Workflow `DAM Asset Update` pour traiter les images ingérées. | L’assimilation de ressources utilise maintenant les [microservices de ressources](/help/assets/asset-microservices-overview.md). |
| [!DNL Assets] | Chargez des ressources directement dans [!DNL Experience Manager]. Voir [API de chargement de ressources obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Utilisez le [chargement de binaire direct](/help/assets/add-assets.md). Pour plus d’informations techniques, consultez [API de transfert direct](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Certaines étapes](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) du workflow `DAM Asset Update` ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que ImageMagick.. | [Les microservices de ressources](/help/assets/asset-microservices-overview.md) remplacent de nombreux workflows. Pour le traitement personnalisé, utilisez des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | Transcodage FFmpeg des vidéos. | Pour la génération de miniatures FFmpeg, utilisez les [microservices de ressources](/help/assets/asset-microservices-overview.md). Pour le transcodage FFmpeg, utilisez [Dynamic Media](/help/assets/manage-video-assets.md). |

## Fonctionnalités supprimées {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées de [!DNL Experience Manager] avec [!DNL Experience Manager] comme [!DNL Cloud Service].

| Zone | Fonctionnalité | Remplacement |
| ------------ | ------------------ | ----------- |
| Interface utilisateur | L’interface utilisateur classique est supprimée de l’interface utilisateur du produit. Quelques boîtes de dialogue d’interface utilisateur classique sont disponibles pour quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations de Cloud Service. Les [mises à jour de produit](/help/release-notes/home.md) à venir peuvent supprimer la disponibilité de l’interface utilisateur classique. | Interface utilisateur standard |
| [!DNL Dynamic Media] | Les intégrations précédentes avec [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=fr#integration) et le [mode hybride de Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=fr#dynamic)[!DNL Experience Manager] ne sont pas disponibles dans as a [!DNL Cloud Service]. | Utilisez [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) fourni avec [!DNL Experience Manager] comme [!DNL Cloud Service]. |
| [!DNL Sites] | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans [!DNL Experience Manager] 6.4 et ont été supprimées de [!DNL Experience Manager]. |
| [!DNL Sites] | Importateur de conception | Cette fonctionnalité a été supprimée, car les sections non modifiables du référentiel [!DNL Experience Manager] ne sont pas accessibles au moment de l’exécution. |
| [!DNL Assets] | [!DNL Assets] le partage avec Marketing Cloud Assets Core Service et les services Creative Cloud n’est pas disponible. | Pour l’intégration avec [!DNL Adobe Creative Cloud], utilisez [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html). |

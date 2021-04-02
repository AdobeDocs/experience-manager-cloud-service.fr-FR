---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour spécifiques aux fonctions obsolètes et supprimées de  [!DNL Adobe Experience Manager] en tant que  [!DNL Cloud Service].
translation-type: tm+mt
source-git-commit: e6ad571b7428f6fb7a11907e752ba670a722057c
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 49%

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante. En outre, comme [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] fournit un modèle de déploiement natif au cloud, certaines capacités et fonctionnalités ont été remplacées par des équivalents natifs au cloud.

Pour communiquer la suppression ou le remplacement imminent des capacités [!DNL Experience Manager], les règles suivantes s&#39;appliquent :

1. L’annonce de la suppression arrive en premier. Des capacités obsolètes demeurent disponibles, mais ne sont pas encore améliorées.
1. Les fonctionnalités annoncées comme obsolètes sont supprimées au plus tôt dans la version majeure qui suit. La date cible réelle de la suppression est annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Cette section liste les fonctionnalités qui ont été marquées comme obsolètes dans [!DNL Experience Manager] en tant que [!DNL Cloud Service]. En règle générale, les fonctions à supprimer dans une version ultérieure sont définies comme obsolètes en premier, avec une alternative fournie.

Il est conseillé aux clients de vérifier s’ils utilisent la fonctionnalité ou la fonctionnalité dans leur déploiement actuel et de planifier la modification de leur mise en oeuvre pour utiliser l’alternative fournie.

| Fonctionnalités | Fonctionnalité obsolète | Remplacement |
| ------------ | ------------------ | ----------- |
| [!DNL Assets] | Workflow `DAM Asset Update` pour traiter les images ingérées. | L’assimilation de ressources utilise maintenant les [microservices de ressources](/help/assets/asset-microservices-overview.md). |
| [!DNL Assets] | Téléchargez des ressources directement vers [!DNL Experience Manager]. Voir [API de transfert de ressources obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Utilisez le [chargement de binaire direct](/help/assets/add-assets.md). Pour plus d’informations techniques, consultez [API de transfert direct](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Certaines étapes](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) du workflow `DAM Asset Update` ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que ImageMagick.. | [Les microservices de ressources](/help/assets/asset-microservices-overview.md) remplacent de nombreux workflows. Pour le traitement personnalisé, utilisez des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | Transcodage FFmpeg des vidéos. | Pour la génération de miniatures FFmpeg, utilisez les [microservices de ressources](/help/assets/asset-microservices-overview.md). Pour le transcodage FFmpeg, utilisez [Dynamic Media](/help/assets/manage-video-assets.md). |

## Fonctionnalités supprimées {#removed-features}

Cette section liste les fonctionnalités et fonctionnalités qui ont été supprimées de [!DNL Experience Manager] avec [!DNL Experience Manager] comme [!DNL Cloud Service].

| Zone | Fonctionnalité | Remplacement |
| ------------ | ------------------ | ----------- |
| Interface utilisateur | L’interface utilisateur classique est supprimée de l’interface utilisateur du produit. Quelques boîtes de dialogue d’interface utilisateur classiques sont disponibles pour quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations de Cloud Service. Les [mises à jour de produits](/help/release-notes/home.md) à venir peuvent encore supprimer la disponibilité de l’interface utilisateur classique. | Interface utilisateur standard |
| [!DNL Dynamic Media] | Les intégrations précédentes avec [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=fr#integration) et le [mode hybride de Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=fr#dynamic)[!DNL Experience Manager] ne sont pas disponibles dans as a [!DNL Cloud Service]. | Utilisez [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) fourni avec [!DNL Experience Manager] comme [!DNL Cloud Service]. |
| [!DNL Sites] | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans [!DNL Experience Manager] 6.4 et ont maintenant été supprimées de [!DNL Experience Manager]. |
| [!DNL Sites] | Importateur de conception | Cette fonctionnalité a été supprimée car les sections non modifiables du référentiel [!DNL Experience Manager] ne sont pas accessibles au moment de l&#39;exécution. |
| [!DNL Assets] | [[!DNL Assets] partage avec Marketing Cloud Assets Core Service et les ](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/integration/configure-assets-cc-integration.html) services Creative Cloud non disponibles. | Pour l’intégration à [!DNL Adobe Creative Cloud], utilisez [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html). |

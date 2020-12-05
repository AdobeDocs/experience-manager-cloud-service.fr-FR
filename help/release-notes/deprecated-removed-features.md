---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans Adobe Experience Manager as a Cloud Service.
translation-type: tm+mt
source-git-commit: e31ac0c2d28f60d7b98036c16f154a09da51d6bf
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 92%

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante. En outre, comme Adobe Experience Manager as a Cloud Service fournit un modèle de déploiement natif au cloud, certaines capacités et fonctionnalités ont été remplacées par des homologues natives sur le cloud.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’AEM, les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Les capacités obsolètes demeurent disponibles, mais ne sont plus améliorées.
1. Les fonctionnalités annoncées comme obsolètes sont supprimées au plus tôt dans la version majeure qui suit. La date cible réelle de la suppression est annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été marquées comme obsolètes dans Experience Manager as a Cloud Service. En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont d’abord définies comme obsolètes, et une alternative est fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Fonctionnalités | Fonctionnalié obsolète | Remplacement |
| ------------ | ------------------ | ----------- |
| Assets | Workflow `DAM Asset Update` pour traiter les images ingérées. | L’assimilation de ressources utilise maintenant les [microservices de ressources](/help/assets/asset-microservices-overview.md). |
| Ressources | Chargement direct de ressources vers AEM. Voir [API de chargement de ressources obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Utilisez le [chargement de binaire direct](/help/assets/add-assets.md). Pour plus d’informations techniques, consultez [API de transfert direct](/help/assets/developer-reference-material-apis.md#upload-binary). |
| Ressources | [Certaines étapes](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) du workflow `DAM Asset Update` ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que ImageMagick.. | [Les microservices de ressources](/help/assets/asset-microservices-overview.md) remplacent de nombreux workflows. Pour le traitement personnalisé, utilisez des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| Ressources | Transcodage FFmpeg des vidéos. | Pour la génération de miniatures FFmpeg, utilisez les [microservices de ressources](/help/assets/asset-microservices-overview.md). Pour le transcodage FFmpeg, utilisez [Dynamic Media](/help/assets/manage-video-assets.md). |

## Fonctionnalités supprimées {#removed-features}

Cette section répertorie les capacités et fonctionnalités qui ont été supprimées d’AEM avec Experience Manager as a Cloud Service.

| Zone | Fonctionnalité | Remplacement |
| ------------ | ------------------ | ----------- |
| Interface utilisateur | Bien que certaines boîtes de dialogue de l’interface utilisateur classique restent pour l’instant réservées à quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations du Cloud Service, l’accès à l’interface utilisateur classique en général a été supprimé dans l’interface utilisateur du produit AEM. | Interface utilisateur standard |
| Dynamic Media | Les intégrations précédentes avec [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html#integration) et [le mode hybride Contenu multimédia dynamique](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html#dynamic) ne sont pas disponibles en AEM en tant que Cloud Service. | Utilisez [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) fourni avec Experience Manager as a Cloud Service. |
| Sites | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans AEM 6.4 et ont été supprimées d’AEM. |
| Sites | Importateur de conception | Cette fonctionnalité a été supprimée, car les sections non modifiables du référentiel AEM ne sont pas accessibles au moment de l’exécution. |
| Ressources | [Le partage d’AEM Assets avec le service principal Experience Cloud Assets et les services Creative Cloud](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/integration/configure-assets-cc-integration.html) n’est pas disponible. | Pour l’intégration à Creative Cloud, utilisez [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html). |

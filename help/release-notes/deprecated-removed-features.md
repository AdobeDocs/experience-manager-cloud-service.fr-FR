---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 459e6cbf91f9b7f995bd1fd9c8758962c41c9341
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 99%

---

# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Fonctionnalités obsolètes et supprimées dans AEM as a Cloud Service"
>abstract="AEM as a Cloud Service dispose d’un modèle de déploiement natif dans le cloud. Certaines fonctionnalités ont été remplacées par des homologues natifs du cloud et cet onglet affiche ces fonctionnalités."


Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante. En outre, comme [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] fournit un modèle de déploiement natif au cloud, certaines capacités et fonctionnalités ont été remplacées par des homologues natives sur le cloud.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’[!DNL Experience Manager], les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Les capacités obsolètes demeurent disponibles, mais ne sont plus améliorées.
1. Les fonctionnalités annoncées comme obsolètes sont supprimées au plus tôt dans la version majeure qui suit. La date cible réelle de la suppression est annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été marquées comme obsolètes dans [!DNL Experience Manager] as a [!DNL Cloud Service]. En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont d’abord définies comme obsolètes, et une alternative est fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Fonctionnalités | Fonctionnalité obsolète | Remplacement |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | Propriétés des fragments d’expérience pour **Statut des médias sociaux**. | La fonctionnalité sera bientôt supprimée. |
| [!DNL Sites] | Fragments de contenu simples basés sur des modèles. | [Fragments de contenu structuré basés sur des modèles](/help/assets/content-fragments/content-fragments-models.md) maintenant. |
| [!DNL Assets] | Workflow `DAM Asset Update` pour traiter les images ingérées. | L’assimilation de ressources utilise maintenant les [microservices de ressources](/help/assets/asset-microservices-overview.md). |
| [!DNL Assets] | Chargement direct de ressources vers [!DNL Experience Manager]. Consultez [API de chargement de ressources obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Utilisez le [chargement de binaire direct](/help/assets/add-assets.md). Pour plus d’informations techniques, consultez [API de transfert direct](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Certaines étapes](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) du workflow `DAM Asset Update` ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que [!DNL ImageMagick]. | [Les microservices de ressources](/help/assets/asset-microservices-overview.md) remplacent de nombreux workflows. Pour le traitement personnalisé, utilisez des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | Transcodage FFmpeg des vidéos. | Pour la génération de miniatures FFmpeg, utilisez les [microservices de ressources](/help/assets/asset-microservices-overview.md). Pour le transcodage FFmpeg, utilisez [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | Interface utilisateur de réplication de l’arborescence sous l’onglet Distribuer de l’agent de réplication (suppression après le 30 septembre 2021) | Approches [Gérer la publication](/help/operations/replication.md#manage-publication) ou [Workflow de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) |
| [!DNL Foundation] | Ni l’onglet Distribution de l’écran de l’administrateur de l’agent de réplication, ni l’API de réplication ne peuvent être utilisés pour répliquer des packages de contenu de plus de 10 Mo (application après le 12 septembre 2022). | Approches [Gérer la publication](/help/operations/replication.md#manage-publication) ou [Workflow de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) |


| [!DNL Foundation] | Ni l’onglet Distribution de l’écran de l’administrateur de l’agent de réplication, ni l’API de réplication ne peuvent être utilisés pour répliquer les packages de contenu de plus de 10 Mo. Utilisez plutôt l’une des méthodes suivantes : [Gérer la publication](/help/operations/replication.md#manage-publication) ou [workflow Publier l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) |

## Fonctionnalités supprimées {#removed-features}

Cette section répertorie les capacités et fonctionnalités qui ont été supprimées d’[!DNL Experience Manager] avec [!DNL Experience Manager] as a [!DNL Cloud Service].

| Domaine | Fonctionnalité | Remplacement | Date de suppression visée |
| ------------ | ------------------ | ----------- | ------------------- |
| Interface utilisateur | L’interface utilisateur Classic est supprimée de l’interface utilisateur du produit. Quelques boîtes de dialogue d’interface utilisateur Classic sont disponibles pour quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations de Cloud Service. Les [mises à jour de produit](/help/release-notes/home.md) à venir peuvent supprimer la disponibilité de l’interface utilisateur Classic. | Interface utilisateur standard | Supprimé |
| [!DNL Dynamic Media] | Les intégrations précédentes avec [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=fr#integration) et le [mode hybride de Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=fr#dynamic) ne sont pas disponibles dans [!DNL Experience Manager] as a [!DNL Cloud Service]. | Utilisez [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) fourni avec [!DNL Experience Manager] as a [!DNL Cloud Service]. | Supprimé |
| [!DNL Sites] | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans [!DNL Experience Manager] 6.4 et ont été supprimées d’[!DNL Experience Manager]. | Supprimé |
| [!DNL Sites] | Importateur de conception | Cette fonctionnalité a été supprimée, car les sections non modifiables du référentiel de [!DNL Experience Manager] ne sont pas accessibles au moment de l’exécution. | Supprimé |
| [!DNL Assets] | Le partage d’[!DNL Assets] avec le service principal Experience Cloud Assets et les services Creative Cloud n’est pas disponible. | Pour l’intégration à [!DNL Adobe Creative Cloud], utilisez [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html). | Supprimé |
| [!DNL Foundation] | Prise en charge des sources de données Apache Sling (offre spéciale OSGi org.apache.sling.datasource) | S/O | Supprimé |
| [!DNL Foundation] | Prise en charge des modèles de script JST (offre spéciale OSGi org.apache.sling.scripting.jst) | S/O | Supprimé |
| [!DNL Foundation] | Prise en charge d’Apache Felix Http Whiteboard | OSGi Http Whiteboard | Mars 2022 |
| [!DNL Foundation] | Prise en charge de com.adobe.granite.oauth.server | Intégration Adobe IMS |  mars 2023 |


## API Java {#java-api}

Voir [cette page](/help/release-notes/deprecated-apis.md) pour toutes les API Java obsolètes ou supprimées, qui sont parfois introduites.

## Configuration OSGI {#osgi-configuration}

Voir [cet article](/help/implementing/deploying/osgi-configuration-api.md) pour connaître toutes les restrictions concernant la configuration des propriétés OSGI, dont certaines peuvent être introduites au fil du temps.

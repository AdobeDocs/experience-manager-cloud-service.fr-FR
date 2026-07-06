---
title: Configuration d’un domaine personnalisé pour le niveau de diffusion
description: Découvrez comment configurer un domaine personnalisé pour le niveau de diffusion dans Adobe Cloud Manager.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 230ca753bd5f3d5b26b30a962a526dc0edfc9bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 14%

---


# Configuration d’un domaine personnalisé pour le niveau de diffusion{#configure-custom-domain}

Dans Adobe Cloud Manager, vous pouvez faire en sorte que votre site web se démarque en ajoutant un domaine personnalisé. Bien qu’AEM as a Cloud Service soit fourni avec un domaine par défaut, vous pouvez le personnaliser en fonction de vos besoins.

>[!NOTE]
>
>Les clients disposant de licences Dynamic Media Prime ou Dynamic Media Ultimate doivent utiliser la configuration de domaine personnalisé en libre-service disponible dans Cloud Manager.Pour plus d’informations, consultez la [documentation de Dynamic Media Prime et d’Ultimate](/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md#configure-custom-domain-in-delivery-tier).
>
>Les clients qui utilisent d’anciennes configurations de Dynamic Media dans lesquelles Dynamic Media avec OpenAPI est activé manuellement doivent suivre cette documentation. Pour ces configurations, le mappage de domaine personnalisé est effectué par le biais d’une demande d’assistance Adobe.

## Préparez-vous à démarrer

Assurez-vous de répondre aux exigences suivantes avant de démarrer le processus de configuration :

* Accès à Cloud Manager
* Déjà activé Dynamic Media avec OpenAPI dans votre environnement via un ticket d’assistance
* Certificat SSL de type EV ou OV pour le domaine utilisé dans le niveau de diffusion. Voir [&#x200B; Présentation des certificats SSL &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates) pour plus d’informations

## Configuration d’un domaine personnalisé dans le niveau de diffusion à l’aide de Cloud Manager

Exécutez les étapes suivantes dans Cloud Manager :

1. [Ajouter un certificat SSL géré par le client](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate#add-customer-managed-ssl-cert)

2. [Ajouter un nom de domaine personnalisé](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name#adding-cdn-settings)

Après avoir suivi les étapes ci-dessus, ouvrez un ticket d’assistance Adobe pour le mappage de domaine personnalisé. Adobe effectue le mappage de domaine dans le cadre du processus de prise en charge.

**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

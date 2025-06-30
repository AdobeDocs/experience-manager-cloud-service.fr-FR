---
title: Flux d’activité dans la chronologie
description: Cet article décrit comment afficher les journaux d’activité pour les ressources de la chronologie.
contentOwner: AG
feature: Asset Reports, Asset Management
role: Admin, User
exl-id: 8dd82c31-f88e-4407-9b6d-c87033d7a823
hide: true
hidefromtoc: true
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 100%

---

# Affichage des journaux d’opération de ressource dans le flux d’activité {#activity-stream-in-timeline}

Cette fonctionnalité affiche les journaux d’activités correspondant aux ressources de la chronologie. Si vous effectuez les opérations liées aux ressources suivantes dans [!DNL Experience Manager Assets], la fonction de flux d’activités met à jour la chronologie afin de refléter l’activité.

Les opérations suivantes sont consignées dans le flux d’activités :

* Créer
* Supprimer
* Télécharger (y compris les rendus)
* Publication
* Dépublier
* Approuver
* Rejeter
* Déplacer

Les journaux d’activité à afficher dans la chronologie sont récupérés à partir de l’emplacement `/var/audit/com.day.cq.dam/content/dam` dans CRX, où les fichiers journaux sont stockés. De plus, l’activité de la chronologie est consignée lorsque de nouvelles ressources sont chargées ou que des ressources existantes sont modifiées et archivées dans [!DNL Experience Manager] via [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html) ou l’application de bureau [[!DNL Experience Manager] ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=fr).

>[!NOTE]
>
>Les workflows transitoires ne sont pas affichés dans la chronologie, car aucune information d’historique n’est enregistrée pour ces derniers.

Pour afficher le flux d’activités, effectuez une ou plusieurs des opérations sur la ressource, sélectionnez la ressource, puis sélectionnez **[!UICONTROL Chronologie]** dans la liste de navigation globale.

<!-- ![timeline-2](assets/timeline-2.png) -->

La chronologie affiche le flux d’activités des opérations que vous effectuez sur les ressources.

<!-- ![activity_stream](assets/activity_stream.png) -->

>[!NOTE]
>
>L’emplacement de stockage par défaut pour les tâches **[!UICONTROL Publier]** et **[!UICONTROL Dépublier]** est `/var/audit/com.day.cq.replication/content`. Pour les tâches **[!UICONTROL Déplacer]**, l’emplacement par défaut est `/var/audit/com.day.cq.wcm.core.page`.

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

---
title: Notes de mise à jour de Cloud Manager 2023.4.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2023.4.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: be39b09b609cccff916db462af9a84149d23a698
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 55%

---


# Notes de mise à jour de Cloud Manager 2023.4.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2023.4.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de la version actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version 2023.4.0 de Cloud Manager dans AEM as a Cloud Service est le 13 avril 2023. La prochaine version est prévue pour le 11 mai 2023.

## Nouveautés {#what-is-new}

* L’[Archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) a été mis à jour vers la version 41.

## Correctifs {#bug-fixes}

* Lorsqu’une [certificate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) expire, [noms de domaine](/help/implementing/cloud-manager/custom-domain-names/introduction.md) et [LISTES AUTORISÉES IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) n’est plus supprimé du réseau de diffusion de contenu associé au certificat.  Dans ce cas, le site reste accessible.
* L’interface utilisateur de Cloud Manager fournit des avertissements avancés plus visibles indiquant que la variable [certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) est sur le point d’expirer.
* Correction d’une rare situation en raison de laquelle les clients ne pouvaient pas créer un environnement ni supprimer un environnement.

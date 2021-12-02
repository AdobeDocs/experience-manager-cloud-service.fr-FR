---
title: Notes de mise à jour des outils de migration dans AEM version 2021.12.0 as a Cloud Service
description: Notes de mise à jour des outils de migration dans AEM version 2021.12.0 as a Cloud Service
feature: Release Information
exl-id: null
source-git-commit: 3bd73869fb04c82fb908a5530728040c7e573eb0
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 19%

---


# Notes de mise à jour des outils de migration dans AEM version 2021.12.0 as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour des outils de migration dans AEM 2021.12.0 as a Cloud Service.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.2 de l’analyseur des bonnes pratiques est le 1er décembre 2021.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur la version d’ACS commons utilisée.
* Possibilité de détecter et de générer des rapports sur le nombre d’utilisateurs et de sous-groupes d’un groupe.
* Possibilité de détecter et de générer des rapports sur les valeurs de propriété de noeud dans MongoDB dépassant 16 Mo.

### Correctifs {#bug-fixes-bpa}

* La détection des composants Foundation a été améliorée afin de réduire les faux négatifs.
* Pour les clients AEM Forms, message BPA concernant `EMAIL_PDF_SUBMIT_ACTION` n’étant pas disponible sur AEM as a Cloud Service a été corrigé.

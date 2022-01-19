---
title: Notes de mise à jour des outils de migration dans AEM version 2021.12.0 as a Cloud Service
description: Notes de mise à jour des outils de migration dans AEM version 2021.12.0 as a Cloud Service
feature: Release Information
source-git-commit: 2788db9338da5499b4a9e72ce196e4ae9857b5d5
workflow-type: tm+mt
source-wordcount: '257'
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


## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.7.10 est le 8 décembre 2021.

### Nouveautés {#what-is-new-ctt}

* Activation/désactivation de l’ajout à la phase d’ingestion dans l’outil de transfert de contenu pour permettre aux utilisateurs de désactiver [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr) pendant l’ingestion. Pour des vitesses d’ingestion optimales, la pré-copie lors de l’ingestion doit être désactivée pour les petits jeux de migration ou si seulement quelques objets Blob ont été ajoutés depuis la dernière ingestion.
* Mappage des utilisateurs mis à jour afin d’utiliser une API de gestion des utilisateurs améliorée qui lui permet d’obtenir 2 000 utilisateurs à la fois, ce qui améliore considérablement les performances.

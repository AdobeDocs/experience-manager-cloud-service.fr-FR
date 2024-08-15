---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2021.12.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2021.12.0
feature: Release Information
exl-id: 4155e1c0-cd40-4cbc-9d6c-b106d68a2db5
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 92%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2021.12.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2021.12.0.

>[!NOTE]
>
>Voir [Notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md) pour consulter les dernières notes de mise à jour.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur des bonnes pratiques v2.1.22 est le 01 décembre 2021.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur la version d’ACS couramment utilisée.
* Possibilité de détecter et de générer des rapports sur le nombre d’utilisateurs et de sous-groupes dans un groupe.
* Possibilité de détecter et de générer des rapports sur les valeurs des propriétés des noeuds dans MongoDB dépassant 16 Mo.

### Correctifs {#bug-fixes-bpa}

* La détection des composants Foundation a été améliorée afin de réduire les faux négatifs.
* Pour les clients AEM Forms, la messagerie BPA concernant `EMAIL_PDF_SUBMIT_ACTION` n’étant pas disponible sur AEM as a Cloud Service a été corrigé.


## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.7.10 est le 8 décembre2021.

### Nouveautés {#what-is-new-ctt}

* Bouton bascule ajouté à la phase d’extraction dans l’outil de transfert de contenu pour permettre aux utilisateurs de désactiver la [pré-copie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html) lors de l’extraction. Pour des vitesses d’ingestion optimales, la pré-copie lors de l’ingestion doit être désactivée pour les petits jeux de migration ou si seulement quelques objets Blob ont été ajoutés depuis la dernière ingestion.
* Mappage des utilisateurs mis à jour afin d’utiliser une API de gestion des utilisateurs améliorée qui lui permet d’obtenir 2 000 utilisateurs à la fois, ce qui améliore considérablement les performances.

---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.1.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.1.0
exl-id: cbd0c316-bda3-48fb-89d6-a8f97bad1970
feature: Release Information
role: Admin
source-git-commit: 81aacb0c616490eed4589cb8927ea1316ca1670e
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 99%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.1.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.1.0.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.7.18 est le 18 janvier 2022.

### Nouveautés {#what-is-new-ctt}

* Bouton bascule ajouté à la phase d’extraction dans l’outil de transfert de contenu pour permettre aux utilisateurs de désactiver la [pré-copie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html) lors de l’extraction. Pour des vitesses d’extraction optimales, la pré-copie lors de l’extraction doit être désactivée pour les petits jeux de migration ou si seulement quelques objets Blob ont été ajoutés depuis la dernière extraction.

### Correctifs {#bug-fixes-ctt}

* Configurations par défaut mises à jour afin de réduire les délais d’exécution lors de l’extraction.

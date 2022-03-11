---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0
feature: Release Information
exl-id: 7ef738a5-4657-482d-848b-e95e4fb816f9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.7.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.7.0 est le 15 juillet 2021.


### Nouveautés {#what-is-new}

* Les clients peuvent désormais utiliser les JDK Azul 8 et 11 pour leurs processus de génération Cloud Manager et peuvent choisir d’utiliser un de ces JDK pour les plug-ins Maven compatibles avec les chaînes d’outils *ou* pour l’exécution du processus Maven complet.

* L’adresse IP sortante sera désormais consignée dans le fichier journal de l’étape de génération.

* Les environnements d’évaluation et de production exécutant d’anciennes versions d’AEM signalent désormais l’état de **Mise à jour disponible**.

* Le nombre maximal de certificats SSL pris en charge est passé à 20 par programme.

* Le nombre maximal de domaines pouvant être configurés a été porté à 500 par environnement.

* Les boutons **Gérer Git** ont été renommés **Accéder aux informations Git** et le visuel de la boîte de dialogue a été rafraîchi.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 28.

### Correctifs {#bug-fixes}

* Dans certains cas, l’aperçu n’était pas une option disponible lors de la liaison d’une Liste d’adresses IP autorisées à un environnement.

* La navigation manuelle vers la page des détails de l’exécution pour une exécution non existante n’affichait pas d’erreur, mais simplement un écran de chargement sans fin.

* Le message d’erreur affiché lorsque le nombre maximal de certificats SSL a été atteint n’était pas utile.

* Dans certains cas, il pouvait y avoir une incohérence dans la version affichée dans la carte de pipeline de la page **Aperçu**.

* L’ajout d’un assistant de programme indiquait de manière incorrecte que le nom ne pouvait pas être modifié après la création.

### Problèmes connus {#known-issues}

Les clients basculant sur les JDK Azul doivent savoir que toutes les applications existantes ne seront pas compilées sans erreur sur le JDK Azul. Il est vivement recommandé d’exécuter un test local avant de basculer.

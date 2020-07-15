---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.7.0
description: Notes de mise à jour d’Experience Manager version 2020.7.0
translation-type: tm+mt
source-git-commit: 22a025b49444e08d014e0459443751b5a3cfc7bf
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 22%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.7.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.7.0.

## Nouveautés de Cloud Manager {#cloud-manager}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.7.0.

### Date de publication {#release-date}

La date de publication de la mise à jour 2020.7.0 de [!UICONTROL Cloud Manager] est le 09 juillet 2020.

### Nouveautés {#what-is-new-cloud-manager}

* La page environnements a été repensée.

* Les environnements en veille prolongée affichent désormais un état discret dans Cloud Manager lorsqu’ils sont mis en veille prolongée.

* Le nombre de variables d&#39;environnement par environnement a été porté à 200.

* Le conteneur de création de Cloud Manager prend désormais en charge Java 8 et Java 11.

### Correctifs {#bug-fixes-cm}

* Le lien entre Cloud Manager et la Console développeur était incorrectement actif avant la création complète des environnements.

* Le lien vers la Console développeur directement à partir de Cloud Manager n’affichait pas l’option permettant de dé-hiberner/hiberner un environnement de Programme Sandbox.

* Les options **Annuler** et **Enregistrer** sur la page de modification du pipeline hors production n’étaient pas toujours visibles.

* Certains échecs du processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un nouveau programme, le nom suggéré renvoyait parfois un duplicata de nom de programme existant.

* Certains journaux d&#39;étape de pipeline volumineux n&#39;ont pas pu être téléchargés de manière cohérente via l&#39;interface utilisateur.

* La validation des noms d&#39;environnement comportait une erreur &quot;off-by-one&quot;.

* La page Environnements affichait parfois des segments de publication et de répartiteur lorsqu’aucun segment n’était présent.

## Nouveautés de l’analyseur de l’état de préparation du cloud {#cloud-readiness-analyzer}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Readiness Analyzer.

### Correctifs {#cra-bug-fixes}

* La version antérieure de l&#39;ARC n&#39;a pas pu être exécutée sur l&#39;Adobe Experience Manager (AEM) 6.1. Un soutien explicite pour autoriser les utilisateurs du groupe d&#39;administrateurs a été ajouté.

   Consultez la section [Installation de l’ARC sur AEM 6.1](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) pour plus d’informations.

* L&#39;horodatage d&#39;expiration affiché sur le rapport récapitulatif était incorrect.

* L&#39;ARC détectait les composants personnalisés de duplicata.

* Dans AEM 6.1, l’inspection du contenu était terminée avant d’effectuer l’inspection complète. La gestion des exceptions a été ajoutée pour permettre à l&#39;inspecteur de sauter et de continuer jusqu&#39;à ce que l&#39;inspection complète soit terminée.


---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.7.0
description: Notes de mise à jour d’Experience Manager version 2020.7.0
translation-type: tm+mt
source-git-commit: 9e27ff9510fda5ed238a25b2d63d1d9a3099a8b5
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 100%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.7.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.7.0.

## Nouveautés de Cloud Manager {#cloud-manager}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.7.0.

### Date de publication {#release-date}

La date de publication de la mise à jour 2020.7.0 de [!UICONTROL Cloud Manager] est le 09 juillet 2020.

### Nouveautés {#what-is-new-cloud-manager}

* La page Environnements a été repensée.

* Les environnements en veille prolongée affichent désormais un état discret dans Cloud Manager.

* Le nombre de variables d’environnement par environnement a été porté à 200.

* Les pipelines de Cloud Manager prennent désormais en charge les variables et les secrets définis par le client.
Pour plus d’informations, consultez [Variables de pipeline](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#pipeline-variables).

### Correctifs {#bug-fixes-cm}

* Le lien entre Cloud Manager et Developer Console était actif avant la création complète des environnements alors qu’il ne devait pas l’être.

* Le lien direct vers Developer Console à partir de Cloud Manager n’affichait pas l’option permettant de mettre en veille/réactiver un environnement de programme sandbox.

* Les options **Annuler** et **Enregistrer** sur la page Modification d’un pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un programme, le nom suggéré renvoyait parfois un duplicata de nom de programme existant.

* Certains journaux d&#39;étape de pipeline volumineux n&#39;ont pas pu être téléchargés de manière cohérente via l&#39;interface utilisateur.

* La validation des noms d’environnement comportait une erreur de décalage d’une unité.

* La page Environnements affichait parfois des segments de publication et de répartiteur alors qu’aucun segment n’était présent.

### Problèmes connus {#known-issues}

* En raison d’un changement dans le mode de calcul de la couverture du code, la version _minimale_ du module externe Jacoco est désormais 0.7.5.201505241946 (publiée en mai 2015). Les clients référençant explicitement une ancienne version recevront un message d’erreur dans le processus de qualité du code.

## Nouveautés de Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.0.2 de Cloud Readiness Analyzer.

### Correctifs {#cra-bug-fixes}

* La version antérieure de CRA ne pouvait pas s’exécuter sur Adobe Experience Manager (AEM) 6.1. Nous avons ajouté la prise en charge explicite de l’autorisation des utilisateurs dans le groupe d’administrateurs.

   Voir [Installation de CRA sur AEM 6.1](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) pour plus d’informations.

* L’horodatage d’expiration affiché sur le rapport résumé était incorrect.

* CRA détectait des doublons de composants personnalisés.

* Dans AEM 6.1, l’inspection du contenu se terminait avant la fin de l’analyse complète. Nous avons ajouté la gestion des exceptions pour permettre à l’inspecteur d’ignorer et de continuer jusqu’à ce que l’inspection complète soit terminée.


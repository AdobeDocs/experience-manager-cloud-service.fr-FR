---
title: Notes de mise à jour de Cloud Manager en AEM version 2020.10.0 du Cloud Service
description: Notes de mise à jour de Cloud Manager en AEM version 2020.10.0 du Cloud Service
translation-type: tm+mt
source-git-commit: d992646fd89a4e502d74533f5fa2bbe994a9ab97
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 48%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.10.0 {#release-notes}

Cette page présente les Notes de mise à jour de Cloud Manager en AEM en tant que Cloud Service 2020.10.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager en tant que Cloud Service 2020.10.0 en AEM est le 01 octobre 2020.

## Cloud Manager {#cloud-manager}

### Nouveautés {#what-is-new}

* La page Environnements a été repensée.

* Les environnements en veille prolongée affichent désormais un état discret dans Cloud Manager.

* Le conteneur de création de Cloud Manager prend désormais en charge la compilation de projets à l’aide de Java 8 ou Java 11. La prise en charge de Java 11 est assurée par le système de chaînes d’outils Maven.

* Le nombre de variables d’environnement par environnement a été porté à 200.

* La carte d’Environnement de la page Aperçu liste désormais jusqu’à trois environnements. Les utilisateurs peuvent sélectionner le bouton **Afficher tout** pour accéder à la page de résumé de l’Environnement et vue d’un tableau avec une liste complète d’environnements.
Consultez [Affichage de l’Environnement](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) pour plus d’informations.


### Correctifs {#bug-fixes-cloud-manager}

* Le lien entre Cloud Manager et Developer Console était actif avant la création complète des environnements alors qu’il ne devait pas l’être.

* Le lien direct vers Developer Console à partir de Cloud Manager n’affichait pas l’option permettant de mettre en veille/réactiver un environnement de programme sandbox.

* Les boutons Annuler et Enregistrer de la page Modification du pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un programme, le nom suggéré renvoyait parfois un duplicata de nom de programme existant.

* Certains journaux d&#39;étape de pipeline volumineux n&#39;ont pas pu être téléchargés de manière cohérente via l&#39;interface utilisateur.

* La validation des noms d’environnement comportait une erreur de décalage d’une unité.

* La page Environnements affichait parfois des segments de publication et de répartiteur alors qu’aucun segment n’était présent.
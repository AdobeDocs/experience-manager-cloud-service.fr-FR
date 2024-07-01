---
title: Notes de mise à jour d’Universal Editor 2024.06.28
description: Il s’agit des notes de mise à jour de la version 2024.06.28 d’Universal Editor.
feature: Release Information
role: Admin
source-git-commit: cc94ad2ba42707bb7541217f0225b995f64ad84f
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 1%

---


# Notes de mise à jour d’Universal Editor 2024.06.28 {#release-notes}

Il s’agit des notes de mise à jour de la version d’Universal Editor du 28 juin 2024.

>[!TIP]
>
>Pour consulter les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, voir [cette page.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nouveautés {#what-is-new}

* **Accueil**: les pages récentes s’affichent sous forme de liste, sans prévisualisation d’images.
* **Barre d’emplacement**: ajout d’une validation d’URL améliorée, application des URL HTTPS et prise en charge des hachages dans les URL pour prendre en compte les applications orientées hachage.
* **Navigation au clavier**: la sélection de superposition de page a été découplée de la sélection du rail de propriétés afin d’améliorer la navigation au clavier sur la page sans perdre la sélection.
* **Étiquettes d’éléments**: la valeur de secours pour les étiquettes utilise désormais `data-aue-prop` au lieu de `data-aue-type` pour une identification plus claire dans les superpositions et dans l’arborescence de contenu.
* **Modèle d’éditeur de texte enrichi**: A **Annuler** a été ajouté au modal de l’éditeur de texte enrichi lors de son ouverture à partir du panneau des propriétés.
* **Service UE sur le noeud**: la prise en charge HTTP du service Universal Editor a été réintroduite, car toutes les connexions HTTPS sont interrompues au niveau de Dispatcher.
* **API de copie interne**: ajout d’une API au service d’éditeur universel pour copier les composants, ce qui permettra l’introduction ultérieure des options de la barre d’outils pour copier et dupliquer le contenu.

## Correctifs {#bug-fixes}

* **Chemin de navigation du panneau Propriétés**: le menu de chemin de navigation du panneau des propriétés pour les éléments imbriqués profondément, qui ne restaient pas ouverts, a été corrigé.
* **Sélecteur de fragment de contenu**: le sélecteur de fragment de contenu a été amélioré afin de s’assurer qu’il respecte les règles définies dans le modèle de fragment de contenu ou dans la variable `data-aue-filter`.
* **Insertion de composants**: correction de la liste pour insérer de nouveaux composants qui ne se mettaient pas à jour correctement après avoir accédé à une autre page.
* **État de publication**: la gestion des états de publication a été améliorée afin de fonctionner de manière plus cohérente.
* **Correctifs divers**: cette version contient également divers correctifs mineurs, le nettoyage de la dette des technologies, des améliorations de sécurité et des tests consolidés pour garantir la stabilité et les performances globales.

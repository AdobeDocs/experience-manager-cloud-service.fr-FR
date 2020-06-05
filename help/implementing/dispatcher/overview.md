---
title: Présentation du flux de la Diffusion de contenu
description: Présentation du flux de la Diffusion de contenu
translation-type: tm+mt
source-git-commit: 0080ace746f4a7212180d2404b356176d5f2d72c
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 81%

---


# Flux de Diffusion de contenu {#content-delivery}

La page actuelle détaille la diffusion du contenu du service de publication dans AEM as a Cloud Service. La diffusion du contenu du service de publication comprend :

* Réseau de diffusion de contenu
* AEM Dispatcher
* Publication AEM

Le flux de données est le suivant :

1. L’URL est ajoutée dans le navigateur.
1. Requête effectuée sur le réseau de diffusion de contenu mappé à ce domaine dans le DNS
1. Si le contenu est entièrement mis en cache sur le réseau de diffusion de contenu, celui-ci l’affiche dans le navigateur.
1. Si le contenu n’est pas entièrement mis en cache, le réseau de diffusion de contenu appelle Dispatcher (par proxy inverse).
1. Si le contenu est entièrement mis en cache sur Dispatcher, celui-ci l’affiche sur le réseau de diffusion de contenu.
1. Si le contenu n’est pas entièrement mis en cache, Dispatcher appelle la publication AEM (par proxy inverse).
1. Le rendu du contenu est effectué par le navigateur, qui peut également le mettre en cache, selon les en-têtes

Par défaut, le type de contenu HTML/texte est défini pour expirer après 300 s (5 minutes) au niveau du répartiteur, un seuil que respectent à la fois le cache du répartiteur et le CDN. Lors des redéploiements du service de publication, le cache du Dispatcher est effacé puis réchauffé avant que les nouveaux nœuds de publication n’acceptent le trafic.

Les sections ci-dessous fournissent des informations plus détaillées sur la diffusion de contenu, notamment la configuration du CDN et la mise en cache.

Des informations sur la réplication du service de création vers le service de publication sont disponibles [ici](/help/operations/replication.md).

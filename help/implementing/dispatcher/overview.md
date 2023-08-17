---
title: Présentation du flux de diffusion de contenu
description: En savoir plus sur le flux de données de diffusion de contenu et comment publier votre contenu
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: d1da8559da856e028a5dcad1d0c0b2c00176af0c
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 45%

---

# Flux de diffusion de contenu {#content-delivery}

La page actuelle détaille la diffusion du contenu du service de publication dans AEM as a Cloud Service. La diffusion du contenu du service de publication comprend :

* Réseau de diffusion de contenu
* AEM Dispatcher
* AEM éditeur

Le flux de données est le suivant :

1. L’URL est ajoutée dans le navigateur.
1. Requête effectuée sur le réseau de diffusion de contenu mappé à ce domaine dans le DNS
1. Si le contenu est entièrement mis en cache sur le réseau de diffusion de contenu, celui-ci l’affiche dans le navigateur.
1. Si le contenu n’est pas entièrement mis en cache, le réseau de diffusion de contenu appelle Dispatcher (proxy inverse).
1. Si le contenu est entièrement mis en cache sur Dispatcher, Dispatcher l’affiche sur le réseau de diffusion de contenu.
1. Si le contenu n’est pas entièrement mis en cache, Dispatcher appelle (proxy inverse) la publication AEM.
1. Le rendu du contenu est effectué par le navigateur, qui peut également le mettre en cache, selon les en-têtes

Par défaut, le type de contenu HTML/texte est défini pour expirer après 300 secondes (5 minutes) au niveau de la couche de Dispatcher, un seuil que le cache de Dispatcher et le réseau de diffusion de contenu respectent. Lors des redéploiements du service de publication, le cache de Dispatcher est effacé, puis réchauffé avant que les nouveaux noeuds de publication n’acceptent le trafic.

Les sections suivantes fournissent des informations plus détaillées sur la diffusion de contenu :
* [Configuration du réseau CDN](/help/implementing/dispatcher/cdn.md)
* [Mise en cache](/help/implementing/dispatcher/caching.md)


Des informations sur la réplication du service de création vers le service de publication sont disponibles [ici](/help/operations/replication.md).

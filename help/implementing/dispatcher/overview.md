---
title: Présentation du flux de diffusion de contenu
description: Présentation du flux de diffusion de contenu
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: 60fc1b8f93c93ca427507dbe56511342f285e6bc
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 100%

---

# Flux de diffusion de contenu {#content-delivery}

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

Par défaut, le type de contenu HTML/texte est défini pour expirer après 300 s (5 minutes) au niveau de la couche du Dispatcher, un seuil que le cache du Dispatcher et le réseau de diffusion de contenu respectent. Lors des redéploiements du service de publication, le cache du Dispatcher est effacé puis préchauffé avant que les nouveaux nœuds de publication n’acceptent le trafic.

Les sections suivantes fournissent des informations plus détaillées sur la diffusion de contenu :
* [Configuration du réseau CDN](/help/implementing/dispatcher/cdn.md)
* [Mise en cache](/help/implementing/dispatcher/caching.md)


Des informations sur la réplication du service de création vers le service de publication sont disponibles [ici](/help/operations/replication.md).

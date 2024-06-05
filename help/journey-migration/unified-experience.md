---
title: Expérience unifiée pour les outils de refactorisation du code
description: Découvrez l’expérience unifiée pour les outils de refactorisation du code.
exl-id: daee0e2d-1e2b-41a3-acab-fc59142d0e05
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 37%

---

# Expérience unifiée pour les outils de refactorisation du code {#unified-experience}

Adobe a développé des outils pour automatiser certaines des tâches de refactorisation du code requises pour être compatible avec Adobe Experience Manager (AEM) as a Cloud Service. Pour réduire la complexité associée à l’installation et à la configuration de différents outils de refactorisation du code, Adobe a développé un plug-in pour unifier les outils qui fonctionnent sur le code et les référentiels.

## Avantages {#benefits}

Le plug-in Unified Experience offre les avantages suivants :

* Unifie les outils qui fonctionnent sur le code source en une application `node.js` exposée sous la forme d’un plug-in `aio-cli ` afin d’offrir à l’utilisateur une expérience utilisateur cohérente.

* Exécute tous les outils au moyen d’une seule commande, tout en offrant la possibilité d’exécuter des outils spécifiques selon les besoins.

* Simplifie l’ajout de nouveaux outils, tout en maintenant l’expérience cohérente.

## Présentation du plug-in {#understanding-plugin}

Le plug-in `aio-cli-plugin-aem-cloud-service-migration` se compose de deux parties principales :

* **Interface utilisateur**

   * `aio-cli` pour exécuter un ou plusieurs outils de refactorisation du code (en mettant en chaîne les outils à exécuter de manière séquentielle).
   * `config.yaml` qui accepte les paramètres d’entrée requis.

* **Suite d’outils de refactorisation du code sous-jacente**

  Les outils de refactorisation du code exécutent leurs fonctionnalités en procédant comme suit :

   * Analyse de la section respective du code du client et manipulation du code (en fonction de l’implémentation du code pour connaître les bonnes pratiques) pour produire la sortie qui peut ensuite être validée et déployée.

   * Génération d’un rapport récapitulatif pour enregistrer les opérations effectuées au cours de l’exécution.

## Disponibilité {#availability}

Voir [Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) où vous pouvez en savoir plus sur l’utilisation et comment contribuer à ce code de plug-in open source dans GitHub.

>[!NOTE]
>Actuellement, le plug-in est intégré à AEM Dispatcher Converter et Repository Modernizer.

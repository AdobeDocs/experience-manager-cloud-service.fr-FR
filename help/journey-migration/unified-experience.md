---
title: Expérience unifiée pour les outils de refactorisation du code
description: Expérience unifiée pour les outils de refactorisation du code
exl-id: daee0e2d-1e2b-41a3-acab-fc59142d0e05
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 90%

---

# Expérience unifiée pour les outils de refactorisation du code {#unified-experience}

Nous avons développé des outils afin de rendre autonomes certaines des tâches de refactorisation du code requises pour une compatibilité avec AEM as a Cloud Service. Pour réduire la complexité associée à l’installation et à la configuration de différents outils de refactorisation du code, nous avons développé un plug-in afin d’unifier les outils qui fonctionnent sur le code et les référentiels.

## Avantages {#benefits}

Le plug-in Unified Experience offre les avantages suivants :

* Unifie les outils qui fonctionnent sur le code source en une application `node.js` exposée sous la forme d’un plug-in `aio-cli ` afin d’offrir à l’utilisateur une expérience utilisateur cohérente.

* Permet d’exécuter tous les outils par le biais d’une seule commande, tout en offrant la possibilité d’exécuter des outils spécifiques en fonction des besoins.

* Fournit une extensibilité pour simplifier l’ajout de nouveaux outils, tout en maintenant l’expérience cohérente.

## Présentation du plug-in {#understanding-plugin}

Le plug-in `aio-cli-plugin-aem-cloud-service-migration` se compose de deux parties principales :

* **Interface utilisateur**

   * Commandes `aio-cli` pour exécuter un ou plusieurs outils de refactorisation du code (en mettant en chaîne les outils à exécuter de manière séquentielle).
   * `config.yaml` qui accepte les paramètres d’entrée requis.

* **Suite d’outils de refactorisation du code sous-jacente**

  Les outils de refactorisation du code exécutent leurs fonctionnalités en procédant comme suit :

   * Analyse de la section respective du code du client et manipulation du code (en fonction de l’implémentation du code pour connaître les bonnes pratiques) pour produire la sortie qui peut ensuite être validée et déployée.

   * Génération d’un rapport récapitulatif pour enregistrer les opérations effectuées au cours de l’exécution.

## Disponibilité {#availability}

Voir [Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) pour en savoir plus sur l’utilisation et sur la manière dont vous pouvez contribuer à ce code de plug-in open source dans GitHub.

>[!NOTE]
>Actuellement, le plug-in est intégré à AEM Dispatcher Converter et Repository Modernizer.

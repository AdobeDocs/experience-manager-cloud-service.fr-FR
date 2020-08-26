---
title: Expérience unifiée pour les outils de refactorisation du code
description: Expérience unifiée pour les outils de refactorisation du code
translation-type: tm+mt
source-git-commit: 03434343829e1a1fb95256a607619b55626c6afc
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 1%

---


# Expérience unifiée pour les outils de refactorisation du code {#unified-experience}

Nous avons développé des outils pour automatiser certaines des tâches de refactorisation du code requises pour être compatible avec AEM en tant que Cloud Service. Pour réduire la complexité associée à l&#39;installation et à la configuration de différents outils de refactorisation du code, nous avons développé un module externe pour unifier les outils qui fonctionnent sur le code et les référentiels.

## Avantages {#benefits}

Le module externe Expérience unifiée offre les avantages suivants :

* Unifie les outils qui fonctionnent sur le code source dans une `node.js` application exposée en tant que `aio-cli ` module externe afin de fournir une expérience utilisateur cohérente à l’utilisateur.

* Permet d&#39;exécuter tous les outils par le biais d&#39;une seule commande, tout en offrant la possibilité d&#39;exécuter des outils spécifiques en fonction des besoins.

* Fournit une extensibilité pour simplifier l’ajout de nouveaux outils, tout en maintenant l’expérience cohérente.

## Présentation du module externe {#understanding-plugin}

Le `aio-cli-plugin-aem-cloud-service-migration` module externe se compose de deux parties principales :

* **Interface utilisateur**

   * `aio-cli` commandes pour exécuter un ou plusieurs outils de refactorisation du code (en chaînant les outils à exécuter de manière séquentielle)
   * `config.yaml` qui accepte les paramètres d&#39;entrée requis

* **Suite d&#39;outils de refactorisation du code sous-jacente**

   Les outils de refactorisation du code exécutent leurs fonctionnalités en procédant comme suit :

   * Analyse de la section respective du code du client et manipulation du code (en fonction de l’implémentation du code pour connaître les meilleures pratiques) pour produire la sortie qui peut ensuite être validée et déployée.

   * Génération d’un rapport récapitulatif pour enregistrer les opérations effectuées au cours de l’exécution.

## Disponibilité {#availability}

Reportez-vous à la ressource [Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) pour en savoir plus sur l’utilisation et comment vous pouvez contribuer à ce code de module externe ouvert dans GitHub.

>[!NOTE]
>Actuellement, seul le convertisseur de répartiteur est intégré au module externe.

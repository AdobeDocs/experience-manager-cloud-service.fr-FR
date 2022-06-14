---
title: Tableau de bord des licences
description: Cloud Manager fournit un tableau de bord pour un affichage convivial des droits des produits AEMaaCS disponibles pour votre entreprise ou client.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
source-git-commit: 1b7183421b9acd30697f1dc228dd9e2728d24ba6
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 6%

---

# Tableau de bord des licences {#license-dashboard}

Cloud Manager fournit un tableau de bord pour un affichage convivial des droits des produits AEMaaCS disponibles pour votre entreprise ou client.

## Présentation {#overview}

Le tableau de bord de la licence Cloud Manager permet d’accéder facilement aux informations suivantes :

1. Droits aux solutions disponibles pour l’ensemble de vos programmes, y compris ce qui est utilisé et ce qui est disponible
1. Mesures de consommation des demandes de contenu selon les tendances par mois pour la solution Sites

## Utilisation du tableau de bord de la licence {#using-dashboard}

Pour accéder à votre tableau de bord de licence, procédez comme suit.

>[!NOTE]
>
>Un utilisateur dans **Propriétaire de l’entreprise** doit être connecté pour afficher le tableau de bord de la licence.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la page d’aperçu des produits, passez au **Licence** .

![Tableau de bord des licences](assets/license-dashboard.png)

Le tableau de bord se divise en trois sections :

* **Solutions** - Cette section résume les solutions pour lesquelles vous disposez d’une licence, telles que Sites ou Assets.
* **Modules complémentaires** - Cette section résume les modules complémentaires disponibles pour vos solutions sous licence.
* **Environnements de test et de développement** - Cette section résume les environnements disponibles.

Chaque section résume ce qui est disponible et comment il est actuellement utilisé, le cas échéant. Actuellement, seules les solutions Sites s’affichent même si d’autres solutions existent dans le client.

* Le **État** affiche le nombre de droits inutilisés par rapport au total disponible pour le client.
* Le **Configuré sur** indique les programmes sur lesquels le droit à la solution a été appliqué.
   * Un droit est considéré comme utilisé uniquement lorsqu’un environnement de production a été créé ou s’il existe déjà, si un pipeline de mise à jour a été exécuté.
* Le **Utilisation** affiche les requêtes de contenu consommées au cours des 12 derniers mois sous la forme d’un graphique lorsque l’utilisateur clique dessus.

>[!TIP]
>
>Reportez-vous à la [présentation d’Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour savoir comment gérer vos droits Adobe dans l’ensemble de votre organisation à partir d’Admin Console.

## Questions fréquemment posées {#faq}

### Qu’est-ce qu’une requête de contenu ? {#what-is-a-content-request}

Une requête de contenu est une requête qui arrive dans AEM Sites ou tout système de mise en cache fourni par le client, tel qu’un réseau de diffusion de contenu, pour diffuser du contenu ou des données au format HTML sous la forme d’une page vue ou au format JSON sous la forme d’un appel API.

Une demande de contenu est comptabilisée pour chaque page vue ou pour chaque cinq appels d’API, mesurés à l’entrée du premier système de mise en cache qui reçoit une demande de contenu.

Les demandes de contenu excluent les demandes ou activités initiées par ou pour le compte d’Adobe dans le seul but de fournir des produits et des services. Le trafic des agents utilisateurs identifiés par l’Adobe provenant des robots, des robots d’indexation et des araignées associés aux moteurs de recherche et aux services de médias sociaux courants est également exclu.

### Comment Adobe Experience Manager mesure-t-il les demandes de contenu ? {#how-are-content-requests-measured}

Les demandes de contenu sont suivies côté serveur dans Cloud Service. Le réseau de diffusion de contenu intégré à AEM as a Cloud Service effectue le suivi de HTMLS valides et de requêtes JSON. AEM a également mis en place des règles pour exclure les robots connus, notamment les services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

Voici une liste non exhaustive d’exemples de services connus exclus.

* AddSearchBot
* AhrefsBot
* Applebot
* Demander à Jeeves Corporate Spider
* Bingbot
* BingPreview
* BLEXBot
* builtWith
* Bytespider
* CrawlerKengo
* Facebook externalhit
* Google AdsBot
* Google AdsBot Mobile

### Pourquoi mon rapport Analytics présente-t-il des résultats différents de ceux des demandes de contenu AEM ? {#why-are-reports-different}

Les requêtes de contenu présentent des variations avec les outils de création de rapports Analytics d’une organisation, comme illustré dans ce tableau.

| Raison de la variation | Explication |
|---|---|
| Balisage | Toutes les pages qui font l’objet d’un suivi AEM demandes de contenu peuvent être ou non balisées avec le suivi Analytics.<br>Tous les appels d’API qui font l’objet d’un suivi AEM demandes de contenu ne seront pas balisés par l’outil Analytics d’une organisation.<br>Les pages ou les appels d’API peuvent être balisés pour effectuer le suivi des actions plutôt que des vues. |
| Règles Tag Management | Les paramètres des règles de gestion des balises peuvent entraîner diverses configurations de collecte de données sur une page, ce qui entraîne une combinaison d’incohérences avec le suivi des demandes de contenu. |
| Robots | Les robots inconnus qui n’ont pas été préidentifiés et supprimés par AEM peuvent entraîner des incohérences dans le suivi. |
| Suites de rapports | Les pages qui font partie d’une même instance AEM et d’un même domaine peuvent envoyer des données à différentes suites de rapports Analytics. |
| Outils de surveillance et de sécurité tiers | Les outils de surveillance et d’analyse de sécurité peuvent générer des demandes de contenu pour les AEM qui ne sont pas suivies dans les rapports Analytics. |
| Prérécupération des requêtes | L’utilisation d’un service de prérécupération pour précharger les pages afin d’accélérer le chargement peut entraîner une augmentation significative du trafic de requêtes de contenu. |
| DDOS | Bien qu’Adobe fasse tout son possible pour détecter et filtrer automatiquement le trafic provenant des attaques DDOS, il n’existe aucune garantie que toutes les attaques DDOS possibles seront détectées. |

### Que se passe-t-il si j’utilise mon propre réseau de diffusion de contenu ? {#using-own-cdn}

Le tableau de bord de requêtes de contenu de Cloud Manager n’affiche pas le suivi pour votre propre réseau de diffusion de contenu.

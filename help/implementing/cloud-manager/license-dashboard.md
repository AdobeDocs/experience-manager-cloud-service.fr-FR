---
title: Tableau de bord des licences
description: Cloud Manager fournit un tableau de bord pour un affichage convivial des produits AEMaaCS disponibles pour votre entreprise ou vos clients.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 100%

---

# Tableau de bord des licences {#license-dashboard}

Cloud Manager fournit un tableau de bord pour un affichage convivial des produits AEMaaCS disponibles pour votre entreprise ou vos clients.

## Vue d’ensemble {#overview}

Le tableau de bord de la licence Cloud Manager permet d’accéder facilement aux informations suivantes :

1. Solutions disponibles pour l’ensemble de vos programmes, y compris ce qui est utilisé et ce qui est disponible
1. Mesures de consommation des demandes de contenu selon les tendances par mois pour la solution Sites

## Utiliser le tableau de bord des licences {#using-dashboard}

Pour accéder à votre tableau de bord des licences, procédez comme suit.

>[!NOTE]
>
>Un utilisateur détenant le rôle de **propriétaire de l’entreprise** doit être connecté pour pouvoir consulter le tableau de bord des licences.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la page d’aperçu des produits, passez à l’onglet **Licences**.

![Tableau de bord des licences](assets/license-dashboard.png)

Le tableau de bord se divise en trois sections, comme suit :

* **Solutions** - Cette section résume les solutions pour lesquelles vous disposez d’une licence, telles que Sites ou Assets.
* **Modules complémentaires** - Cette section résume les modules complémentaires disponibles pour vos solutions sous licence.
* **Environnement de sandbox et de développement** - Cette section résume les environnements disponibles.

Chaque section résume ce qui est disponible et l’utilisation associée, le cas échéant. Actuellement, seules les solutions Sites s’affichent même si d’autres solutions existent dans le client.

* La colonne **Statut** affiche le nombre de droits inutilisés par rapport au total disponible pour le client.
* La colonne **Configuré sur** indique les programmes sur lesquels le droit de la solution a été appliqué.
   * Un droit est considéré comme utilisé uniquement lorsqu’un environnement de production a été créé ou s’il existe déjà, si un pipeline de mise à jour y a été exécuté.
* La colonne **Utilisation** affiche les requêtes de contenu consommées au cours des 12 derniers mois sous la forme d’un graphique lorsque l’utilisateur clique dessus.

>[!TIP]
>
>Reportez-vous à la [vue d’ensemble d’Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour découvrir comment gérer vos droits Adobe dans l’ensemble de votre organisation à partir d’Admin Console.

## Foire aux questions {#faq}

### Qu’est-ce qu’une requête de contenu ? {#what-is-a-content-request}

Une requête de contenu est une requête qui arrive dans AEM Sites ou tout système de mise en cache fourni par le client, tel qu’un réseau de diffusion de contenu, pour diffuser du contenu ou des données au format HTML sous la forme d’une page vue ou au format JSON sous la forme d’un appel API.

Une demande de contenu est comptabilisée pour chaque page vue ou chaque fois que cinq appels d’API sont effectués, mesurée à l’entrée du premier système de mise en cache qui reçoit une demande de contenu. Les demandes de contenu sont comptabilisées par rapport aux environnements de production uniquement.

Les demandes de contenu excluent les demandes ou activités initiées par ou pour le compte d’Adobe dans le seul but de fournir des produits et des services. Le trafic des agents utilisateurs identifiés par Adobe provenant des robots associés aux moteurs de recherche et aux services de médias sociaux est également exclu.

### Comment Adobe Experience Manager mesure-t-il les demandes de contenu ? {#how-are-content-requests-measured}

Les demandes de contenu sont suivies sur les serveurs Edge d’AEM as a Cloud Service. Le trafic d’origine n’est pas comptabilisé dans les demandes de contenu. Le réseau CDN intégré à AEM as a Cloud Service effectue le suivi des requêtes HTML et JSON valides.

AEM a également mis en place des règles pour exclure les robots connus, notamment les services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

### Pourquoi mon rapport Analytics présente-t-il des résultats différents de ceux des demandes de contenu AEM ? {#why-are-reports-different}

Les requêtes de contenu présentent des écarts avec les outils de création de rapports Analytics d’une organisation, comme illustré dans ce tableau.

| Raison de l’écart | Explication |
|---|---|
| Balisage | Toutes les pages qui font l’objet d’un suivi sous forme de demandes de contenu AEM peuvent être ou non balisées avec le suivi Analytics. Tous les appels d’API qui font l’objet d’un suivi sous forme de demandes de contenu AEM ne seront pas balisés par l’outil Analytics d’une organisation.<br>Les pages ou les appels d’API peuvent être balisés pour effectuer le suivi des actions ou simplement des pages vues uniques au lieu de toutes les vues. |
| Règles de gestion des balises | Les paramètres des règles de gestion des balises peuvent entraîner diverses configurations de collecte de données sur une page, ce qui entraîne une combinaison d’incohérences avec le suivi des demandes de contenu. |
| Robots | Les robots inconnus qui n’ont pas été préalablement identifiés et supprimés par AEM peuvent entraîner des incohérences dans le suivi. |
| Suites de rapports | Les pages qui font partie d’une même instance AEM et d’un même domaine peuvent envoyer des données à différentes suites de rapports Analytics. |
| Outils de surveillance et de sécurité tiers | Les outils de surveillance et d’analyse de sécurité peuvent générer des demandes de contenu pour AEM qui ne sont pas suivies dans les rapports Analytics. |
| Pré-récupérer des demandes | L’utilisation d’un service de pré-récupération pour précharger les pages afin d’augmenter la vitesse peut entraîner une augmentation significative du trafic de demandes de contenu. |
| DDOS | Bien qu’Adobe s’efforce de détecter et de filtrer automatiquement le trafic provenant des attaques DDOS, il n’existe aucune garantie que toutes les attaques DDOS possibles soient détectées |
| Bloqueurs de trafic | L’utilisation d’un bloqueur de suivi dans un navigateur peut exclure certaines requêtes du suivi. |
| Pare-feux | Les pare-feu peuvent bloquer le suivi Analytics. Cela est plus fréquent avec les pare-feu d’entreprise. |

### Comment en savoir plus sur le volume de ma requête de contenu ? {#current-request-volumes}

Si vous souhaitez obtenir des informations supplémentaires sur le volume des requêtes de contenu affiché dans le tableau de bord des licences, votre équipe Adobe peut fournir un rapport qui indique les principaux facteurs de volume des requêtes de contenu. Contactez votre équipe Adobe ou l’assistance clientèle d’Adobe pour demander un rapport sur l’utilisation optimale.

### Que se passe-t-il si j’utilise mon propre réseau CDN ? {#using-own-cdn}

Le tableau de bord des licences affiche uniquement les données suivies par le réseau CDN du service cloud.  Si vous choisissez d’importer votre propre réseau CDN (BYOCDN), vous rapporterez annuellement votre volume de requête de contenu à Adobe, comme indiqué dans votre contrat.

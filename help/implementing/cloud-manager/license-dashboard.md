---
title: Tableau de bord des licences
description: Cloud Manager fournit un tableau de bord pour un affichage convivial des produits AEMaaCS disponibles pour votre entreprise ou vos clients.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
source-git-commit: d1b2226a1deec2e71056c43c84672cb4a358bc8c
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 58%

---

# Tableau de bord des licences {#license-dashboard}

Cloud Manager fournit un tableau de bord pour un affichage convivial des produits AEMaaCS disponibles pour votre entreprise ou vos clients.

## Vue d’ensemble {#overview}

Le tableau de bord de la licence Cloud Manager permet d’accéder facilement aux informations suivantes :

1. Les droits aux solutions sont disponibles pour tous vos programmes, y compris les éléments utilisés et disponibles.
1. Mesures de consommation des demandes de contenu selon les tendances par mois pour la solution Sites

## Utiliser le tableau de bord des licences {#using-dashboard}

Pour accéder à votre tableau de bord des licences, procédez comme suit.

>[!NOTE]
>
>Un utilisateur de la variable **Propriétaire de l’entreprise** doit être connecté pour afficher le tableau de bord de la licence.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)** , basculez sur la console **Licence** .

![Tableau de bord des licences](assets/license-dashboard.png)

Le tableau de bord se divise en trois sections, comme suit :

* **Solutions** - Cette section résume les solutions pour lesquelles vous disposez d’une licence, telles que Sites ou Assets.
* **Modules complémentaires** - Cette section résume les modules complémentaires disponibles pour vos solutions sous licence.
* **Environnement de sandbox et de développement** - Cette section résume les environnements disponibles.

Chaque section résume ce qui est disponible et comment il est utilisé, le cas échéant. Actuellement, seules les solutions Sites s’affichent même si d’autres solutions existent dans le client.

* La variable **État** affiche le nombre de droits inutilisés par rapport au total disponible pour le client.
* La colonne **Configuré sur** indique les programmes sur lesquels le droit de la solution a été appliqué.
   * Un droit est considéré comme utilisé uniquement lorsqu’un environnement de production a été créé ou, s’il en existe un, si un pipeline de mise à jour a été exécuté.
* La colonne **Utilisation** affiche les requêtes de contenu consommées au cours des 12 derniers mois sous la forme d’un graphique lorsque l’utilisateur clique dessus.

>[!TIP]
>
>Pour savoir comment gérer les droits de vos Adobes dans l’ensemble de votre organisation à partir de Admin Console, voir [Présentation du Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

## Foire aux questions {#faq}

### Qu’est-ce qu’une requête de contenu ? {#what-is-a-content-request}

Une requête de contenu est une requête qui arrive dans AEM Sites ou tout système de mise en cache fourni par le client, tel qu’un réseau de diffusion de contenu, pour diffuser du contenu ou des données au format HTML sous la forme d’une page vue ou au format JSON sous la forme d’un appel API.

Une demande de contenu est comptabilisée pour chaque page vue ou chaque fois que cinq appels d’API sont effectués, mesurée à l’entrée du premier système de mise en cache qui reçoit une demande de contenu. Les demandes de contenu sont comptabilisées par rapport aux environnements de production uniquement.

Les demandes de contenu excluent les demandes ou activités initiées par ou pour le compte d’Adobe dans le seul but de fournir des produits et des services. Le trafic des agents utilisateurs identifiés par Adobe provenant des robots associés aux moteurs de recherche et aux services de médias sociaux est également exclu.

Voir aussi [Compréhension des requêtes de contenu Cloud Service](/help/implementing/cloud-manager/content-requests.md).

### Comment Adobe Experience Manager mesure-t-il les demandes de contenu ? {#how-are-content-requests-measured}

Les demandes de contenu sont suivies sur les serveurs Edge d’AEM as a Cloud Service. Le trafic d’origine n’est pas comptabilisé dans les demandes de contenu. Le réseau CDN intégré à AEM as a Cloud Service effectue le suivi des requêtes HTML et JSON valides.

AEM a également mis en place des règles pour exclure les robots connus, notamment les services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

Voir aussi [Compréhension des requêtes de contenu Cloud Service](/help/implementing/cloud-manager/content-requests.md).

### Pourquoi mon rapport Analytics présente-t-il des résultats différents de ceux des demandes de contenu AEM ? {#why-are-reports-different}

Les requêtes de contenu peuvent présenter des variations avec les outils de création de rapports Analytics d’une organisation. Pour plus d’informations, voir [Compréhension des requêtes de contenu Cloud Service](/help/implementing/cloud-manager/content-requests.md).

### Comment en savoir plus sur le volume de ma requête de contenu ? {#current-request-volumes}

Si vous souhaitez obtenir des informations supplémentaires sur le volume des requêtes de contenu affiché dans le tableau de bord des licences, votre équipe Adobe peut fournir un rapport qui indique les principaux facteurs de volume des requêtes de contenu. Contactez votre équipe d’Adobe ou le service clientèle pour demander un rapport d’utilisation optimal.

### Que se passe-t-il si j’utilise mon propre réseau CDN ? {#using-own-cdn}

Le tableau de bord de la licence affiche uniquement les données suivies par le réseau de diffusion de contenu du Cloud Service. Si vous choisissez d’importer votre propre réseau de diffusion de contenu (BYOCDN), vous signalez le volume de vos demandes de contenu à l’Adobe sur une base annuelle, comme indiqué dans votre contrat.

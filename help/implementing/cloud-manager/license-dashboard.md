---
title: Tableau de bord des licences
description: Cloud Manager fournit un tableau de bord pour un affichage convivial des produits AEMaaCS disponibles pour votre entreprise ou vos clients.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: eae5c75e1bf4f7201fe2c01d08737d36489ca3e4
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 31%

---


# Tableau de bord des licences {#license-dashboard}

Cloud Manager fournit un tableau de bord pour un affichage convivial des produits AEMaaCS disponibles pour votre entreprise ou vos clients.

>[!IMPORTANT]
>
>Le tableau de bord des licences s’applique uniquement aux programmes AEM as a Cloud Service. [Les programmes AMS](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/introduction) ne sont pas inclus dans le tableau de bord des licences.
>
>Pour déterminer le type de service de votre programme (AMS ou AEMaaCS), consultez le document [Navigation dans l’interface utilisateur de Cloud Manager.](/help/implementing/cloud-manager/navigation.md#program-cards)

## Vue d’ensemble {#overview}

Le tableau de bord de la licence Cloud Manager permet d’accéder facilement aux informations suivantes :

1. Les droits aux solutions sont disponibles pour tous vos programmes, y compris les éléments utilisés et disponibles.
1. Mesures de consommation des demandes de contenu selon les tendances par mois pour la solution Sites

## Utiliser le tableau de bord des licences {#using-dashboard}

Pour accéder à votre tableau de bord des licences, procédez comme suit.

>[!NOTE]
>
>Un utilisateur possédant le rôle **Propriétaire de l’entreprise** doit être connecté pour afficher le tableau de bord de la licence.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, appuyez ou cliquez sur le bouton du menu du hamburger sur l’ [en-tête Cloud Manager.](/help/implementing/cloud-manager/navigation.md#cloud-manager-header) Les onglets s’affichent.
1. Appuyez ou cliquez sur l’option **Licence** dans l’onglet .

![Tableau de bord des licences](assets/license-dashboard.png)

Le tableau de bord se divise en trois sections, comme suit :

* **Solutions** - Cette section résume les solutions pour lesquelles vous disposez d’une licence, telles que Sites ou Assets.
* **Modules complémentaires** - Cette section résume les modules complémentaires disponibles pour vos solutions sous licence.
* **Autres droits** - Cette section résume l’environnement de test et de développement ainsi que d’autres droits qui peuvent être utilisés dans votre client.

Chaque section résume ce qui est disponible et comment il est utilisé, le cas échéant. Actuellement, seules les solutions Sites et Assets sont affichées même si d’autres solutions existent dans le client.

* La colonne **État** affiche le nombre de droits inutilisés par rapport au total disponible pour le client.
* La colonne **Configuré sur** indique les programmes sur lesquels le droit de la solution a été appliqué.
   * Un droit est considéré comme utilisé uniquement lorsqu’un environnement de production a été créé ou, s’il en existe un, si un pipeline de mise à jour a été exécuté.
   * Seul un nombre limité de programmes sont répertoriés individuellement dans la colonne avec le reste représenté par une entrée `+x`.
   * Passez la souris sur l’entrée `+x` d’une fenêtre contextuelle avec les détails de tous les programmes.
* La colonne **Utilisation** affiche un bouton **[Afficher les détails d’utilisation](#view-usage-details)** pour afficher les statistiques d’utilisation de la solution.

>[!TIP]
>
>Pour savoir comment gérer les droits d’Adobe de l’ensemble de votre organisation à partir d’Admin Console, consultez la [présentation de l’Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

## Afficher les détails d’utilisation {#view-usage-details}

Le bouton **Afficher les détails d’utilisation** donne accès à la fenêtre **Détails d’utilisation** de la solution choisie. Cette fenêtre présente une ventilation détaillée comprenant des graphiques indiquant l’utilisation de votre solution. La manière dont cette utilisation est mesurée dépend de la solution choisie.

### Détails de l’utilisation des sites {#sites-usage-details}

La fenêtre **Détails de l’utilisation des sites** présente des graphiques qui donnent un aperçu de l’utilisation de vos licences Sites en fonction des [demandes de contenu.](#what-is-a-content-request)

![Fenêtre des détails d’utilisation des sites](assets/sites-usage-details.png)

Le côté gauche de la fenêtre présente un graphique circulaire indiquant la ventilation du contrat pour l’année du contrat sélectionnée dans la liste déroulante **Afficher l’année du contrat** .

Le côté droit de la fenêtre présente un diagramme de surface présentant l&#39;utilisation répartie par programme au fil du temps pour l&#39;année contractuelle sélectionnée. Une survol permet d’afficher une fenêtre contextuelle contenant des détails par programme pour le moment sélectionné.

### Détails de l’utilisation d’Assets {#assets-usage-details}

La fenêtre **Détails de l’utilisation d’Assets** présente des graphiques qui donnent un aperçu de l’utilisation de vos licences Assets en fonction des [utilisateurs standard](#storage) et [.](#standard-users) Sélectionnez l’onglet approprié pour basculer entre les vues.

Pour les vues de stockage et d’utilisateurs standard, vous pouvez utiliser la liste déroulante **Type d’environnement** pour basculer l’affichage entre les environnements de production, d’évaluation et de développement.

#### Stockage  {#storage}

![Fenêtre des détails d’utilisation d’Assets pour le stockage](assets/assets-usage-details-storage.png)

Le côté gauche de la fenêtre présente un graphique circulaire indiquant la ventilation du contrat pour l’année du contrat sélectionnée dans la liste déroulante **Afficher l’année du contrat** .

Le côté droit de la fenêtre présente un diagramme de surface présentant l&#39;utilisation répartie par programme au fil du temps pour l&#39;année contractuelle sélectionnée. Une survol permet d’afficher une fenêtre contextuelle contenant des détails par programme pour le moment sélectionné.

#### Utilisateurs standard {#standard-users}

![Fenêtre de détails d’utilisation d’Assets pour les utilisateurs standard](assets/assets-usage-details-standard-users.png)

Le côté gauche de la fenêtre présente un graphique circulaire indiquant la ventilation du contrat pour l’année du contrat sélectionnée dans la liste déroulante **Afficher l’année du contrat** .

Le côté droit de la fenêtre présente un diagramme de surface présentant l&#39;utilisation répartie par programme au fil du temps pour l&#39;année contractuelle sélectionnée. Une survol permet d’afficher une fenêtre contextuelle contenant des détails par programme pour le moment sélectionné.

## Foire aux questions {#faq}

### Qu’est-ce qu’une requête de contenu ? {#what-is-a-content-request}

Une requête de contenu est une requête qui arrive dans AEM Sites ou tout système de mise en cache fourni par le client, tel qu’un réseau de diffusion de contenu, pour diffuser du contenu ou des données au format HTML en tant que page vue ou au format JSON en tant qu’appel API.

Une demande de contenu est comptabilisée pour chaque page vue ou chaque fois que cinq appels d’API sont effectués, mesurée à l’entrée du premier système de mise en cache qui reçoit une demande de contenu. Les demandes de contenu sont comptabilisées par rapport aux environnements de production uniquement.

Les demandes de contenu excluent les demandes ou activités initiées par ou pour le compte d’Adobe dans le seul but de fournir des produits et des services. Le trafic des agents utilisateurs identifiés par Adobe provenant des robots associés aux moteurs de recherche et aux services de médias sociaux est également exclu.

Voir aussi [Comprendre les demandes de contenu de Cloud Service](/help/implementing/cloud-manager/content-requests.md).

### Comment Adobe Experience Manager mesure-t-il les demandes de contenu ? {#how-are-content-requests-measured}

Les demandes de contenu sont suivies sur les serveurs Edge d’AEM as a Cloud Service. Le trafic d’origine n’est pas comptabilisé dans les demandes de contenu. Le réseau CDN intégré à AEM as a Cloud Service effectue le suivi des requêtes HTML et JSON valides.

AEM a également mis en place des règles pour exclure les robots connus, notamment les services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

Voir aussi [Comprendre les demandes de contenu de Cloud Service](/help/implementing/cloud-manager/content-requests.md).

### Pourquoi mon rapport Analytics présente-t-il des résultats différents de ceux des demandes de contenu AEM ? {#why-are-reports-different}

Les requêtes de contenu peuvent présenter des variations avec les outils de création de rapports Analytics d’une organisation. Pour plus d’informations, voir [Présentation des requêtes de contenu de Cloud Service](/help/implementing/cloud-manager/content-requests.md).

### Comment en savoir plus sur le volume de ma requête de contenu ? {#current-request-volumes}

Si vous souhaitez obtenir des informations supplémentaires sur le volume des requêtes de contenu affiché dans le tableau de bord des licences, votre équipe Adobe peut fournir un rapport qui indique les principaux facteurs de volume des requêtes de contenu. Contactez votre équipe d’Adobe ou le service clientèle pour demander un rapport d’utilisation optimal.

### Que se passe-t-il si j’utilise mon propre réseau CDN ? {#using-own-cdn}

Le tableau de bord de la licence affiche uniquement les données suivies par le réseau de diffusion de contenu du Cloud Service. Si vous choisissez d’importer votre propre réseau de diffusion de contenu (BYOCDN), vous signalez le volume de vos demandes de contenu à l’Adobe sur une base annuelle, comme indiqué dans votre contrat.

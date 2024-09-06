---
title: Navigation dans l’interface d’utilisation de Cloud Manager
description: Découvrez l’organisation de l’interface d’utilisation de Cloud Manager et comment gérer vos programmes et vos environnements.
exl-id: 3f3d7631-2bc9-440b-9888-50f6529bcd42
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 75%

---


# Navigation dans l’interface d’utilisation de Cloud Manager {#navigation}

Découvrez l’organisation de l’interface d’utilisation de Cloud Manager et comment gérer vos programmes et vos environnements.

L’interface d’utilisation de Cloud Manager est composée principalement de deux interfaces graphiques :

* [La console Mes programmes](#my-programs-console) où vous pouvez afficher et gérer tous vos programmes.
* [La fenêtre Vue d’ensemble du programme](#program-overview) où vous pouvez consulter les détails d’un programme individuel et le gérer.

>[!TIP]
>
>Consultez également le [parcours de documentation d’intégration](/help/journey-onboarding/overview.md) pour obtenir un aperçu complet de la prise en main d’AEM as a Cloud Service à l’aide de Cloud Manager.

## Console Mes programmes {#my-programs-console}

Lorsque vous vous connectez à Cloud Manager sur la page [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et que vous sélectionnez l’organisation appropriée, vous accédez à la console **Mes programmes**.

![Console Mes programmes](assets/my-programs-console.png)

La console Mes programmes fournit une vue d’ensemble de tous les programmes auxquels vous avez accès dans l’organisation sélectionnée. Elle est constituée de plusieurs éléments.

1. Des [Barres d’outils](#toolbars-my-programs-toolbars) pour la sélection de l’organisation, les alertes et les paramètres de compte.
1. Des onglets qui permettent de changer l’affichage actuel de vos programmes.
   * Vue **Accueil** (par défaut) qui sélectionne la vue **Mes programmes** avec une vue d’ensemble de tous les programmes.
   * **Licence** qui accède au [tableau de bord de licence](/help/implementing/cloud-manager/license-dashboard.md).
   * Notez que les onglets sont fermés par défaut et peuvent être affichés à l’aide du menu hamburger dans l’[en-tête Cloud Manager](#cloud-manager-header).
1. Des [Statistiques et un appel à l’action](#statistics) pour une vue d’ensemble de votre activité récente.
1. [**Section Mes programmes**](#my-programs-section) avec une vue d’ensemble de tous vos programmes.
1. Des [Liens rapides](#quick-links-section) pour accéder facilement aux ressources connexes.

>[!TIP]
>
>Consultez le document [Programmes et types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) pour plus d’informations sur les programmes.

### Barres d’outils {#my-programs-toolbars}

Il y a deux barres d’outils superposées.

#### En-tête de Cloud Manager {#cloud-manager-header}

La première est l’en-tête de Cloud Manager, qui est présent en permanence lorsque vous naviguez dans Cloud Manager. Il s’agit d’un élément ancré qui permet d’accéder aux paramètres et aux informations relatifs à l’ensemble des programmes Cloud Manager.

![En-tête Experience Cloud](assets/experience-cloud-header.png)

1. Le menu hamburger donne accès à des onglets qui peuvent vous amener à des parties spécifiques d’un programme individuel ou basculer entre le [Tableau de bord de la licence](/help/implementing/cloud-manager/license-dashboard.md) et la console **[Mes programmes](#my-programs-console)** en fonction du contexte.
1. Le bouton Cloud Manager vous ramène à la console Mes programmes de Cloud Manager, où que vous soyez dans Cloud Manager.
1. Appuyez ou cliquez sur le bouton Commentaires pour envoyer des commentaires à Adobe concernant Cloud Manager.
1. Le sélecteur d’organisation affiche l’organisation que vous utilisez actuellement pour vous connecter (dans cet exemple, Fonudation Internal). Appuyez ou cliquez pour passer à une autre organisation si votre Adobe ID est associé à plusieurs d’entre elles.
1. Appuyez ou cliquez sur le sélecteur de solutions pour accéder rapidement à d’autres solutions Experience Cloud.
1. L’icône d’aide permet d’accéder rapidement aux ressources d’apprentissage et d’assistance.
1. L’icône de notifications comporte un badge indiquant le nombre de [notifications](/help/implementing/cloud-manager/notifications.md) incomplètes actuellement attribuées.
1. Appuyez ou cliquez sur l’icône qui représente votre utilisateur ou votre utilisatrice pour accéder à vos paramètres d’utilisateur ou d’utilisatrice. Si vous n’avez configuré aucune image d’utilisateur ou d’utilisatrice, une icône est attribuée de manière aléatoire.

#### Barre d’outils des programmes {#program-toolbar}

La barre d’outils des programmes fournit des liens pour basculer entre les programmes Cloud Manager et des actions contextuelles.

![Barre d’outils des programmes](assets/program-toolbar.png)

1. Le sélecteur de programme s’ouvre dans une liste déroulante dans laquelle vous pouvez sélectionner rapidement d’autres programmes ou effectuer des actions contextuelles, telles que la création d’un programme.
1. Le lien de prise en main vous permet d’accéder au [parcours d’intégration et de documentation](/help/journey-onboarding/overview.md) pour vous familiariser avec Cloud Manager.
1. Le bouton d’action propose des actions contextuelles, telles que la création d’un programme.

### Statistiques et appels à l’action {#statistics}

La section statistiques et appel à l’action fournit des données agrégées pour votre organisation. Par exemple, si vous avez configuré vos programmes avec succès, les statistiques de vos activités au cours des 90 derniers jours peuvent s’afficher, notamment :

* Le nombre de [déploiements](/help/implementing/cloud-manager/deploy-code.md)
* Le nombre de [problèmes relatifs à la qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) identifiés
* Le nombre de versions

Si vous êtes au commencement de la configuration de votre organisation, vous pouvez obtenir des conseils sur les étapes suivantes ou des ressources de documentation.

### Section Mes programmes {#my-programs-section}

Le contenu principal de la console **Mes programmes** est la liste des programmes de la section **Mes programmes** .

La section **Mes programmes** répertorie les cartes représentant chaque programme. Appuyez ou cliquez sur une carte pour accéder à la page **Vue d’ensemble du programme** du programme pour obtenir plus d’informations sur le programme.

>[!NOTE]
>
>Selon vos privilèges, il se peut que vous ne puissiez pas sélectionner certains programmes.

Utilisez les options de tri pour trouver plus rapidement le programme dont vous avez besoin.

![Options de tri](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Trier par
   * Date de création (par défaut)
   * Nom du programme
   * Statut
* Croissant (par défaut) / Décroissant
* Vue Grille (par défaut)
* Vue Liste

#### Cartes de programme {#program-cards}

Chaque programme est représenté par une vignette (ou une ligne dans un tableau), qui donne une vue d’ensemble du programme et des liens rapides pour effectuer des actions.

![Vignette du programme](assets/program-card.png)

* Image du programme (si configurée)
* Nom du programme
* Type de service :
   * **Cloud Experience Manager** pour les programmes AEM as a Cloud Service
   * **Experience Manager** pour [programmes AMS](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/introduction)
* [Type de programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) :
   * Sandbox
   * Production
* Statut
* Solutions configurées
* Date de création

Selon les options sélectionnées lors de la création du programme, un programme de production peut être marqué pour afficher des fonctionnalités supplémentaires.

* [HIPAA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

  ![Badge HIPAA](assets/hipaa.png)

* [Protection WAF-DDOS](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

  ![Badge WAF-DDOS](assets/waf-ddos-protection.png)

* [Contrat de niveau de service à 99,99 %](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)

  ![Badge SLA 99,99 %](assets/9999-sla.png)

L’icône d’informations permet un accès rapide à des informations supplémentaires sur le programme (utile dans la vue Liste).

![Informations](assets/information-list-view.png)

L’icône représentant des points de suspension vous permet d’accéder à des actions supplémentaires que vous pouvez effectuer sur le programme.

![Bouton représentant des points de suspension pour les programmes](assets/program-ellipsis.png)

* Accéder à un [environnement](/help/implementing/cloud-manager/manage-environments.md) particulier du programme
* Ouvrir la [vue d’ensemble du programme](#program-overview)
* [Modifier le programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#editing)
* [Suppression d’un programme d’environnement de test](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-sandbox-program)

>[!TIP]
>
>Pour plus d’informations sur les programmes et la création et la gestion des programmes, consultez les documents suivants.
>
>* [Programmes et types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
>* [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)
>* [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

### Section Liens rapides {#quick-links-section}

La section Liens rapides vous donne accès aux ressources connexes couramment utilisées.

## Fenêtre Vue d’ensemble du programme {#program-overview}

Une fois que vous avez sélectionné un programme dans la console **[Mes programmes](#my-programs-console)**, vous accédez à la fenêtre **Aperçu du programme**.

![Vue d’ensemble du programme](assets/program-overview.png)

La vue d’ensemble du programme vous donne accès à toutes les informations d’un programme Cloud Manager. Comme la console **Mes programmes**, elle est composée de plusieurs parties.

1. Des [barres d’outils](#program-overview-toolbar) pour revenir rapidement à la console Mes programmes et naviguer dans le programme.
1. Des [onglets](#program-tabs) pour basculer entre les différents éléments du programme.
1. Un [appel à l’action](#cta) basé sur les dernières actions du programme.
1. Une [vue d’ensemble des environnements](#environments) du programme.
1. Une [vue d’ensemble des pipelines](#pipelines) du programme.
1. Une [présentation des performances](#performance) du programme
1. Des liens vers des [ressources utiles](#useful-resources).

### Barres d’outils {#program-overview-toolbar}

Les barres d’outils de la présentation du programme sont similaires à celles de la [console Mes programmes](#my-programs-toolbars). Seules les différences sont indiquées ici.

#### En-tête de Cloud Manager {#cloud-manager-header-2}

L’en-tête de Cloud Manager comporte un menu Hamburger qui s’ouvre automatiquement et affiche les onglets navigables de la vue d’ensemble du programme.

![Menu Hamburger de Cloud Manager](assets/cloud-manager-hamburger.png)

Appuyez ou cliquez sur l’icône de menu Hamburger pour masquer les onglets.

#### Barre d’outils des programmes {#program-toolbar-2}

La barre d’outils du programme vous permet de basculer rapidement vers d’autres programmes, mais vous permet également d’accéder à des actions contextuelles telles que l’ajout et la modification du programme.

![Barre d’outils du programme](assets/cloud-manager-program-toolbar.png)

De plus, la barre d’outils indique toujours l’onglet sur lequel vous vous trouvez si vous avez choisi de masquer les onglets à l’aide du menu Hamburger.

### Onglets des programmes {#program-tabs}

Chaque programme comporte de nombreuses options et données. Ces données sont regroupées dans des onglets afin de faciliter la navigation dans le programme. Les onglets permettent d’accéder aux éléments suivants :

* Vue d’ensemble : vue d’ensemble du programme, telle que décrite dans le présent document.
* [Activité](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity) : historique des exécutions de pipeline du programme.
* [Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines) : tous les pipelines configurés pour le programme.
* [Référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) : tous les référentiels configurés pour le programme.
* [Rapports](/help/implementing/cloud-manager/sla-reporting.md) : mesures, telles que les données SLA.
* [Environnements](/help/implementing/cloud-manager/manage-environments.md) : tous les environnements configurés pour le programme.
* [Paramètres de domaine](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - Gestion des noms de domaine personnalisés pour le programme
* [Certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) - Gestion des certificats SSL pour le programme
* [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) - Définition de listes autorisées pour certaines adresses IP
* [Jeux de contenu](/help/implementing/developing/tools/content-copy.md) : jeux de contenu créé à des fins de copie.
* [Activité Copie de contenu](/help/implementing/developing/tools/content-copy.md) : activités de copie de contenu.
* [Infrastructure réseau](/help/security/configuring-advanced-networking.md) - Gérez les options de mise en réseau avancées pour le programme
* Parcours de formation : ressources de formation supplémentaires pour Cloud Manager.

Par défaut, lorsque vous ouvrez un programme, vous accédez à l’onglet **Vue d’ensemble**. L’onglet actif est mis en surbrillance. Sélectionnez un autre onglet pour afficher ses détails.

Utilisez le menu Hamburger dans l’[en-tête de Cloud Manager](#cloud-manager-header-2) pour masquer les onglets.

### Appel à l’action {#cta}

La section Appel à l’action vous fournit des informations utiles en fonction du statut de votre programme. Pour un nouveau programme, vous pouvez voir les étapes suivantes proposées ainsi qu&#39;un rappel d&#39;une date de mise en service, [définie lors de la création du programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).

![Appel à l’action pour un nouveau programme](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

Pour un programme actif, vous pouvez voir le statut de votre dernier déploiement accompagné de liens pour obtenir plus de détails pour démarrer un nouveau déploiement.

![Appel à l’action](/help/implementing/cloud-manager/assets/info-banner.png)

### Vignette Environnements {#environments}

La vignette **Environnements** vous fournit une vue d’ensemble de vos environnements ainsi que des liens vers les actions rapides.

La carte **Environnements** répertorie seulement trois environnements. Cliquez sur **Tout afficher** pour voir tous les environnements du programme.

Consultez le document [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la gestion de vos environnements.

### Vignette Pipelines {#pipelines}

La vignette **Pipelines** vous fournit une vue d’ensemble de vos pipelines ainsi que des liens vers les actions rapides.

La vignette **Pipelines** répertorie seulement trois pipelines. Cliquez sur **Tout afficher** pour voir tous les pipelines du programme.

Consultez le document [Gestion des pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) pour plus d’informations sur la gestion des pipelines.

### Carte de performance {#performance}

La carte **Performance** donne un aperçu du **[tableau de bord CDN](/help/implementing/cloud-manager/cdn-performance.md)**.

![Carte de performance](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

### Ressources utiles {#useful-resources}

La section **Ressources utiles** fournit des liens vers des ressources de formation supplémentaires pour Cloud Manager.

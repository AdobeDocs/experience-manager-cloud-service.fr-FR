---
title: Navigation dans l’interface utilisateur de Cloud Manager
description: Découvrez l’organisation de l’interface d’utilisation de Cloud Manager et comment gérer vos programmes et vos environnements.
exl-id: 3f3d7631-2bc9-440b-9888-50f6529bcd42
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: eb2e1555f684a68807b0b3764cd1be03c2d439ab
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 41%

---


# Naviguer dans l’interface d’utilisation de Cloud Manager {#navigation}

Découvrez l’organisation de l’interface d’utilisation de Cloud Manager et comment gérer vos programmes et vos environnements.

L’interface d’utilisation de Cloud Manager est composée principalement de deux interfaces graphiques :

* [La console Mes programmes](#my-programs-console) permet d’afficher et de gérer tous vos programmes.
* [La fenêtre Vue d’ensemble du programme](#program-overview) permet de consulter les détails d’un programme individuel et de le gérer.

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
1. [Liens rapides](#quick-links-section) pour accéder facilement aux ressources associées.

>[!TIP]
>
>Consultez le document [Programmes et types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) pour plus d’informations sur les programmes.

### Barres d’outils {#my-programs-toolbars}

Il y a deux barres d’outils superposées.

#### En-tête de Cloud Manager {#cloud-manager-header}

La première est l’en-tête de Cloud Manager, qui est présent en permanence lorsque vous naviguez dans Cloud Manager. Il s’agit d’un élément ancré qui permet d’accéder aux paramètres et aux informations relatifs à l’ensemble des programmes Cloud Manager.

![En-tête Experience Cloud](assets/experience-cloud-header.png)

1. Cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) (menu afficher ou masquer) pour accéder à divers onglets qui peuvent vous emmener à des parties spécifiques d’un programme. Vous pouvez également basculer entre le [tableau de bord de la licence](/help/implementing/cloud-manager/license-dashboard.md) et la console **[Mes programmes](#my-programs-console)** en fonction du contexte.
1. Cliquez sur le bouton Adobe Cloud Manager pour revenir à la console Mes programmes de Cloud Manager, où que vous soyez dans Cloud Manager.
1. Cliquez sur **Feedback** pour fournir des commentaires à Adobe sur Cloud Manager.
1. Cliquez sur le sélecteur d’organisation pour afficher l’organisation dans laquelle vous êtes actuellement connecté (dans cet exemple, Foundation Internal). Cliquez pour passer à une autre organisation si votre Adobe ID est associé à plusieurs d’entre elles.
1. Cliquez sur ![Icône Applications](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) (sélecteur de solutions) pour accéder rapidement à d’autres solutions Experience Cloud.
1. Cliquez sur ![Icône d’aide](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Help_18_N.svg) pour accéder rapidement aux ressources d’apprentissage et d’assistance.
1. Cliquez sur ![Icône Bell](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) ([Notifications](/help/implementing/cloud-manager/notifications.md)) pour afficher les notifications et les annonces, entre autres.
1. Cliquez sur l’icône représentant l’accès de l’utilisateur à vos paramètres utilisateur. Si vous n’avez configuré aucune image d’utilisateur ou d’utilisatrice, une icône est attribuée de manière aléatoire.

#### Barre d’outils du programme {#program-toolbar}

La barre d’outils des programmes fournit des liens pour basculer entre les programmes Cloud Manager et des actions contextuelles.

![Barre d’outils des programmes](assets/program-toolbar.png)

1. Le sélecteur **Mes programmes** ouvre une liste déroulante dans laquelle vous pouvez sélectionner d’autres programmes rapidement ou prendre des actions appropriées au contexte, telles que la création d’un nouveau programme.
1. Le lien **Prise en main** vous donne accès au [parcours de documentation d’intégration](/help/journey-onboarding/overview.md) pour vous aider à maîtriser Cloud Manager.
1. Le bouton d’action propose des actions contextuelles, telles que l’ajout d’un programme.

### Statistiques et appels à l&#39;action {#statistics}

La section statistiques et appel à l’action fournit des données agrégées pour votre organisation. Par exemple, si vous avez configuré vos programmes avec succès, les statistiques de vos activités au cours des 90 derniers jours peuvent s’afficher, notamment :

* Le nombre de [déploiements](/help/implementing/cloud-manager/deploy-code.md)
* Le nombre de [problèmes relatifs à la qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) identifiés
* Le nombre de versions

Si vous êtes au commencement de la configuration de votre organisation, vous pouvez obtenir des conseils sur les étapes suivantes ou des ressources de documentation.

### Section Mes programmes {#my-programs-section}

Le contenu principal de la console **Mes programmes** est la liste des programmes de la section **Mes programmes** .

La section **Mes programmes** répertorie les cartes représentant chaque programme. Cliquez sur une carte pour accéder à la page **Vue d’ensemble du programme** du programme concerné pour obtenir plus d’informations sur le programme.

>[!NOTE]
>
>Selon vos privilèges, il se peut que vous ne puissiez pas sélectionner certains programmes.


Pour trouver plus facilement le programme dont vous avez besoin, utilisez les options de tri.

![Options de tri](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* Trier par :
   * **Date de création** (par défaut)
   * **Nom du programme**
   * **Statut**
* ![Icône Ordre de tri descendant](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) ascendant (par défaut) / ![Icône Ordre descendant](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Descendant
* ![Icône Affichage de grille classique](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) Affichage de la grille (par défaut)
* ![Icône Afficher la liste](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ViewList_18_N.svg) Mode Liste

#### Cartes de programme {#program-cards}

Une carte (ou ligne dans un tableau) représente chaque programme, fournissant un aperçu du programme et des liens rapides pour agir.

![Vignette du programme](assets/program-card.png)

* Image associée au programme, si elle est configurée. L&#39;image ci-dessus est &quot;WKND&quot;.
* Nom attribué au programme. L’image ci-dessus montre &quot;SecurBank Sample&quot; comme nom du programme.
* Type de service :
   * **Experience Manager Cloud** — pour les programmes AEM as a Cloud Service
   * **Experience Manager** — pour les [programmes AMS (Adobe Managed Services)](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/introduction)
* [Type de programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) :
   * Sandbox
   * Production
* État. Dans l’image ci-dessus, l’état est Prêt avec une coche.
* Solutions configurées. Dans l’image ci-dessus, Sites et Assets sont les solutions configurées.
* Date de création.

Un programme de production peut comporter un badge pour afficher les fonctionnalités supplémentaires sélectionnées au moment de l’ajout, telles que :

* ![Badge HIPAA](assets/hipaa.png) [HIPAA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* ![Badge WAF-DDOS](assets/waf-ddos-protection.png) [Protection WAF-DDOS](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

* [99,99 % SLA (contrat de niveau de service)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)

L’icône d’informations permet un accès rapide à des informations supplémentaires sur le programme (utile dans la vue Liste).

![Informations](assets/information-list-view.png)

L&#39;icône ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_22/Smock_More_22_N.svg) vous donne accès à des actions supplémentaires que vous pouvez entreprendre sur le programme.

![Bouton représentant des points de suspension pour les programmes](assets/program-ellipsis.png)

* Accédez à une ![icône de données](https://spectrum.adobe.com/static/icons/workflow_22/Smock_Data_22_N.svg) [Environnement](/help/implementing/cloud-manager/manage-environments.md) particulier du programme
* Ouvrez l’ ![icône de présentation du programme](/help/implementing/cloud-manager/assets/program-overview.svg) [Aperçu du programme](#program-overview)
* ![Icône Modifier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) [Modifier le programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#editing)
* ![Icône Supprimer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)[Supprimer un programme sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-sandbox-program)

>[!TIP]
>
>Pour plus d’informations sur les programmes et l’ajout et la gestion des programmes, voir :
>
>* [Programmes et types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
>* [Créer des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
>* [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)


### Section Liens rapides {#quick-links-section}

La section Liens rapides vous donne accès aux ressources fréquemment utilisées qui sont liées.

## Page Aperçu du programme {#program-overview}

Lorsqu’un programme est sélectionné dans la console **[Mes programmes](#my-programs-console)**, vous accédez à la page **Aperçu du programme**.

![Vue d’ensemble du programme](assets/program-overview.png)

La vue d’ensemble du programme vous donne accès à toutes les informations d’un programme Cloud Manager. Comme la console **Mes programmes**, elle est composée de plusieurs parties.

1. [Barres d’outils](#program-overview-toolbar) pour revenir rapidement à la console Mes programmes et parcourir le programme
1. Des [onglets](#program-tabs) pour basculer entre les différents éléments du programme.
1. Un [appel à l’action](#cta) basé sur les dernières actions du programme.
1. Une [vue d’ensemble des environnements](#environments) du programme.
1. Une [vue d’ensemble des pipelines](#pipelines) du programme.
1. Une [présentation des performances](#performance) du programme
1. Des liens vers des [ressources utiles](#useful-resources).

### Barres d’outils {#program-overview-toolbar}

Les barres d’outils pour la présentation du programme sont similaires à celles de la [console Mes programmes](#my-programs-toolbars). Seules les différences sont indiquées ici.

#### En-tête de Cloud Manager {#cloud-manager-header-2}

Dans le coin supérieur gauche de la page se trouve l’en-tête Adobe Cloud Manager. Vous pouvez cliquer sur ![Icône de menu latéral](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher ou masquer le menu latéral des onglets dans d’autres zones du logiciel.

![Menu latéral Cloud Manager](assets/cloud-manager-hamburger.png)

Cliquez sur Adobe Cloud Manager pour revenir à la page d’accueil.

#### Barre d’outils du programme {#program-toolbar-2}

La barre d’outils du programme permet de basculer rapidement vers d’autres programmes, mais permet également d’accéder à des actions contextuelles telles que l’ajout et la modification du programme.

![Barre d’outils du programme](assets/cloud-manager-program-toolbar.png)

La barre d’outils affiche toujours l’onglet actif, même si vous avez masqué les onglets à l’aide du menu hamburger.

### Onglets des programmes {#program-tabs}

Chaque programme comporte de nombreuses options et des données associées. Ces options et données sont regroupées dans des onglets afin de faciliter la navigation dans le programme. Les onglets permettent d’accéder aux éléments suivants :

**Programme**

* ![Icône d’affichage de grille moderne](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ModernGridView_18_N.svg) - Présentation du programme, comme décrit dans le document actuel
* ![Icône Bell](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) [Activité](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity) - Historique des exécutions de pipeline du programme
* ![Icône de workflow](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) [Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines) - Tous les pipelines configurés pour le programme
* ![Icône de dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) [Référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) - Tous les référentiels configurés pour le programme
* ![Icône Graph ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_GraphPie_18_N.svg) [Rapports](/help/implementing/cloud-manager/sla-reporting.md) - Mesures telles que les données SLA

**Services**

* ![Icône de données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) [Environnements](/help/implementing/cloud-manager/manage-environments.md) - Tous les environnements configurés pour le programme
* ![ Icône Pages Web ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) [Edge Delivery Sites](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md) - Gérer les sites Edge Delivery
* ![Icône Paramètres](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) [Paramètres de domaine](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - Gestion des noms de domaine personnalisés pour le programme
* ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) [Certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) - Gestion des certificats SSL pour le programme
* ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) [Configurations CDN](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - Gérer les configurations CDN
* ![Icône Liste de tâches](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) - Définition de listes autorisées pour certaines adresses IP
* ![Icône de boîte](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) [Visionneuses de contenu](/help/implementing/developing/tools/content-copy.md) - Visionneuses de contenu créées à des fins de copie
* ![Icône Historique](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) [Copier l’activité de contenu](/help/implementing/developing/tools/content-copy.md) - Activités de copie de contenu
* ![Icône Canal](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Channel_18_N.svg) [Infrastructure réseau](/help/security/configuring-advanced-networking.md) - Gestion des options de mise en réseau avancées pour le programme

**Resources**

* ![Icône de livre](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Book_18_N.svg) Chemins d’apprentissage - Ressources d’apprentissage supplémentaires sur Cloud Manager

Par défaut, lorsque vous ouvrez un programme, vous accédez à l’onglet **Vue d’ensemble**. L’onglet actif est mis en surbrillance. Sélectionnez un autre onglet pour afficher ses détails.

Dans le coin supérieur gauche de l’en-tête [ de Cloud Manager ](#cloud-manager-header-2), cliquez sur l’icône ![Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher ou masquer le menu latéral des onglets.

### Appel à destination {#cta}

La section Appel à l’action fournit des informations utiles en fonction du statut de votre programme. Pour un nouveau programme, vous pouvez voir les étapes suivantes et un rappel d’une date de mise en service, [définie lors de la création du programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).

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

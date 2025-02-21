---
title: Création d’un site Edge Delivery dans Cloud Manager
description: Découvrez comment créer rapidement un site Edge Delivery dans Cloud Manager en un clic de bouton.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1e4e07d2690bcbd44ffe994a571ffc0a8ae7eb50
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 24%

---


# À propos de la création d’un site Edge Delivery dans Cloud Manager {#about-one-click-edge-delivery-site}

La fonctionnalité Créer un site Edge Delivery est conçue pour vous aider à automatiser l’intégration et le déploiement des sites Edge Delivery dans Cloud Manager. Cela simplifie grandement le processus en vous permettant de cliquer sur un seul bouton. Ce clic unique fournit l’infrastructure requise, l’intègre à GitHub pour la gestion de versions et configure votre stockage de documents et de ressources dans Google Drive.

Cette automatisation permet de réduire l’effort manuel nécessaire à la configuration de votre site initial. Cela garantit des workflows transparents, l’évolutivité et améliore les performances de vos équipes en matière de gestion de contenu Edge.

## Concepts clés {#key-concepts}

Concepts clés lors de la création d’un site Edge Delivery dans Cloud Manager en un seul clic.

| Concept clé | Description |
| --- | --- |
| Déploiement Edge automatisé | <ul><li>Les utilisateurs peuvent créer et configurer des sites Edge Delivery instantanément.</li><li>L’utilisation de l’intégration de Cloud Manager au workflow CI/CD réduit ou élimine le besoin de processus d’intégration manuels.</li><li>Intégration à Cloud Manager pour des workflows CI/CD transparents.</li></ul> |
| Intégration à Cloud Manager | <ul><li>Utilise l’interface d’utilisation de Cloud Manager pour déclencher le processus Edge Delivery en un clic.</li><li>Permet d’accéder à la création et au déploiement automatisés du référentiel.</li></ul> |
| Gestion de versions basée sur GitHub | <ul><li>Crée un référentiel GitHub au sein d’une organisation à l’aide de modèles standard prédéfinis pour normaliser les déploiements.</li><li>Établit un lien avec le robot AEM pour les mises à jour de contenu.</li></ul> |
| Intégration du stockage de documents et de ressources | <ul><li>Génère un dossier Google Drive pour le stockage.<li>Installe l’application AEM Code Sync sur le référentiel, assurant ainsi une synchronisation et un déploiement transparents.</li></li><li>Les collaborateurs peuvent gérer facilement les documents.</li></ul> |
| Sécurité et confidentialité | <ul><li>Garantit la conformité aux normes de sécurité d’entreprise.</li><li>Prend en charge plusieurs sites Edge Delivery sous différents clients Cloud Manager.</li></ul> |

<!-- >
## Practical use cases {#use-cases}

| Use case | Description |
| --- | --- |
| Website and application deployment | <ul><li>Automate the hosting and delivery of static or dynamic sites.</li><li>Ensure fast performance through edge caching. </li></ul> |
| API gateway and content delivery | <ul><li>Optimize API responses by caching data at the edge.</li><li>Reduce backend load and improved response times. </li></ul> |
| Real-time content updates | <ul><li>Instant deployment of new content across edge locations.</li><li>Support integration with automated content pipelines. </li></ul> |
| Edge computing workloads | <ul><li>Support serverless computing to process workloads closer to users.</li><li>Reduce latency and enhance performance. </li></ul> |
| Security and governance | <ul><li>Security is provided with integrated DDoS (Distributed Denial of Service) protection and WAF (Web Application Firewall) integration.</li><li>Ensure that content is delivered securely through TLS (Transport Security Layer) encryption. </li></ul> |
-->

## Création d’un site Edge Delivery dans Cloud Manager en un seul clic {#one-click-edge-delivery-site}

Pour créer un site de diffusion Adobe Edge en un clic, votre entreprise doit disposer d’une licence Edge Delivery Services disponible. Cette licence fait partie de Adobe Experience Manager (AEM) et est nécessaire pour créer Edge Delivery Services dans Cloud Manager.

En termes d’autorisations, vous devez être membre du rôle Propriétaire de l’entreprise ou disposer des autorisations appropriées pour ajouter ou modifier des programmes dans Cloud Manager. Ce niveau d’accès permet de gérer l’intégration d’Edge Delivery Services dans vos programmes.

Voir également [Présentation d’Edge Delivery Services dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

<!-- PROPER AEM BOT CONFIGURATIONS MUST BE IN PLACE FIRST FOR AUTOMATIC CONTENT UPDATES? TRUE or FALSE? -->

**Pour créer un site Edge Delivery dans Cloud Manager en un seul clic, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche.
1. Dans le menu de gauche, sous l’en-tête **Programme**, cliquez sur **Aperçu**.
1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**.
1. Sur la page Edge Delivery, dans la boîte de dialogue **Liste de tâches Edge Delivery**, dans la zone de groupe **Ajouter un site Edge Delivery**, cliquez sur **Créer un site maintenant**.
1. Dans la boîte de dialogue **Créer un site Edge Delivery**, dans le champ de texte **Nom du projet**, saisissez le nom de votre site, puis cliquez sur **Créer un site maintenant**.

   Un toast s’affiche près du centre supérieur de l’écran pour vous informer que l’approvisionnement du site Edge Delivery a commencé.

Une fois l’approvisionnement et la validation du site terminés par Cloud Manager, le **nom du site** (nom du projet que vous avez saisi précédemment) s’affiche dans la zone de liste **Sites Edge Delivery** de la page Edge Delivery. En outre, une coche verte s’affiche à gauche de l’URL du référentiel.


### Explorer un site Edge Delivery créé en un clic {#explore-one-click-ed-site}

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche.
1. Dans le menu de gauche, sous l’en-tête **Programme**, cliquez sur **Aperçu**.
1. Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**.
1. Sur la page Edge Delivery, effectuez l’une des opérations suivantes :

   | Éléments à explorer | Étapes |
   | --- | --- |
   | référentiel GitHub d’un site. | <ul><li>Dans la zone de liste **Sites Edge Delivery**, sous l’en-tête de colonne **Référentiel**, cliquez sur l’URL du site que vous venez de créer.<br>Vous devrez peut-être vous connecter à GitHub avec votre nom d’utilisateur ou votre adresse e-mail et votre mot de passe.</li> |
   | Publication d’un site | <ul><li> Dans la zone de liste **Sites Edge Delivery**, à l’extrémité droite du nom de votre site, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour afficher le menu déroulant.</li><li>Cliquez sur ![icône de vérification de publication](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PublishCheck_18_N.svg) **Publier le site** dans le menu déroulant.<br>Un message toast s’affiche pour vous informer que la publication du site a bien démarré.</li></ul> |
   | Prévisualiser un site publié | <ul><li>Dans la zone de liste **Sites Edge Delivery**, sous l&#39;en-tête de colonne **Nom du site**, cliquez sur l&#39;URL du site que vous venez de créer et de publier.<br>Dans la barre d’adresse URL de votre navigateur, notez que l’URL du site se termine par des `.page` indiquant que vous voyez un aperçu du site.</li><li>Pour afficher le site en ligne, modifiez manuellement `.page` en `.live` dans la barre d’adresse URL.</li></ul> |
   | Accorder aux utilisateurs l’accès au référentiel de contenu sur Google Drive | <ul><li> Dans la zone de liste **Sites Edge Delivery**, à l’extrémité droite du nom de votre site, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour afficher le menu déroulant.</li><li>Cliquez sur ![icône Ajouter des utilisateurs](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg) **Accédez au référentiel de contenu** dans le menu déroulant.</li><li>Dans la boîte de dialogue **Ajouter des collaborateurs à votre site**, saisissez l’adresse e-mail d’un contributeur, puis cliquez sur ![Icône de coche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Continuez à ajouter des e-mails aux contributeurs, si nécessaire.</li><li>Lorsque vous avez terminé, cliquez sur **Ajouter des collaborateurs**.</li><li>Pour partager le lien avec vos collaborateurs de contenu, dans la boîte de dialogue **Collaboration ajoutée** cliquez sur **OK**.</li><li>Dans la boîte de dialogue Collaboration ajouté avec succès, cliquez sur ![Icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le lien et le partager avec vos collaborateurs.<br>Avant de partager le lien, vérifiez que les collaborateurs sont connectés avec l’adresse e-mail associée à leur compte IMS. Si leur compte de messagerie IMS n’est pas disponible, ils doivent utiliser l’adresse e-mail ajoutée en tant que collaborateurs. Cela permet de s’assurer que les collaborateurs peuvent accéder au lien et voir le contenu à modifier ou à mettre à jour sur Google Drive.</li><li>Une fois la modification terminée, cliquez sur **Publier le site** dans Cloud Manager, comme décrit ci-dessus.<br>Ou prévisualisez les modifications apportées comme décrit ci-dessus.</li></ul> |
   | Accorder aux utilisateurs l’accès au référentiel de base sur GitHub | <ul><li> Dans la zone de liste **Sites Edge Delivery**, à l’extrémité droite du nom de votre site, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour afficher le menu déroulant.</li><li>Cliquez sur ![Icône de code](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) **Accédez au référentiel de base** dans le menu déroulant.</li><li>Dans la boîte de dialogue **Accéder au référentiel de base de votre site**, saisissez le nom d’utilisateur GitHub d’un collaborateur, puis cliquez sur ![Icône de coche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Continuez à ajouter des noms d’utilisateur GitHub, si nécessaire.</li><li>Lorsque vous avez terminé, cliquez sur **Ajouter des collaborateurs**.</li>Les utilisateurs doivent accorder l’accès à leur propre nom d’utilisateur GitHub pour afficher le référentiel. |



---
title: Création d’un site Edge Delivery dans Cloud Manager en un seul clic
description: Découvrez comment créer rapidement un site Edge Delivery dans Cloud Manager en un clic.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 292bf0b4-990b-4980-b971-91b8aedde3de
source-git-commit: 59743546b5e057599f60a76d3087d7c5b6423b2e
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 98%

---

# À propos de la création d’un site Edge Delivery dans Cloud Manager {#about-one-click-edge-delivery-site}

La fonctionnalité Créer un site Edge Delivery est conçue pour automatiser l’intégration et le déploiement des sites Edge Delivery dans Cloud Manager. Cela simplifie grandement le processus en vous permettant de cliquer sur un seul bouton. Ce clic unique fournit l’infrastructure requise, l’intègre à GitHub pour la gestion de versions et configure votre stockage de documents et de ressources dans Google Drive.

Cette automatisation permet de réduire l’effort manuel nécessaire à la configuration de votre site initial. Cela garantit des workflows transparents, l’évolutivité et améliore les performances de vos équipes en matière de gestion de contenu Edge.

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

## Créer un site Edge Delivery dans Cloud Manager en un seul clic {#one-click-edge-delivery-site}

Pour créer un site Adobe Edge Delivery en un clic, votre entreprise doit disposer d’une licence Edge Delivery Services disponible. Cette licence fait partie d’Adobe Experience Manager (AEM) et est nécessaire pour créer Edge Delivery Services dans Cloud Manager.

En termes d’autorisations, vous devez être membre du rôle Propriétaire de l’entreprise ou disposer des autorisations appropriées pour ajouter ou modifier des programmes dans Cloud Manager. Ce niveau d’accès permet de gérer l’intégration d’Edge Delivery Services dans vos programmes.

Voir également [Présentation d’Edge Delivery Services dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

<!-- PROPER AEM BOT CONFIGURATIONS MUST BE IN PLACE FIRST FOR AUTOMATIC CONTENT UPDATES? TRUE or FALSE? -->

**Pour créer un site Edge Delivery dans Cloud Manager en un clic :**

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche.
1. Dans le menu de gauche, sous l’en-tête **Programme**, cliquez sur **Vue d’ensemble**.
1. Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**.
1. Sur la page Edge Delivery, dans la boîte de dialogue **Liste des tâches Edge Delivery**, dans la zone de groupe **Ajouter un site Edge Delivery**, cliquez sur **Créer un site maintenant**.
1. Dans la boîte de dialogue **Créer un site Edge Delivery**, dans le champ de texte **Nom du projet**, saisissez le nom de votre site, puis cliquez sur **Créer un site maintenant**.

   Une notification toast s’affiche près du centre supérieur de l’écran pour vous informer que l’approvisionnement du site Edge Delivery a commencé.

Une fois l’approvisionnement et la validation du site terminés par Cloud Manager, le **nom du site** (nom du projet que vous avez saisi précédemment) s’affiche dans la zone de liste **Sites Edge Delivery** de la page Edge Delivery. En outre, une coche verte s’affiche à gauche de l’URL du référentiel.


### Découvrir comment créer un site Edge Delivery en un seul clic {#explore-one-click-ed-site}

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche.
1. Dans le menu de gauche, sous l’en-tête **Programme**, cliquez sur **Vue d’ensemble**.
1. Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**.
1. Dans la page Edge Delivery, réalisez une des étapes suivantes :

   | Éléments à explorer | Étapes |
   | --- | --- |
   | Référentiel GitHub d’un site | <ul><li>Dans la zone de liste **Sites Edge Delivery**, sous l’en-tête de colonne **Référentiel**, cliquez sur l’URL du site que vous venez de créer.<br>Vous devrez peut-être vous connecter à GitHub avec votre nom d’utilisateur ou votre adresse e-mail et votre mot de passe.</li> |
   | Publier un site | <ul><li> Dans la zone de liste **Sites Edge Delivery**, à l’extrémité droite du nom de votre site, cliquez sur l’![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour afficher le menu déroulant.</li><li>Cliquez sur l’![icône de vérification de publication](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PublishCheck_18_N.svg) **Publier le site** dans le menu déroulant.<br>Un message toast s’affiche pour vous informer que la publication du site a bien démarré.</li></ul> |
   | Prévisualiser un site publié | <ul><li>Dans la zone de liste **Sites Edge Delivery**, sous l’en-tête de colonne **Nom du site**, cliquez sur l’URL du site que vous venez de créer et de publier.<br>Dans la barre d’adresse URL de votre navigateur, notez que l’URL du site se termine par `.page` indiquant que vous voyez un aperçu du site.</li><li>Pour afficher le site en ligne, modifiez manuellement `.page` en `.live` dans la barre d’adresse URL.</li></ul> |
   | Accorder aux utilisateurs et utilisatrices l’accès au référentiel de contenu sur Google Drive | <ul><li> Dans la zone de liste **Sites Edge Delivery**, à l’extrémité droite du nom de votre site, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour afficher le menu déroulant.</li><li>Cliquez sur ![icône Ajouter des utilisateurs et utilisatrices](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg) **Accédez au référentiel de contenu** dans le menu déroulant.</li><li>Dans la boîte de dialogue **Ajouter des collaborateurs et collaboratrices à votre site**, saisissez l’adresse e-mail d’un contributeur ou d’une contributrice, puis cliquez sur ![icône de coche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Continuez à ajouter des e-mails de contributeurs et contributrices, si nécessaire.</li><li>Lorsque vous avez terminé, cliquez sur **Ajouter des collaborateurs et collaboratrices**.</li><li>Pour partager le lien avec vos collaborateurs et collaboratrices de contenu, dans la boîte de dialogue **Collaboration ajoutée**, cliquez sur **OK**.</li><li>Dans la boîte de dialogue Collaboration ajoutée, cliquez sur ![icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le lien et le partager avec vos collaborateurs et collaboratrices.<br>Avant de partager le lien, vérifiez que les collaborateurs et collaboratrices sont connectés avec l’adresse e-mail associée à leur compte IMS. Si leur compte de messagerie IMS n’est pas disponible, les personnes doivent utiliser l’adresse e-mail ajoutée en tant que collaborateurs et collaboratrices. Cela permet de s’assurer que les collaborateurs et collaboratrices peuvent accéder au lien et voir le contenu à modifier ou à mettre à jour sur Google Drive.</li><li>Une fois la modification terminée, cliquez sur **Publier le site** dans Cloud Manager, comme décrit ci-dessus.<br>Vous pouvez aussi prévisualiser les modifications apportées comme décrit ci-dessus.</li></ul> |
   | Accorder aux utilisateurs et utilisatrices l’accès au référentiel de base sur GitHub | <ul><li> Dans la zone de liste **Sites Edge Delivery**, à l’extrémité droite du nom de votre site, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour afficher le menu déroulant.</li><li>Cliquez sur ![icône de code](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) **Accédez au référentiel de base** dans le menu déroulant.</li><li>Dans la boîte de dialogue **Accéder au référentiel de base de votre site**, saisissez le nom d’utilisateur GitHub d’un collaborateur ou d’une collaboratrice, puis cliquez sur ![icône de coche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg).</li><li>Continuez à ajouter des noms d’utilisateur GitHub, si nécessaire.</li><li>Lorsque vous avez terminé, cliquez sur **Ajouter des collaborateurs et collaboratrices**.</li>Les utilisateurs et utilisatrices doivent accorder l’accès à leur propre nom d’utilisateur GitHub pour afficher le référentiel. |

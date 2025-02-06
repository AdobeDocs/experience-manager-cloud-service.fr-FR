---
title: Configuration d’un site Edge Delivery dans Cloud Manager
description: Découvrez comment créer rapidement un site Edge Delivery dans Cloud Manager en un clic de bouton.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ac110fb006ed377403bce52c961712e6e449be88
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 8%

---


# À propos de la configuration d’un site Edge Delivery dans Cloud Manager {#about-provision-edge-delivery-site}

Le service Edge Delivery en un clic (EDS) est conçu pour automatiser l’intégration et le déploiement des sites Edge Delivery dans Cloud Manager. Cela simplifie grandement le processus en vous permettant de cliquer sur un seul bouton. Ce clic fournit l’infrastructure requise, s’intègre à GitHub pour le contrôle de version et configure votre stockage de documents et de ressources dans Google Drive.

Cette automatisation permet de réduire l’effort manuel nécessaire à la configuration de votre site initial. Il garantit des workflows transparents, l’évolutivité et améliore les performances de vos équipes en matière de gestion de contenu Edge.

## Concepts clés {#key-concepts}

Concepts clés de la mise en service d’un site Edge Delivery en un clic.

| Concept clé | Description |
| --- | --- |
| Déploiement automatisé d’Edge | <ul><li>Les utilisateurs et utilisatrices peuvent configurer les sites Edge Delivery instantanément.</li><li>Réduit ou élimine le besoin de processus d’intégration manuels grâce à l’intégration de Cloud Manager au workflow CI/CD.</li><li>S’intègre à Cloud Manager pour des workflows CI/CD transparents.</li></ul> |
| Intégration à Cloud Manager | <ul><li>Utilise l’interface utilisateur de Cloud Manager pour déclencher le processus Edge Delivery en un clic.</li><li>Permet d’accéder à la création et au déploiement automatisés du référentiel.</li></ul> |
| Contrôle de version basé sur GitHub | <ul><li>Crée un référentiel GitHub au sein d’une organisation à l’aide de modèles standard prédéfinis pour normaliser les déploiements.</li><li>établit des liens avec les robots AEM pour les mises à jour de contenu ;</li></ul> |
| Intégration du stockage de documents et de ressources | <ul><li>Génère un dossier Google Drive pour le stockage.<li>Installe l’application de synchronisation du code AEM sur le référentiel, assurant ainsi une synchronisation et un déploiement transparents.</li></li><li>Permet à plusieurs collaborateurs de gérer facilement des documents.</li></ul> |
| Sécurité et évolutivité | <ul><li>Garantit la conformité aux normes de sécurité d&#39;entreprise.</li><li>Prend en charge plusieurs sites Edge Delivery sous différents clients Cloud Manager.</li></ul> |



## Configuration d’un site Edge Delivery dans Cloud Manager {#provision-edge-delivery-site}

Pour pouvoir configurer un site de diffusion Adobe Edge en un clic, votre entreprise doit disposer d’une licence Edge Delivery Services disponible. Cette licence fait partie de Adobe Experience Manager (AEM) et est nécessaire pour configurer des Edge Delivery Services dans Cloud Manager.

En termes d’autorisations, vous devez être membre du rôle Propriétaire de l’entreprise ou disposer des autorisations appropriées pour ajouter ou modifier des programmes dans Cloud Manager. Ce niveau d’accès permet de gérer l’intégration des Edge Delivery Services dans vos programmes.

Voir également [Présentation d’Edge Delivery Services dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

LES CONFIGURATIONS DE ROBOTS AEM APPROPRIÉES DOIVENT-ELLES ÊTRE EN PLACE AU PRÉALABLE POUR LES MISES À JOUR AUTOMATIQUES DE CONTENU ? VRAI ? FAUX ?

**Pour configurer un site Edge Delivery dans Cloud Manager :**

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral gauche.
1. Dans le menu de gauche, sous l’en-tête **Services**, cliquez sur ![Icône de page web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
1. Sur la page Edge Delivery, dans la boîte de dialogue **Liste de tâches d’Edge Delivery**, dans la zone de groupe **Remplir les conditions préalables**, cliquez sur **Approvisionnement**.
1. Dans la boîte de dialogue **Approvisionnement d’un site Edge Delivery**, dans le champ de texte **Nom du projet**, saisissez le nom de votre site, puis cliquez sur **Approvisionnement**.
Un toast s’affiche près du centre supérieur de l’écran pour vous informer que l’approvisionnement du site Edge Delivery a commencé.
Une fois l’approvisionnement terminé et votre site validé, son nom apparaît dans la zone **Sites Edge Delivery** de la page Edge Delivery.

### Explorer un site Edge Delivery nouvellement configuré




1. Cliquez sur le lien Référentiel Git situé à droite du nom du site.

Publish. Cliquez sur Nom du site, apportez des modifications, puis publiez

Affichez la page dans l’aperçu, puis modifiez l’URL pour afficher la version active.

Ajoutez des collaborateurs.




## Publish et site Edge Delivery



## Ajout de collaborateurs à un site Edge Delivery


































Ces améliorations visent à améliorer l’automatisation, à simplifier les processus de configuration et à améliorer la collaboration des utilisateurs et utilisatrices Edge Delivery Services. <!-- CMGR-59362 -->

![Approvisionnement d’un site Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

![Boîte de dialogue Configuration du site Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)
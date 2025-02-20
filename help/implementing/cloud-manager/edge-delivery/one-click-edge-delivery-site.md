---
title: Création d’un site Edge Delivery dans Cloud Manager en un seul clic
description: Découvrez comment créer rapidement un site Edge Delivery dans Cloud Manager en un clic.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8034fc8454fca41c2430fa1179f80d2d2ab80563
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 71%

---


# À propos de la création d’un site Edge Delivery dans Cloud Manager en un seul clic {#about-one-click-edge-delivery-site}

Le service Edge Delivery Service (EDS) en un clic est conçu pour automatiser l’intégration et le déploiement des sites Edge Delivery dans Cloud Manager. Cela simplifie grandement le processus en vous permettant de cliquer sur un seul bouton. Ce clic unique fournit l’infrastructure requise, l’intègre à GitHub pour la gestion de versions et configure votre stockage de documents et de ressources dans Google Drive.

Cette automatisation permet de réduire l’effort manuel nécessaire à la configuration de votre site initial. Cela garantit des workflows transparents, l’évolutivité et améliore les performances de vos équipes en matière de gestion de contenu Edge.

## Concepts clés {#key-concepts}

Concepts clés de la création d’un site Edge Delivery en un clic.

| Concept clé | Description |
| --- | --- |
| Déploiement Edge automatisé | <ul><li>Les utilisateurs peuvent créer et configurer des sites Edge Delivery instantanément.</li><li>Il réduit ou élimine le besoin de processus d’intégration manuels grâce à l’intégration de Cloud Manager au workflow CI/CD.</li><li>Intégration à Cloud Manager pour des workflows CI/CD transparents.</li></ul> |
| Intégration à Cloud Manager | <ul><li>Utilise l’interface d’utilisation de Cloud Manager pour déclencher le processus Edge Delivery en un clic.</li><li>Permet d’accéder à la création et au déploiement automatisés du référentiel.</li></ul> |
| Gestion de versions basée sur GitHub | <ul><li>Crée un référentiel GitHub au sein d’une organisation à l’aide de modèles standard prédéfinis pour normaliser les déploiements.</li><li>Établit un lien avec le robot AEM pour les mises à jour de contenu.</li></ul> |
| Intégration du stockage de documents et de ressources | <ul><li>Génère un dossier Google Drive pour le stockage.<li>Installe l’application AEM Code Sync sur le référentiel, assurant ainsi une synchronisation et un déploiement transparents.</li></li><li>Permet à plusieurs personnes de gérer facilement des documents.</li></ul> |
| Sécurité et confidentialité | <ul><li>Garantit la conformité aux normes de sécurité d’entreprise.</li><li>Prend en charge plusieurs sites Edge Delivery sous différents clients Cloud Manager.</li></ul> |



## Création d’un site Edge Delivery dans Cloud Manager en un seul clic {#one-click-edge-delivery-site}

Pour pouvoir créer un site de diffusion Adobe Edge en un clic, votre entreprise doit disposer d’une licence Edge Delivery Services disponible. Cette licence fait partie de Adobe Experience Manager (AEM) et est nécessaire pour créer Edge Delivery Services dans Cloud Manager.

En termes d’autorisations, vous devez être membre du rôle Propriétaire de l’entreprise ou disposer des autorisations appropriées pour ajouter ou modifier des programmes dans Cloud Manager. Ce niveau d’accès permet de gérer l’intégration d’Edge Delivery Services dans vos programmes.

Voir également [Présentation d’Edge Delivery Services dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

LES CONFIGURATIONS DE ROBOTS AEM APPROPRIÉES DOIVENT-ELLES ÊTRE MISES EN PLACE AU PRÉALABLE POUR LES MISES À JOUR AUTOMATIQUES DE CONTENU ? VRAI ? FAUX ?

**Pour créer un site Edge Delivery dans Cloud Manager en un seul clic, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche.
1. Dans le menu de gauche, sous l’en-tête **Services**, cliquez sur ![Icône de page web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Sites Edge Delivery**.
1. Sur la page Edge Delivery, dans la boîte de dialogue **Liste des tâches Edge Delivery**, dans la zone de groupe **Remplir les conditions préalables**, cliquez sur **Approvisionner**.
1. Dans la boîte de dialogue **Approvisionner le site Edge Delivery**, dans le champ de texte **Nom du projet**, saisissez le nom de votre site, puis cliquez sur **Approvisionner**.
Un toast s’affiche près du centre supérieur de l’écran pour vous informer que l’approvisionnement du site Edge Delivery a commencé.
Une fois l’approvisionnement terminé et votre site validé, son nom apparaît dans la zone **Sites Edge Delivery** de la page Edge Delivery.

### Explorer un site Edge Delivery nouvellement créé


1. Cliquez sur le lien Référentiel Git situé à droite du nom du site.

Publier.

Cliquez sur Nom du site,

apportez des modifications, puis publiez

Affichez la page dans l’aperçu, puis modifiez l’URL pour afficher la version active.

Ajoutez des collaborateurs et collaboratrices.


## Prévisualiser un site Edge Delivery en un clic

## Publier un site Edge Delivery en un clic





## Ajout de collaborateurs à un site Edge Delivery en un clic


































Ces améliorations visent à améliorer l’automatisation, à simplifier les processus de configuration et à améliorer la collaboration des utilisateurs et utilisatrices Edge Delivery Services. <!-- CMGR-59362 -->

![Création d’un site Edge Delivery en un clic](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

![Boîte de dialogue Configuration du site Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)
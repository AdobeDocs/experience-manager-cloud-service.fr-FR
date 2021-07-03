---
title: Automatisation du contenu pour l’intégration de Creative Cloud
description: Génération de variantes des ressources à l’aide de l’intégration de Creative Cloud
contentOwner: AG
feature: Chargement,Traitement des ressources,Publication,Asset compute Microservices,Workflow
role: User,Admin
source-git-commit: a2c2a1f4ef4a8f0cf1afbba001d24782a6a2a24e
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---


# Générer des variantes de ressources à l’aide de l’intégration [!DNL Adobe Creative Cloud] {#content-automation}

Le module complémentaire d’automatisation du contenu intègre Experience Manager Assets en tant que Cloud Service et les API Adobe Creative Cloud pour traiter vos ressources de manière créative à grande échelle. Experience Manager utilise des [microservices de ressources](/help/assets/asset-microservices-overview.md) basés sur le cloud pour tirer parti des fonctionnalités de Adobe Creative Cloud et automatiser la création de ressources et la gestion des médias.

Pour modifier des ressources dans [!DNL Adobe Photoshop] et [!DNL Adobe Lightroom], il n’est pas nécessaire de les télécharger, de les modifier et de les transférer vers [!DNL Experience Manager Assets]. Il vous suffit de créer et configurer un profil de traitement, d’appliquer le profil à un dossier et de charger les ressources dans le dossier. Les ressources chargées dans le dossier sont traitées pour créer différentes variantes de cette ressource. Le traitement en masse et la modification des ressources, sans effort et cohérents, ont permis d’économiser des efforts manuels et d’accroître la vitesse du contenu. En outre, les développeurs et les partenaires peuvent étendre les microservices de ressources avec un accès direct à ces API et inclure une logique personnalisée.

Les utilisateurs peuvent créer des profils de traitement afin d’automatiser les opérations de création suivantes sur leurs ressources :

* **Réglage automatique** : Utilise l’intelligence artificielle pour analyser le contenu de l’image et corrige intelligemment la lumière et les couleurs en fonction des attributs uniques de l’image.
* **Hauteur** automatique : Utilise l’intelligence artificielle pour analyser le contenu de l’image et corriger la perspective biaisée dans les images. Par exemple, pour créer des horizons de niveau.
* **Paramètres prédéfinis** Lightroom : Applique une apparence définie par l’utilisateur aux images afin d’obtenir un aspect cohérent à l’aide de paramètres prédéfinis personnalisés.
* **Découpage d’image** : Utilise l’intelligence artificielle pour créer une sélection autour d’objets importants et supprimer l’arrière-plan à l’aide d’une seule commande.
* **Masque d’image** : Utilise l’intelligence artificielle pour créer un masque autour d’objets importants à l’aide d’une seule commande.
* **Actions Photoshop** : Applique une série de tâches (dans Photoshop) à un fichier ou à un lot de fichiers.
* **Remplacement d’objet dynamique** : Effectue une personnalisation à grande échelle en vous permettant de permuter des images tout en conservant tous les effets et ajustements appliqués à un fichier PSD.

## Utilisation d’un profil de traitement pour traiter des ressources {#process-assets}

Pour utiliser des profils de traitement afin de créer automatiquement des variations, procédez comme suit :

1. Contactez [l’Assistance clientèle d’Adobe](https://experienceleague.adobe.com/#support) pour recevoir la licence.

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Profils de traitement]**.

1. Sélectionnez **[!UICONTROL Créer]**, puis spécifiez un **[!UICONTROL Nom]**.

1. Sélectionnez l’onglet **[!UICONTROL Creative]**, indiquez le dossier de sortie, puis sélectionnez **[!UICONTROL Ajouter]** pour ajouter des configurations créatives.

1. Indiquez **[!UICONTROL Nom du rendu]** (ou nom de sortie), **[!UICONTROL Extension]** (ou type de fichier), sélectionnez **[!UICONTROL Qualité]** (ou paramètres de sortie), sélectionnez Inclut et Exclut les listes de type MIME (ou saisissez un filtre de ressource d’entrée) et sélectionnez l’opération de création requise.

1. Certaines opérations nécessitent un paramètre supplémentaire (ressource). Si nécessaire, indiquez des valeurs pour ces paramètres supplémentaires.

1. Ajoutez d’autres opérations créatives dans le cadre du même profil de traitement ou enregistrez le profil.

1. Appliquez le profil de traitement à un dossier. Sur la page **[!UICONTROL Propriétés]** d’un dossier, sélectionnez **[!UICONTROL Traitement des ressources]**, puis sélectionnez le profil de traitement à appliquer.

Une fois le profil de traitement appliqué à un dossier DAM, toutes les ressources chargées ou mises à jour dans ce dossier exécutent les opérations définies en plus du traitement standard. Les sous-dossiers héritent des mêmes profils que ceux appliqués aux dossiers parents. Les utilisateurs peuvent remplacer cet héritage.

Pour traiter les ressources existantes, sélectionnez les ressources, sélectionnez l’option **[!UICONTROL Retraiter]**, puis sélectionnez le profil de traitement requis.

## Conseils et restrictions {#limitations-best-practices}

* [!DNL Experience Manager] limite le traitement des ressources à 300 requêtes par minute par environnement et à 700 requêtes par minute par organisation.
* La taille du fichier est limitée à 4 Go pour les opérations de l’API [!DNL Adobe Photoshop] et 1 Go pour les opérations [!DNL Adobe Lightroom].

>[!MORELIKETHIS]
>
>* [Configurer et utiliser les microservices de ressources via des profils de traitement](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager] Intégration avec [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).


---
title: Extension de l’éditeur universel
description: Découvrez les différentes options permettant d’étendre les fonctionnalités de l’éditeur universel afin de prendre en charge les besoins des auteurs de contenu.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 0cab4a807be4aa402667feddb6a948f0d2db371f
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# Extension de l’éditeur universel {#extending}

Découvrez les différentes options permettant d’étendre les fonctionnalités de l’éditeur universel afin de prendre en charge les besoins des auteurs de contenu.

>[!TIP]
>
>L’éditeur universel propose également plusieurs options de personnalisation [personnalisation](/help/implementing/universal-editor/customizing.md) qui vous permettent de mieux répondre aux besoins de votre projet.

## Extensions {#extensions}

En tant que service Adobe Experience Cloud, l’interface utilisateur de l’éditeur universel peut être étendue à l’aide d’App Builder et d’Experience Manager. Adobe propose de nombreuses extensions toutes prêtes que vous pouvez utiliser pour votre projet.

* **[Sélecteur de produit AEM pour l’éditeur universel ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)** : intégrez les données Adobe Commerce en sélectionnant ou en supprimant les données de produit de l’éditeur.
* **[Brouillons de contenu de l’éditeur universel](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)** : créez, modifiez et gérez plusieurs brouillons de contenu.
* **[Sélecteur de ressources configurable](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)** : permet d’activer la sélection de ressources à partir de référentiels autres que celui utilisé par la page modifiée.
* **Éditeur de règles Forms** : ajoutez visuellement un comportement dynamique aux champs AEM Forms, sans codage.
* **[Exporter des fragments de contenu vers Adobe Target](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)** : exportez des fragments de contenu, créés dans Adobe Experience Manager as a Cloud Service vers Adobe Target pour être utilisés comme offres dans les activités Target, afin de tester et de personnaliser des expériences à grande échelle.
* **[Workflows de fragment de contenu](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)** : lancez un workflow AEM pour les fragments de contenu sélectionnés.

## Étendre l’interface utilisateur {#extending-ui}

Les extensions de l’interface utilisateur de l’éditeur universel sont des applications JavaScript créées avec Adobe App Builder. À l’aide de ces mêmes outils, vous pouvez également ajouter vos propres boutons et actions au menu d’en-tête et au panneau des propriétés, ainsi que créer vos propres événements pour l’éditeur universel.

Si vous souhaitez explorer les possibilités de créer vos propres extensions, consultez les ressources suivantes :

1. [Extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/) - Il s’agit de la documentation du développeur pour l’extension d’interface utilisateur.
1. [Guides d’extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/guides/) - Instructions détaillées sur la manière de développer votre propre extension
1. [Points d’extension de l’interface utilisateur de l’éditeur universel](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Documentation sur les points d’extension spécifiques à l’éditeur universel

>[!TIP]
>
>Si vous préférez apprendre par l’exemple, consultez le tutoriel sur l’extensibilité de l’interface utilisateur d’AEM [](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview). Bien qu’il se concentre sur l’extension de la console Fragments de contenu, les concepts d’implémentation d’une extension d’interface utilisateur dans l’éditeur universel sont les mêmes.

[En utilisant Extension Manager dans AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/), vous pouvez activer ou désactiver vos extensions par instance, accéder aux extensions propriétaires d’Adobe, y compris celles de l’éditeur universel, et bien plus encore.

## Points d’extension {#extension-points}

En plus de l’extensibilité de l’interface utilisateur, l’éditeur universel offre de nombreux autres points d’extension flexibles pour permettre une intégration transparente des exigences commerciales personnalisées.

* **[Blocs](/help/edge/developer/block-collection.md)** : au format JSON simple, les projets peuvent ajuster les blocs et les fonctionnalités UE disponibles pour la création de contenu.
* **[Interface utilisateur personnalisée](#extending-ui)** : les extensions peuvent afficher l’interface utilisateur nécessaire dans les panneaux latéraux ou les boîtes de dialogue modales.
* **[Événements](/help/implementing/universal-editor/events.md)** : les extensions reçoivent des événements sur les actions et les sélections de l’auteur sur la page pour répondre de manière appropriée.

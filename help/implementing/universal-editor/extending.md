---
title: Extension de l’éditeur universel
description: Découvrez les différentes options permettant d’étendre les fonctionnalités de l’éditeur universel afin de répondre aux besoins des auteurs ou des autrices de contenu.
feature: Developing
role: Admin, Developer
exl-id: 2f487fa5-57a7-477a-ad68-590e6cc12f4e
source-git-commit: d938abce2b46786343b19113454da1738a824ed0
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 100%

---

# Extension de l’éditeur universel {#extending}

Découvrez les différentes options permettant d’étendre les fonctionnalités de l’éditeur universel afin de répondre aux besoins des auteurs ou des autrices de contenu.

>[!TIP]
>
>L’éditeur universel propose également plusieurs [options de personnalisation](/help/implementing/universal-editor/customizing.md), permettant de mieux répondre aux besoins du projet.

## Extensions {#extensions}

En tant que service Adobe Experience Cloud, l’interface utilisateur de l’éditeur universel peut être étendue à l’aide de l’App Builder et d’Experience Manager. Adobe propose de nombreuses extensions prêtes à l’emploi disponibles via [Extension Manager](https://experience.adobe.com/aem/extension-manager) que vous pouvez utiliser pour votre projet.

* **[Extension de la gestion multi-sites AEM (MSM)](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)** : interrompez ou rétablissez l’héritage au niveau du composant.
* **[Extension des propriétés de page AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties)** : accédez à la fenêtre des propriétés de page de la page dans l’éditeur universel.
* **[Extension de l’administration de site AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#sites-console)** : ouvrez la console Sites à l’emplacement de la page dans l’éditeur universel.
* **[Extension de verrouillage de page AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#locking-pages)** : affichez et modifiez le statut de verrouillage de page à partir de l’éditeur universel.
* **[Extension des workflows AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#workflows)** : lancez des workflows sur la page et son contenu depuis l’éditeur universel.
* **[Générer des variations](/help/generative-ai/generate-variations-integrated-editor.md)** : utilisez l’intelligence artificielle (IA) générative pour créer des variations pour votre contenu directement dans le panneau des propriétés.
* **[Sélecteur de produit AEM pour l’éditeur universel](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/ue-product-picker/)** : intégrez les données Adobe Commerce en sélectionnant ou en supprimant les données de produit de l’éditeur.
* **[Brouillons de contenu de l’éditeur universel](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/universal-editor-content-drafts/)**: créez, modifiez et gérez plusieurs brouillons de contenu.
* **[Sélecteur de ressources configurable](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/)** : activez la sélection de ressources à partir de référentiels autres que celui utilisé par la page modifiée.
* **Éditeur de règles de formulaires** : ajoutez un comportement dynamique aux champs AEM Forms de manière visuelle, sans coder.
* **[Exporter des fragments de contenu vers Adobe Target](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/exporting-content-fragment-to-adobe-target/)** : exportez les fragments de contenu créés dans Adobe Experience Manager as a Cloud Service vers Adobe Target, afin de les utiliser comme offres dans les activités Target, pour tester et personnaliser les expériences à grande échelle.
* **[Workflows de fragments de contenu](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/content-fragments-workflows/)** : initiez un workflow AEM pour les fragments de contenu sélectionnés.

Pour plus d’informations sur l’activation de ces extensions, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## Extension de l’interface d’utilisation {#extending-ui}

Les extensions de l’interface utilisateur de l’éditeur universel sont des applications JavaScript créées avec Adobe App Builder. À l’aide de ces mêmes outils, vous pouvez également ajouter vos propres boutons et actions au menu d’en-tête et au panneau des propriétés, ainsi que créer vos propres événements pour l’éditeur universel.

Pour explorer les possibilités de création de vos propres extensions, consultez les ressources suivantes :

1. [Extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/) : il s’agit de la documentation destinée au développeur ou à la développeuse pour l’extension de l’interface utilisateur.
1. [Guides d’extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/guides/) : instructions détaillées sur la manière de développer votre propre extension
1. [Points d’extension de l’interface utilisateur de l’éditeur universel](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) : documentation sur les points d’extension spécifiques à l’éditeur universel

>[!TIP]
>
>Si vous préférez apprendre par l’exemple, consultez le tutoriel sur l’extensibilité de l’interface utilisateur d’AEM [](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview). Bien qu’il se concentre sur l’extension de la console Fragments de contenu, les concepts d’implémentation d’une extension d’interface utilisateur dans l’éditeur universel restent les mêmes.

[En utilisant Extension Manager dans AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/), vous pouvez activer ou désactiver vos extensions par instance, accéder aux extensions propriétaires d’Adobe, y compris celles de l’éditeur universel, et bien plus encore.

## Points d’extension {#extension-points}

En plus de l’extensibilité de l’interface utilisateur, l’éditeur universel offre de nombreux autres points d’extension flexibles pour permettre une intégration transparente des exigences commerciales personnalisées.

* **[Blocs](https://www.aem.live/developer/block-collection)** : au format JSON simple, les projets peuvent ajuster les blocs et les fonctionnalités d’interface utilisateur disponibles pour la création de contenu.
* **[Interface utilisateur personnalisée](#extending-ui)** : les extensions peuvent afficher l’interface utilisateur nécessaire dans les panneaux latéraux ou les boîtes de dialogue modales.
* **[Événements](/help/implementing/universal-editor/events.md)** : les extensions reçoivent des événements sur les actions et les sélections réalisées dans l’environnement auteur sur la page afin d’y répondre de manière appropriée.

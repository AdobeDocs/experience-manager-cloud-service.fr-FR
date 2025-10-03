---
title: Aperçu des fragments de contenu
description: Découvrez comment prévisualiser vos fragments de contenu grâce à diverses méthodes.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
source-git-commit: 42dbf6138920c4f733d7dc74dfc81504dee1e0ae
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 2%

---

# Aperçu des fragments de contenu {#previewing-content-fragments}

Les fragments de contenu peuvent être utilisés pour une diffusion découplée et la création de pages. Comme les fragments sont uniquement du contenu, sans formatage, leur révision peut s’avérer plus difficile. Ainsi, plusieurs méthodes de prévisualisation de vos fragments sont fournies, dans divers scénarios.

Plusieurs méthodes sont disponibles pour les fragments de contenu, accessibles à partir de la console Fragments de console et de l’éditeur. La console et l’éditeur décrits dans cette section ont été développés pour la diffusion de contenu en mode découplé (bien qu’ils puissent être utilisés dans tous les scénarios).

Vous pouvez prévisualiser votre fragment :

* en utilisant le modèle d’URL [Aperçu](#preview-url-pattern)

* en publiant sur l’instance [Preview](#preview-instance) et en dépubliant à partir de celle-ci ;

<!--
* with a HTML template, using **[Preview]()** from the Content Fragments console
-->

>[!IMPORTANT]
>
>Les fragments de contenu sont accessibles à partir de deux consoles : **Fragments de contenu** et **Assets**.
>
>Il existe également deux éditeurs pour créer des fragments de contenu ; bien que la fonctionnalité de base soit la même, il existe quelques différences. Les deux éditeurs sont accessibles à partir des deux consoles.
>
>Cette section traite de la console **Fragments de contenu** et du *nouvel* éditeur de fragment de contenu. Ils ont été développés pour la diffusion de contenu découplé (bien qu’ils puissent être utilisés dans tous les scénarios).
>
>Pour plus d’informations, consultez ce qui suit :
>
>* utilisation de la console **Assets** pour [gérer les fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md)
>* l’utilisation de l’éditeur de fragment de contenu [*original*](/help/assets/content-fragments/content-fragments-variations.md),
>* à l’aide de [Fragments de contenu pour la création de pages](/help/sites-cloud/authoring/fragments/content-fragments.md).

## Modèle d’URL de prévisualisation {#preview-url-pattern}

L’éditeur de fragment de contenu permet aux auteurs de prévisualiser leurs modifications dans une application frontale externe.

Pour utiliser cette fonctionnalité, vous devez d’abord :

* Contactez votre équipe informatique pour configurer l’application frontale externe qui effectue le rendu du fragment de contenu en utilisant sa sortie JSON.

* Lorsque l’application frontale externe est configurée, le **Modèle d’URL d’aperçu par défaut** doit être défini en tant que propriété [&#x200B; du modèle de fragment de contenu approprié](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#model-properties).

L’URL de prévisualisation doit suivre le modèle suivant :

    `https://<preview_url>?param=${expression}`

Les expressions disponibles sont les suivantes :

* `${contentFragment.path}`
* `${contentFragment.model.path}`
* `${contentFragment.model.name}`
* `${contentFragment.variation}`
* `${contentFragment.id}`

Une fois l’URL définie, le bouton **[Aperçu](/help/sites-cloud/administering/content-fragments/authoring.md#preview-content-fragment)** est actif dans la barre d’outils supérieure de l’éditeur. Vous pouvez sélectionner ce bouton pour lancer l’application externe (dans un onglet distinct) afin d’effectuer le rendu du fragment de contenu.

## Preview Instance {#preview-instance}

Vous pouvez **Publier** et **Dépublier** votre fragment vers votre instance d’aperçu (ainsi que vers votre instance de publication).

Vous pouvez publier le fragment à partir de l’éditeur ou de la console.

Voir :

* [&#x200B; Publication et prévisualisation d’un fragment &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) pour plus d’informations.

* [Dépublication d’un fragment](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) pour plus d’informations.

<!--
## Preview based on a HTML Template {#preview-based-on-a-html-template}

The Content Fragment console provides a **Preview** option for every fragment.

The icon can be selected to open a dialog that represents the fragment based on a HTML template. You can use the default template, or develop and load your own.
-->

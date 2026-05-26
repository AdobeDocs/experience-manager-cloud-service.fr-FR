---
title: Aperçu des fragments de contenu
description: Découvrez comment prévisualiser vos fragments de contenu grâce à diverses méthodes.
feature: Content Fragments
role: User, Developer
solution: Experience Manager Sites
badgeSaas: label="AEM Sites" type="Positive" tooltip="S’applique à AEM Sites)."
exl-id: 40c02806-76a2-43ed-982c-0410c2125a36
source-git-commit: 5413e173ac159015f224845e238779c5dc997ee5
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---

# Aperçu des fragments de contenu {#previewing-content-fragments}

Les fragments de contenu peuvent être utilisés pour une diffusion découplée et la création de pages. Comme les fragments sont uniquement du contenu, sans formatage, leur révision peut s’avérer plus difficile. Ainsi, plusieurs méthodes de prévisualisation de vos fragments sont fournies, dans divers scénarios.

Plusieurs méthodes sont disponibles pour les fragments de contenu, accessibles à partir de la console Fragments de console et de l’éditeur. La console et l’éditeur décrits dans cette section ont été développés pour la diffusion de contenu en mode découplé (bien qu’ils puissent être utilisés dans tous les scénarios).

Vous pouvez prévisualiser votre fragment :

* en publiant sur l’instance [Preview](#preview-instance) et en dépubliant à partir de celle-ci ;

* dans une [application externe](#preview-url-pattern), en utilisant le modèle d’URL [Aperçu](#preview-url-pattern)

* avec un modèle [visualisation (HTML)](#preview-with-visualization-html-templates)

Bien sûr, vous pouvez également afficher votre fragment dans l’[éditeur de fragment de contenu](/help/sites-cloud/administering/content-fragments/authoring.md).

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
>* utilisation de la console **&#x200B;**&#x200B;pour [gérer les fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md)
>* l’utilisation de l’éditeur de fragment de contenu [*original*](/help/assets/content-fragments/content-fragments-variations.md),
>* à l’aide de [Fragments de contenu pour la création de pages](/help/sites-cloud/authoring/fragments/content-fragments.md).

## Preview Instance {#preview-instance}

Vous pouvez **Publier** et **Dépublier** votre fragment sur votre **[Service d’aperçu](/help/headless/deployment/architecture.md)** (ainsi que sur votre instance de publication).

Vous pouvez publier le fragment à partir de l’éditeur ou de la console.

Voir :

* [&#x200B; Publication et prévisualisation d’un fragment &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) pour plus d’informations.

* [Dépublication d’un fragment](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) pour plus d’informations.

## Aperçu dans une application externe {#preview-in-an-external-application}

L’éditeur de fragment de contenu permet aux auteurs de prévisualiser leurs modifications dans une application frontale externe.

### Modèle d’URL de prévisualisation {#preview-url-pattern}

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

### Aperçu dans l’application externe {#preview-in-the-external-application}

Vous pouvez prévisualiser un fragment de contenu dans une application externe :

>[!NOTE]
>
>Le [modèle d’URL de prévisualisation](#preview-url-pattern) doit être configuré pour cette option.

1. Dans la console Fragment de contenu , naviguez jusqu’à l’emplacement de votre fragment.
1. Ouvrez votre fragment dans l’éditeur
1. Sélectionnez **Aperçu** dans la barre d’outils supérieure.
1. Sélectionnez **Application** pour ouvrir le fragment dans l’application externe, par exemple, l’[éditeur universel](/help/implementing/universal-editor/introduction.md).

## Modèles d’aperçu avec visualisation (HTML) {#preview-with-visualization-html-templates}

<!-- CQDOC-23232 - remove when GA -->

>[!NOTE]
>
>Les fragments de contenu visuel sont actuellement en disponibilité limitée.
>
>Si vous souhaitez participer, veuillez envoyer une demande à partir de votre adresse e-mail officielle à [&#128279;](mailto:experience-production-agent@adobe.com).

AEM vous permet de prévisualiser votre fragment de contenu à l’aide d’une disposition visuelle basée sur un modèle HTML.

Voir [Fragments de contenu visuels](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md) pour plus d’informations sur la manière de [prévisualiser votre fragment avec des modèles](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md#preview-your-template-with-a-template).

>[!NOTE]
>
>Consultez [Fragments de contenu visuels - Modèles](/help/implementing/developing/extending/content-fragments-visualization-templates.md) pour plus d’informations sur la création, la personnalisation et le chargement de vos propres modèles HTML.


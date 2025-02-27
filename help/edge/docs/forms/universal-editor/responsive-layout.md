---
title: Présentation de l’éditeur universel - Mode réactif
description: Cet article explique comment prévisualiser des formulaires à l’aide de différents émulateurs dans l’éditeur universel pour visualiser leur aspect lors de la création.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 8f5b4d863ab469c44b4c221eab1fb128706b45c7
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 2%

---

# Mode réactif dans la création WYSIWYG

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> avec le nom de votre organisation GitHub et le nom du référentiel. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>


L’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) vous permet de prévisualiser Edge Delivery Services Forms avec différents émulateurs pour voir l’aspect du formulaire lors de la création.

Le mode réactif permet aux développeurs de concevoir des mises en page qui s’adaptent automatiquement à différentes tailles d’écran, notamment aux ordinateurs de bureau, aux tablettes et aux appareils mobiles. L’éditeur universel prend en charge les émulateurs pour les ordinateurs de bureau, les tablettes et les appareils mobiles. Vous pouvez définir la hauteur et la largeur en fonction de la taille de votre écran et effectuer les actions suivantes :

* Définir l’orientation
* Spécifier la largeur et la hauteur
* Modifier l’orientation

## Aperçu de Forms en mode réactif pour différents appareils

L’éditeur universel propose une icône **Émulateur** située dans le coin supérieur droit de l’écran. Elle vous permet de prévisualiser des pages sur différents formats d’appareil et de tester le comportement de votre conception responsive pour une meilleure expérience utilisateur.

Pour voir comment l’éditeur universel effectue le rendu des formulaires sur différentes tailles d’écran, procédez comme suit :

1. Ouvrez le formulaire dans l’éditeur universel pour le modifier.
1. Sélectionnez l’icône ![Émulateur](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%} disponible dans la barre d’outils de l’éditeur universel, puis cliquez sur l’icône de l’émulateur pour afficher l’option.

   ![Mode réactif](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

1. Sélectionnez une option pour émuler un formulaire dans l’éditeur universel sur un appareil sélectionné : Bureau, Tablette, Mobile.

   ![Mode réactif](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png){width=40%,height=40%}

   Par défaut, l’éditeur s’ouvre dans une disposition de bureau, la hauteur et la largeur étant automatiquement déterminées par le navigateur. Vous pouvez également émuler un formulaire sur un appareil mobile ou tablette. Vous pouvez également personnaliser la largeur et la hauteur de l’écran pour les appareils personnalisés.

L’éditeur universel fournit différents émulateurs pour prévisualiser les formulaires sur différents appareils. Le tableau ci-dessous répertorie les types d’émulateurs disponibles, ainsi que les représentations d’appareils correspondantes :

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">Type d’émulateur</th>
        <th style="width: 80%">Image de l’appareil</th>
    </tr>
    <tr>
        <td style="width: 20%">Poste de travail</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="Émulateur de bureau" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Tablette</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="Émulateur de tablette" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Mobile</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="Émulateur mobile" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Appareil Personnalisé</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="Émulateur d’appareil personnalisé" style="width: auto; height: auto"></td>
    </tr>
</table>

Vous pouvez utiliser l’icône **Rotateur d’écran** pour basculer entre les orientations portrait et paysage lors de la prévisualisation d’un formulaire sur différents appareils. Il permet aux développeurs de tester la manière dont le responsive design s’adapte aux rotations d’écran sur différents appareils.

L’éditeur universel prend en charge les différentes dispositions de formulaire. Pour découvrir les différentes mises en page, reportez-vous à la section [Fonctionnalités de mise en page](#layout-capabilities).

## Fonctionnalités de disposition

L’éditeur universel vous permet de créer des formulaires simples d’utilisation qui offrent des expériences dynamiques aux utilisateurs finaux. La disposition du formulaire contrôle l’affichage des éléments ou des composants dans un formulaire.

L’éditeur universel prend en charge les types de disposition suivants pour les formulaires :
* [Disposition de panneau](#panel-layout)
* [Disposition Assistant](#wizard-layout)
* [Disposition en accordéon](#accordion-layout)

### Disposition de panneau

La disposition des panneaux est utile pour organiser les champs associés de manière à faciliter la navigation et la recherche du contenu correspondant. La disposition des panneaux organise les composants de formulaire en sections ou panneaux distincts dans les formulaires.

![Disposition de panneau](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

Vous pouvez utiliser le [composant de panneau](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) pour ajouter la disposition du panneau dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Panneau, reportez-vous à l’article [composant Panneau](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).

### Disposition Assistant


La disposition « Assistant » permet de simplifier un formulaire complexe en le divisant en étapes distinctes. Chaque étape représente une partie différente du processus et les utilisateurs et utilisatrices naviguent de manière séquentielle parmi les étapes, souvent avec les boutons **Suivant** et **Précédent**. Vous pouvez utiliser la disposition Assistant pour créer un formulaire qui implique plusieurs sections ou étapes.

![Disposition Assistant](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

Vous pouvez utiliser le [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) pour ajouter la disposition Assistant dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Assistant, reportez-vous à l’article [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).

### Disposition Accordéon

La disposition en accordéon affiche le contenu dans des sections ou des panneaux réductibles d’un formulaire adaptatif. Lorsqu’une section est développée, elle affiche le contenu dans , tandis que les autres sections restent réduites. Cette disposition est idéale pour afficher de grandes quantités d’informations sous une forme compacte.

![Disposition Accordéon](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

Vous pouvez utiliser le [composant d’accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) pour ajouter la disposition en accordéon dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Accordéon, reportez-vous à l’article [Composant Accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) .

### Comment choisir la bonne mise en page ?

Il est important de sélectionner la disposition appropriée pour optimiser l’expérience utilisateur et les fonctionnalités de formulaire. Le tableau ci-dessous vous aide à comprendre les différentes options de mise en page disponibles et vous guide dans le choix de la mise en page la plus adaptée en fonction de vos besoins et cas d’utilisation spécifiques :

| Fonctionnalité | Disposition de panneau | Disposition Assistant | Disposition Accordéon |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Objectif** | Regroupe les contenus associés dans des sections distinctes | Guide les utilisateurs et utilisatrices à travers un processus ou un formulaire à plusieurs étapes | Organise le contenu en sections réductibles |
| **Structure** | Sections distinctes | Étapes/pages séquentielles | Panneaux/sections réductibles |
| **Navigation** | Cliquez sur les en-têtes du panneau pour naviguer | - En avant : bouton « Suivant » <br>- En arrière : bouton « Précédent » <br>- Étapes facultatives à ignorer | Cliquez sur les en-têtes pour développer/réduire les sections. |
| **Expérience utilisateur** | Organise de grandes quantités de contenu de manière gérable. | Conseils détaillés pour réduire la surcharge | Mode compact avec sections développées/réduites |
| **Cas d’utilisation** | Formulaires complexes avec sections classées | Processus de configuration, formulaires complexes | Questions fréquentes, menus de paramètres, sections de contenu détaillées |

## Voir également

{{universal-editor-see-also}}

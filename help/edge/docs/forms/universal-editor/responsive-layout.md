---
title: Présentation de l’éditeur universel - Mode réactif
description: Cet article explique comment prévisualiser des formulaires à l’aide de différents émulateurs dans l’éditeur universel pour visualiser leur aspect lors de la création.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: ht
source-wordcount: '1248'
ht-degree: 100%

---


# Mode réactif dans la création WYSIWYG

<span class="preview"> Il s’agit d’une fonctionnalité de version préliminaire accessible par le biais de notre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features">canal de version préliminaire</a>. </span>

## Présentation des formulaires réactifs

Dans le monde multi-appareils d’aujourd’hui, vos formulaires doivent être attrayants et fonctionner correctement sur des écrans de toutes tailles, qu’il s&#39;agisse d’écrans d’ordinateurs de bureau ou de smartphones. Le mode réactif dans l’éditeur universel vous permet d’y parvenir en vous permettant de prévisualiser et de tester vos formulaires sur différentes tailles d’appareil au cours du processus de création.

L’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) vous permet de créer des formulaires qui s’adaptent automatiquement à différentes tailles d’écran, offrant ainsi une expérience client optimale, quel que soit l’appareil utilisé.

## Prévisualiser les formulaires en mode réactif pour différents appareils

L’éditeur universel propose une icône **Émulateur** située en haut à droite de l’écran. Elle vous permet de prévisualiser des pages sur différents formats d’appareils et de tester le comportement de votre conception réactive pour une meilleure expérience d’utilisation.

Pour prévisualiser un formulaire en mode réactif, procédez comme suit :

1. Ouvrez le formulaire dans l’éditeur universel pour le modifier.
2. Cliquez sur l’icône ![Icône d’émulateur affichant un symbole de prévisualisation d’appareil](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%} dans la barre d’outils.
3. Sélectionnez un format d’appareil :
   - Bureau (par défaut)
   - Tablette
   - Mobile
   - Personnalisé (spécifier la largeur et la hauteur)

![Copie d’écran de l’éditeur universel affichant les options de mode réactif pour différents appareils](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

Vous pouvez utiliser l’icône **Rotateur d’écran** pour basculer entre les orientations portrait et paysage lors de la prévisualisation sur une tablette ou des appareils mobiles.

L’éditeur universel fournit différents émulateurs pour prévisualiser les formulaires sur différents appareils. Le tableau ci-dessous répertorie les types d’émulateurs disponibles, ainsi que les représentations d’appareils correspondantes :

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">Type d’émulateur</th>
        <th style="width: 80%">Image de l’appareil</th>
    </tr>
    <tr>
        <td style="width: 20%">Ordinateur de bureau</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="Vue de bureau d’un formulaire avec disposition pleine largeur" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Tablette</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="Vue de tablette d’un formulaire présentant une disposition de largeur moyenne avec des composants ajustés" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Mobile</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="Vue mobile d’un formulaire présentant une disposition étroite avec des composants empilés" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Appareil personnalisé</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="Vue personnalisée d’appareil d’un formulaire avec dimensions spécifiées par l’utilisateur ou l’utilisatrice" style="width: auto; height: auto"></td>
    </tr>
</table>

## Fonctionnalités de disposition

L’éditeur universel vous permet de créer des formulaires simples d’utilisation qui offrent des expériences dynamiques. La disposition des formulaires détermine le mode d’affichage des éléments et des composants dans un formulaire.

L’éditeur universel prend en charge les types de disposition suivantes pour les formulaires :

- [Disposition de panneau](#panel-layout)
- [Disposition de l’Assistant](#wizard-layout)
- [Disposition en accordéon](#accordion-layout)

### Disposition de panneau

La disposition de panneau est utile pour organiser les champs associés de manière à faciliter la navigation et la recherche du contenu correspondant. La disposition de panneau organise les composants de formulaire en sections ou panneaux distincts dans les formulaires.

![Disposition de panneau présentant plusieurs sections distinctes dans un formulaire](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Exemple :** un formulaire de candidature à un emploi peut utiliser des panneaux pour séparer les éléments « Informations personnelles », « Études », « Expérience professionnelle » et « Références » en sections distinctes.

**Comportement réactif :** sur les écrans plus petits, les panneaux s’empilent généralement verticalement, en conservant leurs regroupements distincts tout en s’ajustant à la largeur plus étroite.

Vous pouvez utiliser le [composant Panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) pour ajouter la disposition de panneau dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Panneau, reportez-vous à l’article [composant Panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).

### Disposition de l’Assistant

La disposition de l’assistant permet de simplifier un formulaire complexe en le divisant en étapes distinctes. Chaque étape représente une partie différente du processus et les utilisateurs et utilisatrices naviguent de manière séquentielle parmi les étapes, souvent avec les boutons **Suivant** et **Précédent**. Vous pouvez utiliser la disposition de l’Assistant pour créer un formulaire qui implique plusieurs sections ou étapes.

![Disposition de l’assistant présentant un formulaire à plusieurs étapes avec commandes de navigation](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Exemple :** un formulaire de déclaration de sinistre peut utiliser un assistant pour guider les utilisateurs et utilisatrices à travers la fourniture de détails sur l’incident, le chargement de pièces, la saisie d’informations personnelles et la révision de l’envoi.

**Comportement réactif :** sur les appareils mobiles, l’assistant conserve son approche étape par étape, mais ajuste le contenu de chaque étape pour l’adapter à l’écran plus étroit, en empilant souvent des éléments qui apparaîtraient côte à côte sur des écrans plus grands.

Vous pouvez utiliser le [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) pour ajouter la disposition de l’Assistant dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Assistant, reportez-vous à l’article [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).

### Disposition en accordéon

La disposition en accordéon affiche le contenu dans des sections ou des panneaux réductibles d’un formulaire adaptatif. Lorsqu’une section est développée, elle y affiche le contenu tandis que les autres sections restent réduites. Cette disposition est idéale pour afficher de grandes quantités d’informations sous une forme compacte.

![Disposition en accordéon présentant des sections extensibles dans un formulaire](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Exemple :** un formulaire de configuration de produit peut utiliser des sections en accordéon pour les éléments « Options de base », « Fonctionnalités avancée », « Accessoire » et « Plans de paiement », ce qui permet aux utilisateurs et aux utilisatrices de se concentrer sur un aspect à la fois.

**Comportement réactif :** les accordéons fonctionnent particulièrement bien sur les appareils mobiles, car ils conservent naturellement l’espace vertical en n’affichant que la section de contenu développée, ce qui les rend idéaux pour les écrans plus petits.

Vous pouvez utiliser le [composant Accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) pour ajouter la disposition en accordéon dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Accordéon, reportez-vous à l’article [Composant Accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion).

### Comment choisir la bonne disposition ?

Il est important de sélectionner la disposition appropriée pour optimiser l’expérience clientèle et les fonctionnalités de formulaire. Le tableau ci-dessous vous aide à comprendre les différentes options de disposition disponibles et vous guide dans le choix de la plus adaptée en fonction de vos besoins et cas d’utilisation spécifiques :

| Fonctionnalité | Disposition de panneau | Disposition de l’Assistant | Disposition en accordéon |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Objectif** | Regroupe les contenus associés dans des sections distinctes. | Guide les utilisateurs et utilisatrices à travers un processus ou un formulaire à plusieurs étapes. | Organise le contenu en sections réductibles. |
| **Structure** | Sections distinctes | Étapes/pages séquentielles | Panneaux/sections réductibles |
| **Navigation** | Cliquez sur les en-têtes du panneau pour naviguer. | - Avancer : bouton « Suivant »<br>- Revenir en arrière : bouton « Précédent »<br>- Étapes facultatives à ignorer | Cliquez sur les en-têtes pour développer/réduire les sections. |
| **Expérience clientèle** | Organise de grandes quantités de contenu faciles à gérer. | Conseils détaillés pour réduire la surcharge | Vue compacte avec sections développées/réduites |
| **Cas d’utilisation** | Formulaires complexes avec sections classées | Processus de configuration, formulaires complexes | Questions fréquentes, menus de paramètres, sections de contenu détaillées |
| **Idéal pour mobile** | Modéré : les panneaux s’empilent verticalement. | Correct : se concentre uniquement sur l’étape actuelle. | Excellent : conserve l’espace grâce à des sections réductibles. |

## Bonnes pratiques relatives aux formulaires réactifs

Pour vous assurer que vos formulaires fournissent une expérience optimale sur tous les appareils, suivez ces bonnes pratiques :

1. **Concevoir d’abord pour les appareils mobiles :** commencez par concevoir votre formulaire pour les appareils mobiles, puis améliorez-le pour les écrans plus grands. Cette approche garantit que la fonctionnalité principale fonctionne sur les écrans les plus petits.

2. **Utiliser des types de champs appropriés :** choisissez des types de champs qui fonctionnent bien sur les appareils tactiles :
   - Utiliser des listes déroulantes au lieu des boutons radio en cas d’options nombreuses
   - Utiliser des sélecteurs de date conçus pour la saisie tactile
   - Assurer une taille minimale de 44 px x 44 px pour les boutons et les cibles tactiles

3. **Simplifier pour les plus petits écrans :**
   - Afficher moins de champs par ligne sur les appareils mobiles
   - Envisager de masquer les champs facultatifs derrière une option « Afficher plus »
   - Diviser les formulaires complexes en plusieurs étapes sur les appareils mobiles

4. **Effectuer des tests minutieux :** testez toujours vos formulaires sur des appareils réels ou à l’aide du mode émulateur dans l’éditeur universel pour vous assurer qu’ils fonctionnent correctement sur toutes les tailles d’écran.

5. **Tenir compte des temps de chargement :** optimisez la taille des images et réduisez les ressources requises, en particulier pour les utilisateurs et utilisatrices mobiles dont les connexions peuvent être plus lentes.

## Résolution des problèmes liés aux formulaires réactifs

| Problème | Cause possible | Solution |
|-------|---------------|----------|
| Le formulaire semble tronqué sur les appareils mobiles. | Correction des paramètres de largeur ou des problèmes de débordement | Utilisez des unités relatives (%, rem) au lieu des pixels et recherchez les propriétés overflow:hidden. |
| Difficultés pour interagir avec des éléments tactiles | Cibles tactiles trop petites ou trop proches les unes des autres | Augmentez la taille du bouton/de l’entrée à au moins 44 px x 44 px et ajoutez plus d’espace entre les éléments interactifs. |
| Débordements de contenu sur les petits écrans | Aucune règle réactive pour les fenêtres d’affichage plus petites | Ajoutez des requêtes de média ou des classes réactives pour ajuster la disposition selon différentes tailles d’écran. |
| Formulaire trop lent sur les appareils mobiles | Images volumineuses ou scripts excessifs | Optimisez les images, réduisez le code JavaScript et envisagez un chargement différé pour les éléments non critiques. |
| Différence d’aspect entre l’émulateur et les appareils réels | Rendu spécifique au navigateur ou variations d’appareil | Testez sur des appareils réels lorsque cela est possible, et pas seulement sur des émulateurs. |

## Voir également

{#see-more-eds-forms}

---
title: Incorporer un thème Forms adaptatif dans un thème AEM Sites
description: Découvrez comment intégrer un thème Forms adaptatif (par exemple, Zone de travail) dans un thème AEM Sites afin que les pages Sites et le Forms adaptatif incorporé partagent un thème et un déploiement unifiés.
keywords: thème de formulaires adaptatifs, thème de site, thème AEM Sites, intégration du thème forms, pipeline front-end, incorporation du thème
feature: Adaptive Forms, Core Components
role: Developer
exl-id: a1f8c4d2-3e5b-4a2f-9b7e-2d4f6a8c1b0e
source-git-commit: 2aa13887949507ab74c45b4b6f3135aebd59c6ea
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# Incorporer un thème Forms adaptatif dans un thème AEM Sites

Vous pouvez incorporer un thème Forms adaptatif (tel que le thème [Zone de travail AEM Forms](https://github.com/adobe/aem-forms-theme-canvas)) dans votre thème AEM Sites. Ainsi, un seul thème oriente à la fois les pages de votre site et tout Forms adaptatif incorporé dans ces pages, avec une version et un déploiement via le pipeline front-end [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=fr).

Cet article est destiné aux développeurs qui gèrent ou personnalisent le thème AEM Sites standard (ou personnalisé) et qui souhaitent inclure le style de formulaire adaptatif sans gérer de déploiement de thème Forms distinct.

## Prérequis {#prerequisites}

Avant de commencer, vérifiez que vous disposez des éléments suivants :

* **AEM as a Cloud Service** avec le [pipeline front-end](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=fr) configuré pour le thème de votre site.
* **Sources de thème du site** par exemple, le [thème standard du modèle de site](https://github.com/adobe/aem-site-template-standard) (le référentiel qui contient des `theme/` avec `src/theme.scss`, `src/components/`, etc.).
* **Sources de thème Forms** - le [thème de la zone de travail AEM Forms](https://github.com/adobe/aem-forms-theme-canvas) (ou un autre thème de Forms adaptatif compatible) cloné ou téléchargé localement.
* **Node.js et npm** - pour créer le thème du site (consultez la section « LISEZ-MOI le thème » pour les versions prises en charge).
* **Maven** - si vous créez le package de modèle de site complet (facultatif pour le travail sur le thème uniquement).

## Étape 1 : créer le dossier de composants de formulaire adaptatif {#step-1-create-folder}

Dans le référentiel de thèmes de votre site, créez le dossier dans lequel le thème Forms sera stocké :

```text
theme/src/components/adaptiveform/
```

Toutes les ressources de thème Forms se trouvent sous ce dossier afin de rester distinctes des composants de site existants.

## Étape 2 : copie des composants de thème Forms et des images {#step-2-copy-components-and-images}

En utilisant votre thème **Forms** (par exemple, `aem-forms-theme-canvas`) et votre **thème du site** chemins d’accès :

1. **Copier des dossiers de composants**\
   À partir du thème Forms, copiez l’intégralité du contenu de `src/components/` dans le thème du site en tant que :

   ```text
   theme/src/components/adaptiveform/
   ```

   Vous obtenez ainsi des chemins d’accès du type :

   ```text
   theme/src/components/adaptiveform/button/
   theme/src/components/adaptiveform/checkbox/
   theme/src/components/adaptiveform/container/
   … (one folder per component)
   ```

2. **Copier les images**\
   Copiez les images du thème Forms dans le thème du site :

   ```text
   Forms theme:  src/resources/images/*
   Site theme:   theme/src/components/adaptiveform/resources/images/
   ```

   Créez des `theme/src/components/adaptiveform/resources/images/` s’ils n’existent pas, puis copiez toutes les ressources d’image (par exemple, `question.svg`, `Chevron-Left.svg`, `busy-state.gif`, etc.).

## Étape 3 : copie de variables et de mixins {#step-3-copy-variables-and-mixins}

Le thème Forms utilise des variables partagées et des mixins sous `src/site/`. Copiez uniquement ces deux fichiers dans la **racine** du `adaptiveform/` (et non dans un sous-dossier `site`) :

| Source (thème Forms) | Destination (thème du site) |
|---------------------------|---------------------------------------------------|
| `src/site/_variables.scss` | `theme/src/components/adaptiveform/_variables.scss` |
| `src/site/_mixin.scss` | `theme/src/components/adaptiveform/_mixin.scss` |

Ne copiez **pas** le reste du dossier `src/site/` du thème Forms ; seuls ces deux fichiers sont nécessaires pour les styles de formulaires incorporés.

## Étape 4 : correction des chemins d’accès aux images dans SCSS {#step-4-fix-image-paths}

Dans le thème Forms, les fichiers SCSS de composant référencent souvent des images avec des chemins d’accès tels que `./resources/` ou `url(resources/`. Une fois déplacés dans `theme/src/components/adaptiveform/<component>/`, ces chemins doivent pointer d’un niveau vers `adaptiveform/resources/`.

**Rechercher et remplacer** dans chaque `.scss` sous `theme/src/components/adaptiveform/` :

| Rechercher | Remplacer par |
|------|------------------|
| `./resources/` | `../resources/` |
| `url(resources/` | `url(../resources/` |
| `url('resources/` | `url('../resources/` |

**Exemple** - avant (thème Forms) :

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(./resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

**Après** (thème du site) :

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(../resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

Après le remplacement, ceux-ci deviennent respectivement `url(../resources/images/...)` et `url('../resources/images/...')`. Répétez l’opération pour chaque fichier SCSS sous `adaptiveform/` qui référence des images (bouton, accordéon, assistant, conteneur, saisie tactile, etc.).

## Étape 5 : créer le SCSS de point d’entrée du formulaire adaptatif {#step-5-create-adaptiveform-scss}

Créez des **`theme/src/components/adaptiveform/_adaptiveform.scss`** dans le thème du site. Ce fichier doit :

1. Importez les variables et mixins partagés.
2. Importez le fichier SCSS principal de chaque composant de formulaire adaptatif.

Utilisez les éléments suivants comme point d’entrée complet (correspond à l’intégration standard avec tous les composants de formulaire basés sur les composants principaux) :

```scss
//== Adaptive Form components (forms theme integration)
// Variables and mixins for adaptive form components
@import 'variables';
@import 'mixin';

//== Core adaptive form components
@import './button/_button.scss';
@import './checkboxgroup/_checkboxgroup.scss';
@import './container/_container.scss';
@import './datepicker/_datepicker.scss';
@import './dropdown/_dropdown.scss';
@import './fileinput/_fileinput.scss';
@import './footer/_footer.scss';
@import './image/_image.scss';
@import './numberinput/_numberinput.scss';
@import './panelcontainer/_panelcontainer.scss';
@import './radiobutton/_radiobutton.scss';
@import './text/_text.scss';
@import './textinput/_textinput.scss';
@import './accordion/_accordion.scss';
@import './tabsontop/_tabsontop.scss';
@import './pageheader/_pageheader.scss';
@import './wizard/_wizard.scss';
@import './title/_title.scss';
@import './telephoneinput/_telephoneinput.scss';
@import './emailinput/_emailinput.scss';
@import './recaptcha/_recaptcha.scss';
@import './verticaltabs/_verticaltabs.scss';
@import './checkbox/_checkbox.scss';
@import './termsandconditions/_termsandconditions.scss';
@import './switch/_switch.scss';
@import './hcaptcha/_hcaptcha.scss';
@import './turnstile/_turnstile.scss';
@import './review/_review.scss';
@import './scribble/_scribble.scss';
@import './datetime/_datetime.scss';
```

Si votre thème Forms omet certains composants (par exemple, aucune saisie tactile ou captcha), supprimez ou commentez les lignes de `@import` correspondantes pour éviter les erreurs de création. La liste ci-dessus correspond à la structure [Thème de la zone de travail](https://github.com/adobe/aem-forms-theme-canvas).

## Étape 6 : importer le thème du formulaire adaptatif dans le thème du site {#step-6-import-in-theme-scss}

Dans **`theme/src/theme.scss`**, ajoutez une seule importation à la **fin** du fichier (après les autres importations de composants) :

```scss
//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

**Exemple** - fin de `theme.scss` :

```scss
// ... existing site component imports ...
@import './components/embed/_embed.scss';
@import './components/pdfviewer/_pdfviewer.scss';
@import './components/socialmediasharing/_social_media_sharing.scss';

//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

Il s’agit de la seule modification requise dans la structure de thème de site existante ; tout le code spécifique au formulaire reste sous `src/components/adaptiveform/`.

## Étape 7 : créer et déployer {#step-7-build-and-deploy}

1. Créez le thème du site à partir de la racine du thème :

   ```bash
   cd theme
   npm install
   npm run build
   ```

2. Effectuez le déploiement via votre [pipeline front-end](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=fr) existant. Après le déploiement, le même thème CSS s’applique aux pages du site et au Forms adaptatif incorporé.

## Résolution des problèmes {#troubleshooting}

| Problème | Éléments à vérifier |
|-------|-------------------------------|
| Échec de la création : « fichier introuvable » pour une image | Placez toutes les images de formulaire dans `theme/src/components/adaptiveform/resources/images/`. Dans chaque `.scss` sous `adaptiveform/`, utilisez `../resources/` (et `url(../resources/`) pour les chemins d’accès aux images, et non `./resources/`. Si votre lot résout les chemins d’accès depuis `theme/src/`, placez les images dans `theme/src/resources/images/` et utilisez `resources/images/` (pas de `../`) dans SCSS. |
| Échec de la création : « fichier introuvable » pour `_variables.scss` ou `_mixin.scss` | Copiez les deux fichiers du `src/site/` de thème Forms dans `theme/src/components/adaptiveform/` (racine du formulaire adaptatif), et non dans un sous-dossier `site`. |
| Échec de la création : « fichier introuvable » pour un composant (par exemple, `_scribble.scss`) | Votre thème Forms peut ne pas inclure ce composant. Dans `theme/src/components/adaptiveform/_adaptiveform.scss`, supprimez ou mettez en commentaire la ligne de `@import` de ce composant. |
| Le formulaire s’affiche, mais ne comporte aucun style. | Vérifiez que la page utilise la bibliothèque cliente qui inclut le thème créé CSS et que `theme.scss` contient la ligne de `@import './components/adaptiveform/_adaptiveform.scss';` et que le thème a été recréé et déployé. |
| Conflits de styles entre les composants de site et de formulaire | Les classes de composants de formulaire comportent des espaces de noms (par exemple, `cmp-adaptiveform-button`). Si vous constatez des conflits, vérifiez si le CSS du site personnalisé remplace ces classes et ajuste la spécificité ou l’ordre. |

## Voir également {#see-also}

* [Utilisation des thèmes pour appliquer un style au Forms adaptatif basé sur les composants principaux](/help/forms/using-themes-in-core-components.md)
* [Développement avec des pipelines front-end](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=fr)
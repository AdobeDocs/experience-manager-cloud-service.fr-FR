---
title: Prise en main de la traduction AEM Sites
description: Découvrez comment organiser votre contenu AEM Sites et comment AEM outils de traduction fonctionnent.
index: true
hide: false
hidefromtoc: false
source-git-commit: 8c04ffde2cbafcb6d556de8d48fc19f5b130a2c1
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 1%

---


# Prise en main de la traduction AEM Sites {#getting-started}

Découvrez comment organiser votre contenu AEM Sites et comment AEM outils de traduction fonctionnent.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours de traduction AEM Sites, [Découvrez le contenu d’AEM Sites et comment traduire en AEM](learn-about.md) vous avez appris la théorie de base d’AEM Sites et vous devriez maintenant :

* Découvrez les concepts de base de la création de contenu AEM Sites.
* Familiarisez-vous avec la façon dont AEM prend en charge la traduction.

Cet article s’appuie sur ces principes de base afin que vous compreniez comment AEM stocke et gère le contenu et comment vous pouvez utiliser AEM outils de traduction pour traduire ce contenu.

## Objectif {#objective}

Ce document vous aide à comprendre comment commencer à traduire le contenu d’un site dans AEM. Après l’avoir lu, vous devriez :

* Comprendre l’importance de la structure de contenu pour la traduction.
* Découvrez comment AEM stocke le contenu.
* Familiarisez-vous avec AEM outils de traduction.

## Exigences et conditions préalables {#requirements-prerequisites}

Avant de commencer à traduire le contenu de votre AEM, plusieurs conditions s’imposent.

### Connaissances {#knowledge}

* Expérience de traduction de contenu dans un CMS
* Expérience d’utilisation des fonctionnalités de base d’un CMS à grande échelle
* posséder une connaissance pratique de AEM gestion de base ;
* Compréhension du service de traduction que vous utilisez
* avoir une compréhension de base du contenu que vous traduisez ;

>[!TIP]
>
>Si vous ne connaissez pas l’utilisation d’un système de gestion de contenu (CMS) à grande échelle comme AEM, consultez la documentation [Manipulation de base](/help/sites-cloud/authoring/getting-started/basic-handling.md) avant de continuer. La documentation Manipulation de base ne fait pas partie du parcours. Revenez donc sur cette page une fois l’opération terminée.

### Outils {#tools}

* Accès aux environnements de test pour tester la traduction de votre contenu
* Informations d’identification pour se connecter à votre service de traduction préféré
* Être membre du groupe `project-administrators` dans AEM

## Comment AEM stocke le contenu {#content-in-aem}

Pour le spécialiste de la traduction, il n’est pas important de comprendre en profondeur la manière dont AEM gère le contenu. Toutefois, il sera utile de connaître les concepts et la terminologie de base, car vous utiliserez ensuite AEM outils de traduction. Plus important encore, vous devez comprendre votre propre contenu et sa structure afin de le traduire efficacement.

### La console Sites {#sites-console}

La console Sites fournit un aperçu de la structure de votre contenu, ce qui facilite la navigation dans votre contenu et sa gestion en créant des pages, en déplaçant et en copiant des pages, ainsi qu’en publiant du contenu.

Pour accéder à la console Sites :

1. Dans le menu de navigation globale, cliquez ou appuyez sur **Navigation** -> **Sites**.
1. La console Sites s’ouvre au niveau supérieur de votre contenu.
1. Assurez-vous que le **Mode Colonnes** est sélectionné à l’aide du sélecteur d’affichage situé en haut à droite de la fenêtre.

   ![Sélection du mode Colonne](assets/selecting-column-view.png)

1. En appuyant ou en cliquant sur un élément d’une colonne, il affiche le contenu situé en dessous dans la hiérarchie de la colonne située à droite.

   ![Hiérarchie du contenu](assets/sites-console-hierarchy.png)

1. En appuyant ou en cliquant sur la case à cocher d’un élément dans une colonne, il sélectionne cet élément et affiche les détails de l’élément sélectionné dans la colonne de droite, ainsi que le nombre d’actions disponibles pour l’élément sélectionné dans la barre d’outils ci-dessus.

   ![Sélection de contenu](assets/sites-console-selection.png)

1. En appuyant ou en cliquant sur le sélecteur de rail en haut à gauche, vous pouvez également afficher la vue **Arborescence de contenu** pour une présentation arborescente de votre contenu.

   ![Arborescence de contenu](assets/sites-console-content-tree.png)

À l’aide de ces outils simples, vous pouvez parcourir intuitivement votre structure de contenu.

>[!NOTE]
>
>L’architecte de contenu définit normalement la structure de contenu pendant que les auteurs de contenu créent le contenu dans cette structure.
>
>En tant que traducteur, il est important de simplement comprendre comment naviguer dans cette structure et comprendre où se trouve le contenu.

### Éditeur de page {#page-editor}

La console Sites vous permet de parcourir votre contenu et fournit un aperçu de sa structure. Pour afficher les détails d’une page, vous devez utiliser l’éditeur de sites.

Pour modifier une page :

1. Utilisez la console Sites pour localiser et sélectionner une page. N’oubliez pas que vous devez appuyer ou cocher la case d’une page pour la sélectionner.

   ![Sélectionner une page à modifier](assets/sites-editor-select-page.png)

1. Appuyez sur l’option **Modifier** dans la barre d’outils.
1. L’éditeur de sites s’ouvre avec la page sélectionnée chargée pour modification dans un nouvel onglet du navigateur.
1. Lorsque vous pointez ou appuyez sur le contenu, les sélecteurs s’affichent pour chaque composant. Les composants sont les blocs de création glisser-déposer qui constituent la page.

   ![Modification d’une page](assets/sites-editor-title.png)

Vous pouvez revenir à la console Sites en revenant à cet onglet dans votre navigateur à tout moment. L’éditeur de sites vous permet d’afficher rapidement le contenu de la page, car les auteurs de contenu et votre audience le verront.

>[!NOTE]
>
>Les auteurs de contenu créent le contenu de votre site à l’aide de l’éditeur de sites.
>
>En tant que traducteur, il est important de simplement comprendre comment visualiser le détail de ce contenu à l’aide de l’éditeur de sites.

## La structure est la clé {#content-structure}

AEM contenu est piloté par sa structure. AEM impose peu d’exigences à la structure de contenu, mais une prise en compte attentive de votre hiérarchie de contenu dans le cadre de la planification du projet peut rendre la traduction beaucoup plus simple.

>[!TIP]
>
>Prévoyez la traduction dès le début de votre projet AEM. Collaborez rapidement avec le chef de projet et les architectes de contenu.
>
>Un responsable de projet d’internationalisation peut être requis en tant que personne distincte dont la responsabilité est de définir quel contenu doit être traduit et ce qui ne l’est pas, et quel contenu traduit peut être modifié par les producteurs de contenu régionaux ou locaux.

## Structure de contenu recommandée {#recommended-structure}

Comme recommandé précédemment, travaillez avec votre architecte de contenu pour déterminer la structure de contenu appropriée pour votre propre projet. Cependant, voici une structure éprouvée, simple et intuitive, qui est assez efficace.

Définissez un dossier de base pour votre projet sous `/content`.

```text
/content/<your-project>
```

La langue dans laquelle votre contenu est créé est appelée racine de langue. Dans notre exemple, il s’agit de l’anglais et il doit se trouver sous ce chemin.

```text
/content/<your-project>/en
```

Tout le contenu du projet qui doit peut-être être localisé doit être placé sous la racine de langue.

```text
/content/<your-project>/en/<your-project-content>
```

Les traductions doivent être créées en tant que dossiers frères à côté de la racine de langue avec leur nom de dossier représentant le code de langue ISO-2 de la langue. Par exemple, l’allemand aurait le chemin suivant.

```text
/content/<your-project>/de
```

>[!NOTE]
>
>L’architecte de contenu est généralement chargé de créer ces dossiers de langue. S’ils ne sont pas créés, AEM ne pourra pas créer ultérieurement de tâches de traduction.

La structure finale peut ressembler à ce qui suit.

```text
/content
    |- your-project
        |- en
            |- some
            |- exciting
            |- sites
            |- content
        |- de
        |- fr
        |- it
        |- ...
    |- another-project
    |- ...
```

Vous devez prendre note du chemin spécifique de votre contenu, car il sera nécessaire ultérieurement pour configurer votre traduction.

>[!NOTE]
>
>Il incombe généralement à l’architecte de contenu de définir la structure du contenu, souvent en collaboration avec le spécialiste de traduction.
>
>Il est présenté ici pour être complet.

## AEM outils de traduction {#translation-tools}

Maintenant que vous comprenez la console et l’éditeur des sites et l’importance de la structure du contenu, nous pouvons examiner comment traduire le contenu. Les outils de traduction en AEM sont assez puissants, mais sont faciles à comprendre à un haut niveau.

* **Connecteur de traduction**  : le connecteur est le lien entre AEM et le service de traduction que vous utilisez.
* **Règles**  de traduction : les règles définissent le contenu sous des chemins d’accès spécifiques qui doit être traduit.
* **Projets de traduction**  : les projets de traduction rassemblent le contenu qui doit être traité comme un effort de traduction unique et suivent l’avancement de la traduction, en interfaçant avec le connecteur pour transmettre le contenu à traduire et le recevoir du service de traduction.

En règle générale, vous ne configurez votre connecteur qu’une seule fois pour votre instance et les règles par projet. Ensuite, vous utilisez des projets de traduction pour traduire votre contenu et tenir ses traductions à jour en permanence.

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de traduction AEM Sites, vous devez :

* Comprendre l’importance de la structure de contenu pour la traduction.
* Découvrez comment AEM stocke le contenu.
* Familiarisez-vous avec AEM outils de traduction.

Tirez parti de ces connaissances et poursuivez votre parcours de traduction AEM Sites en consultant le document [Configurer le connecteur de traduction](configure-connector.md) dans lequel vous apprendrez à vous connecter AEM à un service de traduction.|

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de traduction en consultant le document [Configurer le connecteur de traduction](configure-connector.md), voici quelques ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours.

* [AEM Manipulation de base](/help/sites-cloud/authoring/getting-started/basic-handling.md)  : découvrez les principes de base de l’interface utilisateur d’AEM pour pouvoir naviguer facilement et effectuer les tâches essentielles telles que trouver votre contenu.
* [Identification du contenu à traduire](/help/sites-cloud/administering/translation/rules.md)  : découvrez comment les règles de traduction identifient le contenu à traduire.
* [Configuration de la structure d’intégration de traduction](/help/sites-cloud/administering/translation/integration-framework.md)  - Découvrez comment configurer la structure d’intégration de traduction pour l’intégrer à des services de traduction tiers.
* [Gestion des projets de traduction](/help/sites-cloud/administering/translation/managing-projects.md)  : découvrez comment créer et gérer des projets de traduction humaine et automatique dans AEM.

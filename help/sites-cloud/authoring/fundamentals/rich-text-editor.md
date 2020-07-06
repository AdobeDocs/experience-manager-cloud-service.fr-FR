---
title: Use the Rich Text Editor in [!DNL Adobe Experience Manager] to author content.
description: Use the [!DNL Experience Manager] Rich Text Editor to author content.
translation-type: tm+mt
source-git-commit: 5437329c55bd7da6d8b966a7f01c9e57ff1feb59
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 42%

---


# Utilisation de l’éditeur de texte enrichi pour créer du contenu {#use-rich-text-editor-to-author-content}

L’Editeur de texte enrichi (RTE) est un élément de base permettant d’ajouter du contenu textuel à [!DNL Adobe Experience Manager]. En outre, de nombreux autres composants qui autorisent la création sont basés sur RTE. Les développeurs Experience Manager peuvent personnaliser RTE et les administrateurs configurer RTE pour l’utiliser par les auteurs.

## Modification statique {#in-place-editing}

Sélection d’un composant texte d’un simple clic pour afficher la barre d’outils [du](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar)composant.

![Barre d’outils de composant](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

Cliquez de nouveau ou sélectionnez initialement le composant avec un clic de doublon lent pour ouvrir la modification statique. Le mode de modification contient une barre d’outils. Vous pouvez modifier le contenu et effectuer des modifications de mise en forme de base.

![Modification en place avec l’éditeur de texte enrichi](/help/sites-cloud/authoring/assets/rte-in-place-editing.png)

En règle générale, la barre d’outils propose les options suivantes :

* **Format** : mettre le texte en gras ou en italique ou le souligner.
* **Listes** : créer des listes à puces ou numérotées et définir le retrait.
* **Hyperlien** : créer des liens.
* **Dissocier** : supprimer l’hyperlien.
* **Plein écran**: Ouvrez l’éditeur en mode plein écran.
* **Fermer** : arrêter les modifications.
* **Enregistrer** : enregistrer les modifications.

## Modification en plein écran {#full-screen-editing}

For text-based components, click the full-screen mode ![RTE full screen button](/help/sites-cloud/authoring/assets/editing-full-screen.png) from the [toolbar](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) to open the rich text editor and hides the rest of the page content.

Le mode Plein écran affiche toutes les options configurées que vous pouvez utiliser pour la création. La disponibilité des options dépend de la configuration. <!--Full screen mode displays all the configured options that you can use for authoring. The availability of options [depends on the configuration](/help/sites-administering/rich-text-editor.md).-->

![Éditeur de texte enrichi en mode plein écran](/help/sites-cloud/authoring/assets/rte-full-screen.png)

Les autres options d’éditeur de texte enrichi sont les suivantes :

* **Ancre** : crée une ancre dans le texte avec laquelle vous pourrez ensuite établir un lien ou créer une référence.
* **Aligner le texte à gauche**.
* **Texte centré**.
* **Aligner le texte à droite**.

Cliquez sur Réduire pour fermer le mode plein écran.

>[!Tip]
>
>Copying nested lists from [!DNL Microsoft Word] into the RTE can give inconsistent results. Il est préférable d’effectuer une copie sous forme de texte et un ajustement manuel.

>[!MORELIKETHIS]
>
>* [Configuration des éditeurs de texte enrichi](/help/implementing/developing/extending/rich-text-editor.md)


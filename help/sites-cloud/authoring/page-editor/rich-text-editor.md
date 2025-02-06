---
title: Utilisation de l’éditeur de texte enrichi dans [!DNL Adobe Experience Manager] pour créer du contenu.
description: Utilisation de l’éditeur de texte enrichi [!DNL Experience Manager] pour créer du contenu.
exl-id: 15c175f8-11de-4475-87a9-920219a4c004
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 96%

---

# Utilisation de l’éditeur de texte enrichi pour créer du contenu {#use-rich-text-editor-to-author-content}

L’éditeur de texte enrichi (RTE) est un élément de base permettant d’ajouter du contenu textuel à [!DNL Adobe Experience Manager]. En outre, de nombreux autres composants qui autorisent la création sont basés sur l’éditeur de texte enrichi. Les développeurs d’Experience Manager peuvent personnaliser RTE et les administrateurs le configurer pour qu’il soit utilisé par les auteurs.

## Modification statique {#in-place-editing}

Sélection d’un composant texte d’un simple clic pour afficher la [barre d’outils de composant](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser).

![Barre d’outils de composant](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

Cliquez de nouveau ou sélectionnez initialement le composant d’un double clic lent pour ouvrir la modification statique. Le mode de modification contient une barre d’outils. Vous pouvez modifier le contenu et apporter des modifications de base à la mise en forme.

![Modification en place avec l’éditeur de texte enrichi](/help/sites-cloud/authoring/assets/rte-in-place-editing.png)

En règle générale, la barre d’outils propose les options suivantes :

* **Format** : mettre le texte en gras ou en italique ou le souligner.
* **Listes** : créer des listes à puces ou numérotées et définir le retrait.
* **Hyperlien** : créer des liens.
* **Dissocier** : supprimer l’hyperlien.
* **Plein écran** : ouvrir l’éditeur en mode plein écran.
* **Fermer** : arrêter les modifications.
* **Enregistrer** : enregistrer les modifications.

## Modification en plein écran {#full-screen-editing}

Pour les composants basés sur du texte, cliquez sur le bouton ![Mode plein écran de l’éditeur de texte enrichi](/help/sites-cloud/authoring/assets/editing-full-screen.png) de la [barre d’outils](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) pour ouvrir l’éditeur de texte enrichi et masquer le reste du contenu de la page.

Le mode Plein écran affiche toutes les options configurées que vous pouvez utiliser pour la création. La disponibilité des options [dépend de la configuration](/help/implementing/developing/extending/rich-text-editor.md).

![Éditeur de texte enrichi en mode plein écran](/help/sites-cloud/authoring/assets/rte-full-screen.png)

Les options supplémentaires de l’éditeur de texte enrichi incluent les suivantes :

* **Ancre** : crée une ancre dans le texte avec laquelle vous pourrez ensuite établir un lien ou créer une référence.
* **Aligner le texte à gauche**.
* **Texte centré**.
* **Aligner le texte à droite**.

Cliquez sur Réduire pour fermer le mode plein écran.

>[!TIP]
>
>La copie de listes imbriquées de [!DNL Microsoft Word] vers l’éditeur de texte enrichi peut donner des résultats incohérents. Il est préférable d’effectuer une copie sous forme de texte et un ajustement manuel.

>[!MORELIKETHIS]
>
>* [Configuration d’éditeurs de texte enrichi](/help/implementing/developing/extending/rich-text-editor.md)

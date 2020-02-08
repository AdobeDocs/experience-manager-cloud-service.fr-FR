---
title: Ajout d’annotations de page
description: De nombreux composants directement liés au contenu permettent d’ajouter une annotation.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Ajout d’annotations de page {#adding-page-annotations}

L’ajout de contenu aux pages de votre site Web est souvent l’objet de discussions avant la publication réelle. Pour faciliter cette procédure, de nombreux composants directement liés au contenu (contrairement, par exemple, à la mise en page) permettent d’ajouter une annotation.

Une annotation place un croquis coloré ou un pense-bête sur la page. L’annotation vous permet (ainsi qu’aux autres utilisateurs) de laisser des commentaires ou des questions à l’intention d’autres auteurs ou réviseurs.

>[!NOTE]
>
>Pour rappel, des [commentaires](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) sont également disponibles pour fournir un retour d’informations sur une page.

## Annotations {#annotations}

Un [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) spécial est utilisé pour la création et l’affichage des annotations.

>[!CAUTION]
>
>La suppression d’une ressource (composant, par exemple) supprime toutes les annotations et esquisses associées à cette ressource, quelle que soit leur position sur la page dans son ensemble.

>[!NOTE]
>
>Selon vos besoins, vous pouvez également développer un flux de travail pour envoyer des notifications lorsque des annotations sont ajoutées, mises à jour ou supprimées.

### Annotation d’un composant {#annotating-a-component}

Le mode Annoter permet de créer, de modifier, de déplacer ou de supprimer des annotations sur votre contenu :

1. Pour activer le mode Annotation, cliquez sur l’icône dans la barre d’outils (en haut à droite) lorsque vous modifiez une page :

   ![Bouton Annotation](/help/sites-cloud/authoring/assets/annotations.png)

   Vous pouvez maintenant afficher les annotations existantes.

   >[!NOTE]
   >
   >Pour quitter le mode Annotation, appuyez ou cliquez sur l’icône Annoter (symbole x) à droite de la barre d’outils supérieure.

1. Cliquez/appuyez sur l’icône Ajouter une annotation (symbole plus à gauche de la barre d’outils) pour commencer à ajouter des annotations.

   >[!NOTE]
   >
   >Pour mettre un terme à l’ajout d’annotations (et revenir à l’affichage), appuyez/cliquez sur l’icône Annuler (symbole x dans un cercle blanc) à gauche de la barre d’outils supérieure.

1. Cliquez/appuyez sur le composant requis (les composants qui peuvent être annotés sont encadrés en bleu) pour ajouter l’annotation et ouvrir la boîte de dialogue :

   ![Ajout d’une annotation](/help/sites-cloud/authoring/assets/annotation-adding.png)

   Utilisez alors le champ et/ou l’icône appropriée pour effectuer ce qui suit :

   * Entrez le texte de l’annotation.
   * Créez une esquisse (lignes et formes) pour mettre en surbrillance une zone du composant.

      ![Bouton Annotation Sketch](/help/sites-cloud/authoring/assets/annotation-sketch.png)

      Le curseur se transforme en croix lorsque vous créez une esquisse. Vous pouvez tracer plusieurs lignes distinctes. La ligne d’esquisse reflète la couleur de l’annotation et peut être une flèche, un cercle ou un ovale.

   * Choisissez/changez la couleur :

      ![Bouton de nuance d’annotation](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

   * Supprimez l’annotation.

      ![Bouton de suppression d’annotation](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. Pour fermer la boîte de dialogue de l’annotation, cliquez ou appuyez en dehors de la boîte de dialogue. Une vue tronquée (le premier mot) de l’annotation s’affiche avec les schémas :

   ![Esquisses d’annotation](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Après avoir modifié une annotation, vous pouvez effectuer ce qui suit :

   * Cliquer/appuyer sur la marque de texte pour ouvrir l’annotation. Vous pouvez alors voir le texte intégral de l’annotation, modifier cette dernière ou encore la supprimer.

      * Il n’est pas possible de supprimer les esquisses indépendamment de l’annotation.
   * Repositionner la marque de texte.
   * Cliquez/appuyez sur un trait du schéma pour sélectionner ce dernier et le faire glisser jusqu’à la position voulue.
   * Déplacer ou copier un composant.

      * Toutes les annotations qui lui sont associées, ainsi que leurs esquisses, sont également déplacées ou copiées ; leur position par rapport au paragraphe demeure inchangée.


1. Pour quitter le mode Annotation et revenir au mode précédemment affiché, appuyez ou cliquez sur l’icône Annoter (symbole x) à droite de la barre d’outils supérieure.

>[!NOTE]
>
>Les annotations ne peuvent pas être ajoutées à une page verrouillée par un autre utilisateur.

>[!NOTE]
>
>La définition d’un type de composant individuel détermine s’il est possible d’ajouter une annotation sur des instances de ce composant.

## Indicateur d’annotations {#annotation-indicator}

Les annotations n’apparaissent pas en mode d’édition, mais le badge en haut à droite de la barre d’outils indique le nombre d’annotations figurant sur la page active. Le badge remplace l’icône Annotations par défaut ; il fonctionne comme un lien rapide pour activer/désactiver le mode Annotation :

![Indicateur d’annotation](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## Annotation d’autres ressources {#annotating-other-resources}

Outre les composants, vous pouvez annoter diverses ressources :

* Annotation de fichiers [Annotation de fichiers](/help/assets/manage-digital-assets.md#annotating)
* Annotation de fichiers vidéo [Annotation de fichiers vidéo](/help/assets/manage-video-assets.md#annotate-video-assets)

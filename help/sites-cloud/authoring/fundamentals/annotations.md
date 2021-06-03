---
title: Ajout d’annotations de page
description: Utilisez le mode d’annotation pour laisser des annotations et des schémas sur les pages, car vous utiliserez des pense-bêtes pour faciliter le processus de révision du contenu.
exl-id: a9cb9745-8140-4795-a5f9-fb3a1a299bd8
source-git-commit: 5d533354a29237aeafc00e5570ede3ab00b721fd
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 34%

---

# Ajout d’annotations de page {#adding-page-annotations}

La création de contenu pour votre expérience numérique nécessite souvent des discussions et des commentaires avant la publication. Pour faciliter ce processus de retour, AEM vous permet d’ajouter des annotations à votre contenu.

Une annotation place une simple esquisse ou une simple note (pense-toi à la note autocollante du monde réel) sur la page. L’annotation vous permet de laisser des commentaires ou des questions à l’intention d’autres auteurs et réviseurs.

>[!TIP]
>
>Pour rappel, des [commentaires](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) sont également disponibles pour fournir un retour d’informations sur une page.

Un [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) spécial est utilisé pour la création et l’affichage des annotations.

>[!TIP]
>
>Selon vos besoins, vous pouvez également développer un [workflow](/help/sites-cloud/authoring/workflows/overview.md) pour envoyer des notifications lorsque des annotations sont ajoutées, mises à jour ou supprimées.

## Indicateur d’annotations {#annotation-indicator}

Les annotations n’apparaissent pas en mode d’édition, mais le badge en haut à droite de la barre d’outils indique le nombre d’annotations figurant sur la page active. Le badge remplace l’icône Annotations par défaut ; il fonctionne comme un lien rapide pour activer/désactiver le mode Annotation :

![Indicateur d’annotations](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## Mode d’annotation {#annotate-mode}

Les annotations ne sont visibles qu’en mode Annotation .

1. Pour activer le mode Annotation, cliquez sur l’icône située dans la barre d’outils (en haut à droite) lorsque vous modifiez une page :

   ![Bouton Annotation](/help/sites-cloud/authoring/assets/annotations.png)

   Vous pouvez maintenant afficher les annotations existantes.

   ![Exemples d’annotations](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Cliquez ou appuyez sur l’annotation pour ouvrir la boîte de dialogue d’annotation et afficher ses détails.

   ![Détails de l’annotation](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Pour quitter le mode Annotation et revenir au mode précédemment utilisé, appuyez/cliquez sur le bouton x situé à droite de la barre d’outils supérieure.

## Ajout et modification d’annotations {#annotating-a-component}

Outre l’affichage des annotations, le mode Annotation vous permet de créer, modifier, déplacer ou supprimer des annotations sur votre contenu.

1. [Commencer Annoter le ](#annotate-mode) mode sur la page.

1. Cliquez ou appuyez sur l’icône Ajouter une annotation (symbole plus à gauche de la barre d’outils) pour commencer à ajouter des annotations.

1. Cliquez ou appuyez sur le composant requis (les composants pouvant être annotés sont mis en surbrillance avec une bordure bleue) pour ajouter l’annotation et ouvrir la boîte de dialogue :

   ![Ajout d’une annotation](/help/sites-cloud/authoring/assets/annotation-adding.png)

   Utilisez alors le champ et/ou l’icône appropriée pour effectuer ce qui suit :

   * Entrez le texte de l’annotation.
   * Créez une esquisse (traits et formes) pour mettre en surbrillance une zone du composant.

      ![Bouton d’esquisse d’annotation](/help/sites-cloud/authoring/assets/annotation-sketch.png)

      Le curseur prend la forme d’un pointeur lorsque vous créez une esquisse. Vous pouvez tracer plusieurs lignes distinctes. La ligne d’esquisse reflète la couleur de l’annotation et peut être une flèche, un cercle ou un ovale.

   * Sélectionnez ou modifiez la couleur :

      ![Bouton d’échantillon de nuance d’annotation](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

1. Vous pouvez fermer la boîte de dialogue d’annotation en cliquant ou en appuyant en dehors de la boîte de dialogue. Une vue tronquée de l’annotation, ainsi que les esquisses, s’affiche :

   ![Esquisses d’annotation](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Après avoir modifié une annotation, vous pouvez effectuer ce qui suit :

   * Cliquez ou appuyez sur le marqueur de texte pour ouvrir l’annotation. Une fois ouvert, vous pouvez afficher le texte intégral, apporter des modifications ou [supprimer l’annotation.](#deleting-annotations)
   * Repositionner la marque de texte.
   * Cliquez ou appuyez sur une ligne d’esquisse pour la sélectionner et la faire glisser jusqu’à l’emplacement de votre choix.
   * Déplacer ou copier un composant
      * Toutes les annotations associées et leurs schémas seront également déplacés ou copiés, mais leur position par rapport au paragraphe restera la même.


>[!NOTE]
>
>Les annotations ne peuvent pas être ajoutées à une page verrouillée par un autre utilisateur.

>[!NOTE]
>
>La définition d’un type de composant individuel détermine s’il est possible d’ajouter une annotation sur des instances de ce composant.

## Suppression d’annotations et de schémas {#deleting-annotations}

Les annotations et leurs schémas associés peuvent être supprimés.

1. [Commencer Annoter le ](#annotate-mode) mode sur la page.

1. Cliquez/appuyez sur le marqueur de texte pour ouvrir l’annotation.

1. Cliquez ou appuyez sur l’icône Supprimer .

   ![Supprimer l’annotation](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. L’annotation et tous les schémas associés sont supprimés.

>[!NOTE]
>
>La suppression d’un composant supprime toutes les annotations et tous les schémas associés à cette ressource, quelle que soit leur position sur la page dans son ensemble.

## Suppression de schémas uniquement {#deleting-sketches}

Vous pouvez supprimer uniquement des schémas spécifiques au lieu de l’ensemble de l’annotation avec tous les schémas associés.

1. [Commencer Annoter le ](#annotate-mode) mode sur la page.

1. Cliquez ou appuyez sur le schéma. AEM le surligne avec une boîte bleue plus foncée.

   ![Sélectionner l’esquisse à supprimer](/help/sites-cloud/authoring/assets/annotation-sketch-delete.png)

1. Appuyez sur la touche Suppr de votre clavier.

1. L’esquisse est supprimée, mais l’annotation est conservée.

## Annotation d’autres ressources {#annotating-other-resources}

En plus des composants, vous pouvez annoter un large éventail de ressources :

* Annotation de ressources [Annotation de ressources](/help/assets/manage-digital-assets.md#annotating)
* Annotation de fichiers vidéo [Annotation de fichiers vidéo](/help/assets/manage-video-assets.md#annotate-video-assets)

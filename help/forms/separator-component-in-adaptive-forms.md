---
title: Qu’est-ce que le composant Separator dans les Forms adaptatives ?
description: Le composant Séparateur dans les Forms adaptatives permet de séparer visuellement les sections d’un formulaire.
feature: Adaptive Forms, Foundation Components
role: User
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 79%

---


# Composant séparateur dans les formulaires adaptatifs {#separator-component-in-adaptive-forms}

Vous pouvez utiliser le composant Séparateur pour isoler visuellement les panneaux d’un formulaire. Vous pouvez définir l’aspect général et le style d’un composant Séparateur en spécifiant les propriétés suivantes du composant :

* **Nom de l’élément :** indique le nom du composant. L’expression SOM intègre au composant la valeur spécifiée dans le champ de nom d’élément.
* **Épaisseur :** indique l’épaisseur en pixels du composant séparateur.

* **Classe CSS :** spécifie la classe CSS personnalisée pour le composant séparateur

* **Styles en ligne :** avec [!DNL AEM Forms], vous pouvez désormais appliquer des styles CSS intraligne à chaque composant de formulaire adaptatif et prévisualiser les modifications en temps réel.

Vous pouvez utiliser le mode Mise en page pour définir le nombre de colonnes sur lequel s’étend le composant séparateur. Pour plus d’informations, voir [Utilisation du mode Mise en page pour redimensionner les composants](resize-using-layout-mode.md).

Pour définir les propriétés d’un composant Séparateur :

1. Sélectionnez un composant Séparateur et sélectionnez ![cmppr](assets/cmppr.png). Les propriétés s’ouvrent dans la barre latérale.
1. Cliquez sur un onglet dans la section Propriétés CSS intégrées afin de spécifier les propriétés CSS. Par exemple, a. Dans l’onglet Champ, cliquez sur **Ajouter un élément**. Une ligne avec deux champs est ajoutée.
1. Dans le premier champ de gauche, spécifiez une propriété CSS3 à appliquer. Par exemple : **border**. Vous pouvez également sélectionner une propriété en cliquant sur la flèche vers le bas. La liste déroulante n’est pas exhaustive et vous pouvez spécifier n’importe quel nom de propriété CSS3 prise en charge dans ce champ.
1. Dans le champ adjacent, spécifiez une valeur valide pour la propriété CSS3 spécifiée. Par exemple, **3 pixels de noir uni**.
1. Cliquez sur **Ajouter un élément** pour définir une autre propriété et sa valeur.
1. Cliquez sur **Aperçu** pour afficher les modifications dans le formulaire.
1. Utilisez l’une des méthodes suivantes :
   * Confirmez les modifications en cliquant sur **OK**
   * Quittez la boîte de dialogue sans modification en cliquant sur **Annuler**.


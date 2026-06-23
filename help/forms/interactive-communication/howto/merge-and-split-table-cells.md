---
title: Fusionner et fractionner des cellules de tableau dans l’éditeur de communication interactive
description: Découvrez comment combiner des cellules de tableau adjacentes en une seule cellule et fractionner une cellule fusionnée en plusieurs colonnes pour créer des dispositions de tableau flexibles dans l’éditeur de communication interactive.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: merge-split-table-cells-ic-editor
source-git-commit: b817bcb02c4ff6ac369973ef658d9fcbdce95c51
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 3%

---


# Fusionner et fractionner des cellules de tableau dans l’éditeur de communication interactive

Les grilles de tableau standard sont uniformes par défaut, chaque ligne comporte le même nombre de cellules de taille égale. De nombreuses mises en page réelles nécessitent plus de flexibilité : un en-tête qui s’étend sur plusieurs colonnes, une ligne de résumé qui occupe toute la largeur du tableau ou des cellules regroupées qui lient visuellement les données associées. Vous pouvez fusionner les cellules adjacentes dans une ligne pour obtenir ces mises en page, et diviser toute cellule précédemment fusionnée en colonnes individuelles chaque fois que vous devez réviser la structure.

| Qui | Avantage |
|-----|---------|
| **Auteur (concepteur de communication interactive/concepteur de mises en page)** | Créez des factures, des plannings et des tableaux de comparaison avec des en-têtes étendus ou des cellules groupées sans quitter l’éditeur de communication interactive. |

## Fusionner les cellules

1. Dans l’éditeur de communication interactive, cliquez sur la première cellule à inclure dans la fusion.

1. Maintenez la touche **Maj** enfoncée et cliquez sur la dernière cellule de la plage pour sélectionner toutes les cellules consécutives de la même ligne.

1. Cliquez avec le bouton droit sur la sélection, sélectionnez **Fusionner**, puis choisissez **Fusionner les cellules**.

   ![Fusionner les cellules](/help/forms/interactive-communication/assets/split-merge-table1.png)

   Les cellules sélectionnées sont combinées en une seule cellule fusionnée. Le contenu et la mise en forme de la première cellule de la sélection sont conservés ; le contenu des cellules suivantes est ignoré.

   Par exemple, dans un tableau Détails du véhicule, vous pouvez fusionner les cellules consécutives de la ligne d’en-tête pour créer une étiquette transversale telle que **Détails du véhicule**.

**Que garder à l’esprit**

- Vous ne pouvez fusionner que les cellules consécutives d&#39;une même ligne. La sélection de cellules sur plusieurs lignes n’est pas prise en charge.
- Seul le contenu et la mise en forme de la première cellule sont conservés après la fusion.

## Fractionner une cellule fusionnée

1. Cliquez avec le bouton droit sur la cellule fusionnée à fractionner.

1. Sélectionnez **Fractionner**, puis choisissez **Fractionner la cellule**.

   ![Fractionner la cellule](/help/forms/interactive-communication/assets/split-merge-table2.png)

1. Dans la boîte de dialogue **Fractionner la cellule**, saisissez le nombre de colonnes dans lesquelles fractionner la cellule.

1. Cliquez sur **OK** pour appliquer.

   ![Boîte de dialogue Fractionner la cellule](/help/forms/interactive-communication/assets/split-merge-table3.png)

   La valeur **Colonnes max** affichée dans la boîte de dialogue représente le nombre maximal de cellules que vous pouvez fractionner, soit le nombre de cellules qui ont été fusionnées à l’origine. Par exemple, si deux cellules ont été fusionnées, **Colonnes max** est 2.

   | Fractionner la valeur | Résultat |
   |-------------|--------|
   | 2 | La cellule se divise en 2 cellules individuelles |
   | 1 | La cellule reste comme une seule cellule (aucune modification). |

   La structure du tableau est automatiquement mise à jour. Toute valeur comprise entre 1 et la valeur **Colonnes max** est valide.

## Remarque

La fusion de cellules qui s’étendent sur plusieurs lignes n’est pas entièrement prise en charge et peut produire des résultats inattendus. Effectuez des opérations de fusion uniquement sur des cellules consécutives dans la même ligne.

## Questions fréquentes

**Puis-je fusionner des cellules dans des lignes et des colonnes ?**
Non. Seules les cellules consécutives d’une même ligne peuvent être fusionnées. Les fusions entre lignes ne sont pas entièrement prises en charge et peuvent produire des résultats inattendus.

**Qu’advient-il du contenu des cellules que je fusionne ?**
Le contenu et la mise en forme de la première cellule de la sélection sont conservés. Le contenu des cellules restantes est ignoré lorsque la fusion est appliquée.

**Comment puis-je connaître le nombre maximal de colonnes dans lesquelles je peux diviser une cellule fusionnée ?**
La boîte de dialogue de division affiche la valeur **Colonnes max**, qui est égale au nombre de cellules qui ont été fusionnées à l’origine pour créer la cellule.

## Voir également

- [Composant Tableau dans l’éditeur de communication interactive](/help/forms/interactive-communication/table.md)
- [Créer un tableau dynamique dans l’éditeur de communication interactive](/help/forms/interactive-communication/dynamic-table-in-interactive-communication-editor.md)
- [Créer une communication interactive](/help/forms/interactive-communication/create-interactive-communication.md)


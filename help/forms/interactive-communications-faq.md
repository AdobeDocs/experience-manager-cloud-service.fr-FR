---
title: Questions fréquentes — Communications interactives
description: Questions fréquentes sur les communications interactives dans AEM Forms as a Cloud Service, couvrant les modèles d’affichage, les annotations, la comparaison de versions, etc.
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 4cc1bff3-edfb-4826-b914-2a2231b703f9
source-git-commit: 8043d0bd709962023f4828a6fffa2939788538b2
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 5%

---

# Questions fréquentes — Communications interactives

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

## Général

**Q : Puis-je importer un fichier XDP existant dans l’éditeur de communications interactives ?**
Oui, vous pouvez importer un fichier XDP existant et l’utiliser comme point de départ. Toutes les fonctionnalités non prises en charge sont mises en surbrillance pendant le processus d’importation.

**Q : L’éditeur de communications interactives est-il disponible pour les déploiements On-Premise ?**
Non, l’éditeur n’est disponible que pour les déploiements de Forms as a Cloud Service.

## Modèles d’affichage

**Q : Qu’est-ce qu’un modèle d’affichage et en quoi est-il différent de la liaison de données ?**
Un modèle d’affichage contrôle la manière dont une valeur de champ est *présentée* aux utilisateurs dans l’aperçu de la zone de travail et dans la sortie générée, par exemple en formatant un nombre en tant que devise (1 234,21 $) ou une chaîne de texte en tant que numéro de téléphone (555) 123-4567). La valeur stockée sous-jacente reste inchangée. La liaison de données, en revanche, contrôle *d’où* la valeur du champ provient - la connexion du champ à un modèle de données ou à un élément de schéma.

**Q : Quels types de champs prennent en charge les modèles d’affichage ?**
Les modèles d’affichage sont pris en charge sur les composants Zone de texte, Champ numérique, Champ de date, Champ de date/heure et Variable non liée. Chaque type de champ utilise la syntaxe de clause d’image XFA appropriée à son type de données.

**Q : Mon modèle d’affichage de date ne fonctionne pas : le champ affiche la valeur brute au lieu de la sortie formatée. Qu&#39;est-ce qui ne va pas ?**
Les champs Date et Date/Heure nécessitent que la valeur sous-jacente soit conforme au format **ISO 8601**. Pour les champs de date, saisissez les valeurs au format `YYYY-MM-DD` (par exemple, `2007-04-01`). Pour les champs Date/Heure, utilisez le format `YYYY-MM-DDTHH:MM` (par exemple, `2007-04-01T14:30`). Les valeurs qui ne respectent pas la norme ISO 8601 sont affichées en l’état, sans le modèle d’affichage appliqué.

**Q : Puis-je définir un modèle personnalisé qui ne figure pas dans la liste prédéfinie ?**
Oui. Vous pouvez saisir une **clause d’image XFA** personnalisée directement dans le champ Modèle d’affichage du panneau Propriétés. Reportez-vous aux symboles des clauses d’image pour chaque type de champ dans les pages de référence de composant respectives.

## Révision et annotations

**Q : Quelle est la différence entre les commentaires et les annotations dans les communications interactives ?**
Les **commentaires** sont des notes générales ajoutées à un IC à partir du panneau Commentaires — elles sont jointes au document dans son ensemble, et non à des composants spécifiques. Les **annotations** sont positionnées, des épingles de révision au niveau du composant : un réviseur ou une réviseuse ouvre une zone de travail d’annotation en lecture seule, clique sur n’importe quel composant de la conception et laisse un commentaire épinglé à cet endroit précis. Tous les réviseurs partagent la même vue d’annotation. Les auteurs peuvent ensuite marquer chaque annotation comme résolue dans l’éditeur IC.

**Q : Un réviseur peut-il accidentellement modifier la CI tout en conservant des annotations ?**
Non. La zone de travail d’annotation est une vue dédiée en lecture seule. Les réviseurs peuvent uniquement ajouter ou afficher des épingles de commentaire — ils ne peuvent pas modifier un composant dans l&#39;IC.

**Q : Qu’advient-il d’une annotation après qu’elle a été marquée comme Résolue ?**
Les annotations résolues restent visibles à des fins d’historique, mais apparaissent sous la forme d’épingles fermées (grises), ce qui les distingue visuellement des éléments de commentaires ouverts (actifs). Cela permet aux équipes de suivre la progression de la révision sans perdre le journal d’audit.

**Q : Les annotations sont-elles prises en charge sur tous les composants ?**
Pas encore. Les annotations sur les parties de fragment d’un document et sur le composant Tableau ne sont actuellement pas prises en charge. Les annotations des autres composants sont entièrement prises en charge.

## Comparaison de versions

**Q : Que puis-je voir lorsque je compare deux versions ?**
Les deux versions s’ouvrent côte à côte en tant qu’aperçus PDF. Vous pouvez ainsi examiner visuellement les différences de disposition et de contenu statique. Les valeurs de champ dynamique ne sont pas incluses : seule la mise en page rendue et le texte statique sont comparés.

**Q : Comment démarrer une comparaison de versions ?**
Accédez à **Forms > Forms et documents**, sélectionnez l’IC, cliquez sur **Comparer la version** dans la barre d’outils d’actions, puis sélectionnez la version à comparer. Un nouvel onglet s’ouvre avec les deux versions affichées côte à côte.

**Q : Puis-je voir des modifications de texte spécifiques dans un paragraphe lors de la comparaison de versions ?**
Non. Si un paragraphe a été réécrit ou réorganisé, les deux pages sont rendues de manière identique à leur PDF source. Il n’existe pas de comparaison de texte intégrée ; la comparaison est visuelle uniquement.

## Tableaux

**Q : Puis-je fusionner des cellules dans un tableau ?**
Oui. Sélectionnez au moins deux cellules consécutives dans la même ligne, cliquez avec le bouton droit de la souris et choisissez **Fusionner les cellules**. Seules les cellules consécutives d’une même ligne peuvent être fusionnées. Les fusions entre lignes ne sont pas entièrement prises en charge. Voir [Fusionner et fractionner des cellules de tableau](/help/forms/interactive-communication/howto/merge-and-split-table-cells.md).

**Q : Puis-je annuler une fusion de cellules ?**
Oui. Cliquez avec le bouton droit sur la cellule fusionnée, sélectionnez **Fractionner la cellule** et indiquez le nombre de colonnes à fractionner (jusqu’au nombre original de cellules fusionnées).

## Page Principal

**Q : Comment puis-je faire apparaître un composant sur chaque page d’une communication interactive ?**
Déplacez le composant vers le gabarit de page. Cliquez avec le bouton droit de la souris sur un composant éligible d’une page de conception et sélectionnez **Déplacer vers > Page de Principal**. Le composant est supprimé de la page de conception et placé sur le gabarit de page à la même position visuelle, afin qu’il apparaisse de manière cohérente sur toutes les pages qui partagent ce gabarit de page. Voir [Déplacer un composant vers la page de Principal &#x200B;](/help/forms/interactive-communication/howto/move-component-to-master-page.md).

**Q : Quels types de composants ne peuvent pas être déplacés vers le gabarit de page ?**
Les types suivants ne sont pas éligibles à l’action Déplacer vers la page de Principal : zones de contenu, zones de page, ensembles de pages, fragments, sous-formulaire, lignes de tableau, cellules de tableau et boutons radio. Les composants dotés d’un verrouillage de contenu ou de disposition ne sont pas éligibles non plus.

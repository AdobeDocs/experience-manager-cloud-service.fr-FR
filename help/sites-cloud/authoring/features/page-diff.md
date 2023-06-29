---
title: Outil de comparaison des pages
description: De fait, l’outil de comparaison des pages permet d’afficher côte à côte deux pages pour les comparer en mettant en évidence leurs différences.
exl-id: 6e5c7f14-c980-48e3-8bdd-a7ec10a9e680
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 45%

---

# Outil de comparaison des pages {#page-diff}

## Présentation {#introduction}

La création de contenu est un processus itératif. Pour être efficace lorsque vous créez du contenu, vous devez pouvoir voir ce qui a changé d’une version à l’autre. L’affichage d’une version de page, puis de l’autre, est inefficace et susceptible d’erreur. Un auteur souhaite pouvoir facilement comparer la page actuelle côte à côte à une autre version.

De fait, l’outil de comparaison des pages permet d’afficher côte à côte deux pages pour les comparer en mettant en évidence leurs différences.

>[!NOTE]
>
>L’utilisateur doit disposer de la variable **Modifier/Créer/Supprimer** autorisation sur le noeud `/content/versionhistory` pour utiliser la fonctionnalité.
>
>Consultez la section consacrée à l’[outil de comparaison des pages](/help/implementing/developing/introduction/page-diff.md#operation-details) pour plus d’informations sur cette fonction.

## Utilisez {#use}

L’outil de comparaison côte à côte permet de comparer les éléments suivants :

* [Versions](/help/sites-cloud/authoring/features/page-versions.md#comparing-a-version-with-current-page) : la version actuelle d’une page et sa version antérieure.
* [Live Copies](/help/sites-cloud/administering/msm/creating-live-copies.md#comparing-a-live-copy-page-with-a-blueprint-page) : une Live Copy et son plan directeur
* [Lancements](/help/sites-cloud/authoring/launches/editing.md#comparing-a-launch-page-to-its-source-page) : un lancement et sa source
* [Copies de langue](/help/sites-cloud/administering/translation/managing-projects.md#comparing-language-copies) : une page avant et après (re)traduction

Reportez-vous aux rubriques correspondantes afin de connaître la procédure de comparaison pour ces différents éléments.

### Présentation des différences {#presentation-of-differences}

Quel que soit le contenu comparé, la présentation de l’outil de comparaison reste la même.

* Le contenu sélectionné au démarrage de l’outil de comparaison s’affiche à gauche (le point d’entrée de l’outil de comparaison).
* Le contenu de la comparaison est affiché à droite (par rapport au contenu sélectionné).

Par exemple, si vous comparez des versions, la version actuelle est affichée à gauche et la version précédente à droite.

La source des deux pages s’affiche clairement dans la barre d’en-tête située en haut de la fenêtre du navigateur.

![Vue côte à côte des versions](/help/sites-cloud/authoring/assets/versions-side-by-side.png)

L’outil de comparaison détecte les modifications effectuées sur les composants et le code HTML. Les éléments qui ont été modifiés sont mis en surbrillance avec des couleurs différentes.

**Modifications des composants**

* Vert clair : composant ajouté
* Rose : composant supprimé

**Modifications du HTML**

* Vert foncé - HTML ajouté
* Rouge : HTML supprimé

>[!NOTE]
>
>Lorsque vous comparez des copies de langue, la mise en surbrillance est désactivée. En effet, dans la mesure où la traduction modifie tout le contenu, la mise en surbrillance ne présente aucun intérêt.

### Affichage en mode plein écran {#fullscreen-and-exiting}

Pour vous concentrer sur un contenu particulier, vous pouvez cliquer sur l’icône Plein écran de l’un ou l’autre des &quot;côtés&quot; de la comparaison côte à côte afin de l’agrandir dans la fenêtre du navigateur.

![Bouton Plein écran](/help/sites-cloud/authoring/assets/versions-full-screen.png)

Le côté sélectionné s’affiche dans la totalité de la fenêtre, mais la barre d’en-tête reste disponible en haut de la fenêtre pour vous permettre de basculer d’une page à l’autre si vous le souhaitez.

![Mode Plein écran](/help/sites-cloud/authoring/assets/versions-full-screen-mode.png)

>[!NOTE]
>
>Si la largeur du navigateur ne peut pas contenir les deux noms de page en mode Plein écran, seul le nom de la page affichée s’affiche et l’autre est disponible derrière les points de suspension.

Vous pouvez également quitter le mode plein écran en cliquant sur l’icône de fermeture du mode plein écran.

![Quitter le plein écran](/help/sites-cloud/authoring/assets/versions-exit-full-screen.png)

Vous pouvez quitter le mode de comparaison côte à côte à tout moment en cliquant sur le bouton Fermer dans l’en-tête.

## Restrictions {#limitations}

Dans certains cas, l’outil de comparaison des pages peut ne pas détecter une différence comme prévu.

* Lors de la comparaison des versions et lancements, la comparaison ne prend pas en compte les composants dynamiques tels que les chemins de navigation, les menus, les listes de produits ou les logos (composants qui dépendent de la structure du site pour effectuer le rendu de leur contenu).
* Pour les versions, l’outil de comparaison ne recrée pas la politique de contrôle d’accès ni les relations Live Copy.
* Si une page est déplacée, vous ne pouvez plus effectuer de comparaison avec les versions antérieures au déplacement.
   * Si vous rencontrez des problèmes avec une comparaison, vérifiez la variable [Chronologie](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) pour la page afin de voir si la page a été déplacée.

>[!NOTE]
>
>Les versions ne peuvent pas être comparées entre elles. Seule la version en cours peut être comparée aux autres versions de la page. La version dont les modifications sont mises en surbrillance est toujours la version en cours.

>[!NOTE]
>
>Pour plus d’informations sur le fonctionnement de l’outil de comparaison des pages et les limites qui peuvent affecter cette comparaison, voir [documentation destinée aux développeurs](/help/implementing/developing/introduction/page-diff.md) de cette fonctionnalité.

---
title: Comment gérer les balises dans la vue Assets ?
description: Découvrez comment gérer les balises dans la vue Assets. Les balises vous aident à classer les ressources qui peuvent être parcourues et recherchées plus efficacement.
source-git-commit: bdbe47a8f06d2ec1cd75103905677fcd3955632d
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 1%

---

# Gestion des balises dans la vue Assets {#view-assets-and-details}


>[!CONTEXTUALHELP]
>id="assets_taxonomy_management"
>title="Gérer les balises"
>abstract="Les balises vous aident à classer les ressources qui peuvent être parcourues et recherchées plus efficacement. Les administrateurs ont la possibilité d’utiliser la structure de balisage hiérarchique, qui facilite l’application des métadonnées pertinentes, la classification des ressources, la prise en charge de la recherche, la réutilisation des balises, l’amélioration de la visibilité, etc."

Les balises vous aident à classer les ressources qui peuvent être parcourues et recherchées plus efficacement. Le balisage permet de propager la taxonomie appropriée à d’autres utilisateurs et workflows.

Des listes plats de vocabulaires contrôlés peuvent devenir ingérables au fil du temps. Les administrateurs ont la possibilité d’utiliser la structure de balisage hiérarchique, qui facilite l’application des métadonnées pertinentes, la classification des ressources, la prise en charge de la recherche, la réutilisation des balises, l’amélioration de la visibilité, etc.

Vous pouvez créer un espace de noms au niveau racine et créer une structure hiérarchique de sous-balises dans l’espace de noms. Par exemple, vous pouvez créer une `Activities` espace de noms au niveau racine et ont `Cycling`, `Hiking`, et `Running` balises dans l’espace de noms. Vous pouvez avoir d’autres sous-balises. `Clothing` et `Shoes` dans `Running`.

![Gestion des balises](assets/tags-hierarchy.png)

Le balisage offre de nombreux avantages, tels que :

* Le balisage permet aux auteurs d’organiser facilement des ressources dissemblables par le biais d’une taxonomie commune. Les auteurs peuvent rapidement rechercher et organiser des ressources par balises courantes.

* Les balises hiérarchiques sont extrêmement flexibles et constituent un excellent moyen d’organiser les termes de manière logique. Grâce aux espaces de noms, balises et sous-balises, des systèmes taxonomiques complets peuvent être représentés.

* Les balises peuvent évoluer au fil du temps à mesure qu’un vocabulaire organisationnel change.

* Les balises gérées dans la vue Admin restent synchronisées avec les balises gérées dans la vue Assets, ce qui garantit la gouvernance et l’intégrité des métadonnées.

Pour pouvoir appliquer des balises à des ressources, vous devez d’abord créer un espace de noms, puis créer et ajouter des balises. Vous pouvez également créer des balises et les ajouter à un espace de noms existant. Toutes les balises que vous créez au niveau racine sont automatiquement ajoutées à l’espace de noms des balises standard. Vous pouvez ensuite ajouter le champ Balises au formulaire de métadonnées afin qu’il s’affiche sur la page Détails de la ressource. Après avoir configuré ces paramètres, vous pouvez commencer à appliquer des balises aux ressources.

>[!NOTE]
>
>Vous ne devez ajouter le champ Balises au formulaire de métadonnées que si vous n’utilisez pas le formulaire de métadonnées par défaut.

![Gestion des balises](assets/tagging-taxonomy-management.png)

D’autres fonctionnalités, dont la fusion, le changement de nom, la localisation et la publication de balises, sont disponibles dans la vue Admin.

## Création d’un espace de noms {#creating-a-namespace}

Un espace de noms est un conteneur de balises qui ne peut exister qu’au niveau racine. Vous pouvez commencer à configurer la structure hiérarchique des balises en définissant d’abord un nom logique pour l’espace de noms. Si vous n’ajoutez pas de balise aux espaces de noms existants, la balise passe automatiquement aux balises standard.

Pour créer un espace de noms, procédez comme suit :

1. Accédez à `Taxonomy Management` under `Settings` pour afficher la liste des espaces de noms existants. Vous pouvez également afficher la date de dernière modification, l’utilisateur qui a modifié l’espace de noms ou les balises qui se trouvent sous celui-ci, ainsi que le nombre de fois où la balise est utilisée dans une ressource.
1. Cliquez sur `Create Namespace`.
1. Ajouter `Title`, `Name`, et `Description` pour l’espace de noms. L’entrée que vous spécifiez dans la variable `Title` s’affiche en haut de la hiérarchie. Par exemple, dans l’image suivante, **Activités** fait référence au titre de l’espace de noms.

   ![Gestion des balises](assets/tags-hierarchy.png)

   <!--
    >[!NOTE]
    >
    >You can use `Name` as a primary key if you are using any other metadata management tool is the source of truth for taxonomy values, you can use the name as a primary key.
    >
    -->

1. Cliquez sur `Save`.

## Ajout de balises à un espace de noms {#adding-tags-to-namespace}

Pour ajouter des balises à un espace de noms, procédez comme suit :

1. Accédez à `Taxonomy Management`.
1. Sélectionnez l’espace de noms et cliquez sur `Create` pour créer la balise au niveau supérieur sous l’espace de noms. Si vous devez créer une sous-balise sous une balise qui existe dans un espace de noms, sélectionnez la balise, puis cliquez sur `Create`.
   ![Hiérarchie des balises](assets/hierarchy-of-tags.png)

   Dans cet exemple, l’image à gauche représente la balise directement sous l’espace de noms `automobile-four-wheeler` affiché dans le `Path` champ . L’image à droite est un exemple de sous-balises ajoutées dans une balise, car il y a plus de noms de balise, `jeep` et `jeep-meridian`, affiché dans le `Path` en plus de l’espace de noms.
1. Indiquez le titre, le nom et la description de la balise, puis cliquez sur `Save`.


   >[!NOTE]
   >
   >* Le `Title` et `Name` sont obligatoires, tandis que la variable `Description` est facultatif.
   >* Par défaut, l’outil copie le texte saisi dans le champ Titre , supprime les espaces vides ou les caractères spéciaux (. &amp; / \ : * ? [ ] | &quot; %) et la stocke sous la forme Nom.
   >* Vous pouvez mettre à jour la variable `Title` plus tard, mais le champ `Name` est en lecture seule.

## Ajout de balises à des balises standard {#adding-tags-to-standard-tags}

Les balises non structurées ou qui n’ont pas de hiérarchie sont stockées sous `Standard Tags` espace de noms. De plus, lorsque vous souhaitez ajouter des termes descriptifs supplémentaires sans affecter la taxonomie régie, vous pouvez stocker cette valeur sous `Standard Tags`. Vous pouvez déplacer ces valeurs sous des espaces de noms structurés au fil du temps. De plus, vous pouvez utiliser la variable `Standard Tags` espace de noms comme entrée de formulaire libre pour les mots-clés.

Pour créer une balise standard, cliquez sur `Create Tag` au niveau racine. Indiquez le titre, le nom et la description, puis cliquez sur `Save`.

![Ajout de balises aux balises standard](assets/adding-tags-to-standard-tags.png)

>[!NOTE]
>
>Si vous supprimez `Standard Tags` à l’aide de la vue Admin, les balises créées au niveau racine ne s’affichent pas dans la liste des balises disponibles.

## Déplacement des balises {#moving-tags}

Si vous stockez vos balises sous une hiérarchie incorrecte ou si votre taxonomie change au fil du temps, vous pouvez déplacer les balises sélectionnées pour préserver l’intégrité des données. Les conditions suivantes doivent être prises en compte lors du déplacement des balises :

* Les balises ne peuvent se déplacer que sous les espaces de noms existants ou dans une hiérarchie de balises existante.
* Les balises ne peuvent pas être déplacées vers la racine pour devenir un espace de noms.
* Le déplacement d’une balise parent déplace également toutes les balises enfants stockées dans la hiérarchie.

Effectuez les étapes suivantes pour déplacer des balises d’un emplacement à un autre :

1. Sélectionnez la balise ou la hiérarchie complète des balises sous l’espace de noms approprié, puis cliquez sur `Move`.
1. Dans la boîte de dialogue Déplacer, sélectionnez la nouvelle balise de destination ou l’espace de noms à l’aide de la variable `Select Tag` .
1. Cliquez sur `Save`. La balise s’affiche à son nouvel emplacement.

## Modification des balises {#editing-tags}

Pour modifier le titre de la balise, sélectionnez-la, puis cliquez sur `Edit`. Indiquez le nouveau titre, puis cliquez sur `Save`.

>[!NOTE]
>
>* Le `Name` d’une balise ne peut pas être mise à jour. Le chemin d’accès racine d’une balise est également basé sur le nom de la balise. Le chemin d’accès reste le même, même si vous mettez à jour la variable `Title` champ .
>* D’autres opérations telles que la fusion, la localisation et la publication sont disponibles dans la vue Admin.

## Suppression des balises {#deleting-tags}

Vous pouvez supprimer plusieurs espaces de noms ou balises simultanément. L’opération de suppression ne peut pas être annulée.

Pour supprimer des balises, procédez comme suit :

1. Sélectionnez l’espace de noms ou la balise et cliquez sur `Delete`.
1. Cliquez sur `Confirm`.

>[!NOTE]
>
>* La suppression de la balise parente ou de l’espace de noms supprime également les sous-balises stockées dans la hiérarchie. Si vous devez supprimer ou mettre à jour l’espace de noms parent, il est recommandé de [déplacer vos balises ;](#moving-tags) vers la nouvelle destination avant de supprimer la hiérarchie parente.
>* La suppression d’une balise supprime également toutes ses références des ressources.
>* Vous ne pouvez pas supprimer les balises standard qui existent au niveau racine.

## Ajout du composant Balises au formulaire de métadonnées {#adding-tags-to-metadata-form}

Le composant de balises est ajouté à la variable `default` formulaire de métadonnées automatiquement. Vous pouvez concevoir une [Formulaire de métadonnées](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/metadata.html?lang=en#metadata-forms) soit en utilisant un modèle, soit à partir de zéro. Si vous n’utilisez pas de modèle de formulaire de métadonnées existant, vous pouvez modifier votre formulaire de métadonnées et ajouter le composant de balises. Le mappage des propriétés de métadonnées est renseigné automatiquement et ne peut pas être modifié pour le moment. Les utilisateurs de la vue Admin peuvent mettre à jour le mappage pour stocker les valeurs de balise à l’aide d’espaces de noms personnalisés et n’exposer que les sous-ensembles de hiérarchies à l’aide des chemins d’accès racine.

Regardez cette vidéo rapide pour découvrir comment ajouter le composant Balises à votre formulaire de métadonnées :

>[!VIDEO](https://video.tv.adobe.com/v/3420452)


### Ajout de balises à Assets {#adding-tags-to-assets}

1. Accédez à la page Détails de la ressource et accédez au `Tags` du formulaire Métadonnées.
1. Sélectionnez l’icône du sélecteur de balises située en regard du champ Balises ou commencez à saisir un nom de balise pour afficher les résultats suggérés.

   ![Balisage des ressources](assets/adding-tags-to-assets.png)

1. Sélectionnez une ou plusieurs balises. La sous-balise est sélectionnée automatiquement avec la balise ou l’espace de noms parent.
Les balises modifiées dans la vue Assets sont également appliquées dans la vue Admin.

## Limites {#limitations}

Les fonctionnalités de taxonomie avancée suivantes ne sont actuellement pas disponibles dans la vue Assets et ne sont accessibles que par la vue Admin :

* **Localisation :** Toute localisation doit se produire dans la vue Admin.
* **Chemin racine :** Les chemins d’accès racine ne peuvent pas être configurés. Tous les espaces de noms stockés dans la Gestion de la taxonomie sont exposés sur la propriété Balises dans la vue Ressources.
* **Balises standard :** Les balises standard appliquées dans la vue Admin sont visibles dans la vue Assets. Vous ne pouvez pas ajouter de nouvelles balises standard dans la vue Ressources de la page Détails de la ressource. Les valeurs existantes qui sont stockées dans des balises standard sont appliquées à la page Détails des ressources.
* **Espaces de noms personnalisés :** Les balises ne peuvent pas être mappées à des espaces de noms personnalisés.
* **Affichage des références :** Les administrateurs peuvent voir l’utilisation des balises dans la vue Assets. Cela fait référence à toutes les ressources qui utilisent activement une balise . Toutefois, les administrateurs ne peuvent pas voir les ressources individuelles à l’aide de la balise dans les références.

<!--
*   Overview
*   Benefits
*   Prerequisites and Permissions
*   Configuration
*   Managing Tags
    *   Creating a Namespace
    *   Adding Tags to a Namespace
    *   Adding Tags to Standard Tags
    *   Moving Tags
    *   Editing Tags
    *   Deleting Tags
*   Applying Tags
    *   Adding Tags to the Metadata form
    *   Adding Tags to Assets
*   Limitations
-->
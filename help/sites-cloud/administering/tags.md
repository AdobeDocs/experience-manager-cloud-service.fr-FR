---
title: Administration des balises
description: Découvrez comment administrer des balises dans AEM pour organiser votre contenu.
exl-id: 42480699-b7a7-4678-a763-569a9b7573e2
solution: Experience Manager Sites
feature: Workflow
role: Admin
source-git-commit: 913b1beceb974243f0aa7486ddd195998d5e9439
workflow-type: tm+mt
source-wordcount: '2200'
ht-degree: 6%

---

# Administration des balises {#administering-tags}

Les balises constituent une méthode intuitive de classification de contenu. Ils peuvent être considérés comme des mots-clés ou des étiquettes (métadonnées) qui permettent de trouver plus rapidement le contenu.

Dans Adobe Experience Manager (AEM), une balise peut être une propriété de :

* Noeud de contenu pour une page
   * Pour plus d’informations, consultez le document [Utilisation des balises](/help/sites-cloud/authoring/sites-console/tags.md) .
* Noeud de métadonnées d’une ressource
   * Pour plus d’informations, consultez le document [Gestion des métadonnées pour Digital Assets](/help/assets/manage-metadata.md) .

>[!TIP]
>
>Il est recommandé de minimiser le nombre de balises qui se rapportent aux mêmes idées. Par exemple, si vous gérez du contenu pour un magasin d’approvisionnement en extérieur, vous n’avez probablement pas besoin d’une balise pour les **chaussures** et **chaussures**.

## Fonctionnalités de balise {#tag-features}

Les balises offrent des fonctionnalités puissantes pour organiser et gérer le contenu.

* Les balises peuvent être regroupées dans différents espaces de noms.
   * Les espaces de noms peuvent être considérés comme des hiérarchies qui permettent de créer des taxonomies.
   * Ces taxonomies sont globales dans l’ensemble d’AEM.
* Les balises peuvent être appliquées par les auteurs et utilisées par les visiteurs du site.
* Quel que soit leur créateur ou créatrice, toutes les formes de balises peuvent être sélectionnées, lors de l’affectation d’une page ou lors d’une recherche.
* Les balises sont utilisées par le [composant Liste](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html?lang=fr) pour générer des listes dynamiques en fonction des balises sélectionnées.

## Exigences en matière de balises {#requirements}

Quelques détails techniques doivent être pris en compte lors de la création et de la gestion des balises.

* Les balises doivent être uniques dans un espace de noms spécifique.
* Le nom d’une balise ne peut pas inclure de délimiteurs de balise :
   * Deux-points (`:`) : délimite la balise d’espace de noms
   * Barre oblique (`/`) - Détermine les sous-balises.
* Si le titre d’une balise inclut des délimiteurs de balise, ils seront supprimés dans l’interface utilisateur.
* Les balises peuvent être créées et leur taxonomie peut être modifiée par les membres du groupe `tag-administrators` et les membres disposant de droits de modification sur `/content/cq:tags`.
   * Une balise contenant des balises enfants est appelée balise conteneur.
   * Une balise qui n’est pas une balise conteneur est appelée balise terminale.
   * Un espace de noms de balise peut être une balise terminale ou conteneur.

Pour plus d’informations techniques sur le fonctionnement des balises, voir [AEM Tagging Framework](/help/implementing/developing/introduction/tagging-framework.md).

## Console Balisage {#tagging-console}

La console de balisage est utilisée pour créer et gérer des balises et leurs taxonomies. Vous pouvez utiliser la console de balisage pour gérer vos balises en procédant comme suit :

* Regroupement dans des espaces de noms
* Vérification de l’utilisation des balises existantes avant d’en créer de nouvelles.
* Réorganisation de vos balises sans déconnecter la balise du contenu actuellement référencé.

Pour accéder à la console de balisage :

1. Connectez-vous à un environnement de création avec les privilèges d’administrateur.
1. Dans le menu de navigation globale, sélectionnez **`Tools`** > **`General`** >
   **`Tagging`**.

![La console de balisage dans AEM](/help/sites-cloud/administering/assets/tagging-console.png)

## Création de balises {#creating-new-tags}

Vous pouvez créer et utiliser des balises pour organiser votre contenu en plusieurs étapes.

1. [Créez un espace de noms pour vos balises ](#creating-namespaces) (ou choisissez un espace de noms existant à réutiliser).
1. [Créez une nouvelle balise.](#creating-tags)
1. [Publish la balise .](#publishing-tags)

### Création d’espaces de noms {#creating-namespaces}

Un espace de noms est utilisé pour organiser d’autres balises. Elle peut être considérée comme la balise de niveau le plus bas et est généralement utilisée pour regrouper d’autres balises.

1. Pour créer un espace de noms, ouvrez la [console de balisage](#tagging-console) et sélectionnez le bouton **Créer** dans la barre d’outils, puis **Créer un espace de noms**.

   ![Boîte de dialogue Ajouter un espace de noms](/help/sites-cloud/administering/assets/add-namespace.png)

1. Fournissez les informations requises.

   * **Titre** - Titre de l’espace de noms affiché pour l’utilisateur dans l’interface utilisateur (facultatif)
   * **Nom** - Si un nom n’est pas spécifié, un nom de noeud valide est créé à partir du **titre**. Pour plus d’informations, consultez le document [AEM Tagging Framework](/help/implementing/developing/introduction/tagging-framework.md#tagid) .
   * **Description** - Description de l’espace de noms (facultatif)

1. Une fois que les informations requises ont été saisies, sélectionnez **Créer**.

L’espace de noms est créé. Dans la console Balisage, les espaces de noms se trouvent au niveau le plus bas (dans la colonne l’extrémité gauche de la console) et sont représentés par des icônes de dossier, reflétant leur nature de &quot;conteneur&quot; ou regroupement d’autres balises.

Vous pouvez désormais [créer de nouvelles balises](#creating-tags) dans cet espace de noms ou [gérer les balises existantes.](#managing-tags)

Un espace de noms ne doit pas contenir de sous-balises. Un espace de noms étant lui-même une balise, il peut être utilisé pour organiser votre contenu comme toute autre balise. Cependant, pour continuer à créer une taxonomie de balisage structurée, vous pouvez [créer des sous-balises](#creating-tags) dans cet espace de noms en fonction des exigences de votre projet.

### Création de balises {#creating-tags}

Les balises sont généralement ajoutées aux espaces de noms.

1. Pour créer une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez l’espace de noms dans lequel vous souhaitez créer la balise. Vous pouvez également sélectionner une autre balise pour créer une sous-balise en dessous.

1. Sélectionnez le bouton **Créer** sur la barre d’outils, puis **Créer une balise**.

1. La boîte de dialogue **Créer une balise** s’ouvre. Fournissez les informations requises pour la nouvelle balise.

   * **Titre** - Titre affiché de la balise (obligatoire).
   * **Nom** - Nom de la balise (obligatoire). Si aucun nom n’est spécifié, un nom de noeud valide est créé à partir du **titre**. Voir [ID de balise](/help/implementing/developing/introduction/tagging-framework.md#tagid).
   * **Description** - Description de la balise
   * **Chemin d’accès aux balises** : par défaut, l’espace de noms (ou la balise) que vous avez sélectionné dans la console de balisage. Vous pouvez le mettre à jour manuellement en appuyant ou en cliquant sur l’icône du sélecteur de chemin.

   ![Boîte de dialogue Créer une balise](assets/create-tag.png)

1. Sélectionnez **Envoyer**.

La balise est créée et la console est mise à jour pour afficher la nouvelle balise.

Les balises permettent la création flexible de votre propre taxonomie en fonction des besoins de votre organisation.

* Vous pouvez créer des balises enfants de balises existantes en sélectionnant la balise parente dans la console avant de créer la balise.
* Si vous créez une balise sans sélectionner un espace de noms ou une autre balise, vous créez effectivement un espace de noms.

### Publier des balises {#publishing-tags}

Comme pour la création d’un autre contenu dans AEM, une fois que vous avez créé une balise (ou un espace de noms), il existe uniquement dans l’environnement de création. Pour que vos balises soient disponibles pour vos utilisateurs, vous devez les publier.

1. Pour publier une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la ou les balises que vous souhaitez publier et, dans la barre d’outils, sélectionnez **Publish**.

   ![Sélectionner des balises dans la console](assets/select-tags.png)

1. La boîte de dialogue **Balise Publish** demande une confirmation pour publier les balises sélectionnées. Sélectionnez **Publier**.

   ![Fenêtre modale de confirmation de balise Publish](assets/publish-tag.png)

1. L’action de publication est confirmée par une boîte de dialogue **Success**.

   ![Boîte de dialogue de succès des balises Publish](assets/publish-tag-success.png)

Les balises sélectionnées sont mises en file d’attente pour publication. Tout comme le contenu de la page, seule la ou les balises sélectionnées sont publiées, qu’elles comportent ou non des sous-balises.

Pour publier une taxonomie entière (un espace de noms et des sous-balises), il est recommandé de créer un [package](/help/implementing/developing/tools/package-manager.md) de l’espace de noms (voir [Noeud racine de taxonomie](/help/implementing/developing/introduction/tagging-framework.md#taxonomy-root-node)).

<!--
Be sure to [apply permissions](#setting-tag-permissions) to the namespace before creating the package.
-->

## Gestion des balises {#managing-tags}

Il existe plusieurs actions que vous pouvez effectuer sur les balises et espaces de noms existants pour les gérer et les organiser. Il vous suffit de sélectionner une balise ou un espace de noms dans la [console de balisage](#tagging-console) pour afficher dans la barre d’outils les actions disponibles.

* [Afficher les propriétés](#viewing-tag-properties)
* [Modifier](#editing-tags)
* [Dépublier](#unpublishing-tags)
* [Références](#viewing-tag-references)
* [Déplacer](#moving-tags)
* [Fusionner](#merging-tags)
* [Supprimer](#deleting-tags)

Lorsque la barre d’outils dispose d’un espace suffisant, d’autres options sont disponibles derrière l’icône représentant des points de suspension.

### Affichage des propriétés de balise {#viewing-tag-properties}

Lorsqu’une balise unique, un espace de noms ou une autre balise est sélectionné dans la console de balisage, les détails de base de la balise sélectionnée, tels que l’heure de la dernière modification et la dernière publication, s’affichent dans la colonne située à gauche de la colonne de balise.

![Colonne Détails de la balise](assets/tag-details-column.png)

Vous pouvez afficher plus d’informations sur la balise, y compris le dernier à l’avoir publiée et le moment où vous la publiez, en basculant la console vers la vue **Propriétés**.

1. Pour afficher les propriétés d&#39;une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la balise dont vous souhaitez afficher les propriétés, puis, dans le rail de gauche, sélectionnez **Propriétés**.

   ![Sélectionner la vue de propriétés](assets/view-tag-properties.png)

1. Les propriétés détaillées de la balise sélectionnée s’affichent dans le rail de gauche.

   ![Affichage des propriétés de balise](assets/tag-properties.png)

Pour plus d’informations sur la sélection des modes d’affichage et du rail, voir [Manipulation de base](/help/sites-cloud/authoring/basic-handling.md#rail-selector).

### Modification des balises {#editing-tags}

Les balises et les espaces de noms peuvent être modifiés après la création.

1. Pour modifier une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la balise à modifier et, dans la barre d’outils, sélectionnez **Modifier**.

1. Apportez les modifications souhaitées. Vous pouvez modifier les éléments suivants :

   * **Titre**
   * **Description**
   * [**Localisation**](#managing-tags-in-different-languages)

1. Une fois les modifications effectuées, sélectionnez **Submit**.

Pour plus d’informations sur l’ajout de traductions, consultez la section [Gestion de balises dans différentes langues](#managing-tags-in-different-languages).

Si les modifications que vous avez apportées concernent une balise déjà publiée, vous pouvez [la republier.](#publishing-tags)

### Dépublication de balises {#unpublishing-tags}

Pour désactiver la balise sur votre instance d’auteur et la supprimer de votre instance de publication, vous pouvez la dépublier.

1. Pour annuler la publication d’une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la ou les balises dont vous souhaitez annuler la publication et, dans la barre d’outils, sélectionnez **Annuler la publication**.

   ![Sélectionner des balises dans la console](assets/select-tags.png)

1. La boîte de dialogue **Annuler la publication de la balise** demande une confirmation pour publier les balises sélectionnées. Sélectionnez **Publier**.

   ![Fenêtre modale de confirmation de balise Publish](assets/unpublish-tag.png)

1. L’action d’annulation de la publication est confirmée par une boîte de dialogue **Success**.

   ![Boîte de dialogue de succès des balises Publish](assets/unpublish-tag-success.png)

Les balises sélectionnées sont mises en file d’attente pour annulation de la publication. Si la balise sélectionnée est une balise conteneur, toutes ses balises enfants sont désactivées dans l’environnement de création et supprimées de l’environnement de publication.

### Affichage des références de balise {#viewing-tag-references}

Il peut s’avérer utile de déterminer le contenu appliqué à une balise particulière. Pour ce faire, utilisez la vue **Références** dans la console de balisage.

1. Pour afficher les références d’une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la balise dont vous souhaitez afficher les références et, dans le rail de gauche, sélectionnez **Références**.

   ![Sélectionner la vue de propriétés](assets/view-tag-references.png)

1. Le nombre total de références pour la balise sélectionnée s’affiche dans le rail de gauche.

   ![Affichage des références de balise](assets/tag-references.png)

1. Sélectionnez le nombre de références de balise pour afficher la liste détaillée du contenu affecté à la balise.

   ![Affichage du détail des références de la balise](assets/tag-references-detail.png)

Passez la souris ou sélectionnez un contenu de référence dans la liste pour afficher le chemin d’accès complet du contenu.

Pour plus d’informations sur la sélection des modes d’affichage et du rail, voir [Manipulation de base](/help/sites-cloud/authoring/basic-handling.md#rail-selector).

### Déplacement des balises {#moving-tags}

Il peut être nécessaire de nettoyer ou de réorganiser votre taxonomie de balisage en déplaçant une balise vers un nouvel emplacement ou en la renommant.

>[!TIP]
>
>Il est recommandé que seuls les administrateurs soient autorisés à déplacer et renommer des balises.

1. Pour déplacer ou renommer une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la balise que vous souhaitez déplacer ou renommer et sélectionnez **Déplacer** dans la barre d’outils.

1. Dans la boîte de dialogue **Déplacer la balise**, spécifiez la propriété à modifier.

   * **Renommer en** - Le nouveau nom que vous souhaitez donner à la balise
      * Ce champ est prérenseigné avec le nom actuel de la balise.
      * Ne modifiez pas la balise si vous souhaitez uniquement la déplacer et ne pas la renommer.
   * **Déplacer vers** - Emplacement où vous souhaitez déplacer la balise.
      * Ce champ est prérenseigné avec l’emplacement actuel de la balise.
      * Ne modifiez pas la balise si vous souhaitez uniquement la renommer et ne pas la déplacer.

   ![Déplacer la balise](assets/move-tag.png)

1. Sélectionnez **Envoyer**.

La balise est renommée et/ou déplacée vers son nouvel emplacement. Si la balise sélectionnée est une balise conteneur, le fait de la déplacer déplace également toutes les balises enfants.

### Fusion de balises {#merging-tags}

Si votre taxonomie de balisage comporte des doublons ou des balises similaires, il peut être utile de les fusionner. Lorsque la balise `A` est fusionnée en balise `B`, toutes les pages balisées avec la balise `A` sont balisées avec la balise `B` et la balise `A` n’est plus disponible pour les auteurs.

1. Pour fusionner deux balises, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la balise à fusionner dans une autre balise, puis sélectionnez **Fusionner** dans la barre d’outils.

1. Dans la boîte de dialogue **Fusionner la balise**, sélectionnez l’icône **Parcourir** du champ **Fusionner dans** pour spécifier dans quelle balise vous souhaitez fusionner la balise sélectionnée.

   ![Boîte de dialogue Fusionner la balise](assets/merge-tag.png)

1. Sélectionnez **Envoyer**.

La balise sélectionnée dans la console est fusionnée dans la balise spécifiée dans la boîte de dialogue. Lorsqu’une balise référencée est déplacée ou fusionnée, elle n’est pas physiquement supprimée, de sorte qu’il soit possible de conserver les références. Pour plus d’informations, voir [AEM Tagging Framework](/help/implementing/developing/introduction/tagging-framework.md#moving-and-merging-tags) .

### Suppression des balises {#deleting-tags}

Si votre taxonomie de balisage change et rend une balise ou un espace de noms inutile, il peut être supprimé.

1. Pour supprimer une balise, ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la balise à supprimer, puis sélectionnez **Supprimer** dans la barre d’outils.

1. La boîte de dialogue **Supprimer la balise** demande une confirmation pour supprimer la ou les balises sélectionnées. Sélectionnez **Supprimer**.

   ![Fenêtre modale de confirmation de suppression de balise](assets/delete-tag.png)

1. AEM vérifie que la balise n’est pas référencée.

   1. Si aucune référence n’est trouvée, AEM demande une confirmation finale de suppression. Sélectionnez **Supprimer**

      ![Aucune référence trouvée](assets/no-references-found.png)

   1. Si des références sont trouvées, AEM les présente et demande une confirmation finale de suppression.

      ![Références trouvées](assets/references-found.png)

Les balises sélectionnées sont supprimées et définitivement supprimées de l’environnement de création. Si la balise a été publiée, elle est également supprimée de l’environnement de publication. Si la balise sélectionnée est une balise conteneur, toutes ses balises enfants sont également supprimées.

<!--

## Setting Tag Permissions {#setting-tag-permissions}

Tag permissions are ['secure (by default)'](/help/sites-administering/production-ready.md); a best practice for the publish environment that requires read permission to be explicitly allowed for tags. Bascially, this is done by creating a package of the Tag Namespace after permissions have been set on author, and installing the package on all publish instances.

* on author instance

    * sign in with administrative privileges
    * access the [Security Console](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console),

        * for example, browse to http://localhost:4502/useradmin

    * in the left pane, select the group (or user) for which [read permission](/help/sites-administering/security.md#permissions) is to be granted
    * in the right pane, locate the **Path **to the Tag Namespace

        * for example, `/content/cq:tags/mycommunity`

    * select the `checkbox`in the **Read** column
    * select **Save**

![Setting tag permissions](assets/chlimage_1-204.png)

* ensure all publish instances have same permissions

    * one approach is to [create a package](/help/sites-administering/package-manager.md#package-manager) of the namespace on author

        * on `Advanced` tab, for `AC Handling` select `Overwrite`

    * replicate the package

        * choose `Replicate` from package manager

-->

## Gestion des balises dans différentes langues {#managing-tags-in-different-languages}

La propriété `title` d’une balise peut être traduite en plusieurs langues. Une fois traduit, le titre de la balise approprié peut s’afficher en fonction de l’utilisateur ou de la langue du contenu.

Supposons que nous ayons une balise appelée `Animals` que nous voulons traduire en allemand et en français.

1. Ouvrez la [console de balisage.](#tagging-console)

1. Sélectionnez la balise à traduire, puis sélectionnez **Modifier** dans la barre d’outils.

1. Dans la boîte de dialogue **Modifier la balise**, dans la colonne **Localisation**, sélectionnez la langue cible, par exemple l’allemand.

1. Dans le champ **German** qui s’affiche, indiquez le titre traduit.

1. Répétez les deux étapes précédentes pour le français.

   ![Traduire les titres de balises](assets/translate-tag.png)

1. Sélectionnez **Envoyer**.

Pour les pages de contenu, la langue choisie pour la balise provient de la langue de la page, le cas échéant.

Toutefois, dans l’environnement de création, AEM utilise le paramètre de langue de l’utilisateur. Ainsi, dans la console de balisage, pour la balise `Animals`, `Animaux` s’affiche pour un utilisateur qui définit la langue sur le français dans ses propriétés utilisateur.

Pour ajouter une nouvelle langue à la boîte de dialogue, reportez-vous au document [Construire le balisage dans AEM applications](/help/implementing/developing/introduction/tagging-applications.md#adding-a-new-language-to-the-edit-tag-dialog)

>[!TIP]
>
>Si vous souhaitez en savoir plus sur les fonctions de localisation AEM, voir [Traduction de votre contenu pour des sites multilingues](/help/sites-cloud/administering/translation/overview.md).

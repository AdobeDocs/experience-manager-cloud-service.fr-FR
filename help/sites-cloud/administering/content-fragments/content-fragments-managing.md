---
title: Gérer des fragments de contenu
description: Découvrez comment utiliser la console Fragments de contenu pour gérer vos fragments de contenu AEM, pour la création de pages ou comme base de votre contenu headless.
feature: Content Fragments
role: User
exl-id: fc4497cb-85ac-4d2d-aca4-588541266f0b
source-git-commit: 944665bc7cac1f00811187a508a18800c3d73f2a
workflow-type: tm+mt
source-wordcount: '1947'
ht-degree: 93%

---

# Gérer des fragments de contenu {#managing-content-fragments}

Découvrez comment utiliser la console **Fragments de contenu** pour gérer vos fragments de contenu AEM. Ils peuvent être utilisés pour la création de pages ou comme base de votre contenu headless.

Après avoir défini vos [modèles de fragment de contenu](#creating-a-content-model), vous pouvez les utiliser pour [créer vos fragments de contenu](#creating-a-content-fragment).

L’[éditeur de fragment de contenu](#opening-the-fragment-editor) fournit différents [modes](#modes-in-the-content-fragment-editor) vous permettant :

* de [modifier du](#editing-the-content-of-your-fragment) contenu et de [gérer des variations ;](#creating-and-managing-variations-within-your-fragment)
* [d’annoter votre fragment ;](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [d’associer du contenu à votre fragment ;](#associating-content-with-your-fragment)
* [de configurer des métadonnées ;](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [d’affcher l’arborescence de la structure ;](/help/sites-cloud/administering/content-fragments/content-fragments-structure-tree.md)
* [de générer un aperçu de la représentation JSON.](/help/sites-cloud/administering/content-fragments/content-fragments-json-preview.md)


>[!NOTE]
>
>Il est possible d’utiliser les fragments de contenu comme suit :
>
>* lors de la création de pages ; voir [Création de pages avec des fragments de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
>* pour la [Diffusion de contenu découplé utilisant des fragments de contenu avec GraphQL](/help/sites-cloud/administering/content-fragments/content-fragments-graphql.md).


>[!NOTE]
>
>Les fragments de contenu sont stockés sous forme de **ressources**. Ils sont principalement gérés à partir de la console **Fragments de contenu** mais peuvent également être gérés à partir de la console **Ressources**.

## Console Fragments de contenu {#content-fragments-console}

La console Fragments de contenu permet d’accéder directement à vos fragments et aux tâches associées. Pour plus d’informations, voir :

* [Structure et gestion de base de la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#basic-structure-handling-content-fragments-console)

* [Informations fournies sur vos fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#information-content-fragments)

* [Actions pour un fragment de contenu dans la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#actions-selected-content-fragment)

* [Personnalisation des colonnes disponibles dans la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#select-available-columns)

* [Rechercher et filtrer dans la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#filtering-fragments)

## Créer des fragments de contenu {#creating-content-fragments}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="Créer un contenu"
>abstract="En vous basant sur les modèles que vous avez créés dans le module 1, vous apprendrez à créer du contenu qui peut être utilisé pour la création de pages ou comme base de votre contenu sans en-tête."

### Création d’un modèle de contenu {#creating-a-content-model}

Les [modèles de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-models.md) peuvent être activés et créés, avant de créer des fragments de contenu avec le contenu structuré.

### Création d’un fragment de contenu {#creating-a-content-fragment}

Pour créer un fragment de contenu :

1. Dans la console **Fragments de contenu**, sélectionnez **Créer** (en haut à droite).

   >[!NOTE]
   >
   >Pour prédéfinir l’emplacement du nouveau fragment, vous pouvez accéder au dossier dans lequel vous souhaitez créer le fragment ou spécifier l’emplacement pendant le processus de création.

1. La boîte de dialogue **Nouveau fragment de contenu** s’ouvre. À partir d’ici, vous pouvez spécifier les éléments suivants :

   * **Emplacement** : l’emplacement actuel sera renseigné automatiquement, mais vous pouvez sélectionner un autre emplacement si nécessaire.
   * **Modèle de fragment de contenu** : sélectionnez le modèle à utiliser comme base du fragment dans la liste déroulante.
   * **Titre**
   * **Nom** : le nom sera automatiquement renseigné en fonction du **Titre**, mais vous pouvez le modifier si nécessaire.
   * **Description**

   ![Boîte de dialogue Nouveau fragment de contenu](assets/cfm-managing-new-cf-01.png)

1. Sélectionnez **Créer** ou **Créer et ouvrir** pour conserver votre définition.

## Statuts des fragments de contenu {#statuses-content-fragments}

Au cours de son existence, un fragment de contenu peut avoir plusieurs statuts, comme indiqué dans la [console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) :

* **Nouveau**
Un nouveau fragment de contenu a été créé, mais n’a jamais été modifié, ni ouvert, dans l’éditeur de fragment de contenu.
* **Brouillon**
Quelqu’un a modifié ou ouvert le (nouveau) fragment de contenu dans l’éditeur de fragment de contenu, mais il n’a pas encore été publié.
* **Publié**
Le fragment de contenu a été publié.
* **Modifié**
Le fragment de contenu a été modifié après sa publication (mais avant de publier la modification).
* **Non publié**
La publication du fragment de contenu a été annulée.

## Ouverture de l’éditeur de fragments {#opening-the-fragment-editor}

Pour ouvrir votre fragment à des fins de modification :

>[!CAUTION]
>
>Pour modifier un fragment de contenu, vous devez disposer des [autorisations appropriées](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions). Si vous rencontrez des problèmes, contactez votre administrateur système.

1. Utilisez la console **Fragments de contenu** afin de naviguer jusqu’à l’emplacement de votre fragment de contenu.
1. Ouvrez le fragment à modifier en le sélectionnant, puis en cliquant sur **Ouvrir** dans la barre d’outils.

1. L’éditeur de fragment s’ouvre alors. Apportez les modifications nécessaires :

   ![éditeur de fragment](assets/cfm-managing-03.png)

1. Après avoir apporté vos modifications, cliquez sur **Enregistrer**, **Enregistrer et fermer** ou **Fermer** selon les besoins.

   >[!NOTE]
   >
   >L’option **Enregistrer et fermer** est disponible dans la liste déroulante **Enregistrer**.

   >[!NOTE]
   >
   >Les options **Enregistrer et fermer** et **Fermer** vous font quitter l’éditeur. Pour plus d’informations sur le fonctionnement des différentes options avec les fragments de contenu, voir [Enregistrer, Fermer et Versions](#save-close-and-versions).

## Modes et actions dans l’éditeur de fragment de contenu {#modes-actions-content-fragment-editor}

L’éditeur de fragments de contenu comporte différents modes et actions.

### Modes dans l’éditeur de fragment de contenu {#modes-in-the-content-fragment-editor}

Naviguez entre les différents modes en utilisant les icônes du panneau latéral :

* Variations : [Modification du contenu](#editing-the-content-of-your-fragment) et [Gestion des variations](#creating-and-managing-variations-within-your-fragment)

* [Annotations](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Contenu associé](#associating-content-with-your-fragment)
* [Métadonnées](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [Arborescence de la structure](/help/sites-cloud/administering/content-fragments/content-fragments-structure-tree.md)
* [Aperçu](/help/sites-cloud/administering/content-fragments/content-fragments-json-preview.md)

![modes](assets/cfm-managing-04.png)

### Barre d’outils d’actions dans l’éditeur de fragment de contenu {#toolbar-actions-in-the-content-fragment-editor}

Certaines fonctions de la barre d’outils supérieure sont disponibles dans différents modes :

![modes](assets/cfm-managing-top-toolbar.png)

* Un message s’affiche si le fragment est déjà référencé dans une page de contenu. Vous pouvez **Fermer** le message.

* Le panneau latéral peut être masqué/affiché en appuyant sur l’icône **Activer/désactiver le panneau latéral**.

* Sous le nom du fragment, vous pouvez voir le nom du [Modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-models.md) utilisé pour créer le fragment actif :

   * Le nom est également un lien servant à ouvrir l’éditeur de modèles.

* Voir le statut du fragment, par exemple, les informations relatives à la date et à l’heure de création, de modification ou de publication. Le statut est également codé par couleur :

   * **Nouveau** : gris
   * **Version préliminaire** : bleu
   * **Publié** : vert
   * **Modifié** : orange
   * **Désactivé** : rouge

* **Enregistrer** permet d’accéder à l’option **Enregistrer et fermer**.

* La liste déroulante marquée des trois points (**...**) donne accès à des actions supplémentaires :
   * **Mettre à jour les références de page**
      * Cette option met à jour toutes les références de la page.
   * **[Publication rapide](#publishing-and-referencing-a-fragment)**
   * **[Gérer la publication](#publishing-and-referencing-a-fragment)**

<!--
This updates any page references and ensures that the Dispatcher is flushed as required. -->

## Enregistrer, Fermer et Versions {#save-close-and-versions}

>[!NOTE]
>
>Les versions peuvent également être [créées, comparées et rétablies à partir de la chronologie](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

L’éditeur possède différentes options :

* **Enregistrer** et **Enregistrer et fermer**

   * **Enregistrer** enregistrera les dernières modifications et vous resterez dans l’éditeur.
   * **Enregistrer et fermer** enregistrer les dernières modifications et vous permet de quitter l’éditeur.

   >[!CAUTION]
   >
   >Pour modifier un fragment de contenu, vous devez disposer des [autorisations appropriées](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions). Si vous rencontrez des problèmes, contactez votre administrateur système.

   >[!NOTE]
   >
   >Pour rester dans l’éditeur, il suffit d’apporter une série de modifications avant d’enregistrer.

   >[!CAUTION]
   >
   >En plus de simplement enregistrer vos modifications, ces actions mettent également à jour les références éventuelles et s’assurent que le Dispatcher est nettoyé si nécessaire. Le traitement de ces modifications peut prendre un certain temps. Cela peut donc avoir un impact sur les performances d’un système étendu/complexe/fortement chargé.
   >
   >Prenez cela en compte lorsque vous exécutez **Enregistrer et fermer** puis rouvrez aussitôt l’éditeur de fragments afin d’apporter d’autres modifications et de les enregistrer.

* **Fermer**

   Quittera l’éditeur sans enregistrer les dernières modifications (c’est-à-dire effectuées depuis le dernier **Enregistrer**).

Lorsque vous modifiez votre fragment de contenu, AEM crée automatiquement des versions pour que le contenu précédent puisse être restauré si vous annulez les modifications (en cliquant sur **Fermer** sans enregistrer) :

1. Lorsqu’un fragment de contenu est ouvert pour modification, AEM vérifie l’existence d’un jeton basé sur les cookies indiquant s’il existe une *session de modification* :

   1. Si ce jeton est trouvé, le fragment est considéré comme faisant partie de la session de modification existante.
   2. Si le jeton *n’est pas* disponible et que l’utilisateur commence à modifier le contenu, une version est créée et un jeton est envoyé au client pour cette nouvelle session de modification, où il est enregistré dans un cookie.

2. Lors d’une session de modification *active*, le contenu en cours de modification est automatiquement enregistré toutes les 600 secondes (par défaut).

   >[!NOTE]
   >
   >L’intervalle d’enregistrement automatique est configurable à l’aide du mécanisme `/conf`.
   >
   >Valeur par défaut, voir :
   >  `/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

3. Si l’utilisateur choisit d’annuler la modification, la version créée au début de la session de modification est restaurée et le jeton est supprimé afin de mettre fin à la session de modification.
4. Si l’utilisateur choisit d’**enregistrer** les modifications apportées, les éléments/variations mis à jour sont conservés et le jeton est supprimé pour mettre fin à la session de modification.

## Modification du contenu du fragment {#editing-the-content-of-your-fragment}

Une fois que vous avez ouvert le fragment, vous pouvez utiliser l’onglet [Variations](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md) pour créer votre contenu.

## Création et gestion de variations dans un fragment {#creating-and-managing-variations-within-your-fragment}

Une fois que vous avez créé le contenu maître, vous pouvez créer et gérer des [Variations](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md) de ce contenu.

## Association de contenu au fragment {#associating-content-with-your-fragment}

Vous pouvez également [associer du contenu](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) à un fragment. Cela fournit une liaison pour que les ressources (c’est-à-dire les images) puissent éventuellement être utilisées avec le fragment lorsqu’il est ajouté à une page de contenu.

## Affichage et modification des métadonnées (propriétés) du fragment {#viewing-and-editing-the-metadata-properties-of-your-fragment}

Vous pouvez afficher et modifier les propriétés d’un fragment à l’aide de l’onglet [Métadonnées](/help/sites-cloud/administering/content-fragments/content-fragments-metadata.md).

## Publication et référencement d’un fragment {#publishing-and-referencing-a-fragment}

>[!CAUTION]
Si votre fragment est basé sur un modèle, vous devez vous assurer que le [modèle a été publié](/help/sites-cloud/administering/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model).
Si vous publiez un fragment de contenu pour lequel le modèle n’a pas encore été publié, une liste de sélection indique cela, ainsi que le fait que le modèle sera publié avec le fragment.

Les fragments de contenu doivent être publiés pour être utilisés dans l’environnement de publication. Pour ce faire, utilisez la fonctionnalité Ressources standard.

* À partir de l’option **Publier** dans la barre d’outils de la [console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#actions-selected-content-fragment).
   * **Maintenant** : après confirmation, le fragment sera publié immédiatement.
   * **Planning** : vous pouvez sélectionner la date et l’heure de publication du fragment.

   Si nécessaire, vous devrez spécifier la **Date d’activation** et les références à publier. Par exemple :
   ![Boîte de dialogue Publier](assets/cfm-publish-01.png)

* À partir de l’[éditeur de fragment de contenu](#toolbar-actions-in-the-content-fragment-editor).
   * [**Publication rapide**](/help/assets/manage-publication.md#quick-publish)
   * [**Gérer la publication**](/help/assets/manage-publication.md#manage-publication)

De plus, lorsque vous [publiez une page qui utilise ce fragment](/help/sites-cloud/authoring/fundamentals/content-fragments.md#publishing), celui-ci est répertorié dans les références de la page.

>[!CAUTION]
Une fois qu’un fragment a été publié et/ou référencé, AEM affiche un avertissement lorsqu’un auteur ouvre à nouveau ce fragment en mode d’édition. Il s’agit de signaler que les modifications apportées au fragment seront également répercutées sur les pages référencées.

## Annuler la publication d’un fragment {#unpublishing-a-fragment}

Pour annuler la publication de fragments de contenu, sélectionnez un ou plusieurs fragments, puis cliquez sur **Annuler la publication**.

>[!NOTE]
L’action **Annuler la publication** est visible lorsque des fragments publiés sont disponibles.

>[!CAUTION]
Si le fragment est déjà référencé à partir d’un autre fragment ou d’une page, alors un message d’avertissement s’affiche et vous devez confirmer que vous souhaitez poursuivre.

## Suppression d’un fragment {#deleting-a-fragment}

Pour supprimer un fragment :

1. Dans la console **Fragments de contenu**, naviguez jusqu’à l’emplacement de votre fragment de contenu.
2. Sélectionnez le fragment.

   >[!NOTE]
   L’action **Supprimer** n’est pas proposée comme action rapide.

3. Sélectionnez **Supprimer** dans la barre d’outils.
4. Confirmez l’action **Supprimer**.

   >[!CAUTION]
   Si le fragment est déjà référencé à partir d’un autre fragment ou d’une page, un message d’avertissement s’affiche et vous devez confirmer que vous souhaitez procéder à une **suppression forcée**. Le fragment et son composant de fragment de contenu seront supprimés de toutes les pages de contenu.

## Recherche des références parentes du fragment {#parent-references-fragment}

Les détails des références parentes sont accessibles à partir de la **Références** de la colonne [Console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#information-content-fragments).

## Recherche de copies de langue du fragment {#language-copies-fragment}

Les détails des copies de langue sont accessibles à partir du **Langue** de la colonne [Console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md#information-content-fragments).

## Chronologie pour les fragments de contenu {#timeline-for-content-fragments}

>[!NOTE]
Cette fonctionnalité n’est disponible que dans la console **Ressources**.

Outre les options standard, la [Chronologie](/help/assets/manage-digital-assets.md#timeline) fournit les informations et les actions spécifiques aux fragments de contenu :

* Affichage des informations sur les versions, commentaires et annotations
* Actions pour les versions

   * **[Revenir à cette version](#reverting-to-a-version)** (sélectionner un fragment existant, puis une version spécifique)

   * **[Comparer à actuel](#comparing-fragment-versions)** (sélectionner un fragment existant, puis une version spécifique)

   * Ajouter une **étiquette** et/ou un **commentaire** (sélectionner un fragment existant, puis une version spécifique)

   * **Enregistrer comme version** (sélectionner un fragment existant, puis la flèche du haut au bas de la chronologie)

* Actions pour les annotations

   * **Supprimer**

>[!NOTE]
Les commentaires :
* Une fonctionnalité standard pour toutes les ressources
* Réalisés dans la chronologie
* Liés à la ressource de fragment
>
Les annotations (pour les fragments de contenu) sont :
* Entrées dans l’éditeur de fragments
* Spécifiques à un segment de texte sélectionné au sein du fragment
>


Par exemple :

![chronologie](assets/cfm-managing-05.png)

## Comparaison des versions de fragments {#comparing-fragment-versions}

>[!NOTE]
Cette fonctionnalité n’est disponible que dans la console **Ressources**.

L’action de **comparer à la version actuelle** est disponible dans la [chronologie](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) après avoir sélectionné une version spécifique.

Cette opération va ouvrir :

* la version **actuelle** (la plus récente) (à gauche) ;

* la version sélectionnée **v&lt;*x.y*>** (à droite).

Elles sont affichées dans des versions côte à côte dans lesquelles :

* les différences sont mises en surbrillance ;

   * le texte supprimé est en rouge ;
   * le texte inséré est en vert ;
   * le texte remplacé est en bleu.

* L’icône en plein écran permet d’ouvrir l’une ou l’autre version seule, puis de revenir en mode parallèle.
* Vous pouvez **rétablir** la version spécifique
* **Terminé** vous ramène à la console

>[!NOTE]
Vous ne pouvez pas modifier le contenu du fragment lors de la comparaison des fragments.

![comparaison](assets/cfm-managing-06.png)

## Restauration vers une version spécifique   {#reverting-to-a-version}

>[!NOTE]
Cette fonctionnalité n’est disponible que dans la console **Ressources**.

Vous pouvez restaurer vers une version spécifique de votre fragment :

* Directement à partir de la [chronologie](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

   Sélectionnez la version requise, puis l’action **Revenir à cette version**.

* Lors de la [comparaison d’une version à la version actuelle](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#comparing-fragment-versions), vous pouvez **restaurer** la version sélectionnée.

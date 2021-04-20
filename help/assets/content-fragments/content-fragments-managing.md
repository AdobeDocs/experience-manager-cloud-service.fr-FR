---
title: Gestion des fragments de contenu
description: Découvrez comment utiliser la console Ressources pour gérer vos AEM Fragments de contenu, à la base de votre contenu sans en-tête.
feature: Content Fragments
role: Business Practitioner
exl-id: 333ad877-db2f-454a-a3e5-59a936455932
translation-type: tm+mt
source-git-commit: 114b38142f01b56652a7b840501f7420fdc25562
workflow-type: tm+mt
source-wordcount: '1748'
ht-degree: 78%

---

# Gestion des fragments de contenu {#managing-content-fragments}

Découvrez comment utiliser la console Ressources pour gérer vos AEM Fragments de contenu, à la base de votre contenu sans en-tête.

Après avoir défini vos [modèles de fragments de contenu](#creating-a-content-model), vous pouvez les utiliser pour [créer vos fragments de contenu](#creating-a-content-fragment).

L&#39;[éditeur de fragments de contenu](#opening-the-fragment-editor) fournit divers [modes](#modes-in-the-content-fragment-editor) pour vous permettre d&#39;effectuer les opérations suivantes :

* [Modifier le ](#editing-the-content-of-your-fragment) contenu et  [gérer les variantes](#creating-and-managing-variations-within-your-fragment)
* [Annoter votre fragment](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Association de contenu à votre fragment](#associating-content-with-your-fragment)
* [Configuration des métadonnées](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [Vue de l&#39;arborescence de structure](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Prévisualisation de la représentation JSON](/help/assets/content-fragments/content-fragments-json-preview.md)


>[!NOTE]
>
>Il est possible d’utiliser les fragments de contenu comme suit :
>
>* lors de la création de pages ; voir [Création de pages avec des fragments de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
>* pour la [Diffusion de contenu découplé utilisant des fragments de contenu avec GraphQL](/help/assets/content-fragments/content-fragments-graphql.md).


>[!NOTE]
>
>Les fragments de contenu sont stockés en tant que **Ressources**, et ils sont donc principalement gérés par l’intermédiaire de la console **Ressources**.

## Création de fragments de contenu {#creating-content-fragments}

### Création d’un modèle de contenu {#creating-a-content-model}

Les [modèles de fragments de contenu](/help/assets/content-fragments/content-fragments-models.md) peuvent être activés et créés, avant de créer des fragments de contenu avec le contenu structuré.

### Création d’un fragment de contenu {#creating-a-content-fragment}

La méthode de création d’un fragment de contenu est la suivante :

1. Accédez au dossier **Ressources** dans lequel vous souhaitez créer le fragment.
1. Pour ouvrir l’assistant, sélectionnez **Créer**, puis **Fragment de contenu**.
1. La première étape de l’assistant nécessite de spécifier la base du nouveau fragment.

   * [Modèle](/help/assets/content-fragments/content-fragments-models.md) : utilisé pour créer un fragment qui nécessite du contenu structuré, par exemple, le modèle **Adventure**.

      * Tous les modèles disponibles s’affichent.

   Après la sélection, cliquez ou appuyez sur **Suivant** pour continuer.

   ![base du fragment](assets/cfm-managing-01.png)

1. Dans l’étape **Propriétés**, spécifiez :

   * **De base**

      * **Titre**

         Titre du fragment.

         Obligatoire.

      * **Description**

      * **Balises**
   * **Avancé**

      * **Nom**

         Nom utilisé pour former l’URL.

         Obligatoire, il sera dérivé automatiquement du titre, mais il peut être modifié.


1. Sélectionnez **Créer** pour terminer l’action, puis **ouvrez** le fragment en mode d’édition ou revenez à la console en sélectionnant **Terminé**.

   >[!NOTE]
   >En mode **Liste** de la console, vous pouvez mettre à jour les **Paramètres d’affichage** pour activer la colonne **Modèle de fragment de contenu**.

## Actions pour un fragment de contenu dans la console de ressources {#actions-for-a-content-fragment-assets-console}

Dans la console **Ressources**, différentes actions sont disponibles pour vos fragments de contenu, soit :

* dans la barre d’outils : une fois le fragment sélectionné, toutes les actions appropriées sont disponibles ;
* sous forme d’[actions rapides](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions) : un sous-ensemble d’actions disponibles pour les différentes cartes de fragments.

![actions](assets/cfm-managing-02.png)

Sélectionnez le fragment pour afficher la barre d’outils avec les actions applicables :

* **Retraiter les éléments**
* **Créer**
* **Télécharger**

   * Enregistrez le fragment sous forme d’un fichier ZIP. Vous pouvez indiquer si vous souhaitez inclure des éléments, des variations ou des métadonnées.

* **Passage en caisse**
* **Propriétés**

   * Permet d’afficher et/ou de modifier les métadonnées du fragment.

* **Modifier**

   * Permet [d’ouvrir le fragment afin d’en modifier le contenu](/help/assets/content-fragments/content-fragments-variations.md) ainsi que ses variations, contenu, métadonnées et éléments associés.

* **Publication rapide**
* **Gérer la publication**
* **Gérer les balises**
* **À la collection**
* **Copier** (et **coller**)
* **Déplacer**
* **Supprimer**

>[!NOTE]
>
>La plupart de ces actions sont [standard pour Assets](/help/assets/manage-digital-assets.md) et/ou l’[application de bureau AEM](https://helpx.adobe.com/fr/experience-manager/desktop-app/aem-desktop-app.html).

## Ouverture de l’éditeur de fragments {#opening-the-fragment-editor}

Pour ouvrir votre fragment à des fins de modification :

>[!CAUTION]
>
>Pour modifier un fragment de contenu, vous devez disposer des [autorisations appropriées](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions). Si vous rencontrez des problèmes, contactez votre administrateur système.

>[!CAUTION]
>
>Pour modifier un fragment de contenu, vous devez disposer des autorisations appropriées. Si vous rencontrez des problèmes, contactez votre administrateur système.

1. Utilisez la console **Assets** afin de naviguer jusqu’à l’emplacement de votre fragment de contenu.
1. Ouvrez le fragment en mode édition, en effectuant l’une des opérations suivantes :

   * Cliquez/appuyez sur le fragment ou le lien de fragment (selon l’affichage console).
   * Sélectionnez le fragment, puis cliquez sur **Modifier** dans la barre d’outils.

1. L’éditeur de fragments s’ouvre. Effectuez les modifications nécessaires :

   ![éditeur de fragment](assets/cfm-managing-03.png)

1. Après avoir apporté des modifications, utilisez **Save**, **Save &amp; close** ou **Close**, selon les besoins.

   >[!NOTE]
   >
   >**Save &amp;** close est disponible via la  **** liste déroulante des options.

   >[!NOTE]
   >
   >**Enregistrer et fermer** et **Fermer** quitteront l’éditeur. Pour plus d’informations sur le fonctionnement des différentes options pour les fragments de contenu, voir [Enregistrer, fermer et versions](#save-close-and-versions).

## Modes et actions dans l’éditeur de fragment de contenu {#modes-actions-content-fragment-editor}

L’éditeur de fragments de contenu comporte différents modes et actions.

### Modes dans l’éditeur de fragment de contenu {#modes-in-the-content-fragment-editor}

Naviguez entre les différents modes en utilisant les icônes du panneau latéral :

* Variations : [Modification du contenu](#editing-the-content-of-your-fragment) et [Gestion des variations](#creating-and-managing-variations-within-your-fragment)

* [Annotations](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Contenu associé](#associating-content-with-your-fragment)
* [Métadonnées](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [Arborescence de la structure](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Aperçu](/help/assets/content-fragments/content-fragments-json-preview.md)

![modes](assets/cfm-managing-04.png)

### Actions de la barre d’outils dans l’éditeur de fragments de contenu {#toolbar-actions-in-the-content-fragment-editor}

Certaines fonctions de la barre d’outils supérieure sont disponibles dans différents modes :

![modes](assets/cfm-managing-top-toolbar.png)

* Un message s’affiche si le fragment est déjà référencé dans une page de contenu. Vous pouvez **Fermer** le message.

* Le panneau latéral peut être masqué/affiché en appuyant sur l’icône **Activer/désactiver le panneau latéral**.

* Sous le nom du fragment, vous pouvez voir le nom du [Modèle de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md) utilisé pour créer le fragment actif :

   * Le nom est également un lien servant à ouvrir l’éditeur de modèles.

* Voir l’état du fragment, par exemple, les informations relatives à la date et à l’heure de création, de modification ou de publication. L’état est également codé par couleur :

   * **Nouveau** : gris
   * **Version préliminaire** : bleu
   * **Publié** : vert
   * **Modifié** : orange
   * **Désactivé** : rouge

* **** Savepermet d’accéder à l’option  **Enregistrer et** fermer.

* Les trois points (**...La liste déroulante**) permet d’accéder à d’autres actions :
   * **Mettre à jour les références de page**
      * Ceci met à jour toutes les références de page.
   * **[Publication rapide](#publishing-and-referencing-a-fragment)**
   * **[Gérer la publication](#publishing-and-referencing-a-fragment)**

<!--
This updates any page references and ensures that the Dispatcher is flushed as required. -->

## Enregistrer, fermer et versions {#save-close-and-versions}

>[!NOTE]
>
>Les versions peuvent également être [créées, comparées et rétablies à partir de la chronologie](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

L’éditeur propose différentes options :

* **** Enregistrer et  **Enregistrer et fermer**

   * **** Saveenregistrer les dernières modifications et rester dans l&#39;éditeur.
   * **Enregistrer et** fermer enregistrera les dernières modifications et quittera l&#39;éditeur.

   >[!CAUTION]
   >
   >Pour modifier un fragment de contenu, vous devez disposer des [autorisations appropriées](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions). Si vous rencontrez des problèmes, contactez votre administrateur système.

   >[!NOTE]
   >
   >Il est possible de rester dans l&#39;éditeur, en effectuant une série de modifications, avant d&#39;enregistrer.

   >[!CAUTION]
   >
   >En plus d&#39;enregistrer simplement vos modifications, les actions mettent également à jour les références et s&#39;assurent que le Répartiteur est vidé selon les besoins. Le traitement de ces modifications peut prendre un certain temps. Cela peut donc avoir un impact sur les performances d’un système étendu/complexe/fortement chargé.
   >
   >N’oubliez pas ce point lorsque vous utilisez **Enregistrer et fermer**, puis que vous entrez de nouveau rapidement dans l’éditeur de fragments pour effectuer et enregistrer d’autres modifications.

* **Fermer**

   Quitte l&#39;éditeur sans enregistrer les dernières modifications (c&#39;est-à-dire depuis le dernier **Enregistrer**).

Lors de la modification de votre fragment de contenu, AEM crée automatiquement des versions pour vous assurer que le contenu précédent peut être restauré si vous annulez vos modifications (en utilisant **Fermer** sans enregistrer) :

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

3. Si l’utilisateur annule la modification, la version créée au début de la session de modification est restaurée et le jeton est supprimé pour terminer la session de modification.
4. Si l’utilisateur choisit d’**enregistrer** les modifications apportées, les éléments/variations mis à jour sont conservés et le jeton est supprimé pour mettre fin à la session de modification.

## Modification du contenu du fragment {#editing-the-content-of-your-fragment}

Une fois que vous avez ouvert le fragment, vous pouvez utiliser l’onglet [Variations](/help/assets/content-fragments/content-fragments-variations.md) pour créer votre contenu.

## Création et gestion de variations dans un fragment  {#creating-and-managing-variations-within-your-fragment}

Une fois que vous avez créé le contenu maître, vous pouvez créer et gérer des [Variations](/help/assets/content-fragments/content-fragments-variations.md) de ce contenu.

## Association de contenu au fragment  {#associating-content-with-your-fragment}

Vous pouvez également [associer du contenu](/help/assets/content-fragments/content-fragments-assoc-content.md) à un fragment. Cela fournit une liaison pour que les ressources (c’est-à-dire les images) puissent éventuellement être utilisées avec le fragment lorsqu’il est ajouté à une page de contenu.

## Affichage et modification des métadonnées (propriétés) du fragment  {#viewing-and-editing-the-metadata-properties-of-your-fragment}

Vous pouvez afficher et modifier les propriétés d’un fragment à l’aide de l’onglet [Métadonnées](/help/assets/content-fragments/content-fragments-metadata.md).

## Chronologie pour les fragments de contenu  {#timeline-for-content-fragments}

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

Les annotations (pour les fragments de contenu) sont :
* Entrées dans l’éditeur de fragments
* Spécifiques à un segment de texte sélectionné au sein du fragment



Par exemple :

![chronologie](assets/cfm-managing-05.png)

## Comparaison des versions de fragments {#comparing-fragment-versions}

L’action de **comparer à la version actuelle** est disponible dans la [chronologie](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) après avoir sélectionné une version spécifique.

Cette opération va ouvrir :

* la version **actuelle** (la plus récente) (à gauche) ;

* la version sélectionnée **v&lt;*x.y*>** (à droite).

Ils seront présentés côte à côte, où :

* Les différences sont mises en surbrillance.

   * Le texte supprimé est en rouge
   * Le texte inséré est en vert
   * Le texte remplacé est en bleu

* L’icône en plein écran permet d’ouvrir l’une ou l’autre version seule, puis de revenir en mode parallèle.
* Vous pouvez **rétablir** la version spécifique
* **Terminé** vous ramène à la console

>[!NOTE]
Vous ne pouvez pas modifier le contenu du fragment lors de la comparaison des fragments.

![comparaison](assets/cfm-managing-06.png)

## Restauration vers une version spécifique {#reverting-to-a-version}

Vous pouvez restaurer vers une version spécifique de votre fragment :

* Directement à partir de la [chronologie](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

   Sélectionnez la version requise, puis l’action **Revenir à cette version**.

* Lors de la [comparaison d’une version à la version actuelle](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions), vous pouvez **restaurer** la version sélectionnée.

## Publication et référencement d’un fragment {#publishing-and-referencing-a-fragment}

>[!CAUTION]
Si votre fragment est basé sur un modèle, vous devez vous assurer que le [modèle a été publié](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model).
Si vous publiez un fragment de contenu pour lequel le modèle n’a pas encore été publié, une liste de sélection indique cela, ainsi que le fait que le modèle sera publié avec le fragment.

Les fragments de contenu doivent être publiés pour être utilisés dans l’environnement de publication. Ils peuvent être publiés :

* Après la création, en utilisant les actions [disponibles dans la console de ressources](#actions-for-a-content-fragment-assets-console).
* Dans l’[éditeur de fragment de contenu](#toolbar-actions-in-the-content-fragment-editor).
* Lorsque vous [publiez une page qui utilise le fragment](/help/sites-cloud/authoring/fundamentals/content-fragments.md#publishing), celui-ci est répertorié dans les références de la page.

>[!CAUTION]
Une fois qu’un fragment a été publié et/ou référencé, AEM affiche un avertissement lorsqu’un auteur ouvre à nouveau ce fragment en mode d’édition. Il s’agit de signaler que les modifications apportées au fragment seront également répercutées sur les pages référencées.

## Suppression d’un fragment {#deleting-a-fragment}

Pour supprimer un fragment :

1. Dans la console **Ressources**, naviguez jusqu’à l’emplacement de votre fragment de contenu.
2. Sélectionnez le fragment.

   >[!NOTE]
   L’action **Supprimer** n’est pas proposée comme action rapide.

3. Sélectionnez **Supprimer** dans la barre d’outils.
4. Confirmez l’action **Supprimer**.

   >[!CAUTION]
   Si le fragment est déjà référencé dans une page, un message d’avertissement vous demande de confirmer que vous souhaitez poursuivre et **forcer la suppression**. Le fragment et son composant de fragment de contenu seront supprimés de toutes les pages de contenu.

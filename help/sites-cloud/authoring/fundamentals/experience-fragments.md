---
title: Fragments d’expérience
description: Utilisez Adobe Experience Manager comme fragments d’expérience de service Cloud pour rendre vos expériences réutilisables et flexibles.
translation-type: tm+mt
source-git-commit: b7a2e86de27dbfcdecaf3a2bc1984678b7b69375

---


# Fragments d’expérience {#experience-fragments}

Dans Adobe Experience Manager en tant que service Cloud, un fragment d’expérience :
* est un groupe d’un ou de plusieurs composants
* inclut le contenu et la mise en page
* peut être référencée dans les pages
* peut contenir n’importe quel composant

Un fragment d’expérience :

* fait partie d’une expérience (page) ;
* peut être utilisé sur plusieurs pages ;
* est basé sur un modèle (uniquement modifiable) qui définit la structure et les composants ;
* comprend un ou plusieurs composants, avec mise en page, dans un système de paragraphes ;
* peut contenir d’autres fragments d’expérience ;
* peut être combiné à d’autres composants (y compris d’autres fragments d’expérience) pour former une page entière (expérience) ;
* peut avoir différentes variations et partager du contenu et/ou des composants ;
* peut être scindé en blocs de création utilisables dans plusieurs variations du fragment.

Vous pouvez utiliser des fragments d’expérience :

* Si un auteur souhaite réutiliser des parties (un fragment d’une expérience) d’une page.
Sans Fragments d’expérience, l’auteur doit copier et coller ce fragment. La création et la gestion de ces expériences de copier/coller est chronophage et source d’erreurs pour l’utilisateur.
Les fragments d’expérience rendent inutiles les opérations de copier/coller.
* Pour prendre en charge le cas d’utilisation CMS sans tête.
Les auteurs veulent utiliser AEM uniquement pour la création, mais pas pour la livraison au client. Un système/point de contact tiers utilise cette expérience, puis la diffuse à l’utilisateur final.

>[!NOTE]
>
>Dans le cas des fragments d’expérience, l’accès en écriture exige que le compte utilisateur soit enregistré dans le groupe :
>
>* `experience-fragments-editors`
>
>
Si vous rencontrez des problèmes, contactez votre administrateur système. 

## Quand utiliser les fragments d’expérience ? {#when-should-you-use-experience-fragments}

Les fragments d’expérience doivent être utilisés dans les cas suivants :

* Chaque fois que vous souhaitez réutiliser des expériences.
   * Expériences qui seront réutilisées avec un contenu identique ou similaire.
* Lorsque vous utilisez AEM en tant que plateforme de diffusion de contenu à des tiers.
   * Toute solution qui souhaite utiliser AEM comme plateforme de diffusion de contenu.
   * Intégration de contenu dans des points de contact tiers.
* Si l’une de vos expériences se décline en plusieurs variations ou rendus.
   * Variations spécifiques à un canal ou contexte particulier.
   * les expériences qui ont un sens pour le regroupement; par exemple, une campagne avec des expériences différentes sur plusieurs canaux.
* Lorsque vous avez recours au commerce omnicanal.
   * Partage de contenu commercial sur les canaux des [médias sociaux](/help/implementing/developing/extending/experience-fragments.md#social-variations) de grande échelle.
   * Conversion des points de contact en points de transaction.

## Organisation des fragments d’expérience {#organizing-your-experience-fragments}

Il est recommandé de :
* utiliser des dossiers pour organiser vos fragments d’expérience,

* [configurez les modèles autorisés sur ces dossiers](#configure-allowed-templates-folder).

La création de dossiers vous permet d’effectuer les opérations suivantes :

* créer une structure significative pour vos fragments d’expérience ; par exemple, selon la classification

   >[!NOTE]
   >
   >Il n’est pas nécessaire d’aligner la structure de vos fragments d’expérience sur la structure des pages de votre site.

* [allouer les modèles autorisés au niveau du dossier](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >Vous pouvez utiliser l’[éditeur de modèles](/help/sites-cloud/authoring/features/templates.md) pour créer votre propre modèle.

Le projet WKND structure certains fragments d’expérience selon `Contributors`. La structure utilisée illustre également l’utilisation d’autres fonctionnalités, telles que la gestion multisite (y compris des copies de langue).

Voir :

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Dossiers des fragments d’expérience](/help/sites-cloud/authoring/assets/xf-folders.png)

## Création et configuration d’un dossier pour vos fragments d’expérience {#creating-and-configuring-a-folder-for-your-experience-fragments}

Pour créer et configurer un dossier pour vos fragments d’expérience, il est recommandé de :

1. [Créer un dossier](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-folder).

1. [Configurez les modèles de fragments d’expérience autorisés pour ce dossier](#configure-allowed-templates-folder).

>[!NOTE]
>
>Il est également possible de configurer les modèles [autorisés pour votre instance](#configure-allowed-templates-instance), mais cette méthode **n’est pas** recommandée car les valeurs peuvent être remplacées lors de la mise à niveau.

### Configuration des modèles autorisés pour votre dossier {#configure-allowed-templates-folder}

>[!NOTE]
>
>Il s’agit de la méthode recommandée pour spécifier les modèles **** autorisés, car les valeurs ne seront pas remplacées lors de la mise à niveau.

1. Naviguez jusqu’au dossier **Fragments d’expérience** concerné.

1. Sélectionnez le dossier, puis **Propriétés**.

1. Spécifiez l’expression régulière pour récupérer les modèles requis dans le champ Modèles **** autorisés.

   Par exemple :
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Voir :
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Propriétés du fragment d’expérience - Modèles autorisés](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Modèles de fragments d’expérience](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Select **Save and Close**.

### Configuration des modèles autorisés pour votre instance {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Il n’est pas recommandé de modifier les modèles **** autorisés par cette méthode, car les modèles spécifiés peuvent être remplacés lors de la mise à niveau.
>
>Veuillez utiliser cette boîte de dialogue à titre d&#39;information uniquement.

1. Navigate to the required **Experience Fragments** console.

1. Sélectionnez **Options de configuration** :

   ![Bouton Configuration](/help/sites-cloud/authoring/assets/xf-18.png)

1. Spécifiez les modèles requis dans la boîte de dialogue **Configurer les Fragments d’expérience** :

   ![Configurer des fragments d’expérience](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Modèles de fragments d’expérience](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Sélectionnez **Enregistrer**.


## Création d’un fragment d’expérience {#creating-an-experience-fragment}

Pour créer un fragment d’expérience :

1. Select **Experience Fragments** from the Global Navigation.

   ![Fragments d’expérience dans le panneau de navigation](/help/sites-cloud/authoring/assets/xf-01.png)

1. Accédez au dossier requis et sélectionnez **Créer**:

   ![Création d’un dossier pour les fragments d’expérience](/help/sites-cloud/authoring/assets/xf-02.png)

1. Sélectionnez **Fragment** d’expérience pour ouvrir l’assistant **Créer un fragment** d’expérience.

   Sélectionnez le **Modèle** requis, puis **Suivant** :

   ![Sélection d’un modèle de fragment d’expérience](/help/sites-cloud/authoring/assets/xf-03.png)


1. Saisissez les **Propriétés** de votre **Fragment d’expérience**.

   Un **Titre** est obligatoire. Si le **Nom** n’est pas spécifié, il est dérivé du **Titre**.

   ![Propriétés du fragment d’expérience](/help/sites-cloud/authoring/assets/xf-04.png)

1. Cliquez sur **Créer**.

   Un message s’affiche. Sélectionnez :

   * **Terminé** pour revenir à la console
   * **Ouvrir** pour ouvrir l’éditeur de fragments

## Modification d’unְ fragment d’expérience {#editing-your-experience-fragment}

L’Éditeur de fragments d’expérience offre des fonctionnalités similaires à celles à l’Éditeur de page classique.

>[!NOTE]
>
>Pour plus d’informations sur l’utilisation de l’Éditeur de page, voir [Modification du contenu de la page](/help/sites-cloud/authoring/fundamentals/editing-content.md).

La procédure suivante explique comment créer un teaser pour un produit :

1. Faites glisser et déposez le composant requis depuis l’explorateur de [composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

1. Selon le composant :
   * Ajoutez le contenu et/ou les ressources nécessaires.
   * Configurez les propriétés selon les besoins.

1. Ajoutez d’autres composants, en fonction de vos besoins.

Par exemple: `http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![Fragment d’expérience sur la page](/help/sites-cloud/authoring/assets/xf-05.png)

## Création d’une variation de fragment d’expérience {#creating-an-experience-fragment-variation}

Vous pouvez créer des variations du fragment d’expérience, selon vos besoins :

1. Ouvrez le fragment à des fins de [modification](#editing-your-experience-fragment).
1. Ouvrez l’onglet **Variations**.

   ![Création d’une variation de fragment d’expérience](/help/sites-cloud/authoring/assets/xf-06.png)

1. L’option **Créer** permet de créer les éléments suivants :

   * **Variation**
   * **Variation comme Live Copy**.

1. Définissez les propriétés requises :

   * **Modèle**
   * **Titre**
   * **Nom** - Si rien n&#39;est fait, il sera dérivé du titre
   * **Description**
   * **Balises de variation**
   Par exemple :

   ![Propriétés de variation](/help/sites-cloud/authoring/assets/xf-07.png)

1. Confirm with **Done**, the new variation will be shown in the panel.

## Utilisation du fragment d’expérience {#using-your-experience-fragment}

Vous pouvez désormais utiliser le fragment d’expérience lors de la création de vos pages :

1. Ouvrez une page à modifier.

1. Créez une instance du composant Fragment d’expérience, dans le système de paragraphes de page :

1. Ajoutez le fragment d’expérience proprement dit à l’instance de composant. Pour ce faire, vous pouvez effectuer l’une des opérations suivantes :

   * Faites glisser le fragment requis depuis l’explorateur de ressources et déposez-le sur le composant.
   * Select **Configure** from the component toolbar and specify the fragment to use, confirm with **Done**.
   >[!NOTE]
   >
   >L’option Modifier disponible dans la barre d’outils du composant sert de raccourci pour ouvrir le fragment dans l’éditeur de fragments.

Par exemple: `http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![Fragment d’expérience dans l’éditeur de page](/help/sites-cloud/authoring/assets/xf-08.png)

## Blocs de création {#building-blocks}

Vous pouvez sélectionner un ou plusieurs composants pour créer un bloc de création à recycler dans votre fragment :

### Création d’un bloc {#creating-a-building-block}

Pour créer un bloc de ce type, procédez comme suit :

1. Dans l’éditeur de fragments d’expérience, sélectionnez les composants que vous souhaitez réutiliser :

   ![Sélectionner un composant pour le bloc de création](/help/sites-cloud/authoring/assets/xf-09.png)

1. Dans la barre d’outils des composants, sélectionnez **Convertir en bloc de création** :

   ![Bouton Bloc de création](/help/sites-cloud/authoring/assets/xf-10.png)

1. Saisissez le nom du **Bloc de création** et confirmez en cliquant sur **Convertir** :

   ![Bloc de création du nom](/help/sites-cloud/authoring/assets/xf-11.png)

1. Le bloc **de** création s’affichera dans le panneau de gauche (**Local**) et peut être sélectionné pour une action ultérieure :

   ![Bloc de création dans le rail](/help/sites-cloud/authoring/assets/xf-12.png)

#### Gestion d’un bloc de création {#managing-a-building-block}

Le bloc de création est visible dans l’onglet **Blocs de création**. Pour chaque bloc, les actions suivantes peuvent être effectuées :

* **** Atteindre l’élément principal : ouvre la variation principale dans un nouvel onglet
* **Renommer**
* **Supprimer**

![Gestion des blocs de création](/help/sites-cloud/authoring/assets/xf-13.png)

#### Utilisation d’un bloc de création {#using-a-building-block}

Vous pouvez faire glisser votre bloc de création vers le système de paragraphes de n’importe quel fragment, comme avec n’importe quel composant.

Lors de la modification d’un fragment d’expérience, les blocs de création disponibles s’affichent dans l’onglet de gauche. Vous pouvez filtrer selon :

* **Local** - Blocs de création à partir du fragment d’expérience actuel
* **Tout** : création de blocs à partir de tous les fragments

![Sélection de blocs de création](/help/sites-cloud/authoring/assets/xf-14.png)

## Détails de votre Éditeur de fragments {#details-of-your-experience-fragment}

Les détails de votre fragment sont visibles :

1. Accédez à l’emplacement de vos fragments d’expérience (n’accédez pas aux variations du fragment).
Details are shown in all views of the **Experience Fragments** console, with the **List View** including details of an export to Target: <!--Details are shown in all views of the **Experience Fragments** console, with the **List View** including details of an [export to Target](/help/sites-administering/experience-fragments-target.md):-->

   ![Détails du fragment d’expérience](/help/sites-cloud/authoring/assets/xf-15.png)

1. Lorsque vous ouvrez la section **Propriétés** du composant Fragment d’expérience :

   ![Bouton Propriétés](/help/sites-cloud/authoring/assets/xf-16.png)

   Les propriétés sont disponibles sous plusieurs onglets :

   >[!CAUTION]
   >
   >Ces onglets s’affichent lorsque vous ouvrez **Propriétés** à partir de la console Fragments d’expérience.
   >
   >Si vous **ouvrez les propriétés** lors de la modification d’un fragment d’expérience, les propriétés [de](/help/sites-cloud/authoring/fundamentals/page-properties.md) page appropriées s’affichent.

   ![Propriétés du fragment d’expérience](/help/sites-cloud/authoring/assets/xf-17.png)

   * **De base**
      * **Titre** - obligatoire
      * **Description**
      * **Balises**
      * **Nombre total de variantes** - informations uniquement
      * **Nombre de variantes Web** - informations uniquement
      * **Nombre de variantes** non web - informations uniquement
      * **Nombre de pages utilisant ce fragment** - informations uniquement
   * **Services cloud**
      * **Configuration du cloud**
      * **Configurations du service cloud**
      * **Identifiant de page Facebook**
      * **Panorama Pinterest**
   * **Références**
      * Liste de références
   * **État des réseaux sociaux**
      * Détails des variantes des réseaux sociaux

## Rendu HTML brut {#the-plain-html-rendition}

Using the `.plain.` selector in the URL, you can access the plain HTML rendition from the browser.

>[!NOTE]
>
>Même s’il est directement disponible à partir du navigateur, [le principal objectif consiste à autoriser d’autres applications (des applications Web tierces et des implémentations mobiles personnalisées, par exemple) à accéder directement au contenu du composant Fragment d’expérience en utilisant uniquement l’URL](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition).

## Exportation de fragments d’expérience {#exporting-experience-fragments}

Par défaut, les fragments d’expérience sont fournis au format HTML. Ils peuvent être utilisés à la fois par AEM et les canaux tiers.

Pour l’exportation vers Adobe Target, JSON peut également être utilisé. Pour obtenir des informations complètes, voir Intégration de Target aux Fragments d’expérience. <!--For export to Adobe Target, JSON can also be used. See [Target Integration with Experience Fragments](/help/sites-administering/experience-fragments-target.md) for full information.-->

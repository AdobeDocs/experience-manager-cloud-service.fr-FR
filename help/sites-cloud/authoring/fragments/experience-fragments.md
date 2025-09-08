---
title: Fragments d’expérience
description: Utilisez les fragments d’expérience dans Adobe Experience Manager as a Cloud Service pour rendre vos expériences réutilisables et flexibles.
exl-id: 9dc33677-141f-47e5-a01e-6c7488686314
solution: Experience Manager Sites
feature: Authoring, Experience Fragments
role: User
source-git-commit: 5578cfd1bbe91d904d3f36b67acf610f9196cb7d
workflow-type: tm+mt
source-wordcount: '2142'
ht-degree: 94%

---

# Fragments d’expérience {#experience-fragments}

Dans Adobe Experience Manager as a Cloud Service, un fragment d’expérience :

* est un groupe comprenant un ou plusieurs composants ;
* inclut le contenu et la disposition ;
* peut être référencé dans les pages ;
* peut contenir n’importe quel composant.

Un fragment d’expérience :

* fait partie d’une expérience (page) ;
* Peut être utilisé sur plusieurs pages (basées sur des modèles modifiables).
* est basé sur un modèle (modifiable uniquement) pour définir la structure et les composants.
* Ce modèle est utilisé pour créer la *page racine* du fragment d’expérience.
* est constitué d’un ou de plusieurs composants, avec disposition, dans un système de paragraphes ;
* peut contenir d’autres fragments d’expérience ;
* peut être combiné à d’autres composants (y compris d’autres fragments d’expérience) pour former une page complète (expérience).
* Il est possible de créer une ou plusieurs variations en fonction de la page racine.
* Ces variations peuvent partager du contenu et des composants.
* peut être scindé en blocs de création utilisables dans plusieurs variations du fragment.

Vous pouvez utiliser des fragments d’expérience :

* Si l’auteur souhaite réutiliser des parties (un fragment d’une expérience) d’une page.
Sans les fragments d’expérience, il doit copier et coller ce fragment. La création et la gestion de ces expériences de copier/coller sont chronophages et sources d’erreurs pour l’utilisateur.
Les fragments d’expérience rendent inutiles les opérations de copier/coller.
* Pour gérer le scénario d’utilisation CMS sans interface.
Les auteurs souhaitent utiliser AEM uniquement dans une optique de création, mais pas pour diffuser du contenu au client. Un système/point de contact tiers utilise cette expérience, puis la diffuse à l’utilisateur.
* Avec la [gestion multisite (MSM, Multi-Site Management)](/help/sites-cloud/administering/msm/overview.md) en tant que fragment d’expérience faisant partie d’une page. Cela s’applique à la fois aux fragments individuels et aux dossiers dans lesquels ils résident.

>[!NOTE]
>
>Les **[fragments de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md)** et les **fragments d’expérience** représentent deux fonctions distinctes d’AEM :
>* Les **fragments de contenu** sont des contenus éditoriaux, avec définition et structure, mais sans conception visuelle et/ou mise en page supplémentaires. Ils permettent d’accéder aux données structurées telles que les textes, les nombres et les dates, entre autres.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, consultez [Présentation des fragments de contenu et d’expérience dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=fr#content-fragments).

>[!NOTE]
>
>Dans le cas des fragments d’expérience, l’accès en écriture exige que le compte d’utilisateur ou d’utilisatrice soit enregistré dans le groupe :
>
>* `experience-fragments-editors`
>
>Si vous rencontrez des problèmes, contactez votre administration système.

## Quand utiliser les fragments d’expérience ? {#when-should-you-use-experience-fragments}

Les fragments d’expérience doivent être utilisés :

* Lorsque vous souhaitez réutiliser des expériences.
   * Expériences qui sont réutilisées avec un même contenu ou un contenu similaire.
* Lorsque vous utilisez AEM en tant que plateforme de diffusion de contenu à des tiers.
   * Toute solution qui souhaite utiliser AEM en tant que plateforme de diffusion de contenu.
   * Incorporation de contenu dans des points de contact tiers.
* Si vous disposez d’une expérience avec des variations ou des rendus différents.
   * Variations spécifiques au canal ou au contexte.
   * Expériences qu’il est logique de regrouper, par exemple, une campagne avec des expériences différentes sur les canaux.
* Lorsque vous avez recours au commerce omnicanal.
   * Rendre les points de contact transactionnels.

## Organisation des fragments d’expérience {#organizing-your-experience-fragments}

Nous vous encourageons à :
* utiliser des dossiers pour organiser vos fragments d’expérience ;

* [configurer les modèles autorisés sur ces dossiers](#configure-allowed-templates-folder).

La création de dossiers permet :

* Créer une structure significative pour vos fragments d’expérience ; en fonction de la classification, par exemple

  >[!NOTE]
  >
  >Il n’est pas nécessaire d’aligner la structure de vos fragments d’expérience sur la structure de page de votre site.

* [Allouer les modèles autorisés au niveau du dossier](#configure-allowed-templates-folder)

  >[!NOTE]
  >
  >Vous pouvez utiliser l’[éditeur de modèles](/help/sites-cloud/authoring/page-editor/templates.md) pour créer votre propre modèle.

Le projet WKND structure certains fragments d’expérience en fonction de `Contributors`. La structure utilisée illustre également l’utilisation d’autres fonctionnalités, telles que la gestion multisite (y compris des copies de langue).

Voir :

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Dossiers des fragments d’expérience](/help/sites-cloud/authoring/assets/xf-folders.png)

## Création et configuration d’un dossier pour vos fragments d’expérience {#creating-and-configuring-a-folder-for-your-experience-fragments}

Pour créer et configurer un dossier pour vos fragments d’expérience, il est recommandé de :

1. [Créer un dossier](/help/sites-cloud/authoring/sites-console/managing-pages.md#creating-a-new-folder)

1. [Configurer les modèles de fragments d’expérience autorisés pour ce dossier](#configure-allowed-templates-folder)

>[!NOTE]
>
>Il est également possible de configurer les [modèles autorisés pour votre instance](#configure-allowed-templates-instance). Cependant, cette méthode n’est **pas** recommandée, car les valeurs peuvent être remplacées lors de la mise à niveau.

### Configuration des modèles autorisés pour votre dossier {#configure-allowed-templates-folder}

>[!NOTE]
>
>Il s’agit de la méthode recommandée pour spécifier les **Modèles autorisés**, car les valeurs ne sont pas remplacées lors de la mise à niveau.

1. Accédez au dossier **Fragments d’expérience** concerné.

1. Sélectionnez le dossier, puis **Propriétés**.

1. Spécifiez l’expression régulière pour récupérer les modèles requis dans le champ **Modèles autorisés**.

   Par exemple :
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Voir :
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Propriétés des fragments d’expérience – Modèles autorisés](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Modèles de fragments d’expérience](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Sélectionnez **Enregistrer et fermer**.

### Configuration des modèles autorisés pour votre instance {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Il est déconseillé de modifier les **Modèles autorisés** à l’aide de cette méthode, car les modèles spécifiés peuvent être remplacés lors de la mise à niveau.
>
>Utilisez cette boîte de dialogue uniquement à titre d’information.

1. Accédez à la console **Fragments d’expérience** concernée.

1. Sélectionnez **Options de configuration** :

   ![Bouton Configuration](/help/sites-cloud/authoring/assets/xf-18.png)

1. Spécifiez les modèles requis dans la boîte de dialogue **Configurer des Fragments d’expérience** :

   ![Configurer des fragments d’expérience](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Modèles de fragments d’expérience](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Sélectionnez **Enregistrer**.

## Création d’un fragment d’expérience {#creating-an-experience-fragment}

Pour créer un fragment d’expérience :

1. Sélectionnez **Fragments d’expérience** dans la navigation globale.

   ![Fragments d’expérience dans le panneau Navigation](/help/sites-cloud/authoring/assets/xf-01.png)

1. Accédez au dossier requis et sélectionnez ensuite **Créer** :

   ![Création d’un dossier pour les fragments d’expérience](/help/sites-cloud/authoring/assets/xf-02.png)

1. Sélectionnez **Fragment d’expérience** pour ouvrir l’assistant **Créer un fragment d’expérience**.

   Sélectionnez le **Modèle** requis, puis **Suivant** :

   ![Sélection d’un modèle de fragment d’expérience](/help/sites-cloud/authoring/assets/xf-03.png)


1. Renseignez les **Propriétés** de votre **Fragment d’expérience**.

   Le **titre** est obligatoire. Si le **nom** n’est pas indiqué, il est déduit du **titre**.

   ![Propriétés du fragment d’expérience](/help/sites-cloud/authoring/assets/xf-04.png)

   >[!NOTE]
   >
   >Les balises du modèle de fragment d’expérience ne seront pas fusionnées avec les balises sur cette page racine de fragment d’expérience.
   >
   >Elles sont complètement séparées.

1. Cliquez sur **Créer**.

   Un message s’affiche. Sélectionnez :

   * **Terminé** pour revenir à la console
   * **Ouvrir** pour ouvrir l’éditeur de fragments

## Modification d’un fragment d’expérience {#editing-your-experience-fragment}

L’Éditeur de fragments d’expérience offre des fonctionnalités similaires à celles à l’Éditeur de page classique.

>[!NOTE]
>
>Voir [Modifier le contenu d’une page](/help/sites-cloud/authoring/page-editor/edit-content.md) pour plus d’informations sur l’utilisation de l’éditeur de page.

L’exemple de procédure suivant illustre la création d’un teaser pour un produit :

1. Faites glisser le composant requis à partir de l’[Explorateur de composants](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser).

1. En fonction du composant :
   * Ajoutez le contenu et/ou les ressources nécessaires.
   * Configurez les propriétés suivant les besoins.

1. Ajoutez d’autres composants, en fonction de vos besoins.

Par exemple : `http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![Fragment d’expérience sur la page](/help/sites-cloud/authoring/assets/xf-05.png)

## Création d’une variation de fragment d’expérience {#creating-an-experience-fragment-variation}

Vous pouvez créer des variantes de votre fragment d’expérience en fonction de vos besoins :

1. Ouvrez votre fragment pour [modification](#editing-your-experience-fragment).
1. Ouvrez l’onglet **Variations**.

   ![Création d’une variation de fragment d’expérience](/help/sites-cloud/authoring/assets/xf-06.png)

1. **Créer** permet de créer :

   * **Variation**
   * **Variation en tant que Live Copy**.

     >[!NOTE]
     >
     >La création d’une variation en tant que Live Copy initiale héritera du titre en utilisant la source de Live Copy comme variation principale.

1. Définissez les propriétés requises :

   * **Modèle**
   * **Titre**
   * **Nom** : si rien n’est indiqué dans ce champ, le nom est déduit du titre
   * **Description**
   * **Balises de variation**

   Par exemple :

   ![Propriétés de la variation](/help/sites-cloud/authoring/assets/xf-07.png)


1. Confirmez en cliquant sur **Terminé**. La nouvelle variation est alors affichée dans le panneau.

## Utilisation du fragment d’expérience {#using-your-experience-fragment}

Vous pouvez désormais utiliser votre fragment d’expérience lors de la création de vos pages :

1. Ouvrez la page à modifier.

   >[!NOTE]
   >
   >La page doit être basée sur un modèle modifiable.

1. Créez une instance du composant Fragment d’expérience dans le système de paragraphes de la page :

1. Ajoutez le fragment d’expérience proprement dit à l’instance de composant. Pour ce faire, vous pouvez effectuer l’une des opérations suivantes :

   * Faites glisser le fragment requis sur le composant depuis l’Explorateur de ressources.
   * Sélectionnez **Configurer** dans la barre d’outils du composant et indiquez le fragment à utiliser. Confirmez en cliquant sur **Terminé**.

   >[!NOTE]
   >
   >L’option Modifier disponible dans la barre d’outils du composant sert de raccourci pour ouvrir le fragment dans l’éditeur de fragments.

Par exemple : `http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![Fragment d’expérience dans l’éditeur de page](/help/sites-cloud/authoring/assets/xf-08.png)

## Blocs de création {#building-blocks}

Vous pouvez sélectionner un ou plusieurs composants pour créer un bloc de création à recycler dans votre fragment :

### Création d’un bloc de création {#creating-a-building-block}

Pour créer un bloc de création :

1. Dans l’éditeur de fragments d’expérience, sélectionnez les composants à réutiliser :

   ![Sélection du composant pour le bloc de création](/help/sites-cloud/authoring/assets/xf-09.png)

1. Dans la barre d’outils des composants, sélectionnez **Convertir en bloc de création** :

   ![Bouton Bloc de création](/help/sites-cloud/authoring/assets/xf-10.png)

1. Saisissez le nom du **Bloc de création** et confirmez en cliquant sur **Convertir** :

   ![Attribution d’un nom au bloc de création](/help/sites-cloud/authoring/assets/xf-11.png)

1. Le **bloc de création** s’affiche dans l’onglet de gauche (**Local**) et peut être sélectionné pour effectuer d’autres actions :

   ![Bloc de création dans le rail](/help/sites-cloud/authoring/assets/xf-12.png)

#### Gestion d’un bloc de création {#managing-a-building-block}

Votre bloc de création est visible dans l’onglet **Blocs de création**. Pour chaque bloc, les actions disponibles sont les suivantes :

* **Atteindre l’élément principal** : ouvre la variation de la page racine dans un nouvel onglet.
* **Renommer**
* **Supprimer**

![Gestion des blocs de création](/help/sites-cloud/authoring/assets/xf-13.png)

#### Utilisation d’un bloc de création {#using-a-building-block}

Vous pouvez faire glisser votre bloc de création vers le système de paragraphes de n’importe quel fragment, comme avec n’importe quel composant.

Lors de la modification d’un fragment d’expérience, les blocs de création disponibles s’affichent dans l’onglet de gauche. Vous pouvez effectuer un filtrage en fonction des éléments suivants :

* **Local** : blocs de création à partir du fragment d’expérience actuel
* **Tout** : blocs de création à partir de tous les fragments

![Sélection de blocs de création](/help/sites-cloud/authoring/assets/xf-14.png)

## Personnalisation de votre fragment d’expérience {#personalization-experience-fragment}

La personnalisation de votre fragment d’expérience vous permet, en tant que spécialiste marketing, de définir les audiences cibles pour le fragment d’expérience une seule fois, puis de réutiliser le fragment dans n’importe quelle page. Cela :

* élimine le besoin de spécifier les variations requises pour chaque audience à chaque fois que le fragment est utilisé ;
* maintient le style à travers les offres.

Vous pouvez créer un fragment d’expérience comportant plusieurs composants regroupés dans ce fragment unique. Vous pouvez également créer des variations du fragment pour chaque segment d’audience spécifique, puis réutiliser ces fragments d’expérience sur les canaux requis.

La personnalisation s’effectue en définissant les propriétés de **Personnalisation** du fragment d’expérience ou de la variation, ou du dossier contenant les fragments. Ainsi, l’héritage peut remplacer les propriétés de personnalisation.

La configuration de ces propriétés active également le mode **Ciblage** dans l’éditeur de fragments d’expérience.

### Définir la personnalisation de votre fragment d’expérience {#defining-personalization-experience-fragment}

Pour personnaliser votre fragment, procédez comme suit :

1. Accédez à l’emplacement requis dans la console **Fragments d’expérience**.

1. Sélectionnez un dossier ou votre fragment, puis cliquez sur **Propriétés** dans la barre d’outils.

   >[!NOTE]
   >
   >Les propriétés de personnalisation définies pour un dossier sont héritées par tous les dossiers enfants de la sous-arborescence, ainsi que par les fragments d’expérience (et leurs variations) de cette sous-arborescence. Les propriétés peuvent être modifiées en annulant l’héritage.

1. Ouvrez l’onglet **Personnalisation** pour définir et enregistrer vos paramètres. Par exemple, pour un dossier :

   ![Fragment d’expérience - Propriétés de personnalisation](/help/sites-cloud/authoring/assets/xf-personalization-properties.png)

   >[!CAUTION]
   >
   >Lorsqu’un fragment est incorporé dans une page Sites et que la **Personnalisation** a été configurée, seule la version de personnalisation de la page sera utilisée au moment du rendu de la page.
   >
   >Pour que le ciblage effectué sur les composants d’un fragment fonctionne lors du rendu de la page, les conditions suivantes doivent être remplies :
   >
   >Le **Chemin d’accès ContextHub** sélectionné dans l’onglet **Personnalisation** doit correspondre à l’une des valeurs suivantes :
   >
   >* le même chemin d’accès que celui configuré pour la page sur laquelle le fragment est rendu
   >
   >  Ou :
   >
   >* un chemin contenant un sous-ensemble des magasins définis dans le chemin d’accès ContextHub configuré pour la page.
   >
   >Le **chemin d’accès aux segments** sélectionné dans l’onglet **Personalization** doit être :
   >
   >* le même chemin d’accès que celui configuré pour la page sur laquelle le fragment est rendu
   >
   >  Ou
   >
   >* un chemin d’accès contenant un sous-ensemble des segments configurés pour la page.

### Définir le ciblage de votre fragment d’expérience {#defining-targeting-experience-fragment}

Une fois les propriétés de personnalisation configurées, le mode Ciblage est disponible lorsque le fragment est ouvert en vue d’être modifié.

![Éditeur de fragments d’expérience - Mode Ciblage](/help/sites-cloud/authoring/assets/xf-targeting-mode.png)

Ce mode fonctionne de la même manière que pour la modification de pages. Consultez la section [Mode Ciblage pour l’éditeur de page](/help/sites-cloud/authoring/personalization/targeted-content.md) pour plus d’informations.

## Détails de votre fragment d’expérience {#details-of-your-experience-fragment}

Les détails de votre fragment sont visibles :

1. Accédez à l’emplacement de vos fragments d’expérience (ne poursuivez pas l’exploration vers le bas jusqu’aux variations du fragment).
Les détails sont affichés dans toutes les vues de la console **Fragments d’expérience**, dans la vue **Liste**, notamment les détails d’une [exportation vers Target](/help/sites-cloud/integrating/integrating-adobe-target.md) :

   ![Détails du fragment d’expérience](/help/sites-cloud/authoring/assets/xf-15.png)

1. Lorsque vous ouvrez la section **Propriétés** du composant Fragment d’expérience :

   ![Bouton Propriétés](/help/sites-cloud/authoring/assets/xf-16.png)

   Les propriétés sont disponibles dans plusieurs onglets :

   >[!CAUTION]
   >
   >Ces onglets s’affichent lorsque vous ouvrez les **propriétés** à partir de la console Fragments d’expérience.
   >
   >Si vous **ouvrez les propriétés** lors de la modification d’un fragment d’expérience, les [propriétés de page](/help/sites-cloud/authoring/sites-console/page-properties.md) appropriées s’affichent.

   ![Propriétés du fragment d’expérience](/help/sites-cloud/authoring/assets/xf-17.png)

   * **De base**
      * **Titre** – obligatoire
      * **Description**
      * **Balises**
      * **Nombre total de variations** – informations uniquement
      * **Nombre de variations web** – informations uniquement
      * **Nombre de variations non-web** – informations uniquement
      * **Nombre de pages utilisant ce fragment** – informations uniquement
   * **Cloud Services**
      * **Configuration du cloud**
      * **Configuration de Cloud Services**
      * **Identifiant de page Facebook**
      * **Panorama Pinterest**
   * **Références**
      * Liste de références
   * **Personnalisation**
      * **Chemin d’accès ContextHub**
      * **Chemin d’accès de segments**
      * **Marque**

## Rendu HTML brut {#the-plain-html-rendition}

Utiliser le sélecteur `.plain.` de l’URL permet d’accéder au rendu HTML brut à partir du navigateur.

>[!NOTE]
>
>Même s’il est directement disponible à partir du navigateur, [le principal objectif consiste à autoriser d’autres applications (des applications web tierces et des implémentations mobiles personnalisées, par exemple) à accéder directement au contenu du composant Fragment d’expérience en utilisant uniquement l’URL](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition).

## Publication de fragments d’expérience {#publishing-experience-fragments}

La publication de votre fragment d’expérience est essentiellement identique à [publication d’une page](/help/sites-cloud/authoring/sites-console/publishing-pages.md) (à partir de la console Fragments d’expérience ou de l’éditeur).

Vous pouvez également [Publier en aperçu](/help/sites-cloud/authoring/sites-console/previewing-content.md) (toujours à partir de la console de Fragments d’expérience ou de l’éditeur).

>[!CAUTION]
>
>Par défaut, la publication du dossier racine des fragments d’expérience (situé directement sous `/content/experience-fragments`) :
>
>* ne publie que le dossier de conteneur lui-même
>* ne publie aucun enfant
>* dépublie tous les enfants déjà publiés
>
>Pour la publication de tous les fragments d’expérience dans le dossier , chacun doit être publié séparément.

## Exportation de fragments d’expérience {#exporting-experience-fragments}

Par défaut, les fragments d’expérience sont fournis au format HTML. Peut être utilisée par les canaux AEM et les canaux tiers.

Pour l’exportation vers Adobe Target, JSON peut également être utilisé. Voir :

* [Intégration à Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Exportation de fragments d’expérience vers Adobe Target](/help/sites-cloud/integrating/experience-fragments-target.md)

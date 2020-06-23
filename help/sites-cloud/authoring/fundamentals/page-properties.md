---
title: Modification des propriétés de page
description: Définissez les propriétés requises pour une page
translation-type: tm+mt
source-git-commit: 5d72645aa3a5296e7b616101955734f03425ab59
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 99%

---


# Modification des propriétés de page {#editing-page-properties}

Vous pouvez définir les propriétés requises pour une page. Celles-ci peuvent varier selon la nature de la page. Par exemple, certaines pages peuvent être connectées à une Live Copy, et d’autres pas, et les informations Live Copy seront disponibles suivant le cas.

## Propriétés de page {#page-properties}

Les propriétés sont réparties sur plusieurs onglets.

### De base {#basic}

* **Titre**

   * Le titre de la page s’affiche à divers endroits. Par exemple, la liste de l’onglet **Sites web** et les modes Carte/Liste des **Sites**.
   * Ce champ est obligatoire.

* **Balises**

   * Vous pouvez ajouter des balises sur la page, ou en supprimer, en mettant à jour la liste dans la zone de sélection.
   * La balise sélectionnée est alors répertoriée sous la zone de sélection. Vous pouvez supprimer une balise de cette liste à l’aide du symbole x.
   * Vous pouvez saisir une nouvelle balise en entrant son nom dans une zone de sélection vide.
      * La nouvelle balise est créée lorsque vous appuyez sur Entrée.
      * Elle s’affiche alors avec une petite étoile à droite indiquant qu’il s’agit d’une nouvelle balise.
   * Vous pouvez faire votre choix parmi les balises existantes dans la liste déroulante.
   * Un « x » apparaît lorsque vous passez le pointeur de la souris sur une entrée de balise dans la zone de sélection ; vous pouvez vous en servir pour supprimer cette balise de la page.
   * Pour plus d’informations sur les balises, voir [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md).

* **Masquer dans la navigation**

   * Indique si la page doit être affichée ou masquée dans la navigation entre les pages du site qui en résulte.

* **ID HTML**

   * ID HTML à appliquer au composant.

* **Titre de la page**

   * Titre à utiliser sur la page. Habituellement utilisé par les composants du titre. Si ce champ reste vide, le **titre** est utilisé.

* **Titre de navigation**

   * Vous pouvez spécifier un titre distinct à utiliser dans la navigation (par exemple, si vous souhaitez qu’il soit plus concis). Si ce champ reste vide, le **titre** est utilisé.

* **Sous-titre**

   * Sous-titre à utiliser sur la page.

* **Description**

   * Votre description de la page, son objectif ou tout autre détail que vous souhaiteriez ajouter.

* **Heure d’activation**

   * Date et heure auxquelles la page publiée sera activée. Une fois publiée, cette page restera dormante jusqu’à l’heure indiquée.
   * Ne complétez pas ces champs pour les pages que vous souhaitez publier immédiatement (scénario normal).

* **Heure de désactivation**

   * Heure à laquelle la page publiée sera désactivée.
   * Ne renseignez pas ces champs pour une action immédiate.

* **URL Vanity**

   * Permet de saisir une URL Vanity pour cette page. Vous pouvez ainsi disposer d’une URL plus courte et/ou plus explicite.
   * Par exemple, si l’URL de redirection est définie sur `welcome` sur la page identifiée par le chemin `/v1.0/startpage` pour le site web `http://example.com`, `http://example.com/welcome` sera l’URL de redirection de `http://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >L’URL de redirection :
   >
   >* doit être unique. Vous devez donc veiller à ce que la valeur ne soit pas déjà utilisée par une autre page.
   >* ne prend pas en charge les modèles d’expression régulière.
   >* ne doit pas être définie sur une page existante.


* **Rediriger l’URL Vanity**

   * Indique si vous souhaitez que la page utilise l’URL de redirection.

### Avancé {#advanced}

* **Langue**

   * Langue de la page.

* **Racine de la langue**

   * Cette option doit être activée si la page est la racine d’une copie de langue.

* **Rediriger**

   * Indique la page vers laquelle cette page doit être automatiquement redirigée.

* **Conception**

   * Indique si la page doit être affichée ou masquée dans la navigation entre les pages du site qui en résulte.

* **Alias**

   * Indique un alias à utiliser avec cette page.
   >[!NOTE]
   >
   >L’alias définit la propriété `sling:alias` afin de définir un nom d’alias pour la ressource (cela n’affecte que la ressource, et non le chemin).
   >
   >Par exemple, si vous définissez l’alias `latin-lang` pour le nœud `/content/we-retail/spanish`, cette page est accessible via `/content/we-retail/latin-language`.
   >
   >Pour plus d’informations, voir Noms de page localisés sous Bonnes pratiques relatives à la gestion des URL et à l’optimisation du moteur de recherche.

   <!--
  >For further details see [Localized page names under SEO and URL Management Best Practices](/help/managing/seo-and-url-management.md#localized-page-names).
  -->

<!--
* **Inherited from &lt;*path*&gt;**

  * Indicates whether the page is inherited. and where from.
-->

* **Configuration du cloud**

   * Chemin d’accès à la configuration.

* **Modèles autorisés**

   * [Définissez la liste des modèles qui seront disponibles](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) dans cette sous-branche.

* **Activer** (exigence d’authentification)

   * Activez (ou désactivez) l’utilisation de l’authentification pour accéder à la page.
   >[!NOTE]
   >
   >Les groupes d’utilisateurs fermés pour la page sont définis dans l’onglet **[Autorisations](#permissions)**.

* **Page de connexion**

   * Page à utiliser pour la connexion.

* **Exporter la configuration**

   * Indiquez une configuration d’exportation.

### Miniature  {#thumbnail}

Affiche l’image de la miniature de la page. Vous pouvez :

* **Générer l’aperçu**

   * Génère un aperçu de la page à utiliser comme miniature.

* **Télécharger l’image**

   * Télécharge une image à utiliser comme miniature.

* **Sélectionner une image**

   * Sélectionne une ressource existante à utiliser comme vignette.

* **Rétablir**

   * Cette option n’est disponible qu’après avoir effectué une modification de la vignette. Si vous ne souhaitez pas conserver votre modification, vous pouvez la rétablir avant de l’enregistrer.

### Réseaux sociaux {#social-media}

* **Partage sur les réseaux sociaux**

   Définit les options de partage disponibles sur la page. Affiche les options disponibles pour le [composant principal de partage](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/sharing.html).

   * **Activer le partage utilisateur pour Facebook**
   * **Activer le partage utilisateur pour Pinterest**
   * **Variation de fragment d’expérience préférée**
      * Définit la variation de fragment d’expérience utilisée pour générer les métadonnées de la page.

### Cloud Services {#cloud-services}

* **Configuration de Cloud Services**

   * Définissez les propriétés des services cloud.

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### Personnalisation  {#personalization}

* **Configurations ContextHub**

   * Sélectionnez la configuration ContextHub et le chemin d’accès aux segments.

   <!--Select the [ContextHub Configuration](/help/sites-administering/contexthub-config.md) and [Segments Path](/help/sites-administering/segmentation.md).
  -->

* **Configuration du ciblage**

   * Sélectionnez une [marque pour spécifier la portée du ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md).
   >[!NOTE]
   >Cette option nécessite que le compte utilisateur figure dans le groupe `Target Adminstrators`.

### Autorisations {#permissions}

* **Autorisations**

   * Ajouter des autorisations
   * Modifier le groupe d’utilisateurs fermé
   * Afficher les autorisations effectives

   <!--[Add Permissions](/help/sites-administering/user-group-ac-admin.md) -->

   <!-- [Edit Closed User Group](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)-->

   <!-- View the [Effective Permissions](/help/sites-administering/user-group-ac-admin.md)-->

### Blueprint {#blueprint}

* **Blueprint**

   * Définissez les propriétés d’une page de plan directeur dans le cadre de la gestion multi-site.

   <!--Define properties for a Blueprint page within [multi-site management](/help/sites-administering/msm.md).-->

   * Détermine les circonstances dans lesquelles les modifications seront diffusées à la Live Copy.


### Live Copy  {#live-copy}

* **Live Copy**

   * Définissez les propriétés d’une page Live Copy dans le cadre de la gestion multi-site. <!--Define properties for a Live Copy page within [multi-site management](/help/sites-administering/msm.md).-->
   * Détermine les circonstances dans lesquelles les modifications seront propagées à partir du plan directeur.

### Structure du site  {#site-structure}

* Diffusez des liens d’accès aux pages qui fournissent les fonctionnalités à l’échelle du site, comme la **page d’inscription** et la page **en mode hors ligne**, entre autres.

## Modification des propriétés de page {#editing-page-properties-1}

* Dans la console **Sites** :
   * [En créant une page](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (sous-ensemble des propriétés)
   * En cliquant ou en appuyant sur **Propriétés**
      * Pour une seule page
      * Pour plusieurs pages (un seul sous-ensemble des propriétés est disponible pour la modification en masse)
* Dans l’éditeur de page :
   * En sélectionnant **Informations sur la page** (puis **Ouvrir les propriétés**)

### À partir de la console Sites – Une seule page {#from-the-sites-console-single-page}

Cliquez ou appuyez sur **Propriétés** pour définir les propriétés de la page :

1. Dans la console **Sites**, accédez à l’emplacement de la page pour laquelle afficher et modifier les propriétés.
1. Sélectionnez l’option **Propriétés** pour la page requise, en utilisant :
   * [Actions rapides](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * Les propriétés de la page affichées dans les onglets appropriés.
1. Affichez ou modifiez les propriétés selon les besoins.
1. Puis cliquez sur **Enregistrer** pour enregistrer vos modifications et sur **Fermer** pour revenir à la console.

### Lors de la modification d’une page {#when-editing-a-page}

Lorsque vous modifiez une page, utilisez les **Informations sur la page** pour définir ses propriétés :

1. Ouvrez la page dont vous souhaitez modifier les propriétés.
1. Sélectionnez l’icône **Informations sur la page** pour ouvrir le menu de sélection :
1. Sélectionnez **Ouvrir les propriétés**. Une boîte de dialogue s’ouvre alors pour vous permettre de modifier les propriétés, triées selon l’onglet approprié. Les boutons suivants sont également disponibles à droite de la barre d’outils :
   * **Annuler**
   * **Enregistrer et fermer**
1. Utilisez le bouton **Enregistrer et fermer** pour enregistrer les modifications.

### À partir de la console Sites – Plusieurs pages {#from-the-sites-console-multiple-pages}

Dans la console **Sites**, vous pouvez sélectionner plusieurs pages, puis utiliser **Afficher les propriétés** pour afficher et/ou modifier les propriétés de la page. On parle alors de modification en masse des propriétés de la page.

>[!NOTE]
>
>La modification en masse des propriétés est également disponible pour les ressources. La procédure est très semblable. Seuls quelques points sont différents. Pour plus d’informations, voir Modification des propriétés de plusieurs ressources.
>
>Il existe également un éditeur en bloc qui vous permet de rechercher du contenu provenant de plusieurs pages à l’aide du langage GQL (Google Query Language), puis de le modifier directement avant d’enregistrer les modifications dans les pages d’origine.

<!--
>Bulk editing of properties is also available for Assets. It is very similar, but differs in a few points. See [Editing Properties of Multiple Assets](/help/assets/managing-multiple-assets.md) for details.
>
>There is also the [Bulk Editor](/help/sites-administering/bulk-editor.md), which allows you to search for content from multiple pages using GQL (Google Query Language) and then edit the content directly in the bulk editor before saving your changes to the originating pages.
-->

Vous pouvez sélectionner plusieurs pages en vue d’une modification en masse de différentes façons :

* Lors de l’exploration de la console **Sites**
* Après avoir utilisé la fonction **Rechercher** pour localiser un ensemble de pages

Sélectionnez les pages et cliquez ou appuyez ensuite sur l’option **Propriétés** pour afficher les propriétés en bloc :

![Modification groupée des propriétés de page](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

Vous ne pouvez modifier en masse que des pages qui :

* Partagent le même type de ressource.
* Ne font pas partie d’une Live Copy.
   * Si l’une de ces pages fait partie d’une Live Copy, un message s’affiche lorsque les propriétés sont ouvertes.

Une fois le mode de modification en bloc activé, vous pouvez effectuer les opérations suivantes :

* **Mode**

   * La liste des pages affectées
      * Vous pouvez, au besoin, en sélectionner/désélectionner.
      * Onglets
         * Comme c’est le cas lors de l’affichage des propriétés d’une seule page, celles-ci sont organisées sous des onglets.
   * Un sous-ensemble de propriétés
      * Les propriétés qui sont disponibles sur toutes les pages sélectionnées, et qui ont été définies explicitement comme étant disponibles pour la modification en masse, sont visibles.
      * Si vous réduisez la sélection à une seule page, toutes les propriétés sont alors visibles.
   * Propriétés communes partageant une valeur commune
      * Seules les propriétés qui partagent une valeur commune sont visibles en mode Affichage.
      * Si le champ comporte plusieurs valeurs (Balises, par exemple), les valeurs ne sont visibles que lorsque *toutes* sont communes. Si seulement quelques-unes sont communes, elles sont visibles lors de la phase de modification.
      * En l’absence de propriétés avec une valeur commune, un message s’affiche.

* **Modifier**

   * Vous pouvez mettre à jour les valeurs dans les champs disponibles.
      * Les nouvelles valeurs sont appliquées à toutes les pages sélectionnées lorsque vous appuyez sur **Terminé**.
      * Lorsque le champ comporte plusieurs valeurs (Balises, par exemple), vous pouvez ajouter une valeur ou supprimer une valeur commune.
   * Les champs qui sont communs, mais pour lesquels des valeurs différentes sont renseignées dans les différentes pages, sont signalés par une valeur spéciale, par exemple par le texte `<Mixed Entries>`. Vous devez être prudent lors de la modification de ces champs afin d’éviter toute perte de données.

>[!NOTE]
>
>Le composant de page peut être configuré pour spécifier les champs disponibles en vue de la modification en bloc. Reportez-vous à la section Configuration de votre page en vue de la modification en masse des propriétés.

<!--
>The page component can be configured to specify the fields available for bulk editing. See [Configuring your page for bulk editing of page properties](/help/sites-developing/bulk-editing.md).
-->

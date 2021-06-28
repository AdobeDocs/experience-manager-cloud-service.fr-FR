---
title: Modification des propriétés de page
description: Définissez les propriétés requises pour une page
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
source-git-commit: af06d288af688dbc3baf73526460bc17d6ff7a35
workflow-type: tm+mt
source-wordcount: '1930'
ht-degree: 98%

---

# Modification des propriétés de page {#editing-page-properties}

Vous pouvez définir les propriétés requises pour une page. Celles-ci peuvent varier selon la nature de la page. Par exemple, certaines pages peuvent être connectées à une Live Copy, et d’autres pas, et les informations Live Copy seront disponibles suivant le cas.

## Propriétés de page {#page-properties}

Les propriétés sont réparties sur plusieurs onglets.

### De base {#basic}

* **Titre et balises**

   * **Titre** - Le titre de la page est affiché à divers emplacements ; dans la liste de l’onglet **Sites Web** et les vues de carte/liste **Sites**, par exemple
      * Ce champ est obligatoire.
   * **Balises** - Vous pouvez ajouter des balises sur la page, ou en supprimer, en mettant à jour la liste dans la zone de sélection.
      * La balise sélectionnée est alors répertoriée sous la zone de sélection. Vous pouvez supprimer une balise de cette liste à l’aide du symbole x.
      * Vous pouvez saisir une nouvelle balise en entrant son nom dans une zone de sélection vide.
         * La nouvelle balise est créée lorsque vous appuyez sur Entrée.
         * Elle s’affiche alors avec une petite étoile à droite indiquant qu’il s’agit d’une nouvelle balise.
      * Vous pouvez faire votre choix parmi les balises existantes dans la liste déroulante.
      * Un « x » apparaît lorsque vous passez le pointeur de la souris sur une entrée de balise dans la zone de sélection ; vous pouvez vous en servir pour supprimer cette balise de la page.
      * Pour plus d’informations sur les balises, voir [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md).
   * **Masquer dans la navigation** - Indique si la page doit être affichée ou masquée dans la navigation entre les pages du site qui en résulte.

* **Valorisation de marque**

   Appliquez une identité de marque cohérente sur plusieurs pages en ajoutant un rappel à chaque titre de page. Cette fonctionnalité nécessite l’utilisation du composant de page de la version 2.14.0, ou ultérieure, des [composants principaux.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)

   * **Remplacer** : cochez la case pour définir le titre de rappel sur cette page.
      * La valeur sera héritée par toutes les pages enfants à moins que leurs valeurs de **remplacement** ne soient également définies.
   * **Remplacer la valeur** : texte de rappel à ajouter au titre de la page.
      * La valeur est ajoutée au titre de la page après un caractère de barre verticale, par exemple « La Toscane en vélo | Toujours prêt pour le WKND »

* **ID HTML**

   * **ID** - Identification HTML à appliquer au composant.

* **Autres titres et descriptions**

   * **Titre de la page** - Titre - à utiliser sur la page. Habituellement utilisé par les composants du titre. Si ce champ reste vide, le **titre** est utilisé.
   * **Titre de navigation** - Vous pouvez spécifier un titre distinct à utiliser dans la navigation (par exemple, si vous souhaitez qu’il soit plus concis). Si ce champ est vide, le **Titre** est utilisé.
   * **Sous-titre** - Sous-titre - à utiliser sur la page.
   * **Description** - Votre description de la page, son objectif ou tout autre détail que vous souhaiteriez ajouter.

* **Heure d’activation/de désactivation**

   * **Heure d’activation** - Date et heure auxquelles la page publiée sera rendue visible (rendue) dans l’environnement de publication. La page doit être publiée, soit manuellement, soit par réplication automatique préconfigurée.

      >[!NOTE]
      >
      > Voir [Heures d’activation et de désactivation - Configuration du déclenchement](/help/operations/replication.md#on-and-off-times-trigger-configuration) pour en savoir plus sur la configuration de la réplication automatique associée.

      * Si elle a déjà été [publiée (manuellement)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md), cette page reste inactive (masquée) jusqu’à son rendu au moment spécifié.
      * Si elle n’est pas publiée et configurée pour la réplication automatique, la page est automatiquement publiée, puis rendue au moment spécifié.
      * Si elle n’est pas publiée et n’est pas configurée pour la réplication automatique, la page n’est pas publiée automatiquement. Un message 404 s’affiche donc lors d’une tentative d’accès à la page.
   * **Heure de désactivation** - Similaire à l’**heure d’activation**, souvent utilisée en combinaison avec cette dernière, définit l’heure à laquelle la page publiée sera masquée dans l’environnement de publication.

   * Laissez ces champs (**Heure d’activation** et **Heure de désactivation**) vides pour les pages que vous souhaitez publier immédiatement et qui sont disponibles dans l’environnement de publication jusqu’à ce qu’elles soient désactivées (scénario normal).


* **URL Vanity**

   * Permet de saisir une URL Vanity pour cette page. Vous pouvez ainsi disposer d’une URL plus courte et/ou plus explicite.
   * Par exemple, si l’URL Vanity est définie sur `welcome` sur la page identifiée par le chemin `/v1.0/startpage` pour le site web `http://example.com`, `http://example.com/welcome` sera l’URL Vanity de `http://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >L’URL Vanity :
   >
   >* doit être unique. Vous devez donc veiller à ce que la valeur ne soit pas déjà utilisée par une autre page.
   >* ne prend pas en charge les modèles d’expression régulière.
   >* ne doit pas être définie sur une page existante.


   * **Ajouter** - Appuyez ou cliquez pour afficher un champ afin de définir une URL d’origine pour la page.
      * Appuyez ou cliquez de nouveau pour ajouter plusieurs éléments.
      * Appuyez ou cliquez sur l’icône **Supprimer** pour supprimer l’URL Vanity.
   * **Rediriger l’URL Vanity** - Indique si vous souhaitez que la page utilise l’URL Vanity.




### Avancé {#advanced}

* **Paramètres**

   * **Langue** - Langue de la page.
   * **Racine de la langue** - Cette option doit être activée si la page est la racine d’une copie de langue.
   * **Rediriger** - Indique la page vers laquelle cette page doit être automatiquement redirigée.
   * **Conception** - Indique si la page doit être affichée ou masquée dans la navigation entre les pages du site qui en résulte.
   * **Alias** - Indique un alias à utiliser avec cette page.

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

* **Configuration**

   * **Configuration du cloud** - Chemin d’accès à la configuration

* **Paramètres de modèles**

   * **Modèles autorisés** - [Définit la liste des modèles qui seront disponibles](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) dans cette sous-branche

* **Exigence d’authentification**

   * **Activer** - Activer l’utilisation de l’authentification pour accéder à la page

      >[!NOTE]
      >
      >Les groupes d’utilisateurs fermés pour la page sont définis dans l’onglet **[Autorisations](#permissions)**.

   * **Page de connexion** - Page à utiliser pour la connexion

* **Exportation**

   * **Configuration de l’exportation** - Spécifie une configuration d’exportation.

### Miniature {#thumbnail}

Configuration de la miniature de la page

* **Générer l’aperçu** - Génère un aperçu de la page à utiliser comme miniature.
* **Télécharger l’image** - Transfère une image à utiliser comme miniature
* **Sélectionner une image** - Sélectionne une ressource existante à utiliser comme miniature.
* **Rétablir** - Cette option n’est disponible qu’après avoir effectué une modification de la miniature. Si vous ne souhaitez pas conserver votre modification, vous pouvez la rétablir avant de l’enregistrer.

### Réseaux sociaux {#social-media}

* **Partage sur les réseaux sociaux**

   Définit les options de partage disponibles sur la page. Affiche les options disponibles pour le [composant principal de partage](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/sharing.html).

   * **Activer le partage utilisateur pour Facebook**
   * **Activer le partage utilisateur pour Pinterest**
   * **Variation de fragment d’expérience préférée**
      * Définit la variation de fragment d’expérience utilisée pour générer les métadonnées de la page.

### Cloud Services {#cloud-services}

* **Configurations du service cloud**  - Définit les propriétés des services cloud

   <!--Define properties for [cloud services](/help/sites-developing/extending-cloud-config.md).
  -->

### Personnalisation {#personalization}

* **Configurations ContextHub**

   * **Chemin ContextHub** - Définit la [configuration ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Chemin d’accès aux segments** - Définit le chemin d’accès aux [segments](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **Configuration du ciblage**

   * **Marque** - Définit une [marque pour spécifier la portée du ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md).
   >[!NOTE]
   >Cette option nécessite que le compte utilisateur figure dans le groupe `Target Administrators`.

### Autorisations {#permissions}

* **Autorisations**

   * Ajouter des autorisations
   * Modifier le groupe d’utilisateurs fermé
   * Afficher les autorisations effectives

   <!--[Add Permissions](/help/sites-administering/user-group-ac-admin.md) -->

   <!-- [Edit Closed User Group](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)-->

   <!-- View the [Effective Permissions](/help/sites-administering/user-group-ac-admin.md)-->

### Blueprint {#blueprint}

Cet onglet n’est visible que pour les pages qui servent de plan directeur. Les plans directeurs servent de base aux Live Copies pour [la gestion multisite.](/help/sites-cloud/administering/msm/overview.md)

* **Live Copies actuelles** - Listes de pages basées sur (c.-à-d. Live Copies de) cette page de plan directeur.

* **Configurations du déploiement** - Détermine les circonstances dans lesquelles les modifications seront diffusées à la Live Copy.

### Live Copy  {#live-copy}

* **Synchroniser** - Synchroniser la Live Copy avec le plan directeur, en conservant les modifications locales.
* **Réinitialiser** - Réinitialiser la Live Copy à l’état de plan directeur, en supprimant les modifications locales.
* **Suspendre** - Suspendre la Live Copy des modifications de déploiement supplémentaires.
* **Désolidariser** - Désolidariser la Live Copy du plan directeur

* **Source**

   * Affiche le chemin du plan directeur pour cette Live Copy

* **État**

   * Liste l’état actuel de la Live Copy de la page

* **Configuration**

   * **Héritage de Live Copy** - Si cette option est cochée, la configuration de la Live Copy est effective sur tous les enfants.
   * **Hériter des configurations de déploiement du parent** - Si cette option est cochée, la configuration de déploiement est héritée du parent de la page.
   * **Choisir la configuration de déploiement** - Définit les circonstances dans lesquelles les modifications seront propagées à partir du plan directeur et disponibles uniquement lorsque **Hériter des configurations de déploiement du parent** n’est pas sélectionné

### Aperçu {#preview}

Lorsqu’un environnement de prévisualisation est activé, les éléments suivants s’affichent :

* URL de prévisualisation : URL utilisée pour accéder au contenu dans l’environnement de prévisualisation.

## Modification des propriétés de page {#editing-page-properties-1}

* Dans la console **Sites** :
   * [En créant une page](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (sous-ensemble des propriétés)
   * En cliquant ou en appuyant sur **Propriétés**
      * Pour une seule page
      * Pour plusieurs pages (un seul sous-ensemble des propriétés est disponible pour la modification en masse)
* À partir de l’éditeur de page:
   * En sélectionnant **Informations sur la page** (puis **Ouvrir les propriétés**)

### À partir de la console Sites – Une seule page {#from-the-sites-console-single-page}

Cliquez ou appuyez sur **Propriétés** pour définir les propriétés de la page :

1. Dans la console **Sites**, accédez à l’emplacement de la page pour laquelle afficher et modifier les propriétés.
1. Sélectionnez l’option **Propriétés** pour la page requise, en utilisant :
   * [Actions rapides](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
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

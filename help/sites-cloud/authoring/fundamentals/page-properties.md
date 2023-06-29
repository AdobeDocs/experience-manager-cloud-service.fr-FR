---
title: Modification des propriétés de page
description: Définir les propriétés requises pour une page
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2341'
ht-degree: 81%

---

# Modification des propriétés de page {#editing-page-properties}

Vous pouvez définir les propriétés requises pour une page. Celles-ci peuvent varier selon la nature de la page. Par exemple, certaines pages peuvent être connectées à une Live Copy, tandis que d’autres ne le sont pas, et les informations de Live Copy sont disponibles, le cas échéant.

## Propriétés de page {#page-properties}

Les propriétés sont réparties sur plusieurs onglets.

### De base {#basic}

* **Titre et balises**

   * **Titre** – Le titre de la page est affiché à divers emplacements ; dans la liste de l’onglet **Sites web** et les vues Carte/Liste **Sites**, par exemple
      * Ce champ est obligatoire.
   * **Balises** : vous pouvez ajouter des balises sur la page, ou en supprimer, en mettant à jour la liste dans la zone de sélection.
      * La balise sélectionnée est alors répertoriée sous la zone de sélection. Vous pouvez supprimer une balise de cette liste à l’aide du symbole x.
      * Vous pouvez saisir une nouvelle balise en saisissant son nom dans une zone de sélection vide.
         * La nouvelle balise est créée lorsque vous appuyez sur Entrée.
         * Elle est marquée d’une petite étoile sur la droite indiquant qu’il s’agit d’une nouvelle balise.
      * Avec la fonctionnalité de liste déroulante, vous pouvez effectuer un choix parmi des balises existantes.
      * Un x s’affiche lorsque vous placez le pointeur de la souris sur une entrée de balise dans la zone de sélection, qui peut être utilisé pour supprimer cette balise pour cette page.
      * Pour plus d’informations sur les balises, consultez la section [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md).
   * **Masquer dans la navigation** : indique si la page est affichée ou masquée dans la navigation entre les pages du site qui en résulte.

* **Valorisation de marque**

  Appliquez une identité de marque cohérente sur plusieurs pages en ajoutant un rappel à chaque titre de page. Cette fonctionnalité nécessite l’utilisation du composant de page de la version 2.14.0, ou ultérieure, des [composants principaux.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)

   * **Slug de la marque**

      * **Remplacer** : cochez la case pour définir le titre de rappel sur cette page.
         * La valeur est héritée par toutes les pages enfants, sauf si elles disposent également de la variable **Remplacement** valeurs définies.
      * **Remplacer la valeur** : texte de rappel à ajouter au titre de la page.
         * La valeur est ajoutée au titre de la page après un caractère de barre verticale, par exemple « La Toscane en vélo | Toujours prêt pour le WKND »

* **ID HTML**

   * **ID** – Identification HTML à appliquer au composant.

* **Autres titres et descriptions**

   * **Titre de la page** – Titre à utiliser sur la page. Généralement utilisé par les composants de titre. Si elle est vide, la variable **Titre** est utilisée.
   * **Titre de navigation** - Vous pouvez spécifier un titre distinct à utiliser dans la navigation (par exemple, si vous souhaitez qu’il soit plus concis). Si elle est vide, la variable **Titre** est utilisée.
   * **Sous-titre** – Sous-titre à utiliser sur la page.
   * **Description** – Votre description de la page, son objectif ou tout autre détail que vous souhaiteriez ajouter.

* **Heure d’activation/de désactivation**

  >[!NOTE]
  >
  > Voir [Heures d’activation et de désactivation – Configuration du déclenchement](/help/operations/replication.md#on-and-off-times-trigger-configuration) pour en savoir plus sur la configuration de la réplication automatique associée.

  >[!NOTE]
  >Si la variable **Heure d’activation** ou **Heure de désactivation** est dans le passé et la réplication automatique est configurée, puis l’action appropriée est déclenchée immédiatement.

   * **Heure d’activation** - Date et heure auxquelles la page publiée est rendue visible (rendue) dans l’environnement de publication. La page doit être publiée, soit manuellement, soit par réplication automatique préconfigurée.

      * Si existe déjà [publié (manuellement)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) cette page reste inactive (masquée) jusqu’au rendu à l’heure indiquée.
      * Si elle n’est pas publiée et configurée pour la réplication automatique, la page est automatiquement publiée, puis rendue au moment spécifié.
      * Si elle n’est pas publiée et n’est pas configurée pour la réplication automatique, la page n’est pas publiée automatiquement. Un message 404 s’affiche donc lorsqu’une tentative d’accès à la page est effectuée.

   * **Heure de désactivation** - Similaire à et souvent utilisé en combinaison avec **Heure d’activation**, cette option définit l’heure à laquelle la page publiée est masquée dans l’environnement de publication.

   * Laissez ces champs (**Heure d’activation** et **Heure de désactivation**) vides pour les pages que vous souhaitez publier immédiatement et qui sont disponibles dans l’environnement de publication jusqu’à ce qu’elles soient désactivées (scénario normal).

* **URL de redirection**

   * Permet de saisir une URL de redirection pour cette page, ce qui peut vous permettre d’avoir une URL plus courte ou plus expressive.
   * Par exemple, si l’URL Vanity est définie sur `welcome` sur la page identifiée par le chemin `/v1.0/startpage` pour le site web `http://example.com`, `http://example.com/welcome` sera l’URL Vanity de `http://example.com/content/v1.0/startpage`

  >[!CAUTION]
  >
  >L’URL Vanity :
  >
  >* doit être unique. Vous devez donc veiller à ce que la valeur ne soit pas déjà utilisée par une autre page.
  >* Ne prennent pas en charge les modèles d’expression régulière.
  >* ne doit pas être définie sur une page existante.

   * **Ajouter** – Appuyez ou cliquez pour afficher un champ afin de définir une URL d’origine pour la page.
      * Appuyez ou cliquez de nouveau pour ajouter plusieurs éléments.
      * Appuyez ou cliquez sur l’icône **Supprimer** pour supprimer l’URL Vanity.
   * **Rediriger l’URL Vanity** – Indique si vous souhaitez que la page utilise l’URL Vanity.

### Avancé {#advanced}

* **Paramètres**

   * **Langue** – Langue de la page.
   * **Racine de la langue** – Cette option doit être activée si la page est la racine d’une copie de langue.
   * **Rediriger** – Indique la page vers laquelle cette page doit être automatiquement redirigée. avec un statut HTML `302 Found`.
      * **Redirection permanente** - Lorsque cette case est cochée, la page redirige vers le chemin cible fourni avec un statut HTML `301 Moved Permanently`.
   * **Conception** – Indique si la page doit être affichée ou masquée dans la navigation entre les pages du site qui en résulte.
   * **Alias** – Indique un alias à utiliser avec cette page.
      * Par exemple, si vous définissez l’alias de `private` pour la page `/content/wknd/us/en/magazine/members-only`, alors cette page est également accessible via `/content/wknd/us/en/magazine/private`.
      * La création d’un alias permet de définir la propriété `sling:alias` sur le nœud de page, ce qui affecte uniquement la ressource, et non le chemin d’accès au référentiel.
      * Les pages accessibles par alias dans l’éditeur ne peuvent pas être publiées. Les [options de publication](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès réel.
      * Pour plus d’informations, consultez [Noms de page localisés dans les Bonnes pratiques de SEO et de gestion des URL](/help/overview/seo-and-url-management.md#localized-page-names).

* **Configuration**

   * **Hérité de &lt;path>** - activer/désactiver l’héritage ; active la disponibilité de la **Configuration du cloud** pour la sélection.

   * **Configuration du cloud** – Chemin d’accès à la configuration sélectionnée

* **Paramètres de modèles**

   * **Modèles autorisés** - [Définit la liste des modèles disponibles](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) dans cette sous-branche

* **Exigence d’authentification**

   * **Activer** – Activer l’utilisation de l’authentification pour accéder à la page

     >[!NOTE]
     >
     >Les groupes d’utilisateurs fermés pour la page sont définis dans l’onglet **[Autorisations](#permissions)**.

   * **Page de connexion** – Page à utiliser pour la connexion

* **Exportation**

   * **Configuration de l’exportation** – Spécifie une configuration d’exportation.

* **SEO**

   * **URL canonique** - peut être utilisé pour remplacer l’URL canonique de la page ; si rien n’est indiqué, l’URL de la page est son URL canonique.

   * **Balises robots** - sélectionner les balises robots pour contrôler le comportement des robots des moteurs de recherche.

     >[!NOTE]
     >
     >Certaines des options sont en conflit les unes avec les autres. En cas de conflit, l’option la plus permissive est prioritaire.

   * **Générer un plan de site** : lorsqu’il est sélectionné, un fichier sitemap.xml est généré pour cette page et ses descendants.

### Images {#images}

* **Image en vedette**

  Sélectionnez et configurez l’image à afficher. Cette option est utilisée dans les composants qui référencent la page, par exemple, les teasers, les listes de pages, etc.

   * **Image**

     Vous pouvez **Choisir** une ressource ou rechercher un fichier à charger, puis sélectionner **Modifier** ou **Effacer**.

   * **Texte secondaire** : texte utilisé pour représenter la signification et/ou la fonction de l’image, par exemple, pour une utilisation par des lecteurs d’écran.

   * **Hériter - Valeur issue de la ressource DAM** : lorsque cette option est cochée, le texte secondaire est renseigné avec la valeur des métadonnées `dc:description`dans DAM.

* **Miniature**

  Configuration de la miniature de la page

   * **Générer l’aperçu** – Génère un aperçu de la page à utiliser comme miniature.
   * **Télécharger l’image** – Transfère une image à utiliser comme miniature
   * **Sélectionner une image** – Sélectionne une ressource existante à utiliser comme miniature.
   * **Rétablir** – Cette option n’est disponible qu’après avoir effectué une modification de la miniature. Si vous ne souhaitez pas conserver votre modification, vous pouvez la rétablir avant de l’enregistrer.

### Services cloud {#cloud-services}

* **Configurations du service cloud** – Définition des propriétés des services cloud

### Personnalisation {#personalization}

* **Configurations ContextHub**

   * **Hérité de &lt;path>** : active/désactive l’héritage ; active la disponibilité du **Chemin d’accès ContextHub** et du **Chemin d’accès des segments** pour la sélection

   * **Chemin ContextHub** – Définit la [configuration ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Chemin d’accès aux segments** – Définit le chemin d’accès aux [segments](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **Configuration du ciblage**

   * **Marque** – Définit une [marque pour spécifier la portée du ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md).

  >[!NOTE]
  >Cette option nécessite que le compte utilisateur figure dans le groupe `Target Administrators`.

### Autorisations {#permissions}

* **Autorisations**

   * **Ajouter des autorisations**
   * **Modifier le groupe d’utilisateurs fermé**
   * Afficher les **autorisations effectives**

### Blueprint {#blueprint}

Cet onglet n’est visible que pour les pages qui servent de plan directeur. Les plans directeurs servent de base aux Live Copies, et font partie de la [gestion multisite](/help/sites-cloud/administering/msm/overview.md).

* **Live Copies actuelles** - Répertorie les pages basées sur (c’est-à-dire Live Copies de) cette page de plan directeur.

* **Configurations du déploiement** : contrôle les circonstances dans lesquelles les modifications sont propagées à la Live Copy.

### Live Copy {#live-copy}

Cet onglet n’est visible que pour les pages configurées en tant que Live Copies. Comme pour les plans directeurs, les Live Copies font partie de la [gestion multisite](/help/sites-cloud/administering/msm/overview.md).

* **Synchroniser** – Synchroniser la Live Copy avec le plan directeur, en conservant les modifications locales.
* **Réinitialiser** – Réinitialiser la Live Copy à l’état de plan directeur, en supprimant les modifications locales.
* **Suspendre** – Suspendre la Live Copy des modifications de déploiement supplémentaires.
* **Désolidariser** – Désolidariser la Live Copy du plan directeur

* **Source**

   * Affiche le chemin du plan directeur pour cette Live Copy

* **État**

   * Liste l’état actuel de la Live Copy de la page

* **Configuration**

   * **Héritage de Live Copy** – Si cette option est cochée, la configuration de la Live Copy est effective sur tous les enfants.
   * **Hériter des configurations de déploiement du parent** – Si cette option est cochée, la configuration de déploiement est héritée du parent de la page.
   * **Choisir la configuration de déploiement** - Définit les circonstances dans lesquelles les modifications sont propagées à partir du plan directeur et disponibles uniquement lorsque **Hériter des configurations de déploiement du parent** n’est pas sélectionné

### Aperçu {#preview}

Lorsqu’un environnement de prévisualisation est activé, les éléments suivants s’affichent :

* URL de prévisualisation : URL utilisée pour accéder au contenu dans l’environnement de prévisualisation.

### Application web progressive {#progressive-web-app}

Grâce à une configuration simple, une personne en charge de la création de contenu peut désormais activer des fonctionnalités d’application web progressive (PWA) pour les expériences créées dans AEM Sites.

>[!NOTE]
>
>Pour plus d’informations, consultez la section [Activation des fonctionnalités d’applications web progressives](/help/sites-cloud/authoring/features/enable-pwa.md).

* **Configurer l’expérience d’installation**

   * **Activer PWA** : active/désactive la fonction ; permet d’installer le site en tant que PWA.
   * **StartupURL** : URL de démarrage préférée
   * **Mode d’affichage** : définit la manière dont le navigateur doit être masqué ou présenté sur l’appareil local
   * **Orientation de l’écran** : définit comment le PWA gère les orientations de l’appareil
   * **Couleur du thème** : la couleur de l’application utilisée pour l’affichage de la barre d’outils et des commandes de navigation de l’interface utilisateur native par le système d’exploitation de l’utilisateur ou de l’utilisatrice local
   * **Couleur d’arrière-plan** : la couleur d’arrière-plan de l’application qui s’affiche au chargement de l’application
   * **Icône** : l’icône qui représente l’application sur l’appareil de l’utilisateur

* **Gestion du cache (avancé)**

   * **Stratégie de mise en cache et fréquence d’actualisation du contenu** : définit le modèle de mise en cache de votre PWA
   * **Fichiers à mettre en cache pour une utilisation hors ligne**
      * **Prémise du cache du fichier (aperçu technique)** - les fichiers hébergés sur AEM sont enregistrés dans le cache du navigateur local lorsque le service worker est installé et avant d’être utilisé
      * **Bibliothèques côté client** : bibliothèques côté client à mettre en cache pour une expérience hors ligne
      * **Inclusions des chemins** : les demandes réseau pour les chemins définis sont interceptées et le contenu mis en cache est renvoyé conformément à la stratégie de mise en cache et à la fréquence d’actualisation configurées pour le contenu
      * **Exclusions des chemins** : ces fichiers ne seront jamais mis en cache, quels que soient les paramètres définis dans Prémise en cache des fichiers et dans Inclusions des chemins

## Modification des propriétés de page {#editing-page-properties-1}

* Dans la console **Sites** :
   * [En créant une page](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (sous-ensemble des propriétés)
   * En cliquant ou en appuyant sur **Propriétés**
      * Pour une seule page
      * Pour plusieurs pages (seul un sous-ensemble des propriétés peut être modifié en masse)
* À partir de l’éditeur de page :
   * En sélectionnant **Informations sur la page** (puis **Ouvrir les propriétés**)

### À partir de la console Sites – Une seule page {#from-the-sites-console-single-page}

Cliquez ou appuyez sur **Propriétés** pour définir les propriétés de la page :

1. Dans la console **Sites**, accédez à l’emplacement de la page pour laquelle afficher et modifier les propriétés.
1. Sélectionnez l’option **Propriétés** pour la page requise, en utilisant :
   * [Actions rapides](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * Les propriétés de la page s’affichent à l’aide des onglets appropriés.
1. Affichez ou modifiez les propriétés selon les besoins.
1. Puis cliquez sur **Enregistrer** pour enregistrer vos modifications et sur **Fermer** pour revenir à la console.

### Lors de la modification d’une page {#when-editing-a-page}

Lorsque vous modifiez une page, utilisez les **Informations sur la page** pour définir ses propriétés :

1. Ouvrez la page dont vous souhaitez modifier les propriétés.
1. Sélectionnez l’icône **Informations sur la page** pour ouvrir le menu de sélection :
1. Sélectionnez **Ouvrir les propriétés**. Une boîte de dialogue s’ouvre alors pour vous permettre de modifier les propriétés, triées selon l’onglet approprié. Les boutons suivants sont également disponibles à droite de la barre d’outils :
   * **Annuler**
   * **Enregistrez et fermez**
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

Vous pouvez sélectionner plusieurs pages à des fins de modification en bloc de différentes manières, notamment :

* Lorsque vous parcourez la console **Sites**
* Après avoir utilisé **Rechercher** pour localiser un ensemble de pages

Après avoir sélectionné les pages, puis cliqué ou appuyé sur l’icône **Option Propriétés**, les propriétés en bloc s’affichent :

![Modification groupée des propriétés de page](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

Vous ne pouvez modifier en masse que des pages qui :

* Partagent le même type de ressource.
* Ne font pas partie d’une Live Copy.
   * Si l’une des pages fait partie d’une Live Copy, un message s’affiche lorsque les propriétés sont ouvertes.

Une fois le mode de modification en bloc activé, vous pouvez effectuer les opérations suivantes :

* **Mode**

   * Liste des pages affectées
      * Vous pouvez sélectionner/désélectionner si nécessaire.
      * Onglets
         * Comme pour l’affichage des propriétés d’une seule page, les propriétés sont classées dans des onglets.
   * Un sous-ensemble de propriétés
      * Les propriétés qui sont disponibles sur toutes les pages sélectionnées, et qui ont été définies explicitement comme étant disponibles pour la modification en masse, sont visibles.
      * Si vous réduisez la sélection à une seule page, toutes les propriétés sont alors visibles.
   * Propriétés communes partageant une valeur commune
      * Seules les propriétés qui partagent une valeur commune sont visibles en mode Affichage.
      * Si le champ comporte plusieurs valeurs (Balises, par exemple), les valeurs ne sont visibles que lorsque *toutes* sont communes. Si seulement quelques-unes sont communes, elles sont visibles lors de la phase de modification.
      * En l’absence de propriétés avec une valeur commune, un message s’affiche.

* **Modifier**

   * Vous pouvez mettre à jour les valeurs dans les champs disponibles.
      * Les nouvelles valeurs sont appliquées à toutes les pages sélectionnées lorsque vous sélectionnez **Terminé**.
      * Lorsque le champ comporte plusieurs valeurs (Balises, par exemple), vous pouvez ajouter une nouvelle valeur ou supprimer une valeur commune.
   * Les champs qui sont communs, mais qui ont des valeurs différentes sur les différentes pages, sont indiqués par une valeur spéciale, telle que le texte. `<Mixed Entries>`.

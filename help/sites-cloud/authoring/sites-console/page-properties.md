---
title: Propriétés de page
description: Découvrez les différentes propriétés qu’une page peut avoir, comment elles contrôlent le comportement de la page et comment elle est gérée.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
solution: Experience Manager Sites
feature: Authoring
role: User
mini-toc-levels: 2
source-git-commit: b9328a22ff544f2c663868d33d7b06e02819f1d7
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 34%

---


# Propriétés de page {#page-properties}

Découvrez les différentes propriétés qu’une page peut avoir, comment elles contrôlent le comportement de la page et comment elle est gérée.

>[!TIP]
>
>Pour plus d’informations sur la modification des propriétés d’une page, consultez le document [&#x200B; Modification des propriétés de page &#x200B;](/help/sites-cloud/authoring/sites-console/edit-page-properties.md).

## Présentation et disponibilité des propriétés {#overview}

Les propriétés de page peuvent contrôler de nombreux aspects d’une page, depuis le titre jusqu’aux autorisations, en passant par le branding. Les propriétés sont réparties sur plusieurs onglets, dont certains peuvent être masqués selon le type de page. Comme la plupart des propriétés dans AEM, [&#x200B; propriétés de page peuvent être héritées.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md#inheritance)

>[!NOTE]
>
>Ce document décrit toutes les propriétés de page possibles. Selon le type de page, toutes les propriétés ne sont pas disponibles.

## Onglet De base {#basic}

### Titre et balises {#title-tags}

* **Titre** - Définit le titre des métadonnées de page à des fins d’optimisation du moteur de recherche (SEO) ainsi que le titre affiché dans le contenu de la page (sauf s’il est remplacé)
   * Le titre de la page est affiché à divers emplacements de l’interface utilisateur d’AEM, y compris dans les vues Carte/Liste **Sites** de la [Console Sites.](/help/sites-cloud/authoring/sites-console/introduction.md)
   * Ce champ est obligatoire.
* **Balises** - Définit les balises de métadonnées de page à des fins d’optimisation pour les moteurs de recherche.
   * Vous pouvez ajouter ou supprimer des balises de la page en mettant à jour la liste dans la zone de sélection.
   * Utilisez la liste déroulante pour effectuer une sélection parmi des balises existantes.
   * La balise sélectionnée est alors répertoriée sous la zone de sélection. Vous pouvez supprimer une balise de cette liste à l’aide du symbole x.
   * Vous pouvez saisir une nouvelle balise en saisissant son nom dans une zone de sélection vide.
      * La nouvelle balise est créée lorsque vous appuyez sur Entrée.
      * Elle est marquée d’une petite étoile sur la droite indiquant qu’il s’agit d’une nouvelle balise.
   * Un x s’affiche lorsque vous placez le pointeur de la souris sur une entrée de balise dans la zone de sélection, qui peut être utilisé pour supprimer cette balise pour cette page.
   * Pour plus d’informations sur les balises, voir [Utilisation des balises.](/help/sites-cloud/authoring/sites-console/tags.md)
* **Masquer dans la navigation** - Indique si la page doit être affichée ou masquée dans la navigation entre les pages du site qui en résulte

### Branding {#branding}

Appliquez une identité de marque cohérente sur plusieurs pages en ajoutant un rappel à chaque titre de page. Cette fonctionnalité nécessite l’utilisation du composant de page de la version 2.14.0, ou ultérieure, des [composants principaux.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)

* **Slug de la marque**
   * **Remplacer** : cochez la case pour définir le slug de marque sur cette page.
      * La valeur est héritée par toutes les pages enfants, à moins que leurs valeurs de **remplacement** ne soient également définies.
   * **Remplacer la valeur** : texte de rappel à ajouter au titre de la page.
      * La valeur est ajoutée au titre de la page après une barre verticale, par exemple `Cycling Tuscany | Always ready for the WKND`

### ID HTML {#html-id}

* **ID** – Identification HTML à appliquer au composant.

### Autres titres et descriptions {#more-titles}

* **Titre de la page** - Titre à utiliser sur la page
   * Il est généralement utilisé par les composants de titre.
   * Si rien n’est indiqué, le **titre** est utilisé.
* **Titre de navigation** - Vous pouvez spécifier un titre distinct à utiliser dans la navigation (par exemple, si vous souhaitez qu’il soit plus concis).
   * Si ce champ est vide, le **Titre de la page** est utilisé.
* **Sous-titre** - Sous-titre à utiliser sur la page
* **Description** - Votre description de la page, son objectif ou tout autre détail que vous souhaitez ajouter

### Heure d’activation/de désactivation {#on-off-time}

L’heure d’activation/de désactivation d’une page est un moyen pratique de masquer temporairement le contenu déjà publié. Le contenu reste sur l’instance de publication lorsqu’elle est désactivée. La désactivation d’une page ne dépublie pas le contenu.

* **Heure d’activation** – Date et heure auxquelles la page publiée sera rendue visible (rendue) dans l’environnement de publication. La page doit être publiée, soit manuellement, soit par réplication automatique préconfigurée.

   * Si elle est déjà [publiée)](/help/sites-cloud/authoring/sites-console/publishing-pages.md) cette page est disponible sur l’instance de publication, mais reste inactive (masquée) jusqu’au rendu à l’heure spécifiée.
   * Si elle n’est pas publiée et [configurée pour la réplication automatique](/help/operations/replication.md#on-and-off-times-trigger-configuratio) la page est automatiquement publiée, puis rendue, à l’heure spécifiée.
   * Si elle n’est pas publiée et n’est pas configurée pour la réplication automatique, la page n’est pas automatiquement publiée. Une erreur 404 s’affiche donc lorsqu’une tentative d’accès à la page est effectuée.

* **Heure de désactivation** – Similaire à l’**heure d’activation**, souvent utilisée en combinaison avec cette dernière, définit l’heure à laquelle la page publiée est masquée dans l’environnement de publication.

Laissez ces champs (**Heure d’activation** et **Heure de désactivation**) vides pour les pages que vous souhaitez publier et qui sont disponibles immédiatement et qui sont disponibles dans l’environnement de publication jusqu’à ce qu’elles soient désactivées (scénario normal).

>[!NOTE]
>Si l’**heure d’activation** ou l’**heure de désactivation** est dans le passé et que la réplication automatique est configurée, l’action appropriée est déclenchée immédiatement.

>[!TIP]
>
>Les heures d’activation/désactivation traitent strictement du contenu déjà publié (manuellement ou par réplication automatique). Pour cette raison, les workflows de publication tels que ceux destinés à l’approbation de contenu ne sont pas déclenchés par les heures d’activation/de désactivation et les heures d’activation/de désactivation n’affectent pas le statut de publication de la page. Pour cette raison, les heures d’activation/de désactivation sont plus appropriées pour afficher/masquer temporairement le contenu déjà approuvé et publié.
>
>Si vous souhaitez publier un nouveau contenu avec tous les workflows associés ou supprimer entièrement (dépublier le contenu) de votre site, pensez à [gérer votre publication.](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication)

### URL de redirection {#vanity-url}

Cette propriété vous permet de saisir une URL Vanity pour cette page, ce qui peut vous permettre d’avoir une URL plus courte ou plus expressive. Par exemple, si l’URL Vanity est définie sur `welcome` sur la page identifiée par le chemin `/v1.0/startpage` pour le site web `http://example.com`, `http://example.com/welcome` sera l’URL Vanity de `http://example.com/content/v1.0/startpage`

>[!CAUTION]
>
>L’URL Vanity :
>
>* Doit être unique.
>* Elles ne prennent pas en charge les modèles d’expression régulière.
>* ne doit pas être définie sur une page existante.

* **Ajouter** - Sélectionnez cette option pour afficher un champ afin de définir une URL d’origine pour la page.
   * Sélectionnez à nouveau pour ajouter plusieurs éléments.
   * Sélectionnez l’icône **Supprimer** pour supprimer l’URL Vanity.
* **Rediriger l’URL Vanity** - Indique si vous souhaitez que la page utilise l’URL Vanity ou la redirige vers l’URL réelle de la page

## Avancé {#advanced}

### Paramètres {#settings}

* **Langue** – Langue de la page.
* **Racine de la langue** – Cette option doit être activée si la page est la racine d’une copie de langue.
* **Rediriger** - Indique la page vers laquelle cette page doit être automatiquement redirigée avec un statut de `302 Found` HTML
   * **Redirection permanente** - Lorsque cette case est cochée, la page redirige vers le chemin cible fourni avec un statut HTML `301 Moved Permanently`.
* **Conception**
* **Alias** – Indique un alias à utiliser avec cette page.
   * Par exemple, si vous définissez l’alias de `private` pour la page `/content/wknd/us/en/magazine/members-only`, alors cette page est également accessible via `/content/wknd/us/en/magazine/private`.
   * La création d’un alias permet de définir la propriété `sling:alias` sur le nœud de page, ce qui affecte uniquement la ressource, et non le chemin d’accès au référentiel.
   * Les pages accessibles par alias dans l’éditeur ne peuvent pas être publiées. Les [options de publication](/help/sites-cloud/authoring/sites-console/publishing-pages.md) dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès.
   * Pour plus d’informations, consultez [Noms de page localisés dans les Bonnes pratiques de SEO et de gestion des URL](/help/overview/seo-and-url-management.md#localized-page-names).

### Configuration {#configuration}

* **Hérité de &lt;path>** - Activez/désactivez l’héritage de la **Configuration du cloud** de la page
   * Active/désactive la disponibilité de la **configuration cloud** pour modification

* **Configuration du cloud** – Chemin d’accès à la configuration sélectionnée

### Paramètres de modèles {#template-settings}

* **Modèles autorisés** – [Définit la liste des modèles qui seront disponibles](/help/sites-cloud/authoring/page-editor/templates.md#enabling-and-allowing-a-template-template-author) dans cette sous-branche
   * Chaque valeur doit être un chemin d’accès absolu vers un modèle.
   * Utilisez `/.*` pour autoriser tous les modèles sous ce chemin d’accès.
* **Utiliser la page comme modèle** - [Créez un modèle basé sur la page active.](/help/sites-cloud/authoring/universal-editor/templates.md)
   * S’applique uniquement aux pages créées pour être utilisées avec l’éditeur universel exploitant Edge Delivery Services.

### Exigence d’authentification {#authentication}

* **Activer** - Active l’utilisation de l’authentification pour accéder à la page

>[!NOTE]
>
>Les groupes d’utilisateurs fermés pour la page sont définis dans l’onglet **[Autorisations](#permissions)**.

* **Page de connexion** – Page à utiliser pour la connexion

### Export {#export}

* **Configuration de l’exportation** – Spécifie une configuration d’exportation.

## SEO {#seo}

* **URL canonique** - Utilisé pour remplacer l’URL canonique de la page
   * Si rien n’est indiqué, l’URL de la page correspond à son URL canonique.

* **Balises robots** - Utilisez la liste déroulante pour sélectionner les balises robots afin de contrôler le comportement des robots des moteurs de recherche
   * Certaines options sont en conflit les unes avec les autres. Dans ce cas, l’option la plus permissive est prioritaire.

* **Générer un plan de site** : lorsque cette option est sélectionnée, un `sitemap.xml` est généré pour cette page et ses descendants.

## Images {#images}

### Image en vedette {#featured-image}

Cette section permet de sélectionner et de configurer l’image à afficher. Cette option est utilisée dans les composants qui référencent la page, par exemple, les teasers, les listes de pages, etc.

* **Image** - Vous pouvez **Choisir** une ressource ou rechercher un fichier à charger, puis **Modifier** ou **Effacer** l’image sélectionnée.
* **Texte secondaire** - Texte utilisé pour représenter la signification et/ou la fonction de l’image, généralement utilisé par les lecteurs d’écran
* **Hériter - Valeur issue de la ressource DAM** - Lorsque cette case est cochée, le texte secondaire est renseigné avec la valeur des `dc:description`métadonnées dans la gestion des ressources numériques.

### Miniature {#thumbnail}

Cette section permet de sélectionner et de configurer la miniature de l’image de la page. Cette option est utilisée dans les composants qui référencent la page, par exemple, les teasers, les listes de pages, etc.

* **Générer l’aperçu** – Génère un aperçu de la page à utiliser comme miniature.
* **Télécharger l’image** – Transfère une image à utiliser comme miniature
* **Sélectionner une image** - Sélectionnez une ressource existante à utiliser comme miniature.
* **Rétablir** – Cette option n’est disponible qu’après avoir effectué une modification de la miniature. Si vous ne souhaitez pas conserver votre modification, vous pouvez la rétablir avant de l’enregistrer.

## Services cloud {#cloud-services}

* **Configurations de Cloud Service** - Définit la configuration utilisée pour les services cloud de la page
* **Hérité de** - Pour les Live Copies et les copies de langue, les configurations cloud sont par défaut héritées du plan directeur.
   * Décochez cette case pour remplacer l’héritage.

## Personnalisation {#personalization}

### Configurations ContextHub {#contexthub-config}

* **Chemin ContextHub** – Définit la [configuration ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md)
* **Chemin d’accès aux segments** – Définit le chemin d’accès aux [segments](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

### Configuration du ciblage {#targeting-config}

* **Marque** - Définit une [marque pour spécifier la portée du ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md)
   * Cette option nécessite que le compte utilisateur figure dans le groupe `Target Administrators`.

## Autorisations {#permissions}

Utilisez l’onglet **Autorisations** pour définir quels utilisateurs, groupes ou [groupes d’utilisateurs fermés (CUG)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html?lang=fr) peuvent accéder à la page et/ou la modifier.

* **Ajouter des autorisations**
* **Modifier le groupe d’utilisateurs fermé**
* Afficher les **autorisations effectives**

## Blueprint {#blueprint}

Cet onglet n’est visible que pour les pages qui servent de plan directeur. Les plans directeurs servent de base aux Live Copies, et font partie de la [gestion multisite.](/help/sites-cloud/administering/msm/overview.md)

* **Déploiement** - Lancez un déploiement du contenu du plan directeur sur les Live Copies
* **Aperçu de la Live Copy** - Ouvrez une fenêtre pour parcourir la structure de la page Live Copy
* **Live Copies actuelles** - Liste des pages basées sur (c’est-à-dire, Live Copies de) la page de plan directeur sélectionnée

## Live Copy {#live-copy}

Cet onglet n’est visible que pour les pages configurées en tant que Live Copies. Comme pour les [plans directeurs](#blueprint) les Live Copies font partie de la [gestion multisite](/help/sites-cloud/administering/msm/overview.md).

* **Synchroniser** - Synchroniser la Live Copy avec le plan directeur, en conservant les modifications locales.
* **Réinitialiser** - Réinitialiser la Live Copy à l’état de plan directeur, en supprimant les modifications locales.
* **Suspendre** – Suspendre la Live Copy des modifications de déploiement supplémentaires.
* **Désolidariser** - Désolidariser la Live Copy du plan directeur

### Source {#source}

* Affiche le chemin du plan directeur pour cette Live Copy

### Statut {#status}

* Liste l’état actuel de la Live Copy de la page

### Configuration {#live-copy-config}

* **Héritage de Live Copy** - Si cette option est cochée, la configuration de la Live Copy est effective sur tous les enfants.
* **Hériter des configurations de déploiement du parent** - Si cette option est cochée, la configuration de déploiement est héritée du parent de la page.
* **Choisir la configuration de déploiement** – Définit les circonstances dans lesquelles les modifications sont propagées à partir du plan directeur et disponibles uniquement lorsque **Hériter des configurations de déploiement du parent** n’est pas sélectionné
* **Liste des chemins exclus**

## Prévisualisation {#preview}

Lorsqu’un [environnement de prévisualisation](/help/sites-cloud/authoring/sites-console/previewing-content.md) est activé, les détails suivants sont disponibles :

* **URL de prévisualisation** - URL utilisée pour accéder au contenu dans l’environnement de prévisualisation

## Application web progressive {#progressive-web-app}

Grâce à une configuration simple, un créateur de contenu peut activer des fonctionnalités d’application web progressive (PWA) pour les expériences créées dans AEM Sites. Votre site peut ensuite se comporter comme une application native en devenant installable sur l’écran d’accueil de l’appareil des visiteurs et visiteuses et disponible hors ligne.

{{pwa-deprecation}}

### Configurer l’expérience d’installation {#config-pwa}

* **Activer PWA** - Lorsqu’il est activé, les visiteurs de la page peuvent installer le site en tant que PWA.
* **URL de démarrage** - URL à charger lorsque l’utilisateur lance l’application web
   * Si l’URL est relative, l’URL de manifeste est utilisée comme URL de base pour la résolution
   * Lorsqu’elle est vide, l’URL de la page à partir de laquelle l’application a été installée est utilisée.
   * Il est cependant recommandé de définir une valeur pour cette page.
* **Mode d’affichage** - Méthode de masquage ou d’affichage du navigateur sur l’appareil local
* **Orientation de l’écran** - Comment le PWA gérera les orientations de l’appareil
* **Couleur du thème** - La couleur de l’application qui affecte la manière dont le système d’exploitation de l’utilisateur local affiche la barre d’outils de l’interface utilisateur native et les commandes de navigation
* **Couleur d’arrière-plan** - Couleur d’arrière-plan de l’application affichée au chargement de l’application
* **Icône** - Icône représentant l’application sur l’appareil de l’utilisateur ou de l’utilisatrice lors de l’installation de PWA

### Gestion du cache (avancé) {#cache-management}

* **Stratégie de mise en cache et fréquence d’actualisation du contenu** - Définit le modèle de mise en cache de votre PWA.
* **Fichiers à mettre en cache pour une utilisation hors ligne**
   * **Prémise en cache des fichiers (aperçu technique)** - Les fichiers hébergés sur AEM sont enregistrés dans la mémoire cache du navigateur local lorsque l’agent de service effectue l’installation et avant son utilisation.
   * **Bibliothèques côté client** - Bibliothèques côté client à mettre en cache pour une expérience hors ligne
   * **Inclusions des chemins** - Les demandes réseau pour les chemins définis sont interceptées et le contenu mis en cache est renvoyé conformément à la stratégie de mise en cache et à la fréquence d’actualisation configurées pour le contenu
   * **Exclusions des chemins** - Ces fichiers ne seront jamais mis en cache, quels que soient les paramètres définis dans Prémise en cache des fichiers et dans Inclusions des chemins .

>[!NOTE]
>
>Voir [Activation des fonctionnalités d’application web progressive](/help/sites-cloud/authoring/sites-console/enable-pwa.md) pour plus d’informations.


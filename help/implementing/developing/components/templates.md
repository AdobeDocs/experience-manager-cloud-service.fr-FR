---
title: Modèles de page
description: Les modèles de page sont utilisés lors de la création d'une page qui sera utilisée comme base pour la nouvelle page.
translation-type: tm+mt
source-git-commit: 69756d6831678151b0e8eb73db81113d49f17447
workflow-type: tm+mt
source-wordcount: '3228'
ht-degree: 62%

---


# Modèles de page {#page-templates}

Lors de la création d’une page, vous devez sélectionner un modèle. Le modèle de page est utilisé comme base pour la nouvelle page. Le modèle définit la structure de la page créée, le contenu initial et les composants qui peuvent être utilisés (propriétés de conception). Il présente plusieurs avantages :

* Page Templates allow specialized authors to [create and edit templates](/help/sites-cloud/authoring/features/templates.md).
   * Ces auteurs spécialisés sont connus sous le nom de **créateurs (ou auteurs) de modèles**.
   * Les créateurs de modèles doivent être membres du groupe `template-authors`.
* Les modèles de page conservent une connexion dynamique à toutes les pages créées à partir d&#39;eux. De cette manière, toute modification apportée au modèle est répercutée dans les pages proprement dites.
* Les modèles de page rendent le composant de page plus générique afin que le composant de page principal puisse être utilisé sans personnalisation.

Avec les modèles de page, les éléments qui créent une page sont isolés dans les composants. Vous pouvez configurer les combinaisons de composants nécessaires dans une interface utilisateur, rendant ainsi inutile le développement d’un nouveau composant de page pour chaque variante de page.

Ce document :

* Donne un aperçu de la création d&#39;un modèle de page
* décrit les tâches d’administration/de développement requises pour créer des modèles modifiables ;
* décrit les bases techniques des modèles modifiables.
* Décrit comment AEM évalue la disponibilité d’un modèle

>[!NOTE]
>
>Dans ce document, nous partons du principe que vous êtes déjà rompu à la création et la modification de modèles. Consultez le document [Création de modèles de page](/help/sites-cloud/authoring/features/templates.md) qui détaille les fonctionnalités des modèles modifiables telles qu’elles sont présentées au créateur d’un modèle.

>[!TIP]
>
>[Le didacticiel](/help/implementing/developing/introduction/develop-wknd-tutorial.md) WKND explique en détail comment utiliser les modèles de page en implémentant un exemple et est très utile pour comprendre comment configurer un modèle dans un nouveau projet.

## Création d’un modèle {#creating-a-new-template}

Creating Page Templates is primarily done with the [template console and template editor](/help/sites-cloud/authoring/features/templates.md) by a template author. Cette section vous donne un aperçu de ce processus. Elle décrit ensuite ce qui se passe au niveau technique.

Lors de la création d’un modèle modifiable :

1. Créez un [dossier pour les modèles](#template-folders). Il ne s’agit pas d’une pratique obligatoire, mais vivement recommandée.
1. Sélectionnez un [type de modèle](#template-type). Il est copié afin de créer la [définition du modèle](#template-definitions).

   >[!NOTE]
   >
   >Une sélection de types de modèle prêts à l’emploi est fournie. Au besoin, vous pouvez également [créer vos propres types de modèles spécifiques à un site](#creating-template-types).

1. Configurez la structure, les stratégies de contenu, le contenu initial et la disposition du nouveau modèle.

   **Structure**

   * La structure vous permet de définir les composants et le contenu de votre modèle.
   * Les composants définis dans la structure du modèle ne peuvent être ni déplacés ni supprimés dans les pages créées.
   * Si vous souhaitez que les créateurs de pages puissent ajouter et supprimer des composants, ajoutez un système de paragraphes au modèle.
   * Les composants peuvent être déverrouillés (et reverrouillés) pour que vous puissiez définir le contenu initial.

   Pour plus d’informations sur la façon dont un créateur de modèles définit la structure, voir [Création de modèles de page](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author).

   Pour connaître les détails techniques de la structure, consultez la section [Structure](#structure) de ce document.

   **Stratégies**

   * Les stratégies de contenu définissent les propriétés de conception d’un composant.

      * Par exemple, les composants disponibles ou les dimensions minimales/maximales.
   * Elles s’appliquent au modèle (et aux pages créées avec le modèle).

   Pour plus d’informations sur la façon dont un créateur de modèles définit des stratégies, voir [Création de modèles de page](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author).

   Pour connaître les détails techniques des stratégies, consultez la section [Stratégies de contenu](#content-policies) de ce document.

   **Contenu initial**

   * Le contenu initial définit le contenu qui s’affiche lors de la création d’une page basée sur le modèle.
   * Le contenu initial peut ensuite être modifié par les créateurs de la page.

   Pour plus d’informations sur la façon dont un créateur de modèles définit la structure, voir [Création de modèles de page](/help/sites-cloud/authoring/features/templates.md#editing-a-template-initial-content-author).

   Pour connaître les détails techniques du contenu initial, consultez la section [Contenu initial](#initial-content) de ce document.

   **Mise en page**

   * Vous pouvez définir la mise en page du modèle pour différents appareils.
   * La mise en page réactive pour les modèles fonctionne de la même manière que pour la création de pages.

   Pour plus d’informations sur la façon dont le créateur d’un modèle définit la mise en page de ce dernier, voir [Création de modèles de page](/help/sites-cloud/authoring/features/templates.md#editing-a-template-layout-template-author).

   Pour connaître les détails techniques de la mise en page du modèle, consultez la section [Mise en page](#layout) de ce document.

1. Activez le modèle, puis autorisez-le pour des arborescences de contenu spécifiques.

   * Un modèle peut être activé ou désactivé pour être mis à la disposition (ou non) des créateurs de pages.
   * Un modèle peut être rendu disponible ou indisponible pour certaines branches de la page.

   Pour plus d’informations sur la façon dont un créateur de modèles active un modèle, voir [Création de modèles de page](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author).

   Pour obtenir des informations techniques sur l’activation d’un modèle, consultez la section [Activation et autorisation d’un modèle à utiliser](#enabling-and-allowing-a-template-for-use) dans ce document

1. Utilisez-le pour créer des pages de contenu.

   * Lorsque vous utilisez un modèle pour créer une page, il n’existe aucune différence visible ni indication permettant de distinguer les modèles statiques des modèles modifiables.
   * Pour le créateur de pages, le processus est transparent.

   For details on how a page author uses templates to create a page, see [Creating and Organizing Pages](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#templates).

   Pour obtenir des informations techniques sur la création de pages à l’aide de modèles modifiables, consultez la section [Pages de contenu créées](#resultant-content-pages) de ce document.

>[!NOTE]
>
>The editor client library assumes the presence of the `cq.shared` namespace in content pages, and if it is absent the JavaScript error `Uncaught TypeError: Cannot read property 'shared' of undefined` will result.
>
>`cq.shared` est inclus dans tous les exemples de pages de contenu. Par conséquent, tout contenu basé sur ces pages inclut automatiquement `cq.shared`. Toutefois, si vous décidez de créer vos propres pages de contenu à partir de zéro, sans vous servir de l’exemple de contenu, vous devez veiller à inclure l’espace de noms `cq.shared`.
>
>Pour plus d’informations, voir [Utilisation des bibliothèques côté client](/help/implementing/developing/introduction/clientlibs.md).

>[!CAUTION]
>
>Ne saisissez jamais d’informations qui doivent être internationalisées dans un modèle.

## Dossiers de modèles {#template-folders}

Pour organiser vos modèles, vous pouvez utiliser les dossiers suivants :

* `global`
* Spécifique au site

>[!NOTE]
>
>Bien que vous puissiez imbriquer vos dossiers, lorsque l’utilisateur les visualise dans la console **Modèles**, ils sont présentés sous la forme d’une structure plate.

Dans une instance AEM standard, le dossier `global` existe déjà dans la console de modèles. Il contient les modèles par défaut et fait office de dossier de rechange si le dossier actif ne contient pas de stratégies et/ou de types de modèles. Vous pouvez soit ajouter vos modèles par défaut à ce dossier, soit créer un dossier (recommandé).

>[!NOTE]
>
>It is best practice to create a new folder to hold your customized templates and not to use the `global` folder.

>[!CAUTION]
>
>Les dossiers doivent être créés par un utilisateur disposant des droits `admin`.

Les types de modèles et les politiques sont hérités dans tous les dossiers selon l’ordre de priorité suivant :

1. Le dossier actuel
1. Parent(s) du dossier actuel
1. `/conf/global`
1. `/apps`
1. `/libs`

Une liste de toutes les entrées autorisées est créée. If any configurations overlap ( `path`/ `label`), only the instance closest to the current folder is presented to the user.

Pour créer un dossier, vous pouvez procéder de l’une des façons suivantes :

* Soit par programmation, soit en utilisant CRXDE Lite
* Using the [Configuration Browser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

## Utilisation de CRXDE Lite {#using-crxde-lite}

1. Un nouveau dossier (sous /conf) peut être créé pour votre instance par programmation ou avec un CRXDE Lite.

   La structure ci-dessous doit être utilisée :

   ```xml
   /conf
       <your-folder-name> [sling:Folder]
           settings [sling:Folder]
               wcm [cq:Page]
                   templates [cq:Page]
                   policies [cq:Page]
   ```

1. Vous pouvez ensuite définir les propriétés ci-dessous sur le nœud racine du dossier :

   `<your-folder-name> [sling:Folder]`

   * Nom : `jcr:title`
   * Type : `String`
   * Valeur : titre (du dossier) que vous souhaitez afficher dans la console **Modèles**.

1. Outre les autorisations et les droits de création standard (par exemple, `content-authors`), vous devez maintenant affecter les groupes et définir les droits d’accès nécessaires (listes de contrôle d’accès) pour que les créateurs puissent créer des modèles dans le nouveau dossier.

   Le groupe `template-authors` est le groupe par défaut qui doit être affecté. See the section [ACLs and Groups](#acls-and-groups) for details.

   <!--See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.-->

### Utilisation de l’explorateur de configurations {#using-the-configuration-browser}

1. Accédez à **Navigation globale** -> **Outils** > [**Explorateur de configurations**.](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

   The existing folders are listed to the left including the `global` folder.

1. Cliquez sur **Créer**.
1. In the **Create Configuration** dialog the following fields need to be configured:

   * **Titre** : indiquez un titre pour le dossier de configuration.
   * **Modèles modifiables** : cochez la case pour autoriser les modèles modifiables dans ce dossier.

1. Cliquez sur **Créer**

>[!NOTE]
>
>In the [Configuration Browser,](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) you can edit the global folder and activate the **Editable Templates** option if you wish to create templates within this folder, however this is not recommended best practice.

### ACL et groupes {#acls-and-groups}

Une fois vos dossiers de modèles créés (soit via CRXDE, soit à l’aide de l’explorateur de configurations), des listes de contrôle d’accès (ACL) doivent être définies pour les groupes appropriés afin que les dossiers de modèles garantissent une protection adéquate.

The template folders for the [WKND tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) can be used as an example.

#### Groupe template-authors {#the-template-authors-group}

Le groupe `template-authors` est utilisé pour gérer l’accès aux modèles. Il est fourni en standard avec AEM, mais il est vide. Les utilisateurs doivent donc être ajoutés au groupe pour le projet/site.

>[!CAUTION]
>
>Le groupe `template-authors` est destiné uniquement aux utilisateurs qui doivent pouvoir créer des modèles.
>
>La modification de modèles est très puissante et si elle n&#39;est pas effectuée correctement, les modèles existants peuvent être endommagés. Par conséquent, ce rôle doit être ciblé et ne contenir que des utilisateurs qualifiés.

Le tableau suivant récapitule les autorisations nécessaires pour la modification de modèles.

<table>
 <tbody>
  <tr>
   <th>Chemin   </th>
   <th>Rôle/Groupe</th>
   <th>Autorisations<br /> </th>
   <th>Description</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>Template Authors<br /> </td>
   <td>lecture, écriture, réplication</td>
   <td>Les auteurs de modèles qui créent, lisent, mettent à jour, suppriment et répliquent des modèles dans un <code>/conf</code> espace spécifique au site</td>
  </tr>
  <tr>
   <td>Utilisateur Web anonyme</td>
   <td>lire</td>
   <td>L'utilisateur Web anonyme doit lire les modèles lors du rendu d'une page.</td>
  </tr>
  <tr>
   <td>Auteurs de contenu</td>
   <td>répliquer</td>
   <td>Les auteurs replicateContent doivent activer les modèles d’une page lors de l’activation d’une page.</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>lecture, écriture, réplication</td>
   <td>Les auteurs de modèles qui créent, lisent, mettent à jour, suppriment et répliquent des modèles dans un <code>/conf</code> espace spécifique au site</td>
  </tr>
  <tr>
   <td>Utilisateur Web anonyme</td>
   <td>lire</td>
   <td>L’utilisateur Web anonyme doit lire les stratégies lors du rendu d’une page.</td>
  </tr>
  <tr>
   <td>Auteurs de contenu</td>
   <td>répliquer</td>
   <td>Les auteurs de contenu doivent activer les stratégies d’un modèle de page lors de l’activation d’une page.</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>Auteur de modèle</td>
   <td>lire</td>
   <td>L’auteur de modèles crée un modèle basé sur l’un des types de modèles prédéfinis.</td>
  </tr>
  <tr>
   <td>Utilisateur Web anonyme</td>
   <td>none</td>
   <td>L'utilisateur Web anonyme ne doit pas accéder aux types de modèles</td>
  </tr>
 </tbody>
</table>

This default `template-authors` group only covers the project setups, where all `template-authors` members are allowed to access and author all templates. S’agissant des configurations plus complexes, dans lesquelles plusieurs groupes d’auteurs de modèles sont nécessaires pour séparer l’accès aux modèles, il convient de créer davantage de groupes de ce type. Cependant, les autorisations relatives aux groupes d’auteurs de modèles restent les mêmes.

## Type de modèle {#template-type}

Lors de la création d’un modèle, vous devez spécifier un type :

* Ces types de modèle fournissent effectivement des modèles pour un modèle. Lors de la création d’un modèle, la structure et le contenu initial du type sélectionné sont utilisés.

   * Le type est copié afin de créer le modèle.
   * Une fois la copie effectuée, la seule connexion entre le modèle et son type est une référence statique à des fins d’information.

* Les types de modèle vous permettent de définir les éléments suivants :

   * Le type de ressource du composant de page.
   * La stratégie du nœud racine, laquelle définit les composants autorisés dans l’éditeur de modèles.
   * Il est recommandé de définir les points d’arrêt pour la grille réactive et la configuration de l’émulateur mobile au niveau du type d’émulateur.

* AEM fournit une petite sélection de types de modèle prêts à l’emploi tels que Page HTML5 et Page de formulaire adaptatif.

   * Des exemples supplémentaires sont fournis dans le didacticiel de [WKND.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

* En règle générale, les types de modèle sont définis par des développeurs.

Les types de modèle prêts à l’emploi sont stockés sous :

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>Vous ne devez rien modifier dans le chemin `/libs`. Cela est dû au fait que le contenu de `/libs` peut être remplacé à tout moment par une mise à jour de AEM.

Les types de modèle spécifiques à un site doivent être stockés dans l’emplacement comparable :

* `/apps/settings/wcm/template-types`

Definitions for your customized templates types should be stored in user-defined folders (recommended) or alternatively in `global`. Par exemple :

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>The template types have to respect the correct folder structure (i.e. `/settings/wcm/...`), otherwise the template types will not be found.

<!--
### Template Type and Mobile Device Groups {#template-type-and-mobile-device-groups-br}

The [device groups](/help/sites-developing/mobile.md#device-groups) used for an editable template (set as relative path of the property `cq:deviceGroups`) define which mobile devices are available as emulators in the [layout mode](/help/sites-authoring/responsive-layout.md) of page authoring. This value can be set in two places:

* On the editable template type
* On the editable template

When creating a new editable template, the value is copied from the template type to the individual template. If the value is not set on the type, it can be set on the template. Once a template is created, there is no inheritance from the type to the template.

>[!CAUTION]
>
>The value of `cq:deviceGroups` must be set as a relative path such as `mobile/groups/responsive` and not as an absolute path such as `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>With static templates /help/sites-developing/page-templates-static.md, the value of `cq:deviceGroups` could be set at the root of the site.
>
>With editable templates, this value is now stored at the template level and is not supported at the page root level.
-->

### Création de types de modèle {#creating-template-types}

Si vous avez créé un modèle qui peut servir de base pour d’autres modèles, vous pouvez le copier en tant que type de modèle.

1. Create a template as you would any Page Template [as documented here](/help/sites-cloud/authoring/features/templates.md#creating-a-new-template-template-author), which will serve as the basis of your template type.
1. À l’aide de CRXDE Lite, copiez le nouveau modèle depuis le nœud `templates` dans le nœud `template-types` sous le [dossier de modèles](#template-folders).
1. Delete the template from the `templates` node under the [template folder](#template-folders).
1. In the copy of the template that is under the `template-types` node, delete all `cq:template` and `cq:templateType` `jcr:content` properties.

Vous pouvez également développer votre propre type de modèle en utilisant un exemple de modèle modifiable comme base (disponible sur GitHub).

CODE SUR GITHUB

Vous pouvez trouver le code de cette page sur GitHub.

* [Ouvrez un projet aem-sites-example-custom-template-type sur GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Téléchargez le projet sous la forme d’[un fichier ZIP](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip).

## Définitions de modèle {#template-definitions}

Les définitions des modèles modifiables sont stockées dans des [dossiers définis par l’utilisateur](#template-folders) (ce qui est recommandé) ou bien dans `global`. Par exemple :

* `/conf/<my-folder>/settings/wcm/templates`
* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/templates`
* `/conf/global/settings/wcm/templates`

Le nœud racine du modèle est de type `cq:Template` avec l’ossature suivante :

```xml
<template-name>
  initial
    jcr:content
      root
        <component>
        ...
        <component>
  jcr:content
    @property status
  policies
    jcr:content
      root
        @property cq:policy
        <component>
          @property cq:policy
        ...
        <component>
          @property cq:policy
  structure
    jcr:content
      root
        <component>
        ...
        <component>
      cq:responsive
        breakpoints
  thumbnail.png
```

Les éléments principaux sont les suivants :

* `<template-name>`

   * ` [initial](#initial-content)`
   * `jcr:content`
   * ` [structure](#structure)`
   * ` [policies](#policies)`
   * `thumbnail.png`

### jcr:content {#jcr-content}

Ce nœud contient des propriétés pour le modèle :

* **Nom** : `jcr:title`
* **Nom** : `status`
   * ``**Type**: `String`
   * **Valeur**: `draft`, `enabled` ou `disabled`

### Structure {#structure}

Définit la structure de la page créée :

* Is merged with the initial content ( `/initial`) when creating a new page.
* Les modifications apportées à la structure sont répercutées dans toute page créée avec le modèle.
* The `root` ( `structure/jcr:content/root`) node defines the list of components that will be available in the resulting page.
   * Les composants définis dans la structure du modèle ne peuvent être ni déplacés ni supprimés dans les pages créées.
   * Une fois qu’un composant est déverrouillé, la propriété `editable` est définie sur `true`.
   * Dès qu’un composant non vide est déverrouillé, son contenu est déplacé vers la branche `initial`.

* The `cq:responsive` node holds definitions for the responsive layout.

### Contenu initial {#initial-content}

Définit le contenu initial dont une nouvelle page disposera au moment de sa création :

* Contient un nœud `jcr:content` copié dans toute nouvelle page.
* Is merged with the structure ( `/structure`) when creating a new page.
* Aucune page existante n’est mise à jour si le contenu initial est modifié après la création.
* Le nœud `root` contient une liste de composants permettant de définir les éléments qui seront disponibles dans la page créée.
* Si du contenu est ajouté à un composant en mode de structure et que ce composant est ensuite déverrouillé (ou inversement), ce contenu est utilisé comme contenu initial.

### Mise en page {#layout}

Lorsque vous [modifiez un modèle, vous pouvez définir la mise en page](/help/sites-cloud/authoring/features/templates.md), cette dernière utilise une mise en page [réactive](/help/sites-cloud/authoring/features/responsive-layout.md)standard.

<!-- that can also be [configured](/help/sites-administering/configuring-responsive-layout.md). -->

### Stratégies de contenu {#content-policies}

Les stratégies de contenu définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle). Les stratégies de contenu peuvent être créées et sélectionnées dans l’éditeur de modèles.

* The property `cq:policy`, on the `root` node
   `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Fournit une référence relative à la stratégie de contenu pour le système de paragraphes de la page.

* The property `cq:policy`, on the component-explicit nodes under `root`, provide links to the policies for the individual components.

* Les définitions de stratégie réelles sont stockées sous :
   `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>Les chemins d’accès des définitions de stratégie dépendent du chemin du composant. `cq:policy` contient une référence relative à la configuration elle-même.

### Stratégies de page {#page-policies}

Les stratégies de page vous permettent de définir la [stratégie de contenu](#content-policies) de la page (système de paragraphes principal), soit dans le modèle soit dans les pages créées.

### Activation et autorisation d’un modèle à utiliser {#enabling-and-allowing-a-template-for-use}

1. **Activation du modèle**

   Avant de pouvoir être utilisé, un modèle doit être activé en effectuant l’une des opérations suivantes :

   * [Activer le modèle](/help/sites-cloud/authoring/features/templates.md) à partir de la console **Modèles**.

   * Setting the status property on the `jcr:content` node.

      * Par exemple, on :
         `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Définissez la propriété :

         * Nom : status
         * Type : Chaîne
         * Valeur : `enabled`

1. **Modèles autorisés**

   * [Définissez le(s) chemin(s) d’accès des modèles autorisés dans les **Propriétés de page**](/help/sites-cloud/authoring/features/templates.md#allowing-a-template-author) de la page appropriée ou de la page racine d’une sous-branche.
   * Définissez la propriété :
      `cq:allowedTemplates`
Sur la 
`jcr:content` du noeud de la branche requise.
   Par exemple, avec la valeur suivante :

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Pages de contenu créées {#resultant-content-pages}

Les pages créées à partir de modèles modifiables :

* sont créées avec une sous-arborescence qui est fusionnée à partir de `structure` et `initial` dans le modèle ;

* contiennent des références aux informations contenues dans le modèle et le type de modèle. Pour cela, on utilise un nœud `jcr:content` avec les propriétés suivantes :

   * `cq:template` - Fournit la référence dynamique au modèle proprement dit ; fait en sorte que les modifications apportées au modèle soient répercutées sur les pages proprement dites.

   * `cq:templateType` - Fournit une référence au type de modèle.

![Comment les modèles, le contenu et les composants interagissent](assets/templates-content-components.png)

Le schéma ci-dessus montre la corrélation entre les modèles, le contenu et les composants :

* Contrôleur - `/content/<my-site>/<my-page>` - Page résultante référençant le modèle. Le contenu contrôle l’ensemble du processus. En fonction des définitions, il accède au modèle et aux composants appropriés.
* Configuration - `/conf/<my-folder>/settings/wcm/templates/<my-template>` - Le [modèle et les stratégies](#template-definitions) de contenu associées définissent la configuration de la page.
* Model - OSGi bundles - The [OSGI bundles](/help/implementing/deploying/configuring-osgi.md) implement the functionality.
* View - `/apps/<my-site>/components` - On both the author and publish environments the content is rendered by components.

Lors du rendu d’une page :

* **Modèles**:

   * The `cq:template` property of its `jcr:content` node will be referenced to access the template that corresponds to that page.

* **Composants**:

   * The page component will merge the `structure/jcr:content` tree of the template with the `jcr:content` tree of the page.
      * Le composant de page autorisera uniquement l’auteur à modifier les nœuds de la structure du modèle qui ont été marqués comme étant modifiables (ainsi que ses éventuels enfants).
      * Lors du rendu d’un composant sur une page, le chemin d’accès relatif de ce composant est prélevé dans le nœud `jcr:content` ; une recherche est ensuite effectuée dans le même emplacement sous le nœud `policies/jcr:content` du modèle.
         * The `cq:policy` property of this node points to the actual content policy (i.e. it holds the design configuration for that component).
            * De cette manière, vous pouvez disposer de plusieurs modèles qui réutilisent les mêmes configurations de stratégie de contenu.

### Disponibilité des modèles {#template-availability}

Lors de la création d’une page dans l’interface admin du site, la liste des modèles disponibles dépend de l’emplacement de la nouvelle page et des restrictions de positionnement spécifiées dans chaque modèle.

Les propriétés suivantes déterminent si un modèle `T` peut être utilisé pour qu’une nouvelle page soit placée en tant qu’enfant de la page `P`. Chacune de ces propriétés est une chaîne à valeurs multiples contenant zéro ou plusieurs expressions régulières utilisées pour la correspondance avec les chemins :

* The `cq:allowedTemplates` property of the `jcr:content` subnode of `P` or an ancestor of `P`.

* La `allowedPaths` propriété de `T`.

* La `allowedParents` propriété de `T`.

* The `allowedChildren` property of the template of `P`.

L’évaluation fonctionne comme suit :

* The first non-empty `cq:allowedTemplates` property found while ascending the page hierarchy starting with `P` is matched against the path of `T`. Si aucune des valeurs ne correspond, `T`est rejeté.

* If `T` has a non-empty `allowedPaths` property, but none of the values match the path of `P`, `T` is rejected.

* If both of the above properties are either empty or non-existent, `T` is rejected unless it belongs to the same application as `P`. `T` appartient à la même application que `P` si et seulement si le nom du deuxième niveau du chemin de `T` est identique à celui du deuxième niveau du chemin de `P`. For example, the template `/apps/geometrixx/templates/foo` belongs to the same application as the page `/content/geometrixx`.

* If `T` has an non-empty `allowedParents` property, but none of the values match the path of `P`, `T` is rejected.

* If the template of `P` has a non-empty `allowedChildren` property, but none of the values match the path of `T`, `T` is rejected.

* Dans tous les autres cas, `T`est autorisé.

Le diagramme suivant illustre le processus d’évaluation de modèle :

![Processus d’évaluation des modèles](assets/template-evaluation.png)

>[!CAUTION]
>
>aem offre plusieurs propriétés pour contrôler les modèles autorisés sous **Sites**. Cependant, leur combinaison peut conduire à des règles très complexes, difficiles à suivre et à gérer.
>
>Par conséquent, l’Adobe vous recommande de début simple en définissant :
>
>* uniquement la `cq:allowedTemplates` propriété
   >
   >
* uniquement sur la racine du site
>
>
Pour consulter un exemple, reportez-vous au didacticiel [](/help/implementing/developing/introduction/develop-wknd-tutorial.md) WKND : `/content/wknd/jcr:content`
>
>Les propriétés `allowedPaths`, `allowedParents`et `allowedChildren` peuvent également être placées sur les modèles pour définir des règles plus élaborées. Cependant, dans la mesure du possible, il est *beaucoup* plus simple de définir d&#39;autres `cq:allowedTemplates` propriétés sur des sous-sections du site si des restrictions supplémentaires s&#39;imposent pour les modèles autorisés.
>
>Un autre avantage est que les `cq:allowedTemplates` propriétés peuvent être mises à jour par un auteur dans l’onglet **Avancé** des Propriétés **de la** page. Les autres propriétés de modèle ne peuvent pas être mises à jour à l’aide de l’interface utilisateur (standard). Il faudrait donc qu’un développeur conserve les règles et qu’un déploiement du code soit effectué pour chaque modification.

#### Limitation des modèles utilisés dans les pages enfants {#limiting-templates-used-in-child-pages}

To limit what templates can be used to create child pages under a given page, use the `cq:allowedTemplates` property of `jcr:content` node of the page to specify the list of templates to be allowed as child pages. Each value in the list must be an absolute path to a template for an allowed child page, for example `/apps/wknd/templates/page-content`.

You can use the `cq:allowedTemplates` property on the template&#39;s  `jcr:content` node to have this configuration applied to all newly created pages that use this template.

Si vous souhaitez ajouter d’autres contraintes, par exemple concernant la hiérarchie des modèles, vous pouvez appliquer les propriétés `allowedParents/allowedChildren` sur le modèle. Vous pouvez ensuite spécifier explicitement que les pages créées à partir d’un modèle T doivent être des parents/enfants de pages créées à partir d’un modèle T.

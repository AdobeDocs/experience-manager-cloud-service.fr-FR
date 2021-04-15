---
title: Création et synchronisation de Live Copies
description: Découvrez comment créer et synchroniser des Live Copies pour réutiliser votre contenu sur votre site.
feature: Multi Site Manager
role: Administrator
exl-id: 53ed574d-e20d-4e73-aaa2-27168b9d05fe
translation-type: tm+mt
source-git-commit: 1ba90d9ccbae70c612e223835fbeb4dfdaf60975
workflow-type: tm+mt
source-wordcount: '4192'
ht-degree: 41%

---

# Création et synchronisation de Live Copies {#creating-and-synchronizing-live-copies}

Vous pouvez créer une Live Copy à partir d’une configuration de page ou de plan afin de réutiliser ce contenu sur votre site. Gérez l’héritage et la synchronisation, vous pouvez contrôler la propagation des modifications apportées au contenu.

## Gestion des configurations de plans directeurs {#managing-blueprint-configurations}

Une configuration de plan identifie un site Web existant que vous souhaitez utiliser comme source pour une ou plusieurs pages Live Copy.

>[!TIP]
>
>Les configurations de plan directeur vous permettent d&#39;envoyer les modifications de contenu aux Live Copies. Voir [Live Copies - Source, plans directeurs et configurations de plan directeur](overview.md#source-blueprints-and-blueprint-configurations).

Lorsque vous créez une configuration de plan directeur, vous sélectionnez un modèle qui définit la structure interne du plan directeur. Le modèle de plan directeur par défaut suppose que le site web source présente les caractéristiques suivantes :

* Le site web possède une page racine.
* Les pages enfants immédiates de la racine sont des branches de langue du site web. Lors de la création d’une Live Copy, les langues sont présentées comme du contenu facultatif à inclure dans la copie.
* La racine de chaque branche de langue possède une ou plusieurs pages enfants. Lors de la création d’une Live Copy, les pages enfants sont présentées de sorte que vous puissiez les inclure dans la Live Copy.

>[!NOTE]
>
>Une structure différente requiert un modèle de plan différent.

Après avoir créé la configuration de plan directeur, configurez les propriétés suivantes :

* **Nom** : le nom de la configuration de plan directeur
* **Chemin source** : le chemin d’accès de la page racine du site que vous utilisez comme source (plan directeur)
* **Description**. (Facultatif) Description de la configuration du plan directeur, qui s&#39;affiche dans la liste des configurations du plan à choisir lors de la création d&#39;un site.

Lorsque votre configuration de plan directeur est utilisée, vous pouvez l&#39;associer à une configuration de déploiement qui détermine comment les Live Copies de la source/plan directeur sont synchronisées. Voir [Spécification des configurations de déploiement à utiliser](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use).

### Création d’une configuration de plan directeur {#creating-a-blueprint-configuration}

Pour créer une configuration de plan directeur :

1. [Accédez](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) au menu **Outils**, puis sélectionnez le menu **Sites**.
1. Sélectionnez **Plans directeurs** pour ouvrir la console **Configurations de plans directeurs** :

   ![Configurations du plan directeur](../assets/blueprint-configurations.png)

1. Sélectionnez **Créer**.
1. Sélectionnez le modèle de plan directeur, puis **Suivant** pour continuer.
1. Choisissez la page source à utiliser comme plan directeur, puis cliquez sur **Suivant** pour continuer.
1. Définissez les éléments suivants :

   * **Titre** : titre obligatoire du plan directeur
   * **Description** : description facultative pour fournir plus de détails.

1. L’option **Créer** crée la configuration de plan directeur selon votre spécification.

### Modification ou suppression d’une configuration de plan directeur  {#editing-or-deleting-a-blueprint-configuration}

Vous pouvez modifier ou supprimer une configuration de plan directeur existante :

1. [Accédez](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) au menu **Outils**, puis sélectionnez le menu **Sites**.
1. Sélectionnez **Plans directeurs** pour ouvrir la console **Configurations de plans directeurs** :

   ![Configurations du plan directeur](../assets/blueprint-configurations.png)

1. Sélectionnez la configuration de plan directeur requise ; les actions appropriées deviennent disponibles dans la barre d’outils :

   * **Propriétés** : vous pouvez utiliser cette option pour afficher puis modifier les propriétés de la configuration.
   * **Supprimer**

## Création d’une Live Copy {#creating-a-live-copy}

Il existe plusieurs façons de créer une Live Copy.

### Création d’une Live Copy d’une page {#creating-a-live-copy-of-a-page}

Vous pouvez créer une Live Copy de n’importe quelle page ou branche. Lorsque vous créez Live Copy, vous pouvez spécifier les configurations de déploiement à utiliser pour la synchronisation du contenu :

* Les configurations de déploiement sélectionnées s’appliquent à la page Live Copy et à ses pages enfants.
* Si vous ne spécifiez aucune configuration de déploiement, MSM détermine les configurations de déploiement à utiliser. Voir [Spécification de la configuration de déploiement à utiliser](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use).

Vous pouvez créer une copie dynamique de n’importe quelle page :

* Pages référencées par une configuration de plan directeur [](#creating-a-blueprint-configuration)
* Et des pages n’ayant aucune connexion avec une configuration
* Live Copy dans les pages d’une autre Live Copy ([Live Copies imbriquées](overview.md#nested-live-copies))

La seule différence est que la disponibilité de la commande **Déployer** sur les pages source/de plan directeur dépend du référencement ou non de la source par une configuration de plan directeur :

* Si vous créez la Live Copy à partir d&#39;une page source **référencée** dans une configuration de plan, la commande Déploiement est alors disponible sur les pages source/plan.
* Si vous créez la Live Copy à partir d&#39;une page source **qui n&#39;est pas** référencée dans une configuration de plan, la commande Déploiement n&#39;est pas disponible sur les pages source/plan.

Pour créer une Live Copy :

1. Dans la console **Sites**, sélectionnez **Créer**, puis **Live Copy**.

   ![Créer une Live Copy](../assets/create-live-copy.png)

1. Sélectionnez la page source et appuyez ou cliquez sur **Suivant**. Par exemple :

   ![Sélectionner la source Live Copy](../assets/live-copy-from.png)

1. Spécifiez le chemin de destination de la Live Copy (ouvrez le dossier parent/page de la Live Copy), puis cliquez ou appuyez sur **Suivant**.

   ![Sélectionner la destination Live Copy](../assets/live-copy-to.png)

   >[!NOTE]
   >
   >Le chemin de destination ne peut pas être dans le chemin source.

1. Entrer :

   * Le **Titre** de la page.
   * Le **Nom** utilisé dans l’URL.

   ![Propriétés de Live Copy](../assets/live-copy-properties.png)

1. Utilisez la case **Exclure les sous-pages** :

   * Sélectionné : créer une Live Copy de la page sélectionnée uniquement (Live Copy peu profond)
   * Non sélectionné : créer une Live Copy qui inclut tous les descendants de la page sélectionnée (Live Copy profond)

1. (Facultatif) Pour spécifier une ou plusieurs configurations de déploiement à utiliser pour Live Copy, utilisez la liste déroulante **Configurations de déploiement** pour les sélectionner. Les configurations sélectionnées s’affichent sous le sélecteur déroulant.
1. Cliquez ou appuyez sur **Créer**. Un message de confirmation s’affiche, dans lequel vous pouvez sélectionner **Ouvrir** ou **Terminé**.

### Création d’une Live Copy d’un site à partir d’une configuration de plan directeur  {#creating-a-live-copy-of-a-site-from-a-blueprint-configuration}

Créez une Live Copy en utilisant une configuration de plan pour créer un site basé sur le contenu du plan (source). Lorsque vous créez une Live Copy à partir d&#39;une configuration de plan, vous sélectionnez une ou plusieurs branches de langue de la source de plan à copier, puis vous sélectionnez les chapitres à copier à partir des branches de langue. Voir [Création d&#39;une configuration de plan directeur](#creating-a-blueprint-configuration).

Si vous omettez certaines branches de langue de la Live Copy, vous pouvez les ajouter ultérieurement. Voir [Création d’une copie dynamique dans une copie dynamique (configuration du plan directeur)](#creating-a-live-copy-inside-a-live-copy-blueprint-configuration) pour plus d’informations.

>[!CAUTION]
>
>Lorsque la source du plan directeur contient des liens et des références qui cible un paragraphe dans une autre branche, les cibles ne sont pas mises à jour dans les pages Live Copy, mais restent pointées vers la destination d&#39;origine.

Lorsque vous créez le site, saisissez des valeurs pour les propriétés suivantes :

* **Langues** initiales : Les branches de langue de la source du plan directeur à inclure dans la Live Copy
* **Chapitres** initiaux : Pages enfants des branches de langue du plan directeur à inclure dans la Live Copy
* **Chemin** de destination : Emplacement de la page racine du site Live Copy
* **Titre** : Titre de la page racine du site Live Copy
* **Nom** : (Facultatif) Nom du noeud JCR qui stocke la page racine de la Live Copy (la valeur par défaut est basée sur le titre)
* **Propriétaire** du site : (Facultatif) Informations sur le responsable de la Live Copy
* **Live Copy** : sélectionnez cette option pour établir une relation en direct avec le site source. Si vous ne sélectionnez pas cette option, une copie du plan directeur est créée, mais n’est pas ensuite synchronisée avec la source.
* **Configurations** de déploiement : (Facultatif) Sélectionnez une ou plusieurs configurations de déploiement à utiliser pour la synchronisation de Live Copy. Par défaut, les configurations de déploiement sont héritées du plan directeur. Voir [Spécification des configurations de déploiement à utiliser](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use) pour plus d&#39;informations.

Pour créer une copie dynamique d&#39;un site à partir d&#39;une configuration de plan :

1. Dans la console **Sites**, sélectionnez **Créer**, puis **Site** dans le sélecteur déroulant.
1. Sélectionnez la configuration du plan directeur à utiliser comme source de la Live Copy et passez à **Next** :

   ![Créer un site à partir d&#39;un plan](../assets/create-site-from-blueprint.png)

1. Utilisez le sélecteur **Langues initiales** pour spécifier la ou les langues du site du plan directeur à utiliser pour la Live Copy.

   Toutes les langues disponibles sont sélectionnées par défaut. Pour supprimer une langue, appuyez ou cliquez sur le **X** qui apparaît en regard de la langue.

   Par exemple :

   ![Spécification des propriétés lors de la création du site](../assets/create-site-properties.png)

1. Utilisez la liste déroulante **Chapitres initiaux** pour sélectionner les sections du plan à inclure dans la Live Copy. Tous les chapitres disponibles sont inclus par défaut, mais peuvent être supprimés.
1. Saisissez les valeurs des propriétés restantes, puis sélectionnez **Créer**. Dans la boîte de dialogue de confirmation, sélectionnez **Terminé** pour retourner à la console **Sites** ou **Ouvrir le site** pour ouvrir la page racine du site.

### Création d’une Live Copy dans une Live Copy (configuration de plan directeur)  {#creating-a-live-copy-inside-a-live-copy-blueprint-configuration}

Lorsque vous créez une Live Copy dans la Live Copy existante (créée à l’aide d’une configuration de plan), vous pouvez insérer une copie de langue ou des chapitres qui n’ont pas été inclus lors de la création initiale de la Live Copy.

## Surveillance de votre Live Copy {#monitoring-your-live-copy}

### Affichage de l’état d’une Live Copy {#seeing-the-status-of-a-live-copy}

Les propriétés d’une page Live Copy présentent les informations suivantes sur la Live Copy :

* **Source** : Page source de la page Live Copy
* **État** : État de synchronisation de Live Copy, y compris si Live Copy est à jour avec la source, la date de la dernière synchronisation et l&#39;auteur de la synchronisation.
* **Configuration**:

   * Si la page est toujours soumise à l&#39;héritage de Live Copy
   * Si la configuration est héritée de la page parent
   * Toute configuration de déploiement utilisée par Live Copy

Pour afficher les propriétés :

1. Dans la console **Sites**, sélectionnez la page Live Copy et ouvrez les propriétés.
1. Sélectionnez l’onglet **Live Copy**.

   Par exemple :

   ![Onglet Live Copy dans les propriétés de la page](../assets/live-copy-inherit.png)

   Voir la section [Utilisation de la fonction Aperçu de Live Copy](live-copy-overview.md#using-the-live-copy-overview) dans l’article Live Copy Overview Console pour plus d’informations.

### Affichage des Live Copies d’une page de plan directeur {#seeing-the-live-copies-of-a-blueprint-page}

Les pages de plan (référencées dans une configuration de plan) vous fournissent une liste des pages Live Copy qui utilisent la page active (plan directeur) comme source. Utilisez cette liste pour effectuer le suivi des Live Copies. La liste s’affiche dans l’onglet **Plan directeur** des [propriétés de page](/help/sites-cloud/authoring/fundamentals/page-properties.md).

![Onglet Plan directeur des propriétés de page](../assets/live-copy-blueprint-tab.png)

## Synchronisation de votre Live Copy {#synchronizing-your-live-copy}

Il existe plusieurs façons de synchroniser votre Live Copy.

### Déploiement d’un plan directeur {#rolling-out-a-blueprint}

Exécutez une page de plan pour pousser les modifications de contenu vers les Live Copies. L’action **Déployer** exécute les configurations de déploiement qui utilisent le déclencheur [En cas de déploiement](live-copy-sync-config.md#rollout-triggers).

>[!NOTE]
>
>Des conflits peuvent survenir si de nouvelles pages portant le même nom de page sont créées à la fois dans la branche du plan directeur et dans une branche Live Copy dépendante.
>
>Ces [conflits doivent être traités et résolus lors du déploiement](rollout-conflicts.md).

#### Déploiement d’un plan directeur à partir des propriétés de page  {#rolling-out-a-blueprint-from-page-properties}

1. Dans la console **Sites**, sélectionnez la page dans le plan et ouvrez les propriétés.
1. Ouvrez l’onglet **Plan directeur**.
1. Sélectionnez **Déployer**.

   ![Bouton Déployer](../assets/rollout.png)

1. Spécifiez les pages et les sous-pages, puis cochez la case :

   ![Sélectionner les pages à déployer](../assets/select-rollout-pages.png)

1. Indiquez si la tâche de déploiement doit être exécutée immédiatement (**Maintenant**) ou à une autre date/heure (**Ultérieurement**).

   ![Définir le temps de déploiement](../assets/rollout-now-later.png)

Les déploiements sont traités comme des tâches asynchrones et peuvent être vérifiés sur la page [***État des tâches asynchrones**.](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations)

#### Déploiement d’un plan directeur à partir du rail de référence {#roll-out-a-blueprint-from-the-reference-rail}

1. Dans la console **Sites**, sélectionnez la page dans la copie dynamique et ouvrez le panneau **[Références](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** (dans la barre d&#39;outils).
1. Sélectionnez l’option **Plan directeur** dans la liste pour afficher les plans directeurs associés à cette page.
1. Sélectionnez le plan directeur requis dans la liste.
1. Cliquez ou appuyez sur **Déployer**.

   ![Plan de déploiement à partir du rail de références](../assets/rollout-blueprint-from-references.png)

1. Vous êtes invité à confirmer les détails du déploiement :

   * **Etendue du déploiement**:

      Indiquez si la plage est réservée à la page sélectionnée ou si elle doit inclure des sous-pages.

   * **Planification** :

      Indiquez si la tâche de déploiement doit être exécutée immédiatement (**Maintenant**) ou ultérieurement (**Ultérieurement**).

      ![Définir la portée et la planification du déploiement](../assets/rollout-scope-schedule.png)

1. Après avoir défini ces détails, sélectionnez **Déployer** pour exécuter l’opération.

Les déploiements sont traités comme des tâches asynchrones et peuvent être vérifiés sur la page [**État des tâches asynchrones**.](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations)

#### Déploiement d’un plan directeur de l’aperçu de la Live Copy {#roll-out-a-blueprint-from-the-live-copy-overview}

L’[**** action Déployer est également disponible dans l’aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview) lorsqu’une page Plan directeur est sélectionnée.

1. Ouvrez l’[aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview) et sélectionnez une page Plan directeur.
1. Sélectionnez **Déployer** dans la barre d’outils.

   ![Présentation de LiveCopy](../assets/live-copy-overview-actions-blueprint.png)

1. Spécifiez les pages et les sous-pages, puis cochez la case :

   ![Sélectionner les pages à déployer](../assets/select-rollout-pages.png)

1. Indiquez si la tâche de déploiement doit être exécutée immédiatement (**Maintenant**) ou à une autre date/heure (**Ultérieurement**).

   ![Définir le calendrier de déploiement](../assets/rollout-now-later.png)

Les déploiements sont traités comme des tâches asynchrones et peuvent être vérifiés sur la page [**État des tâches asynchrones**.](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations)

### Synchronisation d’une Live Copy {#synchronizing-a-live-copy}

Synchronisez une page Live Copy pour extraire les modifications de contenu de la source vers Live Copy.

#### Synchronisation d’une Live Copy à partir des propriétés de page {#synchronize-a-live-copy-from-page-properties}

Synchronisez une Live Copy pour extraire les modifications de la source vers la Live Copy.

>[!NOTE]
>
>La synchronisation effectue les configurations de déploiement qui utilisent le déclencheur [En cas de déploiement](live-copy-sync-config.md#rollout-triggers).

1. Dans la console **Sites**, sélectionnez la page Live Copy et ouvrez les propriétés.
1. Ouvrez l’onglet **Live Copy**.
1. Cliquez ou appuyez sur **Synchroniser**.

   ![Bouton Synchroniser](../assets/synchronize.png)

   Une confirmation est demandée ; utilisez **Synchroniser** pour continuer.

#### Synchronisation d’une Live Copy à partir de l’aperçu de la Live Copy  {#synchronize-a-live-copy-from-the-live-copy-overview}

L’[action Synchroniser est également disponible dans l’aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview), lorsqu’une page Live Copy est sélectionnée.

1. Ouvrez l’[aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview) et sélectionnez une page Live Copy.
1. Sélectionnez **Synchroniser** dans la barre d’outils.
1. Confirmez l&#39;action **Déploiement** dans la boîte de dialogue après avoir spécifié si vous souhaitez inclure :

   * **Page et sous-pages**
   * **Page seulement**

   ![Pages de déploiement avec ou sans sous-pages](../assets/rollout-page-and-subpages.png)

## Modification du contenu de Live Copy {#changing-live-copy-content}

Pour modifier le contenu Live Copy, vous pouvez :

* Ajoutez des paragraphes sur la page.
* Mettez à jour le contenu existant en rompant l’héritage de Live Copy pour n’importe quelle page ou composant.

>[!TIP]
>
>Si vous créez manuellement une nouvelle page dans Live Copy, la nouvelle page est locale dans Live Copy, ce qui signifie qu’elle ne comporte pas de page source correspondante à laquelle elle est jointe.
>
>La meilleure pratique pour créer une page locale qui fait partie de la relation consiste à créer la page locale dans la source et à effectuer un déploiement approfondi. La page sera alors créée localement sous forme de Live Copies.

>[!NOTE]
>
>Des conflits peuvent survenir si de nouvelles pages portant le même nom de page sont créées à la fois dans la branche du plan directeur et dans une branche Live Copy dépendante.
>
>Ces [conflits doivent être traités et résolus lors du déploiement](rollout-conflicts.md).

### Ajout de composants à une page Live Copy  {#adding-components-to-a-live-copy-page}

Vous pouvez ajouter des composants à une page Live Copy à tout moment. L’état d’héritage de Live Copy et de son système de paragraphes ne contrôle pas votre capacité à ajouter des composants.

Lorsque la page Live Copy est synchronisée avec la page source, les composants ajoutés restent inchangés. Voir également [Modification de l’ordre des composants sur une page Live Copy.](#changing-the-order-of-components-on-a-live-copy-page)

>[!TIP]
>
>Les modifications apportées localement à un composant marqué en tant que conteneur ne sont pas remplacées par le contenu du plan directeur lors d’un déploiement. Voir [Meilleures pratiques MSM](best-practices.md#components-and-container-synchronization) pour plus d’informations.

### Suspension de l’héritage pour une page {#suspending-inheritance-for-a-page}

Lorsque vous créez une Live Copy, la configuration de Live Copy est enregistrée sur la page racine des pages copiées. Toutes les pages enfants de la page racine héritent des configurations Live Copy. Les composants des pages Live Copy héritent également de la configuration de Live Copy.

Vous pouvez suspendre l’héritage de Live Copy pour une page Live Copy afin de pouvoir modifier les propriétés et les composants de la page. Lorsque vous suspendez l’héritage, les propriétés et les composants de la page ne sont plus synchronisés avec la source.

>[!TIP]
>
>Vous pouvez également [détacher une Live Copy](#detaching-a-live-copy) de son plan pour supprimer toutes les connexions. Contrairement à la suspension de l&#39;héritage, l&#39;action de détachement est permanente et non réversible.

#### Suspension de l’héritage à partir des propriétés de page {#suspending-inheritance-from-page-properties}

Pour suspendre l’héritage sur une page :

1. Ouvrez les propriétés de la page Live Copy à l’aide de la commande **Propriétés de la Vue** de la console **Sites** ou à l’aide de **Informations sur la page** dans la barre d’outils de la page.
1. Cliquez ou appuyez sur l’onglet **Live Copy**.
1. Sélectionnez **Suspendre** dans la barre d’outils. Vous pouvez ensuite sélectionner, au choix :

   * **Suspendre** : pour suspendre uniquement la page active.
   * **Suspendre avec les enfants** : pour suspendre la page active avec toutes les pages enfants.

1. Sélectionnez **Suspendre** dans la boîte de dialogue de confirmation.

#### Suspension de l’héritage à partir de l’aperçu de la Live Copy {#suspending-inheritance-from-the-live-copy-overview}

L’[action Suspendre est également disponible dans l’aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview), lorsqu’une page Live Copy est sélectionnée.

1. Ouvrez l’[aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview) et sélectionnez une page Live Copy.
1. Sélectionnez **Suspendre** dans la barre d’outils.
1. Sélectionnez l’option appropriée parmi les deux actions suivantes :

   * **Suspendre**
   * **Suspendre avec enfants**

   ![Suspendre avec enfants](../assets/suspend-with-children.png)

1. Confirmez l&#39;action **Suspendre** dans la boîte de dialogue **Suspendre la Live Copy** :

   ![Confirmer la suspension](../assets/confirm-suspend.png)

### Reprise de l’héritage pour une page {#resuming-inheritance-for-a-page}

La suspension de l’héritage de Live Copy pour une page est une action temporaire. Une fois l’héritage suspendu, l’action **Reprendre** devient disponible, ce qui vous permet de rétablir la relation en direct.

![Reprendre l&#39;héritage](../assets/resume-inheritance.png)

Lorsque vous réactivez l’héritage, la page n’est pas automatiquement synchronisée avec la source. Si nécessaire, vous pouvez demander une synchronisation, soit :

* Dans la boîte de dialogue **Reprendre**/**Rétablir**, par exemple :

   ![Reprendre et synchroniser](../assets/resume-and-synch.png)

* Par la suite, en sélectionnant manuellement l’action de synchronisation.

>[!NOTE]
>
>Lorsque vous réactivez l’héritage, la page n’est pas automatiquement synchronisée avec la source. Si cela est nécessaire, vous pouvez demander manuellement une synchronisation au moment de la reprise ou plus tard.

#### Reprise de l’héritage à partir des propriétés de page {#resuming-inheritance-from-page-properties}

Une fois l’héritage [suspendu](#suspending-inheritance-from-page-properties), l’action **Reprendre** devient disponible dans la barre d’outils des propriétés de page :

![Bouton Reprendre](../assets/resume.png)

Lorsque cette action est sélectionnée, la boîte de dialogue s’affiche. Vous pouvez sélectionner une synchronisation, si nécessaire, puis confirmer l’action.

#### Reprise d’une page Live Copy à partir de l’aperçu de la Live Copy {#resume-a-live-copy-page-from-the-live-copy-overview}

L’[action Reprendre est également disponible dans l’aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview), lorsqu’une page Live Copy est sélectionnée.

1. Ouvrez [Aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview) et sélectionnez une page de Live Copy suspendue. La page s&#39;affichera sous la forme **HÉRITAGE ANNULÉE**.
1. Sélectionnez **Reprendre** dans la barre d’outils.
1. Indiquez si vous souhaitez synchroniser la page après avoir rétabli l’héritage, puis confirmez l’action **Reprendre** dans la boîte de dialogue **Reprendre la Live Copy**.

### Changement de la profondeur d’héritage (superficielle/profonde) {#changing-inheritance-depth-shallow-deep}

Sur une Live Copy existante, vous pouvez modifier la profondeur d’une page, c’est-à-dire si des pages enfants sont incluses.

* Passage à une Live Copy peu profonde :

   * Prend immédiatement effet et est irréversible.

   * Détache explicitement les pages enfants de la Live Copy. Les autres modifications des pages enfants ne peuvent pas être préservées si elles sont annulées.

   * Supprimera tout descendant `LiveRelationships` même s’il y a des imbriqués `LiveCopies`.

* Passage à une Live Copy profonde :

   * Ne touche pas aux pages enfants.
   * Pour visualiser l’effet de la transition, vous pouvez procéder à un déploiement ; toutes les modifications de contenu sont appliquées en fonction de la configuration de déploiement.

* Basculer vers une Live Copy peu profonde, puis revenir à une Copie profonde :

   * Traite tous les enfants de la Live Copy (anciennement) peu profonde comme s’ils avaient été créés manuellement et sont donc déplacés en utilisant `[oldname]_msm_moved name`.

Pour spécifier ou changer la profondeur :

1. Ouvrez les propriétés de la page Live Copy à l’aide de la commande **Propriétés de la Vue** de la console **Sites** ou à l’aide de **Informations sur la page** dans la barre d’outils de la page.
1. Cliquez ou appuyez sur l’onglet **Live Copy**.
1. Dans la section **Configuration**, cochez ou décochez la case **Héritage de Live Copy** selon que les pages enfants sont incluses ou non :

   * Cochée - Copie dynamique profonde (les pages enfants sont incluses)
   * Non coché - Copie dynamique peu profonde (les pages enfants sont exclues)

   >[!CAUTION]
   >
   >Le passage à une Live Copy peu profonde aura un effet immédiat et sera irréversible.
   >
   >Voir f[Live Copies - Composition](overview.md#live-copies-composition) pour plus d’informations.

1. Cliquez ou appuyez sur **Enregistrer** pour conserver vos mises à jour.

### Annulation de l’héritage pour un composant  {#cancelling-inheritance-for-a-component}

Annulez l’héritage de Live Copy pour un composant afin que le composant ne soit plus synchronisé avec le composant source. Vous pouvez activer l’héritage ultérieurement si nécessaire.

>[!NOTE]
>
>Lorsque vous réactivez l’héritage, le composant n’est pas automatiquement synchronisé avec la source. Vous pouvez demander manuellement une synchronisation si nécessaire.

Annulez l’héritage pour modifier le contenu du composant ou supprimer le composant :

1. Cliquez ou appuyez sur le composant pour lequel vous souhaitez annuler l’héritage.

   ![Héritage dans la barre d’outils des composants](../assets/inheritance-toolbar.png)

1. Sur la barre d’outils du composant, appuyez ou cliquez sur l’icône **Annuler l’héritage**.

   ![Annuler l&#39;icône d&#39;héritage](../assets/cancel-inheritance-icon.png)

1. Dans la boîte de dialogue Annuler l’héritage, confirmez l’action en cliquant sur **Oui**.

   La barre d’outils du composant est mise à jour pour inclure toutes les commandes de modification (appropriées).

### Réactivation de l&#39;héritage pour un composant {#re-enabling-inheritance-for-a-component}

Pour activer l&#39;héritage pour un composant, cliquez ou appuyez sur l&#39;icône **Réactiver l&#39;héritage** dans la barre d&#39;outils du composant.

![Réactiver l’icône d’héritage](../assets/re-enable-inheritance-icon.png)

### Modification de l’ordre des composants sur une page Live Copy {#changing-the-order-of-components-on-a-live-copy-page}

Si une Live Copy contient des composants qui font partie d’un système de paragraphes, l’héritage de ce système de paragraphes respecte les règles suivantes :

* L’ordre des composants dans un système de paragraphes hérité peut être modifié, même si l’héritage est établi.
* Sur le déploiement, l’ordre des composants est restauré à partir du plan directeur. Si de nouveaux composants ont été ajoutés à Live Copy avant le déploiement, ils seront réorganisés avec les composants au-dessus desquels ils ont été ajoutés.
* Si l’héritage du système de paragraphes est annulé, l’ordre des composants ne sera pas restauré lors du déploiement et restera tel quel dans Live Copy.

>[!NOTE]
>
>Lors de la restauration d’un héritage annulé sur un système de paragraphes, l’ordre des composants **n’est pas automatiquement restauré** à partir du plan directeur. Vous pouvez demander manuellement une synchronisation si nécessaire.

Suivez la procédure suivante pour annuler l’héritage du système de paragraphes.

1. Ouvrez la page Live Copy.
1. Faites glisser un composant existant vers un nouvel emplacement sur la page.
1. Dans la boîte de dialogue **Annuler l’héritage**, confirmez l’action en cliquant sur **Oui**.

### Remplacement des propriétés d’une page Live Copy  {#overriding-properties-of-a-live-copy-page}

Par défaut, les propriétés de page d’une page Live Copy sont héritées de la page source et ne sont pas modifiables.

Vous pouvez annuler l’héritage d’une propriété lorsque vous devez modifier la valeur de la propriété pour Live Copy. Une icône de lien indique que l’héritage est activé pour la propriété.

![Propriétés de page héritées](../assets/properties-inherited.png)

Lorsque vous annulez l’héritage, vous pouvez modifier la valeur de la propriété. Une icône de lien brisé indique que l’héritage est annulé.

![Propriétés non héritées](../assets/properties-not-inherited.png)

Vous pourrez par la suite réactiver l’héritage pour une propriété, si nécessaire.

>[!NOTE]
>
>Lorsque vous réactivez l’héritage, la propriété de page Live Copy n’est pas automatiquement synchronisée avec la propriété source. Vous pouvez demander manuellement une synchronisation si cela est nécessaire.

1. Ouvrez les propriétés de la page Live Copy à l’aide de l’option **Propriétés de la Vue** de la console **Sites** ou de l’icône **Informations sur la page** de la barre d’outils de la page.
1. Pour annuler l’héritage d’une propriété, appuyez ou cliquez sur l’icône de lien qui s’affiche à droite de la propriété.

   ![Bouton Annuler l’héritage](../assets/cancel-inheritance-button.png)

1. Dans la boîte de dialogue de confirmation **Annuler l’héritage**, cliquez ou appuyez sur **Oui**.

### Rétablissement des propriétés d’une page de la Live Copy  {#revert-properties-of-a-live-copy-page}

Pour activer l&#39;héritage d&#39;une propriété, cliquez ou appuyez sur l&#39;icône **Rétablir l&#39;héritage** qui s&#39;affiche en regard de la propriété.

![Bouton Restaurer l’héritage](../assets/revert-inheritance-button.png)

### Réinitialisation d’une page Live Copy {#resetting-a-live-copy-page}

Vous pouvez réinitialiser une page Live Copy afin de :

* Supprimer toutes les annulations d’héritage et
* Restaurer la page dans le même état que la page source.

La réinitialisation affecte les modifications apportées aux propriétés de page, au système de paragraphe et aux composants.

#### Réinitialisation d’une page Live Copy à partir des propriétés de la page {#reset-a-live-copy-page-from-the-page-properties}

1. Dans la console **Sites**, sélectionnez la page Copie dynamique et **Propriétés de la Vue**.
1. Ouvrez l’onglet **Live Copy**.
1. Sélectionnez **Réinitialiser** dans la barre d’outils.

   ![Bouton Réinitialiser](../assets/reset.png)

1. Dans la boîte de dialogue **Réinitialiser la Live Copy**, confirmez en cliquant sur **Réinitialiser**.

#### Réinitialisation d’une page Live Copy à partir de l’aperçu de la Live Copy  {#reset-a-live-copy-page-from-the-live-copy-overview}

L’[**** action Réinitialiser est également disponible dans l’aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview), lorsqu’une page Live Copy est sélectionnée.

1. Ouvrez l’[aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview) et sélectionnez une page Live Copy.
1. Sélectionnez **Réinitialiser** dans la barre d’outils.
1. Confirmez l&#39;action **Réinitialiser** dans la boîte de dialogue **Réinitialiser Live Copy** :

   ![Confirmer la réinitialisation de Live Copy](../assets/reset-live-copy.png)

## Comparaison d’une page Live Copy à une page de plan directeur {#comparing-a-live-copy-page-with-a-blueprint-page}

Pour effectuer le suivi des modifications que vous avez apportées, vous pouvez vue la page de plan dans **Références** et la comparer à sa page Live Copy :

1. Dans la console **Sites**, [accédez à un plan ou à la page Live Copy et sélectionnez-le.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. Ouvrez le panneau **[Références](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** et, selon le contexte, sélectionnez l’une des options suivantes :

   * **Blueprint**
   * **Live Copies**

1. Sélectionnez votre Live Copy spécifique en fonction du contexte et sélectionnez l’une des options suivantes :

   * **Comparer au plan directeur**
   * **Comparer à la Live Copy**

   Par exemple :

   ![Comparaison des Live Copies](../assets/compare-live-copy.png)

1. Les pages Live Copy et les pages du plan directeur seront ouvertes côte à côte.

   Pour plus d&#39;informations sur l&#39;utilisation de la fonction de comparaison, voir [Diff de page](/help/sites-cloud/authoring/features/page-diff.md).

## Désolidarisation d’une Live Copy {#detaching-a-live-copy}

L’action de détachement supprime définitivement la relation active entre une Live Copy et sa page source/plan. Toutes les propriétés pertinentes pour MSM sont supprimées de Live Copy et les pages Live Copy deviennent une copie autonome.

>[!CAUTION]
>
>Vous ne pouvez pas rétablir la relation active après avoir détaché la Live Copy.
>
>Pour supprimer la relation dynamique avec l’option de rétablissement ultérieur, vous pouvez [annuler l’héritage de Live Copy](#suspending-inheritance-for-a-page) pour la page.

Il existe des implications liées à l’endroit dans l’arborescence où vous utilisez l’option **Désolidariser** :

* **Détacher sur la page racine d’une copie dynamique**

   Lorsque cette opération est effectuée sur la page racine d&#39;une Live Copy, elle supprime la relation dynamique entre toutes les pages du plan et sa Live Copy.

   D&#39;autres modifications apportées aux pages du plan directeur **n&#39;auront pas d&#39;impact sur la Live Copy.**

* **Détacher sur une sous-page d’une copie dynamique**

   Lorsque cette opération est effectuée sur une sous-page (ou branche) dans une Live Copy :

   * La relation dynamique est supprimée pour cette sous-page (ou branche) et
   * Les (sous-)pages de la branche Live Copy sont traitées comme si elles avaient été créées manuellement.

   Toutefois, les sous-pages étant encore soumises aux relations en direct de la branche parent, un autre déploiement de la ou des pages de plan directeur aura à la fois pour effet :

   1. De renommer les pages désolidarisées :

      * Cela est dû au fait que MSM les considère comme des pages créées manuellement qui provoquent un conflit car elles portent le même nom que les pages Live Copy qu’il tente de créer.
   1. Créez une page Live Copy avec le nom d’origine, contenant les modifications du déploiement.

   >[!NOTE]
   >
   >Voir [Conflits de déploiement MSM](rollout-conflicts.md) pour obtenir des détails sur ces situations.

### Désolidarisation d’une page Live Copy à partir des propriétés de la page {#detach-a-live-copy-page-from-the-page-properties}

Pour détacher une Live Copy :

1. Dans la console **Sites**, sélectionnez la page Live Copy et cliquez ou appuyez sur **Propriétés de la Vue**.
1. Ouvrez l’onglet **Live Copy**.
1. Dans la barre d’outils, sélectionnez **Désolidariser**.

   ![Bouton Détacher](../assets/detach-button.png)

1. Une boîte de dialogue de confirmation s’affiche. Sélectionnez **Désolidariser** pour exécuter l’opération.

### Désolidarisation d’une page Live Copy à partir de l’aperçu de la Live Copy  {#detach-a-live-copy-page-from-the-live-copy-overview}

L’[action Désolidariser est également disponible dans l’aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview), lorsqu’une page Live Copy est sélectionnée.

1. Ouvrez l’[aperçu de la Live Copy](live-copy-overview.md#using-the-live-copy-overview) et sélectionnez une page Live Copy.
1. Sélectionnez **Désolidariser** dans la barre d’outils.
1. Confirmez l&#39;action **Détacher** dans la boîte de dialogue **Détacher la Live Copy** :

   ![Désolidarisation d’une Live Copy](../assets/detach-live-copy.png)

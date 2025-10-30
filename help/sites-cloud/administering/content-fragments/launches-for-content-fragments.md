---
title: Lancements pour les fragments de contenu
description: Découvrez comment utiliser les lancements pour les fragments de contenu dans Adobe Experience Manager as a Cloud Service. Les lancements vous permettent de développer efficacement du contenu pour une prochaine version, tout en conservant vos fragments de contenu actuels.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: c0b9e571-3be5-42ab-8d56-d93e8ef4c2f7
source-git-commit: 39ff527f0082a18f0853964172eabf438caa1098
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 2%

---

# Lancements pour les fragments de contenu {#launches-for-content-fragments}

Dans Adobe Experience Manager (AEM) as a Cloud Service, les lancements vous permettent de développer efficacement du contenu pour une version ultérieure.

Un *Launch* est créé pour vous permettre d’apporter des modifications en vue d’une publication ultérieure, tout en conservant votre contenu actuel. Pour les fragments de contenu, cela signifie que vous modifiez deux versions simultanément : le contenu actuellement publié et une version de ce contenu, qui sera publiée à un moment donné dans le futur. Une fois ce délai écoulé, vous pouvez remplacer le contenu des fragments de contenu d’origine et publier les nouvelles versions.

>[!NOTE]
>
>Les lancements sont également disponibles pour les pages. Les concepts de base sont les mêmes, mais il existe des différences dans la manière de les gérer dans AEM.
>
>Pour plus d’informations, consultez [Lancements de pages](/help/sites-cloud/authoring/launches/overview.md).

Vous créez un *Launch*, puis vous modifiez et mettez à jour vos fragments de contenu dans votre *Launch*. Si des modifications sont apportées aux fragments *Source* au cours de cette phase, vous pouvez les copier dans *Launch* avec l’opération *Rebase*. Une fois prêt, *Promouvoir* duplique le contenu du lancement vers la source. Vous pouvez ensuite activer vos fragments source manuellement ou automatiquement (selon les champs définis lors de la création et de la modification du lancement). Vous pouvez également indiquer si les fragments référencés doivent être inclus dans ce processus.

Par exemple, les fragments de produits saisonniers de votre boutique en ligne sont mis à jour chaque trimestre, de sorte que les produits présentés correspondent à la saison en cours. Pour préparer la prochaine mise à jour trimestrielle, vous pouvez créer un lancement des fragments appropriés. Tout au long du trimestre, les modifications suivantes sont cumulées dans la copie de lancement :

* Les modifications effectuées directement sur les fragments de lancement en préparation du trimestre suivant.
* Les modifications apportées aux fragments de contenu source que vous transférez aux pages de lancement avec *Rebase*.
* Vous pouvez également parcourir le contenu dans la branche de lancement ; en ajoutant ou en supprimant des fragments si nécessaire.

Lorsque le trimestre suivant arrive, vous convertissez les pages de lancement afin de pouvoir publier les pages source (contenant le contenu mis à jour). Vous pouvez convertir tous les fragments ou uniquement ceux que vous avez modifiés.

![Présentation des lancements - Rebaser et promouvoir](/help/sites-cloud/administering/content-fragments/assets/cf-launches-overview.png)

Cette section décrit comment créer, modifier, gérer, rebaser, promouvoir et, si nécessaire, supprimer des lancements à partir de la console [Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md) :

* [Accès et affichage des lancements dans la console Fragments de contenu](#launches-in-the-content-fragment-console)
* [Création d’un lancement](#create-a-launch)
* [Modifier le contenu de Launch](#edit-launch-content)
* [Gestion du contenu dans un lancement](#manage-content-within-a-launch)
* [Comparer le lancement à la source](#compare-launch-to-source)
* [Rebaser un lancement à partir de Source](#rebase-a-launch-from-source)
* [Convertir un lancement en Source](#promote-a-launch-to-source)
* [Suppression d’un lancement](#delete-a-launch)

## Lancements dans la console Fragments de contenu {#launches-in-the-content-fragment-console}

L’onglet **Lancements** de la console Fragments de contenu vous permet de créer des lancements, de répertorier tous les lancements existants, de voir les propriétés clés et d’effectuer des actions sur ceux-ci.

Si aucun lancement n’est sélectionné, vous pouvez [créer un lancement](#create-a-launch).

![Onglet Lancements dans la console](/help/sites-cloud/administering/content-fragments/assets/cf-launches-tab.png)

Sélectionnez votre lancement pour afficher les éléments suivants :

* la barre d’outils, avec les actions disponibles ;
* le panneau de droite, affichant les propriétés et d’autres actions

![Barre d’outils des actions Launch dans la console](/help/sites-cloud/administering/content-fragments/assets/cf-launches-actions.png)

La barre d’outils permet d’effectuer les opérations suivantes :

* **[Ouvrir le lancement](#edit-launch-content)**
* **[Modifier les sources](#manage-content-within-a-launch)**
* **[Comparer Launch à Source](#compare-launch-to-source)**
* **[Promouvoir](#promote-a-launch-to-source)**
* **[Rebaser](#promote-a-launch-to-source)**
* **[Supprimer le lancement](#delete-a-launch)**

Alors que le panneau de droite vous permet d’effectuer les opérations suivantes :

* Modifiez le lancement **Titre**
* Modifiez le lancement **Description**
* Mettez à jour les détails de configuration définis lors de la [création du lancement](#create-a-launch) :

   * **Inclure les références** : créez le lancement avec ou sans, y compris les fragments de contenu référencés. Par défaut, les fragments référencés sont inclus.

      * Les fragments référencés sont également affectés lorsque vous [ajoutez ou supprimez des fragments du lancement](#manage-content-within-a-launch) à un stade ultérieur.

     >[!NOTE]
     >
     >Voir [Détails concernant les références incluses](#details-concerning-included-references)

   * **Publication prête** ; l’activation de cette option publiera automatiquement les fragments lorsque le lancement sera promu à la source.

* Définissez également les éléments suivants :

   * Une **Date et heure de promotion** : si le lancement [&#x200B; doit être automatiquement promu](#promote-automatically)

## Création d’un lancement {#create-a-launch}

Pour créer votre lancement :

1. Accédez à la console Fragments de contenu .

1. Ouvrez l’onglet **Lancements**.

1. Sélectionnez **Créer un lancement**.

1. Accédez au dossier approprié et sélectionnez les fragments à inclure dans le lancement :

   ![Sélectionner les fragments de contenu pour le nouveau lancement](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-select-cfs.png)

1. Sélectionnez **Suivant**.

1. Spécifiez les détails de configuration du lancement :

   * **Titre**
   * **Description**
   * **Inclure les références** : créez le lancement avec ou sans, y compris les fragments de contenu référencés. Par défaut, les fragments référencés sont inclus.

     >[!NOTE]
     >
     >Voir [Détails concernant les références incluses](#details-concerning-included-references)

   * **Publication prête** : l’activation de cette option publiera automatiquement les fragments lorsque le lancement sera promu à la source.

   ![Détails du nouveau lancement](/help/sites-cloud/administering/content-fragments/assets/cf-launches-create-launch-details.png)

1. **Enregistrez** la configuration.

1. Vous revenez alors à l’onglet **Lancements** de la console Fragments de contenu, où :

   * votre nouveau lancement est maintenant répertorié
   * un message s’affiche pour confirmer que la création du lancement a commencé :

      * **Le traitement a commencé pour créer un lancement, surveiller la progression dans AEM et recharger la page une fois terminé.**

1. Sélectionnez **Afficher**, dans la zone de message, pour afficher plus de détails dans la console AEM pour [Opérations en arrière-plan](/help/operations/asynchronous-jobs.md).

   ![&#x200B; Nouveau lancement dans la console &#x200B;](/help/sites-cloud/administering/content-fragments/assets/cf-launches-new-launch-in-console.png)

## Modifier le contenu de Launch {#edit-launch-content}

Pour modifier les fragments de contenu dans votre lancement :

1. Accédez à la console Fragments de contenu .

1. Ouvrez l’onglet **Lancements**.

1. Sélectionnez votre lancement pour afficher les actions de la barre d’outils.

1. Sélectionnez **Ouvrir le lancement**.

   Votre lancement s’affiche, ainsi que les fragments qu’il contient.

   ![Modifier le contenu de Launch](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-launch-content.png)

1. Sélectionnez **Modifier** pour le fragment à mettre à jour. Elle s’ouvre dans l’[éditeur de fragments](/help/sites-cloud/administering/content-fragments/authoring.md) comme d’habitude.

## Gestion du contenu dans un lancement {#manage-content-within-a-launch}

Pour gérer les fragments de contenu dans votre lancement et modifier leur contenu :

1. Accédez à la console Fragments de contenu .

1. Ouvrez l’onglet **Lancements**.

1. Sélectionnez votre lancement.

1. Sélectionnez **Modifier les sources**.

   Les fragments source de votre lancement s’affichent.

   ![Modifier Source](/help/sites-cloud/administering/content-fragments/assets/cf-launches-edit-sources.png)

1. Vous pouvez :

   1. **Ajouter des sources** pour ajouter d’autres fragments à votre lancement.

      * Si la mention **Inclure les références** est vraie pour le lancement, tous les fragments de contenu référencés seront également importés dans le lancement (s’ils ne sont pas déjà présents).

   1. Sélectionnez **Modifier** pour le fragment source à mettre à jour. Elle s’ouvre dans l’[éditeur de fragments](/help/sites-cloud/administering/content-fragments/authoring.md) comme d’habitude.

   1. Sélectionnez un fragment, puis l’action **Supprimer des sources** de la barre d’outils pour supprimer ce fragment du lancement.

      * Si la mention **Inclure les références** est vraie pour le lancement, tous les fragments de contenu référencés seront également supprimés du lancement, à moins qu’ils ne soient également référencés par d’autres fragments de contenu encore dans le lancement.

   >[!NOTE]
   >
   >Voir [Détails concernant les références incluses](#details-concerning-included-references)

## Comparer le lancement à la source {#compare-launch-to-source}

Il est recommandé, avant toute action Rebaser ou Promouvoir, de toujours comparer la source et le lancement afin de confirmer les modifications et leur impact sur votre contenu (les deux actions remplacent le contenu cible) :

1. Accédez à la console Fragments de contenu .

1. Ouvrez l’onglet **Lancements**.

1. Sélectionnez votre lancement.

1. Sélectionnez **Comparer Launch à Source**.

   * Les fragments source et de lancement sont affichés côte à côte pour mettre en évidence les différences.
      * Les fragments Source s’affichent à gauche, les fragments Launch à droite.
      * Les mises à jour sont mises en surbrillance :
         * Source : bleu
         * Lancement : rose
         * Conflits : jaune
   * Les actions [Promouvoir](#promote-a-launch-to-source) et [Rebaser](#rebase-a-launch-from-source) sont disponibles dans le coin supérieur droit.
   * **Mises à jour trouvées** : un résumé de toutes les mises à jour s’affiche dans le coin supérieur gauche. Le nombre de mises à jour source en bleu, le nombre de mises à jour de lancement en rose et le nombre de mises à jour des deux (conflits) en jaune.
      * Les icônes représentant des yeux vous permettent d’afficher ou de masquer les mises à jour du contenu réel pour une vue d’ensemble plus claire.
   * Les curseurs **Inclure** vous permettent de définir les fragments de contenu à inclure dans l’opération de promotion ou de bascule suivante :
      * **Tout inclure** en haut à droite
      * **Inclure** au-dessus de chaque fragment dans le lancement

     >[!NOTE]
     >
     >Les curseurs s’appliquent uniquement aux actions Promouvoir et Rebaser extraites de l’écran Comparer .

   * Le contenu du fragment est affiché au niveau du champ (élément de fragment de contenu/niveau de type de données) ; avec des mises en surbrillance indiquant les modifications.
   * Sélectionnez **Affichage** pour recalculer les différences.

   ![Comparer Source et Launch](/help/sites-cloud/administering/content-fragments/assets/cf-launches-compare.png)

## Rebaser un lancement (à partir de Source) {#rebase-a-launch-from-source}

Lorsque des mises à jour ont été apportées aux fragments source et que vous souhaitez copier ces modifications dans votre lancement :

1. Accédez à la console Fragments de contenu .

1. Ouvrez l’onglet **Lancements**.

1. Sélectionnez votre lancement et vos fragments.

1. Sélectionnez **Rebaser**.

>[!NOTE]
>
>Vous pouvez également **Rebaser** un lancement à partir de **[Comparer Launch à Source](#compare-launch-to-source)**.

## Promouvoir un lancement (vers Source) {#promote-a-launch-to-source}

Lorsque votre lancement est prêt à être publié, il doit être copié dans la source. Vous pouvez le faire dans la console ou configurer les paramètres pour que cela se produise automatiquement à une date et une heure spécifiques.

### Promouvoir manuellement {#promote-manually}

Lorsque votre lancement est prêt à être publié, il peut être copié dans la source avec l’action explicite :

1. Accédez à la console Fragments de contenu .

1. Ouvrez l’onglet **Lancements**.

1. Sélectionnez votre lancement et vos fragments.

1. Sélectionnez **Convertir**.

>[!NOTE]
>
>Vous pouvez également **Promouvoir** un lancement à partir de **Comparer le lancement à Source**.

### Promouvoir automatiquement {#promote-automatically}

Pour qu’un lancement fasse automatiquement l’objet d’une promotion à une date et une heure spécifiées, vous devez :

1. Définissez l’**Date et heure de promotion** dans le panneau de droite de l’onglet [Lancements](#launches-in-the-content-fragment-console).

1. Si le contenu peut être publié lors de sa conversion, définissez **Publier prêt** lors de la [création du lancement](#create-a-launch) ou dans le panneau de droite de l’onglet [Lancements](#launches-in-the-content-fragment-console).

## Suppression d’un lancement {#delete-a-launch}

Après avoir promu votre lancement ou décidé que vous n’en avez plus besoin, vous pouvez le supprimer :

1. Accédez à la console Fragments de contenu .

1. Ouvrez l’onglet **Lancements**.

1. Sélectionnez votre lancement.

1. Sélectionnez **Supprimer le lancement**.

   Vous êtes invité à confirmer l’action avant la suppression du lancement.

## Détails concernant les références incluses {#details-concerning-included-references}

Pour les lancements , les références de fragment de contenu suivantes sont prises en compte, selon le [type de données](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types) :

* Le type de données **Référence de fragment**, applicable à la fois aux références de fragment unique et aux références de fragment à champs multiples.
* Fragments référencés dans le type de données **texte multiligne** lors de l’utilisation de **texte enrichi**.

Tous les points s’appliquent également aux fragments référencés dans les variations

Les éléments suivants ne sont pas pris en compte :

* Les fragments référencés dans les types de données de référence de contenu, à la fois **Référence de contenu** (basée sur un chemin d’accès) et **Référence de contenu (UUID)**.
* Fragments référencés dans le type de données **Référence de fragment (UUID)**.

---
title: Configuration de la segmentation avec ContextHub
description: Découvrez comment configurer la segmentation à l’aide de ContextHub.
translation-type: tm+mt
source-git-commit: c9c7176f6c3bf70529b761183341a2490d4ecbfc
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 47%

---


# Configuration de la segmentation avec ContextHub{#configuring-segmentation-with-contexthub}

La segmentation est un élément clé de la création d’une campagne. See [Understanding Segmentation](segmentation.md) for information on how segmentation works and key terms.

En fonction des informations que vous avez déjà collectées sur les visiteurs de votre site et des objectifs que vous souhaitez atteindre, vous devez définir les segments et les stratégies requis pour votre contenu ciblé.

Ces segments sont ensuite utilisés pour fournir aux visiteurs du contenu spécifiquement ciblé. Les [activités](activities.md) définies ici peuvent être ajoutées à n’importe quelle page et définissent à quel segment de visiteurs le contenu spécialisé s’applique.

aem vous permet de personnaliser facilement les expériences de vos utilisateurs. Il vous permet également de vérifier les résultats de vos définitions de segment.

## Accès aux segments {#accessing-segments}

The [Audiences](audiences.md) console is used to manage segments for ContextHub as well as audiences for your Adobe Target account. Cette documentation couvre la gestion des segments pour ContextHub.

Pour accéder à vos segments, dans la navigation globale, sélectionnez **Navigation > Personnalisation > Audiences**.

![Gestion des audiences](../assets/contexthub-segmentation-audiences.png)

## Éditeur de segment {#segment-editor}

<!--The **Segment Editor** allows you to easily modify a segment. To edit a segment, select a segment in the [list of segments](/help/sites-administering/segmentation.md#accessing-segments) and click the **Edit** button.-->
The **Segment Editor** allows you to easily modify a segment. Pour modifier un segment, sélectionnez un segment dans la liste de segments et cliquez sur le bouton **Modifier**.

![Éditeur de segments](../assets/contexthub-segment-editor.png)

Using the components browser you can add **AND** and **OR** containers to define the segment logic, then add additional components to compare properties and values or reference scripts and other segments to define the selection criteria (see [Creating a New Segment](#creating-a-new-segment)) to define the exact scenario for selecting the segment.

Lorsque l’intégralité de l’instruction est vraie, alors le segment a été résolu. Si plusieurs segments sont applicables, le facteur **Amplifier** est également utilisé. See [Creating a New Segment](#creating-a-new-segment) for details on the boost factor.

>[!CAUTION]
>
>L’éditeur de segment ne vérifie aucune référence circulaire. Par exemple, le segment A fait référence à un autre segment B qui, à son tour, fait référence au segment A. Vous devez vous assurer que vos segments ne contiennent aucune référence circulaire.

### Conteneurs {#containers}

Les conteneurs suivants sont disponibles clé en main et vous permettent de regrouper des comparaisons et des références en vue de l’évaluation booléenne. Ils peuvent être déplacés de l’explorateur de composants vers l’éditeur. See the following section [Using AND and OR Containers](#using-and-and-or-containers) for more information.

|  |  |
|---|---|
| Conteneur ET | Opérateur ET booléen |
| Conteneur OU | Opérateur OR booléen |

### Comparaisons {#comparisons}

Les comparaisons de segments suivantes sont disponibles par défaut pour évaluer les propriétés des segments. Elles peuvent être déplacées de l’explorateur de composants vers l’éditeur.

|  |  |
|---|---|
| Propriété-Valeur | Compare une propriété d’une boutique à une valeur définie |
| Propriété-Propriété | Compare une propriété d’un magasin à une autre propriété |
| Référence des segments de propriété | Compare une propriété d’un magasin à un autre segment référencé |
| Référence des scripts de propriété | Compare une propriété d’un magasin aux résultats d’un script |
| Référence de segment-Référence de script | Compare un segment référencé aux résultats d’un script |

>[!NOTE]
>
>Lors de la comparaison de valeurs, si le type de données de la comparaison n’est pas défini (c.-à-d. défini pour la détection automatique), le moteur de segmentation de ContextHub compare simplement les valeurs comme le ferait javascript. Il ne projette pas de valeurs sur leurs types inattendus, ce qui peut donner des résultats trompeurs. Par exemple :
>
>`null < 30 // will return true`
>
>Therefore when [creating a segment](#creating-a-new-segment), you should select a **data type** whenever the types of compared values are known. Par exemple :
>
>When comparing the property `profile/age`, you already know that the compared type will be **number**, so even if `profile/age` is not set, a comparison `profile/age` less-than 30 will return **false**, as you would expect.

### Références {#references}

Les références suivantes sont disponibles clé en main pour établir un lien direct à un script ou un segment différent. Elles peuvent être déplacées de l’explorateur de composants vers l’éditeur.

|  |  |
|---|---|
| Référence de segment | Évaluer le segment référencé |
| Référence de script | Evaluez le script référencé. Pour plus d’informations, voir la section [Utilisation de références](#using-script-references) de script. |

## Création d’un nouveau segment {#creating-a-new-segment}

Pour définir votre nouveau segment :

1. Après [avoir accédé aux segments](#accessing-segments), [accédez au dossier](#organizing-segments) dans lequel vous souhaitez créer le segment ou laissez-le à la racine.

1. Appuyez sur le bouton **Créer** ou cliquez dessus, puis sélectionnez **Créer un segment** ContextHub.

   ![Ajouter un segment](../assets/contexthub-create-segment.png)

1. Dans la section **Nouveau segment ContextHub**, tapez un titre pour le segment, ainsi qu’une valeur d’amplification si nécessaire, puis appuyez ou cliquez sur **Créer**.

   ![Nouveau segment](../assets/contexthub-new-segment.png)

   Chaque segment comporte un paramètre de stimulation utilisé comme facteur de pondération. Une valeur plus élevée indique que le segment sera sélectionné de préférence à un segment ayant une valeur plus basse dans les cas où plusieurs segments sont valides.

   * Valeur minimale : `0`
   * Valeur maximale : `1000000`

1. Dans la console des segments, modifiez le segment que vous venez de créer pour l’ouvrir dans l’éditeur de segments.
1. Faites glisser une comparaison ou une référence vers l’éditeur de segment dans lequel elle apparaîtra dans le conteneur ET par défaut.
1. Double-cliquez ou appuyez sur l’option de configuration de la nouvelle référence ou du nouveau segment pour modifier les paramètres. Dans cet exemple, nous testons des personnes à Bâle.

   ![Des tests pour les gens à Bâle](../assets/contexthub-comparing-property-value.png)

   Si possible, veillez à toujours définir un **type de données** pour vous assurer que vos comparaisons sont évaluées correctement. Voir la rubrique [Comparaisons](#comparisons) pour plus d’informations.

1. Click **Done** to save your definition:
1. Ajoutez d’autres composants, en fonction de vos besoins. Vous pouvez formuler des expressions booléennes à l’aide des composants de conteneur pour des comparaisons ET et OU (voir la rubrique [Utilisation des conteneurs ET et OU](#using-and-and-or-containers) ci-dessous). Avec l’éditeur de segment, vous pouvez supprimer les composants qui ne sont plus utiles ou les faire glisser vers un nouvel emplacement dans l’instruction.

### Utilisation des conteneurs ET et OU {#using-and-and-or-containers}

Avec les composants de conteneur ET et OU, vous pouvez créer des segments complexes dans AEM. Cette tâche sera plus facile si vous tenez compte de certains aspects élémentaires :

* Le niveau supérieur de la définition est toujours le conteneur ET initialement créé. Cette modification ne peut pas être modifiée, mais n’a aucun effet sur le reste de votre définition de segment.
* Assurez-vous que l’imbrication de votre conteneur a un sens. Les conteneurs peuvent être considérés comme les crochets de votre expression booléenne.

L’exemple suivant permet de sélectionner des visiteurs qui sont pris en compte dans notre Population cible suisse :

```text
 People in Basel

 OR

 People in Zürich
```

Commencez par placer un composant de conteneur OU dans le conteneur ET par défaut. Dans le conteneur OU, vous pouvez ajouter la propriété ou les composants de référence.

![Segmenter avec l’opérateur OU](../assets/contexthub-or-operator.png)

Vous pouvez imbriquer plusieurs opérateurs ET et OU selon les besoins.

### Utilisation de références de script {#using-script-references}

À l’aide du composant Référence de script, l’évaluation d’une propriété de segment peut être déléguée à un script externe. Une fois le script correctement configuré, il peut être utilisé comme n’importe quel autre composant d’une condition de segment.

#### Définition d’une référence de script {#defining-a-script-to-reference}

1. Add file to `contexthub.segment-engine.scripts` clientlib.
1. Implémentez une fonction qui renvoie une valeur. Par exemple :

   ```javascript
   ContextHub.console.log(ContextHub.Shared.timestamp(), '[loading] contexthub.segment-engine.scripts - script.profile-info.js');
   
   (function() {
       'use strict';
   
       /**
        * Sample script returning profile information. Returns user info if data is available, false otherwise.
        *
        * @returns {Boolean}
        */
       var getProfileInfo = function() {
           /* let the SegmentEngine know when script should be re-run */
           this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
           this.dependOn(ContextHub.SegmentEngine.Property('profile/givenName'));
   
           /* variables */
           var name = ContextHub.get('profile/givenName');
           var age = ContextHub.get('profile/age');
   
           return name === 'Joe' && age === 123;
       };
   
       /* register function */
       ContextHub.SegmentEngine.ScriptManager.register('getProfileInfo', getProfileInfo);
   
   })();
   ```

1. Register the script with `ContextHub.SegmentEngine.ScriptManager.register`.

Si le script dépend de propriétés supplémentaires, il doit appeler `this.dependOn()`. For example if the script depends on `profile/age`:

```javascript
this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
```

#### Référencement d’un script {#referencing-a-script}

1. Créez un segment ContextHub.
1. Ajoutez le composant **Référence de script** à l’emplacement souhaité du segment.
1. Ouvrez la boîte de dialogue de modification du composant **Référence de script**. S’il est [correctement configuré](#defining-a-script-to-reference), le script doit être disponible dans le menu déroulant **Nom du script**.

## Organisation des segments {#organizing-segments}

Si vous disposez de plusieurs segments, ils peuvent devenir difficiles à gérer en tant que liste plate. Dans ce cas, il peut s’avérer utile de créer des dossiers pour gérer vos segments.

### Create a New Folder {#create-folder}

1. After [accessing the segments](#accessing-segments), click or tap the **Create** button and select **Folder**.

   ![Dossier Ajouter](../assets/contexthub-create-segment.png)

1. Indiquez un **titre** et un **nom** pour votre dossier.
   * Le **titre** doit être descriptif.
   * Le **nom** deviendra le nom du noeud dans le référentiel.
      * Elle sera générée automatiquement en fonction du titre et ajustée en fonction des conventions de dénomination [AEM.](/help/implementing/developing/introduction/naming-conventions.md)
      * Il peut être ajusté si nécessaire.

   ![Créer un dossier](../assets/contexthub-create-folder.png)

1. Appuyez ou cliquez sur **Créer**.

   ![Confirmer le dossier](../assets/contexthub-confirm-folder.png)

1. Le dossier s’affiche dans la liste des segments.
   * La manière dont vous triez vos colonnes aura une incidence sur l&#39;emplacement d&#39;affichage du nouveau dossier dans la liste.
   * Vous pouvez appuyer ou cliquer sur les en-têtes de colonne pour ajuster votre tri.
      ![Le nouveau dossier](../assets/contexthub-folder.png)

### Modifier les dossiers existants {#modify-folders}

1. Après [avoir accédé aux segments](#accessing-segments), cliquez ou appuyez sur le dossier que vous souhaitez modifier pour le sélectionner.

   ![Sélectionner un dossier](../assets/contexthub-select-folder.png)

1. Appuyez ou cliquez sur **Renommer** dans la barre d’outils pour renommer le dossier.

1. Saisissez un nouveau titre **de** dossier et appuyez ou cliquez sur **Enregistrer**.

   ![Renommer le dossier](../assets/contexthub-rename-folder.png)

>[!NOTE]
>
>Lorsque vous renommez des dossiers, seul le titre peut être modifié. Le nom ne peut pas être modifié.

### Suppression d’un dossier

1. Après [avoir accédé aux segments](#accessing-segments), cliquez ou appuyez sur le dossier que vous souhaitez modifier pour le sélectionner.

   ![Sélectionner un dossier](../assets/contexthub-select-folder.png)

1. Appuyez ou cliquez sur **Supprimer** dans la barre d’outils pour supprimer le dossier.

1. Une boîte de dialogue présente une liste de dossiers sélectionnés pour suppression.

   ![Confirmer la suppression](../assets/contexthub-confirm-segment-delete.png)

   * Appuyez sur ou sur **Supprimer** pour confirmer.
   * Appuyez ou cliquez sur **Annuler** pour abandonner.

1. Si l’un des dossiers sélectionnés contient des sous-dossiers ou des segments, leur suppression doit être confirmée.

   ![Confirmer la suppression des enfants](../assets/contexthub-confirm-segment-child-delete.png)

   * Appuyez ou cliquez sur **Forcer la suppression** pour confirmer.
   * Appuyez ou cliquez sur **Annuler** pour abandonner.

>[!NOTE]
>
> Il n’est pas possible de déplacer un segment d’un dossier à un autre.

## Test de l’application d’un segment {#testing-the-application-of-a-segment}

Une fois le segment défini, les résultats potentiels peuvent être testés avec **[ContextHub](contexthub.md).**

1. Affichage de l’aperçu d’une page
1. Cliquez sur l’icône ContextHub pour afficher la barre d’outils ContextHub
1. Sélectionnez une personne qui correspond au segment que vous avez créé.
1. ContextHub permet de résoudre les segments applicables pour la personne sélectionnée.

Par exemple, notre définition de segment simple pour identifier les utilisateurs à Bâle est basée sur l’emplacement de l’utilisateur. Le chargement d’une personne spécifique qui correspond à ces critères indique si le segment a été résolu avec succès :

![Segment résolu](../assets/contexthub-segment-resolve.png)

Ou s’il n’est pas résolu :

![Segment non résolu](../assets/contexthub-segment-doesnt-resolve.png)

>[!NOTE]
>
>Toutes les caractéristiques sont résolues immédiatement, bien que la plupart ne soient modifiées qu’au rechargement de la page.

Ces tests peuvent également être effectués sur les pages de contenu et en combinaison avec le contenu ciblé et les **Activités** et **Expériences** associées.

Si vous avez configuré une activité et une expérience, vous pouvez facilement tester votre segment avec l’activité. Pour plus d’informations sur la configuration d’une activité, voir la [documentation relative à la création de contenu ciblé](targeted-content.md).

1. En mode de modification d’une page sur laquelle vous avez configuré du contenu ciblé, vous pouvez constater que le contenu est ciblé via une icône de flèche sur le contenu.
1. Basculez vers le mode Aperçu et, avec ContextHub, passez à une personne qui ne correspond pas à la segmentation configurée pour l’expérience.
1. Passez à une personne qui correspond à la segmentation configurée pour l’expérience et constatez que l’expérience change en conséquence.

## Utilisation de votre segment {#using-your-segment}

Les segments permettent de contrôler le contenu réel affiché par des audiences de cible spécifiques. See [Managing Audiences](audiences.md) for more information about audiences and segments and [Authoring Targeted Content](targeted-content.md) about using audiences and segments to target content.

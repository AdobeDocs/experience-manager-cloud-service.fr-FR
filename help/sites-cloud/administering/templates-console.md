---
title: Console Modèles
description: Découvrez comment la console de modèles sert d’emplacement central pour afficher et gérer vos modèles de page.
solution: Experience Manager Sites
feature: Administering
role: User
source-git-commit: 993f81e0ff2b71ce2edf59a2c74398db3abe8f06
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 3%

---


# Console Modèles {#templates-console}

Découvrez comment la console de modèles sert d’emplacement central pour afficher et gérer vos modèles de page.

## Vue d’ensemble {#overview}

Lors de la création d’une page, vous devez sélectionner un modèle. Le modèle de page est utilisé comme base pour la nouvelle page. [AEM des modèles modifiables](/help/implementing/developing/components/templates.md) peuvent définir la structure de la page créée, tout contenu initial et les composants qui peuvent être utilisés (propriétés de conception).

Les auteurs de contenu reçoivent une sélection de modèles disponibles lorsqu&#39;ils [ créent des pages dans la console Sites.](/help/sites-cloud/authoring/sites-console/creating-pages.md) Les modèles peuvent être utilisés pour créer des pages modifiables avec :

* [Éditeur de page](/help/sites-cloud/authoring/page-editor/templates.md) ou
* [Éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md)

La console de modèles permet à un administrateur d’afficher et de gérer tous les modèles de page dans un emplacement central.

## Accès à la console de modèles {#accessing}

1. Connectez-vous à AEM as a Cloud Service.
1. Ouvrez la navigation globale et sélectionnez le panneau **Outils** , puis **Général** -> **Modèles**.

## Orientation {#orientation}

La console de modèles est organisée en dossiers avec un dossier par [configuration](/help/implementing/developing/introduction/configurations.md) où des modèles modifiables ont été activés pour la configuration.

![La console Modèles](assets/templates-console/templates-console.png)

[La vue par défaut](/help/sites-cloud/authoring/quick-start.md) de la console est la vue Carte. Appuyez ou cliquez sur un dossier pour en explorer le contenu.

![Contenu du dossier de modèles dans la console de modèles](assets/templates-console/templates-console-templates.png)

Sélectionnez un modèle pour afficher les options disponibles dans la barre d’outils.

![Barre d’outils de la console Modèles](assets/templates-console/templates-console-toolbar.png)

* [Modifier](#edit-edit)
* [Propriétés](#properties)
* [Désactiver/activer](#enable-disable)
* [Publier](#publish)
* [Copier](#copy)
* [Supprimer](#delete)

## Modifier {#edit}

La modification d’un modèle ouvre l’éditeur qui a été utilisé pour créer le modèle. Vous pouvez effectuer les actions suivantes :

* [L’éditeur de modèles](/help/sites-cloud/authoring/page-editor/templates.md)
* [Éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md)

En utilisant n’importe quel éditeur, vous pouvez apporter les modifications nécessaires au modèle. Notez que la modification d’un modèle en cours d’utilisation peut affecter vos auteurs.

* Pour les modèles créés avec l’éditeur de modèles, les modifications apportées peuvent affecter les pages actives basées sur le modèle sélectionné.
* Pour les modèles créés avec l’éditeur universel, les modifications apportées n’affectent que les nouvelles pages que vos auteurs créent en fonction du modèle sélectionné.

Si un auteur commence par un modèle créé avec l’éditeur de modèles qui a déjà été activé, un avertissement s’affiche.

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez la touche d’accès rapide `e` pour modifier le modèle sélectionné.

## Propriétés {#properties}

Vous pouvez modifier les [propriétés du modèle](/help/sites-cloud/authoring/page-editor/templates.md) de la même manière que vous pouvez [modifier les propriétés de la page.](/help/sites-cloud/authoring/sites-console/page-properties.md) Les propriétés du modèle incluent :

* Titre du modèle
* Description
* Image

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez la touche d’accès rapide `p` pour ouvrir les propriétés du modèle sélectionné.

## Activer et désactiver {#enable-disable}

Un modèle peut avoir l’un des trois états suivants :

* **Version préliminaire** - Le modèle est toujours en cours de création et n’est pas disponible pour la création de pages.
* **Activé** - Le modèle est complet et disponible pour la création de pages.
* **Désactivé** - Le modèle est terminé mais n’est pas disponible pour la création de pages.

Lorsqu’un modèle est créé, il est soit dans un état **Brouillon** (pour les modèles créés avec l’[éditeur de modèles](/help/sites-cloud/authoring/page-editor/templates.md)), soit dans un état **Activé** (pour les modèles créés avec l’[éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md)).

Un modèle doit être activé avant de pouvoir être utilisé par les auteurs de contenu pour créer des pages. Si un modèle n’est plus nécessaire, il peut être désactivé afin qu’il ne s’affiche plus dans l’assistant de création de page.

* Sélectionnez le modèle et cliquez ou appuyez sur **Désactiver** pour le désactiver.
* Sélectionnez le modèle et cliquez ou appuyez sur **Activer** pour activer le modèle.

## Publication {#publish}

Un modèle créé avec l’éditeur de modèles ne peut être utilisé qu’une fois publié. Sélectionnez le modèle et cliquez ou appuyez sur **Publish** pour publier.

Il n’est pas nécessaire de publier les modèles créés avec Universal Editor pour les utiliser.

## Copie en cours {#copy}

Si vous disposez de plusieurs pages dont la structure est similaire, vous pouvez utiliser le bouton **Copier** pour créer une étendue d’un modèle, puis modifier la copie en fonction de vos besoins. Cela s’avère également utile si vous souhaitez utiliser un modèle sur un autre site.

1. Sélectionnez le modèle, puis appuyez ou cliquez sur **Copier** pour créer une copie.
1. Accédez à l’emplacement où vous souhaitez créer la copie.
1. Appuyez ou cliquez sur **Coller** dans la barre d’outils.

Une fois collé, vous pouvez :

* [Modifiez le modèle](#edit) pour l’ajuster selon les besoins.
* [Utilisez la fenêtre de propriétés](#properties) pour mettre à jour le titre du modèle.
* [Activez le modèle](#enable-disable) afin qu’il puisse être utilisé pour créer une page.
* [Publish le modèle](#publish) si nécessaire.

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez la touche d’accès rapide `Command+c` ou `ctrl+c` pour copier le modèle sélectionné.

## Suppression en cours {#delete}

Si un modèle n’est plus nécessaire, il peut être supprimé s’il n’est référencé par aucune page.

Sélectionnez le modèle, puis appuyez ou cliquez sur **Supprimer** pour le supprimer.

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez la touche d’accès rapide `Backspace` pour supprimer le modèle sélectionné.

## Création de modèles {#create}

Utilisez le bouton **Créer** de la console pour créer un modèle à l’emplacement actuel. Pour plus d’informations sur la création d’un modèle, consultez le document [Modèles de création de pages modifiables avec l’éditeur de page.](/help/sites-cloud/authoring/page-editor/templates.md)

Le bouton **Créer** sert uniquement à créer des modèles modifiables à l’aide de l’éditeur de page. Consultez le document [Modèles de création de pages modifiables avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md) pour en savoir plus sur la création de modèles à partir de pages créées avec l’éditeur universel.

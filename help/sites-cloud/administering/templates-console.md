---
title: Console Modèles
description: Découvrez comment la console de modèles sert d’emplacement central pour afficher et gérer vos modèles de page.
solution: Experience Manager Sites
feature: Administering
role: User
exl-id: d11d7176-dd35-4855-9dcd-dd40ff096510
source-git-commit: 3238b11cdd891cf18048199d4103397e3af75edf
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 3%

---

# Console Modèles {#templates-console}

Découvrez comment la console de modèles sert d’emplacement central pour afficher et gérer vos modèles de page.

## Vue d’ensemble {#overview}

Lors de la création d’une page, vous devez sélectionner un modèle. Le modèle de page est utilisé comme base pour la nouvelle page. [Les modèles modifiables AEM ](/help/implementing/developing/components/templates.md) peuvent définir la structure de la page créée, le contenu initial et les composants qui peuvent être utilisés (propriétés de conception).

Une sélection de modèles est présentée aux auteurs de contenu lorsqu’ils [créent des pages dans la console Sites](/help/sites-cloud/authoring/sites-console/creating-pages.md). Les modèles peuvent être utilisés pour créer des pages modifiables avec :

* [Éditeur de page](/help/sites-cloud/authoring/page-editor/templates.md) ou
* [Éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md)

La console de modèles permet à un administrateur ou une administratrice d’afficher et de gérer tous les modèles de page dans un emplacement central.

## Accès à la console Modèles {#accessing}

1. Connectez-vous à AEM as a Cloud Service
1. Ouvrez la navigation globale et sélectionnez le panneau **Outils**, puis **Général** -> **Modèles**.

## Orientation {#orientation}

La console de modèles est organisée en dossiers avec un dossier par [configuration](/help/implementing/developing/introduction/configurations.md) dans lequel les modèles modifiables ont été activés pour la configuration.

![Console Modèles](assets/templates-console/templates-console.png)

[La vue par défaut](/help/sites-cloud/authoring/quick-start.md) de la console est la vue Cartes. Appuyez ou cliquez sur un dossier pour en explorer le contenu.

![Contenu du dossier des modèles dans la console des modèles](assets/templates-console/templates-console-templates.png)

Sélectionnez un modèle pour afficher les options disponibles dans la barre d’outils.

![Barre d’outils de la console Modèles](assets/templates-console/templates-console-toolbar.png)

* [Modifier](#edit-edit)
* [Propriétés](#properties)
* [Désactiver/Activer](#enable-disable)
* [Publication](#publish)
* [Copier](#copy)
* [Supprimer](#delete)

## Modifier {#edit}

La modification d’un modèle ouvre l’éditeur utilisé pour créer le modèle. Vous pouvez effectuer les actions suivantes :

* [Éditeur de modèles](/help/sites-cloud/authoring/page-editor/templates.md)
* [Éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md)

À l’aide de l’éditeur de votre choix, vous pouvez apporter les modifications nécessaires au modèle. Notez que la modification d’un modèle en cours d’utilisation peut avoir une incidence sur vos auteurs.

* Pour les modèles créés avec l’éditeur de modèles, les modifications apportées peuvent affecter les pages en direct basées sur le modèle sélectionné.
* Pour les modèles créés avec l’éditeur universel, les modifications apportées n’affectent que les nouvelles pages créées par les auteurs en fonction du modèle sélectionné.

Si l’auteur commence à créer un modèle avec l’éditeur de modèles déjà activé, un avertissement s’affiche.

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez le raccourci `e` pour modifier le modèle sélectionné.

## Propriétés {#properties}

Vous pouvez modifier les [propriétés du modèle](/help/sites-cloud/authoring/page-editor/templates.md) de la même manière que vous pouvez [modifier les propriétés de la page.Les propriétés du modèle de ](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) incluent :

* Titre du modèle
* Description
* Image

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez le raccourci `p` pour ouvrir les propriétés du modèle sélectionné.

## Activation et désactivation {#enable-disable}

Un modèle peut avoir l’un des trois états suivants :

* **Brouillon** - Le modèle est toujours en cours de création et n’est pas disponible pour la création de pages.
* **Activé** - Le modèle est complet et disponible pour la création de pages.
* **Désactivé** - Le modèle est terminé, mais il n’est pas disponible pour la création de pages.

Lorsqu’un modèle est créé, il est par défaut à l’état **Brouillon** (pour les modèles créés avec l’[Éditeur de modèles](/help/sites-cloud/authoring/page-editor/templates.md)) ou **Activé** (pour les modèles créés avec l’[Éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md)).

Un modèle doit être activé avant de pouvoir être utilisé par les personnes créant du contenu pour créer des pages. Si un modèle n’est plus nécessaire, il peut être désactivé afin de ne plus s’afficher dans l’assistant de création de page.

* Sélectionnez le modèle et cliquez sur **Désactiver** pour le désactiver.
* Sélectionnez le modèle et cliquez sur **Activer** pour l’activer.

## Publication {#publish}

Un modèle créé avec l’éditeur de modèles ne peut être utilisé qu’une fois publié. Sélectionnez le modèle, puis cliquez sur **Publier** pour le publier.

Les modèles créés avec l’éditeur universel n’ont pas besoin d’être publiés pour être utilisés.

## Copie en cours {#copy}

Si la structure de plusieurs pages est similaire, vous pouvez utiliser le bouton **Copier** pour créer la portée d’un modèle, puis modifier la copie en fonction de vos besoins. Cela s’avère également utile si vous souhaitez utiliser un modèle sur un autre site.

1. Sélectionnez le modèle, puis appuyez ou cliquez sur **Copier** pour créer une copie.
1. Accédez à l’emplacement où vous souhaitez créer la copie.
1. Appuyez ou cliquez sur **Coller** dans la barre d’outils.

Une fois collé, vous pouvez :

* [Modifiez le modèle](#edit) pour l’ajuster si nécessaire.
* [Utilisez la fenêtre des propriétés](#properties) pour mettre à jour le titre du modèle.
* [Activez le modèle](#enable-disable) afin qu’il puisse être utilisé pour créer une page.
* [Publiez le modèle](#publish) si nécessaire.

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez le raccourci clavier `Command+c` ou `ctrl+c` pour copier le modèle sélectionné.

## Suppression en cours {#delete}

Si un modèle n’est plus nécessaire, il peut être supprimé à condition qu’il ne soit référencé par aucune page.

Sélectionnez le modèle, puis appuyez ou cliquez sur **Supprimer** pour le supprimer.

>[!TIP]
>
>Une fois que vous avez sélectionné un modèle dans la console, utilisez le raccourci `Backspace` pour supprimer le modèle sélectionné.

## Création de modèles {#create}

Utilisez le bouton **Créer** de la console pour créer un modèle à votre emplacement actuel. Pour plus d’informations sur la création d’un modèle, consultez le document [ Modèles pour créer des pages modifiables avec l’éditeur de page ](/help/sites-cloud/authoring/page-editor/templates.md).

Le bouton **Créer** n’est utilisé que pour créer des modèles modifiables avec l’éditeur de page. Consultez le document [Modèles pour créer des pages modifiables avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md) pour en savoir plus sur la création de modèles basés sur des pages créées avec l’éditeur universel.

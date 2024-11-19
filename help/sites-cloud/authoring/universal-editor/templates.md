---
title: Modèles de création de pages modifiables à l’aide de l’éditeur universel
description: Découvrez comment créer des modèles qui peuvent être utilisés pour créer des pages modifiables à l’aide de l’éditeur universel, ce qui vous permet de gagner du temps et d’assurer une valorisation de marque cohérente.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: f0d60086-e92e-4492-ad50-bef84fed2a82
source-git-commit: 92da26452438f2b56cdec1aecc76587d4982f00e
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 3%

---


# Modèles de création de pages modifiables à l’aide de l’éditeur universel {#page-templates}

Découvrez comment créer des modèles qui peuvent être utilisés pour créer des pages modifiables à l’aide de l’éditeur universel, ce qui vous permet de gagner du temps et d’assurer une valorisation de marque cohérente.

>[!NOTE]
>
>[ Des modèles sont également disponibles pour créer des pages modifiables à l’aide de l’éditeur de page.](/help/sites-cloud/authoring/page-editor/templates.md)

## Que sont les modèles de page ? {#what-are}

Les directives de marketing et de branding dictent souvent des mises en page spécifiques pour vos pages de contenu. Il est également courant que la plupart de vos pages partagent la même structure et la même mise en page. Pour gagner du temps aux auteurs de contenu, vous pouvez créer des pages à partir de modèles.

Les modèles de page servent de gabarits de mises en page. Lorsque vous créez une page à partir d’un modèle, le contenu initial du modèle est copié dans la nouvelle page, ce qui permet de prédéfinir la mise en page et le contenu de base de la page pour l’auteur du contenu, ce qui leur permet de gagner du temps.

## Activation des modèles de page {#enabling-templates}

Pour utiliser des modèles afin de créer des pages modifiables à l’aide de l’éditeur universel, vous devez activer l’option .

Commencez d’abord par activer les modèles modifiables pour la configuration de votre site.

1. Utilisez la console **Sites** et [sélectionnez la racine de votre site.](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)
1. Une fois la racine du site sélectionnée, appuyez ou cliquez sur l’icône [**Propriétés**](/help/sites-cloud/authoring/sites-console/page-properties.md) dans la barre d’outils.
1. Dans l’onglet **Avancé** de la boîte de dialogue Propriétés, notez la valeur du champ **Configuration cloud**.
1. Dans la navigation principale, sélectionnez **Outils** -> **Général** -> **Navigateur de configuration**.
1. Dans le **[navigateur de configuration,](/help/implementing/developing/introduction/configurations.md)** sélectionnez la configuration que vous avez remarquée à l’étape précédente et appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre **Propriétés de configuration**, cochez l’option **Modèles modifiables**.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

Une fois la configuration activée, vous devez autoriser les modèles pour votre site.

1. Utilisez la console **Sites** et [sélectionnez la racine de votre site.](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)
1. Une fois la racine du site sélectionnée, appuyez ou cliquez sur l’icône [**Propriétés**](/help/sites-cloud/authoring/sites-console/page-properties.md) dans la barre d’outils.
1. Dans l’onglet **Avancé** de la boîte de dialogue Propriétés sous la section **Paramètres du modèle**, appuyez ou cliquez sur le bouton **Ajouter** .
1. Dans le nouveau champ vide qui apparaît sous **Modèles autorisés**, ajoutez le chemin `/conf/<site>/settings/wcm/templates/.*`.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

Vous pouvez désormais utiliser des modèles pour créer des pages pour votre site. Cette tâche ne doit être effectuée qu’une seule fois pour chaque site/configuration sur lequel vous souhaitez utiliser des modèles lors de la création de pages modifiables à l’aide de l’éditeur universel.

## Création d’un modèle {#create-new}

Vous pouvez [ créer une page](/help/sites-cloud/authoring/sites-console/creating-pages.md) qui servira de modèle ou utiliser une page existante comme base de modèle.

1. Utilisez la console **Sites** pour [ accéder à la page nouvelle ou existante](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) que vous souhaitez utiliser comme modèle et appuyez ou cliquez dessus pour la sélectionner.

1. Une fois la page sélectionnée, appuyez ou cliquez sur l’icône [**Propriétés**](/help/sites-cloud/authoring/sites-console/page-properties.md) dans la barre d’outils.

1. Dans l’onglet **Avancé** de la boîte de dialogue Propriétés sous la section **Paramètres du modèle**, sélectionnez le bouton d’activation/désactivation **Utiliser la page comme modèle**.

1. Appuyez et cliquez sur **Enregistrer et fermer**.

La nouvelle page peut désormais être utilisée comme modèle lors de la création de pages.

## Création d’une page à partir d’un modèle {#creating-from-template}

La création d’une page à partir d’un modèle modifiable avec l’éditeur universel est le même processus que la [création d’une autre page.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Utilisez la console **Sites** pour [ accéder à l’emplacement](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) où vous souhaitez créer la page.

1. Appuyez ou cliquez sur **Créer** -> **Page**.

1. Sur l’onglet **Modèle** de l’assistant **Créer une page**, vous pouvez sélectionner le modèle sur lequel vous souhaitez baser votre nouvelle page. Appuyez ou cliquez sur le modèle souhaité pour le sélectionner, puis appuyez ou cliquez sur **Suivant**.

Suivez l’assistant comme vous le feriez pour toute autre page et vous avez créé votre nouvelle page en fonction du modèle sélectionné.

## Pages et modèles {#pages-vs-templates}

Les modèles de page définissent uniquement le contenu initial des pages. Les pages sont alors entièrement modifiables à l’aide de l’éditeur universel.

* Les pages créées à partir de modèles de pages sont des copies indépendantes du modèle.
* Si le modèle change, les pages existantes basées sur ce modèle ne changent pas.
* L’auteur du contenu peut modifier et mettre à jour le contenu de la page résultant du processus, le cas échéant, sans restriction de la part du modèle.

## Modèles modifiables {#editable-templates}

Les pages créées avec l’[ éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) peuvent également être basées sur des modèles. Les modèles utilisés pour créer des pages pour l’éditeur universel et l’éditeur de page tirent tous deux parti AEM [modèles modifiables.](/help/implementing/developing/components/templates.md)

Les modèles utilisés pour créer des pages modifiables avec l’éditeur de page utilisent toutes les fonctionnalités des modèles modifiables. Les modèles utilisés pour créer des pages modifiables à l’aide de l’éditeur universel n’utilisent que la fonction de contenu initiale.

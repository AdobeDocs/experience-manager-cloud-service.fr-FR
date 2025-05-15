---
title: Modèles pour créer des pages modifiables avec l’éditeur universel
description: Découvrez comment créer des modèles qui peuvent être utilisés pour créer des pages modifiables avec l’éditeur universel, ce qui vous permet de gagner du temps et de garantir la cohérence de l’image de marque.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: f0d60086-e92e-4492-ad50-bef84fed2a82
source-git-commit: bcf0940d3365ecde6788772d28d32f22f367816d
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 26%

---


# Modèles pour créer des pages modifiables avec l’éditeur universel {#page-templates}

Découvrez comment créer des modèles qui peuvent être utilisés pour créer des pages modifiables avec l’éditeur universel, ce qui vous permet de gagner du temps et de garantir la cohérence de l’image de marque.

>[!NOTE]
>
>[Des modèles sont également disponibles pour créer des pages modifiables avec l’éditeur de page](/help/sites-cloud/authoring/page-editor/templates.md).

## Que sont les modèles de page ? {#what-are}

Les directives de marketing et de branding dictent souvent des mises en page spécifiques pour vos pages de contenu. Il est également courant que la plupart de vos pages partagent la même structure et la même mise en page. Pour faire gagner du temps aux personnes chargées de la création du contenu, vous pouvez créer des pages à partir de modèles.

Les modèles de page servent de gabarits de mises en page. Lorsque vous créez une page à partir d’un modèle, le contenu initial du modèle est copié dans la nouvelle page, ce qui permet de prédéfinir la disposition et le contenu de base de la page pour l’auteur du contenu et de gagner du temps.

## Activation des modèles de page {#enabling-templates}

Pour utiliser des modèles afin de créer des pages modifiables avec l’éditeur universel, vous devez activer l’option .

Commencez par activer les modèles modifiables pour la configuration de votre site.

1. Utilisez la console **Sites** et [sélectionnez la racine de votre site](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources).
1. Une fois la racine du site sélectionnée, appuyez ou cliquez sur l’icône [**Propriétés** de la barre d’outils](/help/sites-cloud/authoring/sites-console/page-properties.md).
1. Dans l’onglet **Avancé** de la boîte de dialogue des propriétés, notez la valeur du champ **Configuration cloud**.
1. Dans la navigation principale, choisissez **Outils** -> **Général** -> **Explorateur de configurations**.
1. Dans le **[navigateur de configuration](/help/implementing/developing/introduction/configurations.md)**, sélectionnez la configuration que vous avez notée à l’étape précédente et appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre **Propriétés de configuration**, cochez l’option **Modèles modifiables**.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

Une fois la configuration activée, vous devez autoriser les modèles pour votre site.

1. Utilisez la console **Sites** et [sélectionnez la racine de votre site](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources).
1. Une fois la racine du site sélectionnée, appuyez ou cliquez sur l’icône [**Propriétés** de la barre d’outils](/help/sites-cloud/authoring/sites-console/page-properties.md).
1. Sous l’onglet **Avancé** de la boîte de dialogue des propriétés, sous la section **Paramètres de modèle**, appuyez ou cliquez sur le bouton **Ajouter**.
1. Dans le nouveau champ vide qui s’affiche sous **Modèles autorisés**, ajoutez le chemin d’accès `/conf/<site>/settings/wcm/templates/.*`.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

Vous pouvez désormais utiliser des modèles pour créer des pages pour votre site. Cette tâche ne doit être effectuée qu’une seule fois pour chaque site/configuration pour lequel vous souhaitez utiliser des modèles lors de la création de pages modifiables avec l’éditeur universel.

## Création d’un modèle {#create-new}

Vous pouvez [créer une page](/help/sites-cloud/authoring/sites-console/creating-pages.md) qui servira de modèle ou utiliser une page existante comme base d’un modèle.

1. Utilisez la console **Sites** pour [accéder à la page nouvelle ou existante](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) que vous souhaitez utiliser comme modèle, puis appuyez ou cliquez dessus pour la sélectionner.

1. Une fois la page sélectionnée, appuyez ou cliquez sur l’icône [**Propriétés** de la barre d’outils](/help/sites-cloud/authoring/sites-console/page-properties.md).

1. Dans l’onglet **Avancé** de la boîte de dialogue des propriétés, sous la section **Paramètres du modèle**, sélectionnez le bouton (bascule) **Utiliser la page comme modèle**.

1. Appuyez et cliquez sur **Enregistrer et fermer**.

La nouvelle page peut désormais être utilisée comme modèle lors de la création de pages.

## Création d’une page à partir d’un modèle {#creating-from-template}

La création d’une page à partir d’un modèle modifiable avec l’éditeur universel est le même processus que [création d’une autre page](/help/sites-cloud/authoring/sites-console/creating-pages.md).

1. Utilisez la console **Sites** pour [accéder à l’emplacement](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) où vous souhaitez créer la page.

1. Appuyez ou cliquez sur **Créer** -> **Page**.

1. Sur l’onglet **Modèle** de l’assistant **Créer une page**, vous pouvez sélectionner le modèle sur lequel vous souhaitez baser votre nouvelle page. Appuyez ou cliquez sur le modèle voulu pour le sélectionner, puis appuyez ou cliquez sur **Suivant**.

Suivez l’assistant comme vous le feriez pour toute autre page et vous avez créé votre nouvelle page en fonction du modèle sélectionné.

## Pages et modèles {#pages-vs-templates}

Les modèles de page ne définissent que le contenu initial des pages. Les pages sont alors entièrement modifiables avec l’éditeur universel.

* Les pages créées à partir de modèles de page sont des copies indépendantes du modèle.
* Si le modèle change, les pages existantes basées sur ce modèle ne changent pas.
* La personne ayant créé le contenu peut modifier et mettre à jour le contenu de la page résultant du processus, le cas échéant, sans restriction de la part du modèle.

## Modèles modifiables {#editable-templates}

Les pages créées avec l’[éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) peuvent également être basées sur des modèles. Les modèles utilisés pour créer des pages pour l’éditeur universel et l’éditeur de page exploitent tous deux AEM [modèles modifiables](/help/implementing/developing/components/templates.md).

Les modèles utilisés pour créer des pages modifiables avec l’éditeur de page exploitent toutes les fonctionnalités des modèles modifiables. Les modèles utilisés pour créer des pages modifiables avec l’éditeur universel n’utilisent que la fonction de contenu initial.

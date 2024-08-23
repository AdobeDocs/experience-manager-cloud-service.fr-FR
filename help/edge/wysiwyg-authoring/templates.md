---
title: Utilisation des modèles de page avec l’éditeur universel
description: Découvrez comment créer et utiliser des modèles de page avec l’éditeur universel.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 773ce75975f4dcc2c5310422bcc377b487ebec25
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 2%

---


# Utilisation des modèles de page avec l’éditeur universel {#page-templates}

Découvrez comment créer et utiliser des modèles de page avec l’éditeur universel.

>[!NOTE]
>
>Cette fonctionnalité sera disponible dans une prochaine version d’AEM as a Cloud Service.

## Que sont les modèles de page ? {#what-are}

Les directives de marketing et de branding dictent souvent des mises en page spécifiques pour vos pages de contenu. Il est également courant que la plupart de vos pages partagent la même structure et la même mise en page. Pour gagner du temps aux auteurs de contenu, vous pouvez créer des pages à partir de modèles.

Les modèles de page servent de gabarits de mises en page. Lorsque vous créez une page à partir d’un modèle, le contenu du modèle est copié dans la nouvelle page, ce qui permet de prédéfinir la mise en page et le contenu initial de la page pour l’auteur du contenu, ce qui leur permet de gagner du temps.

## Création d’un modèle de page {#creating}

Vous pouvez créer un modèle de page en créant une page ou en utilisant une page existante pour servir de modèle. Dans les deux cas, vous utilisez la console [**Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)

### Création d’un modèle {#create-new}

1. Utilisez la console **Sites** pour accéder à l’emplacement où vous souhaitez créer la page qui servira de modèle et [créer la page comme vous le feriez pour une autre.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Une fois la page créée et que vous revenez à la console, sélectionnez la page, puis appuyez ou cliquez sur l’icône [**Propriétés**](/help/sites-cloud/authoring/sites-console/page-properties.md) dans la barre d’outils.

1. Dans l’onglet **Avancé** de la boîte de dialogue Propriétés sous la section **Paramètres du modèle**, sélectionnez le bouton d’activation/désactivation **Utiliser comme modèle**.

1. Dans le champ **Nom du modèle**, indiquez un nom explicite.

   * Il s’agit du nom qui indique la création de pages de contenu et vous sélectionnez un modèle sur lequel baser la nouvelle page.

1. Appuyez et cliquez sur **Enregistrer et fermer**.

La nouvelle page peut désormais être utilisée comme modèle lors de la création de pages.

### Utilisation d’une page existante comme modèle {#existing-page}

1. Utilisez la console **Sites** pour [ accéder à l’emplacement de la page](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) que vous souhaitez utiliser comme modèle.

1. Sélectionnez la page, puis appuyez ou cliquez sur l’icône [**Propriétés**](/help/sites-cloud/authoring/sites-console/page-properties.md) dans la barre d’outils.

1. Dans l’onglet **Avancé** de la boîte de dialogue Propriétés sous la section **Paramètres du modèle**, sélectionnez le bouton d’activation/désactivation **Utiliser comme modèle**.

1. Dans le champ **Nom du modèle**, indiquez un nom explicite.

   * Il s’agit du nom qui indique la création de pages de contenu et vous sélectionnez un modèle sur lequel baser la nouvelle page.

1. Appuyez et cliquez sur **Enregistrer et fermer**.

La page sélectionnée peut désormais être utilisée comme modèle lors de la création de pages.

## Création d’une page à partir d’un modèle {#creating-from-template}

La création d&#39;une page à partir d&#39;un modèle à utiliser avec l&#39;éditeur universel est le même processus que lors de la [création de la page comme vous le feriez pour n&#39;importe quel autre.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Utilisez la console **Sites** pour [ accéder à l’emplacement](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) où vous souhaitez créer la page.

1. Appuyez ou cliquez sur **Créer** -> **Page**.

1. Sur l’onglet **Modèle** de l’assistant **Créer une page**, vous pouvez sélectionner le modèle sur lequel vous souhaitez baser votre nouvelle page. Appuyez ou cliquez sur le modèle souhaité pour le sélectionner, puis appuyez ou cliquez sur **Suivant**.

Suivez l’assistant comme vous le feriez pour toute autre page et vous avez créé votre nouvelle page en fonction du modèle sélectionné.

## Éditeur universel et éditeur de page {#page-vs-universal}

Les modèles de page pour l’éditeur universel résolvent le même problème que les modèles de page [pour l’éditeur de page AEM :](/help/sites-cloud/authoring/page-editor/templates.md) afin de pouvoir réutiliser le contenu pour créer rapidement des pages en fonction d’un ensemble de mises en page prédéfinies. Cependant, ils résolvent le problème de façons très différentes. Si vous utilisez l’éditeur de page, veuillez tenir compte de ces différences.

* Les pages créées à partir de modèles de pages pour l’éditeur universel sont des copies indépendantes du modèle.
* Par conséquent, si le modèle change, les pages résultantes ne changent pas.
* L’auteur du contenu peut modifier et mettre à jour le contenu de la page résultant du processus, le cas échéant, sans restriction de la part du modèle.

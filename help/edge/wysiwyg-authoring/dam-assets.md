---
title: Publication de pages avec DAM Assets à l’aide de Edge Delivery Services
description: Découvrez les paramètres requis pour vous assurer que les ressources de gestion des ressources numériques de vos pages sont publiées de manière transparente dans les Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 160f0474-a72d-4183-a2b2-2f8ba177605d
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 2%

---

# Publication de pages avec DAM Assets à l’aide de Edge Delivery Services {#dam-assets}

Découvrez les paramètres requis pour vous assurer que les ressources de gestion des ressources numériques de vos pages sont publiées de manière transparente dans les Edge Delivery Services.

## Éditeur universel, DAM Assets et Edge Delivery {#overview}

Lors de la modification du contenu pour l’éditeur universel, vous pouvez bien sûr sélectionner des ressources dans la gestion des ressources numériques (DAM). Lorsque vous publiez votre contenu dans les Edge Delivery Services, le contenu de gestion des ressources numériques associé est également publié.

Pour garantir ce comportement transparent, AEM et les Edge Delivery Services doivent disposer d’un accès approprié à la gestion des ressources numériques pour pouvoir effectuer la publication. Cela inclut les éléments suivants :

* [Accès aux dossiers de ressources](#accessible).
* [S’assurer que le dossier de ressources se voit attribuer la configuration appropriée (selon les besoins)](#configuration)

## Vérification de l’accessibilité des dossiers Assets {#accessible}

Lors de la publication de pages d’AEM dans des Edge Delivery Services, [un compte technique](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) est utilisé. Ce compte, dont le nom est au format `<hash>@techacct.adobe.com`, est créé automatiquement en tant qu’utilisateur dans AEM par Cloud Manager chaque fois que vous publiez une page créée avec l’éditeur universel pour la première fois.

![ Compte technique ](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

Ce compte technique doit disposer de droits d’accès à tous les dossiers de gestion des ressources numériques pour publier son contenu. Vous pouvez effectuer l’une des actions suivantes :

* N’utilisez pas de dossiers DAM privés.
* Accordez à l’utilisateur du compte technique l’accès aux dossiers de gestion des ressources numériques.

## Assurance que la configuration appropriée est affectée au dossier Assets {#configuration}

En règle générale, il suffit de s’assurer que votre compte technique a accès à vos ressources dans la gestion des ressources numériques pour publier vos ressources ainsi que vos pages dans les Edge Delivery Services.

Une configuration supplémentaire est toutefois nécessaire dans deux cas supplémentaires :

* Si vous souhaitez publier des pages avec des ressources autres que des images, telles que des PDF ou des vidéos, dans des Edge Delivery Services.
* Si vous souhaitez publier des ressources d’image dans des Edge Delivery Services indépendamment des pages.

Pour prendre en charge ces deux cas d’utilisation, une [configuration](/help/implementing/developing/introduction/configurations.md) doit être affectée au dossier de gestion des ressources numériques.

1. Connectez-vous à votre environnement de création AEM.
1. Sous **Sites** sélectionnez le site sur lequel vous publiez vos ressources ou le site auquel elles seront associées.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans l’onglet **Avancé** de la fenêtre des propriétés, notez la configuration dans le champ **Configuration cloud**.
   * Il est créé automatiquement lorsque vous créez votre site au format `/conf/<site-name>`.
1. Appuyez ou cliquez sur **Annuler** dans la fenêtre des propriétés et accédez à **Assets** -> **Fichiers**, puis sélectionnez votre dossier de gestion des ressources numériques.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans l’onglet **Cloud Service** de la fenêtre des propriétés, dans le champ **Configuration du cloud**, sélectionnez la même configuration que celle indiquée précédemment.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

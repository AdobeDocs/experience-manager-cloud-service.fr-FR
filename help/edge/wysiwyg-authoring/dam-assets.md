---
title: Publication de pages avec DAM Assets à l’aide de Edge Delivery Services
description: Découvrez les paramètres requis pour vous assurer que vos ressources DAM pour vos pages sont publiées en toute transparence vers les Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 65a3b4d923a91702e7ea9b13356802836fa4ce0b
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 2%

---


# Publication de pages avec DAM Assets à l’aide de Edge Delivery Services {#dam-assets}

Découvrez les paramètres requis pour vous assurer que vos ressources DAM pour vos pages sont publiées en toute transparence vers les Edge Delivery Services.

## Éditeur universel, DAM Assets et Edge Delivery {#overview}

Lorsque vous modifiez du contenu pour l’éditeur universel, vous pouvez bien sûr sélectionner des ressources dans la gestion des ressources numériques. Lorsque vous publiez votre contenu sur des Edge Delivery Services, le contenu DAM associé est également publié.

Pour garantir ce comportement transparent, AEM et les Edge Delivery Services doivent disposer d’un accès approprié à la gestion des ressources numériques pour pouvoir publier. Cela inclut les éléments suivants :

* [Vérification de l’accessibilité des dossiers de ressources.](#accessible)
* [Assurez-vous que la configuration appropriée est affectée au dossier assets (selon les besoins).](#configuration)

## Vérification de l’accessibilité des dossiers Assets {#accessible}

Lors de la publication de pages d’AEM vers des Edge Delivery Services, [un compte technique](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) est utilisé. Ce compte, avec un nom au format `<hash>@techacct.adobe.com`, est créé automatiquement en tant qu’utilisateur dans AEM par Cloud Manager dès que vous publiez une page créée avec l’éditeur universel.

![Compte technique](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

Ce compte technique doit disposer de droits d’accès à tous les dossiers DAM pour publier leur contenu. Vous pouvez effectuer l’une des actions suivantes :

* N’utilisez pas de dossiers DAM privés.
* Octroyez à l’utilisateur du compte technique l’accès aux dossiers DAM.

## Vérification de l’attribution d’une configuration appropriée au dossier Assets {#configuration}

En règle générale, s’assurer que votre compte technique a accès à vos ressources dans la gestion des ressources numériques est suffisant pour publier vos ressources avec vos pages sur des Edge Delivery Services.

Une configuration supplémentaire est toutefois nécessaire dans deux cas supplémentaires :

* Si vous souhaitez publier des pages contenant des ressources autres que des images, telles que des PDF ou des vidéos, sur des Edge Delivery Services.
* Si vous souhaitez publier des ressources d’image sur des Edge Delivery Services indépendamment des pages.

Pour prendre en charge ces deux cas d’utilisation, une [configuration](/help/implementing/developing/introduction/configurations.md) doit être affectée au dossier DAM.

1. Connectez-vous à votre environnement de création AEM.
1. Sous **Sites**, sélectionnez le site sur lequel vous publiez vos ressources ou le site auquel elles seront associées.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans l’onglet **Avancé** de la fenêtre des propriétés, prenez note de la configuration dans le champ **Configuration cloud**.
   * Ceci est créé automatiquement lorsque vous créez votre site au format `/conf/<site-name>`.
1. Appuyez ou cliquez sur **Annuler** dans la fenêtre des propriétés, puis accédez à **Assets** -> **Fichiers** et sélectionnez votre dossier DAM.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans l’onglet **Cloud Service** de la fenêtre des propriétés, dans le champ **Configuration cloud**, sélectionnez la même configuration que celle que vous avez précédemment mentionnée.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

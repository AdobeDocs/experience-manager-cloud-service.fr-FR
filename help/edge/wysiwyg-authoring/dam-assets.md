---
title: Publication de pages avec des ressources DAM à l’aide d’Edge Delivery Services
description: Découvrez les paramètres requis pour vous assurer que les ressources DAM de vos pages sont publiées de manière transparente sur Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 160f0474-a72d-4183-a2b2-2f8ba177605d
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '433'
ht-degree: 100%

---

# Publication de pages avec des ressources DAM à l’aide d’Edge Delivery Services {#dam-assets}

Découvrez les paramètres requis pour vous assurer que les ressources DAM de vos pages sont publiées de manière transparente sur Edge Delivery Services.

## Éditeur universel, ressources DAM et Edge Delivery {#overview}

Lors de la modification du contenu pour l’éditeur universel, vous pouvez bien sûr sélectionner des ressources dans la gestion des ressources numériques (DAM). Lorsque vous publiez votre contenu dans Edge Delivery Services, le contenu DAM associé est également publié.

Pour garantir ce comportement fluide, AEM et Edge Delivery Services doivent disposer d’un accès approprié à la gestion des ressources numériques pour pouvoir effectuer la publication. Cela comprend :

* [Garantir l’accès aux dossiers de ressources](#accessible).
* [Garantir que le dossier de ressources se voit attribuer la configuration appropriée (selon les besoins)](#configuration).

## Garantie de l’accessibilité des dossiers de ressources {#accessible}

Lors de la publication de pages d’AEM vers Edge Delivery Services, [un compte technique](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) est utilisé. Ce compte, dont le nom est au format `<hash>@techacct.adobe.com`, est créé automatiquement en tant qu’utilisateur ou utilisatrice dans AEM par Cloud Manager chaque fois que vous publiez pour la première fois une page créée avec l’éditeur universel.

![Compte technique](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

Ce compte technique doit disposer de droits d’accès à tous les dossiers DAM pour en publier le contenu. Vous pouvez effectuer l’une des actions suivantes :

* N’utilisez pas de dossiers DAM privés.
* Accordez à l’utilisateur ou à l’utilisatrice du compte technique l’accès aux dossiers DAM.

## Configuration correcte du dossier de ressources {#configuration}

En règle générale, il suffit de s’assurer que votre compte technique a accès à vos ressources dans la gestion des ressources numériques pour publier vos ressources ainsi que vos pages dans Edge Delivery Services.

Une configuration supplémentaire est toutefois nécessaire dans deux cas supplémentaires :

* Si vous souhaitez publier dans Edge Delivery Services des pages contenant des ressources autres que des images, par exemple des fichiers PDF ou des vidéos.
* Si vous souhaitez publier des ressources d’images dans Edge Delivery Services indépendamment des pages.

Pour prendre en charge ces deux cas d’utilisation, une [configuration](/help/implementing/developing/introduction/configurations.md) doit être affectée au dossier DAM.

1. Connectez-vous à votre environnement de création AEM.
1. Sous **Sites**, sélectionnez le site sur lequel vous publiez vos ressources ou le site auquel elles seront associées.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans l’onglet **Avancé** de la fenêtre des propriétés, notez la configuration dans le champ **Configuration cloud**.
   * Cet élément est créé automatiquement lorsque vous créez votre site au format `/conf/<site-name>`.
1. Appuyez ou cliquez sur **Annuler** dans la fenêtre des propriétés et accédez à **Ressources** -> **Fichiers**, puis sélectionnez votre dossier DAM.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans l’onglet **Services cloud** de la fenêtre des propriétés, dans le champ **Configuration cloud**, sélectionnez la même configuration que celle que vous avez notée précédemment.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

---
title: Réplication de la gestion multisite
description: Découvrez les recommandations de bonnes pratiques sur la configuration d’un projet de manière réorganisée avec des sites localisés qui utilisent une seule base de code, chacune fournie par des Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: e25e21984ebadde7076d95c6051b8bfca5b2ce03
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 1%

---


# Réplication de la gestion multisite {#repoless-msm}

Découvrez les recommandations de bonnes pratiques sur la configuration d’un projet de manière réorganisée avec des sites localisés qui utilisent une seule base de code, chacune fournie par des Edge Delivery Services.

## Vue d’ensemble {#overview}

[Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) et ses fonctionnalités Live Copy vous permettent d’utiliser le même contenu de site à plusieurs emplacements, tout en autorisant des variations. Vous pouvez créer du contenu une seule fois et créer des Live Copies. MSM entretient des relations en direct entre le contenu source et ses Live Copies de sorte que lorsque vous modifiez le contenu source, la source et les Live Copies peuvent être synchronisées.

Vous pouvez utiliser MSM pour créer une structure de contenu complète pour votre marque, quelle que soit la langue et la langue, en créant le contenu de manière centralisée. Vos sites localisés peuvent ensuite être diffusés par des Edge Delivery Services, en utilisant une base de code centrale.

## Conditions requises {#requirements}

Pour configurer MSM dans un cas d’utilisation de réplication, vous devez d’abord effectuer un certain nombre de tâches.

* Ce document suppose que vous avez déjà créé un site pour votre projet en fonction du guide de prise en main [du développeur pour la création WYSIWYG avec des Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md).
* Vous devez avoir déjà [activé la fonction de résolution pour votre projet.](/help/edge/wysiwyg-authoring/repoless.md)

## Cas d’utilisation {#use-case}

Ce document suppose que vous avez déjà créé une structure de site localisée de base pour votre projet. Elle utilise, à titre d’exemple, la structure suivante pour la marque wknd présente en Suisse et en Allemagne.

```text
/content/wknd
/content/wknd/language-masters
/content/wknd/language-masters/en
/content/wknd/language-masters/de
/content/wknd/language-masters/fr
/content/wknd/language-masters/it
/content/wknd/ch
/content/wknd/ch/de
/content/wknd/ch/fr
/content/wknd/ch/it
/content/wknd/ch/en
/content/wknd/de
/content/wknd/de/de
/content/wknd/de/en
```

Le contenu de `language-masters` est la source des Live Copies pour les sites localisés : Allemagne (`de`) et Suisse (`ch`). L’objectif de ce document est de créer des sites Edge Delivery Services qui utilisent tous la même base de code pour chaque site localisé.

## Configuration {#configuration}

Il existe plusieurs étapes pour configurer le cas d’utilisation des réponses MSM.

1. [Mettez à jour les configurations AEM site.](#update-aem-configurations)
1. [Créez de nouveaux sites de Edge Delivery Services pour vos pages localisées.](#create-edge-sites)
1. [Mettez à jour la configuration du cloud dans AEM pour vos sites localisés.](#update-cloud-configurations)

### Mise à jour AEM configurations du site {#update-aem-configurations}

[Les configurations](/help/implementing/developing/introduction/configurations.md) peuvent être considérées comme des espaces de travail qui peuvent être utilisés pour rassembler des groupes de paramètres et leur contenu associé à des fins d’organisation. Lorsque vous créez un site dans AEM, une configuration lui est automatiquement créée.

Vous souhaitez généralement partager un certain contenu entre les sites, par exemple :

* Modèles créés à partir du contenu dans le plan directeur
* Modèles de fragment de contenu, persistant, requêtes, etc.

Vous pouvez créer des configurations supplémentaires pour faciliter ce partage. Pour le cas d’utilisation Wknd, des configurations sont nécessaires pour les chemins suivants.

```text
/content/wknd
/content/wknd/ch
/content/wknd/de
```

En d’autres termes, vous disposez d’une configuration pour la racine du contenu de la marque wknd (`/content/wknd`) utilisée par les plans directeurs et d’une configuration utilisée par chaque site localisé (Suisse et Allemagne).

1. Connectez-vous à votre instance de création AEM.
1. Accédez au **navigateur de configuration** en accédant à **Outils** -> **Général** -> **Navigateur de configuration**.
1. Sélectionnez la configuration qui a été automatiquement créée pour votre projet (dans ce cas, wknd), puis appuyez ou cliquez sur **Créer** dans la barre d’outils.
1. Dans la boîte de dialogue **Créer une configuration**, fournissez un **nom** descriptif pour votre site localisé (tel que `Switzerland`) et pour le **titre**, utilisez le même titre que la taille localisée (dans ce cas `ch`).
1. Sélectionnez la fonction **Configuration du cloud** et toutes les fonctions supplémentaires dont vous aurez besoin pour votre projet, telles que les **modèles modifiables**.
1. Appuyez ou cliquez sur **Créer**.

Créez des configurations pour chaque site localisé dont vous avez besoin. Dans le cas de wknd, vous devez également créer une configuration pour `de` avec la configuration `ch`.

Une fois les configurations créées, vous devez vous assurer que les sites localisés les utilisent.

1. Connectez-vous à votre instance de création AEM.
1. Accédez à la **console Sites** en accédant à **Navigation** -> **Sites**.
1. Sélectionnez le site localisé tel que `Switzerland`.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre des propriétés de page, sélectionnez l’onglet **Avancé** et sous l’en-tête **Configuration**, désélectionnez l’option **Hérité de /content/wknd**, où `wknd` est la racine du site.
1. Dans le champ **Configuration cloud** , utilisez l’explorateur de chemins d’accès pour sélectionner la configuration que vous avez créée pour votre site localisé, telle que `Switzerland` sous `/conf/wknd/ch`.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

Affectez les configurations respectives aux sites localisés supplémentaires. Dans le cas de wknd, vous devez également attribuer la configuration `/conf/wknd/de` au site de l’Allemagne.

### Création de sites Edge Delivery Services pour vos pages localisées {#create-edge-sites}

Pour connecter d’autres sites à des Edge Delivery Services pour une configuration de site multirégionale et multilingue, vous devez configurer un nouveau site aem.live pour chacun de vos sites MSM AEM. Il existe une relation 1:1 entre AEM sites MSM et aem.live sites avec un référentiel Git partagé et une base de code.

Pour cet exemple, nous allons créer le site `wknd-ch` pour la présence suisse de wknd, dont le contenu localisé se trouve sous le chemin d’AEM `/content/wknd/ch`.

1. Récupérez votre jeton d’authentification et le compte technique de votre programme.
   * Consultez le document **Réutilisation du code sur plusieurs sites** pour plus d’informations sur la [obtention de votre jeton d’accès](/help/edge/wysiwyg-authoring/repoless.md#access-token) et le [compte technique](/help/edge/wysiwyg-authoring/repoless.md#access-control) de votre programme.
1. Créez un site en effectuant l’appel suivant au service de configuration. Veuillez tenir compte des points suivants :
   * Le nom du projet dans l’URL du POST doit correspondre au nouveau nom du site que vous créez. Dans cet exemple, il s’agit de `wknd-ch`.
   * La configuration `code` doit être la même que celle utilisée pour la création initiale du projet.
   * Le `content` > `source` > `url` doit être adapté au nom du nouveau site que vous créez. Dans cet exemple, il s’agit de `wknd-ch`.
   * En d’autres termes, le nom du site dans l’URL du POST et `content` > `source` > `url` doivent être identiques.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "code": {
           "owner": "<your-github-org>",
           "repo": "wknd",
           "source": {
               "type": "github",
               "url": "https://github.com/<your-github-org>/wknd"
           }
       },
       "content": {
           "source": {
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-ch/main",
               "type": "markup",
               "suffix": ".html"
           }
       },
       "access": {
           "admin": {
               "role": {
                   "admin": [
                       "*@adobe.com"
                   ],
                   "publish": [
                       "<tech-account-id>@techacct.adobe.com"
                   ]
               },
               "requireAuth": "auto"
           }
       }
   }'
   ```

1. Ajoutez le mappage de chemin pour votre nouveau site en effectuant l’appel suivant au service de configuration.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/ch/:/"
           ],
           "includes": [
               "/content/wknd/ch/"
           ]
       }
   }'
   ```

1. Vérifiez que la configuration publique de votre nouveau site fonctionne en appelant `https://main--wknd-ch--<your-github-org>.aem.page/config.json` et en vérifiant le contenu du JSON renvoyé.

Répétez les étapes pour créer d’autres sites localisés. Dans le cas de wknd, vous devez également créer un site `wknd-de` pour la présence allemande.

### Mise à jour des configurations du cloud dans AEM pour vos pages localisées {#update-cloud-configurations}

Vos pages dans AEM doivent être configurées pour utiliser les nouveaux sites Edge Delivery que vous avez créés dans la section précédente pour votre présence localisée. Dans cet exemple, le contenu situé sous `/content/wknd/ch` doit savoir utiliser le site `wknd-ch` que vous avez créé. De même, le contenu situé sous `/content/wknd/de` doit utiliser le site `wknd-de`.

1. Connectez-vous à l’instance d’auteur AEM et accédez à **Outils** -> **Cloud Service** -> **Configuration de Edge Delivery Services**.
1. Sélectionnez la configuration automatiquement créée pour votre projet, puis le dossier créé pour la page localisée. Dans ce cas, ce serait la Suisse (`ch`).
1. Appuyez ou cliquez sur **Créer** > **Configuration** dans la barre d’outils.
1. Dans la fenêtre **Configuration de Edge Delivery Services** :
   * Fournissez votre organisation GitHub dans le champ **Organization**.
   * Remplacez le nom du site par celui que vous avez créé dans la section précédente. Dans ce cas, il s’agira de `wknd-ch`.
   * Remplacez le type de projet par **aem.live with repoless config setup**.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

## Vérification de votre configuration {#verify}

Maintenant que vous avez apporté toutes les modifications de configuration nécessaires, vérifiez que tout fonctionne comme prévu.

1. Connectez-vous à votre instance de création AEM.
1. Accédez à la **console Sites** en accédant à **Navigation** -> **Sites**.
1. Sélectionnez le site localisé tel que `Switzerland`.
1. Appuyez ou cliquez sur **Modifier** dans la barre d’outils.
1. Assurez-vous que la page s’affiche correctement dans l’éditeur universel et utilise le même code que la racine de votre site.
1. Apportez une modification à la page et republiez-la.
1. Visitez votre nouveau site de Edge Delivery Services pour cette page localisée à l’adresse `https://main--wknd-ch--<your-github-org>.aem.page`.

Si vous voyez les modifications que vous avez apportées, votre configuration MSM fonctionne correctement.

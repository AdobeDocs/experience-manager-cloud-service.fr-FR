---
title: Gestion de plusieurs sites sans référentiel
description: Découvrez les recommandations de bonnes pratiques relatives à la configuration d’un projet de manière réactive avec des sites localisés qui utilisent une seule base de code, chacune diffusée par Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: f6b861ed-18e4-4c81-92d2-49fadfe4669a
source-git-commit: c9d0d3cd7e18b56db36a379b63f8fb48e18a40db
workflow-type: tm+mt
source-wordcount: '1260'
ht-degree: 2%

---

# Gestion de plusieurs sites sans référentiel {#repoless-msm}

Découvrez les recommandations de bonnes pratiques relatives à la configuration d’un projet de manière réactive avec des sites localisés qui utilisent une seule base de code, chacune diffusée par Edge Delivery Services.

## Vue d’ensemble {#overview}

[Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) et ses fonctionnalités Live Copy vous permettent d’utiliser le même contenu de site à plusieurs emplacements, tout en autorisant des variations. Vous pouvez créer du contenu une seule fois et créer des Live Copies. MSM conserve les relations en direct entre votre contenu source et ses Live Copies afin que lorsque vous modifiez le contenu source, la source et les Live Copies puissent être synchronisées.

Vous pouvez utiliser MSM pour créer une structure de contenu complète pour votre marque dans les paramètres régionaux et les langues, en créant le contenu de manière centralisée. Vos sites localisés peuvent ensuite être diffusés par Edge Delivery Services, à l’aide d’une base de code centrale.

## Conditions requises {#requirements}

Pour configurer MSM dans un cas d’utilisation sans réponse, vous devez d’abord effectuer les tâches suivantes :

* Ce document suppose que vous avez déjà créé un site pour votre projet à partir du guide de prise en main [Developer Getting Started Guide for WYSIWYG Authoring with Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md).
* Vous devez avoir déjà [activé la fonction Réponses pour votre projet](/help/edge/wysiwyg-authoring/repoless.md).

## Cas d’utilisation {#use-case}

Ce document suppose que vous avez déjà créé une structure de site localisée de base pour votre projet. Elle utilise la structure suivante pour la marque wknd présente en Suisse et en Allemagne à titre d’exemple.

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

Le contenu en `language-masters` est la source des Live Copies pour les sites localisés : Allemagne (`de`) et Suisse (`ch`). L’objectif de ce document est de créer des sites Edge Delivery Services qui utilisent tous la même base de code pour chaque site localisé.

## Configuration {#configuration}

La configuration du cas d’utilisation des réponses du MSM comporte plusieurs étapes.

1. [Mettez à jour les configurations de site AEM](#update-aem-configurations).
1. [Création de sites Edge Delivery Services pour vos pages localisées](#create-edge-sites).
1. [Mettez à jour la configuration cloud dans AEM pour vos sites localisés](#update-cloud-configurations).

### Mettre à jour les configurations de site AEM {#update-aem-configurations}

Les [configurations](/help/implementing/developing/introduction/configurations.md) peuvent être considérées comme des espaces de travail qui peuvent être utilisés pour rassembler des groupes de paramètres et leur contenu associé à des fins d’organisation. Lorsque vous créez un site dans AEM, une configuration est automatiquement créée pour celui-ci.

En règle générale, vous souhaitez partager certains contenus entre des sites, tels que :

* Modèles créés à partir du contenu du plan directeur
* Modèles de fragment de contenu, persistants, requêtes, etc.

Vous pouvez créer des configurations supplémentaires pour faciliter ce partage. Pour le cas d’utilisation de wknd, des configurations sont nécessaires pour les chemins d’accès suivants.

```text
/content/wknd
/content/wknd/ch
/content/wknd/de
```

En d’autres termes, vous disposez d’une configuration pour la racine du contenu de la marque wknd (`/content/wknd`) utilisée par les plans directeurs et d’une configuration utilisée par chaque site localisé (Suisse et Allemagne).

1. Connectez-vous à votre instance de création AEM.
1. Accédez au **navigateur de configuration** en accédant à **Outils** -> **Général** -> **navigateur de configuration**.
1. Sélectionnez la configuration qui a été automatiquement créée pour votre projet (dans ce cas wknd), puis appuyez ou cliquez sur **Créer** dans la barre d’outils.
1. Dans la boîte de dialogue **Créer une configuration**, fournissez un **Nom** descriptif pour votre site localisé (tel que `Switzerland`) et pour le **Titre** utilisez le même titre que la taille localisée (dans ce cas `ch`).
1. Sélectionnez la fonction **Configuration du cloud** et toute fonctionnalité supplémentaire dont vous pourriez avoir besoin pour votre projet, telle que **Modèles modifiables**.
1. Appuyez ou cliquez sur **Créer**.

Créez des configurations pour chaque site localisé dont vous avez besoin. Dans le cas de wknd, vous devez créer une configuration pour `de` ainsi que la configuration `ch` .

Une fois les configurations créées, vous devez vous assurer que les sites localisés les utilisent.

1. Connectez-vous à votre instance de création AEM.
1. Accédez à la **console Sites** en accédant à **Navigation** -> **Sites**.
1. Sélectionnez le site localisé, tel que `Switzerland`.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre des propriétés de la page, sélectionnez l’onglet **Avancé** et, sous l’en-tête **Configuration**, désélectionnez l’option **Hérité de /content/wknd**, où `wknd` correspond à la racine du site.
1. Dans le champ **Configuration du cloud**, utilisez l’explorateur de chemins d’accès pour sélectionner la configuration que vous avez créée pour votre site localisé, telle que `Switzerland` sous `/conf/wknd/ch`.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

Attribuez les configurations respectives aux sites localisés supplémentaires. Dans le cas de wknd, vous devez également attribuer la configuration `/conf/wknd/de` au site d’Allemagne .

### Création de nouveaux sites Edge Delivery Services pour vos pages localisées {#create-edge-sites}

Pour connecter d’autres sites à Edge Delivery Services en vue d’une configuration de site multi-région et multilingue, vous devez configurer un nouveau site aem.live pour chacun de vos sites MSM AEM. Il existe une relation 1:1 entre les sites AEM MSM et les sites aem.live avec un référentiel Git et une base de code partagés.

Pour cet exemple, nous allons créer le `wknd-ch` de site pour la présence suisse de wknd, dont le contenu localisé se trouve sous le chemin d’accès AEM `/content/wknd/ch`.

1. Récupérez votre jeton d’authentification et le compte technique de votre programme.
   * Veuillez consulter le document **Réutilisation de code sur plusieurs sites** pour plus d’informations sur la manière d’[obtenir votre jeton d’accès](/help/edge/wysiwyg-authoring/repoless.md#access-token) et le [compte technique](/help/edge/wysiwyg-authoring/repoless.md#access-control) pour votre programme.
1. Créez un site en effectuant l’appel suivant au service de configuration . Veuillez tenir compte des points suivants :
   * Le nom du projet dans l’URL POST doit correspondre au nouveau nom du site que vous êtes en train de créer. Dans cet exemple, il s’agit de `wknd-ch`.
   * La configuration `code` doit être identique à celle que vous avez utilisée lors de la création initiale du projet.
   * Le `content` > `source` > `url` doit être adapté au nom du nouveau site que vous êtes en train de créer. Dans cet exemple, il s’agit de `wknd-ch`.
   * En d’autres termes, le nom du site dans l’URL POST et le `content` > `source` > `url` doivent être identiques.
   * Adaptez le bloc `admin` pour définir les utilisateurs et utilisatrices qui doivent disposer d’un accès administratif complet au site.
      * Il s’agit d’un tableau d’adresses e-mail.
      * Le caractère générique `*` peut être utilisé.
      * Consultez le document [Configuration de l’authentification pour les auteurs](https://www.aem.live/docs/authentication-setup-authoring#default-roles) pour plus d’informations.

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
                       "<email>@<domain>.<tld>"
                   ],
                   "config_admin": [
                       "<tech-account-id>@techacct.adobe.com"
                   ]
               },
               "requireAuth": "auto"
           }
       }
   }'
   ```

1. Ajoutez le mappage de chemin d’accès à votre nouveau site en effectuant l’appel suivant au service de configuration .

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

1. Vérifiez que la configuration publique de votre nouveau site fonctionne en appelant `https://main--wknd-ch--<your-github-org>.aem.page/config.json` et en vérifiant le contenu du fichier JSON renvoyé.

Répétez les étapes pour créer d’autres sites localisés. Dans le cas de wknd, vous devez également créer un site `wknd-de` pour la présence allemande.

### Mettre à jour les configurations cloud dans AEM pour vos pages localisées {#update-cloud-configurations}

Vos pages dans AEM doivent être configurées de manière à utiliser les nouveaux sites Edge Delivery que vous avez créés dans la section précédente pour votre présence localisée. Dans cet exemple, le contenu sous `/content/wknd/ch` doit savoir comment utiliser le site `wknd-ch` que vous avez créé. De même, le contenu sous `/content/wknd/de` doit utiliser le site `wknd-de`.

1. Connectez-vous à l’instance d’auteur AEM et accédez à **Outils** -> **Services cloud** -> **Configuration Edge Delivery Services**.
1. Sélectionnez la configuration qui a été automatiquement créée pour votre projet, puis le dossier qui a été créé pour la page localisée. Dans ce cas, il s&#39;agirait de la Suisse (`ch`).
1. Appuyez ou cliquez sur **Créer** > **Configuration** dans la barre d’outils.
1. Dans la fenêtre **Configuration de Edge Delivery Services** :
   * Indiquez votre organisation GitHub dans le champ **Organisation**.
   * Remplacez le nom du site par le nom du site que vous avez créé dans la section précédente. Dans ce cas-ci, ce serait `wknd-ch`.
   * Remplacez le type de projet par **aem.live avec la configuration repoless**.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

## Vérification de votre configuration {#verify}

Maintenant que vous avez effectué toutes les modifications de configuration nécessaires, vérifiez que tout fonctionne comme prévu.

1. Connectez-vous à votre instance de création AEM.
1. Accédez à la **console Sites** en accédant à **Navigation** -> **Sites**.
1. Sélectionnez le site localisé, tel que `Switzerland`.
1. Appuyez ou cliquez sur **Modifier** dans la barre d’outils.
1. Assurez-vous que la page s’affiche correctement dans l’éditeur universel et utilise le même code que la racine de votre site.
1. Apportez une modification à la page et republiez-la.
1. Visitez votre nouveau site Edge Delivery Services pour cette page localisée à l’adresse `https://main--wknd-ch--<your-github-org>.aem.page`.

Si les modifications que vous avez apportées s’affichent, votre configuration MSM fonctionne correctement.

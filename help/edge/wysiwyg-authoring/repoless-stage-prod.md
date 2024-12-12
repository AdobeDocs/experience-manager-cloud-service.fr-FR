---
title: Réplication des environnements d’évaluation et de production
description: Découvrez comment configurer des sites distincts pour vos environnements d’évaluation et de production en exploitant une seule base de code de manière réactive.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 709d0661286d023c5cec51be2c51a1123ef7deb6
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 1%

---


# Réplication des environnements d’évaluation et de production {#repoless-stage-prod}

Découvrez comment configurer des sites distincts pour vos environnements d’évaluation et de production en exploitant une seule base de code de manière réactive.

## Vue d’ensemble {#overview}

Vous pouvez configurer un site pour votre environnement de production distinct de votre environnement d’évaluation. La configuration d’un second site pour une configuration d’évaluation et de production distincte est similaire à la configuration [requise pour la gestion de plusieurs sites.](/help/edge/wysiwyg-authoring/repoless-msm.md) En fait, il peut être combiné avec des structures de site MSM si nécessaire.

Ce document utilise l’exemple type d’environnements d’évaluation et de production distincts. Vous pouvez créer des environnements distincts pour tous les environnements que vous souhaitez.

## Configuration {#configuration}

Ce document décrit comment configurer un site de production distinct pour votre projet à l’aide de la même base de code. Les hypothèses suivantes sont faites.

* Le site d’évaluation est déjà configuré et vous souhaitez maintenant créer une configuration pour le site de production.
* La structure de contenu dans AEM création est similaire.
* Les mêmes mappages de chemin seront utilisés pour l’évaluation et la production.

Dans cet exemple, nous supposons qu’un site de production a déjà été créé pour le projet appelé wknd dont le référentiel GitHub est également appelé wknd.

La configuration d’un site de production distinct comporte deux étapes.

1. [Créez de nouveaux sites Edge Delivery Services pour votre environnement de production.](#create-edge-site)
1. [Mettez à jour la configuration du cloud dans AEM pour votre site de production.](#update-cloud-configuration)

### Création de sites Edge Delivery Services pour votre environnement de production {#create-edge-site}

1. Récupérez votre jeton d’authentification et le compte technique de votre programme.
   * Consultez le document **Réutilisation du code sur plusieurs sites** pour plus d’informations sur la [obtention de votre jeton d’accès](/help/edge/wysiwyg-authoring/repoless.md#access-token) et le [compte technique](/help/edge/wysiwyg-authoring/repoless.md#access-control) de votre programme.
1. Créez un site en effectuant l’appel suivant au service de configuration. Veuillez tenir compte des points suivants :
   * Le nom du projet dans l’URL du POST doit correspondre au nouveau nom du site que vous créez. Dans cet exemple, il s’agit de `wknd-prod`.
   * La configuration `code` doit être la même que celle utilisée pour la création initiale du projet.
   * Le `content` > `source` > `url` doit être adapté au nom du nouveau site que vous créez. Dans cet exemple, il s’agit de `wknd-prod`.
   * En d’autres termes, le nom du site dans l’URL du POST et `content` > `source` > `url` doivent être identiques.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
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
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-prod/main",
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
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/:/"
           ],
           "includes": [
               "/content/wknd/"
           ]
       }
   }'
   ```

Vérifiez que la configuration publique de votre nouveau site fonctionne en appelant `https://main--wknd-prod--<your-github-org>.aem.page/config.json` et en vérifiant le contenu du JSON renvoyé.

### Mise à jour des configurations du cloud dans AEM pour votre site de production {#update-cloud-configuration}

Votre AEM de production doit être configurée pour utiliser les nouveaux sites Edge Delivery que vous avez créés dans la section précédente pour un site de production dédié. Dans cet exemple, le contenu situé sous `/content/wknd` de votre environnement de production doit savoir comment utiliser le site `wknd-prod` que vous avez créé.

1. Connectez-vous à l’instance de production AEM et accédez à **Outils** -> **Cloud Service** -> **Configuration de Edge Delivery Services**.
1. Sélectionnez la configuration qui a été automatiquement créée pour votre projet.
1. Appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre **Configuration de Edge Delivery Services** :
   * Fournissez votre organisation GitHub dans le champ **Organization**.
   * Remplacez le nom du site par celui que vous avez créé dans la section précédente. Dans ce cas, il s’agira de `wknd-prod`.
   * Remplacez le type de projet par **aem.live with repoless config setup**.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

## Vérification de votre configuration {#verify}

Maintenant que vous avez apporté toutes les modifications de configuration nécessaires, vérifiez que tout fonctionne comme prévu.

1. Connectez-vous à votre instance de création de production AEM.
1. Accédez à la **console Sites** en accédant à **Navigation** -> **Sites**.
1. Sélectionnez une page de votre site.
1. Appuyez ou cliquez sur **Modifier** dans la barre d’outils.
1. Assurez-vous que la page s’affiche correctement dans l’éditeur universel et utilise le même code que la racine de votre site.
1. Apportez une modification à la page et republiez-la.
1. Visitez votre nouveau site de Edge Delivery Services pour cette page à l’adresse `https://main--wknd-prod--<your-github-org>.aem.page`.

Si vous voyez les modifications que vous avez apportées, votre configuration de site de production distincte fonctionne correctement.

---
title: Réutilisation du code sur plusieurs sites
description: Si vous disposez de nombreux sites similaires qui se comportent généralement de la même manière, mais présentent un contenu différent, découvrez comment partager du code sur plusieurs sites dans un modèle de réplication.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: e25e21984ebadde7076d95c6051b8bfca5b2ce03
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---


# Réutilisation du code sur plusieurs sites {#repoless}

Si vous disposez de nombreux sites similaires qui se comportent généralement de la même manière, mais présentent un contenu différent, découvrez comment partager du code sur plusieurs sites dans un modèle de réplication.

## Un code base pour plusieurs sites {#one-codebase}

Par défaut, AEM est étroitement lié à votre référentiel de code, qui répond à la plupart des cas d’utilisation. Cependant, vous pouvez avoir plusieurs sites dont le contenu diffère le plus souvent, mais qui peuvent utiliser la même base de code.

Plutôt que de créer plusieurs référentiels GitHub et d’exécuter chaque site à partir d’un référentiel GitHub dédié tout en les synchronisant, AEM prend en charge l’exécution de plusieurs sites à partir de la même base de code.

Cette configuration simplifiée, qui élimine la nécessité de la réplication du code, est également connue sous le nom de [&quot;repoless&quot;,](https://www.aem.live/docs/repoless), car tous les sites, à l’exception de votre premier site, n’ont pas besoin d’un référentiel GitHub qui leur soit propre.

Si votre projet nécessite la flexibilité de réutilisation du code sur plusieurs sites, vous pouvez activer la fonctionnalité.

Quel que soit le nombre de sites que vous souhaitez créer en fin de compte de manière récurrente, vous devez créer votre premier site, qui sert de site de base. Ce document explique comment créer votre premier site à des fins de réutilisation.

## Conditions préalables {#prerequisites}

Pour tirer parti de cette fonctionnalité, vérifiez que vous avez effectué les opérations suivantes.

* Votre site est déjà entièrement configuré en suivant le document [Guide de prise en main du développeur pour la création avec des Edge Delivery Services dans WYSIWYG.](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)
* Vous exécutez AEM as a Cloud Service 2024.08 au minimum.

Vous devrez également demander à Adobe de configurer deux éléments pour vous. Contactez l’Adobe via votre canal de Slack ou soulevez un problème de support pour effectuer ces requêtes.

* Le [service de configuration aem.live](https://www.aem.live/docs/config-service-setup#prerequisites) est actif pour votre environnement et vous êtes configuré en tant qu’administrateur.
* La fonctionnalité de répolération doit être activée par Adobe pour votre programme.

## Fonction Activer les réponses {#activate}

Plusieurs étapes permettent d’activer la fonctionnalité de réplication pour votre projet.

1. [Récupération du jeton d’accès](#access-token)
1. [Configuration du service de configuration](#config-service)
1. [Définir le contrôle d’accès](#access-control)
1. [Mise à jour de la configuration AEM](#update-aem)
1. [Authentification du site](#authenticate-site)

Ces étapes utilisent le site `https://wknd.site` comme exemple. Remplacez les vôtres de manière appropriée.

### Récupération du jeton d’accès {#access-token}

Vous aurez d’abord besoin d’un jeton d’accès pour utiliser le service de configuration et le configurer pour le cas d’utilisation de la réplication.

1. Accédez à `https://admin.hlx.page/login` et utilisez l’adresse `login_adobe` pour vous connecter avec le fournisseur d’identité d’Adobe.
1. Vous serez transféré à `https://admin.hlx.page/profile`.
1. En utilisant les outils de développement de votre navigateur, copiez la valeur du cookie de jeton Web JSON `x-auth-token` défini par la page `admin.hlx.page`.

Une fois que vous disposez de votre jeton d’accès, il peut être transmis dans l’en-tête des requêtes cURL au format suivant.

```text
--header 'x-auth-token: <your-token>'
```

### Configuration de votre service de configuration {#config-service}

Comme mentionné dans les [ conditions préalables, ](#prerequisites) le service de configuration doit être activé pour votre environnement. Vous pouvez vérifier la configuration de votre service de configuration à l’aide de cette commande cURL.

```text
curl  --location 'https://admin.hlx.page/config/<your-github-org>.json' \
--header 'x-auth-token: <your-token>'
```

Si le service de configuration est configuré correctement, JSON similaire à ce qui suit est renvoyé.

```json
{
  "title": "<your-github-org>",
  "description": "Your GitHub Org",
  "lastModified": "2024-11-14T12:14:04.230Z",
  "created": "2024-11-14T12:13:37.032Z",
  "version": 1,
  "users": [
    {
      "email": "justthisguyyouknow@adobe.com",
      "roles": [
        "admin"
      ],
      "id": "<your-id>"
    }
  ]
}
```

Contactez Adobe via votre canal de Slack de projet ou soulevez un problème de prise en charge si votre service de configuration n’est pas activé. Une fois que vous disposez de votre jeton et que vous avez vérifié que le service de configuration est activé, vous pouvez continuer la configuration.

1. Vérifiez que votre source de contenu est correctement configurée.

   ```text
   curl --request GET \
   --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>.json \
   --header 'x-auth-token: <your-token>'
   ```

1. Ajoutez un mappage de chemin à la configuration publique.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```

Une fois la configuration publique créée, vous pouvez y accéder via une URL similaire à `https://main--<your-aem-project>--<your-github-org>.aem.page/config.json` afin de la vérifier.

### Définir le contrôle d’accès {#access-control}

Pour configurer le contrôle d’accès, vous devez fournir le compte technique.

1. Créez une page à la racine de votre site et sélectionnez le modèle [**Configuration**.](/help/edge/wysiwyg-authoring/tabular-data.md#other)
   * Vous pouvez laisser la configuration vide avec uniquement les colonnes `key` et `value` prédéfinies. Il vous suffit de le créer.
1. Créez un mappage dans la configuration publique à la configuration du site à l’aide d’une commande cURL similaire à ce qui suit.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/",
               "/content/<your-site-content>/configuration:/.helix/config.json"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```
1. Vérifiez que la configuration publique a été définie et qu’elle est disponible avec une commande cURL similaire à celle-ci.

   ```text
   curl 'https://main--<your-aem-project>--<your-github-org>.aem.live/config.json'
   ```
1. Dans votre navigateur, vous pouvez désormais récupérer le compte technique en réponse au lien suivant.

   ```text
   https://author-p<programID>-e<envionmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/<your-aem-project>/main/.helix/config.json
   ```

La réponse sera similaire à ce qui suit.

```json
{
  "total": 1,
  "offset": 0,
  "limit": 1,
  "data": [
    {
      "key": "admin.role.publish",
      "value": "<tech-account-id>@techacct.adobe.com"
    }
  ],
  ":type": "sheet"
}
```

1. Définissez le compte technique dans votre configuration avec une commande cURL similaire à ce qui suit.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "admin": {
           "role": {
               "admin": [
                   "*@adobe.com"
               ],
               "config_admin": [
                   "<tech-account-id>@techacct.adobe.com"
               ]
           },
           "requireAuth": "auto"
       }
   }'
   ```

Puisque vous utilisez maintenant le service de configuration, vous pouvez supprimer `fstab.yaml` et `paths.json` de votre référentiel Git.

>[!NOTE]
>
>En utilisant le service de configuration et en exposant le mappage de chemin d’accès via `config.json`, le fichier `path.json` est ignoré.

Une fois que AEM est configuré pour une utilisation de réutilisation, vous devez utiliser le service de configuration et fournir un `config.json` valide avec le mappage des chemins.

### Mise à jour de la configuration AEM {#update-aem}

Vous êtes maintenant prêt à apporter les modifications nécessaires à vos Edge Delivery Services dans AEM.

1. Connectez-vous à l’instance d’auteur AEM et accédez à **Outils** -> **Cloud Service** -> **Configuration de Edge Delivery Services** et sélectionnez la configuration qui a été automatiquement créée pour votre site, puis appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre **Configuration de Edge Delivery Services**, remplacez le type de projet par **aem.live with repoless config setup** et appuyez ou cliquez sur **Enregistrer et fermer**.
   ![Configuration de Edge Delivery Services](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Revenez à votre site à l’aide d’Universal Editor et assurez-vous qu’il s’affiche toujours correctement.
1. Modifiez une partie de votre contenu et republiez-le.
1. Visitez votre site publié sur `https://main--<your-aem-project>--<your-github-org>.aem.page/` et vérifiez que les modifications sont correctement reflétées.

Votre projet est maintenant configuré pour être réutilisé.

## Étapes suivantes {#next-steps}

Maintenant que votre site de base est configuré pour l’utilisation des repolis, vous pouvez créer d’autres sites qui exploitent la même base de code. Reportez-vous à la documentation suivante en fonction de votre cas d’utilisation.

* [Réplication de la gestion multisite](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Réplication des environnements d’évaluation et de production](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)

## Résolution des problèmes {#troubleshooting}

Le problème le plus courant rencontré après la configuration du cas d’utilisation des répolations est que les pages de l’éditeur universel ne s’affichent plus ou que vous recevez une page blanche ou un message d’erreur AEM as a Cloud Service générique. Dans ce cas :

* Affichez la source de la page rendue.
   * Existe-t-il un rendu (en-tête d’HTML correct avec les fichiers `scripts.js`, `aem.js` et JSON liés à l’éditeur) ?
* Recherchez les exceptions dans l’AEM `error.log` de l’instance d’auteur.
   * Le problème le plus courant est que le composant de page échoue avec des erreurs 404.
   * `config.json or paths.json` ne peut pas être chargé
   * `component-definition.json` etc. ne peut pas être chargé

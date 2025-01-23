---
title: Réutilisation du code sur plusieurs sites
description: Si vous disposez de nombreux sites similaires qui ressemblent et se comportent globalement de la même manière, mais avec un contenu différent, découvrez comment partager du code sur plusieurs sites dans un modèle de réponse.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
source-git-commit: e7f7c169e7394536fc2968ecf1418cd095177679
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 2%

---

# Réutilisation du code sur plusieurs sites {#repoless}

Si vous disposez de nombreux sites similaires qui ressemblent et se comportent globalement de la même manière, mais avec un contenu différent, découvrez comment partager du code sur plusieurs sites dans un modèle de réponse.

## Une base de code pour plusieurs sites {#one-codebase}

Par défaut, AEM est étroitement lié à votre référentiel de code, qui répond à la majorité des cas d’utilisation. Cependant, vous pouvez avoir plusieurs sites qui diffèrent principalement par leur contenu, mais qui peuvent utiliser la même base de code.

Au lieu de créer plusieurs référentiels GitHub et d’exécuter chaque site à partir d’un référentiel GitHub dédié tout en les maintenant synchronisés, AEM prend en charge l’exécution de plusieurs sites à partir de la même base de code.

Cette configuration simplifiée, qui élimine la nécessité de la réplication du code, est également appelée [ « réponses » ](https://www.aem.live/docs/repoless), car tous les sites, à l’exception du premier, n’ont pas besoin de leur propre référentiel GitHub.

Si votre projet nécessite la flexibilité réactive de la réutilisation du code sur plusieurs sites, vous pouvez activer la fonctionnalité.

Quel que soit le nombre de sites que vous souhaitez créer en fin de compte sans réponse, vous devez créer votre premier site, qui sert de site de base. Ce document explique comment créer votre premier site pour une utilisation sans réponse.

## Conditions préalables {#prerequisites}

Pour tirer parti de cette fonctionnalité, vérifiez que vous avez effectué les opérations suivantes.

* Votre site est déjà entièrement configuré en suivant le document [Guide de prise en main pour le développeur pour la création WYSIWYG avec des Edge Delivery Services.](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)
* Vous exécutez AEM as a Cloud Service 2024.08 au minimum.

Vous devrez également demander à l’Adobe de configurer les éléments suivants pour vous. Contactez par le biais de votre canal de Slack ou soulevez un problème d’assistance pour demander l’Adobe d’effectuer ces modifications :

* Demandez l’activation du [service de configuration aem.live](https://www.aem.live/docs/config-service-setup#prerequisites) pour votre environnement et indiquez que vous êtes configuré en tant qu’administrateur.
* Demandez à d’activer la fonction Repoless pour votre programme par Adobe.
* Demandez à Adobe de créer l’organisation pour vous.

## Activer la fonction Réponses {#activate}

Il existe plusieurs étapes pour activer la fonctionnalité de réponses pour votre projet.

1. [Récupérer le jeton d’accès](#access-token)
1. [Configurer le service de configuration](#config-service)
1. [Ajouter la configuration du site et le compte technique](#access-control)
1. [Mise à jour de la configuration AEM](#update-aem)
1. [Authentifier le site](#authenticate-site)

Ces étapes utilisent l’`https://wknd.site` de site comme exemple. Remplacez le vôtre de manière appropriée.

### Récupérer le jeton d’accès {#access-token}

Vous aurez d’abord besoin d’un jeton d’accès pour utiliser le service de configuration et le configurer pour le cas d’utilisation des réponses.

1. Accédez à `https://admin.hlx.page/login` et utilisez l’adresse `login_adobe` pour vous connecter avec le fournisseur d’identités d’Adobe.
1. Vous serez transféré à `https://admin.hlx.page/profile`.
1. À l’aide des outils de développement de votre navigateur, copiez la valeur du `x-auth-token` à partir du cookie de jeton web JSON défini par la page `admin.hlx.page`.

Une fois que vous disposez de votre jeton d’accès, il peut être transmis dans l’en-tête des requêtes cURL au format suivant.

```text
--header 'x-auth-token: <your-token>'
```

### Ajout d’un mappage de chemin pour la configuration du site et définition du compte technique {#access-control}

Vous devez créer une configuration de site et l’ajouter à votre mappage de chemin d’accès.

1. Créez une page à la racine de votre site et choisissez le modèle [**Configuration**. ](/help/edge/wysiwyg-authoring/tabular-data.md#other)
   * Vous pouvez laisser la configuration vide avec uniquement les colonnes `key` et `value` prédéfinies. Il suffit de le créer.
1. Créez un mappage dans la configuration publique à la configuration du site à l’aide d’une commande cURL similaire à la suivante.

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
1. Vérifiez que la configuration publique a été définie et qu’elle est disponible avec une commande cURL similaire à la suivante.

   ```text
   curl 'https://main--<your-aem-project>--<your-github-org>.aem.live/config.json'
   ```

Une fois la configuration du site mappée, vous pouvez configurer le contrôle d’accès en définissant votre compte technique afin qu’il dispose des privilèges de publication.

1. Dans votre navigateur, récupérez le compte technique dans la réponse du lien suivant.

   ```text
   https://author-p<programID>-e<envionmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/<your-aem-project>/main/.helix/config.json
   ```

1. La réponse sera similaire à ce qui suit.

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

1. Définissez le compte technique dans votre configuration avec une commande cURL similaire à la suivante.

   * Adaptez le bloc `admin` pour définir les utilisateurs et utilisatrices qui doivent disposer d’un accès administratif complet au site.
      * Il s’agit d’un tableau d’adresses e-mail.
      * Le caractère générique `*` peut être utilisé.
      * Consultez le document [Configuration de l’authentification pour les auteurs](https://www.aem.live/docs/authentication-setup-authoring#default-roles) pour plus d’informations.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
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
   }'
   ```

Puisque vous utilisez maintenant le service de configuration, vous pouvez supprimer `fstab.yaml` et `paths.json` de votre référentiel Git.

>[!NOTE]
>
>En utilisant le service de configuration et en exposant le mappage de chemin d’accès via `config.json`, le fichier `path.json` est ignoré.

Une fois AEM configuré pour une utilisation en mode sans réponse, vous devez utiliser le service de configuration et fournir un `config.json` valide avec le mappage des chemins d’accès.

### Mettre à jour la configuration AEM {#update-aem}

Vous êtes maintenant prêt à apporter les modifications nécessaires à vos Edge Delivery Services dans AEM.

1. Connectez-vous à l’instance d’auteur AEM et accédez à **Outils** -> **Configuration des Cloud Service** -> **Configuration des Edge Delivery Services** et sélectionnez la configuration qui a été automatiquement créée pour votre site, puis appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre **Configuration des Edge Delivery Services**, remplacez le type de projet par **aem.live avec la configuration repoless** et appuyez ou cliquez sur **Enregistrer et fermer**.
   ![Configuration des Edge Delivery Services ](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Revenez à votre site à l’aide de l’éditeur universel et assurez-vous qu’il s’affiche toujours correctement.
1. Modifier une partie de votre contenu et le republier.
1. Rendez-vous sur le site publié à l’adresse `https://main--<your-aem-project>--<your-github-org>.aem.page/` et vérifiez que les modifications sont correctement répercutées.

Votre projet est maintenant configuré pour une utilisation sans réponse.

## Étapes suivantes {#next-steps}

Maintenant que votre site de base est configuré pour une utilisation sans réponse, vous pouvez créer d’autres sites qui utilisent la même base de code. Reportez-vous à la documentation suivante en fonction de votre cas d’utilisation.

* [Gestion de plusieurs sites sans référentiel](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Environnements d’évaluation et de production sans référentiel](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)

## Résolution des problèmes {#troubleshooting}

Le problème le plus courant rencontré après la configuration du cas d’utilisation des réponses est que les pages dans l’éditeur universel ne s’affichent plus ou que vous recevez une page blanche ou un message d’erreur AEM as a Cloud Service générique. Dans ce cas :

* Affichez la source de la page rendue.
   * Existe-t-il réellement un rendu (HTML correct avec les fichiers JSON liés à `scripts.js`, `aem.js` et l’éditeur) ?
* Recherchez des exceptions dans la `error.log` AEM de l’instance de création.
   * Le problème le plus courant est l’échec du composant de page avec des erreurs 404.
   * `config.json or paths.json` ne peut pas être chargé
   * `component-definition.json`, etc. ne peut pas être chargé

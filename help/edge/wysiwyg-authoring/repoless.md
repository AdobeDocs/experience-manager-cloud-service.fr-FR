---
title: Réutilisation du code sur plusieurs sites
description: Si vous disposez de nombreux sites similaires qui se ressemblent et se comportent globalement de la même manière, mais avec un contenu différent, découvrez comment partager du code sur plusieurs sites dans un modèle sans référentiel.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '1039'
ht-degree: 100%

---

# Réutilisation du code sur plusieurs sites {#repoless}

Si vous disposez de nombreux sites similaires qui se ressemblent et se comportent globalement de la même manière, mais avec un contenu différent, découvrez comment partager du code sur plusieurs sites dans un modèle sans référentiel.

## Une base de code pour plusieurs sites {#one-codebase}

Par défaut, AEM est étroitement lié à votre référentiel de code, ce qui répond à la majorité des cas d’utilisation. Cependant, vous pouvez avoir plusieurs sites qui diffèrent principalement par leur contenu, mais qui peuvent utiliser la même base de code.

Plutôt que de créer plusieurs référentiels GitHub et d’exécuter chaque site à partir d’un référentiel GitHub dédié tout en les maintenant synchronisés, AEM prend en charge l’exécution de plusieurs sites à partir de la même base de code.

Cette configuration simplifiée, qui élimine la nécessité de la réplication du code, est également appelée [« sans référentiel »](https://www.aem.live/docs/repoless) car tous les sites, à l’exception de votre premier site, n’ont pas besoin de leur propre référentiel GitHub.

Si votre projet nécessite la flexibilité de la réutilisation du code sans référentiel sur plusieurs sites, vous pouvez activer la fonctionnalité.

Quel que soit le nombre de sites que vous souhaitez créer en fin de compte sans référentiel, vous devez créer votre premier site, qui sert de site de base. Ce document explique comment créer votre premier site pour une utilisation sans référentiel.

## Prérequis {#prerequisites}

Pour tirer parti de cette fonctionnalité, assurez-vous de répondre aux conditions suivantes.

* Votre site est déjà entièrement configuré conformément au document [Guide de prise en main du développement pour la création WYSIWYG avec Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md).
* Vous exécutez AEM as a Cloud Service, version 2024.08 ou ultérieure.

Vous devrez également demander à Adobe de configurer les éléments suivants pour vous. Contactez Adobe par l’intermédiaire du canal Slack ou créez un ticket d’assistance afin de demander d’apporter les modifications suivantes :

* Demandez l’activation du [service de configuration aem.live](https://www.aem.live/docs/config-service-setup#prerequisites) pour votre environnement et votre configuration en tant qu’administrateur ou administratrice.
* Demandez à Adobe d’activer la fonction d’absence de référentiel pour votre programme.
* Demandez à Adobe de créer l’organisation pour vous.

## Activer la fonction d’absence de référentiel {#activate}

Plusieurs étapes permettent d’activer la fonctionnalité d’absence de référentiel pour votre projet.

1. [Récupérer le jeton d’accès](#access-token)
1. [Configurer un service de configuration](#config-service)
1. [Ajouter la configuration du site et le compte technique](#access-control)
1. [Mettre à jour la configuration AEM](#update-aem)
1. [Authentifier le site](#authenticate-site)

Ces étapes utilisent le site `https://wknd.site` comme exemple. Remplacez-le par le vôtre en conséquence.

### Récupérer le jeton d’accès {#access-token}

Vous aurez d’abord besoin d’un jeton d’accès pour utiliser le service de configuration et le configurer pour le cas d’utilisation sans référentiel.

1. Accédez à `https://admin.hlx.page/login` et utilisez l’adresse `login_adobe` pour vous connecter au fournisseur d’identités Adobe.
1. Vous ferez l’objet d’un transfert vers `https://admin.hlx.page/profile`.
1. À l’aide des outils de développement de votre navigateur, copiez la valeur du `x-auth-token` à partir du cookie de jeton web JSON défini par la page `admin.hlx.page`.

Une fois que vous disposez de votre jeton d’accès, il peut être transmis dans l’en-tête des requêtes cURL au format suivant.

```text
--header 'x-auth-token: <your-token>'
```

### Ajouter un mappage de chemin d’accès pour la configuration du site et définir le compte technique {#access-control}

Vous devez créer une configuration de site et l’ajouter à votre mappage de chemin d’accès.

1. Créez une page à la racine de votre site et choisissez le [**modèle Configuration**](/help/edge/wysiwyg-authoring/tabular-data.md#other).
   * Vous pouvez laisser la configuration vide avec uniquement les colonnes `key` et `value` prédéfinies. Il suffit de la créer.
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

1. Connectez-vous à l’instance de création AEM et accédez à **Outils** -> **Services cloud** -> **Configuration Edge Delivery Services** et sélectionnez la configuration qui a été automatiquement créée pour votre site, puis appuyez ou cliquez sur **Propriétés** dans la barre d’outils.

1. Dans la fenêtre **Configuration d’Edge Delivery Services**, sélectionnez l’onglet **Authentification** et copiez la valeur de l’**Identifiant du compte technique**.

   * Il ressemblera à `<tech-account-id>@techacct.adobe.com`.
   * Le compte technique est le même pour tous les sites sur un seul environnement de création AEM.

1. Définissez le compte technique pour votre configuration sans référentiel avec une commande cURL similaire à la suivante, à l’aide de l’identifiant de compte technique que vous avez copié.

   * Adaptez le bloc `admin` pour définir les utilisateurs et utilisatrices qui doivent disposer d’un accès administratif complet au site.
      * Il s’agit d’un tableau d’adresses e-mail.
      * Le caractère générique `*` peut être utilisé.
      * Pour plus d’informations, consultez le document [Configuration de l’authentification pour les personnes chargées de la création](https://www.aem.live/docs/authentication-setup-authoring#default-roles).

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

Une fois AEM configuré pour une utilisation sans référentiel, vous devez utiliser le service de configuration et fournir un `config.json` valide avec le mappage des chemins d’accès.

### Mettre à jour la configuration AEM {#update-aem}

Vous êtes maintenant en mesure d’apporter les modifications nécessaires à Edge Delivery Services dans AEM.

1. Connectez-vous à l’instance de création AEM et accédez à **Outils** -> **Services cloud** -> **Configuration d’Edge Delivery Services** et sélectionnez la configuration qui a été automatiquement créée pour votre site, puis appuyez ou cliquez sur **Propriétés** dans la barre d’outils.
1. Dans la fenêtre **Configuration d’Edge Delivery Services**, remplacez le type de projet par **aem.live avec configuration sans référentiel** et appuyez ou cliquez sur **Enregistrer et fermer**.
   ![Configuration d’Edge Delivery Services](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Revenez à votre site à l’aide de l’éditeur universel et assurez-vous qu’il s’affiche toujours correctement.
1. Modifiez une partie de votre contenu et republiez-le.
1. Rendez-vous sur le site publié à l’adresse `https://main--<your-aem-project>--<your-github-org>.aem.page/` et vérifiez que les modifications sont correctement répercutées.

Votre projet est maintenant configuré pour une utilisation sans référentiel.

## Étapes suivantes {#next-steps}

Maintenant que votre site de base est configuré pour une utilisation sans référentiel, vous pouvez créer d’autres sites qui utilisent la même base de code. Reportez-vous à la documentation suivante en fonction de votre cas d’utilisation.

* [Gestion de plusieurs sites sans référentiel](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Environnements d’évaluation et de production sans référentiel](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)
* [Authentification de site pour la création de contenu](/help/edge/wysiwyg-authoring/site-authentication.md)

## Résolution des problèmes {#troubleshooting}

Le problème le plus courant rencontré après la configuration du cas d’utilisation sans référentiel est que les pages dans l’éditeur universel ne s’affichent plus ou que vous recevez une page blanche ou un message d’erreur AEM as a Cloud Service générique. Dans ces cas :

* Affichez la source de la page rendue.
   * Existe-t-il réellement un rendu (en-tête HTML correct avec les fichiers JSON liés à `scripts.js`, `aem.js` et l’éditeur) ?
* Recherchez des exceptions dans le `error.log` d’AEM de l’instance de création.
   * Le problème le plus courant est l’échec du composant de page avec des erreurs 404.
   * `config.json or paths.json` ne peut pas être chargé.
   * `component-definition.json` etc. ne peut pas être chargé.

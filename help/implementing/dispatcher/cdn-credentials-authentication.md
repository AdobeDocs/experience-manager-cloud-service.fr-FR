---
title: Configurer les informations d’identification et l’authentification du réseau CDN
description: Découvrez comment configurer les informations d’identification et l’authentification du réseau de diffusion de contenu en déclarant les règles dans un fichier de configuration qui est ensuite déployé à l’aide du pipeline de configuration Cloud Manager.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
role: Admin
source-git-commit: c31441baa6952d92be4446f9035591b784091324
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 4%

---


# Configurer les informations d’identification et l’authentification du réseau CDN {#cdn-credentials-authentication}

Le réseau de diffusion de contenu fourni par l’Adobe dispose de plusieurs fonctionnalités et services, dont certains dépendent des informations d’identification et de l’authentification afin d’assurer un niveau approprié de sécurité de l’entreprise. En déclarant des règles dans un fichier de configuration déployé à l’aide du pipeline de configuration Cloud Manager [config, les clients ](/help/operations/config-pipeline.md) peuvent configurer, en libre-service, les éléments suivants :

* La valeur d’en-tête HTTP X-AEM-Edge utilisée par le réseau de diffusion de contenu Adobe pour valider les requêtes provenant d’un réseau de diffusion de contenu géré par le client.
* Jeton API utilisé pour purger les ressources dans le cache CDN.
* Liste de combinaisons nom d’utilisateur/mot de passe pouvant accéder à un contenu restreint, en envoyant un formulaire d’authentification de base.

Chacune d’elles, y compris la syntaxe de configuration, est décrite dans sa propre section ci-dessous.

Il existe une section sur la façon de [faire pivoter les clés](#rotating-secrets), ce qui est une bonne pratique de sécurité.

## Valeur d’en-tête HTTP CDN gérée par le client {#CDN-HTTP-value}

Comme décrit dans la page [CDN dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN), les clients peuvent choisir d’acheminer le trafic par le biais de leur propre CDN, qui est appelé le CDN client (également parfois appelé BYOCDN).

Dans le cadre de la configuration, le réseau de diffusion de contenu Adobe et le réseau de diffusion de contenu client doivent s’entendre sur une valeur de l’en-tête HTTP `X-AEM-Edge-Key`. Cette valeur est définie sur chaque requête, sur le réseau de diffusion de contenu client, avant d’être acheminée vers le réseau de diffusion de contenu Adobe, qui valide ensuite que la valeur est comme prévu, de sorte qu’il puisse faire confiance à d’autres en-têtes HTTP, y compris ceux qui aident à acheminer la demande vers l’origine AEM appropriée.

La valeur *X-AEM-Edge-Key* est référencée par les propriétés `edgeKey1` et `edgeKey2` dans un fichier nommé `cdn.yaml` ou similaire, quelque part sous un dossier de niveau supérieur `config`. Lisez [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure) pour plus d’informations sur la structure de dossiers et sur le déploiement de la configuration.

La syntaxe est décrite ci-dessous :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
    authenticators:
      - name: edge-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_052824}}
        edgeKey2: ${{CDN_EDGEKEY_041425}}
    rules:
      - name: edge-auth-rule
        when: { reqProperty: tier, equals: "publish" }
        action:
          type: authenticate
          authenticator: edge-auth
```

Voir la section [Utiliser les pipelines de configuration](/help/operations/config-pipeline.md#common-syntax) pour obtenir une description des propriétés situées au-dessus du nœud `data`. La valeur de la propriété `kind` doit être *CDN* et la propriété `version` doit être définie sur `1`.

Autres propriétés :

* Noeud `Data` contenant un noeud `authentication` enfant.
* Sous `authentication`, un noeud `authenticators` et un noeud `rules`, qui sont tous deux des tableaux.
* Authentificateurs : vous permet de déclarer un type de jeton ou d’informations d’identification, qui dans ce cas est une clé de périphérie. Elle comprend les propriétés suivantes :
   * name : chaîne descriptive.
   * type - doit être `edge`.
   * edgeKey1 : valeur de la *X-AEM-Edge-Key*, qui doit référencer une [variable d&#39;environnement de type secret Cloud Manager](/help/operations/config-pipeline.md#secret-env-vars). Pour le champ Service appliqué, sélectionnez Tous. Il est recommandé que la valeur (par exemple,`${{CDN_EDGEKEY_052824}}`) reflète le jour où elle a été ajoutée.
   * edgeKey2 : utilisé pour la rotation des secrets, qui est décrite dans la [section de secrets tournants](#rotating-secrets) ci-dessous. Définissez-le de la même manière que edgeKey1. Au moins un des `edgeKey1` et `edgeKey2` doit être déclaré.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* Règles : vous permet de déclarer quels authentificateurs doivent être utilisés et s’il s’agit du niveau de publication et/ou d’aperçu.  Il comprend :
   * name : chaîne descriptive.
   * when - condition qui détermine quand la règle doit être évaluée, selon la syntaxe de l’article [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) . En règle générale, il comprend une comparaison du niveau actuel (par exemple, publication) afin que tout le trafic en direct soit validé en tant que routage via le réseau de diffusion de contenu du client.
   * action : doit spécifier &quot;authenticate&quot;, avec l’authentificateur prévu référencé.

>[!NOTE]
>La clé Edge doit être configurée en tant que [ variable d’environnement Cloud Manager de type secret ](/help/operations/config-pipeline.md#secret-env-vars) avant le déploiement de la configuration qui la référence. Il est recommandé d’utiliser une clé aléatoire unique d’une longueur minimale de 32 octets ; par exemple, la bibliothèque cryptographique Open SSL peut générer une clé aléatoire en exécutant la commande `openssl rand -hex 32`.

### Migration sécurisée pour réduire le risque de trafic bloqué {#migrating-safely}

Si votre site est déjà actif, soyez prudent lors de la migration vers le réseau de diffusion de contenu géré par le client, car une mauvaise configuration peut bloquer le trafic public. En effet, seules les demandes avec la valeur d’en-tête X-AEM-Edge-Key attendue seront acceptées par le réseau de diffusion de contenu Adobe. Une approche est recommandée lorsqu’une condition supplémentaire est temporairement incluse dans la règle d’authentification, ce qui la force à évaluer uniquement la requête si un en-tête de test est inclus :

```
    - name: edge-auth-rule
        when:
          allOf:  
            - { reqProperty: tier, equals: "publish" }
            - { reqHeader: x-edge-test, equals: "test" }
        action:
          type: authenticate
          authenticator: edge-auth
```

Le modèle de requête `curl` suivant peut être utilisé :

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <CONFIGURED_EDGE_KEY>" -H "x-edge-test: test"
```

Une fois le test réussi, la condition supplémentaire peut être supprimée et la configuration redéployée.

## Purge du jeton API {#purge-API-token}

Les clients peuvent [purger le cache CDN](/help/implementing/dispatcher/cdn-cache-purge.md) à l’aide d’un jeton API de purge déclaré. Le jeton est déclaré dans un fichier nommé `cdn.yaml` ou similaire, quelque part sous un dossier de niveau supérieur `config`. Lisez [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure) pour plus d’informations sur la structure de dossiers et sur le déploiement de la configuration.

La syntaxe est décrite ci-dessous :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
    authenticators:
       - name: purge-auth
         type: purge
         purgeKey1: ${{CDN_PURGEKEY_031224}}
         purgeKey2: ${{CDN_PURGEKEY_021225}}
    rules:
       - name: purge-auth-rule
         when: { reqProperty: tier, equals: "publish" }
         action:
           type: authenticate
           authenticator: purge-auth
```

Voir la section [Utiliser les pipelines de configuration](/help/operations/config-pipeline.md#common-syntax) pour obtenir une description des propriétés situées au-dessus du nœud `data`. La valeur de la propriété `kind` doit être *CDN* et la propriété `version` doit être définie sur `1`.

Autres propriétés :

* Noeud `data` contenant un noeud `authentication` enfant.
* Sous `authentication`, un noeud `authenticators` et un noeud `rules`, qui sont tous deux des tableaux.
* Authentificateurs : vous permet de déclarer un type de jeton ou d’informations d’identification, qui dans ce cas est une clé de purge. Elle comprend les propriétés suivantes :
   * name : chaîne descriptive.
   * type : doit être purge.
   * purgeKey1 : sa valeur doit référencer une [variable d’environnement de type secret Cloud Manager](/help/operations/config-pipeline.md#secret-env-vars). Pour le champ Service appliqué, sélectionnez Tous. Il est recommandé que la valeur (par exemple, `${{CDN_PURGEKEY_031224}}`) reflète le jour où elle a été ajoutée.
   * purgeKey2 : utilisé pour la rotation des secrets, qui est décrite dans la section [Rotation des secrets](#rotating-secrets) ci-dessous. Au moins un des `purgeKey1` et `purgeKey2` doit être déclaré.
* Règles : vous permet de déclarer quels authentificateurs doivent être utilisés et s’il s’agit du niveau de publication et/ou d’aperçu.  Il comprend :
   * name - chaîne descriptive
   * when - condition qui détermine quand la règle doit être évaluée, selon la syntaxe de l’article [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) . En règle générale, il comprend une comparaison du niveau actuel (par exemple, publication).
   * action : doit spécifier &quot;authenticate&quot;, avec l’authentificateur prévu référencé.

>[!NOTE]
>La clé de purge doit être configurée en tant que [ variable d’environnement de Cloud Manager de type secret ](/help/operations/config-pipeline.md#secret-env-vars) avant le déploiement de la configuration qui la fait référence. Il est recommandé d’utiliser une clé aléatoire unique d’une longueur minimale de 32 octets ; par exemple, la bibliothèque cryptographique Open SSL peut générer une clé aléatoire en exécutant la commande openssl rand -hex 32.

Vous pouvez référencer [un tutoriel](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache) axé sur la configuration des clés de purge et l’exécution de la purge du cache CDN.

## Authentification de base {#basic-auth}

Protégez certaines ressources de contenu en affichant une boîte de dialogue d’authentification de base nécessitant un nom d’utilisateur ou d’utilisatrice et un mot de passe. Cette fonctionnalité est principalement destinée aux cas d’utilisation de l’authentification légère, tels que la révision du contenu par les parties prenantes de l’entreprise, plutôt qu’en tant que solution complète pour les droits d’accès des utilisateurs finaux.

Une boîte de dialogue d’authentification de base s’affiche pour l’utilisateur final comme suit :

![basicauth-dialog](/help/implementing/dispatcher/assets/basic-auth-dialog.png)


La syntaxe est la suivante :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
    authenticators:
       - name: my-basic-authenticator
         type: basic
         credentials:
           - user: johndoe
             password: ${{JOHN_DOE_PASSWORD}}
           - user: janedoe
             password: ${{JANE_DOE_PASSWORD}}
    rules:
       - name: basic-auth-rule
         when: { reqProperty: path, like: "/summercampaign" }
         action:
           type: authenticate
           authenticator: my-basic-authenticator
```

Voir la section [Utiliser les pipelines de configuration](/help/operations/config-pipeline.md#common-syntax) pour obtenir une description des propriétés situées au-dessus du nœud `data`. La valeur de la propriété `kind` doit être *CDN* et la propriété `version` doit être définie sur `1`.

En outre, la syntaxe comprend :

* un noeud `data` contenant un noeud `authentication`.
* Sous `authentication`, un noeud `authenticators` et un noeud `rules`, qui sont tous deux des tableaux.
* Authentificateurs : dans ce scénario, déclarez un authentificateur de base, qui possède la structure suivante :
   * name - chaîne descriptive
   * type - doit être `basic`
   * un tableau de 10 informations d’identification au maximum, dont chacune comprend les paires nom/valeur suivantes, que les utilisateurs finaux peuvent entrer dans la boîte de dialogue d’authentification de base :
      * user : nom de l’utilisateur
      * password : sa valeur doit faire référence à une [variable d’environnement de type secret Cloud Manager](/help/operations/config-pipeline.md#secret-env-vars), **All** étant sélectionné en tant que champ de service.
* Règles : vous permet de déclarer quels authentificateurs doivent être utilisés et quelles ressources doivent être protégées. Chaque règle comprend :
   * name - chaîne descriptive
   * when - condition qui détermine quand la règle doit être évaluée, selon la syntaxe de l’article [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) . En règle générale, il comprend une comparaison du niveau de publication ou des chemins spécifiques.
   * action : doit spécifier &quot;authenticate&quot;, avec l’authentificateur prévu référencé, qui est une authentification de base pour ce scénario.

>[!NOTE]
>Les mots de passe doivent être configurés en tant que [ variables d’environnement Cloud Manager de type secret ](/help/operations/config-pipeline.md#secret-env-vars) avant le déploiement de la configuration qui y fait référence.

## Rotation des secrets {#rotating-secrets}

1. Il est recommandé de modifier occasionnellement les informations d’identification en toute sécurité. Vous pouvez y parvenir comme illustré ci-dessous en utilisant l’exemple d’une clé de périphérie, bien que la même stratégie soit utilisée pour les clés de purge.

1. Initialement, seul `edgeKey1` a été défini, dans ce cas appelé `${{CDN_EDGEKEY_052824}}`, qui, comme convention recommandée, reflète la date à laquelle il a été créé.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
   ```
1. Lorsque le temps est venu de faire pivoter la clé, créez un secret Cloud Manager, par exemple `${{CDN_EDGEKEY_041425}}`.
1. Dans la configuration, référencez-la à partir de `edgeKey2` et déployez-la.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```

1. Une fois que vous êtes certain que l’ancienne clé Edge n’est plus utilisée, supprimez-la en supprimant `edgeKey1` de la configuration.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```
1. Supprimez l’ancienne référence secrète (`${{CDN_EDGEKEY_052824}}`) de Cloud Manager et déployez-la.

1. Lorsque vous êtes prêt pour la rotation suivante, procédez de la même manière. Toutefois, cette fois, vous ajouterez `edgeKey1` à la configuration, en référençant un nouveau secret d’environnement Cloud Manager nommé, par exemple `${{CDN_EDGEKEY_031426}}`.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
         edgeKey1: ${{CDN_EDGEKEY_031426}}
   ```

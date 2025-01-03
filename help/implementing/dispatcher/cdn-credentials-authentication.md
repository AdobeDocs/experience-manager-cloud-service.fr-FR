---
title: Configurer les informations d’identification et l’authentification du réseau CDN
description: Découvrez comment configurer les informations d’identification et d’authentification du réseau CDN en déclarant des règles dans un fichier de configuration qui est ensuite déployé à l’aide du pipeline de configuration Cloud Manager.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
role: Admin
source-git-commit: d6484393410d32f348648e13ad176ef5136752f2
workflow-type: tm+mt
source-wordcount: '1497'
ht-degree: 4%

---


# Configurer les informations d’identification et l’authentification du réseau CDN {#cdn-credentials-authentication}

Le réseau CDN fourni par l’Adobe dispose de plusieurs fonctionnalités et services, dont certains reposent sur des informations d’identification et une authentification afin d’assurer un niveau approprié de sécurité de l’entreprise. En déclarant des règles dans un fichier de configuration déployé à l’aide du pipeline Cloud Manager [config](/help/operations/config-pipeline.md) les clients peuvent configurer les éléments suivants en libre-service :

* Valeur d’en-tête HTTP X-AEM-Edge-Key utilisée par le réseau CDN d’Adobe pour valider les requêtes provenant d’un réseau CDN géré par le client ou la cliente.
* Jeton API utilisé pour purger les ressources dans le cache du réseau CDN.
* Liste des combinaisons de nom d’utilisateur/mot de passe pouvant accéder au contenu restreint en envoyant un formulaire d’authentification de base.

Chacune de ces options, y compris la syntaxe de configuration, est décrite dans sa propre section ci-dessous.

Il existe une section sur la [rotation de clés](#rotating-secrets), qui est une bonne pratique de sécurité.

## Valeur de l’en-tête HTTP du réseau CDN géré par le client {#CDN-HTTP-value}

Comme indiqué dans la page [Réseau CDN dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN), les clients peuvent choisir d’acheminer le trafic via leur propre réseau CDN, qui est appelé réseau CDN client (également parfois appelé BYOCDN).

Dans le cadre de la configuration, le réseau CDN d’Adobe et le réseau CDN client doivent convenir d’une valeur de l’en-tête HTTP `X-AEM-Edge-Key`. Cette valeur est définie sur chaque requête sur le réseau CDN client, avant d’être acheminée vers le réseau CDN Adobe, qui valide ensuite que la valeur est comme prévu, afin qu’il puisse approuver d’autres en-têtes HTTP, y compris ceux qui permettent d’acheminer la requête vers l’origine AEM appropriée.

La valeur *X-AEM-Edge-Key* est référencée par les propriétés `edgeKey1` et `edgeKey2` dans un fichier nommé `cdn.yaml` ou similaire, quelque part sous un dossier `config` de niveau supérieur. Lisez [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure) pour plus d’informations sur la structure de dossiers et sur le déploiement de la configuration.  La syntaxe est décrite dans l’exemple ci-dessous.

Pour plus d’informations sur le débogage et les erreurs courantes, consultez la section [Erreurs courantes](/help/implementing/dispatcher/cdn.md#common-errors).

>[!WARNING]
>L’accès direct sans clé X-AEM-Edge-Key correcte sera refusé pour toutes les requêtes correspondant à la condition (dans l’exemple ci-dessous, cela signifie toutes les requêtes au niveau de publication). Si vous devez introduire progressivement l’authentification, reportez-vous à la section [ Migration en toute sécurité pour réduire le risque de trafic bloqué ](#migrating-safely).

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

Pour plus d’informations](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/content-delivery/custom-domain-names-with-customer-managed-cdn#configure-and-deploy-http-header-validation-cdn-rule) consultez l’étape de tutoriel [Configurer et déployer une règle CDN de validation d’en-tête HTTP .

Les propriétés supplémentaires sont les suivantes :

* `Data` nœud qui contient un nœud `authentication` enfant.
* Sous `authentication`, un nœud `authenticators` et un nœud `rules`, qui sont tous deux des tableaux.
* Authentificateurs : vous permet de déclarer un type de jeton ou d’informations d’identification, qui est dans ce cas une clé Edge. Il comprend les propriétés suivantes :
   * name : chaîne descriptive.
   * type : doit être `edge`.
   * edgeKey1 : valeur de *X-AEM-Edge-Key*, qui doit référencer une variable d’environnement de type secret Cloud Manager [](/help/operations/config-pipeline.md#secret-env-vars). Pour le champ Service appliqué , sélectionnez Tout. Il est recommandé que la valeur (par exemple, `${{CDN_EDGEKEY_052824}}`) reflète le jour où elle a été ajoutée.
   * edgeKey2 - utilisé pour la rotation des secrets, qui est décrite dans la [section rotation des secrets](#rotating-secrets) ci-dessous. Définissez-le de la même manière que edgeKey1. Au moins un des `edgeKey1` et `edgeKey2` doit être déclaré.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* Règles : vous permet de déclarer quels authentificateurs doivent être utilisés, et s’il s’agit du niveau de publication et/ou d’aperçu.  Il comprend :
   * name : chaîne descriptive.
   * when : condition qui détermine le moment où la règle doit être évaluée, en fonction de la syntaxe contenue dans l’article [Règles de filtrage de trafic](/help/security/traffic-filter-rules-including-waf.md). En règle générale, il comprend une comparaison du niveau actuel (par exemple, publication) afin que tout le trafic en direct soit validé comme routage via le réseau CDN client.
   * action : vous devez spécifier « authentifier », avec l’authentificateur prévu référencé.

>[!NOTE]
>La clé Edge doit être configurée en tant que [variable d’environnement Cloud Manager de type secret](/help/operations/config-pipeline.md#secret-env-vars), avant que la configuration qui y fait référence ne soit déployée. Il est recommandé d’utiliser une clé aléatoire unique d’une longueur minimale de 32 octets ; par exemple, la bibliothèque cryptographique SSL ouverte peut générer une clé aléatoire en exécutant la commande `openssl rand -hex 32`.

### Migration en toute sécurité pour réduire le risque de trafic bloqué {#migrating-safely}

Si votre site est déjà actif, soyez prudent lors de la migration vers le réseau CDN géré par le client, car une mauvaise configuration peut bloquer le trafic public. En effet, seules les requêtes présentant la valeur d’en-tête X-AEM-Edge-Key attendue seront acceptées par le réseau CDN d’Adobe. Une approche est recommandée lorsqu’une condition supplémentaire est temporairement incluse dans la règle d’authentification, ce qui entraîne le blocage de la requête uniquement si un en-tête de test est inclus ou si un chemin d’accès correspond :

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

```
    - name: edge-auth-rule
        when:
          allOf:
            - { reqProperty: tier, equals: "publish" }
            - { reqProperty: path, like: "/test*" }
        action:
          type: authenticate
          authenticator: edge-auth
```

Le modèle de requête `curl` suivant peut être utilisé :

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <CONFIGURED_EDGE_KEY>" -H "x-edge-test: test"
```

Une fois le test réussi, la condition supplémentaire peut être supprimée et la configuration redéployée.

## Purger le jeton API {#purge-API-token}

Les clients peuvent [purger le cache du réseau CDN](/help/implementing/dispatcher/cdn-cache-purge.md) en utilisant un jeton API de purge déclaré. Le jeton est déclaré dans un fichier nommé `cdn.yaml` ou similaire, quelque part sous un dossier de `config` de niveau supérieur. Lisez [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure) pour plus d’informations sur la structure de dossiers et sur le déploiement de la configuration.

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

Les propriétés supplémentaires sont les suivantes :

* `data` nœud qui contient un nœud `authentication` enfant.
* Sous `authentication`, un nœud `authenticators` et un nœud `rules`, qui sont tous deux des tableaux.
* Authentifiants : vous permet de déclarer un type de jeton ou d’informations d’identification, qui est dans ce cas une clé de purge. Il comprend les propriétés suivantes :
   * name : chaîne descriptive.
   * type : doit être purgé.
   * purgeKey1 - sa valeur doit référencer une variable d’environnement de type secret Cloud Manager [](/help/operations/config-pipeline.md#secret-env-vars). Pour le champ Service appliqué , sélectionnez Tout. Il est recommandé que la valeur (par exemple, `${{CDN_PURGEKEY_031224}}`) reflète le jour où elle a été ajoutée.
   * purgeKey2 - utilisé pour la rotation des secrets, qui est décrite dans la section [rotation des secrets](#rotating-secrets) ci-dessous. Au moins un des `purgeKey1` et `purgeKey2` doit être déclaré.
* Règles : vous permet de déclarer quels authentificateurs doivent être utilisés, et s’il s’agit du niveau de publication et/ou d’aperçu.  Il comprend :
   * name : chaîne descriptive.
   * when : condition qui détermine le moment où la règle doit être évaluée, en fonction de la syntaxe contenue dans l’article [Règles de filtrage de trafic](/help/security/traffic-filter-rules-including-waf.md). En règle générale, il comprend une comparaison du niveau actuel (par exemple, publication).
   * action : vous devez spécifier « authentifier », avec l’authentificateur prévu référencé.

>[!NOTE]
>La clé de purge doit être configurée en tant que [variable d’environnement Cloud Manager de type secret](/help/operations/config-pipeline.md#secret-env-vars) avant que la configuration qui y fait référence ne soit déployée. Il est recommandé d’utiliser une clé aléatoire unique d’une longueur minimale de 32 octets ; par exemple, la bibliothèque cryptographique Open SSL peut générer une clé aléatoire en exécutant la commande openssl rand -hex 32

Vous pouvez consulter [un tutoriel](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache) axé sur la configuration des clés de purge et l’exécution de la purge du cache du réseau CDN.

## Authentification de base {#basic-auth}

Protégez certaines ressources de contenu en affichant une boîte de dialogue d’authentification de base nécessitant un nom d’utilisateur ou d’utilisatrice et un mot de passe. Cette fonctionnalité est principalement destinée aux cas d’utilisation d’authentification légers tels que l’examen du contenu par les parties prenantes de l’entreprise, plutôt qu’à une solution complète pour les droits d’accès des utilisateurs finaux.

Une boîte de dialogue d’authentification de base s’affiche pour l’utilisateur final, comme suit :

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

* un nœud `data` qui contient un nœud `authentication`.
* Sous `authentication`, un nœud `authenticators` et un nœud `rules`, qui sont tous deux des tableaux.
* Authentificateurs : dans ce scénario, déclarez un authentificateur de base, qui possède la structure suivante :
   * name : chaîne descriptive.
   * type - doit être `basic`
   * un tableau contenant jusqu’à 10 informations d’identification, chacune d’elles incluant les paires nom/valeur suivantes, que les utilisateurs finaux peuvent saisir dans la boîte de dialogue d’authentification de base :
      * user : nom de l’utilisateur.
      * password : sa valeur doit référencer une variable d’environnement de type secret Cloud Manager [](/help/operations/config-pipeline.md#secret-env-vars), avec **All** sélectionné comme champ de service.
* Règles : permet de déclarer quels authentificateurs doivent être utilisés et quelles ressources doivent être protégées. Chaque règle comprend :
   * name : chaîne descriptive.
   * when : condition qui détermine le moment où la règle doit être évaluée, en fonction de la syntaxe contenue dans l’article [Règles de filtrage de trafic](/help/security/traffic-filter-rules-including-waf.md). En règle générale, il comprend une comparaison du niveau de publication ou de chemins d’accès spécifiques.
   * action : vous devez spécifier « authenticate », avec l’authentificateur prévu référencé, qui est une authentification de base pour ce scénario.

>[!NOTE]
>Les mots de passe doivent être configurés en tant que [variables d’environnement Cloud Manager de type secret](/help/operations/config-pipeline.md#secret-env-vars), avant que la configuration qui y fait référence ne soit déployée.

## Rotation des secrets {#rotating-secrets}

1. La modification occasionnelle des informations d’identification est une bonne pratique de sécurité. Vous pouvez le faire comme illustré ci-dessous, en utilisant l’exemple d’une clé Edge, bien que la même stratégie soit utilisée pour les clés de purge.

1. Au départ, `edgeKey1` seule a été définie, dans ce cas référencée par `${{CDN_EDGEKEY_052824}}`, qui, selon une convention recommandée, reflète la date de création.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
   ```
1. Au moment de faire pivoter la clé, créez un secret Cloud Manager, par exemple `${{CDN_EDGEKEY_041425}}`.
1. Dans la configuration, référencez-la à partir de `edgeKey2` et déployez-la.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```

1. Une fois que vous êtes sûr que l’ancienne clé Edge n’est plus utilisée, supprimez-la en supprimant `edgeKey1` de la configuration.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```
1. Supprimez l’ancienne référence secrète (`${{CDN_EDGEKEY_052824}}`) de Cloud Manager et déployez.

1. Lorsque vous êtes prêt pour la prochaine rotation, suivez la même procédure, mais cette fois, vous ajouterez des `edgeKey1` à la configuration, en référençant un nouveau secret d’environnement Cloud Manager nommé, par exemple, `${{CDN_EDGEKEY_031426}}`.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
         edgeKey1: ${{CDN_EDGEKEY_031426}}
   ```

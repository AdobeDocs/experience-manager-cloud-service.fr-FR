---
title: Configuration des règles de filtre de trafic avec des règles WAF
description: Utilisation de règles de filtrage du trafic avec des règles WAF pour filtrer le trafic
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
source-git-commit: 9345ec974c9fbd525b12b53d20d98809cd72cb04
workflow-type: tm+mt
source-wordcount: '3810'
ht-degree: 1%

---

# Configuration des règles de filtrage du trafic avec des règles WAF pour filtrer le trafic {#configuring-cdn-and-waf-rules-to-filter-traffic}

>[!NOTE]
>
>Cette fonctionnalité n’est pas encore disponible pour l’ensemble de la population. Pour rejoindre le programme d’adoption précoce en cours, envoyez un courrier électronique à l’adresse **aemcs-waf-adopter@adobe.com**, notamment le nom de votre organisation et le contexte de votre intérêt pour la fonctionnalité.

Adobe tente d’atténuer les attaques contre les sites web des clients, mais il peut s’avérer utile de filtrer de manière proactive le trafic correspondant à certains modèles afin que le trafic malveillant ne parvienne pas à votre application. Les approches possibles sont les suivantes :

* Modules de calque Apache tels que `mod_security`
* Configuration des règles de filtrage du trafic déployées sur le réseau de diffusion de contenu via le pipeline de configuration de Cloud Manager

Cet article décrit l’approche des règles de filtrage du trafic. La plupart de ces règles bloquent ou autorisent les requêtes en fonction des propriétés de requête et des en-têtes de requête, y compris l’adresse IP, les chemins et l’agent utilisateur. Ces règles peuvent être configurées par tous les clients as a Cloud Service de Sites et Forms AEM.

Les clients qui disposent d’une licence pour le module complémentaire WAF (Web Application Firewall) peuvent également configurer une catégorie supplémentaire de règles appelée &quot;règles de filtrage du trafic WAF&quot; (ou règles WAF, en abrégé). Ces règles WAF bloquent les demandes correspondant à différents modèles connus pour être associés à un trafic malveillant. Contactez votre équipe de compte d’Adobe pour plus d’informations sur les licences de cette fonctionnalité à venir. Notez qu’aucune licence supplémentaire n’est requise lors du programme des premiers adopteurs.

Les règles de filtrage du trafic peuvent être déployées sur tous les types d’environnements cloud (RDE, dev, stage, prod) dans les programmes de production (non sandbox).

## Configuration {#setup}

1. Créez tout d’abord la structure de dossiers et de fichiers suivante dans le dossier de niveau supérieur dans Git :

   ```
   config/
        cdn.yaml
   ```

1. `cdn.yaml` doit contenir des métadonnées ainsi qu’une liste de règles de filtres de trafic et de règles WAF.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
       # Block simple path
       - name: block-path
         when:
           allOf:
             - reqProperty: tier
               matches: "author|publish"
             - reqProperty: path
               equals: '/block/me'
         action: block
   ```

Le paramètre &quot;type&quot; doit être défini sur &quot;CDN&quot; et la version doit être définie sur la version du schéma, qui est actuellement &quot;1&quot;. Voir les exemples ci-dessous.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. Pour configurer les règles WAF, elles doivent être activées dans Cloud Manager, comme décrit ci-dessous pour les scénarios de programme nouveaux et existants. Notez qu’une licence distincte doit être achetée pour WAF.

   1. Pour configurer la fonction WAF sur un nouveau programme, cochez la case **Protection WAF-DDOS** dans la variable **Sécurité** comme illustré ci-dessous. Suivez ensuite les étapes décrites dans la section [Ajout d’un programme de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) pour créer votre programme

   1. Pour configurer le WAF sur un programme existant, sélectionnez l’option **Modifier le programme** en suivant les étapes décrites dans la section [Modification de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) la documentation. Ensuite, dans la variable **Sécurité** de l’assistant, vous pouvez décocher ou cocher l’option WAF-DDOS à tout moment.

1. Pour les types d’environnements autres que RDE, exécutez le pipeline de configuration de Cloud Manager, qui peut être configuré comme décrit ci-dessous.

   1. Dans la carte de pipeline de votre page d’accueil de Cloud Manager, sélectionnez **Ajout d’un pipeline de production** ou **Ajout d’un pipeline hors production** pour lancer l’assistant d’ajout de pipeline
   1. Sélectionner **Pipeline de déploiement** dans l’onglet configuration

      ![Sélection de l’option Pipeline de déploiement](/help/security/assets/deployment.png)

   1. Attribuez un nom à votre pipeline et sélectionnez des déclencheurs de déploiement, puis sélectionnez **Continuer**
   1. Dans le **Code source** onglet, sélectionnez **Déploiement ciblé**, puis sélectionnez **Config**

      ![Sélectionner le déploiement ciblé](/help/security/assets/target-deployment.png)

   1. Sélectionnez le référentiel et la branche selon les besoins. S’il existe un pipeline de configuration pour l’environnement sélectionné, cette sélection est désactivée.

      ![Présentation d’un pipeline de configuration](/help/security/assets/config-pipeline.png)

      >[!NOTE]
      >
      > Les utilisateurs doivent être connectés en tant que Deployment Manager pour configurer ou exécuter ces pipelines.
      > Vous pouvez également configurer et exécuter un seul pipeline de configuration par environnement.

   1. Définissez l’emplacement du code sur l’emplacement où votre configuration racine est stockée (par exemple, /config).
   1. Sélectionnez **Enregistrer**. Votre nouveau pipeline s’affiche dans la carte du pipeline et peut être exécuté lorsque vous êtes prêt.
   1. Pour les RDE, la ligne de commande sera utilisée, mais RDE n’est pas pris en charge pour le moment.

## Syntaxe des règles de filtre de trafic {#rules-syntax}

Vous pouvez configurer `traffic filter rules` pour établir une correspondance sur des modèles tels que les adresses IP, l’agent utilisateur, les en-têtes de requête, le nom d’hôte, la zone géographique et l’URL.

Les clients qui accordent une licence à l’offre WAF peuvent également configurer une catégorie spéciale de règles de filtrage du trafic appelée `WAF traffic filter rules` (ou règles WAF pour abréger) qui font référence à un ou plusieurs indicateurs WAF, répertoriés dans sa propre section ci-dessous.

Voici un exemple d’un ensemble de règles de filtrage du trafic, qui incluent également une règle WAF.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

Le format des règles de filtrage du trafic dans le fichier cdn.yaml est décrit ci-dessous. Consultez quelques exemples dans une section ultérieure.


| **Propriété** | **La plupart des règles de filtrage de trafic** | **Règles de filtre de trafic WAF** | **Type** | **Valeur par défaut** | **Description** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Nom de règle (64 caractères, ne peut contenir que des caractères alphanumériques et - ) |
| when | X | X | `Condition` | - | La structure de base est la suivante :<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>Voir la syntaxe de structure de condition ci-dessous, qui décrit les getters, les prédicats et comment combiner plusieurs conditions. |
| action | X | X | `Action` | log | log, allow, block, log ou action object La valeur par défaut est log |
| rateLimit | X |   | `RateLimit` | non défini | Configuration de limitation de débit. La limitation de débit est désactivée si elle n’est pas définie.<br><br>Vous trouverez ci-dessous une section distincte décrivant la syntaxe rateLimit, ainsi que des exemples. |

### Structure de condition {#condition-structure}

Une condition peut être soit une simple condition, soit un groupe de conditions.

**Condition simple**

Une condition simple est composée d’un getter et d’un prédicat.

```
{ <getter>: <value>, <predicate>: <value> }
```

**Conditions du groupe**

Un groupe de conditions est composé de plusieurs conditions simples et/ou de groupe.

```
<allOf|anyOf>:
  - { <getter>: <value>, <predicate>: <value> }
  - { <getter>: <value>, <predicate>: <value> }
  - <allOf|anyOf>:
    - { <getter>: <value>, <predicate>: <value> }
```

| **Propriété** | **Type** | **Signification** |
|---|---|---|
| **allOf** | `array[Condition]` | **et** opération. true si toutes les conditions répertoriées renvoient true |
| **anyOf** | `array[Condition]` | **ou** opération. true si l’une des conditions répertoriées renvoie true (vrai) |

**Getter**

| **Propriété** | **Type** | **Description** |
|---|---|---|
| reqProperty | `string` | Propriété de requête.<br><br>L’une des : `path` , `queryString`, `method`, `tier`, `domain`, `clientIp`, `clientCountry`<br><br>La propriété domain correspond à une transformation en minuscules de l’en-tête hôte de la requête. Elle est utile pour les comparaisons de chaînes, de sorte que les correspondances ne soient pas omises en raison du respect de la casse.<br><br>La variable `clientCountry` utilise deux codes à lettres affichés à l’adresse [https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) |
| reqHeader | `string` | Renvoie l’en-tête de requête avec le nom spécifié |
| queryParam | `string` | Renvoie le paramètre de requête avec le nom spécifié |
| cookie | `string` | Renvoie le cookie avec le nom spécifié |

**Prédicat**

| **Propriété** | **Type** | **Signification** |
|---|---|---|
| **est égal à** | `string` | true si le résultat getter est égal à la valeur fournie |
| **doesNotEqual** | `string` | true si le résultat getter n’est pas égal à la valeur fournie |
| **j’aime** | `string` | true si le résultat getter correspond au modèle fourni |
| **notLike** | `string` | true si le résultat getter ne correspond pas au modèle fourni |
| **correspond à** | `string` | true si le résultat getter correspond à l’expression régulière fournie |
| **doesNotMatch** | `string` | true si le résultat getter ne correspond pas à l’expression régulière fournie |
| **dans** | `array[string]` | true si la liste fournie contient le résultat getter |
| **notIn** | `array[string]` | true si la liste fournie ne contient pas le résultat getter |
| **pas** | `boolean` | true lorsque la valeur est définie sur true et que la propriété existe ou lorsqu’elle est définie sur false et que la propriété n’existe pas |

### Structure d’action {#action-structure}

Spécifié par `action` qui peut être soit une chaîne spécifiant le type d’action (autoriser, bloquer, consigner) et prenant des valeurs par défaut pour toutes les autres options, soit un objet pour lequel le type de règle est défini via `type` champ obligatoire avec d’autres options applicables à ce type.

**Types d’actions**

Les actions sont classées par ordre de priorité en fonction de leurs types dans le tableau suivant, dans l’ordre d’exécution des actions :

| **Nom** | **Propriétés autorisées** | **Signification** |
|---|---|---|
| **autoriser** | `wafFlags` (facultatif) | si wafFlags n’est pas présent, arrête le traitement des règles et passe à la réponse de diffusion. Si wafFlags est présent, il désactive les protections WAF spécifiées et poursuit le traitement des règles plus poussé. |
| **block** | `status, wafFlags` (facultatif et mutuellement exclusif) | si wafFlags n’est pas présent, renvoie une erreur HTTP en contournant toutes les autres propriétés, le code d’erreur est défini par la propriété status ou la valeur par défaut 406. Si wafFlags est présent, il active les protections WAF spécifiées et poursuit le traitement des règles plus poussé. |
| **log** | `wafFlags` (facultatif) | consigne le fait que la règle a été déclenchée, sinon n’affecte pas le traitement. wafFlags n’a aucun effet |

### Liste des indicateurs WAF {#waf-flags-list}

La variable `wafFlags` peut contenir les éléments suivants :

| **Identifiant d’indicateur** | **Nom de l’indicateur** | **Description** |
|---|---|---|
| SQLI | Injection SQL | SQL Injection est une tentative d’accès à une application ou d’obtention d’informations privilégiées en exécutant des requêtes de base de données arbitraires. |
| ARRIÈRE-PLAN | backdoor | Un signal backdoor est une requête qui tente de déterminer si un fichier backdoor commun est présent sur le système. |
| CMDEXE | Exécution de commande | L’exécution de commande est une tentative de contrôle ou d’endommagement d’un système cible par le biais de commandes système arbitraires par le biais d’entrées utilisateur. |
| XSS | Scripts intersites | Les scripts intersites consistent à tenter de détourner un compte d’utilisateur ou une session de navigation Web par le biais d’un code JavaScript malveillant. |
| TRAVERSAL | Directory Traversal | Directory Traversal est une tentative de navigation dans des dossiers privilégiés à travers un système dans l’espoir d’obtenir des informations sensibles. |
| USERAGENT | Outils d’attaque | L’outil d’attaque est l’utilisation de logiciels automatisés pour identifier des vulnérabilités de sécurité ou pour tenter d’exploiter une vulnérabilité découverte. |
| LOG4J-JNDI | JNDI Log4J | Les attaques JNDI de Log4J tentent d’exploiter la variable [Vulnérabilité de Log4Shell](https://en.wikipedia.org/wiki/Log4Shell) présente dans les versions de Log4J antérieures à la version 2.16.0 |
| AWS SSRF | AWS-SSRF | SSRF (Server Side Request Forgery) est une requête qui tente d’envoyer des requêtes effectuées par l’application web pour cibler les systèmes internes. Les attaques SSRF AWS utilisent SSRF pour obtenir les clés Amazon Web Services (AWS) et accéder aux compartiments S3 et à leurs données. |
| BHH | En-têtes de saut inappropriés | Les en-têtes de saut incorrects indiquent une tentative de contrebande HTTP via un en-tête de transcodage (TE) ou de longueur de contenu (CL) mal formé, ou un en-tête de TE et de CL bien formé. |
| ABNORMALPATH | Chemin anormal | Chemin anormal indique que le chemin d’origine diffère du chemin normalisé (par exemple, `/foo/./bar` est normalisé en `/foo/bar`) |
| COMPRESSÉ | Compression détectée | Le corps de la requête du POST est compressé et ne peut pas être inspecté. Par exemple, si un en-tête de requête &quot;Content-Encoding: gzip&quot; est spécifié et que le corps du POST ne contient pas de texte brut. |
| DOUBLEENCODING | Codage double | Le codage double vérifie la technique d’évasion du double encodage des caractères HTML. |
| NAVIGATION FORCEFULBROWSING | Navigation forcée | La navigation forcée est la tentative d’accès aux pages d’administration qui a échoué. |
| NOTUTF8 | Codage non valide | Un encodage non valide peut entraîner la traduction par le serveur de caractères malveillants d’une requête dans une réponse, provoquant un déni de service ou un XSS. |
| JSON-ERROR | Erreur de codage JSON | Corps de requête de POST, de PUT ou de PATCH spécifié comme contenant JSON dans l’en-tête de requête &quot;Content-Type&quot;, mais contenant des erreurs d’analyse JSON. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |
| MALFORMED-DATA | Données incorrectes dans le corps de la requête | Corps de requête de POST, de PUT ou de PATCH incorrect selon l’en-tête de requête &quot;Content-Type&quot;. Par exemple, si un en-tête de requête &quot;Content-Type: application/x-www-form-urlencoded&quot; est spécifié et contient un corps de POST qui est json. Il s’agit souvent d’une erreur de programmation, d’une requête automatisée ou malveillante. Nécessite l’agent 3.2 ou version ultérieure. |
| SANS | Trafic IP malveillant | [Centre des tempêtes sur Internet SANS](https://isc.sans.edu/) liste des adresses IP qui ont été signalées comme ayant participé à une activité malveillante |
| SIGSCI-IP | Effet réseau | IP marquée par SignalSciences : chaque fois qu’une adresse IP est marquée en raison d’un signal malveillant du moteur de décision, cette adresse IP est propagée à tous les clients. Les demandes suivantes provenant de ces adresses IP qui contiennent un signal supplémentaire pour la durée de l’indicateur sont ensuite consignées. |
| NO-CONTENT-TYPE | En-tête de requête &quot;Content-Type&quot; manquant | Requête de POST, de PUT ou de PATCH ne comportant pas d’en-tête de requête &quot;Content-Type&quot;. Par défaut, les serveurs d’applications doivent assumer &quot;Content-Type: text/plain; charset=us-ascii&quot; dans ce cas. De nombreuses demandes automatisées et malveillantes peuvent ne pas disposer du &quot;type de contenu&quot;. |
| NOUA | Aucun agent utilisateur | De nombreuses requêtes automatisées et malveillantes utilisent des agents utilisateur faux ou manquants pour rendre difficile l’identification du type d’appareil qui effectue les requêtes. |
| TORNODE | Trafic Tor | Tor est un logiciel qui cache l&#39;identité d&#39;un utilisateur. Un pic de trafic Tor peut indiquer qu’un attaquant essaie de masquer sa localisation. |
| DATACENTER | Trafic du centre de données | Le trafic du centre de données est du trafic non organique provenant de fournisseurs d’hébergement identifiés. Ce type de trafic n’est généralement pas associé à un utilisateur final réel. |
| NULLBYTE | Octet nul | Les octets nuls n’apparaissent généralement pas dans une requête et indiquent que la requête est incorrecte et potentiellement malveillante. |
| IMPOSTOR | SearchBot Impostor | L’imposteur de robots de recherche est quelqu’un qui prétend être un robot de recherche Google ou Bing, mais qui n’est pas légitime. Remarque : ne dépend pas d’une réponse seule, mais doit être résolu dans le cloud en premier. Elle ne doit donc pas être utilisée dans une règle précédente. |
| PRIVATEFILE | Fichiers privés | Les fichiers privés sont généralement de nature confidentielle, par exemple un Apache `.htaccess` ou un fichier de configuration susceptible de faire fuiter des informations sensibles. |
| SCANNER | Scanner | Identifie les services et outils d’analyse les plus utilisés |
| RESPONSESPLIT | Fractionnement des réponses HTTP | Identifie le moment où les caractères CRLF sont envoyés en entrée de l’application pour injecter des en-têtes dans la réponse HTTP. |
| XML-ERROR | Erreur de codage XML | Corps de requête de POST, de PUT ou de PATCH spécifié comme contenant du code XML dans l’en-tête de requête &quot;Content-Type&quot;, mais contenant des erreurs d’analyse XML. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |

## Considérations {#considerations}

* Lorsque deux règles en conflit sont créées, les règles d’autorisation ont toujours la priorité sur les règles de blocage. Par exemple, si vous créez une règle pour bloquer un chemin spécifique et une règle pour autoriser une adresse IP spécifique, les demandes de cette adresse IP sur le chemin bloqué seront autorisées.

* Si une règle est mise en correspondance et bloquée, le réseau de diffusion de contenu répond par une `406` code de retour.

* Les fichiers de configuration ne doivent pas contenir de secrets, car ils seront lisibles par toute personne ayant accès au référentiel git.

## Exemples de règles {#examples}

Voici quelques exemples de règles. Voir [section limite de taux](#rules-with-rate-limits) plus bas pour des exemples de limitation de débit.

**Exemple 1**

Cette règle bloque les demandes provenant d’IP 192.168.1.1 :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
     rules:
       - name: "block-request-from-ip"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
         action:
           type: block
```

**Exemple 2**

Cette règle bloque les requêtes sur le chemin d’accès `/helloworld` lors de la publication avec un User-Agent contenant Chrome :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
     rules:
       - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
           allOf:
            - { reqProperty: path, equals: /helloworld }
            - { reqProperty: tier, equals: publish }
            - { reqHeader: user-agent, matches: '.*Chrome.*'  }
           action:
             type: block
```

**Exemple 3**

Cette règle bloque les requêtes qui contiennent le paramètre de requête `foo`, mais autorise chaque requête provenant d’IP 192.168.1.1 :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when: { queryParam: url-param, equals: foo }
        action:
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action:
          type: allow
```

**Exemple 4**

Cette règle bloque les requêtes de chemin /block-me et bloque chaque requête correspondant à un modèle SQLI ou XSS :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

**Exemple 5**

Cette règle bloque l&#39;accès aux pays de l&#39;OFAC :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: block-ofac-countries
        when:
          allOf:
            - reqProperty: tier
              matches: "author|publish"
            - reqProperty: clientCountry
              in:
                - SY
                - BY
                - MM
                - KP
                - IQ
                - CD
                - SD
                - IR
                - LR
                - ZW
                - CU
                - CI
        action: block
```

## Règles avec limites de taux {#rules-with-rate-limits}

Il est parfois souhaitable de bloquer le trafic correspondant à une règle uniquement si la correspondance dépasse un certain taux au fil du temps. Définir une valeur pour la variable `rateLimit` limite le taux de requêtes correspondant à la condition de la règle.

### Structure rateLimit {#ratelimit-structure}

| **Propriété** | **Type** | **Par défaut** | **SIGNIFICATION** |
|---|---|---|---|
| limit | entier compris entre 10 et 10 000 | obligatoire | Taux de requêtes dans les requêtes par seconde pour lesquelles la règle est déclenchée. |
| window | nombre entier : 1, 10 ou 60 | 10 | Fenêtre d’échantillonnage en secondes pour laquelle le taux de requête est calculé. |
| pénalité | entier compris entre 60 et 3 600 | 300 (5 minutes) | Période en secondes pendant laquelle les requêtes correspondantes sont bloquées (arrondie à la minute la plus proche). |
| groupBy | tableau[Getter] | Aucune | le compteur de limiteurs de débit sera agrégé par un ensemble de propriétés de requête (par exemple, clientIp). |

### Exemples {#ratelimiting-examples}

**Exemple 1**

Cette règle bloque un client pour 5 millions lorsqu’il dépasse 100 req/s dans les 60 dernières secondes :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    - name: limit-requests-client-ip
      when:
        - reqProperty: tier
        - matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Exemple 2**

Bloquez les demandes pendant 60 s sur le chemin /critique/resource lorsqu’il dépasse 100 req/s dans les 60 dernières secondes :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when: { reqProperty: path, equals: /critical/resource }
        action:
          type: block
        rateLimit: { limit: 100, window: 60, penalty: 60 }
```

## Journaux du réseau de diffusion de contenu {#cdn-logs}

AEM as a Cloud Service permet d’accéder aux journaux du réseau de diffusion de contenu, qui sont utiles pour les cas d’utilisation, notamment l’optimisation du taux d’accès au cache et la configuration des règles CDN et WAF. Les journaux CDN s’affichent dans Cloud Manager **Journaux de téléchargement** lors de la sélection du service Auteur ou Publier.

La propriété &quot;rules&quot; décrit les règles de filtre de trafic correspondantes et présente le modèle suivant :

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Par exemple :

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

Les règles se comportent comme suit :

* le nom de règle déclaré par le client de toute règle correspondante sera répertorié dans l’attribut matches .
* l’attribut action indique si les règles ont eu pour effet de bloquer, autoriser ou consigner.
* si le WAF est sous licence et activé, l’attribut waf répertorie toutes les règles waf (par exemple, SQLI ; notez qu’elles sont indépendantes du nom déclaré par le client) qui ont été détectées, que les règles waf aient été répertoriées ou non dans la configuration.
* si aucune correspondance de règles déclarées par le client et aucune correspondance de règles waf, la propriété d’attribut rules est vide.

En règle générale, les règles correspondantes apparaissent dans l’entrée de journal pour toutes les requêtes sur le réseau de diffusion de contenu, qu’il s’agisse d’un accès, d’une transmission ou d’une absence sur le réseau de diffusion de contenu. Toutefois, les règles WAF apparaissent dans l’entrée de journal uniquement pour les requêtes au réseau de diffusion de contenu qui sont considérées comme des échecs ou des réussites CDN, mais pas pour les accès CDN.

L’exemple ci-dessous illustre un exemple de cdn.yaml et deux entrées de journal CDN :


```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS ]
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/block-me",
"method": "GET",
"res_ctype": "",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=path-rule,action=blocked"
}
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"rid": "974e67f6",
"host": "example.com",
"url": "/?sqli=%27%29%20UNION%20ALL%20SELECT%20NULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL--%20fAPK",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

### Format du journal {#cdn-log-format}

Vous trouverez ci-dessous une liste des noms de champ utilisés dans les journaux CDN, ainsi qu’une brève description.

| **Nom du champ** | **Description** |
|---|---|
| *timestamp* | Heure à laquelle la demande a commencé, après la fin de TLS. |
| *ttfb* | Abréviation de *Time To First Byte*. Intervalle entre le démarrage de la requête et le début de la diffusion du corps de la réponse. |
| *cli_ip* | Adresse IP du client. |
| *cli_country* | Deux lettres [ISO 3166-1](https://fr.wikipedia.org/wiki/ISO_3166-1) code de pays alpha-2 pour le pays client. |
| *rid* | La valeur de l’en-tête de requête utilisé pour identifier la requête de manière unique. |
| *req_ua* | L’agent utilisateur responsable de l’exécution d’une requête HTTP donnée. |
| *host* | Autorité à laquelle la demande est destinée. |
| *url* | Chemin d’accès complet, y compris les paramètres de requête. |
| *method* | méthode HTTP envoyée par le client, telle que &quot;GET&quot; ou &quot;POST&quot;. |
| *res_ctype* | Type de contenu utilisé pour indiquer le type de média d’origine de la ressource. |
| *cache* | État du cache. Les valeurs possibles sont HIT, MISS ou PASS |
| *status* | Le code d’état HTTP sous la forme d’une valeur entière. |
| *res_age* | Durée (en secondes) pendant laquelle une réponse a été mise en cache (dans tous les noeuds). |
| *pop* | Centre de données du serveur de cache CDN. |
| *règles* | Nom de toute règle correspondante.<br><br>Indique également si la correspondance a entraîné un bloc. <br><br>Par exemple, &quot;`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`&quot;<br><br>Vide si aucune règle ne correspondait. |

## Tutoriel sur les outils de tableau de bord  {#dashboard-tooling}

Adobe fournit un mécanisme de téléchargement des outils de tableau de bord sur votre ordinateur pour ingérer les journaux CDN téléchargés via Cloud Manager. Grâce à cet outil, vous pouvez analyser le trafic afin d’obtenir les règles de filtrage du trafic appropriées à déclarer, y compris les règles WAF. Cette section fournit d’abord quelques instructions pour mieux connaître les outils de tableau de bord dans un environnement de développement, puis des instructions pour tirer parti de ces connaissances afin de créer des règles dans un environnement de production.

Les clients les plus expérimentés des règles de filtrage du trafic doivent demander un fichier zip de l’outil de tableau de bord, qui comprend un fichier README décrivant comment charger le conteneur Docker et ingérer les journaux CDN.


### Familiarisation avec l’outil de tableau de bord {#dashboard-getting-familiar}

1. Créez un pipeline de configuration hors production Cloud Manager, associé à un environnement de développement. Sélectionnez tout d’abord l’option Pipeline de déploiement . Sélectionnez ensuite Déploiement ciblé, Configuration, votre référentiel, la branche git, et définissez l’emplacement du code sur /config.

   ![Ajouter un déploiement sélectionné de pipeline hors production](/help/security/assets/waf-select-pipeline1.png)

   ![Ajouter une sélection de pipeline hors production ciblée](/help/security/assets/waf-select-pipeline2.png)


1. Dans votre espace de travail, créez une configuration de dossier au niveau racine et ajoutez un fichier nommé cdn.yaml, dans lequel vous déclarerez une règle simple, la définissant en mode journal plutôt qu’en mode bloquant.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
       # Log request on simple path
       - name: log-rule-example
         when:
           allOf:
             - reqProperty: tier
               matches: "author|publish"
             - reqProperty: path
               equals: '/log/me'
         action: log
   ```

1. Validez et envoyez vos modifications, puis déployez votre configuration à l’aide du pipeline de configuration.

   ![Exécution du pipeline de configuration](/help/security/assets/waf-run-pipeline.png)

1. Une fois votre configuration déployée, essayez d’accéder à https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me à l’aide de votre navigateur web ou avec la commande curl ci-dessous. Vous devriez être traité avec une page d’erreur 404, car cette page n’existe pas.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. Téléchargez les journaux CDN de Cloud Manager et vérifiez que les règles correspondent à vos attentes, avec une propriété de règles correspondant au nom de la règle :

   ```
   "rules": "match=log-rule-example"
   ```

   ![Sélectionner les journaux de téléchargement](/help/security/assets/waf-download-logs1.png)

   ![Journaux de téléchargement](/help/security/assets/waf-download-logs2.png)

1. Chargez l’image Docker à l’aide de l’outil de tableau de bord et suivez le fichier LISEZMOI pour ingérer les journaux CDN. Comme illustré dans les captures d’écran suivantes, sélectionnez la période appropriée, l’environnement approprié et les filtres appropriés.

   ![Sélectionner l’heure dans le tableau de bord](/help/security/assets/dashboard-select-time.png)

   ![Sélection de l’environnement dans le tableau de bord](/help/security/assets/dashboard-select-env.png)

1. Une fois les filtres adéquats appliqués, vous devriez pouvoir voir un tableau de bord chargé avec les données attendues. Dans la capture d’écran ci-dessous, l’exemple de règle de log a été déclenché 3 fois au cours des deux dernières heures, par la même adresse IP située en Irlande, à l’aide d’un navigateur web et d’une URL.

   ![Affichage des données du tableau de bord de développement](/help/security/assets/dashboard-see-data-logmode.png)
   ![Affichage des widgets de données du tableau de bord de développement](/help/security/assets/dashboard-see-data-logmode2.png)

1. Modifiez maintenant cdn.yaml pour mettre la règle en mode bloc afin de vous assurer que les pages sont bloquées, comme prévu. Ensuite, validez, poussez et déclenchez le pipeline de configuration comme vous l’avez fait précédemment.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
       # Log request on simple path
       - name: log-rule-example
         when:
           allOf:
             - reqProperty: tier
               matches: "author|publish"
             - reqProperty: path
               equals: '/log/me'
         action: block
   ```

1. Une fois votre configuration déployée, essayez d’accéder à https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me à l’aide de votre navigateur web ou avec la commande curl ci-dessous. Une page d’erreur 406 doit s’afficher, indiquant que la demande a été bloquée.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. Une fois de plus, téléchargez vos journaux CDN dans Cloud Manager (remarque : il peut s’écouler jusqu’à 5 minutes avant que les nouvelles requêtes soient exposées dans vos journaux CDN) et importez-les dans l’outil de tableau de bord comme nous l’avons fait précédemment. Une fois cette opération terminée, actualisez votre tableau de bord. Comme vous pouvez le voir dans la capture d’écran ci-dessous, les demandes à /log/me sont bloquées par notre règle.

   ![Affichage des données du tableau de bord de la prod](/help/security/assets/dashboard-see-data-blockmode.png)
   ![Affichage des données du tableau de bord de la prod](/help/security/assets/dashboard-see-data-blockmode2.png)

1. Si les filtres de trafic WAF sont activés (cela nécessitera une licence supplémentaire une fois la fonction GA activée), répétez avec une règle de filtre de trafic WAF, en mode journal, et déployez les règles.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
         - name: log-waf-flags
           when:
             reqProperty: tier
             matches: "author|publish"
           action:
             type: log
             wafFlags:
                 - SANS
                 - SIGSCI-IP
                 - TORNODE
                 - NOUA
                 - SCANNER
                 - USERAGENT
                 - PRIVATEFILE
                 - ABNORMALPATH
                 - TRAVERSAL
                 - NULLBYTE
                 - BACKDOOR
                 - LOG4J-JNDI
                 - SQLI
                 - XSS
                 - CODEINJECTION
                 - CMDEXE
                 - NO-CONTENT-TYPE
                 - UTF8
   ```

1. Utilisez un outil comme [nikto](https://github.com/sullo/nikto/tree/master) pour générer des requêtes correspondantes. La commande ci-dessous enverra environ 550 demandes malveillantes en moins d’une minute.

   ```
   ./nikto.pl -useragent "MyAgent (Demo/1.0)" -D V -Tuning 9 -ssl -h https://publish-pXXXXX-eYYYYY.adobeaemcloud.com
   ```

1. Téléchargez les journaux CDN depuis Cloud Manager (n’oubliez pas qu’ils peuvent prendre jusqu’à 5 minutes pour s’afficher) et vérifiez que les règles déclarées correspondantes et les indicateurs WAF s’affichent.

   Comme vous pouvez le voir, plusieurs des demandes produites par Nikto sont signalées par le WAF comme étant malveillantes. Nous pouvons voir que Nikto a essayé d&#39;exploiter les vulnérabilités CMDEXE, SQLI et NULLBYTE. Si vous modifiez maintenant l’action du journal pour bloquer et déclencher à nouveau une analyse à l’aide de Nikto, toutes les requêtes précédemment marquées seront bloquées cette fois-ci.

   ![Affichage des données WAF](/help/security/assets/dashboard-see-data-waf.png)


   Notez que chaque fois qu’une requête correspond à l’un des indicateurs WAF, ces indicateurs WAF s’affichent, même s’ils ne font pas partie de la règle déclarée. Vous êtes donc toujours conscient du trafic potentiellement malveillant pour lequel vous n’avez pas encore déclaré de règles correspondantes. Par exemple :

   ```
   "rules": "match=log-waf-flags,waf=SQLI,action=blocked"
   ```

1. Répétez cette opération avec une règle qui utilise la limitation de débit, en mode journal. Comme toujours, validez, poussez et déclenchez le pipeline de configuration pour appliquer votre configuration.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
         - name: limit-requests-client-ip
           when:
             reqProperty: tier
             matches: "author|publish"
           rateLimit:
             limit: 10
             window: 1
             penalty: 60
             groupBy:
               - reqProperty: clientIp
           action: log
   ```

1. Utilisez un outil comme [Vegeta](https://github.com/tsenart/vegeta) pour générer le trafic.

   ```
   echo "GET https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com" | vegeta attack -duration=5s
   ```

1. Après avoir exécuté l’outil, vous pouvez télécharger les journaux CDN et les ingérer dans le tableau de bord pour vérifier que la règle du limiteur de taux a été déclenchée.

   Maintenant que vous connaissez le fonctionnement des règles de filtrage du trafic, vous pouvez passer à l’environnement prod.

### Déploiement de règles dans l’environnement prod {#dashboard-prod-env}

Veillez à déclarer initialement des règles en mode journal pour vérifier qu’il n’y a pas de faux positifs, ce qui signifie que le trafic légitime serait incorrectement bloqué.

1. Créez un pipeline de configuration de production associé à votre environnement de production.

1. Copiez les règles recommandées ci-dessous dans votre cdn.yaml. Vous pouvez modifier les règles en fonction des caractéristiques uniques du trafic en direct de votre site web. Validez, poussez et déclenchez votre pipeline de configuration. Assurez-vous que les règles sont en mode journal.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    #  Block client for 5m when it exceeds 100 req/sec on a time window of 1sec
    - name: limit-requests-client-ip
      when:
        reqProperty: path
        like: '*'
      rateLimit:
        limit: 100
        window: 1
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
      # Block requests coming from OFAC countries
      - name: block-ofac-countries
        when:
          allOf:
            - { reqProperty: tier, equals: publish }
            - reqProperty: clientCountry
              in:
                - SY
                - BY
                - MM
                - KP
                - IQ
                - CD
                - SD
                - IR
                - LR
                - ZW
                - CU
                - CI
        action: block
        # Enable recommended WAF protections (only works if WAF is enabled for your environment)
        - name: block-waf-flags-globally
          when:
            reqProperty: tier
            matches: "author|publish"
          action:
            type: block
            wafFlags:
              - SANS
              - SIGSCI-IP
              - TORNODE
              - NOUA
              - SCANNER
              - USERAGENT
              - PRIVATEFILE
              - ABNORMALPATH
              - TRAVERSAL
              - NULLBYTE
              - BACKDOOR
              - LOG4J-JNDI
              - SQLI
              - XSS
              - CODEINJECTION
              - CMDEXE
              - NO-CONTENT-TYPE
              - UTF8
        # Disable protection against CMDEXE on /bin
        - name: allow-cdmexe-on-root-bin
          when:
            allOf:
              - reqProperty: tier
                matches: "author|publish"
              - reqProperty: path
                matches: "^/bin/.*"
          action:
            type: allow
            wafFlags:
              - CMDEXE
```

1. Ajoutez d’autres règles pour bloquer le trafic malveillant que vous connaissez. Par exemple, certaines adresses IP qui ont attaqué votre site.

1. Au bout de quelques minutes, heures ou jours, selon le volume de trafic de votre site, téléchargez les journaux CDN depuis Cloud Manager et analysez-les à l’aide du tableau de bord.

1. Voici quelques considérations à prendre en compte :
   1. Les règles déclarées de correspondance du trafic apparaissent dans les graphiques et les journaux de requêtes afin que vous puissiez facilement vérifier si vos règles déclarées sont déclenchées.
   1. Les indicateurs WAF correspondant au trafic apparaissent dans les graphiques et les journaux de requêtes, même si vous ne les avez pas connectés dans une règle. Cela vous permet de toujours être conscient d’un nouveau trafic malveillant potentiel et de créer de nouvelles règles si nécessaire. Examinez les indicateurs WAF qui ne sont pas reflétés dans les règles déclarées et envisagez de les déclarer.
   1. Pour les règles correspondantes, examinez les journaux de requêtes à la recherche de faux positifs et vérifiez si vous pouvez les filtrer hors des règles. Par exemple, ils sont peut-être faux positifs uniquement pour certains chemins.

1. Définissez les règles appropriées pour le mode bloc et envisagez également d’ajouter des règles supplémentaires. Certaines des règles doivent peut-être rester en mode journal lorsque vous analysez davantage avec plus de trafic.

1. Redéployer la configuration

1. Interrompez et analysez fréquemment les tableaux de bord.


---
title: Règles de filtre de trafic incluant des règles WAF
description: Configuration des règles de filtrage du trafic y compris les règles de pare-feu d’applications web (WAF)
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
source-git-commit: 00d3323be28fe12729204ef00e336c7a4c63cda7
workflow-type: tm+mt
source-wordcount: '3480'
ht-degree: 2%

---


# Règles de filtre de trafic incluant des règles WAF {#traffic-filter-rules-including-waf-rules}

>[!NOTE]
>Cette fonctionnalité sera bientôt disponible dans les environnements de développement, avec un déploiement progressif en novembre dans les environnements d’évaluation et de production. Vous pouvez demander un accès anticipé sur la scène et la production en envoyant un courrier électronique. **aemcs-waf-adopter@adobe.com**.

Les règles de filtrage du trafic peuvent être utilisées pour bloquer ou autoriser les requêtes au niveau de la couche CDN, ce qui peut s’avérer utile dans des scénarios tels que :

* Limitation de l’accès à des domaines spécifiques au trafic interne de l’entreprise, avant la mise en service d’un nouveau site
* Définition de limites de taux afin d’être moins sensible aux attaques par déni de service (DoS) volumétriques
* Empêcher les adresses IP connues pour être malveillantes de cibler vos pages

La plupart de ces règles de filtrage du trafic sont disponibles pour tous les clients as a Cloud Service de Sites et Forms AEM. Elles fonctionnent principalement sur les propriétés de requête et les en-têtes de requête, notamment l’adresse IP, le nom d’hôte, le chemin d’accès et l’agent utilisateur.

Une sous-catégorie de règles de filtrage du trafic nécessite une licence de sécurité améliorée ou une licence de protection WAF-DDoS. Elle sera disponible plus tard cette année. Ces règles puissantes sont connues sous le nom de règles de filtre de trafic WAF (Web Application Firewall) (ou règles WAF, en abrégé) et ont accès aux [Indicateurs WAF](#waf-flags-list) décrits plus loin dans cet article.

Les règles de filtrage du trafic peuvent être déployées par le biais de pipelines de configuration de Cloud Manager vers des types d’environnements de développement, d’évaluation et de production dans des programmes de production (hors environnements de test). La prise en charge des RDE sera assurée à l’avenir.

## Organisation de cet article {#how-organized}

Cet article est organisé en sections suivantes :

* **Présentation de la protection du trafic :** Découvrez comment vous êtes protégé contre le trafic malveillant.
* **Processus suggéré pour la configuration des règles :** Découvrez une méthodologie de haut niveau pour la protection de votre site web.
* **Configuration :** Découvrez comment configurer, configurer et déployer des règles de filtrage du trafic, y compris des règles WAF avancées.
* **Syntaxe des règles :** Découvrez comment déclarer des règles de filtre de trafic dans la variable `cdn.yaml` fichier de configuration. Cela inclut les règles de filtrage du trafic disponibles pour tous les clients Sites et Forms, ainsi que la sous-catégorie des règles WAF pour ceux qui détiennent une licence pour cette fonctionnalité.
* **Exemples de règles :** Consultez des exemples de règles déclarées pour vous mettre en route.
* **Règles de limite de taux :** Découvrez comment utiliser des règles de limitation de débit pour protéger votre site contre les attaques à volume élevé.
* **Journaux CDN :** Découvrez les règles déclarées et les indicateurs WAF qui correspondent à votre trafic.
* **Outils de tableau de bord :** Analysez vos journaux CDN pour obtenir de nouvelles règles de filtrage du trafic.
* **Règles de démarrage recommandées :** Ensemble de règles avec lesquelles commencer.
* **Tutoriel :** Connaissances pratiques relatives à la fonctionnalité, notamment comment utiliser les outils de tableau de bord pour déclarer les règles appropriées.

Nous vous invitons à faire part de vos commentaires ou à poser des questions sur les règles de filtrage de trafic en envoyant un courrier électronique. **aemcs-waf-adopter@adobe.com**.

## Présentation de la protection du trafic {#traffic-protection-overview}

Dans le paysage numérique actuel, le trafic malveillant est une menace omniprésente. Nous reconnaissons la gravité du risque et proposons plusieurs approches pour protéger les applications client et atténuer les attaques lorsqu’elles se produisent.

À la périphérie, le réseau de diffusion de contenu géré par l’Adobe absorbe les attaques DoS sur la couche réseau (couches 3 et 4), y compris les attaques par inondation et par reflux/amplification.

Par défaut, Adobe prend des mesures pour empêcher la dégradation des performances en raison de l’explosion inattendue d’un trafic élevé au-delà d’un certain seuil. En cas d’attaque du déni de service affectant la disponibilité du site, les équipes d’exploitation de l’Adobe sont alertées et prennent des mesures pour l’atténuer.

Les clients peuvent prendre des mesures proactives pour limiter les attaques de couche d’application (couche 7) en configurant des règles à différents niveaux du flux de diffusion de contenu.

Par exemple, au niveau de la couche Apache, les clients peuvent configurer l’une des options suivantes : [module dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#configuring-access-to-content-filter) ou [ModSecurity](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection.html?lang=en) pour limiter l’accès à certains contenus.

Comme le décrit cet article, les règles de filtrage du trafic peuvent être déployées sur le réseau de diffusion de contenu géré par Adobe à l’aide du pipeline de configuration de Cloud Manager. Outre les règles de filtrage du trafic basées sur des propriétés telles que l’adresse IP, le chemin et les en-têtes, ou des règles basées sur la définition de limites de taux, les clients peuvent également acquérir sous licence une puissante sous-catégorie de règles de filtrage du trafic appelées règles WAF.

## Processus suggéré {#suggested-process}

Voici un processus de bout en bout recommandé de haut niveau pour obtenir les règles de filtrage de trafic appropriées :

1. Configurez les pipelines de configuration hors production et en production, comme décrit dans la section [Configuration](#setup) .
1. Les clients qui possèdent une licence pour la sous-catégorie des règles de filtrage du trafic de WAF doivent les activer dans Cloud Manager.
1. Lisez et testez le tutoriel pour comprendre concrètement comment utiliser les règles de filtrage du trafic, y compris les règles WAF si elles ont été sous licence. Ce tutoriel vous guide tout au long des étapes du déploiement de règles dans un environnement de développement, de la simulation du trafic malveillant et du téléchargement de la variable [Journaux CDN](#cdn-logs)et les analyser dans [Outils du tableau de bord](#dashboard-tooling).
1. Copiez les règles de démarrage recommandées dans `cdn.yaml` et déployez la configuration dans l’environnement de production en mode journal.
1. Après avoir collecté du trafic, analysez les résultats à l’aide de [Outils du tableau de bord](#dashboard-tooling) pour voir s’il y avait des correspondances. Recherchez les faux positifs et effectuez les réglages nécessaires, en activant au final les règles de démarrage en mode bloc.
1. Ajoutez des règles personnalisées basées sur l’analyse des journaux du réseau de diffusion de contenu, d’abord en testant avec du trafic simulé sur les environnements de développement avant de procéder au déploiement dans les environnements intermédiaire et de production en mode journal, puis en mode bloc.
1. Surveillez le trafic de manière continue, en apportant des modifications aux règles à mesure que le paysage de la menace évolue.

## Configuration {#setup}

1. Tout d’abord, créez la structure de dossiers et de fichiers suivante dans le dossier de niveau supérieur de votre projet dans Git :

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

La variable `kind` doit être défini sur `CDN` et la version doit être définie sur la version du schéma, qui est actuellement `1`. Voir les exemples ci-dessous.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. Si les règles WAF sont sous licence, vous devez activer la fonctionnalité dans Cloud Manager, comme décrit ci-dessous pour les scénarios de programme nouveaux et existants.

   1. Pour configurer le WAF sur un nouveau programme, cochez la case **Protection WAF-DDOS** de la boîte de dialogue **Sécurité** lorsque vous [ajoutez un programme de production.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

   1. Pour configurer le WAF sur un programme existant, procédez comme suit : [modification de votre programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) et sur le **Sécurité** désélectionnez ou cochez la case **WAF-DDOS** à tout moment.

1. Pour les types d’environnements autres que RDE, créez un pipeline de configuration de déploiement ciblé dans Cloud Manager.

   * [Consultez ce document pour les pipelines de production.](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [Consultez ce document pour les pipelines hors production.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

Pour les RDE, la ligne de commande sera utilisée, mais RDE n’est pas pris en charge pour le moment.

**Remarques**

* Vous pouvez utiliser `yq` pour valider localement la mise en forme YAML de votre fichier de configuration (par exemple, `yq cdn.yaml`).

## Syntaxe des règles de filtre de trafic {#rules-syntax}

Vous pouvez configurer `traffic filter rules` pour établir une correspondance sur des modèles tels que les adresses IP, l’agent utilisateur, les en-têtes de requête, le nom d’hôte, la zone géographique et l’URL.

Les clients qui détiennent une licence pour l’offre de sécurité améliorée ou de protection WAF-DDoS peuvent également configurer une catégorie spéciale de règles de filtrage du trafic appelée `WAF traffic filter rules` (ou règles WAF pour abréger) qui font référence à une ou plusieurs règles [Indicateurs WAF](#waf-flags-list).

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

Format des règles de filtrage du trafic dans la variable `cdn.yaml` est décrit ci-dessous. Voir quelques [autres exemples](#examples) dans une section ultérieure, ainsi qu’une section distincte sur [Règles de limite de taux](#rate-limit-rules).


| **Propriété** | **La plupart des règles de filtrage de trafic** | **Règles de filtre de trafic WAF** | **Type** | **Valeur par défaut** | **Description** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Nom de règle (64 caractères, ne peut contenir que des caractères alphanumériques et - ) |
| when | X | X | `Condition` | - | La structure de base est la suivante :<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[Voir Syntaxe de la structure de condition](#condition-structure) ci-dessous, qui décrit les getters, les prédicats et comment combiner plusieurs conditions. |
| action | X | X | `Action` | log | log, allow, block ou Action. Le journal par défaut |
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
| reqProperty | `string` | Propriété de requête.<br><br>L’une des :<br><ul><li>`path`: renvoie le chemin complet d’une URL sans les paramètres de requête.</li><li>`queryString`: renvoie la partie requête d’une URL</li><li>`method`: renvoie la méthode HTTP utilisée dans la requête.</li><li>`tier`: renvoie l’un de `author`, `preview` ou `publish`.</li><li>`domain`: renvoie la propriété de domaine (telle que définie dans la variable `Host` en-tête) en minuscules</li><li>`clientIp`: renvoie l’adresse IP du client.</li><li>`clientCountry`: renvoie un code à deux lettres ([https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) qui identifient le pays dans lequel se trouve le client.</li></ul> |
| reqHeader | `string` | Renvoie l’en-tête de requête avec le nom spécifié |
| queryParam | `string` | Renvoie le paramètre de requête avec le nom spécifié |
| reqCookie | `string` | Renvoie le cookie avec le nom spécifié |
| postParam | `string` | Renvoie le paramètre de publication avec le nom spécifié du corps de la requête. Fonctionne uniquement lorsque le corps est de type de contenu `application/x-www-form-urlencoded` |

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

**Remarques**

* La propriété request `clientIp` ne peut être utilisé qu’avec les prédicats suivants : `equals`, `doesNotEqual`, `in`, `notIn`. `clientIp` peut également être comparé à des plages d’adresses IP lors de l’utilisation de `in` et `notIn` prédicats. L’exemple suivant met en oeuvre une condition pour évaluer si une adresse IP du client se trouve dans la plage d’adresses IP 192.168.0.0/24 (de 192.168.0.0 à 192.168.0.255) :

```
when:
  reqProperty: clientIp
  in: [ "192.168.0.0/24" ]
```

* Nous vous recommandons d’utiliser [regex101](https://regex101.com/) et [Fastly Fiddle](https://fiddle.fastly.dev/) lorsque vous utilisez l’expression régulière. Vous pouvez également en savoir plus sur la façon dont Fastly gère l’expression régulière dans ce [article](https://developer.fastly.com/reference/vcl/regex/#best-practices-and-common-mistakes).


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

La variable `wafFlags` , qui peut être utilisée dans les règles de filtre de trafic WAF concédable, peut faire référence aux éléments suivants :

| **Identifiant d’indicateur** | **Nom de l’indicateur** | **Description** |
|---|---|---|
| SQLI | Injection SQL | SQL Injection est une tentative d’accès à une application ou d’obtention d’informations privilégiées en exécutant des requêtes de base de données arbitraires. |
| ARRIÈRE-PLAN | backdoor | Un signal backdoor est une requête qui tente de déterminer si un fichier backdoor commun est présent sur le système. |
| CMDEXE | Exécution de commande | L’exécution de commande est une tentative de contrôle ou d’endommagement d’un système cible par le biais de commandes système arbitraires par le biais d’entrées utilisateur. |
| XSS | Scripts intersites | Les scripts intersites consistent à tenter de détourner un compte d’utilisateur ou une session de navigation Web par le biais d’un code JavaScript malveillant. |
| TRAVERSAL | Directory Traversal | Directory Traversal est une tentative de navigation dans des dossiers privilégiés à travers un système dans l’espoir d’obtenir des informations sensibles. |
| USERAGENT | Outils d’attaque | L’outil d’attaque est l’utilisation de logiciels automatisés pour identifier des vulnérabilités de sécurité ou pour tenter d’exploiter une vulnérabilité découverte. |
| LOG4J-JNDI | JNDI Log4J | Les attaques JNDI de Log4J tentent d’exploiter la variable [Vulnérabilité de Log4Shell](https://en.wikipedia.org/wiki/Log4Shell) présente dans les versions de Log4J antérieures à la version 2.16.0 |
| BHH | En-têtes de saut inappropriés | Les en-têtes de saut incorrects indiquent une tentative de contrebande HTTP via un en-tête de transcodage (TE) ou de longueur de contenu (CL) mal formé, ou un en-tête de TE et de CL bien formé. |
| ABNORMALPATH | Chemin anormal | Chemin anormal indique que le chemin d’origine diffère du chemin normalisé (par exemple, `/foo/./bar` est normalisé en `/foo/bar`) |
| DOUBLEENCODING | Codage double | Le codage double vérifie la technique d’évasion du double encodage des caractères HTML. |
| NOTUTF8 | Codage non valide | Un encodage non valide peut entraîner la traduction par le serveur de caractères malveillants d’une requête dans une réponse, provoquant un déni de service ou un XSS. |
| JSON-ERROR | Erreur de codage JSON | Corps de requête de POST, de PUT ou de PATCH spécifié comme contenant JSON dans l’en-tête de requête &quot;Content-Type&quot;, mais contenant des erreurs d’analyse JSON. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |
| MALFORMED-DATA | Données incorrectes dans le corps de la requête | Corps de requête de POST, de PUT ou de PATCH incorrect selon l’en-tête de requête &quot;Content-Type&quot;. Par exemple, si un en-tête de requête &quot;Content-Type: application/x-www-form-urlencoded&quot; est spécifié et contient un corps de POST qui est json. Il s’agit souvent d’une erreur de programmation, d’une requête automatisée ou malveillante. Nécessite l’agent 3.2 ou version ultérieure. |
| SANS | Trafic IP malveillant | [Centre des tempêtes sur Internet SANS](https://isc.sans.edu/) liste des adresses IP qui ont été signalées comme ayant participé à une activité malveillante |
| SIGSCI-IP | Effet réseau | IP marquée par SignalSciences : chaque fois qu’une adresse IP est marquée en raison d’un signal malveillant du moteur de décision, cette adresse IP est propagée à tous les clients. Les demandes suivantes provenant de ces adresses IP qui contiennent un signal supplémentaire pour la durée de l’indicateur sont ensuite consignées. |
| NO-CONTENT-TYPE | En-tête de requête &quot;Content-Type&quot; manquant | Requête de POST, de PUT ou de PATCH ne comportant pas d’en-tête de requête &quot;Content-Type&quot;. Par défaut, les serveurs d’applications doivent assumer &quot;Content-Type: text/plain; charset=us-ascii&quot; dans ce cas. De nombreuses demandes automatisées et malveillantes peuvent ne pas disposer du &quot;type de contenu&quot;. |
| NOUA | Aucun agent utilisateur | De nombreuses requêtes automatisées et malveillantes utilisent des agents utilisateur faux ou manquants pour rendre difficile l’identification du type d’appareil qui effectue les requêtes. |
| TORNODE | Trafic Tor | Tor est un logiciel qui cache l&#39;identité d&#39;un utilisateur. Un pic de trafic Tor peut indiquer qu’un attaquant essaie de masquer sa localisation. |
| NULLBYTE | Octet nul | Les octets nuls n’apparaissent généralement pas dans une requête et indiquent que la requête est incorrecte et potentiellement malveillante. |
| PRIVATEFILE | Fichiers privés | Les fichiers privés sont généralement de nature confidentielle, par exemple un Apache `.htaccess` ou un fichier de configuration susceptible de faire fuiter des informations sensibles. |
| SCANNER | Scanner | Identifie les services et outils d’analyse les plus utilisés |
| RESPONSESPLIT | Fractionnement des réponses HTTP | Identifie le moment où les caractères CRLF sont envoyés en entrée de l’application pour injecter des en-têtes dans la réponse HTTP. |
| XML-ERROR | Erreur de codage XML | Corps de requête de POST, de PUT ou de PATCH spécifié comme contenant du code XML dans l’en-tête de requête &quot;Content-Type&quot;, mais contenant des erreurs d’analyse XML. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |

## Considérations {#considerations}

* Lorsque deux règles en conflit sont créées, les règles d’autorisation ont toujours la priorité sur les règles de blocage. Par exemple, si vous créez une règle pour bloquer un chemin spécifique et une règle pour autoriser une adresse IP spécifique, les demandes de cette adresse IP sur le chemin bloqué seront autorisées.

* Si une règle est mise en correspondance et bloquée, le réseau de diffusion de contenu répond par une `406` code de retour.

* Les fichiers de configuration ne doivent pas contenir de secrets, car ils seront lisibles par toute personne ayant accès au référentiel git.

* Les Listes autorisées IP définies dans Cloud Manager sont prioritaires sur les règles de filtrage du trafic.

## Exemples de règles {#examples}

Voici quelques exemples de règles. Voir [section limite de taux](#rules-with-rate-limits) plus bas pour des exemples de règles de limite de taux.

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
        when:
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

Cette règle bloque les demandes de chemin d’accès `/block-me`et bloque chaque requête qui correspond à un `SQLI` ou `XSS` modèle. Cet exemple comprend des règles de filtrage du trafic WAF, qui font référence à la variable `SQLI` et `XSS` [Indicateurs WAF](#waf-flags-list), et requiert donc une licence distincte.

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

## Règles de limite de taux {#rate-limits-rules}

Il est parfois souhaitable de bloquer le trafic s’il dépasse un certain taux de requêtes entrantes, peut-être selon une condition spécifique. Définir une valeur pour la variable `rateLimit` limite le taux de requêtes correspondant à la condition de la règle.

Les règles de limite de taux ne peuvent pas faire référence aux indicateurs WAF. Ils sont disponibles pour tous les clients Sites et Forms.

Les limites de taux sont calculées par réseau CDN POP. Supposons, par exemple, que les POP de Montréal, Miami et Dublin connaissent des taux de trafic de 80, 90 et 120 demandes par seconde, respectivement, et que la règle de limite de taux soit définie sur une limite de 100. Dans ce cas, seul le trafic vers Dublin serait limité.

### Structure rateLimit {#ratelimit-structure}

| **Propriété** | **Type** | **Par défaut** | **SIGNIFICATION** |
|---|---|---|---|
| limit | entier compris entre 10 et 10 000 | obligatoire | Taux de requêtes (par POP CDN) dans les requêtes par seconde pour lesquelles la règle est déclenchée. |
| window | nombre entier : 1, 10 ou 60 | 10 | Fenêtre d’échantillonnage en secondes pour laquelle le taux de requête est calculé. La précision des compteurs dépend de la taille de la fenêtre (plus grande précision de la fenêtre). Par exemple, on peut s’attendre à une précision de 50 % pour la fenêtre d’une seconde et de 90 % pour la fenêtre de 60 secondes. |
| pénalité | entier compris entre 60 et 3 600 | 300 (5 minutes) | Période en secondes pendant laquelle les requêtes correspondantes sont bloquées (arrondie à la minute la plus proche). |
| groupBy | tableau[Getter] | Aucune | le compteur de limiteurs de débit sera agrégé par un ensemble de propriétés de requête (par exemple, clientIp). |


### Exemples {#ratelimiting-examples}

**Exemple 1**

Cette règle bloque un client pendant 5 m lorsqu’il dépasse 100 req/s (par CDN POP) dans les 60 dernières secondes :

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
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Exemple 2**

Bloquez les demandes pendant 60 s sur le chemin /critique/resource lorsqu’il dépasse 100 req/s (par CDN POP) dans les 60 dernières secondes :

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

AEM as a Cloud Service permet d’accéder aux journaux du réseau de diffusion de contenu, qui sont utiles pour les cas d’utilisation, notamment l’optimisation du rapport d’accès au cache et la configuration des règles de filtrage du trafic. Les journaux CDN s’affichent dans Cloud Manager **Journaux de téléchargement** lors de la sélection du service Auteur ou Publier.

Notez que les journaux CDN peuvent être retardés jusqu’à 5 minutes.

La variable `rules` décrit les règles de filtre de trafic correspondantes et présente le modèle suivant :

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Par exemple :

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

Les règles se comportent comme suit :

* Le nom de règle déclaré par le client de toutes les règles correspondantes sera répertorié dans la variable `match` attribut.
* La variable `action` détermine si les règles ont eu pour effet de bloquer, autoriser ou consigner.
* Si le WAF est sous licence et activé, la variable `waf` répertorie tous les indicateurs WAF (par exemple, SQLI) détectés, que les indicateurs WAF aient été répertoriés dans des règles ou non. Cela permet de fournir des informations sur les nouvelles règles potentielles à déclarer.
* Si aucune correspondance de règles déclarées par le client et aucune correspondance de règles Waf, la variable `rules` est vide.

En règle générale, les règles correspondantes apparaissent dans l’entrée de journal pour toutes les requêtes sur le réseau de diffusion de contenu, qu’il s’agisse d’un accès, d’une transmission ou d’une absence sur le réseau de diffusion de contenu. Toutefois, les règles WAF apparaissent dans l’entrée de journal uniquement pour les requêtes au réseau de diffusion de contenu qui sont considérées comme des échecs ou des réussites CDN, mais pas pour les accès CDN.

L’exemple ci-dessous illustre un exemple `cdn.yaml` et deux entrées de journal CDN :


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

## Outils de tableau de bord {#dashboard-tooling}

Adobe fournit un mécanisme de téléchargement des outils de tableau de bord sur votre ordinateur pour ingérer les journaux CDN téléchargés via Cloud Manager. Grâce à cet outil, vous pouvez analyser le trafic afin d’obtenir les règles de filtrage du trafic appropriées à déclarer, y compris les règles WAF.

Les outils des tableaux de bord peuvent être clonés directement à partir de la [AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) Référentiel Github.

[Voir le tutoriel](#tutorial) pour obtenir des instructions concrètes sur l’utilisation de l’outil de tableau de bord.

## Règles de démarrage recommandées {#recommended-starter-rules}

Vous pouvez copier les règles recommandées ci-dessous dans votre `cdn.yaml` pour commencer. Commencez en mode journal, analysez votre trafic, puis, une fois satisfait, passez en mode bloc. Vous pouvez modifier les règles en fonction des caractéristiques uniques du trafic en direct de votre site web.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
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
      action: log
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
      action: log
    # Enable recommended WAF protections (only works if WAF is licensed enabled for your environment)
    - name: block-waf-flags-globally
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
    # Disable protection against CMDEXE on /bin (only works if WAF is licensed enabled for your environment)
    - name: allow-cdmexe-on-root-bin
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            matches: "^/bin/.*"
      action:
        type: log
        wafFlags:
          - CMDEXE
```

## Tutoriel {#tutorial}

[Utilisation d’un tutoriel](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html) pour acquérir des connaissances pratiques et de l’expérience sur les règles de filtrage du trafic.

Ce tutoriel vous guide à travers :

* Configuration du pipeline de configuration de Cloud Manager
* Utilisation d’outils pour simuler le trafic malveillant
* Déclaration des règles de filtrage du trafic, y compris les règles WAF
* Analyse des résultats à l’aide des outils de tableau de bord
* Bonnes pratiques

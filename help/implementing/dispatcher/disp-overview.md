---
title: Dispatcher en mode cloud
description: 'Dispatcher en mode cloud '
feature: Dispatcher
translation-type: tm+mt
source-git-commit: c11d8e36fe8ba120847c675f40e09a0388943d51
workflow-type: tm+mt
source-wordcount: '4169'
ht-degree: 74%

---


# Dispatcher en mode cloud {#Dispatcher-in-the-cloud}

## Configuration et test d’Apache et de Dispatcher {#apache-and-dispatcher-configuration-and-testing}

Cette section décrit comment structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service. Elle explique également comment valider et exécuter le service localement avant son déploiement dans les environnements cloud. Elle présente en outre le débogage dans les environnements cloud. Pour plus d’informations sur Dispatcher, consultez la [documentation d’AEM Dispatcher](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html).

>[!NOTE]
>Les utilisateurs de Windows doivent utiliser Windows 10 Professionnel ou d&#39;autres distributions qui prennent en charge Docker. Il s’agit d’un prérequis pour l’exécution et le débogage de Dispatcher sur un ordinateur local. Les sections ci-dessous incluent des commandes utilisant les versions Mac ou Linux du SDK, mais le SDK Windows peut être utilisé de la même manière.

## Outils Dispatcher {#dispatcher-sdk}

Les outils Dispatcher font partie du SDK global d’AEM as a Cloud Service et fournissent les éléments suivants :

* Structure de fichiers vanille contenant les fichiers de configuration à inclure dans un projet expert pour le répartiteur.
* Outil permettant aux clients de vérifier que la configuration du répartiteur inclut uniquement des AEM en tant que directives prises en charge par le Cloud Service.        En outre, l’outil confirme également que la syntaxe correcte afin qu’Apache puisse démarrer correctement.
* Image Docker qui affiche le Répartiteur localement.

## Téléchargement et extraction des outils {#extracting-the-sdk}

Les outils Dispatcher, qui font partie du [SDK AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md), peuvent être téléchargés sous la forme d’un fichier zip sur le portail de [distribution de logiciels](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html). Toute nouvelle configuration disponible dans cette nouvelle version des outils du répartiteur peut être utilisée pour le déploiement sur les environnements Cloud exécutant cette version d’AEM dans le Cloud ou une version ultérieure.

Décompressez le SDK, qui regroupe les outils Dispatcher pour macOS/Linux et Windows.

**Pour macOS/Linux**, rendez l’artefact de l’outil Répartiteur exécutable et exécutez-le. Il va extraire automatiquement les fichiers des outils du répartiteur sous le répertoire dans lequel vous l&#39;avez stocké (où `version` correspond à la version des outils du répartiteur).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Pour Windows**, extrayez le fichier d’archive compressé Dispatcher Tooling.

## Structure de fichier {#file-structure}

La structure du sous-dossier Répartiteur du projet est décrite ci-dessous et doit être copiée dans le dossier Répartiteur du projet expert :

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── default.vhost -> ../available_vhosts/default.vhost
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
└── conf.dispatcher.d
    ├── available_farms
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── default.farm -> ../available_farms/default.farm
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
        ├── default_virtualhosts.any
        └── virtualhosts.any
```

Vous trouverez ci-dessous une explication des principaux fichiers qui peuvent être modifiés :

**Fichiers personnalisables**

Les fichiers suivants sont personnalisables et seront transférés vers votre instance cloud au moment du déploiement :

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

Vous pouvez avoir un ou plusieurs de ces fichiers. Ils contiennent des entrées `<VirtualHost>` qui correspondent aux noms d’hôtes et permettent à Apache de gérer chaque trafic de domaine avec des règles différentes. Les fichiers sont créés dans le répertoire `available_vhosts` et activés avec un lien symbolique dans le répertoire `enabled_vhosts`. À partir des fichiers `.vhost`, d’autres fichiers tels que les réécritures (rewrites) et les variables seront inclus.

* `conf.d/rewrites/rewrite.rules`

Ce fichier est inclus dans vos fichiers `.vhost`. Il contient un ensemble de règles de réécriture pour `mod_rewrite`.

>[!NOTE]
>
>Actuellement, un seul fichier de réécriture doit être utilisé plutôt que des fichiers spécifiques au site. En règle générale, la somme du contenu des fichiers personnalisables doit être inférieure à 1 Mo.

* `conf.d/variables/custom.vars`

Ce fichier est inclus dans vos fichiers `.vhost`. Vous pouvez y placer des définitions pour les variables Apache.

* `conf.d/variables/global.vars`

Ce fichier est inclus dans le fichier `dispatcher_vhost.conf`. Vous pouvez modifier votre Répartiteur et réécrire le niveau de journal dans ce fichier.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

Vous pouvez avoir un ou plusieurs de ces fichiers, qui contiennent des fermes pour correspondre aux noms d&#39;hôtes et permettre au module Répartiteur de gérer chaque batterie avec des règles différentes. Les fichiers sont créés dans le répertoire `available_farms` et activés avec un lien symbolique dans le répertoire `enabled_farms`. À partir des fichiers `.farm`, d’autres fichiers tels que les filtres, les règles de cache et d’autres seront inclus.

* `conf.dispatcher.d/cache/rules.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il spécifie les préférences de cache.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il spécifie les en-têtes de requête à transférer au serveur principal.

* `conf.dispatcher.d/filters/filters.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il comporte un ensemble de règles qui indiquent le trafic qui doit être filtré et ne doit pas atteindre le serveur principal.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il comporte une liste de noms d’hôtes ou de chemins d’URI à mettre en correspondance glob. Cela détermine le serveur principal à utiliser pour diffuser une requête.

Les fichiers ci-dessus font référence aux fichiers de configuration non modifiables répertoriés ci-dessous. Les modifications apportées aux fichiers immuables ne seront pas traitées par les répartiteurs dans les environnements Cloud.

**Fichiers de configuration non modifiables**

Ces fichiers font partie du framework de base. Ils respectent les normes et les bonnes pratiques. Les fichiers sont considérés comme non modifiables, car leur modification ou suppression locale n’aura aucun impact sur votre déploiement ; ils ne seront pas transférés vers votre instance cloud.

Il est recommandé que les fichiers ci-dessus fassent référence aux fichiers non modifiables répertoriés ci-dessous, suivis de toute instruction ou remplacement supplémentaire. Lorsque la configuration du répartiteur est déployée sur un environnement cloud, la dernière version des fichiers immuables est utilisée, quelle que soit la version utilisée dans le développement local.

* `conf.d/available_vhosts/default.vhost`

Contient un exemple d’hôte virtuel. Pour votre propre hôte virtuel, créez une copie de ce fichier, personnalisez-la, accédez à `conf.d/enabled_vhosts` et créez un lien symbolique vers votre copie personnalisée.

* `conf.d/dispatcher_vhost.conf`

Élément du framework de base, utilisé pour illustrer la manière dont vos hôtes virtuels et vos variables globales sont inclus.

* `conf.d/rewrites/default_rewrite.rules`

Règles de réécriture par défaut adaptées à un projet standard. Si une personnalisation est nécessaire, modifiez `rewrite.rules`. Dans votre personnalisation, vous pouvez toujours inclure les règles par défaut en premier, si elles répondent à vos besoins.

* `conf.dispatcher.d/available_farms/default.farm`

Contient un exemple de batterie de répartiteurs. Pour votre propre ferme, créez une copie de ce fichier, personnalisez-la, accédez à `conf.d/enabled_farms` et créez un lien symbolique vers votre copie personnalisée.

* `conf.dispatcher.d/cache/default_invalidate.any`

Élément du framework de base, généré au démarrage. Vous **devez** inclure ce fichier dans chaque ferme définie, au niveau de la section `cache/allowedClients`.

* `conf.dispatcher.d/cache/default_rules.any`

Règles de cache par défaut adaptées à un projet standard. Si une personnalisation est nécessaire, modifiez `conf.dispatcher.d/cache/rules.any`. Dans votre personnalisation, vous pouvez toujours inclure les règles par défaut en premier, si elles répondent à vos besoins.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

En-têtes de requête par défaut à transférer vers le serveur principal, adaptés à un projet standard. Si une personnalisation est nécessaire, modifiez `clientheaders.any`. Dans votre personnalisation, vous pouvez toujours inclure d’abord les en-têtes de requête par défaut, s’ils répondent à vos besoins.

* `conf.dispatcher.d/dispatcher.any`

Partie du cadre de base, utilisée pour illustrer comment vos fermes de répartiteurs sont incluses.

* `conf.dispatcher.d/filters/default_filters.any`

Filtres par défaut adaptés à un projet standard. Si une personnalisation est nécessaire, modifiez `filters.any`. Dans votre personnalisation, vous pouvez toujours inclure d’abord les filtres par défaut, s’ils répondent à vos besoins.

* `conf.dispatcher.d/renders/default_renders.any`

Élément du framework de base, ce fichier est généré au démarrage. Vous **devez** inclure ce fichier dans chaque ferme définie, au niveau de la section `renders`.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Extension métacaractère d’hôte par défaut adaptée à un projet standard. Si une personnalisation est nécessaire, modifiez `virtualhosts.any`. Dans votre personnalisation, vous ne devez pas inclure l’extension métacaractère d’hôte par défaut, car elle correspond à **chaque** requête entrante.

>[!NOTE]
>
>L&#39;AEM en tant qu&#39;archétype d&#39;expert Cloud Service générera la même structure de fichiers de configuration du répartiteur.

Les sections ci-dessous décrivent comment valider localement la configuration afin qu’elle puisse franchir le niveau de qualité associé dans Cloud Manager lors du déploiement d’une version interne.

## Validation locale des directives prises en charge dans la configuration Dispatcher {#local-validation-of-dispatcher-configuration}

L’outil de validation est disponible dans le SDK à l’emplacement `bin/validator` sous forme de fichier binaire Mac OS, Linux ou Windows, ce qui permet aux clients d’exécuter la même validation que celle effectuée par Cloud Manager lors de la création et du déploiement d’une version.

Il est appelé comme suit : `validator full [-d folder] [-w allowlist] zip-file | src folder`

L&#39;outil vérifie que la configuration du répartiteur utilise les directives appropriées prises en charge par AEM en tant que service Cloud en analysant tous les fichiers avec le modèle `conf.d/enabled_vhosts/*.vhost`.

Sous Windows, le programme de validation du répartiteur est sensible à la casse. Par conséquent, il peut ne pas valider la configuration si vous ne respectez pas la mise en majuscule du chemin d’accès où se trouve votre configuration, par exemple :

```
bin\validator.exe full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
  
```

Evitez cette erreur en copiant et collant le chemin d&#39;accès depuis l&#39;Explorateur Windows, puis sur l&#39;invite de commande à l&#39;aide d&#39;une commande `cd` dans ce chemin d&#39;accès.

Les directives autorisées dans les fichiers de configuration Apache peuvent être répertoriées en exécutant la commande de liste autorisée du programme de validation :

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

Le tableau ci-dessous présente les modules Apache pris en charge :

| Nom du module | Page de référence |
|---|---|
| `core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_authn_core` | [https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html) |
| `mod_authn_file` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_file.html) |
| `mod_authz_core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) |
| `mod_authz_groupfile` | [https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html) |
| `mod_deflate` | [https://httpd.apache.org/docs/2.4/mod/mod_deflate.html](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html) |
| `mod_dir` | [https://httpd.apache.org/docs/2.4/mod/mod_dir.html](https://httpd.apache.org/docs/2.4/mod/mod_dir.html) |
| `mod_env` | [https://httpd.apache.org/docs/2.4/mod/mod_env.html](https://httpd.apache.org/docs/2.4/mod/mod_env.html) |
| `mod_filter` | [https://httpd.apache.org/docs/2.4/mod/mod_filter.html](https://httpd.apache.org/docs/2.4/mod/mod_filter.html) |
| `mod_headers` | [https://httpd.apache.org/docs/2.4/mod/mod_headers.html](https://httpd.apache.org/docs/2.4/mod/mod_headers.html) |
| `mod_mime` | [https://httpd.apache.org/docs/2.4/mod/mod_mime.html](https://httpd.apache.org/docs/2.4/mod/mod_mime.html) |
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

Les clients ne peuvent pas ajouter de modules arbitraires, mais des modules supplémentaires peuvent être envisagés pour inclusion dans le produit à l’avenir. Pour obtenir la liste des directives disponibles pour une version de Dispatcher donnée, les clients peuvent exécuter la commande de liste autorisée du programme de validation dans le SDK, comme décrit ci-dessus.

La liste autorisée contient la liste des directives Apache autorisées dans une configuration client. Si une directive n’est pas placée sur la liste autorisée, l’outil consigne une erreur et renvoie un code de sortie non nul. Si aucune liste autorisée n’est fournie sur la ligne de commande (c’est-à-dire de la manière dont elle doit être appelée), l’outil utilise une liste autorisée par défaut que Cloud Manager utilisera pour la validation avant de procéder au déploiement dans les environnements cloud.

Il analyse également tous les fichiers présentant le motif `conf.dispatcher.d/enabled_farms/*.farm` et vérifie les éléments suivants :

* Absence de règle de filtre utilisant l’opérateur allow via `/glob` (voir [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) pour plus d’informations)
* Aucune fonction d’administration n’est exposée. Par exemple, l’accès aux chemins tels que `/crx/de or /system/console`.

Lorsqu’il est exécuté sur votre artefact maven ou votre sous-répertoire `dispatcher/src`, il signale les échecs de validation :

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Notez que l’outil de validation ne signale que l’utilisation interdite des directives Apache qui n’ont pas été placées sur la liste autorisée. Il ne signale aucun problème de syntaxe ni de sémantique dans votre configuration Apache, car ces informations ne sont disponibles que pour les modules Apache dans un environnement en cours d’exécution.

Les techniques de dépannage présentées ci-dessous permettent de déboguer les erreurs de validation courantes qui sont générées par l’outil :

**unable to locate a `conf.dispatcher.d` subfolder in the archive**

Votre archive doit contenir les dossiers `conf.d` et `conf.dispatcher.d`. Notez que vous ne devez **pas**
utiliser le préfixe `etc/httpd` dans votre archive.

**unable to find any farm in`conf.dispatcher.d/enabled_farms`**

Vos fermes doivent se trouver dans le sous-dossier mentionné.

**file included (...) must be named: ...**

Deux sections de la configuration de votre ferme **doivent** inclure
un fichier spécifique : `/renders` et `/allowedClients` dans la section `/cache`. Ces
sections doivent se présenter comme suit :

```
/renders {
    $include "../renders/default_renders.any"
}
```

et :

```
/allowedClients {
    $include "../cache/default_invalidate.any"
}
```

**file included at unknown location: ...**

Votre configuration de ferme comporte quatre sections où vous pouvez inclure votre propre fichier : `/clientheaders`, `filters`, `/rules` dans la section `/cache` et `/virtualhosts`. Les fichiers inclus doivent être nommés comme suit :

| Section | Nom du fichier d’inclusion |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

Vous pouvez également inclure la version **par défaut** de ces fichiers, dont les noms sont précédés du mot `default_`, par ex. `../filters/default_filters.any`.

**include statement at (...), outside any known location: ...**

Outre les six sections mentionnées dans les paragraphes ci-dessus, vous n’êtes pas autorisé à utiliser l’instruction `$include` ; par exemple, les éléments suivants généreraient cette erreur :

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**allowed clients/renders are not included from: ...**

Cette erreur est générée lorsque vous ne spécifiez pas d’inclusion pour `/renders` et `/allowedClients` dans la section `/cache`. Voir la section
**file included (...) must be named: ...** pour plus d’informations.

**filter must not use glob pattern to allow requests**

Il n’est pas sûr d’autoriser les requêtes avec une règle de style `/glob`, qui est mise en correspondance avec la ligne de requête complète, par exemple :

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Cette instruction est destinée à autoriser les requêtes de fichiers `css`, mais elle permet également les requêtes de **n’importe quelle** ressource suivie de la chaîne de requête `?a=.css`. Il est donc interdit d’utiliser de tels filtres (voir aussi CVE-2016-0957).

**included file (...) does not match any known file**

Il existe deux types de fichiers dans la configuration de l’hôte virtuel Apache qui peuvent être spécifiés sous la forme d’inclusions : les réécritures et les variables.
Les fichiers inclus doivent être nommés comme suit :

| Type | Nom du fichier d’inclusion |
|-----------|---------------------------------|
| Réécritures | `conf.d/rewrites/rewrite.rules` |
| Variables | `conf.d/variables/custom.vars` |

Vous pouvez également inclure la version **par défaut** des règles de réécriture, dont le nom est `conf.d/rewrites/default_rewrite.rules`.
Notez qu’il n’existe pas de version par défaut des fichiers de variables.

**Deprecated configuration layout detected, enabling compatibility mode**

Ce message indique que votre configuration présente la disposition version 1 obsolète, contenant une
configuration Apache complète et des fichiers avec des préfixes `ams_`. Bien que ceci soit toujours pris en charge pour les versions antérieures
, vous devez passer à la nouvelle mise en page.

## Validation locale de la syntaxe de configuration du répartiteur de manière à ce qu&#39;apache httpd puisse début {#local-validation}

Une fois qu&#39;il a été établi que la configuration du module Répartiteur inclut uniquement les directives prises en charge, vous devez vérifier que la syntaxe est correcte afin qu&#39;apache puisse début. Pour ce faire, Docker doit être installé localement. Il n’est pas nécessaire qu’AEM soit en cours d’exécution.

Utilisez le script `validate.sh` comme indiqué ci-dessous :

```
$ validate.sh src/dispatcher
Phase 1: Dispatcher validator
2019/06/19 16:02:55 No issues found
Phase 1 finished
Phase 2: httpd -t validation in docker image
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
...
}
Syntax OK
Phase 2 finished
```

Le script effectue les opérations suivantes :

1. Il exécute le programme de validation de la section précédente pour s’assurer que seules les directives prises en charge soient incluses. Si la configuration n’est pas valide, le script échoue.
2. Il exécute la `httpd -t command` pour tester si la syntaxe est correcte de sorte qu’Apache httpd puisse démarrer. En cas de réussite, la configuration doit être prête pour le déploiement..
3. Vérifie que le sous-ensemble des fichiers de configuration du SDK du répartiteur, qui sont censés être immuables comme décrit dans la section [Structure de fichiers](#file-structure), n&#39;a pas été modifié. Cette nouvelle vérification a été introduite avec le SDK AEM version v2021.1.4738 qui inclut également Dispatcher Tools version 2.0.36. Avant cette mise à jour, les clients auraient pu supposer à tort que toute modification locale du SDK de ces fichiers immuables est également appliquée à l’environnement cloud.

Lors d’un déploiement de Cloud Manager, la vérification `httpd -t syntax` est également exécutée et toute erreur est incluse dans le journal `Build Images step failure` de Cloud Manager.

## Test local de votre configuration Apache et Dispatcher {#testing-apache-and-dispatcher-configuration-locally}

Il est également possible de tester localement votre configuration Apache et Dispatcher. Cela nécessite que Docker soit installé localement et que votre configuration réussisse la validation comme décrit ci-dessus.

Exécutez l&#39;outil de validation (notez qu&#39;il est différent de `validator.sh` mentionné plus haut) en utilisant le paramètre `-d` qui génère un dossier avec tous les fichiers de configuration du répartiteur. Exécutez ensuite le script `docker_run.sh` en transmettant ce dossier en tant qu’argument. En indiquant le numéro de port (ici : 8080) pour exposer le point de terminaison Répartiteur, un conteneur Docker est démarré, exécutant le Répartiteur avec votre configuration.

```
$ validator full -d out src/dispatcher
2019/06/19 16:02:55 No issues found
$ docker_run.sh out docker.for.mac.localhost:4503 8080
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
Starting httpd server
...
```

Cette opération début le Répartiteur dans un conteneur dont le serveur principal pointe vers une instance AEM s’exécutant sur votre ordinateur Mac OS local au port 4503.

## Débogage de la configuration Apache et Dispatcher {#debugging-apache-and-dispatcher-configuration}

La stratégie suivante peut être utilisée pour augmenter la sortie du journal pour le module Répartiteur et voir les résultats de l&#39;évaluation `RewriteRule` dans les environnements locaux et les  de cloud.

Les niveaux de journal de ces modules sont définis par les variables `DISP_LOG_LEVEL` et `REWRITE_LOG_LEVEL`. Ils peuvent être définis dans le fichier `conf.d/variables/global.vars`. Sa partie pertinente est la suivante :

```
# Log level for the dispatcher
#
# Possible values are: Error, Warn, Info, Debug and Trace1
# Default value: Warn
#
# Define DISP_LOG_LEVEL Warn
 
# Log level for mod_rewrite
#
# Possible values are: Error, Warn, Info, Debug and Trace1 - Trace8
# Default value: Warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to Trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL Warn
```

Lors de l&#39;exécution du répartiteur en local, les journaux sont imprimés directement sur la sortie terminal. La plupart du temps, vous souhaitez que ces journaux soient en mode DEBUG, ce qui peut être réalisé en transmettant le niveau Debug comme paramètre lors de l’exécution de Docker. Par exemple : `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`.

Les journaux des environnements cloud sont exposés par le biais du service de journalisation disponible dans Cloud Manager.

## Différentes configurations Dispatcher par environnement {#different-dispatcher-configurations-per-environment}

Actuellement, la même configuration de Répartiteur est appliquée à tous les AEM en tant qu&#39;environnements Cloud Service. Le composant d’exécution comporte une variable d’environnement `ENVIRONMENT_TYPE` qui contient le mode d’exécution actuel (dev, stage ou prod) ainsi qu’une définition. La définition peut être `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` ou `ENVIRONMENT_PROD`. Dans la configuration Apache, la variable peut être utilisée directement dans une expression. Vous pouvez également utiliser la définition pour créer une logique :

```
# Simple usage of the environment variable
ServerName ${ENVIRONMENT_TYPE}.company.com
 
# When more logic is required
<IfDefine ENVIRONMENT_STAGE>
  # These statements are for stage
  Define VIRTUALHOST stage.example.com
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  # These statements are for production
  Define VIRTUALHOST prod.example.com
</IfDefine>
```

Dans la configuration Dispatcher, la même variable d’environnement est disponible. Si davantage de logique est nécessaire, définissez les variables comme illustré dans l’exemple ci-dessus, puis utilisez-les dans la section de configuration Dispatcher :

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

Lors du test local de votre configuration, vous pouvez simuler différents types d’environnements en transmettant directement la variable `DISP_RUN_MODE` au script `docker_run.sh` :

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
```

Le mode d’exécution par défaut lorsque vous ne transmettez pas de valeur pour DISP_RUN_MODE est « dev ».
Pour obtenir la liste complète des options et variables disponibles, exécutez le script `docker_run.sh` sans argument.

## Affichage de la configuration Dispatcher utilisée par votre conteneur Docker {#viewing-dispatcher-configuration-in-use-by-docker-container}

Avec les configurations spécifiques à l’environnement, il peut s’avérer difficile de déterminer à quoi ressemble la configuration Dispatcher. Après avoir démarré votre conteneur Docker avec `docker_run.sh`, vous pouvez le vider comme suit :

* Déterminez l’identifiant de conteneur Docker utilisé :

```
$ docker ps
CONTAINER ID       IMAGE
d75fbd23b29        adobe/aem-ethos/dispatcher-publish:...
```

* Exécutez la ligne de commande suivante avec cet identifiant de conteneur :

```
$ docker exec d75fbd23b29 httpd-test
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
  /publishfarm {
    /clientheaders {
...
```

## Principales différences entre AMS Dispatcher et AEM as a Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

Comme décrit dans la page de référence ci-dessus, la configuration Apache et Dispatcher dans AEM as a Cloud Service est assez similaire à celle d’AMS. Les principales différences sont :

* Dans AEM as a Cloud Service, certaines directives Apache peuvent ne pas être utilisées (par exemple, `Listen` ou `LogLevel`)
* Dans AEM as a Cloud Service, seules certaines parties de la configuration Dispatcher peuvent être placées dans les fichiers d’inclusion et les noms qui leur sont donnés sont importants. Par exemple, les règles de filtrage que vous souhaitez réutiliser sur différents hôtes doivent être placées dans un fichier nommé `filters/filters.any`. Consultez la page de référence pour plus d’informations.
* Dans AEM as a Cloud Service, il existe une validation supplémentaire pour interdire les règles de filtrage écrites avec `/glob` de façon à éviter les problèmes de sécurité. Puisque `deny *` sera utilisé plutôt que `allow *` (qui ne peut pas être utilisé), les clients auront avantage à exécuter Dispatcher localement et à procéder par tâtonnements, en examinant les journaux pour savoir exactement quels chemins sont bloqués par les filtres Dispatcher afin de pouvoir les ajouter.

## Instructions relatives à la migration de la configuration Dispatcher d’AMS vers AEM as a Cloud Service

La structure de configuration du répartiteur présente des différences entre Managed Services et AEM en tant que Cloud Service. Vous trouverez ci-dessous un guide détaillé sur la migration de la configuration Dispatcher d’AMS version 2 vers AEM as Cloud Service.

## Comment convertir un fichier AMS en un AEM en tant que configuration du répartiteur de services Cloud

La section suivante fournit des instructions détaillées sur la conversion d’une configuration AMS. Elle suppose
que vous disposez d’une archive avec une structure similaire à celle décrite dans [Configuration du répartiteur Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### Extraire l’archive et supprimer tout préfixe

Extrayez l’archive dans un dossier et assurez-vous que les noms des sous-dossiers immédiats commencent par `conf`, `conf.d`,
`conf.dispatcher.d` et `conf.modules.d`. Si tel n’est pas le cas, déplacez-les dans la hiérarchie.

### Débarrassez-vous des sous-dossiers et fichiers inutilisés

Supprimez les sous-dossiers `conf` et `conf.modules.d`, ainsi que les fichiers correspondants à `conf.d/*.conf`.

### Supprimer tous les hôtes virtuels non publiés

Supprimez tout fichier d’hôte virtuel dans `conf.d/enabled_vhosts` dont le nom inclut `author`, `unhealthy`, `health`,
`lc` ou `flush`. Tous les fichiers d’hôtes virtuels dans `conf.d/available_vhosts` non
liés peuvent également être supprimés.

### Supprimer ou mettre en commentaires les sections d’hôte virtuel qui ne font pas référence au port 80

Si des sections de vos fichiers d&#39;hôtes virtuels contiennent toujours des références exclusivement à d&#39;autres ports que le port 80, par exemple :

```
<VirtualHost *:443>
...
</VirtualHost>
```

supprimez-les ou commentez-les. Les instructions de ces sections ne seront pas traitées, mais si vous
les conservez, vous pourriez tout de même finir par les modifier sans effet, ce qui peut porter à confusion.

### Vérifier les réécritures

Entrez dans le répertoire `conf.d/rewrites`.

Supprimez tout fichier nommé `base_rewrite.rules` et `xforwarded_forcessl_rewrite.rules`, et n’oubliez pas de
supprimer les instructions `Include` dans les fichiers d’hôtes virtuels qui y font référence.

Si `conf.d/rewrites` contient maintenant un seul fichier, il doit être renommé `rewrite.rules`.
De plus, veillez à adapter également les instructions `Include` se rapportant à ce fichier dans les fichiers d’hôtes virtuels.

Si le dossier contient toutefois plusieurs fichiers spécifiques à l’hôte virtuel, leur contenu doit être
copié dans l&#39;instruction `Include` faisant référence à eux dans les fichiers hôtes virtuels.

### Vérifier les variables

Entrez dans le répertoire `conf.d/variables`.

Supprimez tout fichier nommé `ams_default.vars` et n’oubliez pas de supprimer les instructions `Include` des fichiers d’hôtes
virtuels qui y font référence.

Si `conf.d/variables` contient maintenant un seul fichier, il doit être renommé `custom.vars`.
De plus, veillez à adapter également les instructions `Include` se rapportant à ce fichier dans les fichiers d’hôtes virtuels.

Si le dossier contient toutefois plusieurs fichiers spécifiques à l’hôte virtuel, leur contenu doit être
copié dans l&#39;instruction `Include` faisant référence à eux dans les fichiers hôtes virtuels.

### Supprimer des listes autorisées

Supprimez le dossier `conf.d/whitelists` et les instructions `Include` des fichiers d’hôtes virtuels faisant référence à
un fichier de ce sous-dossier.

### Remplacer toute variable qui n’est plus disponible

Dans tous les fichiers d’hôtes virtuels :

Renommez `PUBLISH_DOCROOT` en `DOCROOT`
Supprimez les sections faisant référence à des variables nommées `DISP_ID`, `PUBLISH_FORCE_SSL` ou `PUBLISH_WHITELIST_ENABLED`

### Vérifier votre état en exécutant le programme de validation

Exécutez le programme de validation du répartiteur dans votre répertoire, avec la sous-commande `httpd` :

```
$ validator httpd .
```

Si des erreurs s’affichent au sujet de fichiers d’inclusion manquants, vérifiez si vous avez correctement renommé
les fichiers en question.

Si vous voyez des directives Apache qui ne sont pas placées sur la liste autorisée, supprimez-les.

### Supprimer toutes les fermes non publiées

Supprimez tout fichier de ferme dans `conf.dispatcher.d/enabled_farms` dont le nom inclut `author`, `unhealthy`, `health`,
`lc` ou `flush`. Tous les fichiers de fermes dans `conf.dispatcher.d/available_farms` non
liés peuvent également être supprimés.

### Renommer les fichiers de fermes

Toutes les fermes dans `conf.d/enabled_farms` doivent être renommées afin de correspondre au motif `*.farm`.
Par exemple, le fichier de ferme appelé `customerX_farm.any` doit être renommé `customerX.farm`.

### Vérifier le cache

Entrez dans le répertoire `conf.dispatcher.d/cache`.

Supprimez tout fichier portant le préfixe `ams_`.

Si `conf.dispatcher.d/cache` est désormais vide, copiez le fichier `conf.dispatcher.d/cache/rules.any`
de la configuration standard du répartiteur à ce dossier. Répartiteur standard
se trouve dans le dossier `src` de ce SDK. N’oubliez pas d’adapter également les
instructions `$include` faisant référence aux fichiers de règles `ams_*_cache.any` dans les
fichiers de fermes.

En revanche, si `conf.dispatcher.d/cache` contient maintenant un seul fichier portant le suffixe `_cache.any`,
il doit être renommé en `rules.any`. De plus, veillez à adapter les instructions `$include`
se rapportant à ce fichier dans les fichiers de fermes.

Si le dossier contient toutefois plusieurs fichiers spécifiques à une batterie de serveurs avec ce modèle, leur contenu
doit être copiée dans l&#39;instruction `$include` qui y fait référence dans les fichiers de batterie.

Supprimez tout fichier portant le suffixe `_invalidate_allowed.any`.

Copiez le fichier `conf.dispatcher.d/cache/default_invalidate_any` du fichier par défaut.
AEM dans la configuration du répartiteur de cloud à cet emplacement.

Dans chaque fichier de ferme, supprimez tout contenu de la section `cache/allowedClients` et
remplacez-le par :

```
$include "../cache/default_invalidate.any"
```

### Vérifier les en-têtes de client

Entrez dans le répertoire `conf.dispatcher.d/clientheaders`.

Supprimez tout fichier portant le préfixe `ams_`.

Si `conf.dispatcher.d/clientheaders` contient maintenant un seul fichier portant le suffixe `_clientheaders.any`,
il doit être renommé `clientheaders.any`. De plus, veillez à adapter également les instructions `$include`
se rapportant à ce fichier dans les fichiers de fermes.

Si le dossier contient toutefois plusieurs fichiers spécifiques à une batterie de serveurs avec ce modèle, leur contenu
doit être copiée dans l&#39;instruction `$include` qui y fait référence dans les fichiers de batterie.

Copiez le fichier `conf.dispatcher/clientheaders/default_clientheaders.any` du fichier par défaut.
AEM en tant que configuration Cloud Service Dispatcher à cet emplacement.

Dans chaque fichier de batterie de serveurs, remplacez toute instruction d’inclusion clientheader qui se présente comme suit :

```
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"
```

par l’instruction suivante :

```
$include "../clientheaders/default_clientheaders.any"
```

### Vérifier le filtre

Entrez dans le répertoire `conf.dispatcher.d/filters`.

Supprimez tout fichier portant le préfixe `ams_`.

Si `conf.dispatcher.d/filters` contient maintenant un seul fichier, il doit être renommé
`filters.any`. De plus, veillez à adapter également les instructions `$include` se rapportant à ce fichier dans les fichiers de fermes.

Si le dossier contient toutefois plusieurs fichiers spécifiques à une batterie de serveurs avec ce modèle, leur contenu
doit être copiée dans l&#39;instruction `$include` qui y fait référence dans les fichiers de batterie.

Copiez le fichier `conf.dispatcher/filters/default_filters.any` du fichier par défaut.
AEM en tant que configuration Cloud Service Dispatcher à cet emplacement.

Dans chaque fichier de batterie, remplacez les instructions d&#39;inclusion de filtre qui se présentent comme suit :

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

par l’instruction suivante :

```
$include "../filters/default_filters.any"
```

### Vérifier les rendus

Entrez dans le répertoire `conf.dispatcher.d/renders`.

Supprimez tous les fichiers de ce dossier.

Copiez le fichier `conf.dispatcher.d/renders/default_renders.any` du fichier par défaut.
AEM en tant que configuration Cloud Service Dispatcher à cet emplacement.

Dans chaque fichier de ferme, supprimez tout contenu de la section `renders` et
remplacez-le par :

```
$include "../renders/default_renders.any"
```

### Vérifier les hôtes virtuels

Renommez le répertoire `conf.dispatcher.d/vhosts` en `conf.dispatcher.d/virtualhosts` puis entrez dedans.

Supprimez tout fichier portant le préfixe `ams_`.

Si `conf.dispatcher.d/virtualhosts` contient maintenant un seul fichier, il doit être renommé
`virtualhosts.any`. De plus, veillez à adapter également les instructions `$include` se rapportant à ce fichier dans les fichiers de fermes.

Si le dossier contient toutefois plusieurs fichiers spécifiques à une batterie de serveurs avec ce modèle, leur contenu
doit être copiée dans l&#39;instruction `$include` qui y fait référence dans les fichiers de batterie.

Copiez le fichier `conf.dispatcher/virtualhosts/default_virtualhosts.any` du fichier par défaut.
AEM en tant que configuration Cloud Service Dispatcher à cet emplacement.

Dans chaque fichier de batterie, remplacez les instructions d&#39;inclusion de filtre qui se présentent comme suit :

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

par l’instruction suivante :

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Vérifier votre état en exécutant le programme de validation

Exécutez l&#39;AEM en tant que validateur Cloud Service Dispatcher dans votre répertoire, avec la sous-commande `dispatcher` :

```
$ validator dispatcher .
```

Si des erreurs s’affichent au sujet de fichiers d’inclusion manquants, vérifiez si vous avez correctement renommé
les fichiers en question.

Si des erreurs s’affichent concernant une variable `PUBLISH_DOCROOT` non définie, renommez-la `DOCROOT`.

Pour toute autre erreur, consultez la section Dépannage de la documentation
du programme de validation.

### Tester votre configuration avec un déploiement local (installation de Docker requise)

Avec le script `docker_run.sh` dans les outils Dispatcher AEM as a Cloud Service, vous pouvez tester si
votre configuration ne contient aucune autre erreur qui s’afficherait uniquement
dans le déploiement :

### Étape 1 : générer des informations de déploiement avec le programme de validation

```
validator full -d out .
```

Cela valide la configuration complète et génère des informations de déploiement dans `out`

### Étape 2 : Début du répartiteur dans une image de station d&#39;accueil avec ces informations de déploiement

Avec votre serveur de publication AEM exécuté sur votre ordinateur macOS, en écoutant sur le port 4503,
vous pouvez exécuter le répartiteur début devant ce serveur comme suit :

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Cela démarrera le conteneur et exposera Apache sur le port local 8080.

### Utiliser la nouvelle configuration du répartiteur

Félicitations ! Si le programme de validation ne signale plus aucun problème et
que le conteneur Docker démarre sans erreur ni avertissement, vous êtes
prêt à déplacer votre configuration vers un sous-répertoire `dispatcher/src`
de votre référentiel git.

**Les clients qui utilisent la version 1 de la configuration AMS Dispatcher doivent contacter le service clientèle pour les aider à migrer à la version 2 afin de pouvoir suivre les instructions ci-dessus.**

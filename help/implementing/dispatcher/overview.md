---
title: Dispatcher en mode cloud
description: 'Dispatcher en mode cloud '
translation-type: tm+mt
source-git-commit: b7bb84b026c9187cb633e9ccfdc17aa5ec930aff
workflow-type: tm+mt
source-wordcount: '3916'
ht-degree: 99%

---


# Dispatcher en mode cloud {#Dispatcher-in-the-cloud}

## Configuration et test d’Apache et de Dispatcher {#apache-and-dispatcher-configuration-and-testing}

Cette section décrit comment structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service. Elle explique également comment valider et exécuter le service localement avant son déploiement dans les environnements cloud. Elle présente en outre le débogage dans les environnements cloud. Pour plus d’informations sur Dispatcher, consultez la [documentation d’AEM Dispatcher](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html).

>[!NOTE]
>Les utilisateurs de Windows devront utiliser Windows 10 Professionnel ou d’autres distributions prenant en charge Docker. Il s’agit d’un prérequis pour l’exécution et le débogage de Dispatcher sur un ordinateur local. Les sections ci-dessous incluent des commandes utilisant les versions Mac ou Linux du SDK, mais le SDK Windows peut être utilisé de la même manière.

>[!WARNING]
> Utilisateurs de Windows : la version actuelle d’AEM as a Cloud Service local Dispatcher Tools (v2.0.20) est incompatible avec Windows. Contactez l’assistance [](https://daycare.day.com/home.html) Adobe pour recevoir des mises à jour sur la compatibilité avec Windows.

## Outils Dispatcher {#dispatcher-sdk}

Les outils Dispatcher font partie du SDK global d’AEM as a Cloud Service et fournissent les éléments suivants :

* Une structure de fichiers classique contenant les fichiers de configuration à inclure dans un projet maven pour Dispatcher
* Les outils permettant aux clients de valider localement une configuration de Dispatcher
* Une image du Docker qui rend Dispatcher accessible localement

## Téléchargement et extraction des outils {#extracting-the-sdk}

Les outils Dispatcher peuvent être téléchargés à partir d’un fichier ZIP sur le portail [Distribution logicielle](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html). Notez que l’accès aux listes de SDK est limité aux environnements AEM Managed Services ou AEM as a Cloud Service. Toute nouvelle configuration disponible dans cette nouvelle version des outils Dispatcher peut être utilisée pour le déploiement dans les environnements cloud exécutant cette version d’AEM en mode cloud ou une version ultérieure.

**Pour macOS et Linux**, téléchargez le script shell dans un dossier de votre ordinateur, rendez-le exécutable et exécutez-le. Il extrait automatiquement les fichiers des outils Dispatcher au sein du répertoire dans lequel vous l’avez stocké (où `version` est la version des outils Dispatcher).

```bash
$ chmod +x DispatcherSDKv<version>.sh
$ ./DispatcherSDKv<version>.sh
Verifying archive integrity...  100%   All good.
Uncompressing DispatcherSDKv<version>  100% 
```

**Pour Windows**, téléchargez l’archive ZIP et extrayez-la.

## Structure de fichier {#file-structure}

La structure du sous-dossier dispatcher du projet est décrite ci-dessous et doit être copiée dans le dossier dispatcher du projet maven :

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
>Actuellement, un seul fichier de réécriture doit être utilisé au lieu de fichiers spécifiques au site. Ce fichier doit présenter une taille inférieure à 1 Mo.

* `conf.d/variables/custom.vars`

Ce fichier est inclus dans vos fichiers `.vhost`. Vous pouvez y placer des définitions pour les variables Apache.

* `conf.d/variables/global.vars`

Ce fichier est inclus dans le fichier `dispatcher_vhost.conf`. Vous pouvez modifier votre Dispatcher et le niveau du journal des réécritures dans ce fichier.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

Vous pouvez avoir un ou plusieurs de ces fichiers. Ils contiennent des fermes correspondant aux noms d’hôtes et permettant au module Dispatcher de gérer chaque ferme avec des règles différentes. Les fichiers sont créés dans le répertoire `available_farms` et activés avec un lien symbolique dans le répertoire `enabled_farms`. À partir des fichiers `.farm`, d’autres fichiers tels que les filtres, les règles de cache et d’autres seront inclus.

* `conf.dispatcher.d/cache/rules.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il spécifie les préférences de cache.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il spécifie les en-têtes de requête à transférer au serveur principal.

* `conf.dispatcher.d/filters/filters.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il comporte un ensemble de règles qui indiquent le trafic qui doit être filtré et ne doit pas atteindre le serveur principal.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il comporte une liste de noms d’hôtes ou de chemins d’URI à mettre en correspondance glob. Cela détermine le serveur principal à utiliser pour diffuser une requête.

Les fichiers ci-dessus font référence aux fichiers de configuration non modifiables répertoriés ci-dessous. Les modifications apportées aux fichiers non modifiables ne seront pas traitées par les Dispatchers dans les environnements cloud.

**Fichiers de configuration non modifiables**

Ces fichiers font partie du framework de base. Ils respectent les normes et les bonnes pratiques. Les fichiers sont considérés comme non modifiables, car leur modification ou suppression locale n’aura aucun impact sur votre déploiement ; ils ne seront pas transférés vers votre instance cloud.

Il est recommandé que les fichiers ci-dessus fassent référence aux fichiers non modifiables répertoriés ci-dessous, suivis de toute instruction ou remplacement supplémentaire. Lorsque la configuration Dispatcher est déployée dans un environnement cloud, la dernière version des fichiers non modifiables est utilisée, quelle que soit la version utilisée dans le développement local.

* `conf.d/available_vhosts/default.vhost`

Contient un exemple d’hôte virtuel. Pour votre propre hôte virtuel, créez une copie de ce fichier, personnalisez-la, accédez à `conf.d/enabled_vhosts` et créez un lien symbolique vers votre copie personnalisée.

* `conf.d/dispatcher_vhost.conf`

Élément du framework de base, utilisé pour illustrer la manière dont vos hôtes virtuels et vos variables globales sont inclus.

* `conf.d/rewrites/default_rewrite.rules`

Règles de réécriture par défaut adaptées à un projet standard. Si une personnalisation est nécessaire, modifiez `rewrite.rules`. Dans votre personnalisation, vous pouvez toujours inclure les règles par défaut en premier, si elles répondent à vos besoins.

* `conf.dispatcher.d/available_farms/default.farm`

Contient un exemple de ferme Dispatcher. Pour votre propre ferme, créez une copie de ce fichier, personnalisez-la, accédez à `conf.d/enabled_farms` et créez un lien symbolique vers votre copie personnalisée.

* `conf.dispatcher.d/cache/default_invalidate.any`

Élément du framework de base, généré au démarrage. Vous **devez** inclure ce fichier dans chaque ferme définie, au niveau de la section `cache/allowedClients`.

* `conf.dispatcher.d/cache/default_rules.any`

Règles de cache par défaut adaptées à un projet standard. Si une personnalisation est nécessaire, modifiez `conf.dispatcher.d/cache/rules.any`. Dans votre personnalisation, vous pouvez toujours inclure les règles par défaut en premier, si elles répondent à vos besoins.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

En-têtes de requête par défaut à transférer vers le serveur principal, adaptés à un projet standard. Si une personnalisation est nécessaire, modifiez `clientheaders.any`. Dans votre personnalisation, vous pouvez toujours inclure d’abord les en-têtes de requête par défaut, s’ils répondent à vos besoins.

* `conf.dispatcher.d/dispatcher.any`

Élément du framework de base, utilisé pour illustrer la manière dont vos fermes de Dispatcher sont incluses.

* `conf.dispatcher.d/filters/default_filters.any`

Filtres par défaut adaptés à un projet standard. Si une personnalisation est nécessaire, modifiez `filters.any`. Dans votre personnalisation, vous pouvez toujours inclure d’abord les filtres par défaut, s’ils répondent à vos besoins.

* `conf.dispatcher.d/renders/default_renders.any`

Élément du framework de base, ce fichier est généré au démarrage. Vous **devez** inclure ce fichier dans chaque ferme définie, au niveau de la section `renders`.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Extension métacaractère d’hôte par défaut adaptée à un projet standard. Si une personnalisation est nécessaire, modifiez `virtualhosts.any`. Dans votre personnalisation, vous ne devez pas inclure l’extension métacaractère d’hôte par défaut, car elle correspond à **chaque** requête entrante.

>[!NOTE]
>L’archétype maven d’AEM as a Cloud Service génère la même structure de fichiers de configuration Dispatcher.

Les sections ci-dessous décrivent comment valider localement la configuration afin qu’elle puisse franchir le niveau de qualité associé dans Cloud Manager lors du déploiement d’une version interne.

## Validation locale d’une configuration Dispatcher {#local-validation-of-dispatcher-configuration}

L’outil de validation est disponible dans le SDK à l’emplacement `bin/validator` sous forme de fichier binaire Mac OS, Linux ou Windows, ce qui permet aux clients d’exécuter la même validation que celle effectuée par Cloud Manager lors de la création et du déploiement d’une version.

Il est appelé comme suit : `validator full [-d folder] [-w whitelist] zip-file | src folder`

L’outil valide la configuration d’Apache et Dispatcher. Il analyse tous les fichiers avec un motif `conf.d/enabled_vhosts/*.vhost` et vérifie que seules les directives mises en liste blanche sont utilisées. Les directives autorisées dans les fichiers de configuration Apache peuvent être répertoriées en exécutant la commande de liste blanche du validateur :

```
$ validator whitelist
Cloud manager validator 2.0.4
 
Whitelisted directives:
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
| `mod_auth_basic` | [https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html](https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html) |
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

Les clients ne peuvent pas ajouter de modules arbitraires, mais des modules supplémentaires peuvent être envisagés pour inclusion dans le produit à l’avenir. Les clients peuvent trouver la liste des directives disponibles pour une version de Dispatcher donnée en exécutant « validator whitelist » dans le SDK, tel que décrit dans la documentation des outils Dispatcher.

La liste blanche contient la liste des directives Apache autorisées dans une configuration client. Si une directive n’est pas mise en liste blanche, l’outil consigne une erreur et renvoie un code de sortie non nul. Si aucune liste blanche n’est fournie sur la ligne de commande (c’est-à-dire de la manière dont elle doit être appelée), l’outil utilise une liste blanche par défaut que Cloud Manager utilisera pour la validation avant de procéder au déploiement dans les environnements cloud.

Il analyse également tous les fichiers présentant le motif `conf.dispatcher.d/enabled_farms/*.farm` et vérifie les éléments suivants :

* Absence de règle de filtre utilisant l’opérateur allow via `/glob` (voir [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) pour plus d’informations)
* Aucune fonction d’administration n’est exposée. Par exemple, l’accès aux chemins tels que `/crx/de or /system/console`.

Lorsqu’il est exécuté sur votre artefact maven ou votre sous-répertoire `dispatcher/src`, il signale les échecs de validation :

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-whitelisted directives:
 conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
 conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Notez que l’outil de validation ne rapporte que l’utilisation interdite des directives Apache qui n’ont pas été mises sur liste blanche. Il ne signale aucun problème de syntaxe ni de sémantique dans votre configuration Apache, car ces informations ne sont disponibles que pour les modules Apache dans un environnement en cours d’exécution.

Si aucun échec de validation n’est signalé, votre configuration est prête pour le déploiement.

Les techniques de dépannage présentées ci-dessous permettent de déboguer les erreurs de validation courantes qui sont générées par l’outil :

**unable to locate a`conf.dispatcher.d`subfolder in the archive**

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
configuration Apache complète et des fichiers avec des préfixes `ams_`. Bien que cette fonctionnalité soit toujours prise en charge
pour la rétrocompatibilité, vous devez passer à la nouvelle mise en page.

## Test local de votre configuration Apache et Dispatcher {#testing-apache-and-dispatcher-configuration-locally}

Il est également possible de tester localement votre configuration Apache et Dispatcher. Cela nécessite que Docker soit installé localement et que votre configuration réussisse la validation comme décrit ci-dessus.

Avec le paramètre « `-d` », le programme de validation génère un dossier contenant tous les fichiers de configuration requis par Dispatcher.

Ensuite, le script `docker_run.sh` peut pointer vers ce dossier, en démarrant le conteneur avec votre configuration.

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

Dispatcher démarre alors dans un conteneur avec son serveur principal pointant vers une instance AEM s’exécutant sur votre ordinateur Mac OS local au port 4503.

## Débogage de la configuration Apache et Dispatcher {#debugging-apache-and-dispatcher-configuration}

La stratégie suivante peut être utilisée afin d’augmenter la sortie du journal pour le module Dispatcher et voir le résultat de l’évaluation `RewriteRule` dans les environnements locaux et cloud.

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

Lors de l’exécution locale de Dispatcher, les journaux sont également directement imprimés dans la sortie du terminal. La plupart du temps, ces journaux doivent être en mode DEBUG, ce qui peut être effectué en transmettant le niveau Debug comme paramètre lors de l’exécution de Docker. Par exemple :

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

Les journaux des environnements cloud seront exposés par le biais du service de journalisation disponible dans Cloud Manager.

## Différentes configurations Dispatcher par environnement {#different-dispatcher-configurations-per-environment}

Actuellement, la même configuration Dispatcher est appliquée à tous les environnements AEM as a Cloud Service. Le composant d’exécution comporte une variable d’environnement `ENVIRONMENT_TYPE` qui contient le mode d’exécution actuel (dev, stage ou prod) ainsi qu’une définition. La définition peut être `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` ou `ENVIRONMENT_PROD`. Dans la configuration Apache, la variable peut être utilisée directement dans une expression. Vous pouvez également utiliser la définition pour créer une logique :

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

La structure de configuration Dispatcher présente des différences entre Managed Services et AEM as a Cloud Service. Vous trouverez ci-dessous un guide détaillé sur la migration de la configuration Dispatcher d’AMS version 2 vers AEM as a Cloud Service.

## Comment convertir une configuration Dispatcher AMS en AEM as a Cloud Service

La section suivante fournit des instructions étape par étape pour convertir une configuration AMS. Elle suppose
que vous disposez d’une archive avec une structure similaire à celle décrite dans la [configuration Dispatcher Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html).

### Extraire l’archive et supprimer tout préfixe

Extrayez l’archive dans un dossier et assurez-vous que les noms des sous-dossiers immédiats commencent par `conf`, `conf.d`,
`conf.dispatcher.d` et `conf.modules.d`. Si tel n’est pas le cas, déplacez-les dans la hiérarchie.

### Supprimer les sous-dossiers et fichiers non utilisés

Supprimez les sous-dossiers `conf` et `conf.modules.d`, ainsi que les fichiers correspondants à `conf.d/*.conf`.

### Supprimer tous les hôtes virtuels non publiés

Supprimez tout fichier d’hôte virtuel dans `conf.d/enabled_vhosts` dont le nom inclut `author`, `unhealthy`, `health`,
`lc` ou `flush`. Tous les fichiers d’hôtes virtuels dans `conf.d/available_vhosts` non
liés peuvent également être supprimés.

### Supprimer ou commenter les sections d’hôte virtuel qui ne font pas référence au port 80

Si des sections de vos fichiers d’hôtes virtuels font encore référence exclusivement à d’autres ports que le port 80, par exemple :

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
placé dans l’instruction `Include` qui y fait référence dans les fichiers d’hôtes virtuels.

### Vérifier les variables

Entrez dans le répertoire `conf.d/variables`.

Supprimez tout fichier nommé `ams_default.vars` et n’oubliez pas de supprimer les instructions `Include` des fichiers d’hôtes
virtuels qui y font référence.

Si `conf.d/variables` contient maintenant un seul fichier, il doit être renommé `custom.vars`.
De plus, veillez à adapter également les instructions `Include` se rapportant à ce fichier dans les fichiers d’hôtes virtuels.

Si le dossier contient toutefois plusieurs fichiers spécifiques à l’hôte virtuel, leur contenu doit être
placé dans l’instruction `Include` qui y fait référence dans les fichiers d’hôtes virtuels.

### Supprimer les listes blanches

Supprimez le dossier `conf.d/whitelists` et les instructions `Include` des fichiers d’hôtes virtuels faisant référence à
un fichier de ce sous-dossier.

### Remplacer toute variable qui n’est plus disponible

Dans tous les fichiers d’hôtes virtuels :

Renommez `PUBLISH_DOCROOT` en `DOCROOT`
Supprimez les sections faisant référence à des variables nommées `DISP_ID`, `PUBLISH_FORCE_SSL` ou `PUBLISH_WHITELIST_ENABLED`

### Vérifier votre état en exécutant le programme de validation

Exécutez le programme de validation Dispatcher dans votre répertoire, avec la sous-commande `httpd` :

```
$ validator httpd .
```

Si des erreurs s’affichent au sujet de fichiers d’inclusion manquants, vérifiez si vous avez correctement renommé
les fichiers en question.

Si vous voyez des directives Apache qui ne sont pas placées sur liste blanche, supprimez-les.

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

Si `conf.dispatcher.d/cache` est maintenant vide, copiez le fichier `conf.dispatcher.d/cache/rules.any`
de la configuration Dispatcher standard dans ce dossier. La configuration Dispatcher
standard se trouve dans le dossier `src` de ce SDK. N’oubliez pas d’adapter également les
instructions `$include` faisant référence aux fichiers de règles `ams_*_cache.any` dans les
fichiers de fermes.

En revanche, si `conf.dispatcher.d/cache` contient maintenant un seul fichier portant le suffixe `_cache.any`,
il doit être renommé en `rules.any`. De plus, veillez à adapter les instructions `$include`
se rapportant à ce fichier dans les fichiers de fermes.

Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu
doit être copié dans l’instruction `$include` qui y fait référence dans les fichiers de fermes.

Supprimez tout fichier portant le suffixe `_invalidate_allowed.any`.

Copiez le fichier `conf.dispatcher.d/cache/default_invalidate_any` de la configuration
Dispatcher AEM en mode cloud par défaut vers cet emplacement.

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

Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu
doit être copié dans l’instruction `$include` qui y fait référence dans les fichiers de fermes.

Copiez le fichier `conf.dispatcher/clientheaders/default_clientheaders.any` de la configuration
Dispatcher AEM as a Cloud Service par défaut vers cet emplacement.

Dans chaque fichier de ferme, remplacez les instructions d’inclusion clientheader qui se présentent comme suit :

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

Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu
doit être copié dans l’instruction `$include` qui y fait référence dans les fichiers de fermes.

Copiez le fichier `conf.dispatcher/filters/default_filters.any` de la configuration
Dispatcher AEM as a Cloud Service par défaut vers cet emplacement.

Dans chaque fichier de ferme, remplacez les instructions d’inclusion de filtre qui se présentent comme suit :

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

Copiez le fichier `conf.dispatcher.d/renders/default_renders.any` de la configuration
Dispatcher AEM as a Cloud Service par défaut vers cet emplacement.

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

Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu
doit être copié dans l’instruction `$include` qui y fait référence dans les fichiers de fermes.

Copiez le fichier `conf.dispatcher/virtualhosts/default_virtualhosts.any` de la configuration
Dispatcher AEM as a Cloud Service par défaut vers cet emplacement.

Dans chaque fichier de ferme, remplacez les instructions d’inclusion de filtre qui se présentent comme suit :

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

par l’instruction suivante :

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Vérifier votre état en exécutant le programme de validation

Exécutez le programme de validation Dispatcher AEM as a Cloud Service dans votre répertoire, avec la sous-commande `dispatcher` :

```
$ validator dispatcher .
```

Si des erreurs s’affichent au sujet de fichiers d’inclusion manquants, vérifiez si vous avez correctement renommé
les fichiers en question.

Si des erreurs s’affichent concernant une variable non définie `PUBLISH_DOCROOT`, renommez-la `DOCROOT`.

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

### Étape 2 : démarrer Dispatcher dans une image Docker avec ces informations de déploiement

Avec votre serveur de publication AEM en exécution sur votre ordinateur macOS et écoutant le port 4503,
vous pouvez lancer Dispatcher devant ce serveur comme suit :

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Cela démarrera le conteneur et exposera Apache sur le port local 8080.

### Utiliser votre nouvelle configuration Dispatcher

Félicitations ! Si le programme de validation ne signale plus aucun problème et
que le conteneur Docker démarre sans erreur ni avertissement, vous êtes
prêt à déplacer votre configuration vers un sous-répertoire `dispatcher/src`
de votre référentiel git.

**Les clients qui utilisent la version 1 de la configuration AMS Dispatcher doivent contacter le service clientèle pour les aider à migrer à la version 2 afin de pouvoir suivre les instructions ci-dessus.**

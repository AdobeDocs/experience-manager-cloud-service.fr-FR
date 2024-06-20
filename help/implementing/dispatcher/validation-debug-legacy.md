---
title: Validation et débogage à l’aide des outils Dispatcher (hérités)
description: Validation et débogage à l’aide des outils Dispatcher (hérités)
feature: Dispatcher
hidefromtoc: true
exl-id: dc04d035-f002-42ef-9c2e-77602910c2ec
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '2337'
ht-degree: 100%

---

# Validation et débogage à l’aide des outils Dispatcher (hérités)  {#Dispatcher-tools-legacy}

## Présentation {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Pour plus d’informations sur Dispatcher en mode cloud et sur le téléchargement des outils Dispatcher, consulter la page [Dispatcher en mode cloud](/help/implementing/dispatcher/disp-overview.md).

Les sections suivantes décrivent la structure de fichiers du mode hérité, la validation locale, le débogage et la migration du mode hérité vers le [mode flexible](/help/implementing/dispatcher/validation-debug.md).

Cet article suppose que la configuration du Dispatcher de votre projet n’inclut pas le fichier opt-in/USE_SOURCES_DIRECTLY. Par conséquent, il présente des limitations quant au nombre et à la taille des fichiers, tel que :

* l’utilisation d’un fichier unique de réécriture plutôt que des fichiers spécifiques aux sites est nécessaire.
* le total du contenu des fichiers personnalisables doit être inférieur à 1 Mo.

À compter de la version 2021.7.0 de Cloud Manager, les nouveaux programmes de Cloud Manager génèrent des structures de projet Maven avec AEM archétype 28 et versions ultérieures, qui inclut le fichier ci-dessus.

Il est **vivement recommandé** de migrer du mode hérité vers le mode flexible, comme indiqué dans la section de migration [Migration du mode hérité vers le mode flexible](#migrating-flexible). L’utilisation du mode flexible entraîne également le SDK et Runtime à valider et déployer la configuration de manière améliorée.

## Structure de fichier {#legacy-mode-file-structure}

La structure du sous-dossier Dispatcher du projet (en mode hérité) est la suivante :

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
    │   ├── marketing_query_parameters.any
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

Les fichiers suivants sont personnalisables et sont transférés vers votre instance cloud au moment du déploiement :

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

Vous pouvez avoir un ou plusieurs de ces fichiers. Ils contiennent des entrées `<VirtualHost>` qui correspondent aux noms d’hôtes et permettent à Apache de gérer chaque trafic de domaine avec des règles différentes. Les fichiers sont créés dans le répertoire `available_vhosts` et activés avec un lien symbolique dans le répertoire `enabled_vhosts`. À partir des fichiers `.vhost`, d’autres fichiers, tels que les réécritures et les variables, sont inclus.

* `conf.d/rewrites/rewrite.rules`

Ce fichier est inclus dans vos fichiers `.vhost`. Il contient un ensemble de règles de réécriture pour `mod_rewrite`.

>[!NOTE]
>
>Actuellement, vous devez utiliser un fichier unique de réécriture plutôt que des fichiers spécifiques aux sites. En règle générale, le total du contenu des fichiers personnalisables doit être inférieur à 1 Mo.

* `conf.d/variables/custom.vars`

Ce fichier est inclus dans vos fichiers `.vhost`. Vous pouvez y ajouter des définitions pour les variables Apache.

* `conf.d/variables/global.vars`

Ce fichier est inclus dans le fichier `dispatcher_vhost.conf`. Vous pouvez modifier votre Dispatcher et le niveau du journal des réécritures dans ce fichier.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

Vous pouvez avoir un ou plusieurs de ces fichiers. Ils contiennent des fermes correspondant aux noms d’hôtes et permettant au module Dispatcher de gérer chaque ferme avec des règles différentes. Les fichiers sont créés dans le répertoire `available_farms` et activés avec un lien symbolique dans le répertoire `enabled_farms`. À partir des fichiers `.farm`, d’autres fichiers, tels que les filtres, les règles de cache et autres, sont inclus.

* `conf.dispatcher.d/cache/rules.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il spécifie les préférences de cache.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il spécifie les en-têtes de requête à transférer au serveur principal.

* `conf.dispatcher.d/filters/filters.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il comporte un ensemble de règles qui indiquent le trafic qui doit être filtré et ne doit pas atteindre le serveur principal.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Ce fichier est inclus dans vos fichiers `.farm`. Il comporte une liste de noms d’hôtes ou de chemins d’URI à mettre en correspondance glob. Cette correspondance détermine le serveur principal à utiliser pour diffuser une requête.

Les fichiers ci-dessus font référence aux fichiers de configuration non modifiables répertoriés ci-dessous. Les modifications apportées aux fichiers non modifiables ne sont pas traitées par les Dispatchers dans les environnements cloud.

**Fichiers de configuration non modifiables**

Ces fichiers font partie du framework de base. Ils respectent les normes et les bonnes pratiques. Les fichiers sont considérés comme non modifiables, car leur modification ou suppression locale n’a aucun impact sur votre déploiement ; ils ne sont pas transférés vers votre instance cloud.

Il est recommandé que les fichiers ci-dessus fassent référence aux fichiers non modifiables répertoriés ci-dessous, suivis de toute instruction ou remplacement supplémentaire. Lorsque la configuration du Dispatcher est déployée dans un environnement cloud, la dernière version des fichiers non modifiables est utilisée, quelle que soit la version utilisée dans le développement local.

* `conf.d/available_vhosts/default.vhost`

Contient un exemple d’hôte virtuel. Pour votre propre hôte virtuel, créez une copie de ce fichier, personnalisez-la, accédez à `conf.d/enabled_vhosts` et créez un lien symbolique vers votre copie personnalisée.

* `conf.d/dispatcher_vhost.conf`

Élément du framework de base, utilisé pour illustrer la manière dont vos hôtes virtuels et vos variables globales sont inclus.

* `conf.d/rewrites/default_rewrite.rules`

Règles par défaut pour les réécritures adaptées à un projet standard. Si une personnalisation est nécessaire, modifiez `rewrite.rules`. Dans votre personnalisation, vous pouvez toujours inclure les règles par défaut en premier, si elles répondent à vos besoins.

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

## Modules Apache pris en charge {#apache-modules}

Voir [Modules Apache pris en charge](/help/implementing/dispatcher/disp-overview.md#supported-directives).

## Validation locale {#local-validation-legacy-mode}

>[!NOTE]
>Les sections ci-dessous incluent des commandes utilisant les versions Mac ou Linux® du SDK, mais le SDK Windows peut également être utilisé de la même manière.

Utilisez le script `validate.sh` comme indiqué ci-dessous :

```
$ validate.sh src/dispatcher
Phase 1: Dispatcher validator
Cloud manager validator 2.0.32
Phase 1 finished
Phase 2: httpd -t validation in docker image
values.csv found in deployment folder: /tmp/dispatcher_validation_1625150390 - using files listed there
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until localhost is available
localhost resolves to ::1
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {

...

}
Syntax OK
Phase 2 finished
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt

...

no immutable file has been changed - check is SUCCESSFUL
Phase 3 finished
```

Le script effectue les opérations suivantes :

1. Il exécute le programme de validation. Si la configuration n’est pas valide, le script échoue.
2. Il exécute la commande `httpd -t` pour tester si la syntaxe est correcte, de sorte qu’Apache httpd puisse démarrer. En cas de réussite, la configuration doit être prête pour le déploiement.
3. Vérifie que le sous-ensemble des fichiers de configuration du SDK du Dispatcher, qui sont censés être non modifiables (comme décrit dans la [section Structure de fichiers](##legacy-mode-file-structure)) n’a pas été modifié. Cette nouvelle vérification a été introduite avec le SDK AEM version v2021.1.4738 qui inclut également les outils Dispatcher version 2.0.36. Avant cette mise à jour, les clients et clientes auraient pu supposer à tort que toute modification locale du SDK de ces fichiers non modifiables était également appliquée à l’environnement cloud.

Lors d’un déploiement de Cloud Manager, la vérification de la syntaxe `httpd -t` est également exécutée et toute erreur est incluse dans le journal `Build Images step failure` de Cloud Manager.

### Phase 1 {#first-phase}

Si une directive n’est pas placée sur la liste autorisée, l’outil consigne une erreur et renvoie un code de sortie non nul. Il analyse également tous les fichiers présentant le motif `conf.dispatcher.d/enabled_farms/*.farm` et vérifie les éléments suivants :

* Absence de règle de filtre utilisant l’opérateur allow via `/glob` (voir [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) pour plus d’informations.
* Aucune fonction d’administration n’est exposée. Par exemple, l’accès aux chemins tels que `/crx/de or /system/console`.

L’outil de validation ne signale que l’utilisation interdite des directives Apache qui n’ont pas été placées sur la liste autorisée. Il ne signale aucun problème de syntaxe ni de sémantique dans votre configuration Apache, car ces informations ne sont disponibles que pour les modules Apache dans un environnement en cours d’exécution.

Les techniques de dépannage présentées ci-dessous permettent de déboguer les erreurs de validation courantes qui sont générées par l’outil :

**Impossible de localiser un sous-dossier `conf.dispatcher.d` dans l’archive**

Votre archive doit contenir les dossiers `conf.d` et `conf.dispatcher.d`. Notez que vous ne devez **pas**
utiliser le préfixe `etc/httpd` dans votre archive.

**Impossible de trouver une ferme dans`conf.dispatcher.d/enabled_farms`**

Vos fermes activées doivent se trouver dans le sous-dossier mentionné.

**Le fichier inclus (...) doit être nommé : ...**.

Deux sections de la configuration de votre ferme **doivent** inclure
un fichier spécifique : `/renders` et `/allowedClients` dans la section `/cache`. Ces
sections doivent se présenter comme suit :

```
/renders {
    $include "../renders/default_renders.any"
}
```

Et :

```
/allowedClients {
    $include "../cache/default_invalidate.any"
}
```

**fichier inclus dans un emplacement inconnu : ...**

Votre configuration de ferme comporte quatre sections où vous pouvez inclure votre propre fichier : `/clientheaders`, `filters`, `/rules` dans la section `/cache` et `/virtualhosts`. Les fichiers inclus doivent être nommés comme suit :

| Section | Nom du fichier d’inclusion |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

Vous pouvez également inclure la version **par défaut** de ces fichiers, dont les noms sont précédés du mot `default_`, par exemple `../filters/default_filters.any`.

**Inclure l’instruction à (...), en dehors de tout emplacement connu : ...**.

Outre les six sections mentionnées dans les paragraphes ci-dessus, vous n’avez pas l’autorisation d’utiliser l’instruction `$include`. Par exemple, les éléments suivants généreraient cette erreur :

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**Les clients/rendus ne sont pas inclus à partir de : ...**.

Cette erreur est générée lorsque vous ne spécifiez pas d’inclusion pour `/renders` et `/allowedClients` dans la section `/cache`. Voir la section **le fichier inclus (...) doit être nommé : ...** pour plus d’informations.

**Le filtre ne doit pas utiliser de modèle glob pour autoriser les requêtes**

Il n’est pas sécurisé d’autoriser des requêtes avec une règle de style `/glob`, qui est mise en correspondance avec la ligne de requête complète, par exemple :

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Cette instruction est destinée à autoriser les requêtes de fichiers `css`, mais elle permet également les requêtes de **n’importe quelle** ressource suivie de la chaîne de requête `?a=.css`. Il est donc interdit d’utiliser de tels filtres (voir aussi CVE-2016-0957).

**Le fichier inclus (...) ne correspond à aucun fichier connu**

Il existe deux types de fichiers dans la configuration de l’hôte virtuel Apache qui peuvent être spécifiés sous la forme d’inclusions : les réécritures et les variables.
Les fichiers inclus doivent être nommés comme suit :

| Type | Nom du fichier d’inclusion |
|-----------|---------------------------------|
| Réécritures | `conf.d/rewrites/rewrite.rules` |
| Variables | `conf.d/variables/custom.vars` |

>[!TIP]
>
>Pour pouvoir inclure plus de fichiers de manière beaucoup moins limitée, vous pouvez décider de passer en mode de configuration Dispatcher flexible. Consultez [Validation et débogage à l’aide des outils de Dispatcher](/help/implementing/dispatcher/validation-debug.md) pour plus d’informations sur le mode flexible.

Vous pouvez également inclure la version **par défaut** des règles de réécriture, dont le nom est `conf.d/rewrites/default_rewrite.rules`.
Notez qu’il n’existe pas de version par défaut des fichiers de variables.

**Mise en page de configuration obsolète détectée, activation du mode de compatibilité**

Ce message indique que votre configuration présente la disposition version 1 obsolète, contenant une
configuration Apache complète et des fichiers avec des préfixes `ams_`. Bien que cette configuration soit toujours prise en charge
en rétrocompatibilité, vous devriez passer à la nouvelle mise en page.

La première phase peut également être **exécutée séparément**, plutôt qu’à partir du script `validate.sh` de wrapper.

Lorsqu’il est exécuté sur votre artefact Maven ou votre sous-répertoire `dispatcher/src`, il signale les échecs de validation :

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Sous Windows, le programme de validation du Dispatcher est sensible à la casse. Par conséquent, il peut ne pas valider la configuration si vous ne respectez pas la casse du chemin d’accès où se trouve votre configuration, par exemple :

```
bin\validator.exe full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
  
```

Évitez cette erreur en copiant le chemin à partir de l’Explorateur Windows, puis en le collant dans l’invite de commande, en utilisant une commande `cd` dans ce chemin.

### Phase 2 {#second-phase}

Cette phase vérifie la syntaxe Apache en démarrant Docker dans une image. Docker doit être installé localement, mais il n’est pas nécessaire qu’AEM soit en cours d’exécution.

>[!NOTE]
>Les utilisateurs et utilisatrices de Windows doivent utiliser Windows 10 Professionnel ou d’autres distributions prenant en charge Docker. Cette condition préalable est nécessaire pour exécuter et déboguer le Dispatcher sur un ordinateur local.

Cette phase peut également être exécutée indépendamment via `validator full -d out src/dispatcher`, qui génère un répertoire de sortie, dont a besoin la commande suivante `bin/docker_run.sh out host.docker.internal:4503 8080`.

Lors d’un déploiement de Cloud Manager, la vérification de syntaxe `httpd -t` est également exécutée et toutes les erreurs sont incluses dans le journal des échecs de l’étape de création d’images de Cloud Manager.

### Phase 3 {#third-phase}

En cas d’échec au cours de cette phase, cela signifie qu’Adobe a modifié un ou plusieurs fichiers non modifiables. Dans ce cas, vous devez remplacer les fichiers non modifiables correspondants par la nouvelle version fournie dans le répertoire `src` du SDK. L’exemple de journal ci-dessous illustre ce problème :

```
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt
(...)
checking existing 'conf.dispatcher.d/clientheaders/default_clientheaders.any' for changes
immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed:
--- /etc/httpd/conf.dispatcher.d/clientheaders/default_clientheaders.any
+++ /etc/httpd-actual/conf.dispatcher.d/clientheaders/default_clientheaders.any
@@ -40,4 +40,3 @@
"Sling-uploadmode"
"x-requested-with"
"If-Modified-Since"
-"Authorization"
** error: immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed!
  
```

Cette phase peut également être exécutée indépendamment via `validator full -d out src/dispatcher`, qui génère un répertoire de sortie, dont a besoin la commande suivante `bin/docker_immutability_check.sh out`.

## Déboguer la configuration Apache et du Dispatcher {#debugging-apache-and-dispatcher-configuration}

Vous pouvez exécuter le Dispatcher Apache en local à l’aide de `./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`.

Comme indiqué précédemment, Docker doit être installé localement et il n’est pas nécessaire qu’AEM soit en cours d’exécution. Les utilisateurs et utilisatrices de Windows doivent utiliser Windows 10 Professionnel ou d’autres distributions prenant en charge Docker. Cette condition préalable est nécessaire pour exécuter et déboguer le Dispatcher sur un ordinateur local.

La stratégie suivante peut être utilisée afin d’augmenter la sortie du journal pour le module Dispatcher et de voir les résultats de l’évaluation `RewriteRule` dans les environnements locaux et cloud.

Les niveaux de journal de ces modules sont définis par les variables `DISP_LOG_LEVEL` et `REWRITE_LOG_LEVEL`. Ils peuvent être définis dans le fichier `conf.d/variables/global.vars`. Sa partie pertinente est la suivante :

```
# Log level for the dispatcher
#
# Possible values are: error, warn, info, debug and trace1
# Default value: warn
#
# Define DISP_LOG_LEVEL warn
 
# Log level for mod_rewrite
#
# Possible values are: error, warn, info, debug and trace1 - trace8
# Default value: warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL warn
```

Lors de l’exécution locale du Dispatcher, les journaux sont directement imprimés dans la sortie du terminal. La plupart du temps, vous souhaitez que ces journaux soient en mode DEBUG, ce qui peut être réalisé en transmettant le niveau Debug comme paramètre lors de l’exécution de Docker. Par exemple : `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`.

Les journaux des environnements cloud sont exposés par le biais du service de journalisation disponible dans Cloud Manager.

## Différentes configurations Dispatcher par environnement {#different-dispatcher-configurations-per-environment}

Actuellement, la même configuration du Dispatcher est appliquée à tous les environnements AEM as a Cloud Service. L’exécution comporte une variable d’environnement `ENVIRONMENT_TYPE` qui contient le mode d’exécution actuel (développement, évaluation ou production) et une définition. La définition peut être `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` ou `ENVIRONMENT_PROD`. Dans la configuration Apache, la variable peut être utilisée directement dans une expression. Vous pouvez également utiliser la définition pour créer une logique :

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

Avec les configurations spécifiques à l’environnement, il peut se révéler difficile de déterminer à quoi ressemble la configuration du Dispatcher. Après avoir démarré votre conteneur Docker avec `docker_run.sh`, vous pouvez le vider comme suit :

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

## Migration du mode hérité vers le mode flexible {#migrating-flexible}

Avec la version 2021.7.0 de Cloud Manager, les nouveaux programmes génèrent des structures de projet Maven avec AEM archétype 28 ou version ultérieure, ce qui inclut le fichier **opt-in/USE_SOURCES_DIRECTLY**. Les limites précédentes du mode hérité concernant le nombre et la taille des fichiers sont supprimées, ce qui entraîne également la validation et le déploiement de la configuration par le SDK et l’exécution. Si votre configuration du Dispatcher ne comporte pas ce fichier, il est vivement recommandé de migrer. Utilisez les méthodes décrites dans la page [mode flexible](/help/implementing/dispatcher/validation-debug.md#migrating).

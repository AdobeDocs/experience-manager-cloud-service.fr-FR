---
title: Validation et débogage à l’aide des outils Dispatcher
description: Découvrez la validation locale, le débogage, la structure de fichiers du mode flexible et comment migrer du mode hérité vers le mode flexible.
feature: Dispatcher
exl-id: 9e8cff20-f897-4901-8638-b1dbd85f44bf
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '3028'
ht-degree: 93%

---

# Validation et débogage à l’aide des outils Dispatcher {#Dispatcher-in-the-cloud}

## Présentation {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Pour plus d’informations sur Dispatcher en mode cloud et sur le téléchargement des outils Dispatcher, voir la page [Dispatcher en mode cloud](/help/implementing/dispatcher/disp-overview.md). Si votre configuration du Dispatcher est en mode hérité, reportez-vous à la [documentation sur le mode hérité](/help/implementing/dispatcher/validation-debug-legacy.md).

Les sections suivantes décrivent la structure de fichiers du mode flexible, la validation locale, le débogage et la migration du mode hérité vers le mode flexible.

Cet article suppose que la configuration du Dispatcher de votre projet inclut le fichier `opt-in/USE_SOURCES_DIRECTLY`. Ce fichier permet au SDK et à l’exécution de valider et déployer la configuration de manière améliorée par rapport au mode hérité, en supprimant les limites liées au nombre et à la taille des fichiers.

Si votre configuration du Dispatcher n’inclut pas le fichier mentionné précédemment, Adobe vous recommande de migrer du mode hérité vers le mode flexible comme indiqué dans la section [Migration du mode hérité vers le mode flexible](#migrating).

## Structure de fichier {#flexible-mode-file-structure}

La structure du sous-dossier Dispatcher du projet est la suivante :

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   ├── my_site.vhost # Created by customer
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── my_site.vhost -> ../available_vhosts/my_site.vhost  # Created by customer
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
│── opt-in
│   └── USE_SOURCES_DIRECTLY
└── conf.dispatcher.d
    ├── available_farms
    │   ├── my_farm.farm # Created by customer
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
    │   └── my_farm.farm -> ../available_farms/my_farm.farm  # Created by customer
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
    │   ├── default_virtualhosts.any
    │   └── virtualhosts.any
    
```

Vous trouverez ci-dessous une explication des principaux fichiers qui peuvent être modifiés :

**Fichiers personnalisables**

Les fichiers suivants sont personnalisables et sont transférés vers votre instance cloud au moment du déploiement :

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

Vous pouvez avoir un ou plusieurs de ces fichiers. Ils contiennent des entrées `<VirtualHost>` qui correspondent aux noms d’hôtes et permettent à Apache de gérer chaque trafic de domaine avec des règles différentes. Les fichiers sont créés dans le répertoire `available_vhosts` et activés avec un lien symbolique dans le répertoire `enabled_vhosts`. À partir des fichiers `.vhost`, d’autres fichiers, tels que les réécritures et les variables, sont inclus.

>[!NOTE]
>
>En mode flexible, vous devez utiliser des chemins d’accès relatifs plutôt que des chemins absolus.

Assurez-vous qu’au moins un hôte virtuel correspondant aux ServerAlias `\*.local`, `localhost` et `127.0.0.1`, nécessaires pour l’invalidation du Dispatcher, est toujours disponible. Les alias de serveur `*.adobeaemcloud.net` et `*.adobeaemcloud.com` sont également requis dans au moins une configuration vhost et sont nécessaires pour les processus Adobe internes.

Si vous souhaitez faire correspondre l’hôte exact car vous disposez de plusieurs fichiers vhost, vous pouvez suivre l’exemple suivant :

```
<VirtualHost *:80>
    ServerName    "example.com"
    # Put names of which domains are used for your published site/content here
    ServerAlias     "*example.com" "\*.local" "localhost" "127.0.0.1" "*.adobeaemcloud.net" "*.adobeaemcloud.com"
    # Use a document root that matches the one in conf.dispatcher.d/default.farm
    DocumentRoot "${DOCROOT}"
    # URI dereferencing algorithm is applied at Sling's level, do not decode parameters here
    AllowEncodedSlashes NoDecode
    # Add header breadcrumbs for help in troubleshooting which vhost file is chosen
    <IfModule mod_headers.c>
        Header add X-Vhost "publish-example-com"
    </IfModule>
  ...
</VirtualHost>
```

* `conf.d/enabled_vhosts/<CUSTOMER_CHOICE>.vhost`

Ce dossier contient des liens symboliques relatifs vers des fichiers sous conf.dispatcher.d/available_vhosts.

Exemples de commandes nécessaires à la création de liens symboliques :

Apple macOS, Linux et WSL

```
ln -s ../available_vhosts/wknd.vhost wknd.vhost
```

Microsoft Windows

```
mklink wknd.vhost ..\available_vhosts\wknd.vhost
```

>[!NOTE]
>
> Lorsque vous utilisez des liens symboliques sous Windows, vous devez être exécuté dans une invite de commande avec élévation de privilèges, dans le sous-système Windows pour Linux ou avoir le privilège [Créer des liens symboliques](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links) attribué.

* `conf.d/rewrites/rewrite.rules`

Le fichier est inclus dans vos fichiers `.vhost`. Il contient un ensemble de règles de réécriture pour `mod_rewrite`.

* `conf.d/variables/custom.vars`

Le fichier est inclus dans vos fichiers `.vhost`. Vous pouvez y ajouter des définitions pour les variables Apache.

* `conf.d/variables/global.vars`

Le fichier est inclus dans le fichier `dispatcher_vhost.conf`. Vous pouvez modifier votre Dispatcher et le niveau du journal des réécritures dans ce fichier.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

Vous pouvez avoir un ou plusieurs de ces fichiers. Ils contiennent des fermes correspondant aux noms d’hôtes et permettant au module Dispatcher de gérer chaque ferme avec des règles différentes. Les fichiers sont créés dans le répertoire `available_farms` et activés avec un lien symbolique dans le répertoire `enabled_farms`. À partir des fichiers `.farm`, d’autres fichiers, tels que les filtres, les règles de cache et autres, sont inclus.

* `conf.dispatcher.d/enabled_farms/<CUSTOMER_CHOICE>.farm`

Ce dossier contient des liens symboliques relatifs vers des fichiers sous conf.dispatcher.d/available_farms.

Exemples de commandes nécessaires à la création de liens symboliques :

Apple macOS, Linux et WSL

```
ln -s ../available_farms/wknd.farm wknd.farm
```

Microsoft Windows

```
mklink wknd.farm ..\available_farms\wknd.farm
```

>[!NOTE]
>
> Lorsque vous utilisez des liens symboliques sous Windows, vous devez être exécuté dans une invite de commande avec élévation de privilèges, dans le sous-système Windows pour Linux ou avoir le privilège [Créer des liens symboliques](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links) attribué.

* `conf.dispatcher.d/cache/rules.any`

Le fichier est inclus dans vos fichiers `.farm`. Il spécifie les préférences de cache.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Le fichier est inclus dans vos fichiers `.farm`. Il spécifie les en-têtes de requête à transférer au serveur principal.

* `conf.dispatcher.d/filters/filters.any`

Le fichier est inclus dans vos fichiers `.farm`. Il comporte un ensemble de règles qui indiquent le trafic qui doit être filtré et ne doit pas atteindre le serveur principal.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Le fichier est inclus dans vos fichiers `.farm`. Il comporte une liste de noms d’hôtes ou de chemins d’URI à mettre en correspondance glob. Cette correspondance détermine le serveur principal à utiliser pour diffuser une requête.

* `opt-in/USE_SOURCES_DIRECTLY`

Ce fichier permet une configuration du Dispatcher plus flexible et supprime les limitations précédentes concernant le nombre et la taille des fichiers. Cela entraîne également le SDK et l’exécution à valider et déployer la configuration de manière améliorée.

Les fichiers ci-dessus font référence aux fichiers de configuration non modifiables répertoriés ci-dessous. Les modifications apportées aux fichiers non modifiables ne sont pas traitées par les Dispatchers dans les environnements cloud.

**Fichiers de configuration non modifiables**

Ces fichiers font partie du framework de base. Ils respectent les normes et les bonnes pratiques. Les fichiers sont considérés comme non modifiables, car leur modification ou suppression locale n’a aucun impact sur votre déploiement ; ils ne sont pas transférés vers votre instance cloud.

Il est recommandé que les fichiers ci-dessus fassent référence aux fichiers non modifiables répertoriés ci-dessous, suivis de toute instruction ou remplacement supplémentaire. Lorsque la configuration du Dispatcher est déployée dans un environnement cloud, la dernière version des fichiers non modifiables est utilisée, quelle que soit la version utilisée dans le développement local.

* `conf.d/available_vhosts/default.vhost`

Contient un exemple d’hôte virtuel. Pour votre propre hôte virtuel, créez une copie de ce fichier, personnalisez-la, accédez à `conf.d/enabled_vhosts` et créez un lien symbolique vers votre copie personnalisée.
Ne copiez pas directement le fichier default.vhost dans `conf.d/enabled_vhosts`.

Assurez-vous qu’un hôte virtuel correspondant aux ServerAlias `\*.local`, `localhost` et `127.0.0.1`, nécessaires pour l’invalidation du Dispatcher, est toujours disponible. Les alias de serveur `*.adobeaemcloud.net` et `*.adobeaemcloud.com` sont nécessaires pour les processus internes d’Adobe.

* `conf.d/dispatcher_vhost.conf`

Élément du framework de base, utilisé pour illustrer la manière dont vos hôtes virtuels et vos variables globales sont inclus.

* `conf.d/rewrites/default_rewrite.rules`

Les règles de réécriture par défaut conviennent à un projet standard. Si une personnalisation est nécessaire, modifiez `rewrite.rules`. Dans votre personnalisation, vous pouvez toujours inclure les règles par défaut en premier, si elles répondent à vos besoins.

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

## Validation locale {#local-validation-flexible-mode}

>[!NOTE]
>
>Les sections ci-dessous incluent des commandes utilisant les versions Mac ou Linux® du SDK, mais le SDK Windows peut également être utilisé de la même manière.

Utilisez le script `validate.sh` comme indiqué ci-dessous :

```
$ validate.sh src/dispatcher
opt-in USE_SOURCES_DIRECTLY marker file detected
Phase 1: Dispatcher validator
Cloud manager validator 2.0.32
Phase 1 finished
Phase 2: httpd -t validation in docker image
values.csv not found in deployment folder: /Users/foo/src - using files in 'conf.d' and 'conf.dispatcher.d' subfolders directly
processing configuration subfolder: conf.d
processing configuration subfolder: conf.dispatcher.d
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

Le script se compose des trois phases suivantes :

1. Il exécute le programme de validation. Si la configuration n’est pas valide, le script échoue.
2. Il exécute la commande `httpd -t` pour vérifier que la syntaxe est correcte de sorte qu’Apache httpd puisse démarrer. En cas de réussite, la configuration doit être prête pour le déploiement.
3. Il vérifie que le sous-ensemble des fichiers de configuration du SDK du Dispatcher, qui sont censés être modifiables (tel que décrit dans la [section Structure de fichiers](##flexible-mode-file-structure)) n’a pas été modifié et correspond à la version actuelle du SDK.

Lors d’un déploiement de Cloud Manager, la vérification de la syntaxe `httpd -t` est également exécutée et toute erreur est incluse dans le journal `Build Images step failure` de Cloud Manager.

>[!NOTE]
>
>Consultez la section [Rechargement et validation automatiques](#automatic-loading) pour une alternative efficace à l’exécution de `validate.sh` après chaque modification de la configuration.

### Phase 1 {#first-phase}

Si une directive n’est pas placée sur la liste autorisée, l’outil consigne une erreur et renvoie un code de sortie non nul. Il analyse également tous les fichiers présentant le motif `conf.dispatcher.d/enabled_farms/*.farm` et vérifie les éléments suivants :

* Absence de règle de filtre utilisant l’opérateur allow via `/glob` (voir [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957)) pour plus d’informations.
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

**Fichier inclus dans le système à l’emplacement inconnu : ...**.

Votre configuration de ferme de serveurs comporte quatre sections où vous pouvez inclure vos propres fichiers : `/clientheaders`, `filters`, `/rules` dans la section `/cache` et `/virtualhosts`. Les fichiers inclus doivent être nommés comme suit :

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

**Le fichier inclus (...) ne correspond à aucun fichier connu.**

Par défaut, il existe deux types de fichiers dans la configuration de l’hôte virtuel Apache qui peuvent être spécifiés comme inclus : les réécritures et les variables.

| Type | Nom du fichier d’inclusion |
|-----------|---------------------------------|
| Réécritures | `conf.d/rewrites/rewrite.rules` |
| Variables | `conf.d/variables/custom.vars` |

En mode flexible, d’autres fichiers peuvent également être inclus, à condition qu’ils se trouvent dans des sous-répertoires (peu importe le niveau) du répertoire `conf.d`, avec le préfixe suivant.

| Préfixe de répertoire supérieur du fichier d’inclusion |
|-------------------------------------|
| `conf.d/includes` |
| `conf.d/modsec` |
| `conf.d/rewrites` |

Par exemple, vous pouvez inclure un fichier dans un répertoire créé sous le répertoire `conf.d/includes` comme suit :

```
Include conf.d/includes/mynewdirectory/myincludefile.conf
```

Vous pouvez également inclure la version **par défaut** des règles de réécriture, dont le nom est `conf.d/rewrites/default_rewrite.rules`.
Notez qu’il n’existe pas de version par défaut des fichiers de variables.

**Mise en page de configuration obsolète détectée, activation du mode de compatibilité**

Ce message indique que votre configuration présente la disposition version 1 obsolète, contenant une
configuration Apache complète et des fichiers avec des préfixes `ams_`. Bien que cette configuration soit toujours prise en charge
en rétrocompatibilité, vous devriez passer à la nouvelle mise en page.

La première phase peut également être **exécutée séparément**, plutôt qu’à partir du script `validate.sh` de wrapper.

Lorsqu’il est exécuté sur votre artefact Maven ou votre sous-répertoire `dispatcher/src`, il signale les échecs de validation :

```
$ validator full -relaxed dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Sous Windows, le programme de validation du Dispatcher est sensible à la casse. Par conséquent, il peut ne pas valider la configuration si vous ne respectez pas la casse du chemin d’accès où se trouve votre configuration, par exemple :

```
bin\validator.exe -relaxed full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
```

Évitez cette erreur en copiant le chemin à partir de l’Explorateur Windows, puis en le collant dans l’invite de commande, en utilisant une commande `cd` dans ce chemin.

### Phase 2 {#second-phase}

Cette phase vérifie la syntaxe Apache en démarrant Apache HTTPD dans un conteneur Docker. Docker doit être installé localement, mais il n’est pas nécessaire qu’AEM soit en cours d’exécution.

>[!NOTE]
>
>Les utilisateurs et utilisatrices de Windows doivent utiliser Windows 10 Professionnel ou d’autres distributions prenant en charge Docker. Cette exigence est un prérequis pour l’exécution et le débogage du Dispatcher sur un ordinateur local.
>Pour Windows et macOS, Adobe vous recommande d’utiliser Docker Desktop.

Cette phase peut également être exécutée indépendamment via `bin/docker_run.sh src/dispatcher host.docker.internal:4503 8080`.

Lors d’un déploiement de Cloud Manager, la vérification de syntaxe `httpd -t` est également exécutée et toutes les erreurs sont incluses dans le journal des échecs de l’étape de création d’images de Cloud Manager.

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

Cette phase peut également être exécutée indépendamment via `bin/docker_immutability_check.sh src/dispatcher`.

Vos fichiers non modifiables locaux peuvent être mis à jour en exécutant le script `bin/update_maven.sh src/dispatcher` sur votre dossier du Dispatcher, où `src/dispatcher` est votre répertoire de configuration du Dispatcher. Ce script met également à jour tous les fichiers `pom.xml` dans le répertoire parent afin que les contrôles de non modification Maven soient également mis à jour.

## Déboguer la configuration Apache et du Dispatcher {#debugging-apache-and-dispatcher-configuration}

Vous pouvez exécuter le Dispatcher Apache en local à l’aide de `./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080`.

Comme indiqué précédemment, Docker doit être installé localement et il n’est pas nécessaire qu’AEM soit en cours d’exécution. Les utilisateurs et utilisatrices de Windows doivent utiliser Windows 10 Professionnel ou d’autres distributions prenant en charge Docker. Cette exigence est un prérequis pour l’exécution et le débogage du Dispatcher sur un ordinateur local.

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

Lors de l’exécution locale du Dispatcher, les journaux sont directement imprimés dans la sortie du terminal. La plupart du temps, vous souhaitez que ces journaux soient en mode DEBUG, ce qui peut être réalisé en transmettant le niveau Debug comme paramètre lors de l’exécution de Docker. Par exemple : `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh src docker.for.mac.localhost:4503 8080`.

Les journaux des environnements cloud sont exposés par le biais du service de journalisation disponible dans Cloud Manager.

>[!NOTE]
>
>Pour les environnements sur AEM as a Cloud Service, le débogage est le niveau maximal de verbosité. Le niveau de journalisation de trace n’étant pas pris en charge, évitez de le définir lorsque vous travaillez dans des environnements cloud.

### Rechargement et validation automatiques {#automatic-reloading}

>[!NOTE]
>
>En raison d’une limitation du système d’exploitation Windows, cette fonctionnalité est uniquement disponible pour les utilisateurs et utilisatrices de Linux® et macOS.

Au lieu d’exécuter la validation locale (`validate.sh`) et de démarrer le conteneur Docker (`docker_run.sh`) chaque fois que la configuration est modifiée, vous pouvez également exécuter le script `docker_run_hot_reload.sh`. Le script recherche toutes les modifications apportées à la configuration et la recharge automatiquement, puis exécute à nouveau la validation. L’utilisation de cette option vous permet de gagner beaucoup de temps lors du débogage.

Vous pouvez exécuter le script à l’aide de la commande suivante : `./bin/docker_run_hot_reload.sh src/dispatcher host.docker.internal:4503 8080`

Les premières lignes de sortie ressemblent à ce qui serait exécuté pour `docker_run.sh`. Par exemple :

```
~ bin/docker_run_hot_reload.sh src host.docker.internal:8081 8082
opt-in USE_SOURCES_DIRECTLY marker file detected
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/15-check-pod-name.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until host.docker.internal is available
host.docker.internal resolves to 192.168.65.2
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
Running script /docker_entrypoint.d/80-frontend-domain.sh
Running script /docker_entrypoint.d/zzz-import-sdk-config.sh
WARN Mon Jul  4 09:53:54 UTC 2022: Pseudo symlink conf.d seems to point to a non-existing file!
INFO Mon Jul  4 09:53:55 UTC 2022: Copied customer configuration to /etc/httpd.
INFO Mon Jul  4 09:53:55 UTC 2022: Start testing
Cloud manager validator 2.0.43
2022/07/04 09:53:55 No issues found
INFO Mon Jul  4 09:53:55 UTC 2022: Testing with fresh base configuration files.
INFO Mon Jul  4 09:53:55 UTC 2022: Apache httpd informationServer version: Apache/2.4.54 (Unix)
```

### Injection de variables d’environnement personnalisées {#environment-variables}

Les variables d’environnement personnalisées peuvent être utilisées avec le SDK du Dispatcher en les définissant dans un fichier distinct et en le référençant dans la variable d’environnement `ENV_FILE` avant de démarrer le Dispatcher local.

Un fichier contenant des variables d’environnement personnalisées ressemblerait à ceci :

```
COMMERCE_ENDPOINT=commerce-host
AEM_HTTP_PROXY_HOST=host.docker.internal
AEM_HTTP_PROXY_PORT=8000
```

Et il peut être utilisé dans le SDK du Dispatcher local avec les commandes suivantes :

```
export ENV_FILE=custom.env
./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080
```

## Différentes configurations du Dispatcher par environnement {#different-dispatcher-configurations-per-environment}

Actuellement, la même configuration du Dispatcher est appliquée à tous les environnements AEM as a Cloud Service. Le composant d’exécution comporte une variable d’environnement `ENVIRONMENT_TYPE` qui contient le mode d’exécution actuel (développement, évaluation ou production) et une « définition ». La définition peut être `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` ou `ENVIRONMENT_PROD`. Dans la configuration Apache, la variable peut être utilisée directement dans une expression. Vous pouvez également utiliser la « définition » pour créer une logique :

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

Vous pouvez également utiliser des variables d’environnement Cloud Manager dans votre configuration httpd/dispatcher, mais pas de secrets d’environnement. Cette méthode est particulièrement importante si un programme comporte plusieurs environnements de développement et que certains de ces environnements de développement ont des valeurs différentes pour la configuration httpd/dispatcher. La même syntaxe ${VIRTUALHOST} serait utilisée comme dans l’exemple ci-dessus, mais les déclarations Define dans le fichier de variables ci-dessus ne seraient pas utilisées. Lisez la [Documentation Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) pour obtenir des instructions sur la configuration des variables d’environnement Cloud Manager.

Lors du test local de votre configuration, vous pouvez simuler différents types d’environnements en transmettant directement la variable `DISP_RUN_MODE` au script `docker_run.sh` :

```
$ DISP_RUN_MODE=stage docker_run.sh src docker.for.mac.localhost:4503 8080
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

## Migration du mode hérité vers le mode flexible {#migrating}

Avec la version 2021.7.0 de Cloud Manager, les nouveaux programmes génèrent des structures de projet Maven avec [l’archétype 28 d’AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) ou version ultérieure, qui inclut le fichier **opt-in/USE_SOURCES_DIRECTLY**. Cela supprime les limites précédentes du [mode hérité](/help/implementing/dispatcher/validation-debug-legacy.md) concernant le nombre et la taille des fichiers, ce qui entraîne également la validation et le déploiement améliorés de la configuration par le SDK et l’exécution. Si votre configuration du Dispatcher ne comporte pas ce fichier, il est vivement recommandé de migrer. Pour garantir une transition sécurisée, procédez comme suit :

1. **Test local.**&#x200B;À l’aide du dernier SDK des outils du Dispatcher, ajoutez le dossier et le fichier `opt-in/USE_SOURCES_DIRECTLY`. Suivez les instructions de « validation locale » de cet article pour tester le fonctionnement local du Dispatcher.
1. **Test de développement dans le cloud :**
   * Validez le fichier `opt-in/USE_SOURCES_DIRECTLY` dans une branche git déployée par le pipeline hors production vers un environnement de développement cloud.
   * Utilisez Cloud Manager pour déployer un environnement de développement cloud.
   * Testez minutieusement. Il est essentiel de vérifier que votre configuration Apache et Dispatcher se comporte comme prévu avant de déployer les modifications dans des environnements supérieurs. Vérifiez tous les comportements liés à votre configuration personnalisée. Soumettez un ticket au service clientèle si vous pensez que la configuration du Dispatcher déployée ne reflète pas votre configuration personnalisée.

   >[!NOTE]
   >
   >En mode flexible, vous devez utiliser des chemins d’accès relatifs plutôt que des chemins absolus.
1. **Déploiement en production :**
   * Validez le fichier `opt-in/USE_SOURCES_DIRECTLY` dans une branche git déployée par le pipeline de production vers les environnements d’évaluation et de production Cloud.
   * Utilisez Cloud Manager pour effectuer le déploiement vers l’évaluation.
   * Testez minutieusement. Il est essentiel de vérifier que votre configuration Apache et Dispatcher se comporte comme prévu avant de déployer les modifications dans des environnements supérieurs. Vérifiez tous les comportements liés à votre configuration personnalisée. Soumettez un ticket au service clientèle si vous pensez que la configuration du Dispatcher déployée ne reflète pas votre configuration personnalisée.
   * Utilisez Cloud Manager pour poursuivre le déploiement en production.

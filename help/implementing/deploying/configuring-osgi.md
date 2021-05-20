---
title: Configuration d’OSGi pour Adobe Experience Manager en tant que Cloud Service
description: 'Configuration d’OSGi à l’aide de valeurs secrètes et spécifiques aux environnements '
feature: Déploiement
exl-id: f31bff80-2565-4cd8-8978-d0fd75446e15
source-git-commit: 7baacc953c88e1beb13be9878b635b6e5273dea2
workflow-type: tm+mt
source-wordcount: '2850'
ht-degree: 57%

---

# Configuration d’OSGi pour Adobe Experience Manager en tant que Cloud Service {#configuring-osgi-for-aem-as-a-cloud-service}

Le framework [OSGi](https://www.osgi.org/) est un élément fondamental de la pile technologique d’Adobe Experience Manager (AEM). Il est utilisé pour contrôler les lots composites d’AEM et leurs configurations.

OSGi fournit des primitives normalisées qui permettent de construire des applications à partir de petits composants, réutilisables et collaboratifs. Ces composants peuvent être créés dans une application et déployés. Cela permet une gestion conviviale des lots OSGi, car ils peuvent être arrêtés, installés et démarrés individuellement. Les interdépendances sont gérées automatiquement. Chaque composant OSGi est contenu dans l’un des différents lots. Pour plus d’informations, voir la [spécification OSGi](https://www.osgi.org/Specifications/HomePage).

Vous pouvez gérer les paramètres de configuration des composants OSGi par le biais de fichiers de configuration intégrés à un projet de code AEM.

## Fichiers de configuration OSGi {#osgi-configuration-files}

Les modifications de configuration sont définies dans les packages de code du projet AEM (`ui.apps`) en tant que fichiers de configuration (`.cfg.json`) sous les dossiers de configuration spécifiques au mode d’exécution :

`/apps/example/config.<runmode>`

Le format des fichiers de configuration OSGi est basé sur JSON et utilise le format `.cfg.json` défini par le projet Apache Sling.

Les configurations OSGi ciblent les composants OSGi via leur identifiant persistant (PID), qui correspond par défaut au nom de classe Java™ du composant OSGi. Par exemple, pour fournir une configuration OSGi pour un service OSGi implémenté par :

`com.example.workflow.impl.ApprovalWorkflow.java`

un fichier de configuration OSGi est défini à l’adresse suivante :

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

selon le format de configuration OSGi de cfg.json.

>[!NOTE]
>
>Les versions antérieures d’AEM prenaient en charge les fichiers de configuration OSGi à l’aide de différents formats de fichiers tels que .cfg., .config, ainsi que sous la forme de définitions de ressources XML sling:OsgiConfig. Ces formats sont remplacés par le format de configuration OSGi cfg.json.

## Résolution du mode d’exécution {#runmode-resolution}

Il est possible de cibler des configurations OSGi spécifiques sur des instances AEM données grâce aux modes d’exécution. Pour utiliser un mode d’exécution, créez des dossiers de configuration sous `/apps/example` (« example » correspondant au nom de votre projet), selon le format suivant :

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

Toutes les configurations OSGi de ces dossiers sont utilisées si les modes d’exécution définis dans le nom du dossier de configuration correspondent aux modes d’exécution utilisés par AEM.

Par exemple, si AEM utilise les modes d’exécution author et dev, les noeuds de configuration contenus dans `/apps/example/config.author/` et `/apps/example/config.author.dev/` sont appliqués, tandis que les noeuds de configuration contenus dans `/apps/example/config.publish/` et `/apps/example/config.author.stage/` ne le sont pas.

Si plusieurs configurations correspondant au même PID sont applicables, la configuration comportant le nombre le plus élevé de modes d’exécution correspondants est appliquée.

La granularité de cette règle se trouve au niveau du PID. Vous ne pouvez pas définir certaines propriétés pour le même PID dans `/apps/example/config.author/` et des propriétés plus spécifiques dans `/apps/example/config.author.dev/` pour le même PID. La configuration comportant le plus grand nombre de modes d’exécution correspondants sera effective pour l’ensemble du PID.

Lors du développement local, un paramètre de démarrage du mode d’exécution peut être transmis pour indiquer la configuration OSGI du mode d’exécution utilisée.

## Types de valeurs de configuration OSGi {#types-of-osgi-configuration-values}

Il existe trois types de valeurs de configuration OSGi pouvant être utilisées avec Adobe Experience Manager en tant que Cloud Service.

1. **Valeurs intégrées**, codées en dur dans la configuration OSGi et stockées dans Git. Par exemple :

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **Valeurs secrètes**, qui ne doivent pas être stockées dans Git pour des raisons de sécurité. Par exemple :

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **Valeurs** spécifiques à un environnement, qui varient selon les environnements de développement. Elles ne peuvent donc pas être ciblées avec précision par le mode d’exécution (puisqu’il existe un seul  `dev` mode d’exécution dans Adobe Experience Manager en tant que Cloud Service). Par exemple :

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   Notez qu’un seul fichier de configuration OSGi peut utiliser conjointement n’importe quelle combinaison de ces types de valeurs de configuration. Par exemple :

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## Choix du type de valeur de configuration OSGi approprié {#how-to-choose-the-appropriate-osgi-configuration-value-type}

Le cas le plus courant pour OSGi consiste à utiliser des valeurs de configuration OSGi intégrées. Les configurations spécifiques à un environnement ne s’appliquent que pour des cas d’utilisation spécifiques où une valeur diffère d’un environnement de développement à l’autre.

![](assets/choose-configuration-value-type_res1.png)

Les configurations spécifiques à un environnement étendent les configurations OSGi traditionnelles définies de manière statique, qui contiennent des valeurs intégrées, ce qui permet de gérer les valeurs de configuration OSGi en externe via l’API Cloud Manager. Il est important de comprendre dans quels cas appliquer l’approche la plus courante et traditionnelle consistant à définir les valeurs intégrées et à les stocker dans Git, au lieu de les abstraire dans des configurations spécifiques à un environnement.

Les conseils suivants expliquent dans quels cas utiliser des configurations spécifiques à un environnement, secrètes ou non :

### Cas d’utilisation de valeurs de configuration intégrées {#when-to-use-inline-configuration-values}

Les valeurs de configuration intégrées sont considérées comme l’approche standard à utiliser dans la mesure du possible. Les configurations intégrées offrent les avantages suivants :

* Elles sont gérées à l’aide de règles de gouvernance et d’un historique des versions dans Git.
* Les valeurs sont implicitement liées aux déploiements de code.
* Elles ne nécessitent aucune autre considération ni coordination de déploiement.

Lorsque vous définissez une valeur de configuration OSGi, commencez par des valeurs intégrées et sélectionnez uniquement des configurations secrètes ou spécifiques à un environnement si nécessaire pour le cas d’utilisation.

### Cas d’utilisation de valeurs de configuration non secrètes spécifiques à un environnement {#when-to-use-non-secret-environment-specific-configuration-values}

N’utilisez de configurations spécifiques à un environnement (`$[env:ENV_VAR_NAME]`) que pour les valeurs de configuration non secrètes lorsque ces valeurs varient selon les environnements de développement. Cela inclut les instances de développement locales et les environnements de développement Adobe Experience Manager as a Cloud Service. Évitez d’utiliser des configurations non secrètes spécifiques à un environnement pour Adobe Experience Manager en tant qu’environnements d’évaluation ou de production de Cloud Service.

* Utilisez des configurations non secrètes spécifiques à des environnements uniquement pour les valeurs de configuration qui diffèrent selon les environnements de développement, y compris les instances de développement en local.
* Utilisez plutôt les valeurs intégrées standard dans les configurations OSGi pour les valeurs non secrètes d’évaluation et de production. En relation, il n’est pas recommandé d’utiliser des configurations spécifiques à un environnement pour faciliter les modifications de configuration au moment de l’exécution dans les environnements d’évaluation et de production ; ces modifications doivent être introduites par le biais de la gestion du code source.

### Cas d’utilisation de valeurs secrètes de configuration spécifiques à un environnement {#when-to-use-secret-environment-specific-configuration-values}

Adobe Experience Manager as a Cloud Service nécessite l’utilisation de configurations spécifiques à un environnement (`$[secret:SECRET_VAR_NAME]`) pour toute valeur de configuration OSGi secrète, telle que les mots de passe, les clés d’API privées ou toute autre valeur qui ne peut pas être stockée dans Git pour des raisons de sécurité.

Utilisez des configurations secrètes spécifiques à un environnement pour stocker la valeur des secrets dans tous les environnements Adobe Experience Manager as a Cloud Service, y compris dans les environnements d’évaluation et de production.

## Création de configurations OSGi {#creating-sogi-configurations}

Il existe deux manières de créer des configurations OSGi, comme décrit ci-dessous. La première méthode est en général appliquée pour configurer des composants OSGi personnalisés qui possèdent des propriétés et des valeurs OSGi connues du développeur, la seconde pour les composants OSGi fournis par AEM.

### Écriture de configurations OSGi {#writing-osgi-configurations}

Les fichiers de configuration OSGi au format JSON peuvent être écrits manuellement directement dans le projet AEM. Il s’agit souvent de la méthode la plus rapide pour créer des configurations OSGi pour des composants OSGi connus, et en particulier pour des composants OSGi personnalisés qui ont été conçus et développés par le même développeur qui définit les configurations. Cette approche peut également être utilisée pour copier/coller et mettre à jour des configurations pour le même composant OSGi dans différents dossiers de mode d’exécution.

1. Dans votre IDE, ouvrez le projet `ui.apps`, recherchez ou créez le dossier de configuration (`/apps/.../config.<runmode>`) qui cible les modes d’exécution que la nouvelle configuration OSGi doit appliquer.
1. Dans ce dossier de configuration, créez un fichier `<PID>.cfg.json`. Le PID est l’identité persistante du composant OSGi. Il s’agit généralement du nom de classe complet de l’implémentation du composant OSGi. Par exemple :
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
Notez que les noms des fichiers de configuration OSGi d’usine utilisent la convention d’ `<PID>-<factory-name>.cfg.json` affectation des noms.
1. Ouvrez le nouveau fichier `.cfg.json` et définissez les combinaisons clé/valeur pour les paires propriété et valeur OSGi, en appliquant le [format de configuration OSGi JSON](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).
1. Enregistrez les modifications dans le nouveau fichier `.cfg.json`.
1. Ajoutez et validez votre nouveau fichier de configuration OSGi sur Git.

### Génération de configurations OSGi à l’aide de l’environnement d’exécution Quickstart du SDK AEM  {#generating-osgi-configurations-using-the-aem-sdk-quickstart}

Il est possible d’utiliser la console web AEM de l’environnement d’exécution Quickstart Jar du SDK AEM pour configurer les composants OSGi et exporter les configurations OSGi au format JSON. La console facilite la configuration des composants OSGi fournis par AEM dont les propriétés OSGi et leurs formats de valeurs ne sont pas nécessairement bien maîtrisés par le développeur chargé de définir les configurations OSGi du projet AEM.

>[!NOTE]
>
>L’interface utilisateur de configuration de la console Web d’AEM écrit des fichiers `.cfg.json` dans le référentiel. Par conséquent, n’oubliez pas de le savoir afin d’éviter tout comportement inattendu pendant le développement local, lorsque les configurations OSGi définies par AEM projet peuvent différer des configurations générées.

1. Connectez-vous en tant qu’administrateur à la console web de l’environnement Quickstart Jar du SDK AEM.
1. Accédez à OSGi > Configuration.
1. Pour configurer, recherchez le composant OSGi et appuyez sur son titre pour le modifier.
   ![Configuration OSGi](./assets/configuring-osgi/configuration.png)
1. Modifiez, si nécessaire, les valeurs des propriétés de configuration OSGi à l’aide de l’interface utilisateur web.
1. Enregistrez l’identité persistante (PID) en lieu sûr. Il est utilisé ultérieurement pour générer la configuration OSGi au format JSON.
1. Appuyez sur Enregistrer.
1. Accédez à OSGi > OSGi Installer Configuration Printer (Imprimante de configuration du programme d’installation OSGi).
1. Collez le PID copié à l’étape 5 et assurez-vous que le format de sérialisation est défini sur OSGi Configurator JSON (Configurateur OSGi au format JSON).
1. Appuyez sur Imprimer
1. La configuration OSGi au format JSON s’affichera dans la section Propriétés de configuration sérialisées.
   ![Imprimante de configuration du programme d’installation OSGi](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. Dans votre IDE, ouvrez le projet `ui.apps`, recherchez ou créez le dossier de configuration (`/apps/.../config.<runmode>`) qui cible les modes d’exécution que la nouvelle configuration OSGi doit appliquer.
1. Dans ce dossier de configuration, créez un fichier `<PID>.cfg.json`. Le PID est la même valeur qu’à l’étape 5.
1. Collez les propriétés de configuration sérialisées de l’étape 10 dans le fichier `.cfg.json`.
1. Enregistrez les modifications dans le nouveau fichier `.cfg.json`.
1. Ajoutez et validez votre nouveau fichier de configuration OSGi sur Git.


## Formats des propriétés de configuration OSGi  {#osgi-configuration-property-formats}

### Valeurs intégrées {#inline-values}

Les valeurs intégrées sont formatées sous la forme de paires nom-valeur standard, selon la syntaxe JSON standard. Par exemple :

```json
{
   "my_var1": "val",
   "my_var2": [ "abc", "def" ],
   "my_var3": 500
}
```

### Valeurs de configuration spécifiques à un environnement {#environment-specific-configuration-values}

La configuration OSGi doit attribuer un espace réservé à la variable qui doit être définie pour chaque environnement :

```
use $[env:ENV_VAR_NAME]
```

Les clients ne doivent utiliser cette technique que pour les propriétés de configuration OSGI liées à leur code personnalisé ; il ne doit pas être utilisé pour remplacer la configuration OSGI définie par l’Adobe.

>[!NOTE]
>
>Les espaces réservés ne peuvent pas être utilisés dans les [instructions repoinit](/help/implementing/deploying/overview.md#repoinit).

### Valeurs de configuration secrètes {#secret-configuration-values}

La configuration OSGi doit attribuer un espace réservé au secret qui doit être défini pour chaque environnement :

```
use $[secret:SECRET_VAR_NAME]
```

### Dénomination des variables {#variable-naming}

Les règles ci-dessous s’appliquent à la fois aux valeurs de configuration secrètes et à celles spécifiques à un environnement.

Les noms des variables doivent respecter les règles suivantes :

* Longueur minimale : 2
* Longueur maximale : 100
* Doit correspondre à l’expression régulière : `[a-zA-Z_][a-zA-Z_0-9]*`

Les valeurs des variables ne doivent pas dépasser 2 048 caractères.

>[!NOTE]
>
>Les noms de variables précédés de `INTERNAL_` sont réservés par Adobe. Toutes les variables définies par le client commençant par ce préfixe seront ignorées.

### Valeurs par défaut {#default-values}

Les règles ci-dessous s’appliquent à la fois aux valeurs de configuration secrètes et à celles spécifiques à un environnement.

Si aucune valeur spécifique à l’environnement n’est définie, l’espace réservé n’est pas remplacé au moment de l’exécution et est conservé, car aucune interpolation n’a eu lieu. Pour éviter cette situation, une valeur par défaut peut être fournie dans l’espace réservé selon la syntaxe suivante :

```
$[env:ENV_VAR_NAME;default=<value>]
```

Si une valeur par défaut est fournie, l’espace réservé est remplacé par la valeur par environnement, le cas échéant, ou par la valeur par défaut fournie.

### Développement local {#local-development}

Les règles ci-dessous s’appliquent à la fois aux valeurs de configuration secrètes et à celles spécifiques à un environnement.

Les variables peuvent être définies dans l’environnement local afin d’être récupérées par l’instance AEM locale au moment de l’exécution. Par exemple, sous Linux® :

```bash
export ENV_VAR_NAME=my_value
```

Il est recommandé d’écrire un script bash simple qui définit les variables d’environnement utilisées dans les configurations et qui les exécute avant de démarrer AEM. Il est possible de simplifier cette approche à l’aide d’outils tels que [https://direnv.net/](https://direnv.net/). Selon leurs types, il est possible d’archiver les valeurs dans la gestion du code source (si elles peuvent être partagées avec tous).

Les valeurs des secrets sont lues à partir de fichiers. Par conséquent, pour chaque espace réservé utilisant un secret, un fichier texte contenant la valeur secrète doit être créé.

Par exemple, si `$[secret:server_password]` est utilisé, un fichier texte nommé **server_password** doit être créé. Tous ces fichiers secrets doivent être stockés dans le même répertoire et la propriété framework `org.apache.felix.configadmin.plugin.interpolation.secretsdir` doit être configurée avec ce répertoire local.

### Configuration de création ou de publication {#author-vs-publish-configuration}

Si une propriété OSGI nécessite des valeurs différentes pour la création et la publication :

* Vous devez utiliser des dossiers OSGi `config.author` et `config.publish` distincts, comme décrit dans la [section Résolution du mode d’exécution](#runmode-resolution).
* Deux options permettent de créer des noms de variable indépendants qui doivent être utilisés :
   * la première option, recommandée : dans tous les dossiers OSGI (comme `config.author` et `config.publish`) déclarés pour définir des valeurs différentes, utilisez le même nom de variable. Par exemple :
      `$[env:ENV_VAR_NAME;default=<value>]`, où la valeur par défaut correspond à la valeur par défaut de ce niveau (auteur ou publication). Lors de la définition de la variable d’environnement via [l’API Cloud Manager](#cloud-manager-api-format-for-setting-properties) ou via un client, différenciez les niveaux à l’aide du paramètre &quot;service&quot;, comme décrit dans cette [documentation de référence de l’API](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchEnvironmentVariables). Le paramètre &quot;service&quot; lie la valeur de la variable au niveau OSGI approprié.
   * la deuxième option, qui consiste à déclarer des variables distinctes à l’aide d’un préfixe tel que `author_<samevariablename>` et `publish_<samevariablename>` ;

### Exemples de configurations {#configuration-examples}

Dans les exemples ci-dessous, supposons qu’il existe trois environnements de développement, en plus des environnements d’évaluation et de production.

**Exemple 1**

L’objectif est que la valeur de la propriété OSGI `my_var1` soit la même pour l’évaluation et la production, mais différente pour chacun des trois environnements de développement.

<table>
<tr>
<td>
<b>Dossier</b>
</td>
<td>
<b>Contenu de myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

**Exemple 2**

L’objectif est que la valeur de la propriété OSGI `my_var1` soit différente pour l’évaluation, la production et pour chacun des trois environnements de développement. L’API Cloud Manager doit donc être appelée pour définir la valeur de `my_var1` pour chaque environnement de développement.

<table>
<tr>
<td>
<b>Dossier</b>
</td>
<td>
<b>Contenu de myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config.stage
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.prod
</td>
<td>
<pre>
{ 
 "my_var1": "val2",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2" : "abc",
 "my_var3" : 500
}
</pre>
</td>
</tr>
</table>

**Exemple 3**

L’objectif est que la valeur de la propriété OSGi `my_var1` soit identique pour l’évaluation, la production et un seul des environnements de développement, mais différente pour les deux autres. Dans ce cas, l’API Cloud Manager doit être appelée pour définir la valeur de `my_var1` pour chacun des environnements de développement, y compris celui qui doit avoir la même valeur que l’évaluation et la production. Il n’héritera pas de la valeur définie dans le dossier **config**.

<table>
<tr>
<td>
<b>Dossier</b>
</td>
<td>
<b>Contenu de myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1" : "val1",
 "my_var2" : "abc",
 "my_var3" : 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2" : "abc",
 "my_var3" : 500
}
</pre>
</td>
</tr>
</table>

Vous pouvez également définir une valeur par défaut pour le jeton de remplacement dans le dossier config.dev, de sorte qu’elle soit identique à celle du dossier **config**.

<table>
<tr>
<td>
<b>Dossier</b>
</td>
<td>
<b>Contenu de myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1" : "val1",
 "my_var2" : "abc",
 "my_var3" : 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1": "$[env:my_var1;default=val1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

## Format de l’API Cloud Manager pour la définition des propriétés {#cloud-manager-api-format-for-setting-properties}

Voir [cette page](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md) à propos de la configuration de l’API.
>[!NOTE]
>
>Assurez-vous que l’API Cloud Manager utilisée a attribué le rôle « Responsable de déploiement – Cloud Service ». Les autres rôles ne peuvent pas exécuter toutes les commandes ci-dessous.

### Définition de valeurs via l’API {#setting-values-via-api}

L’appel de l’API déploie les nouvelles variables et valeurs dans un environnement cloud, comme pour un pipeline de déploiement de code client classique. Les services de création et de publication sont redémarrés et font référence aux nouvelles valeurs, généralement en quelques minutes.

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

```
]
        {
                "name" : "MY_VAR1",
                "value" : "plaintext value",
                "type" : "string"  <---default
        },
        {
                "name" : "MY_VAR2",
                "value" : "<secret value>",
                "type" : "secretString"
        }
]
```

>[!NOTE]
>Les variables par défaut ne sont pas définies via l’API, mais dans la propriété OSGi elle-même.
>
>Pour plus d’informations, consultez [cette page](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables).

### Obtention de valeurs via l’API {#getting-values-via-api}

```
GET /program/{programId}/environment/{environmentId}/variables
```

Pour plus d’informations, consultez [cette page](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/getEnvironmentVariables).

### Suppression de valeurs via l’API {#deleting-values-via-api}

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

Pour supprimer une variable, indiquez-la avec une valeur vide.

Pour plus d’informations, consultez [cette page](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables).

### Obtention de valeurs via la ligne de commande {#getting-values-via-cli}

```bash
$ aio cloudmanager:list-environment-variables ENVIRONMENT_ID
Name     Type         Value
MY_VAR1  string       plaintext value 
MY_VAR2  secretString ****
```


### Définition de valeurs via la ligne de commande {#setting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable MY_VAR1 "plaintext value" --secret MY_VAR2 "some secret value"
```

### Suppression de valeurs via la ligne de commande {#deleting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --delete MY_VAR1 MY_VAR2
```

>[!NOTE]
>
>Voir [cette page](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) pour plus d’informations sur la configuration des valeurs à l’aide du plug-in d’interface de ligne de commande Adobe I/O de Cloud Manager.

### Nombre de variables {#number-of-variables}

Jusqu’à 200 variables peuvent être déclarées par environnement.

## Considérations relatives au déploiement pour les valeurs de configuration secrètes et spécifiques à un environnement {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

Étant donné que les valeurs de configuration secrètes et spécifiques à l’environnement résident en dehors de Git et ne font donc pas partie des mécanismes de déploiement officiels d’Adobe Experience Manager en tant que Cloud Service, le client doit gérer, gouverner et intégrer le processus de déploiement d’Adobe Experience Manager en tant que Cloud Service.

Comme mentionné ci-dessus, l’appel de l’API déploie les nouvelles variables et valeurs dans les environnements cloud, comme pour un pipeline de déploiement de code client classique. Les services de création et de publication sont redémarrés et font référence aux nouvelles valeurs, généralement en quelques minutes. Notez que les points de contrôle et tests de qualité exécutés par Cloud Manager pour un déploiement normal de code ne sont pas effectués pendant ce processus.

En règle générale, les clients appellent l’API pour définir les variables d’environnement avant de déployer le code associé dans Cloud Manager. Dans certains cas, vous pouvez modifier une variable existante après le déploiement du code.

>[!NOTE]
>
>L’API peut ne pas réussir lorsqu’un pipeline est en cours d’utilisation, qu’il s’agisse d’une mise à jour AEM ou d’un déploiement client, selon la partie du pipeline de bout en bout exécutée à ce moment-là. L’erreur renvoyée indique que la demande a échoué, sans fournir de raison précise.

Dans certains scénarios, le déploiement du code client planifié nécessite de définir de nouvelles valeurs pour les variables existantes, ce qui n’est pas approprié avec le code en l’état. S’il s’agit d’un problème, il est recommandé d’apporter des modifications variables de manière additive. Pour ce faire, créez des noms de variable au lieu de simplement modifier la valeur des anciennes. Ainsi, l’ancien code ne fera jamais référence à la nouvelle valeur. Ensuite, lorsque la nouvelle version client semble stable, vous pouvez supprimer les anciennes valeurs.

De même, comme les versions des valeurs d’une variable ne sont pas contrôlées, une restauration du code pourrait entraîner des références à des valeurs plus récentes qui posent problème. La stratégie d’ajout de variables mentionnée précédemment peut également y contribuer.

Cette stratégie d’ajout de variables est également utile pour les scénarios de reprise après sinistre. Dans ce cas, si une version de code datée de plusieurs jours doit être redéployée, les noms et les valeurs de variables auxquels il fait référence restent inchangés. Cette démarche s’appuie sur une stratégie prévoyant qu’un client attend quelques jours avant de supprimer les variables plus anciennes. Dans le cas contraire, l’ancien code ne pourrait pas faire référence aux variables appropriées.

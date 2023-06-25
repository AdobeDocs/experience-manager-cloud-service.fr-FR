---
title: Migration de la configuration Dispatcher d’AMS vers AEM as a Cloud Service
description: Migration de la configuration Dispatcher d’AMS vers AEM as a Cloud Service
feature: Dispatcher
exl-id: ff7397dd-b6e1-4d08-8e2d-d613af6b81b3
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '1446'
ht-degree: 97%

---

# Migration de la configuration Dispatcher d’AMS vers AEM as a Cloud Service {#Dispatcher-in-the-cloud}

## Principales différences entre AMS Dispatcher et AEM as a Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

La configuration Apache et Dispatcher dans AEM as a Cloud Service est assez similaire à la configuration AMS. Les principales différences sont :

* Dans AEM as a Cloud Service, certaines directives Apache peuvent ne pas être utilisées (par exemple, `Listen` ou `LogLevel`)
* Dans AEM as a Cloud Service, seules certaines parties de la configuration Dispatcher peuvent être placées dans les fichiers d’inclusion et les noms qui leur sont donnés sont importants. Par exemple, les règles de filtrage que vous souhaitez réutiliser sur différents hôtes doivent être placées dans un fichier nommé `filters/filters.any`. Consultez la page de référence pour plus d’informations.
* Dans AEM as a Cloud Service, il existe une validation supplémentaire pour interdire les règles de filtrage écrites avec `/glob` de façon à éviter les problèmes de sécurité. Parce que `deny *` est utilisé plutôt que `allow *` (qui ne peut pas être utilisé), les clients bénéficient de l’exécution locale de Dispatcher et de la vérification par tâtonnements, en examinant les journaux pour savoir exactement quels chemins sont bloqués par les filtres Dispatcher afin de pouvoir les ajouter.

## Instructions relatives à la migration de la configuration Dispatcher d’AMS vers AEM as a Cloud Service

La structure de configuration Dispatcher présente des différences entre Managed Services et AEM as a Cloud Service. Vous trouverez ci-dessous un guide détaillé sur la migration de la configuration Dispatcher d’AMS version 2 vers AEM as Cloud Service.

## Comment convertir une configuration Dispatcher AMS en configuration AEM as a Cloud Service

La section suivante fournit des instructions étape par étape pour convertir une configuration AMS. Elle suppose
que vous disposez d’une archive avec une structure similaire à celle décrite dans la [configuration Dispatcher Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html?lang=fr).

### Extraire l’archive et supprimer tout préfixe

Extrayez l’archive dans un dossier et assurez-vous que les noms des sous-dossiers immédiats commencent par `conf`, `conf.d`,
`conf.dispatcher.d` et `conf.modules.d`. Si tel n’est pas le cas, déplacez-les dans la hiérarchie.

### Supprimer les sous-dossiers et fichiers non utilisés

Supprimez les sous-dossiers `conf` et `conf.modules.d`, ainsi que les fichiers correspondants à `conf.d/*.conf`.

### Supprimer tous les hôtes virtuels non publiés

Supprimez tout fichier d’hôte virtuel dans `conf.d/enabled_vhosts` dont le nom inclut `author`, `unhealthy`, `health`,
`lc` ou `flush`. Tous les fichiers d’hôtes virtuels dans `conf.d/available_vhosts` non
liés peuvent également être supprimés.

### Supprimer ou mettre en commentaires les sections d’hôte virtuel qui ne font pas référence au port 80

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

### Supprimer des listes autorisées

Supprimez le dossier `conf.d/whitelists` et les instructions `Include` des fichiers d’hôtes virtuels faisant référence à
un fichier de ce sous-dossier.

### Remplacer toute variable qui n’est plus disponible

Dans tous les fichiers d’hôtes virtuels :

Renommez `PUBLISH_DOCROOT` en `DOCROOT`
Supprimez les sections faisant référence à des variables nommées `DISP_ID`, `PUBLISH_FORCE_SSL` ou `PUBLISH_WHITELIST_ENABLED`

### Vérifier votre état en exécutant le programme de validation

Exécutez le programme de validation du Dispatcher dans votre répertoire, avec la sous-commande `httpd` :

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

Toutes les fermes dans `conf.d/enabled_farms` doivent être renommées afin de correspondre au motif `*.farm`. Par exemple, le
fichier de ferme appelé `customerX_farm.any` doit être renommé `customerX.farm`.

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

Exécutez le programme de validation du Dispatcher AEM as a Cloud Service dans votre répertoire, avec la sous-commande `dispatcher` :

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

### Étape 2 : démarrer le Dispatcher dans une image Docker avec ces informations de déploiement

Avec votre serveur de publication AEM en exécution sur votre ordinateur macOS et en écoutant le port 4503,
vous pouvez lancer le Dispatcher devant ce serveur comme suit :

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Cela démarrera le conteneur et exposera Apache sur le port local 8080.

### Utiliser votre nouvelle configuration Dispatcher

Félicitations. Si le programme de validation ne signale plus aucun problème et que le conteneur Docker démarre sans erreur ni avertissement, vous êtes prêt à déplacer votre configuration vers un sous-répertoire `dispatcher/src` de votre référentiel git.

**Les clients qui utilisent la version 1 de la configuration AMS Dispatcher doivent contacter le service clientèle pour les aider à migrer à la version 2 afin de pouvoir suivre les instructions ci-dessus.**

---
title: Conversion d’une configuration AMS en configuration de Dispatcher Adobe Experience Manager as a Cloud Service
description: Conversion d’une configuration AMS en configuration de Dispatcher Adobe Experience Manager as a Cloud Service
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 97%

---


# Conversion d’une configuration AMS en configuration de Dispatcher Adobe Experience Manager (AEM) as a Cloud Service

## Présentation {#introduction}

Cette section fournit des instructions étape par étape pour convertir une configuration AMS.

>[!NOTE]
>Elle suppose que vous disposiez d’une archive possédant une structure similaire à celle décrite dans [Gestion des configurations du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/dispatcher-configurations.html?lang=fr).

## Étapes de conversion d’une configuration AMS en configuration de Dispatcher Adobe Experience Manager (AEM) as a Cloud Service

1. **Extraire l’archive et supprimer tout préfixe**

   Extrayez l’archive dans un dossier et assurez-vous que les premiers sous-dossiers commencent par conf, conf.d, conf.dispatcher.d et conf.modules.d. Si tel n’est pas le cas, déplacez-les vers le haut de la hiérarchie.

1. **Supprimer les sous-dossiers et fichiers non utilisés**

   Supprimez les sous-dossiers conf et conf.modules.d, ainsi que les fichiers correspondant à conf.d/*.conf.

1. **Supprimer tous les hôtes virtuels non publiés**

1. **Supprimer tous les fichiers d’hôtes virtuels**

   Dans les hôtes conf.d/enabled_vhosts dont le nom contient les mentions author, unhealthy, health, lc ou flush. Tous les fichiers d’hôtes virtuels contenus dans conf.d/available_vhosts et non liés peuvent également être supprimés.

1. Supprimer ou mettre en commentaires les sections d’hôte virtuel qui ne font pas référence au port 80

   Si vous avez encore des sections dans vos fichiers d’hôtes virtuels qui font exclusivement référence à d’autres ports que le port 80, par exemple,

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`
supprimez-les ou mettez-les en commentaires. Les instructions de ces sections ne sont pas traitées, mais si vous les conservez, vous pourriez tout de même finir par les modifier sans effet, ce qui peut porter à confusion.

1. **Vérifier les réécritures**

   * Accédez au répertoire conf.d/rewrites.

   * Supprimez les fichiers nommés base_rewrite.rules et xforwarded_forcessl_rewrite.rules, et veillez à supprimer les instructions Include dans les fichiers d’hôtes virtuels qui y font référence.

   * Si conf.d/rewrites contient maintenant un seul fichier, il doit être renommé rewrite.rules. De plus, veillez à adapter les instructions Include se rapportant à ce fichier dans les fichiers d’hôtes virtuels.

   * Si le dossier contient toutefois plusieurs fichiers spécifiques à l’hôte virtuel, leur contenu doit être placé dans l’instruction qui y fait référence dans les fichiers d’hôtes virtuels.

1. **Vérifier les variables**

   1. Accédez au répertoire conf.d/variables.

   1. Supprimez tout fichier nommé ams_default.vars et pensez à supprimer les instructions Include dans les fichiers d’hôtes virtuels qui y font référence.

   1. Si conf.d/variables contient un seul fichier, il doit être renommé custom.vars. De plus, veillez à adapter les instructions Include se rapportant à ce fichier dans les fichiers d’hôtes virtuels.

   1. Si le dossier contient toutefois plusieurs fichiers spécifiques à l’hôte virtuel, leur contenu doit être placé dans l’instruction qui y fait référence dans les fichiers d’hôtes virtuels.

1. **Supprimer les listes blanches**

   Supprimez le dossier conf.d/whitelists et les instructions Include des fichiers d’hôtes virtuels faisant référence à un fichier de ce sous-dossier.

1. **Remplacer toute variable qui n’est plus disponible**

   Dans tous les fichiers d’hôtes virtuels :

   Renommez PUBLISH_DOCROOT en DOCROOT
Supprimez les sections faisant référence à des variables appelées DISP_ID, PUBLISH_FORCE_SSL ou PUBLISH_WHITELIST_ENABLED

1. **Vérifier l’état en exécutant le programme de validation**

   Exécutez le programme de validation du Dispatcher dans votre répertoire, avec la sous-commande httpd :

   `$ validator httpd`
Si des erreurs s’affichent au sujet de fichiers &quot;include&quot; manquants, vérifiez si vous avez correctement renommé ces fichiers.

   Si vous voyez des directives Apache qui ne sont pas placées sur liste blanche, supprimez-les.

1. **Supprimer toutes les fermes non publiées**

   Supprimez tout fichier de batterie présent dans conf.dispatcher.d/enabled_farms dont le nom contient les mentions suivantes : author, unhealthy, health, lc ou flush. Tous les fichiers de fermes contenus dans conf.dispatcher.d/available_farms, et non liés, peuvent également être supprimés.

1. **Renommer les fichiers de fermes**

   Toutes les batteries dans conf.dispatcher.d/enabled_farms doivent être renommées pour correspondre au modèle *.farm. Par exemple, renomez `customerX_farm.any` en `customerX.farm`.

1. **Vérifier le cache**

   Accédez au répertoire conf.dispatcher.d/cache.

   Supprimez tout fichier portant le préfixe `ams_`.

   Si conf.dispatcher.d/cache est vide, copiez le fichier `conf.dispatcher.d/cache/rules.any` depuis la configuration du Dispatcher vers ce dossier. La configuration du Dispatcher standard se trouve dans le dossier src de ce SDK. N’oubliez pas d’adapter également les instructions $include qui font référence aux fichiers de règles `ams_*_cache.any` dans les fichiers de batterie.

   Si au lieu de cela, conf.dispatcher.d/cache contient un seul fichier portant le suffixe `_cache.any`, il doit être renommé en `rules.any`. N’oubliez pas d’adapter également les instructions $include se rapportant à ce fichier dans les fichiers de batterie.

   Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu doit être copié dans l’instruction $include qui y fait référence dans les fichiers de batterie.

   Supprimez tout fichier portant le suffixe `_invalidate_allowed.any`.

   Copiez le fichier conf.dispatcher.d/cache/default_invalidate_any depuis la configuration par défaut du Dispatcher vers cet emplacement.

   Dans chaque fichier de ferme, supprimez tout contenu éventuel présent dans la section cache/allowedClients et remplacez-le par :

   $include &quot;../cache/default_invalidate.any&quot;

1. **Vérifier les en-têtes de client**

   Accédez au répertoire conf.dispatcher.d/clientheaders.

   Supprimez tout fichier portant le préfixe `ams_`.

   Si conf.dispatcher.d/clientheaders contient un seul fichier portant le suffixe `_clientheaders.any`, renommez-le en `clientheaders.any`. N’oubliez pas d’adapter également les instructions $include se rapportant à ce fichier dans les fichiers de batterie.

   Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu doit être copié dans l’instruction $include qui y fait référence dans les fichiers de batterie.

   Copiez le fichier `conf.dispatcher/clientheaders/default_clientheaders.any` depuis la configuration du Dispatcher par défaut vers cet emplacement.

   Dans chaque fichier de batterie, remplacez toute instruction `clientheader` « include » qui s’affiche comme suit :

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   par l’instruction suivante :

   `$include "../clientheaders/default_clientheaders.any"`

1. **Vérifier le filtre**

   * Accédez au répertoire conf.dispatcher.d/filters.

   * Supprimez tout fichier portant le préfixe `ams_`.

   * Si conf.dispatcher.d/filters contient un seul fichier, renommez-le en `filters.any`. N’oubliez pas d’adapter également les instructions $include se rapportant à ce fichier dans les fichiers de batterie.

   * Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu doit être copié dans l’instruction $include qui y fait référence dans les fichiers de batterie.

   * Copiez le fichier `conf.dispatcher/filters/default_filters.any` depuis la configuration du Dispatcher par défaut vers cet emplacement.

   * Dans chaque fichier de batterie, remplacez les instructions d’inclusion de filtre qui se présentent comme suit :

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`
avec l’instruction :

     `$include "../filters/default_filters.any"`

1. **Vérifier les rendus**

   * Accédez au répertoire directory conf.dispatcher.d/renders.

   * Supprimez tous les fichiers de ce dossier.

   * Copiez le fichier `conf.dispatcher.d/renders/default_renders.any` de la configuration du Dispatcher par défaut vers cet emplacement.

   * Dans chaque fichier de ferme, supprimez tous les contenus éventuels de la section renders et remplacez-les par :

     `$include "../renders/default_renders.any"`

1. **Vérifier les hôtes virtuels**

   * Renommez le répertoire `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` et accédez-y.

   * Supprimez tout fichier portant le préfixe `ams_`.

   * Si conf.dispatcher.d/virtualhosts contient maintenant un seul fichier, renommez-le en `virtualhosts.any`. N’oubliez pas d’adapter également les instructions $include se rapportant à ce fichier dans les fichiers de batterie.

   * Si le dossier contient toutefois plusieurs fichiers spécifiques à la ferme avec ce motif, leur contenu doit être copié dans l’instruction $include qui y fait référence dans les fichiers de batterie.

   * Copiez le fichier `conf.dispatcher/virtualhosts/default_virtualhosts.any` depuis la configuration du Dispatcher par défaut vers cet emplacement.

   * Dans chaque fichier de batterie, remplacez les instructions d’inclusion de filtre qui se présentent comme suit :

     `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
par l’instruction suivante :

     `$include "../virtualhosts/default_virtualhosts.any"`


1. **Vérifier l’état en exécutant le programme de validation**

   * Exécutez le programme de validation du Dispatcher dans votre répertoire, avec la sous-commande du Dispatcher :

     `$ validator dispatcher`

   * Si des erreurs s’affichent au sujet de fichiers &quot;include&quot; manquants, vérifiez si vous avez correctement renommé ces fichiers.

   * Si des erreurs s’affichent concernant une variable `PUBLISH_DOCROOT` non définie, renommez-la `DOCROOT`.

   * Pour toute autre erreur, consultez la section Dépannage de la documentation du programme de validation.

## Test de votre configuration avec un déploiement local {#testing-config-local-deployment}

>[!IMPORTANT]
>
>Le test de votre configuration avec un déploiement local nécessite l’installation de Docker.

Grâce au script `docker_run.sh` des outils Dispatcher, vous pouvez tester si votre configuration ne contient aucune autre erreur qui ne s’afficherait que lors du déploiement :

1. générer des informations de déploiement avec le programme de validation.

   `validator full -d out`
Valide la configuration complète et génère les informations de déploiement en sortie (out).

1. Démarrez le Dispatcher dans une image Docker avec ces informations de déploiement.

   Avec votre serveur de publication AEM en exécution sur votre ordinateur macOS et en écoutant le port 4503, vous pouvez lancer le Dispatcher devant ce serveur comme suit :

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Démarre le conteneur et expose Apache sur le port local 8080.

## Utiliser votre nouvelle configuration du Dispatcher {#using-dispatcher-config}

Si le programme de validation ne signale plus aucun problème et que le conteneur Docker démarre sans erreur ni avertissement, vous êtes prêt à déplacer votre configuration vers un sous-répertoire d`ispatcher/src` de votre référentiel git.
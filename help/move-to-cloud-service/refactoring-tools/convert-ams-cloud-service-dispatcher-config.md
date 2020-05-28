---
title: Conversion d’un fichier AMS en un Adobe Experience Manager en tant que configuration du répartiteur de services Cloud
description: Conversion d’un fichier AMS en un Adobe Experience Manager en tant que configuration du répartiteur de services Cloud
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 22%

---


# Conversion d’un fichier AMS en un fichier Adobe Experience Manager (AEM) en tant que configuration du répartiteur de services Cloud

## Présentation {#introduction}

Cette section fournit des instructions détaillées sur la conversion d’une configuration AMS.

>[!NOTE]
>It assumes that you have an archive with a structure similar to the one described in [Manage your Dispatcher Configurations](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html).

## Etapes de conversion d’un fichier AMS en AEM en tant que configuration du répartiteur de services Cloud

1. **Extraire l’archive et supprimer tout préfixe**

   Extrayez l’archive dans un dossier et assurez-vous que les sous-dossiers immédiats sont débuts avec conf, conf.d, conf.dispatcher.d et conf.modules.d. S&#39;ils ne le font pas, déplacez-les dans la hiérarchie.

1. **Supprimer les sous-dossiers et fichiers non utilisés**

   Supprimez les sous-dossiers conf et conf.modules.d, ainsi que les fichiers correspondant à conf.d/*.conf.

1. **Supprimer tous les hôtes virtuels non publiés**

1. **Supprimer tout fichier hôte virtuel**

   Dans conf.d/enabled_vhosts dont le nom contient des noms d’auteur, malsain, santé, lc ou flush. Tous les fichiers hôtes virtuels dans conf.d/available_vhosts qui ne sont pas liés peuvent également être supprimés.

1. Supprimer ou commenter les sections d’hôte virtuel qui ne font pas référence au port 80

   Si des sections de vos fichiers d’hôtes virtuels font encore référence exclusivement à d’autres ports que le port 80, par exemple :

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`
supprimez-les ou commentez-les. Les instructions de ces sections ne seront pas traitées, mais si vous
les conservez, vous pourriez tout de même finir par les modifier sans effet, ce qui peut porter à confusion.

1. **Vérifier les réécritures**

   * Entrez le répertoire conf.d/rewrite.

   * Supprimez tout fichier nommé base_rewrite.rules et xuplo_forcessl_rewrite.rules et n&#39;oubliez pas de supprimer les instructions Include dans les fichiers d&#39;hôtes virtuels qui y font référence.

   * Si conf.d/rewrite contient désormais un seul fichier, il doit être renommé rewrite.rules et n&#39;oubliez pas d&#39;adapter les instructions Include faisant référence à ce fichier dans les fichiers hôtes virtuels.

   * Si le dossier contient toutefois plusieurs fichiers spécifiques à l&#39;hôte virtuel, leur contenu doit être copié dans l&#39;instruction Include qui y fait référence dans les fichiers hôtes virtuels.

1. **Vérifier les variables**

   1. Entrez le répertoire conf.d/variables.

   1. Supprimez tout fichier nommé ams_default.vars et n&#39;oubliez pas de supprimer les instructions Include dans les fichiers hôtes virtuels qui y font référence.

   1. Si conf.d/variables contient désormais un seul fichier, il doit être renommé custom.vars et n&#39;oubliez pas d&#39;adapter les instructions Include faisant référence à ce fichier dans les fichiers hôtes virtuels.

   1. Si le dossier contient toutefois plusieurs fichiers spécifiques à l&#39;hôte virtuel, leur contenu doit être copié dans l&#39;instruction Include qui y fait référence dans les fichiers hôtes virtuels.

1. **Supprimer les listes blanches**

   Supprimez le dossier conf.d/whitelists et supprimez les instructions Include dans les fichiers hôtes virtuels faisant référence à un fichier de ce sous-dossier.

1. **Remplacer toute variable qui n’est plus disponible**

   Dans tous les fichiers d’hôtes virtuels :

   Renommez PUBLISH_DOCROOT en DOCROOTRemove des sections faisant référence à des variables appelées DISP_ID, PUBLISH_FORCE_SSL ou PUBLISH_WHITELIST_ENABLED

1. **Vérifier votre état en exécutant le programme de validation**

   Exécutez le programme de validation du répartiteur dans votre répertoire, avec la sous-commande httpd :

   `$ validator httpd`
Si des erreurs s’affichent au sujet de fichiers d’inclusion manquants, vérifiez si vous avez correctement renommé
les fichiers en question.

   Si vous voyez des directives Apache qui ne sont pas placées sur liste blanche, supprimez-les.

1. **Supprimer toutes les fermes non publiées**

   Supprimez tout fichier de batterie de serveurs dans conf.dispatcher.d/enabled_fermes dont le nom contient les éléments suivants : auteur, malsain, santé, lc ou vidage. Tous les fichiers de batterie dans conf.dispatcher.d/available_fermes qui ne sont pas liés peuvent également être supprimés.

1. **Renommer les fichiers de fermes**

   Toutes les fermes de conf.dispatcher.d/enabled_fermes doivent être renommées pour correspondre au modèle *.batterie, par exemple un fichier de ferme appelé customerX_Farm.any doit être renommé customerX.batterie.

1. **Vérifier le cache**

   Entrez le répertoire conf.dispatcher.d/cache.

   Supprimez tout fichier préfixé ams_.

   Si conf.dispatcher.d/cache est maintenant vide, copiez le fichier conf.dispatcher.d/cache/rules.any de la configuration du répartiteur standard dans ce dossier. La configuration du répartiteur standard se trouve dans le dossier src de ce SDK. N&#39;oubliez pas d&#39;adapter les instructions $include faisant référence aux fichiers de règles ams_*_cache.any dans les fichiers de batterie de serveurs.

   Si, à la place, conf.dispatcher.d/cache contient désormais un seul fichier avec le suffixe _cache.any, il doit être renommé règles.any et n&#39;oubliez pas d&#39;adapter les instructions $include se référant à ce fichier dans les fichiers de batterie de serveurs.

   Si le dossier contient toutefois plusieurs fichiers spécifiques à la batterie avec ce modèle, leur contenu doit être copié dans l&#39;instruction $include qui y fait référence dans les fichiers de batterie de serveurs.

   Supprimez tout fichier contenant le suffixe _invalidate_allowed.any.

   Copiez le fichier conf.dispatcher.d/cache/default_invalidate_any de la configuration du répartiteur par défaut vers cet emplacement.

   Dans chaque fichier de batterie, supprimez tout contenu de la section cache/allowedClients et remplacez-le par :

   $include &quot;../cache/default_invalidate.any&quot;

1. **Vérifier les en-têtes de client**

   Entrez le répertoire conf.dispatcher.d/clientheaders.

   Supprimez tout fichier préfixé ams_.

   Si conf.dispatcher.d/clientheaders contient désormais un seul fichier avec le suffixe _clientheaders.any, il doit être renommé clientheaders.any et n&#39;oubliez pas d&#39;adapter les instructions $include faisant référence à ce fichier dans les fichiers de batterie de serveurs.

   Si le dossier contient toutefois plusieurs fichiers spécifiques à la batterie avec ce modèle, leur contenu doit être copié dans l&#39;instruction $include qui y fait référence dans les fichiers de batterie de serveurs.

   Copiez le fichier conf.dispatcher/clientheaders/default_clientheaders.any de la configuration du répartiteur par défaut vers cet emplacement.

   Dans chaque fichier de ferme, remplacez les instructions d’inclusion clientheader qui se présentent comme suit :

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   par l’instruction suivante :

   `$include "../clientheaders/default_clientheaders.any"`

1. **Vérifier le filtre**

   * Entrez le répertoire conf.dispatcher.d/filtres.

   * Supprimez tout fichier préfixé ams_.

   * Si conf.dispatcher.d/filtres contient maintenant un seul fichier, il doit être renommé filtres.any et n&#39;oubliez pas d&#39;adapter les instructions $include faisant référence à ce fichier dans les fichiers de batterie de serveurs.

   * Si le dossier contient toutefois plusieurs fichiers spécifiques à la batterie avec ce modèle, leur contenu doit être copié dans l&#39;instruction $include qui y fait référence dans les fichiers de batterie de serveurs.

   * Copiez le fichier conf.dispatcher/filters/default_filters.any de la configuration du répartiteur par défaut vers cet emplacement.

   * Dans chaque fichier de ferme, remplacez les instructions d’inclusion de filtre qui se présentent comme suit :

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`avec le relevé :

      `$include "../filters/default_filters.any"`

1. **Vérifier les rendus**

   * Entrez le répertoire conf.dispatcher.d/renders.

   * Supprimez tous les fichiers de ce dossier.

   * Copiez le fichier conf.dispatcher.d/renders/default_renders.any de la configuration du répartiteur par défaut vers cet emplacement.

   * Dans chaque fichier de batterie, supprimez tout contenu de la section de rendu et remplacez-le par :

      `$include "../renders/default_renders.any"`

1. **Vérifier les hôtes virtuels**

   * Rename the directory `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` and enter it.

   * Supprimez tout fichier portant le préfixe `ams_`.

   * Si conf.dispatcher.d/virtualhosts contient désormais un seul fichier, il doit être renommé virtualhosts.any et n&#39;oubliez pas d&#39;adapter les instructions $include faisant référence à ce fichier dans les fichiers de batterie de serveurs.

   * Si le dossier contient toutefois plusieurs fichiers spécifiques à la batterie avec ce modèle, leur contenu doit être copié dans l&#39;instruction $include qui y fait référence dans les fichiers de batterie de serveurs.

   * Copiez le fichier conf.dispatcher/virtualhosts/default_virtualhosts.any de la configuration du répartiteur par défaut vers cet emplacement.

   * Dans chaque fichier de ferme, remplacez les instructions d’inclusion de filtre qui se présentent comme suit :

      `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`par l’instruction suivante :

      `$include "../virtualhosts/default_virtualhosts.any"`


1. **Vérifier votre état en exécutant le programme de validation**

   * Exécutez le programme de validation du répartiteur dans votre répertoire, avec la sous-commande dispatcher :

      `$ validator dispatcher`

   * Si des erreurs s’affichent au sujet de fichiers d’inclusion manquants, vérifiez si vous avez correctement renommé
les fichiers en question.

   * Si des erreurs s’affichent concernant une variable non définie `PUBLISH_DOCROOT`, renommez-la `DOCROOT`.

   * Pour toute autre erreur, consultez la section Dépannage de la documentation
du programme de validation.

## Test de votre configuration avec un déploiement local {#testing-config-local-deployment}

>[!IMPORTANT]
> Le test de votre configuration avec un déploiement local requiert l&#39;installation du Docker.

Using the script `docker_run.sh` in the Dispatcher SDK, you can test that your configuration does not contain any other error that would only show up in deployment:

1. Générer des informations de déploiement avec le validateur

   `validator full -d out`
Ceci valide la configuration complète et génère des informations de déploiement dans la fonction

1. Début du répartiteur dans une image de station d&#39;accueil avec ces informations de déploiement

   Avec votre serveur de publication AEM en exécution sur votre ordinateur macOS et écoutant le port 4503,
vous pouvez lancer Dispatcher devant ce serveur comme suit :

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Cela démarrera le conteneur et exposera Apache sur le port local 8080.

## Using your new dispatcher configuration {#using-dispatcher-config}

If the validator no longer reports any issue and the docker container starts up without any failures or warnings, you are ready to move your configuration to a d`ispatcher/src` subdirectory of your git repository.
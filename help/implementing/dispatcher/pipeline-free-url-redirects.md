---
title: Redirections d’URL sans pipeline
description: Découvrez comment déclarer des redirections 301 ou 302 sans accès aux pipelines Git ou Cloud Manager.
feature: Dispatcher
role: Admin
exl-id: dacb1eda-79e0-4e76-926a-92b33bc784de
source-git-commit: e30a9fbe74f1f5cd8a924dc3fec140fad5e0a164
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 1%

---

# Redirections d’URL sans pipeline {#pipeline-free-redirects}

Pour diverses raisons, les organisations réécrivent les URL d’une manière qui entraîne une redirection 301 (ou 302), ce qui signifie que le navigateur est redirigé vers une autre page.

Les scénarios incluent :

* Une page d’HTML supprimée, de sorte que l’utilisateur ou l’utilisatrice est redirigé vers une page de remplacement (parfois la page d’accueil) plutôt que de voir une erreur `404 Page Not Found`.
* Une page d’HTML renommée.
* Optimisation de l’optimisation pour les moteurs de recherche.

AEM as a Cloud Service propose [plusieurs approches](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/administration/url-redirection) pour implémenter les redirections côté client, mais la stratégie décrite dans cet article, redirections sans pipeline, est un bon choix lorsque :

* Les personnes qui gèrent les redirections sont les utilisateurs professionnels, qui n’ont pas l’accès nécessaire pour valider les modifications de fichier dans le contrôle de code source ou la possibilité d’exécuter un pipeline de configuration de niveau web Cloud Manager.
* Le nombre de redirections va de quelques dizaines de milliers à quelques dizaines de milliers.
* Vous souhaitez avoir la possibilité d’utiliser une interface utilisateur, soit créée en tant que projet personnalisé, soit à l’aide du [ACS Commons Redirect Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html) ou [ACS Commons Redirect Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-manager/subpages/rewritemap.html).

Le cœur de cette fonctionnalité est la possibilité pour AEM Apache/Dispatcher de charger (ou recharger) un ou plusieurs fichiers de mappage de réécriture qui ont été placés à un emplacement spécifié dans le référentiel de publication. Il est important de mentionner que la façon dont les fichiers y sont envoyés dépasse le cadre de cette fonctionnalité, mais vous pouvez envisager l’une des méthodes suivantes :

* Ingestion du mappage de réécriture en tant que ressource dans l’interface utilisateur de création et publication de celui-ci.
* Installation du [Gestionnaire de mappages de redirection ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html) ([version 6.7.0 ou ultérieure](https://github.com/Adobe-Consulting-Services/acs-aem-commons/releases)), qui comprend une interface utilisateur pour gérer les mappages d’URL et peut également publier le fichier de mappage de réécriture.
* Installation du [Gestionnaire de redirection ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-manager/subpages/rewritemap.html) ([au moins version 6.10.0 ou ultérieure](https://github.com/Adobe-Consulting-Services/acs-aem-commons/releases)), qui comprend également une interface utilisateur pour gérer les mappages d’URL et peut également publier le fichier de mappage de réécriture.
* Flexibilité totale grâce à l’écriture d’une application personnalisée. Par exemple, une interface utilisateur ou une interface de ligne de commande pour gérer les mappages d’URL ou encore un formulaire pour charger un mappage de réécriture, qui utilise ensuite les API AEM pour publier le fichier de mappage de réécriture.

>[!NOTE]
> Cette fonctionnalité nécessite la version AEM **18311 ou ultérieure**.

>[!NOTE]
> L’utilisation de cette fonctionnalité de Redirect Map Manager nécessite ACS Commons version **6.7.0 ou ultérieure** tandis que l’utilisation de Redirect Manager nécessite version **6.10.0 ou ultérieure**.

## La carte de réécriture {#rewrite-map}

Par défaut, la carte de réécriture est rechargée (si elle est modifiée) par le serveur HTTP Apache toutes les 300 secondes (la valeur est configurable). Le format du fichier doit suivre le format de fichier de mappage clé-valeur en texte brut RewriteMap décrit dans la [documentation Apache](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html#txt).

Un fichier nommé `managed-rewrite-maps.yaml` doit être créé pour spécifier l’emplacement du fichier de mappage de réécriture et il doit être déployé une seule fois, à l’aide du pipeline de pile pleine Cloud Manager ou du pipeline de niveau web. Le fichier doit être créé dans le dossier [src/opt-in](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/dispatcher.cloud/src/opt-in) de votre configuration Dispatcher. Veillez à utiliser la [structure de fichiers en mode flexible](/help/implementing/dispatcher/validation-debug.md#flexible-mode-file-structure).

Vous pouvez le configurer selon le modèle suivant :

```
maps:
- name: my.map
  path: <path-in-publish-repository>/redirectmap.txt
```

Si, par exemple, la méthode choisie pour placer le fichier de mappage de réécriture consiste à l’ingérer dans AEM sous la forme d’une ressource nommée `mysite-redirectmap.txt`, puis à le publier, vous pouvez spécifier un dossier sous `/content/dam` :

```
maps:
- name: my.map
  path: /content/dam/redirectmaps/mysite-redirectmap.txt
```

Ensuite, dans un fichier de configuration Apache tel que `rewrites/rewrite.rules` ou `<yourfile>.vhost`, vous devez configurer le fichier map référencé par la propriété name (`my.map` dans l’exemple ci-dessus). Une fois chargé, ce fichier de mappage est enregistré dans le stockage local du Dispatcher sous le `/tmp/rewrites/` d’emplacement **fixe**.

La directive `RewriteMap` doit indiquer que les données sont stockées dans un format de fichier de gestionnaire de base de données (DBM) au format `sdbm` (DBM simple) et que le chemin d&#39;accès complet au fichier est dérivé du préfixe d&#39;emplacement de stockage et de la propriété name.

Le reste de la configuration dépend du format du `redirectmap.txt`. Le format le plus simple, illustré dans l’exemple ci-dessous, est un mappage un-à-un entre l’URL d’origine et l’URL mappée :

```
# RewriteMap from managed rewrite maps
RewriteMap map.foo dbm=sdbm:/tmp/rewrites/my.map
RewriteCond ${map.foo:$1} !=""
RewriteRule ^(.*)$ ${map.foo:$1|/} [L,R=301]
```


## Considérations {#considerations}

Gardez à l’esprit les points suivants :

* Par défaut, lors du chargement d’un mappage de réécriture, Apache démarre sans attendre le chargement du ou des fichiers de mappage complets. Il peut donc y avoir des incohérences temporaires jusqu’au chargement du ou des mappages complets. Ce paramètre peut être modifié de sorte qu’Apache attende le chargement du contenu de mappage complet, mais il faut plus de temps pour qu’Apache démarre. Pour modifier ce comportement afin qu’Apache attende, ajoutez `wait:true` au fichier `managed-rewrite-maps.yaml`.
* Pour modifier la fréquence entre les chargements, ajoutez `ttl: <integer>` au fichier `managed-rewrite-maps.yaml`. Par exemple : `ttl: 120`.
* Apache a une limite de longueur de 1 024 pour les entrées uniques RewriteMap.

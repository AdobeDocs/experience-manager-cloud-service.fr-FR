---
title: Redirections d’URL sans pipeline
description: Découvrez comment déclarer des redirections 301 ou 302 sans accès aux pipelines Git ou Cloud Manager.
feature: Dispatcher
role: Admin
source-git-commit: 567c75f456f609dbc254753b439151d0f4100bc0
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# Redirections d’URL sans pipeline {#pipeline-free-redirects}

>[!NOTE]
>Cette fonctionnalité n’est pas encore disponible.

Pour diverses raisons, les entreprises réécrivent les URL d’une manière qui entraîne une redirection 301 (ou 302), ce qui signifie que le navigateur est redirigé vers une autre page.

Voici les scénarios :

* Une page d’HTML supprimée, de sorte que l’utilisateur est amené à une page de remplacement (parfois la page d’accueil) plutôt que de voir une erreur `404 Page Not Found`.
* Une page HTML renommée.
* Optimisation de l’optimisation pour les moteurs de recherche.

AEM as a Cloud Service propose [plusieurs approches](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/administration/url-redirection) pour implémenter les redirections côté client, mais la stratégie décrite dans cet article, redirections sans pipeline, est un bon choix lorsque :

* Les personnes qui assurent les redirections sont des utilisateurs professionnels, qui n’ont pas l’accès nécessaire pour valider les modifications de fichier dans le contrôle de code source ou la possibilité d’exécuter un pipeline de configuration de niveau web Cloud Manager.
* Le nombre de redirections est compris entre quelques et des dizaines de milliers.
* Vous souhaitez pouvoir utiliser une interface utilisateur, créée en tant que projet personnalisé ou à l’aide du [gestionnaire de cartes de réécriture ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html).

Le coeur de cette fonctionnalité est la possibilité pour AEM Apache/Dispatcher de charger (ou recharger) un ou plusieurs fichiers de mappage de réécriture qui ont été placés à un emplacement spécifié dans le référentiel de publication. Il est important de mentionner que la manière dont les fichiers y parviennent ne fait pas partie de cette fonctionnalité, mais vous pouvez envisager l’une des méthodes suivantes :

* Ingestion du mappage de réécriture en tant que ressource dans l’interface utilisateur de création et publication.
* L’installation du [gestionnaire de carte de réécriture ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html), qui comprend une interface utilisateur pour gérer les mappages d’URL et peut également publier le fichier de carte de réécriture.
* Flexibilité totale en écrivant une application personnalisée. Par exemple, une interface utilisateur ou une interface de ligne de commande pour gérer les mappages d’URL ou un formulaire pour charger une carte de réécriture, qui utilise ensuite AEM API pour publier le fichier de mappage de réécriture.

>[!NOTE]
> Cette fonctionnalité nécessite AEM version **18311 ou supérieure**.

## La carte de réécriture {#rewrite-map}

La carte de réécriture est rechargée (si elle est modifiée) par le serveur Apache HTTP toutes les 300 secondes par défaut (la valeur est configurable). Le format de fichier doit suivre le format de fichier clé-valeur map RewriteMap en texte brut décrit dans la [documentation Apache](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html#txt).

Un fichier nommé `managed-rewrite-maps.yaml` doit être créé pour spécifier l’emplacement du fichier de mappage de réécriture et il doit être déployé une seule fois, à l’aide du pipeline de pile complète Cloud Manager ou du pipeline de niveau web. Le fichier doit être créé dans le dossier [src/opt-in](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/dispatcher.cloud/src/opt-in) de votre configuration Dispatcher. Assurez-vous d’utiliser la [structure de fichier en mode souple](/help/implementing/dispatcher/validation-debug.md#flexible-mode-file-structure).

Vous pouvez le configurer avec le modèle suivant :

```
maps:
- name: my.map
  path: <path-in-publish-repository>/redirectmap.txt
```

Si, par exemple, la méthode choisie pour placer le fichier de mappage de réécriture consiste à l’ingérer dans AEM en tant que ressource nommée `mysite-redirectmap.txt`, puis à la publier, vous pouvez spécifier un dossier sous `/content/dam` :

```
maps:
- name: my.map
  path: /content/dam/redirectmaps/mysite-redirectmap.txt
```

Ensuite, dans un fichier de configuration Apache tel que `rewrites/rewrite.rules` ou `<yourfile>.vhost`, vous devez configurer le fichier map référencé par la propriété name ( `my.map` dans l’exemple ci-dessus).

La directive `RewriteMap` doit indiquer que les données sont stockées dans un format de fichier de gestionnaire de base de données (DBM) à l’aide du format `sdbm` (DBM simple).

Le reste de la configuration dépendra du format de `redirectmap.txt`. Le format le plus simple, illustré dans l’exemple ci-dessous, est un mappage un-à-un entre l’URL d’origine et l’URL mappée :

```
# RewriteMap from managed rewrite maps
RewriteMap map.foo dbm=sdbm:/tmp/rewrites/my.map
RewriteCond ${map.foo:$1} !=""
RewriteRule ^(.*)$ ${map.foo:$1|/} [L,R=301]
```


## Considérations {#considerations}

Gardez à l’esprit les points suivants :

* Par défaut, lors du chargement d’une carte de réécriture, Apache démarre sans attendre le chargement du ou des fichiers de mappage complets. Il peut donc y avoir des incohérences temporaires jusqu’au chargement de la ou des cartes complètes. Ce paramètre peut être modifié de sorte qu’Apache attende le chargement du contenu complet de la carte, mais cela prendra plus de temps pour qu’Apache démarre. Pour modifier ce comportement afin qu’Apache attende, ajoutez `wait:true` au fichier `managed-rewrite-maps.yaml`.
* Pour modifier la fréquence entre les chargements, ajoutez `ttl: <integer>` au fichier `managed-rewrite-maps.yaml`. Par exemple, `ttl: 120`.
* Apache a une longueur maximale de 1 024 pour les entrées uniques RewriteMap .

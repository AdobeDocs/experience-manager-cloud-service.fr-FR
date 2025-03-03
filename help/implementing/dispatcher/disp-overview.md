---
title: Dispatcher en mode cloud
description: Découvrez les outils Dispatcher, les modules Apache pris en charge et les modes hérités et flexibles.
feature: Dispatcher
exl-id: 6d78026b-687e-434e-b59d-9d101349a707
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 98%

---

# Dispatcher en mode cloud {#Dispatcher-in-the-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispoverview"
>title="Dispatcher en mode cloud"
>abstract="Cette page explique comment télécharger et extraire les outils Dispatcher. Elle décrit aussi les modules Apache pris en charge et donne un aperçu général des modes hérités et flexibles."

## Présentation {#apache-and-dispatcher-configuration-and-testing}

Cette page décrit les outils Dispatcher, ainsi que la manière de les télécharger et de les extraire. Elle décrit en outre les modules Apache pris en charge et fournit un aperçu général des modes hérités et flexibles. Elle contient également d’autres références sur la validation, le débogage et la migration de la configuration de Dispatcher d’AMS vers AEM as a Cloud Service. <!-- ERROR: NOT FOUND (HTTP ERROR 404) Also, see [this video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-dispatcher-cloud.html) for additional details about deploying dispatcher files in a cloud service environment. -->

## Outils Dispatcher {#dispatcher-sdk}

Les outils Dispatcher font partie du SDK global d’AEM as a Cloud Service et fournissent les éléments suivants :

* Une structure de fichiers classique contenant les fichiers de configuration à inclure dans un projet maven pour Dispatcher.
* Un outil permettant aux clients et clientes de confirmer que la configuration de Dispatcher inclut uniquement des directives prises en charge par AEM as a Cloud Service. En outre, l’outil confirme également que la syntaxe est correcte, afin qu’Apache puisse démarrer correctement.
* Une image du Docker qui rend Dispatcher accessible localement

## Téléchargement et extraction des outils {#extracting-the-sdk}

Les outils Dispatcher, qui font partie du [SDK AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md), peuvent être téléchargés sous la forme d’un fichier zip sur le portail de [distribution de logiciels](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html). Toute nouvelle configuration disponible dans cette nouvelle version des outils Dispatcher peut être utilisée pour le déploiement dans les environnements cloud exécutant cette version d’AEM en mode cloud ou une version ultérieure.

Décompressez le SDK, qui regroupe les outils Dispatcher pour macOS, Linux® et Windows.

**Pour macOS/Linux**, rendez l’artefact de l’outil Dispatcher exécutable et exécutez-le. Il extrait automatiquement les fichiers des outils Dispatcher au sein du répertoire dans lequel vous l’avez stocké (où `version` est la version des outils Dispatcher).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Pour Windows**, extrayez le fichier d’archive compressé Dispatcher Tooling.

## Validation et débogage à l’aide des outils Dispatcher {#validation-debug}

Les outils Dispatcher sont utilisés pour valider et déboguer la configuration Dispatcher de votre projet. Découvrez comment utiliser ces outils dans les pages référencées ci-dessous, en fonction de la configuration du Dispatcher de votre projet, structurée en mode flexible ou en mode hérité :

* **Mode flexible** : le mode recommandé et la valeur par défaut de [l’archétype 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) d’AEM et versions ultérieures, également utilisés par Cloud Manager pour les nouveaux environnements créés après la version 2021.7.0 de Cloud Manager. Les clients peuvent activer ce mode en ajoutant le dossier et le fichier `opt-in/USE_SOURCES_DIRECTLY`. En utilisant ce mode plus flexible, il n’existe aucune limite dans la structure de fichiers sous le dossier de réécritures qui, en mode hérité, nécessitait un seul fichier `rewrite.rules`. En outre, il n’y a aucune limitation sur le nombre de règles que vous pouvez ajouter. Pour plus d’informations sur la structure de dossiers et la validation locale, voir [Validation et débogage à l’aide des outils Dispatcher](/help/implementing/dispatcher/validation-debug.md).

* **Mode hérité** : pour plus d’informations sur la structure de dossiers et la validation locale pour le mode hérité de la configuration de Dispatcher, voir [Validation et débogage à l’aide des outils Dispatcher (hérités).](/help/implementing/dispatcher/validation-debug-legacy.md)

Pour plus d’informations sur la migration du modèle de configuration hérité vers le modèle plus flexible, fourni avec l’archétype 28 d’AEM et versions ultérieures, voir [cette documentation](/help/implementing/dispatcher/validation-debug.md#migrating).

## Disposition du contenu {#content-disposition}

Pour le niveau de publication, les objets Blob sont diffusés par défaut en tant que pièce jointe. Vous pouvez modifier ce paramètre en utilisant l’[en-tête standard de disposition du contenu](https://developer.mozilla.org/fr-FR/docs/Web/HTTP/Headers/Content-Disposition) dans le Dispatcher.

La configuration doit se présenter ainsi :

```
<LocationMatch "^\/content\/dam.*\.(pdf).*">
 Header unset Content-Disposition
 Header set Content-Disposition inline
</LocationMatch>
```

## Modules Apache pris en charge {#supported-directives}

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
| `mod_proxy` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html) |
| `mod_proxy_http` | [https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html](https://httpd.apache.org/docs/2.4/mod/mod_proxy_http.html) |
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_ssl (only the SSLProxyEngine directive)` | [https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html#sslproxyengine) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |
| `mod_macro` | [https://httpd.apache.org/docs/2.4/mod/mod_macro.html](https://httpd.apache.org/docs/2.4/mod/mod_macro.html) |
| `mod_include (no directives supported)` | [https://httpd.apache.org/docs/2.4/mod/mod_include.html](https://httpd.apache.org/docs/2.4/mod/mod_include.html) |


Les clients ne peuvent pas ajouter de modules arbitraires, mais des modules supplémentaires peuvent être envisagés pour inclusion à l’avenir. Pour obtenir la liste des directives disponibles pour une version de Dispatcher donnée, les client(e)s peuvent exécuter la commande de liste autorisée du programme de validation dans le SDK.

Les directives autorisées dans les fichiers de configuration Apache peuvent être répertoriées en exécutant la commande de liste autorisée du programme de validation :

```
$ validator allowlist
Cloud manager validator 2.0.4
 
Allowlisted directives:
  <Directory>
  ...
  
```

## Structure de dossiers {#folder-structure}

La structure de dossiers Apache et Dispatcher du projet diffère légèrement selon le mode utilisé par le projet, comme décrit dans la section [Validation et débogage à l’aide des outils Dispatcher](#validation-debug) ci-dessus.

## Migration de la configuration de Dispatcher à partir d’AMS {#ams-aem}

Pour plus d’informations sur la migration de la configuration de Dispatcher d’AMS vers AEM en as a Cloud Service, voir la page [Migration de la configuration de Dispatcher d’AMS vers AEM](/help/implementing/dispatcher/ams-aem.md) as a Cloud Service.

---
title: Index Converter
description: Convertisseur d’index
exl-id: e6a3ec6d-cc02-4f5b-8b1d-ea481d6884ca
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 100%

---

# Index Converter {#index-converter}

Index Converter est un utilitaire développé pour migrer les définitions d’index d’un client en vue du déplacement vers AEM as a Cloud Service.

## Présentation {#introduction}

Index Converter permet aux développeurs AEM de migrer les définitions d’index Custom Oak existantes vers des définitions d’index Custom Oak compatibles avec AEM as a Cloud Service.

>[!NOTE]
>Index Converter transforme uniquement les définitions d’index Custom Oak de type *lucene* qui se trouvent sous `/apps` ou `/oak:index`. Il ne transforme pas les index de type *lucene* créés pour `nt:base`.

Il existe deux façons de créer des définitions d’index Custom Oak :

* `under /apps` (par le biais de tout package de contenu personnalisé)
* Directement sous le chemin `/oak:index`

Si l’[index Ensure Oak](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) a été utilisé, les définitions Ensure ne sont pas prises en charge par AEM as a Cloud Service. Elles doivent d’abord être converties en définitions d’index Oak puis migrées vers des définitions d’index Custom Oak compatibles avec AEM as a Cloud Service, conformément aux instructions suivantes :

* Si la propriété ignore est définie sur `true`, ignorez ou passez la définition Ensure.
* Mettez à jour `jcr:primaryType` sur `oak:QueryIndexDefinition`.
* Supprimez toutes les propriétés à ignorer, comme indiqué dans les configurations OSGi.
* Supprimez la sous-arborescence `/facets/jcr:content` de la définition Ensure.

## Utilisation d’Index Converter {#using-index-converter}

* Via l’interface de ligne de commande d’Adobe I/O : il est recommandé d’utiliser Index Converter via `aio-cli-plugin-aem-cloud-service-migration` (plug-in de refactorisation de code AEM as a Cloud Service pour l’interface de ligne de commande d’Adobe I/O).

   Voir **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser ce module.

* En tant qu’utilitaire autonome : Index Converter peut également être exécuté en tant qu’utilitaire autonome.

   Voir **[Ressource Git : aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** pour découvrir comment utiliser cet outil.

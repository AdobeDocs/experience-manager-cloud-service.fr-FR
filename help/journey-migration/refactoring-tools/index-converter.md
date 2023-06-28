---
title: Index Converter
description: Index Converter
exl-id: ac02ca41-eb35-4f24-bf17-d00ce318423d
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 70%

---

# Index Converter {#index-converter}

Index Converter est un utilitaire développé pour migrer les définitions d’index d’un client en vue du passage à AEM as a Cloud Service.

## Présentation {#introduction}

Index Converter permet aux développeurs AEM de migrer les définitions d’index Custom Oak existantes vers des définitions d’index Custom Oak compatibles avec AEM as a Cloud Service.

>[!NOTE]
>Index Converter transforme uniquement les définitions d’index Custom Oak de type *lucene* qui se trouvent sous `/apps` ou `/oak:index`. Il ne transforme pas les index de type *lucene* créés pour `nt:base`.

Il existe deux façons de créer des définitions d’index Custom Oak :

* `under /apps` (par le biais de tout package de contenu personnalisé)
* Directement sous le chemin `/oak:index`

If [Vérification de l’index Oak](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) était utilisé. Assurez-vous que les définitions ne sont pas prises en charge sur AEM as a Cloud Service. En tant que tels, ils doivent d’abord être convertis en définitions d’index Oak, puis migrés vers des définitions d’index Oak personnalisées compatibles avec AEM as a Cloud Service, conformément aux instructions ci-dessous :

* Si la propriété ignore est définie sur `true`, ignorez ou passez la définition Ensure.
* Mettez à jour `jcr:primaryType` sur `oak:QueryIndexDefinition`.
* Supprimez toutes les propriétés à ignorer, comme indiqué dans les configurations OSGi.
* Supprimez la sous-arborescence `/facets/jcr:content` de la définition Ensure.

## Utilisation d’Index Converter {#using-index-converter}

* Par Adobe I/O, l’interface de ligne de commande : Il est recommandé d’utiliser le convertisseur d’index au moyen de `aio-cli-plugin-aem-cloud-service-migration` (AEM module externe de refactorisation du code as a Cloud Service pour l’interface de ligne de commande d’Adobe I/O).

  Voir **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser ce module.

* En tant qu’utilitaire autonome : Index Converter peut également être exécuté en tant qu’utilitaire autonome.

  Voir **[Ressource Git : aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** pour découvrir comment utiliser cet outil.

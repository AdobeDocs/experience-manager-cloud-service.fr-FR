---
title: Convertisseur d’index
description: Convertisseur d’index
translation-type: tm+mt
source-git-commit: 3fe19282f9e96d503f4e8be05553c6f48a6f19b6
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 9%

---


# Convertisseur d&#39;index {#index-converter}

Index Converter est un utilitaire développé pour migrer les définitions d&#39;index d&#39;un client en vue du déplacement vers l&#39;AEM en tant que Cloud Service.

## Présentation {#introduction}

Le convertisseur d’index permet aux développeurs AEM de migrer les définitions d’index de chêne personnalisé existantes vers AEM en tant que définitions d’index de chêne personnalisé compatibles avec les Cloud Service.

>[!NOTE]
>Le convertisseur d&#39;index transforme uniquement *lucene* le type Custom Oak Index Definitions qui se trouvent sous `/apps` ou `/oak:index`. Il ne transforme pas les index de type *lucene* créés pour `nt:base`.

Il existe deux façons de créer des définitions d’index de chêne personnalisées :

* `under /apps` (par le biais de tout package de contenu personnalisé)
* directement sous `/oak:index` chemin

Si [Vérifier que l&#39;index de chêne](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) a été utilisé, veuillez noter que les définitions de chêne ne sont pas prises en charge sur AEM en tant que Cloud Service. Par conséquent, elles doivent d&#39;abord être converties en définitions d&#39;index de chêne et doivent ensuite être migrées vers des définitions d&#39;index de chêne personnalisées compatibles avec les AEM en tant que Cloud Service, conformément aux instructions suivantes :

* Si la propriété ignore est définie sur `true`, ignorez ou ignorez la définition de l’élément Vérifier
* Mettre à jour `jcr:primaryType` en `oak:QueryIndexDefinition`
* Supprimez toutes les propriétés à ignorer, comme indiqué dans les configurations OSGi.
* Supprimer la sous-arborescence `/facets/jcr:content` de la définition d&#39;assurance

## Utilisation du convertisseur d’index {#using-index-converter}

* Via Adobe I/O CLI : Il est recommandé d’utiliser le convertisseur d’index via `aio-cli-plugin-aem-cloud-service-migration` (AEM comme module externe de refactorisation du code Cloud Service pour l’interface de ligne de commande Adobe I/O).

   Voir la **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser ce module.

* En tant qu&#39;utilitaire autonome : Le convertisseur d’index peut également être exécuté en tant qu’utilitaire autonome.

   Reportez-vous à **[Ressource Git : aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** pour savoir comment utiliser cet outil.




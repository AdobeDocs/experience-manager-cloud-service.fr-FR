---
title: Convertisseur d’index
description: Convertisseur d’index
translation-type: tm+mt
source-git-commit: fecbd0b4d5cfd8aa970c235c79158bea44403c09
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 6%

---


# Convertisseur d&#39;index {#index-converter}

Index Converter est un utilitaire développé pour migrer la définition d&#39;index d&#39;un client en vue de son déplacement en Cloud Service vers l&#39;AEM.

## Présentation {#introduction}

Le convertisseur d’index permet aux développeurs AEM de migrer les définitions d’index de chêne personnalisé existantes vers AEM en tant que définitions d’index de chêne personnalisé compatibles avec les Cloud Service.

>[!NOTE]
>Le convertisseur d&#39;index transforme uniquement *lucene* le type Custom Oak Index Definitions qui se trouvent sous `/apps` ou `/oak:index`. Il ne transforme pas les index de type *lucene* créés pour `nt:base`.

Il existe deux façons de créer des définitions d’index de chêne personnalisées :

* `under /apps` (par le biais de tout package de contenu personnalisé)
* directement sous `/oak:index` chemin

>[!NOTE]
>Voir [Vérifier l&#39;index des chênes](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) pour savoir comment définir et créer des définitions des chênes.

## Utilisation du convertisseur d’index {#using-index-converter}

>[!NOTE]
>Bien qu’il soit recommandé d’utiliser l’outil Index Converter via [le module externe d’interface de ligne de commande AIO pour la migration de la source](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration), il peut également être exécuté de manière autonome.

Reportez-vous à **[Ressource Git : aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** pour savoir comment installer et utiliser le module externe.


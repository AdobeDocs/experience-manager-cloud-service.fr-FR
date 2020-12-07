---
title: Convertisseur d’index
description: Convertisseur d’index
translation-type: tm+mt
source-git-commit: 21bd9392d913369a5e8e0ebd9badbbe30fd4bba3
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 5%

---


# Convertisseur d&#39;index {#index-converter}

Index Converter est un utilitaire développé pour migrer la définition d&#39;index d&#39;un client en vue de son déplacement en Cloud Service vers l&#39;AEM.

## Présentation {#introduction}

Le convertisseur d’index permet aux développeurs AEM de migrer les définitions d’index de chêne personnalisé existantes vers AEM en tant que définitions d’index de chêne personnalisé compatibles avec les Cloud Service.

>[!NOTE]
>Le convertisseur d&#39;index transforme uniquement *lucene* le type Custom Oak Index Definitions qui sont présentes sous `/apps` ou `/oak:index`. Il ne transforme pas les index de type *lucene* créés pour `nt:base`.

## Utilisation du convertisseur d’index {#using-index-converter}

Reportez-vous à **[Ressource Git : aem-cs-source-migration-index-converter](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser le module externe.


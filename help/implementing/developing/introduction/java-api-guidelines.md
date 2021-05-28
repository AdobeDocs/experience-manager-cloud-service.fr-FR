---
title: Instructions relatives aux API Java
description: AEM repose sur une riche pile de logiciels open source qui expose de nombreuses API Java à utiliser.
exl-id: 0be33ec9-a4c3-4400-99d3-ed8366c5b5f9
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 97%

---

# Instructions relatives aux API Java {#java-api-guidelines}

Adobe Experience Manager (AEM) repose sur une riche pile de logiciels open source qui expose de nombreuses API Java à utiliser pendant le développement.

AEM repose sur les quatre principaux ensembles d’API Java suivants, dans l’ordre décroissant de préférence.

1. **[Adobe Experience Manager (AEM)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service-javadoc/index.html)** : abstractions de produits telles que pages, ressources, workflows, etc.
1. **[Apache Sling Web Framework](https://sling.apache.org/apidocs/sling11/)** : REST et abstractions basées sur des ressources telles que les ressources, les cartes de valeurs et les requêtes HTTP.
1. **[JCR (Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)** : abstractions de données et de contenu telles que nœud, propriétés et sessions.
1. **[OSGi (Apache Felix)](https://felix.apache.org)** : abstractions du conteneur d’application OSGi telles que les services et les composants (OSGi).

Si une API est fournie par AEM, préférez-la à Sling, JCR et OSGi. Si AEM ne fournit pas d’API, préférez Sling à JCR et OSGi.

Pour plus d’informations sur ces directives, consultez le document [Présentation des bonnes pratiques de l’API Java.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=fr)

---
title: Instructions relatives aux API Java
description: aem est construit sur une riche pile de logiciels open source qui expose de nombreuses API Java à utiliser.
translation-type: tm+mt
source-git-commit: b927992107d7e7e4df5511a366c71449ff73ec93
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 6%

---


# Directives d&#39;API Java {#java-api-guidelines}

Adobe Experience Manager (AEM) est construit sur une riche pile de logiciels open source qui expose de nombreuses API Java à des fins de développement.

aem est basé sur les quatre ensembles d&#39;API Java Principaux suivants dans l&#39;ordre décroissant de préférence.

1. **Adobe Experience Manager (AEM)**  : abstractions de produits telles que pages, ressources, workflows, etc.
1. **[Apache Sling Web Framework](https://sling.apache.org/apidocs/sling11/)**  - REST et abstractions basées sur des ressources telles que les ressources, les cartes de valeurs et les requêtes HTTP.
1. **[JCR (Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)**  : abstractions de données et de contenu telles que noeud, propriétés et sessions.
1. **[OSGi (Apache Felix)](https://felix.apache.org)**  : abstractions du conteneur d&#39;application OSGi telles que les services et les composants (OSGi).

Si une API est fournie par AEM, préférez-la à Sling, JCR et OSGi. Si AEM ne fournit pas d’API, préférez Sling à JCR et OSGi.

Pour plus d&#39;informations sur ces directives, consultez le document [Comprendre les meilleures pratiques de l&#39;API Java.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

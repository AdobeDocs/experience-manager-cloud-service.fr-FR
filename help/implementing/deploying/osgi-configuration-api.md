---
title: API de configuration OSGi
description: Description de la surface de configuration OSGi d‘AEM as a Cloud Service
feature: Deploying
exl-id: 94d3df65-71d7-4442-8412-fe2cca7e79ff
source-git-commit: cba6648d7ef18f3cccbd9562f3a66d9c683ae852
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 100%

---

# API de configuration OSGi

Les deux listes ci-dessous représentent la surface de configuration OSGi d’AEM as a Cloud Service, décrivant ce que les clients peuvent configurer.

1. Liste des configurations OSGi qui ne doivent pas être configurées par le code client
1. Liste des configurations OSGi dont les propriétés peuvent être configurées, mais doivent respecter les règles de validation indiquées. Ces règles indiquent si la déclaration de la propriété est requise, son type et, dans certains cas, sa plage de valeurs autorisée.

Si une configuration OSGI n’est pas répertoriée, elle peut être configurée par code client.

Ces règles sont validées pendant le processus de création de Cloud Manager. D’autres règles peuvent être ajoutées au fil du temps et la date prévue d’application est indiquée dans le tableau. Les clients doivent respecter ces règles avant la date d’application de la cible. Le fait de ne pas respecter les règles après la date de suppression génère des erreurs dans le processus de création de Cloud Manager. Les projets Maven doivent inclure le [module externe Maven Analyseur de build de SDK d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr) pour signaler les erreurs de configuration OSGI lors du développement du SDK local.

Vous trouverez des informations supplémentaires sur la configuration OSGI à [cet emplacement](/help/implementing/deploying/configuring-osgi.md).

## Configurations OSGi qui ne peuvent pas être modifiées {#osgi-configurations-that-cannot-be-modified}

* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`org.apache.felix.http (Factory)`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** (Date d’annonce : 25/08/2021, Date d’application : 26/11/2021)

## Configuration OSGi soumises aux règles de validation de création {#osgi-configurations-subject-to-build-validation-rules}

* **`org.apache.felix.eventadmin.impl.EventAdmin`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
   * `org.apache.felix.eventadmin.ThreadPoolSize`
      * Type : entier
      * Plage requise : 2 à 100
   * `org.apache.felix.eventadmin.AsyncToSyncThreadRatio`
      * Type : double
   * `org.apache.felix.eventadmin.Timeout`
      * Type : entier
   * `org.apache.felix.eventadmin.RequireTopic`
      * Type : booléen
   * `org.apache.felix.eventadmin.IgnoreTimeout`
      * Requis
      * Type : tableau de chaînes
      * Plage requise : doit inclure au moins tous les éléments `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*`
   * `org.apache.felix.eventadmin.IgnoreTopic`
      * Type : tableau de chaînes
* **`org.apache.felix.http`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
   * `org.apache.felix.http.timeout`
      * Type : entier
   * `org.apache.felix.http.session.timeout`
      * Type : entier
   * `org.apache.felix.http.jetty.threadpool.max`
      * Type : entier
   * `org.apache.felix.http.jetty.headerBufferSize`
      * Type : entier
   * `org.apache.felix.http.jetty.requestBufferSize`
      * Type : entier
   * `org.apache.felix.http.jetty.responseBufferSize`
      * Type : entier
   * `org.apache.felix.http.jetty.maxFormSize`
      * Type : entier
   * `org.apache.felix.https.jetty.session.cookie.httpOnly`
      * Type : booléen
   * `org.apache.felix.https.jetty.session.cookie.secure`
      * Type : booléen
   * `org.eclipse.jetty.servlet.SessionIdPathParameterName`
      * Type : chaîne
   * `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding`
      * Type : booléen
   * `org.eclipse.jetty.servlet.SessionCookie`
      * Type : chaîne
   * `org.eclipse.jetty.servlet.SessionDomain`
      * Type : chaîne
   * `org.eclipse.jetty.servlet.SessionPath`
      * Type : chaîne
   * `org.eclipse.jetty.servlet.MaxAge`
      * Type : entier
   * `org.eclipse.jetty.servlet.SessionScavengingInterval`
      * Type : entier
   * `org.apache.felix.jetty.gziphandler.enable`
      * Type : booléen
   * `org.apache.felix.jetty.gzip.minGzipSize`
      * Type : entier
   * `org.apache.felix.jetty.gzip.compressionLevel`
      * Type : entier
   * `org.apache.felix.jetty.gzip.inflateBufferSize`
      * Type : entier
   * `org.apache.felix.jetty.gzip.syncFlush`
      * Type : booléen
   * `org.apache.felix.jetty.gzip.excludedUserAgents`
      * Type : chaîne
   * `org.apache.felix.jetty.gzip.includedMethods`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.excludedMethods`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.includedPaths`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.excludedPaths`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.includedMimeTypes`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.excludedMimeTypes`
      * Type : tableau de chaînes
   * `org.apache.felix.http.session.invalidate`
      * Type : booléen
   * `org.apache.felix.http.session.container.attribute`
      * Type : tableau de chaînes
   * `org.apache.felix.http.session.uniqueid`
      * Type : booléen
* **`org.apache.sling.scripting.cache`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
   * `org.apache.sling.scripting.cache.size`
      * Type : entier
      * Plage requise : >= 2048
   * `org.apache.sling.scripting.cache.additional_extensions`
      * Requis
      * Type : tableau de chaînes
      * Plage requise : doit inclure js
* **`com.day.cq.mailer.DefaultMailService`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
   * `smtp.host`
      * Type : chaîne
   * `smtp.port`
      * Type : entier
      * Plage requise : 465, 587 ou 25
   * `smtp.user`
      * Type : chaîne
   * `smtp.password`
      * Type : chaîne
   * `from.address`
      * Type : chaîne
   * `smtp.ssl`
      * Type : chaîne
   * `smtp.starttls`
      * Type : booléen
   * `smtp.requiretls`
      * Type : booléen
   * `debug.email`
      * Type : booléen
   * `oauth.flow`
      * Type : booléen
* **`org.apache.sling.commons.log.LogManager.factory.config`** (Date d’annonce: 16/11/21, Date d’application : 16/02/21)
   * `org.apache.sling.commons.log.level`
      * Type : énumération
      * Plage requise : INFO, DEBUG ou TRACE
   * `org.apache.sling.commons.log.names`
      * Type : chaîne
   * `org.apache.sling.commons.log.file`
      * Type : chaîne
   * `org.apache.sling.commons.log.additiv`
      * Type : booléen
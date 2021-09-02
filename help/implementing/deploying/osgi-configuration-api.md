---
title: API de configuration OSGi
description: Description de l’AEM en tant que surface de configuration OSGi Cloud Service
feature: Deploying
source-git-commit: 5223d57377f5c00b090aee1ddd4dbfe2d7113181
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 5%

---


# API de configuration OSGi

Les deux listes ci-dessous représentent la surface de configuration OSGi de l’AEM en tant que Cloud Service, décrivant ce que les clients peuvent configurer.

1. Liste des configurations OSGi qui ne doivent pas être configurées par le code client
1. Liste des configurations OSGi dont les propriétés peuvent être configurées, mais doivent respecter les règles de validation indiquées. Ces règles indiquent si la déclaration de la propriété est requise, son type et, dans certains cas, sa plage de valeurs autorisée.

Si une configuration OSGI n’est pas répertoriée, elle peut être configurée par code client.

Ces règles sont validées pendant le processus de création de Cloud Manager. D’autres règles peuvent être ajoutées au fil du temps et la date prévue d’application est indiquée dans le tableau. Les clients doivent respecter ces règles avant la date d’application de la cible. Le fait de ne pas respecter les règles après la date de suppression génère des erreurs dans le processus de création de Cloud Manager. Les projets Maven doivent inclure le [module externe Maven AEM as a Cloud Service SDK Build Analyzer](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html) pour signaler les erreurs de configuration OSGI lors du développement du SDK local.

Vous trouverez des informations supplémentaires sur la configuration OSGI à [cet emplacement](/help/implementing/deploying/configuring-osgi.md).

## Configurations OSGi qui ne peuvent pas être modifiées {#osgi-configurations-that-cannot-be-modified}

* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
* **`org.apache.felix.http (Factory)`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
* **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** (Date d’annonce : 8/25/2021, Date d’application : 11/26/2021)

## Configuration OSGi Objet pour créer des règles de validation {#osgi-configurations-subject-to-build-validation-rules}

* **`org.apache.felix.eventadmin.impl.EventAdmin`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
   * `org.apache.felix.eventadmin.ThreadPoolSize`
      * Type : entier
      * Période requise : 2 à 100
   * `org.apache.felix.eventadmin.AsyncToSyncThreadRatio`
      * Type : double
   * `org.apache.felix.eventadmin.Timeout`
      * Type : entier
   * `org.apache.felix.eventadmin.RequireTopic`
      * Type : boolean
   * `org.apache.felix.eventadmin.IgnoreTimeout`
      * Requis
      * Type : tableau de chaînes
      * Période requise : Doit inclure au moins tous les éléments `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*`
   * `org.apache.felix.eventadmin.IgnoreTopic`
      * Type : tableau de chaînes
* **`org.apache.felix.http`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
   * `org.apache.felix.http.timeout`
      * Type : entier
   * `org.apache.felix.http.session.timeout`
      * Type : entier
   * `org.apache.felix.http.jetty.threadpool.max`
      * Type : entier
   * `org.apache.felix.http.jetty.headerBufferSize`
      * Type : entier
   * `org.apache.felix.http.jetty.requestBufferSize`
      * Type : entier
   * `org.apache.felix.http.jetty.responseBufferSize`
      * Type : entier
   * `org.apache.felix.http.jetty.maxFormSize`
      * Type : entier
   * `org.apache.felix.https.jetty.session.cookie.httpOnly`
      * Type : boolean
   * `org.apache.felix.https.jetty.session.cookie.secure`
      * Type : boolean
   * `org.eclipse.jetty.servlet.SessionIdPathParameterName`
      * Type : string
   * `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding`
      * Type : boolean
   * `org.eclipse.jetty.servlet.SessionCookie`
      * Type : string
   * `org.eclipse.jetty.servlet.SessionDomain`
      * Type : string
   * `org.eclipse.jetty.servlet.SessionPath`
      * Type : string
   * `org.eclipse.jetty.servlet.MaxAge`
      * Type : entier
   * `org.eclipse.jetty.servlet.SessionScavengingInterval`
      * Type : entier
   * `org.apache.felix.jetty.gziphandler.enable`
      * Type : boolean
   * `org.apache.felix.jetty.gzip.minGzipSize`
      * Type : entier
   * `org.apache.felix.jetty.gzip.compressionLevel`
      * Type : entier
   * `org.apache.felix.jetty.gzip.inflateBufferSize`
      * Type : entier
   * `org.apache.felix.jetty.gzip.syncFlush`
      * Type : boolean
   * `org.apache.felix.jetty.gzip.excludedUserAgents`
      * Type : string
   * `org.apache.felix.jetty.gzip.includedMethods`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.excludedMethods`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.includedPaths`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.excludedPaths`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.includedMimeTypes`
      * Type : tableau de chaînes
   * `org.apache.felix.jetty.gzip.excludedMimeTypes`
      * Type : tableau de chaînes
   * `org.apache.felix.http.session.invalidate`
      * Type : boolean
   * `org.apache.felix.http.session.container.attribute`
      * Type : tableau de chaînes
   * `org.apache.felix.http.session.uniqueid`
      * Type : boolean
* **`org.apache.sling.scripting.cache`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
   * `org.apache.sling.scripting.cache.size`
      * Type : entier
      * Période requise : >= 2048
   * `org.apache.sling.scripting.cache.additional_extensions`
      * Requis
      * Type : tableau de chaînes
      * Période requise : doit inclure js
* **`com.day.cq.mailer.DefaultMailService`** (Date d’annonce : 4/30/2021, Date d’application : 7/31/2021)
   * `smtp.host`
      * Type : string
   * `smtp.port`
      * Type : entier
      * Période requise : 465, 587 ou 25
   * `smtp.user`
      * Type : string
   * `smtp.password`
      * Type : string
   * `from.address`
      * Type : string
   * `smtp.ssl`
      * Type : string
   * `smtp.starttls`
      * Type : boolean
   * `smtp.requiretls`
      * Type : boolean
   * `debug.email`
      * Type : boolean
   * `oauth.flow`
      * Type : boolean

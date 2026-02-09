---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
mini-toc-levels: 1
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
feature: Release Information
role: Admin
source-git-commit: 5b049c6502cddf7009cf5c81b033e290216eb847
workflow-type: tm+mt
source-wordcount: '3695'
ht-degree: 85%

---

# Fonctionnalités et API obsolètes et supprimées {#deprecated-and-removed-features-apis}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Fonctionnalités obsolètes et supprimées dans AEM as a Cloud Service"
>abstract="AEM as a Cloud Service dispose d’un modèle de déploiement natif dans le cloud. Cet onglet met en évidence les capacités et fonctionnalités remplacées par leurs homologues natifs cloud."

Adobe passe régulièrement en revue les fonctionnalités, y compris les API et les configurations, afin de s’assurer qu’elles répondent à des normes en constante évolution en termes de performances, de sécurité et de valeur globale pour AEM as a Cloud Service. En fonction de ces évaluations, certaines fonctionnalités risquent d’être marquées comme obsolètes. Dans la mesure du possible, Adobe proposera une fonctionnalité de remplacement appropriée.

Lorsqu’une obsolescence est annoncée, la fonctionnalité ne reste disponible que pendant une période limitée. Les clientes et les clients doivent alors cesser de l’utiliser avant la date de suppression spécifiée. Adobe annoncera la suppression avec un préavis raisonnable et apportera des conseils pour faciliter une transition en douceur.

Pendant la période d’obsolescence, Adobe rappelle à ses clientes et clients les actions qu’ils doivent entreprendre pour cesser d’utiliser une fonctionnalité au moyen d’e-mails, d’alertes du Centre d’actions ou de rappels dans Cloud Manager.

>[!WARNING]
>
>Dans certains cas, il peut être nécessaire de supprimer une fonctionnalité avant de déployer une nouvelle version de Cloud Manager ou d’effectuer une mise à niveau vers la dernière version d’AEM as a Cloud Service.

>[!IMPORTANT]
>  Plusieurs [API obsolètes](#aem-apis) ciblent la suppression le **26 février 2026**. Veuillez consulter ces dates et impacts clés :
>
> * **À compter du 26 janvier 2026** : les e-mails de notification du Centre d’actions sont envoyés **chaque semaine par environnement** comme rappel pour supprimer l’utilisation de ces API.
> * **26 février 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API seront **mis en pause** pendant l’étape **Qualité du code**. Un responsable de déploiement, un chef de projet ou un propriétaire d’entreprise peut contourner le problème pour autoriser le pipeline à continuer.
> * **26 mars 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API échoueront **&#x200B;**&#x200B;pendant l’étape **Qualité du code**, **blocage des déploiements** du nouveau code jusqu’à ce que l’utilisation soit supprimée.
> * **30 avril 2026** : les environnements qui utilisent toujours ces API peuvent **ne plus recevoir de mises à jour critiques de versions d’Adobe**.
>
> Pour empêcher les blocs de déploiement, supprimez l’utilisation de l’API avant le 26 mars 2026.

## Fonctionnalité obsolète {#deprecated-features}

La fonctionnalité du tableau ci-dessous a été annoncée comme obsolète, mais n’a pas encore été supprimée.  Vous devez cesser d’utiliser la fonctionnalité avant la date de suppression cible, faute de quoi des problèmes liés aux performances, à la disponibilité et à la sécurité sont susceptibles de se produire.

| Fonctionnalités | Fonctionnalité obsolète | Remplacement |
| ------------ | ------------------ | ----------- |
| Sites | [Prise en charge des fragments de contenu dans l’API Assets HTTP](/help/assets/content-fragments/assets-api-content-fragments.md) | [Diffusion de fragments de contenu avec OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)<br> avec <br> [API OpenAPI de fragments de contenu et de gestion de modèles de fragment de contenu](/help/headless/content-fragment-openapis.md) |
| Sites | [Fonctionnalités PWA](/help/sites-cloud/authoring/sites-console/enable-pwa.md) | Aucune |
| Sites | [Éditeur SPA](/help/implementing/developing/hybrid/introduction.md) | Les éditeurs recommandés pour la gestion du contenu découplé dans AEM sont les suivants : <br>- [Éditeur universel](https://www.aem.live/docs/aem-authoring) pour la modification visuelle.<br>- [Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur les formulaires. |
| [!DNL Sites] | [API JavaScript Use](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) | [API JavaScript Use](https://experienceleague.adobe.com/fr/docs/experience-manager-htl/content/java-use-api) |
| [!DNL Sites] | Propriétés des fragments d’expérience pour le **statut des médias sociaux**. | La suppression de la fonctionnalité est prévue prochainement. |
| Sites | [Automatisation de la configuration d’Experience Cloud](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) | Aucune |
| [!DNL Sites] | Fragments de contenu simples basés sur des modèles. | [Fragments de contenu structuré basés sur des modèles](/help/assets/content-fragments/content-fragments-models.md) maintenant. |
| [!DNL Assets] | Workflow `DAM Asset Update` pour traiter les images ingérées. | L’ingestion de ressources utilise maintenant les [microservices de ressources](/help/assets/asset-microservices-overview.md). |
| [!DNL Assets] | Chargez des ressources directement dans [!DNL Experience Manager]. Voir [API de chargement des ressources obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Utilisez le [chargement de binaire direct](/help/assets/add-assets.md). Pour plus d’informations techniques, consultez [API de chargement direct](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Certaines étapes](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) du workflow `DAM Asset Update` ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que [!DNL ImageMagick]. | [Les microservices de ressources](/help/assets/asset-microservices-overview.md) remplacent de nombreux workflows. Pour le traitement personnalisé, utilisez des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | Transcodage FFmpeg des vidéos. | Pour la génération de miniatures FFmpeg, utilisez les [microservices de ressources](/help/assets/asset-microservices-overview.md). Pour le transcodage FFmpeg, utilisez [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | Interface utilisateur de réplication de l’arborescence sous l’onglet Distribuer de l’agent de réplication (suppression après le 30 septembre 2021) | Approches [Gérer la publication](/help/operations/replication.md#manage-publication) ou [Étape de workflow d’activation de l’arborescence](/help/operations/replication.md#tree-activation). |
| [!DNL Foundation] | L’onglet Distribuer de l’écran d’administration de l’agent de réplication et l’API de réplication ne peuvent pas répliquer des modules de contenu de plus de 10 Mo. | [Gérer la publication](/help/operations/replication.md#manage-publication) ou [Étape de workflow d’activation de l’arborescence](/help/operations/replication.md#tree-activation) |
| [!DNL Foundation] | Les intégrations qui utilisent des informations d’identification générées à partir des projets Adobe Developer Console perdent progressivement la prise en charge des informations d’identification du compte de service (JWT). Depuis le 1er mai 2024, les nouvelles informations d’identification du compte de service (JWT) ne peuvent plus être créées dans Adobe Developer Console. Les informations d’identification de compte de service (JWT) existantes restent utilisables pour les intégrations configurées jusqu’au 1er janvier 2025, après quoi elles cesseront de fonctionner, ce qui nécessitera que les clientes et clients et clientes migrent vers les informations d’identification OAuth de serveur à serveur. [En savoir plus](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console). | [Migrez](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration#migration-overview) vers les informations d’identification OAuth serveur à serveur. |
| [!DNL Foundation] | Workflow de publication d’arborescence de contenu et étape de workflow de publication d’arborescence de contenu associée, qui a été utilisée pour les réplications de hiérarchies de contenu. | Utilisez l’[étape de workflow d’activation d’arborescence](/help/operations/replication.md#tree-activation), qui est plus performante. |
| [!DNL Foundation] | Utilisation de YUI pour compresser/réduire les bibliothèques clientes JavaScript. Adobe ne prévoit pas de mettre à jour la bibliothèque YUI. | Adobe recommande aux clientes et clients de passer à Google Closure Compiler (GCC) pour leur implémentation. |
| [!DNL Foundation] | Prise en charge de com.adobe.granite.oauth.server | Intégration Adobe IMS |

## Fonctionnalité supprimée {#removed-features}

Cette section répertorie les fonctionnalités qui ont été supprimées.

| Domaine | Fonctionnalité | Remplacement | Date de suppression visée |
| ------------ | ------------------ | ----------- | ------------------- |
| Interface utilisateur | L’interface utilisateur Classic est supprimée de l’interface utilisateur du produit. Quelques boîtes de dialogue d’interface utilisateur Classic sont disponibles pour quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations de Cloud Service. Les [mises à jour de produit](/help/release-notes/home.md) à venir peuvent supprimer la disponibilité de l’interface utilisateur Classic. | Interface utilisateur standard | Supprimé |
| [!DNL Dynamic Media] | Les intégrations précédentes avec [Dynamic Media Classic](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/sites/administering/integration/scene7#integration) et le [mode hybride de Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/dynamic/config-dynamic#dynamic) ne sont pas disponibles dans [!DNL Experience Manager] as a [!DNL Cloud Service]. | Utilisez [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) fourni avec [!DNL Experience Manager] as a [!DNL Cloud Service]. | Supprimé |
| [!DNL Sites] | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans [!DNL Experience Manager] 6.4 et ont été supprimées d’[!DNL Experience Manager]. | Supprimé |
| [!DNL Sites] | Importateur de conception | Cette fonctionnalité a été supprimée, car les sections non modifiables du référentiel de [!DNL Experience Manager] ne sont pas accessibles au moment de l’exécution. | Supprimé |
| [!DNL Assets] | Le partage d’[!DNL Assets] avec le service principal Assets et le service Creative Cloud n’est pas disponible. | Pour l’intégration à [!DNL Adobe Creative Cloud], utilisez [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html). | Supprimé |
| [!DNL Foundation] | Prise en charge des sources de données Apache Sling (offre spéciale OSGi org.apache.sling.datasource) | S/O | Supprimé |
| [!DNL Foundation] | Prise en charge des modèles de script JST (lot OSGi org.apache.sling.scripting.jst) | S/O | Supprimé |
| [!DNL Foundation] | Prise en charge d’Apache Felix Http Whiteboard | OSGi Http Whiteboard | Mars 2022 |
| [!DNL Foundation] | Prise en charge de la fonctionnalité org.apache.sling.serviceusermapping pour [obtenir l’ID d’utilisateur ou d’utilisatrice du service](https://sling.apache.org/apidocs/sling12/org/apache/sling/serviceusermapping/ServiceUserMapper.html#getServiceUserID-org.osgi.framework.Bundle-java.lang.String-) | S/O | 30/08/24 |
| [!DNL Foundation] | L’exécution de Java 11 est obsolète et Adobe l’a remplacée par l’exécution de Java 21. Cependant, un code créé avec Java 11 reste acceptable (Java 17 et 21 sont les autres options). | L’exécution de Java 21 est appliquée. Pour garantir la compatibilité, il est essentiel de mettre à jour les versions de bibliothèque comme indiqué dans la section [Exigences d’exécution](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements). | 5/29/25 mars |

## API obsolètes {#aem-apis}

Les API du tableau ci-dessous (cliquez pour développer) ont été annoncées comme obsolètes, mais n’ont pas encore été supprimées.  L’utilisation de ces API doit cesser avant la date de suppression cible, faute de quoi des problèmes liés aux performances, à la disponibilité et à la sécurité risquent de se présenter. Certaines API font référence à la section Guide de suppression des API ci-dessous.

>[!IMPORTANT]
> Plusieurs API doivent être supprimées le **26 février 2026**. Veuillez consulter ces dates et impacts clés :
>
> * **À compter du 26 janvier 2026** : les e-mails de notification du Centre d’actions sont envoyés **chaque semaine par environnement** comme rappel pour supprimer l’utilisation de ces API.
> * **26 février 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API seront **mis en pause** pendant l’étape **Qualité du code**. Un responsable de déploiement, un chef de projet ou un propriétaire d’entreprise peut contourner le problème pour autoriser le pipeline à continuer.
> * **26 mars 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API échoueront **&#x200B;**&#x200B;pendant l’étape **Qualité du code**, **blocage des déploiements** du nouveau code jusqu’à ce que l’utilisation soit supprimée.
> * **30 avril 2026** : les environnements qui utilisent toujours ces API peuvent **ne plus recevoir de mises à jour critiques de versions d’Adobe**.
>
> Pour empêcher les blocs de déploiement, supprimez l’utilisation de l’API avant le 26 mars 2026.


<details>
  <summary>Développez pour afficher la liste des API obsolètes.</summary>
<table style="table-layout:auto">
  <tr>
    <th>Package/classe</th>
    <th>Commentaires</th>
    <th>Date d’obsolescence</th>
    <th>Date de suppression visée</th>
  </tr>
<tbody>
  <tr>
    <td>org.apache.sling.commons.auth<br>org.apache.sling.commons.auth.spi</td>
    <td>Utilisez les interfaces Auth Core / Auth Core SPI de Sling comme alternative. <a href="#org.apache.sling.commons.auth">Voir les notes de suppression ci-dessous.</a></td>
    <td>2015</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
<td>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.util<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread</td>
    <td>Les packages Eclipse Jetty et Felix Http Jetty ne sont plus pris en charge. <a href="#org.eclipse.jetty">Voir les notes de suppression ci-dessous.</a></td>
    <td>27/05/2021</td>
    <td>2/26/2026</td>
  </tr>
 <tr>     <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>L’utilisation de cette API n’est pas prise en charge dans AEM as a Cloud Service. <a href="#com.mongodb">Voir les notes de suppression ci-dessous.</a></td>
    <td>27/05/2021</td>
    <td>2/26/2026</td>
  </tr>
   <tr>
    <td>org.apache.abdera<br>org.apache.abdera.model<br>org.apache.abdera.factory<br>org.apache.abdera.ext.media<br>org.apache.abdera.util<br>org.apache.abdera.i18n.iri<br>org.apache.abdera.writer<br>org.apache.abdera.i18n.rfc4646<br>org.apache.abdera.i18n.rfc4646.enums<br>org.apache.abdera.i18n.text<br>org.apache.abdera.filter<br>org.apache.abdera.xpath<br>org.apache.abdera.i18n.text.io<br>org.apache.abdera.i18n.text.data<br>org.apache.abdera.parser</td>
    <td>Cette API est obsolète, car le projet Apache Abdera a été supprimé en 2017. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Voir les notes de suppression ci-dessous.</a></td>
    <td>29/07/2021</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.abdera.ext.opensearch<br>org.apache.abdera.ext.opensearch.model<br>org.apache.abdera.ext.opensearch.server<br>org.apache.abdera.ext.opensearch.server.impl<br>org.apache.abdera.ext.opensearch.server.processors<br>org.apache.abdera.i18n.iri.data<br>org.apache.abdera.i18n.lang<br>org.apache.abdera.i18n.templates<br>org.apache.abdera.i18n.unicode.data<br>org.apache.abdera.parser.stax<br>org.apache.abdera.parser.stax.util<br>org.apache.abdera.protocol<br>org.apache.abdera.protocol.client<br>org.apache.abdera.protocol.client.cache<br>org.apache.abdera.protocol.client.util<br>org.apache.abdera.protocol.error<br>org.apache.abdera.protocol.server<br>org.apache.abdera.protocol.server.context<br>org.apache.abdera.protocol.server.filters<br>org.apache.abdera.protocol.server.impl<br>org.apache.abdera.protocol.server.multipart<br>org.apache.abdera.protocol.server.processors<br>org.apache.abdera.protocol.server.provider.basic<br>org.apache.abdera.protocol.server.provider.managed<br>org.apache.abdera.protocol.server.servlet<br>org.apache.abdera.protocol.util<br>org.apache.abdera.util.filter</td>
    <td>Cette API est obsolète, car le projet Apache Abdera a été supprimé en 2017. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Voir les notes de suppression ci-dessous.</a></td>
    <td>08/04/2019</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.whiteboard</td>
    <td>Le tableau blanc HTTP Apache Felix nʼest plus pris en charge. Migrez votre code vers le tableau blanc HTTP OSGI. <a href="#org.apache.felix.http.whiteboard">Voir les notes de suppression ci-dessous.</a></td>
    <td>27/01/2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.cocoon.xml.dom<br>org.apache.cocoon.xml.sax</td>
    <td>Cette API est obsolète. Migrez votre code vers les API XML fournies par le JDK.</td>
    <td>27/01/2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>ch.qos.logback.classic<br>ch.qos.logback.classic.boolex<br>ch.qos.logback.classic.db.names<br>ch.qos.logback.classic.db.script<br>ch.qos.logback.classic.encoder<br>ch.qos.logback.classic.filter<br>ch.qos.logback.classic.helpers<br>ch.qos.logback.classic.html<br>ch.qos.logback.classic.jmx<br>ch.qos.logback.classic.joran<br>ch.qos.logback.classic.joran.action<br>ch.qos.logback.classic.jul<br>ch.qos.logback.classic.layout<br>ch.qos.logback.classic.log4j<br>ch.qos.logback.classic.net<br>ch.qos.logback.classic.net.server<br>ch.qos.logback.classic.pattern<br>ch.qos.logback.classic.pattern.color<br>ch.qos.logback.classic.selector<br>ch.qos.logback.classic.selector.servlet<br>ch.qos.logback.classic.servlet<br>ch.qos.logback.classic.sift<br>ch.qos.logback.classic.spi<br>ch.qos.logback.classic.turbo<br>ch.qos.logback.classic.util<br>ch.qos.logback.core<br>ch.qos.logback.core.boolex<br>ch.qos.logback.core.encoder<br>ch.qos.logback.core.filter<br>ch.qos.logback.core.helpers<br>ch.qos.logback.core.hook<br>ch.qos.logback.core.html<br>ch.qos.logback.core.joran<br>ch.qos.logback.core.joran.action<br>ch.qos.logback.core.joran.conditional<br>ch.qos.logback.core.joran.event<br>ch.qos.logback.core.joran.event.stax<br>ch.qos.logback.core.joran.node<br>ch.qos.logback.core.joran.spi<br>ch.qos.logback.core.joran.util<br>ch.qos.logback.core.joran.util.beans<br>ch.qos.logback.core.layout<br>ch.qos.logback.core.net<br>ch.qos.logback.core.net.server<br>ch.qos.logback.core.net.ssl<br>ch.qos.logback.core.pattern<br>ch.qos.logback.core.pattern.color<br>ch.qos.logback.core.pattern.parser<br>ch.qos.logback.core.pattern.util<br>ch.qos.logback.core.property<br>ch.qos.logback.core.read<br>ch.qos.logback.core.recovery<br>ch.qos.logback.core.rolling<br>ch.qos.logback.core.rolling.helper<br>ch.qos.logback.core.sift<br>ch.qos.logback.core.spi<br>ch.qos.logback.core.status<br>ch.qos.logback.core.subst<br>ch.qos.logback.core.util</td>
    <td>AEM as a Cloud Service ne prend pas en charge cette API de journalisation interne. <a href="#ch.qos.logback">Voir les notes de suppression ci-dessous.</a></td>
    <td>27/01/2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.slf4j.spi</td>
    <td>AEM as a Cloud Service ne prend pas en charge cette API log4j interne. <a href="#org.slf4j">Voir les notes de suppression ci-dessous.</a></td>
    <td>27/01/2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.log4j<br>org.apache.log4j.helpers<br>org.apache.log4j.spi<br>org.apache.log4j.xml</td>
    <td>Apache Log4j 1 a atteint sa fin de vie en 2015 et n’est plus pris en charge. <a href="#org.apache.log4j">Voir les notes de suppression ci-dessous.</a></td>
    <td>27/01/2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>  <td>com.google.common.annotations<br>com.google.common.base<br>com.google.common.cache<br>com.google.common.collect<br>com.google.common.escape<br>com.google.common.eventbus<br>com.google.common.hash<br>com.google.common.html<br>com.google.common.io<br>com.google.common.math<br>com.google.common.net<br>com.google.common.primitives<br>com.google.common.reflect<br>com.google.common.util.concurrent<br>com.google.common.xml</td>
    <td>Les bibliothèques principales Google Guava sont obsolètes dans Cloud Service. <a href="#com.google.common">Consultez les notes de suppression ci-dessous.</a></td>
    <td>15/05/2023</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.slf4j.event</td>
    <td>AEM as a Cloud Service ne prend pas en charge cette API slf4j interne. <a href="#org.slf4j">Consultez les notes de suppression ci-dessous.</a></td>
    <td>11/04/2022</td>
    <td>2/26/2026</td>
  </tr>
    <tr>
    <td>com.drew.*</td>
    <td>L’extraction des métadonnées des images et des vidéos doit s’effectuer via Asset Compute dans Cloud Service ou via Apache POI ou Apache Tika.</td>
    <td>17/09/2024</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.blob.*</td>
    <td>Cette API est réservée à un usage interne.</td>
    <td>23/09/2024</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.memory</td>
    <td>Cette API est réservée à un usage interne.</td>
    <td>23/09/2024</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
<td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n<br>org.apache.felix.webconsole.spi</td>
    <td>La console web Felix n’est pas prise en charge dans les environnements cloud. <a href="#org.apache.felix.webconsole">Consultez les notes de suppression ci-dessous.</a></td>
    <td>30/04/2021</td>
    <td>2/26/2026</td>
  </tr>
<td>org.bson<br/>org.bson.assertions<br/>org.bson.codecs<br/>org.bson.codecs.configuration<br/>org.bson.codecs.pojo<br/>org.bson.codecs.pojo.annotations<br/>org.bson.conversions<br/>org.bson.diagnostics<br/>org.bson.internal<br/>org.bson.io<br/>org.bson.json<br/>org.bson.types<br/>org.bson.util</td>
    <td>L’utilisation de cette API n’est pas prise en charge dans AEM as a Cloud Service.</td>
    <td>31/10/2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>À déterminer</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>L’implémentation Apache Johnzon de <a href="https://johnzon.apache.org/index.html">javax.json</a> est recommandée et devrait être utilisée. </td>
    <td>30/04/2021</td>
    <td>À déterminer</td>
  </tr>
  <tr>
<td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2 est en mode de maintenance. Commons Lang 3 devrait être utilisé à la place. <a href="#apache.commons">Consultez les notes de suppression ci-dessous.</a></td>
    <td>30/04/2021</td>
    <td>À déterminer</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Commons Collections 3 est en mode de maintenance. Commons Collections 4 devrait être utilisé à la place. <a href="#apache.commons">Consultez les notes de suppression ci-dessous.</a></td>
    <td>30/04/2021</td>
    <td>À déterminer</td>
  </tr>
  <tr>
    <td>com.day.cq.contentsync.handler.util</td>
    <td>Cette API est obsolète. Utilisez les créateurs de ressources d’Apache Sling à la place.</td>
    <td>31/10/2022</td>
    <td>À déterminer</td>
  </tr>
  <tr><td>org.apache.sling.commons.json<br>org.apache.sling.commons.json.http<br>org.apache.sling.commons.json.io<br>org.apache.sling.commons.json.jcr<br>org.apache.sling.commons.json.sling<br>org.apache.sling.commons.json.util<br>org.apache.sling.commons.json.xml</td>
    <td>AEM as a Cloud Service ne prend pas en charge cette API.</td>
    <td>15/05/2023</td>
    <td>À déterminer</td>
  </tr>
  <tr>
    <td>com.day.cq.xss<br>com.day.cq.xss.taglib<br>com.day.cq.xss.impl</td>
    <td>Utilisez org.apache.sling.xss à la place.</td>
    <td>12/12/2023</td>
    <td>À déterminer</td>
  </tr>
  <tr>
    <td>com.adobe.granite.xss<br>com.adobe.granite.xss.impl</td>
    <td>Utilisez org.apache.sling.xss à la place.</td>
    <td>12/12/2023</td>
    <td>À déterminer</td>
  </tr>
  </tbody>
</table>
</details>

## API supprimées {#removed-apis}

Cette section répertorie les API obsolètes et supprimées. Certaines API font référence à la section Guide de suppression des API ci-dessous.

<details>
  <summary>Développez pour afficher la liste des API supprimées.</summary>
<table style="table-layout:auto">
  <tr>
    <th>Package/classe</th>
    <th>Commentaires</th>
  </tr>
<tbody>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>Utiliser l’API Discovery de Sling comme alternative</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Les gestionnaires de persistance personnalisée ne sont pas pris en charge dans AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Il est recommandé d’utiliser l’API Apache Felix HealthCheck à la place</td>
  </tr>
  <tr> <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml</td>
    <td>Les packages Eclipse Jetty et Felix Http Jetty ne sont plus pris en charge.</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info<br>org.apache.felix.scr.component</td>
    <td>Le métatype Apache Felix et les API SCR sont obsolètes.  Utilisez le métatype OSGi et les API Declarative Service à la place.</td>
  </tr>
  <tr>
    <td>org.slf4j.impl</td>
    <td>Les classes d’implémentation de journal ne sont pas compatibles avec AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.sling.startupfilter<br>com.adobe.granite.crypto.spi<br>com.adobe.granite.crpyto.spi.base<br>com.adobe.agl.impl.data.icudt40b<br>com.adobe.agl.impl.data.icudt40b.brkitr<br>com.adobe.agl.impl.data.icudt40b.coll<br>com.adobe.agl.impl.data.icudt40b.rbnf<br>com.<br>adobe.agl.impl.data.icudt40b.translit<br>com.adobe.internal.pdf.tika<br>com.adobe.internal.pdftoolkit.color<br>com.adobe.internal.pdftoolkit.core.encryption<br>com.adobe.internal.pdftoolkit.core.encryption.impl<br>com.adobe.internal.pdftoolkit.core.traverser<br>com.adobe.internal.pdftoolkit.graphicsDOM<br>com.adobe.internal.pdftoolkit.graphicsDOM.shading<br>com.adobe.internal.pdftoolkit.graphicsDOM.utils<br>com.adobe.internal.pdftoolkit.image<br>com.adobe.internal.pdftoolkit.pdf.content<br>com.adobe.internal.pdftoolkit.pdf.content.processor<br>com.adobe.internal.pdftoolkit.pdf.content.processor.base14fontwidths<br>com.adobe.internal.pdftoolkit.pdf.contentmodify<br>com.adobe.internal.pdftoolkit.pdf.contentmodify.impl<br>com.adobe.internal.pdftoolkit.pdf.digsig<br>com.adobe.internal.pdftoolkit.pdf.document<br>com.adobe.internal.pdftoolkit.pdf.document.listener<br>com.adobe.internal.pdftoolkit.pdf.document.permissionhandlers<br>com.adobe.internal.pdftoolkit.pdf.filters<br>com.adobe.internal.pdftoolkit.pdf.graphics<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces.cmykresources<br>com.adobe.internal.pdftoolkit.pdf.graphics.font<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.encodings<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.optionalcontent<br>com.adobe.internal.pdftoolkit.pdf.graphics.patterns<br>com.adobe.internal.pdftoolkit.pdf.graphics.shading<br>com.adobe.internal.pdftoolkit.pdf.graphics.xobject<br>com.adobe.internal.pdftoolkit.pdf.impl<br>com.adobe.internal.pdftoolkit.pdf.inlineimage<br>com.adobe.internal.pdftoolkit.pdf.interactive<br>com.adobe.internal.pdftoolkit.pdf.interactive.action<br>com.adobe.internal.pdftoolkit.pdf.interactive.annotation<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms.impl<br>com.adobe.internal.pdftoolkit.pdf.interactive.geospatial<br>com.adobe.internal.pdftoolkit.pdf.interactive.markedcontent<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation.collection<br>com.adobe.internal.pdftoolkit.pdf.interactive.readerrequirements<br>com.adobe.internal.pdftoolkit.pdf.interactive.requirement<br>com.adobe.internal.pdftoolkit.pdf.interchange<br>com.adobe.internal.pdftoolkit.pdf.interchange.documentparts<br>com.adobe.internal.pdftoolkit.pdf.interchange.metadata<br>com.adobe.internal.pdftoolkit.pdf.interchange.prepress<br>com.adobe.internal.pdftoolkit.pdf.interchange.structure<br>com.adobe.internal.pdftoolkit.pdf.multimedia<br>com.adobe.internal.pdftoolkit.pdf.page<br>com.adobe.internal.pdftoolkit.pdf.rendering<br>com.adobe.internal.pdftoolkit.pdf.transparency<br>com.adobe.internal.pdftoolkit.pdf.utils<br>com.adobe.internal.pdftoolkit.services.Jpeg2000<br>com.adobe.internal.pdftoolkit.services.fontresources<br>com.adobe.internal.pdftoolkit.services.fontresources.subsetting<br>com.adobe.internal.pdftoolkit.services.interchange.structure<br>com.adobe.internal.pdftoolkit.services.optionalcontent<br>com.adobe.internal.pdftoolkit.services.optionalcontent.impl<br>com.adobe.internal.pdftoolkit.services.pdfParser<br>com.adobe.internal.pdftoolkit.services.permissions<br>com.adobe.internal.pdftoolkit.services.rasterizer<br>com.adobe.internal.pdftoolkit.services.readingorder<br>com.adobe.internal.pdftoolkit.services.security<br>com.adobe.internal.pdftoolkit.services.swf<br>com.adobe.internal.pdftoolkit.services.textextraction<br>com.adobe.internal.pdftoolkit.services.textextraction.impl<br>com.adobe.internal.pdftoolkit.services.xmp<br>com.adobe.internal.util.base64<br>com.adobe.internal.xmp.utils<br>com.day.crx.core.cluster<br>com.day.crx.packaging<br>com.day.crx.packaging.gfx<br>com.day.crx.query<br>com.day.crx.sling.server.jmx<br>com.day.durbo<br>com.day.durbo.io<br>com.day.imageio.plugins<br>org.apache.aries.jmx.codec<br>org.h2.mvstore<br>org.h2.mvstore.rtree<br>org.h2.mvstore.type<br>org.openxmlformats.schemas.drawingml.x2006.chart.impl<br>org.openxmlformats.schemas.drawingml.x2006.main.impl<br>org.openxmlformats.schemas.drawingml.x2006.picture.impl<br>org.openxmlformats.schemas.drawingml.x2006.spreadsheetDrawing.impl<br>org.openxmlformats.schemas.drawingml.x2006.wordprocessingDrawing.impl<br>org.openxmlformats.schemas.officeDocument.x2006.customProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.docPropsVTypes.impl<br>org.openxmlformats.schemas.officeDocument.x2006.extendedProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.relationships.impl<br>org.openxmlformats.schemas.presentationml.x2006.main.impl<br>org.openxmlformats.schemas.spreadsheetml.x2006.main.impl<br>org.openxmlformats.schemas.wordprocessingml.x2006.main.impl<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes.impl<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature.impl<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties.impl<br>org.openxmlformats.schemas.xpackage.x2006.relationships<br>org.openxmlformats.schemas.xpackage.x2006.relationships.impl<br>com.adobe.internal.afml<br>com.adobe.internal.agm<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es2<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es3<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.compoundtype<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.editablepdf<br>com.adobe.internal.pdftoolkit.services.ap<br>com.adobe.internal.pdftoolkit.services.ap.annot<br>com.adobe.internal.pdftoolkit.services.ap.extension<br>com.adobe.internal.pdftoolkit.services.ap.impl<br>com.adobe.internal.pdftoolkit.services.ap.spi<br>com.adobe.internal.pdftoolkit.services.digsig<br>com.adobe.internal.pdftoolkit.services.digsig.cryptoprovider<br>com.adobe.internal.pdftoolkit.services.digsig.docmodanalysis<br>com.adobe.internal.pdftoolkit.services.digsig.spi<br>com.adobe.internal.pdftoolkit.services.fdf<br>com.adobe.internal.pdftoolkit.services.formflattener<br>com.adobe.internal.pdftoolkit.services.forms<br>com.adobe.internal.pdftoolkit.services.imageconversion<br>com.adobe.internal.pdftoolkit.services.javascript<br>com.adobe.internal.pdftoolkit.services.javascript.extension<br>com.adobe.internal.pdftoolkit.services.manipulations<br>com.adobe.internal.pdftoolkit.services.manipulations.impl<br>com.adobe.internal.pdftoolkit.services.optimizer<br>com.adobe.internal.pdftoolkit.services.pdfa<br>com.adobe.internal.pdftoolkit.services.pdfa.error<br>com.adobe.internal.pdftoolkit.services.pdfa2<br>com.adobe.internal.pdftoolkit.services.pdfa2.error<br>com.adobe.internal.pdftoolkit.services.pdfa2.error.codes<br>com.adobe.internal.pdftoolkit.services.pdfa3<br>com.adobe.internal.pdftoolkit.services.pdfport<br>com.adobe.internal.pdftoolkit.services.portfolio<br>com.adobe.internal.pdftoolkit.services.rcg<br>com.adobe.internal.pdftoolkit.services.rcg.impl<br>com.adobe.internal.pdftoolkit.services.redaction<br>com.adobe.internal.pdftoolkit.services.redaction.handler<br>com.adobe.internal.pdftoolkit.services.sanitization<br>com.adobe.internal.pdftoolkit.services.xbm<br>com.adobe.internal.pdftoolkit.services.xdp<br>com.adobe.internal.pdftoolkit.services.xfa<br>com.adobe.internal.pdftoolkit.services.xfa.form<br>com.adobe.internal.pdftoolkit.services.xfatext<br>com.adobe.internal.pdftoolkit.services.xfdf<br>com.adobe.internal.pdftoolkit.services.xobjhandler<br>com.adobe.internal.pdftoolkit.xml<br>com.adobe.octopus.extract<br>opennlp.tools.doccat<br>opennlp.tools.entitylinker<br>opennlp.tools.formats<br>opennlp.tools.formats.ad<br>opennlp.tools.formats.brat<br>opennlp.tools.formats.convert<br>opennlp.tools.formats.frenchtreebank<br>opennlp.tools.formats.muc<br>opennlp.tools.formats.ontonotes<br>opennlp.tools.lemmatizer<br>opennlp.tools.parser<br>opennlp.tools.parser.chunking<br>opennlp.tools.parser.lang.en<br>opennlp.tools.parser.lang.es<br>opennlp.tools.parser.treeinsert<br>opennlp.tools.sentdetect<br>opennlp.tools.sentdetect.lang<br>opennlp.tools.sentdetect.lang.th<br>opennlp.tools.stemmer<br>opennlp.tools.stemmer.snowball<br>opennlp.tools.tokenize.lang.en<br>org.apache.commons.imaging.color<br>org.apache.commons.imaging.common<br>org.apache.commons.imaging.common.itu_t4<br>org.apache.commons.imaging.common.mylzw<br>org.apache.commons.imaging.formats.bmp<br>org.apache.commons.imaging.formats.dcx<br>org.apache.commons.imaging.formats.gif<br>org.apache.commons.imaging.formats.icns<br>org.apache.commons.imaging.formats.ico<br>org.apache.commons.imaging.formats.jpeg<br>org.apache.commons.imaging.formats.jpeg.decoder<br>org.apache.commons.imaging.formats.jpeg.exif<br>org.apache.commons.imaging.formats.jpeg.iptc<br>org.apache.commons.imaging.formats.jpeg.segments<br>org.apache.commons.imaging.formats.jpeg.xmp<br>org.apache.commons.imaging.formats.pcx<br>org.apache.commons.imaging.formats.png<br>org.apache.commons.imaging.formats.png.chunks<br>org.apache.commons.imaging.formats.png.scanlinefilters<br>org.apache.commons.imaging.formats.png.transparencyfilters<br>org.apache.commons.imaging.formats.pnm<br>org.apache.commons.imaging.formats.psd<br>org.apache.commons.imaging.formats.psd.dataparsers<br>org.apache.commons.imaging.formats.psd.datareaders<br>org.apache.commons.imaging.formats.rgbe<br>org.apache.commons.imaging.formats.tiff<br>org.apache.commons.imaging.formats.tiff.constants<br>org.apache.commons.imaging.formats.tiff.datareaders<br>org.apache.commons.imaging.formats.tiff.fieldtypes<br>org.apache.commons.imaging.formats.tiff.photometricinterpreters<br>org.apache.commons.imaging.formats.tiff.taginfos<br>org.apache.commons.imaging.formats.tiff.write<br>org.apache.commons.imaging.formats.wbmp<br>org.apache.commons.imaging.formats.xbm<br>org.apache.commons.imaging.formats.xpm<br>org.apache.commons.imaging.icc<br>org.apache.commons.imaging.palette<br>org.apache.commons.imaging.util<br>com.adobe.dam.print.ids.utils<br>com.day.cq.dam.api.reporting<br>com.day.cq.dam.entitlement.api<br>com.day.cq.dam.handler.standard.epub<br>com.day.cq.dam.handler.standard.keynote<br>com.day.cq.dam.handler.standard.mp3<br>com.day.cq.dam.handler.standard.msoffice<br>com.day.cq.dam.handler.standard.msoffice.wmf<br>com.day.cq.dam.handler.standard.ooxml<br>com.day.cq.dam.handler.standard.pdf<br>com.day.cq.dam.handler.standard.pict<br>com.day.cq.dam.handler.standard.ps<br>com.day.cq.dam.handler.standard.psd<br>com.day.cq.dam.handler.standard.zip<br>com.day.cq.dam.word.extraction<br>com.day.cq.dam.word.process<br>com.adobe.xmp.worker.files<br>com.adobe.cq.address.api<br>com.adobe.cq.address.api.location<br>com.day.cq.mcm.emailprovider.impl.types<br>com.day.io<br>com.day.io.disk<br>com.day.io.file<br>org.apache.commons.exec.environment<br>org.apache.commons.exec.launcher<br>org.apache.commons.exec.util<br>com.google.zxing<br>com.google.zxing.common<br>com.google.zxing.common.reedsolomon<br>com.google.zxing.qrcode.decoder<br>com.google.zxing.qrcode.encoder<br>com.adobe.cq.dam.dm.internalapi.image_server<br>com.day.cq.dam.api.s7dam.jobs<br>com.day.cq.dam.api.s7dam.omnisearch<br>com.day.cq.dam.api.s7dam.scene7<br>com.day.cq.dam.scene7<br>com.day.cq.dam.scene7.api.net<br>com.day.cq.analytics.sitecatalyst.rsmerger<br>com.day.cq.searchpromote<br>com.day.cq.searchpromote.xml<br>com.day.cq.searchpromote.xml.form<br>com.day.cq.searchpromote.xml.result&gt;</td>
    <td>API héritée d’AEM 6.x.</td>
  </tr>
  <tr>
    <td>org.apache.sling.discovery.commons<br>org.apache.sling.discovery.commons.providers<br>org.apache.sling.discovery.commons.providers.base<br>org.apache.sling.discovery.commons.providers.spi<br>org.apache.sling.discovery.commons.providers.spi.base<br>org.apache.sling.discovery.commons.providers.util</td>
    <td>Cette API nʼest pas prise en charge dans Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml<br>org.apache.jackrabbit.vault.util.xml.serialize</td>
    <td>Les classes util liées à Apache Xerces sont supprimées dans les versions ultérieures, ce qui entraîne un changement de version majeur. Comme ces utilitaires sont destinés à un usage interne à Filevault, lʼAPI devient obsolète dans lʼinterface de lʼAPI publique.</td>
  </tr>
  <tr>
    <td>org.apache.sling.atom.taglib<br>org.apache.sling.atom.taglib.media</td>
    <td>API héritée d’AEM 6.x. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Voir les notes de suppression ci-dessous.</a></td>
  </tr>
  <tr>
    <td>org.apache.sling.commons.log.logback<br>org.apache.sling.commons.log.logback.webconsole</td>
    <td>AEM as a Cloud Service ne prend pas en charge cette API de journalisation interne.</td>
  </tr>
  <tr>
    <td>com.github.jknack.handlebars.js</td>
    <td>Mise à niveau de Handlebars requise de la version 4.0.5 à la version 4.3.0 en raison d’une vulnérabilité de sécurité. Ce package n’est plus présent dans les mises à niveau de Handlebars.</td>
  </tr>
  <tr>
    <td>com.adobe.granite.resourceresolverhelper</td>
    <td>Cette API n’est plus prise en charge. Utilisez org.apache.sling.api.resource.ResourceResolverFactory à la place.</td>
  </tr>
  <tr>
    <td>org.apache.sling.repoinit.jcr<br>org.apache.sling.repoinit.parser.operations</td>
    <td>L’utilisation de cette API n’est pas prise en charge dans AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.cache</td>
    <td>Cette API est réservée à un usage interne.</td>
  </tr>
</tbody>
</table>
</details>

## Conseils pour la suppression des API {#api-removal-guidance}

Cette section contient des conseils de suppression pour diverses API dans les tableaux ci-dessus.

Pour identifier les API Java obsolètes que votre code utilise, intégrez le plug-in Maven [AEM as a Cloud Service SDK Build Analyzer](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin) dans votre projet Maven et exécutez-le localement. Le rapport répertorie toutes les utilisations obsolètes détectées de l’API et indique quel lot OSGi fait référence à chaque API.

Bien que vous deviez remédier à toutes les API obsolètes au fil du temps, donnez la priorité à toutes les API répertoriées dans le tableau API obsolètes avec une date de suppression cible fixée au 26 février 2026 (ou avant). Dans le rapport AEM Analyzer, ces API peuvent apparaître avec une date de suppression effective du 8/31/2025.

Après avoir mis à jour votre code, vérifiez qu’aucune utilisation obsolète de l’API ne reste dans Cloud Manager en vérifiant les résultats de l’étape de qualité du code.

### Directives générales

Si vous utilisez une bibliothèque tierce qui nécessite actuellement une API obsolète, essayez d’effectuer une mise à jour vers une version plus récente de cette bibliothèque tierce.

Si vous utilisez ACS AEM Commons, utilisez au moins la version 6.11.0 (la dernière version est recommandée) et assurez-vous d’[inclure la version pour Cloud Service](https://adobe-consulting-services.github.io/acs-aem-commons/pages/maven.html) en spécifiant le `cloud` de classificateur du package de contenu.

Si l’importation d’une API obsolète est marquée comme `optional`, vous devez tout de même essayer de la supprimer. Toutefois, cette utilisation facultative ne bloque pas les déploiements. Cependant, votre déploiement peut être affecté, une fois que l’importation facultative n’est plus satisfaite.

### Suppression de `org.apache.sling.commons.auth*` {#org.apache.sling.commons.auth}

Si vous utilisez `org.apache.sling.commons.auth` et/ou `org.apache.sling.commons.auth.spi`, l’utilisation peut être remplacée par la migration du code vers `org.apache.sling.auth`. `org.apache.sling.auth.spi`. Si vous utilisez une ancienne version de [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/), veillez à effectuer la mise à jour vers la dernière version.

Liste d’actions :

* Mettre à jour ACS AEM Commons vers la dernière version (au moins 6.11.0)
* Migrez d’`org.apache.sling.commons.auth` et/ou `org.apache.sling.commons.auth.spi` vers `org.apache.sling.auth`, soit `org.apache.sling.auth.spi`.

### Suppression de `org.apache.felix.webconsole*` {#org.apache.felix.webconsole}

Si vous utilisez des packages provenant de `org.apache.felix.webconsole*`, supprimez ce code du projet. La console web n’est pas accessible dans Cloud Service.

Liste d’actions :

* Supprimer le code à l’aide de packages de `org.apache.felix.webconsole*`

### Suppression de `org.eclipse.jetty*` {#org.eclipse.jetty}

Si vous utilisez un package `org.eclipse.jetty` ou l’un de ses sous-packages, vous pouvez effectuer une migration vers d’autres bibliothèques tierces avec une fonctionnalité similaire. Si la migration n’est pas possible, ajoutez les lots requis de la liste ci-dessous à votre projet.

Liste d’actions :

* Remplacez l’utilisation des packages `org.eclipse.jetty` par d’autres bibliothèques tierces/un autre code propre ou
* Sélectionnez les lots requis dans cette liste et ajoutez-les à votre projet :
   * `org.eclipse.jetty:jetty-client:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-http:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-io:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-security:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-servlet:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-server:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util-ajax:9.4.54.v20240208`

### Suppression de `com.mongodb` {#com.mongodb}

Ajoutez l’API cliente Mongo à votre projet.

Liste d’actions :

* Ajoutez ce lot à votre projet.
   * `org.mongodb:mongo-java-driver:3.12.7`

Vous pouvez choisir une autre version, en fonction de vos besoins.

### Suppression de `com.google.common*` {#com.google.common}

Supprimez l’utilisation des bibliothèques principales Google Guava ou incluez une version appropriée dans votre projet. Dans de nombreux cas, l’utilisation de cette bibliothèque peut être remplacée par des classes de collection provenant des collections 4 JDK ou Apache Commons. Si vous ne trouvez aucun remplacement, incluez la dernière version de la bibliothèque principale Google Guave dans votre projet. Si vous utilisez une ancienne version de [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/), veillez à effectuer la mise à jour vers la dernière version.

Liste d’actions :

* Mettre à jour ACS AEM Commons vers la dernière version (au moins 6.11.0)
* Remplacez l’utilisation de la bibliothèque principale Guava Google par des collections 4 JDK ou Apache Commons.
* Si nécessaire, ajoutez ce lot à votre projet (remplacez la version par la dernière disponible) :
   * `com.google.guava:guava:33.4.8-jre`

### Suppression d’`Apache Commons Lang 2 and Apache Commons Collections 3` {#apache.commons}

Supprimez l’utilisation des bibliothèques Apache Commons non gérées et remplacez-les par l’utilisation de versions prises en charge. Dans la plupart des cas, cela nécessite simplement d’ajuster les imports de packages. Dans certains cas seulement, les classes ou les méthodes ont été renommées. Si vous utilisez une ancienne version de [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/), veillez à effectuer la mise à jour vers la dernière version.

Liste d’actions :

* Mettre à jour ACS AEM Commons vers la dernière version (au moins 6.11.0)
* Remplacer les imports de `org.apache.commons.lang*` par `org.apache.commons.lang3`
* Remplacer les imports de `org.apache.commons.collections*` par `org.apache.commons.collecitons4`

### Utilisation de `org.apache.abdera*` et `org.apache.sling.atom.taglib` {#org.apache.abdera_or_org.apache.sling.atom.taglib}

Remplacez l’utilisation de n’importe quel package de `org.apache.abdera` et `org.apache.sling.atom.taglib` par une bibliothèque tierce fournissant des fonctionnalités similaires ou votre propre code.

Liste d’actions :

* Remplacez l’utilisation des packages de `org.apache.abdera` et `org.apache.sling.atom.taglib` par d’autres bibliothèques tierces/code propre.

### Utilisation de `org.apache.felix.http.whiteboard` {#org.apache.felix.http.whiteboard}

Remplacez l’utilisation de `org.apache.felix.http.whiteboard` par le [tableau blanc HTTP OSGI](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html). L’API OSGi officielle dispose de fonctionnalités similaires. Le plus souvent, le remplacement nécessite uniquement la modification des propriétés d’enregistrement du service.

Liste d’actions :

* Remplacez l’utilisation de `org.apache.felix.http.whiteboard` par le [tableau blanc HTTP OSGI](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html).

### Utilisation de `ch.qos.logback*` {#ch.qos.logback}

La journalisation arrière n’est pas prise en charge dans Cloud Service. Supprimez toute utilisation associée. Si vous utilisez une ancienne version de [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/), veillez à effectuer la mise à jour vers la dernière version.

Liste d’actions :

* Mettre à jour ACS AEM Commons vers la dernière version (au moins 6.11.0)
* Supprimer le code à l’aide de packages de `ch.qos.logback`

### Utilisation de `org.slf4j.event and org.slf4j.spi` {#org.slf4j}

Si vous utilisez `org.slf4j.event` ou `org.slf4j.spi`, supprimez toutes les utilisations associées. Si vous utilisez une ancienne version de [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/), veillez à effectuer la mise à jour vers la dernière version.

Liste d’actions :

* Mettre à jour ACS AEM Commons vers la dernière version (au moins 6.11.0)
* Supprimer le code à l’aide de `org.slf4j.event` et `org.slf4j.spi`
* Si vous utilisez le client Apache Kafka et incluez le bundle de wrapper OSGi d’Apache ServiceMix (`org.apache.servicemix.bundles.kafka-clients`), remplacez-le par le [wrapper client Apache Kafka d’AEM](https://repo.maven.apache.org/maven2/com/adobe/aem/osgi/com.adobe.aem.osgi.kafka-clients/4.0.0_1.0/). Il s’agit de la même version que celle d’Apache ServiceMix, avec seulement l’utilisation de ces deux packages supprimée.

### Utilisation d’`org.apache.log4j` {#org.apache.log4j}

Si vous utilisez `org.apache.log4j`, passez à SLF4J (`org.slf4j`) ou Log4J 2.x (`org.apache.logging.log4j`).

Liste d’actions :

* Remplacer l’utilisation de `org.apache.log4j` par `org.slf4j` (recommandé) ou `org.apache.logging.log4j`

## Configuration OSGI {#osgi-configuration}

Les deux sections ci-dessous représentent la surface de configuration OSGi d’AEM as a Cloud Service. Elles décrivent ce que les clientes et clients peuvent configurer.

1. Le code client ne doit pas configurer les configurations OSGi répertoriées.
1. Liste des configurations OSGi dont les propriétés peuvent être configurées, mais doivent respecter les règles de validation indiquées. Ces règles indiquent si la déclaration de la propriété est requise, son type et, dans certains cas, sa plage de valeurs autorisée.

Le code client peut configurer toute configuration OSGi non répertoriée.

Ces règles sont validées pendant le processus de création de Cloud Manager. D’autres règles peuvent être ajoutées au fil du temps et la date prévue d’application est indiquée dans le tableau. Les clients doivent respecter ces règles avant la date d’application de la cible. Le fait de ne pas respecter les règles après la date de suppression génère des erreurs dans le processus de création de Cloud Manager. Les projets Maven doivent inclure le [module externe Maven Analyseur de build de SDK d’AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin) pour signaler les erreurs de configuration OSGI lors du développement du SDK local.

Vous trouverez des informations supplémentaires sur la configuration OSGI à [cet emplacement](/help/implementing/deploying/configuring-osgi.md).

### Propriétés OSGi obsolètes (bientôt non modifiables) {#deprecated-unmodifiable-osgi-properties}

Les propriétés des PID de composant OSGi suivants sont obsolètes. Vous devez cesser de les utiliser à la date d’application.

| **ID de composant OSGI** | **Propriétés non modifiables** | **Abandon** | **Application** |
|---|---|---|---|
| **`org.apache.sling.commons.log.LogManager`** | tout | 4/24/25 | 31/08/25 (configuration ignorée en juin) |
| **`org.apache.sling.commons.log.LogManager.factory.config`** | org.apache.sling.commons.log.file, org.apache.sling.commons.log.pattern | 4/24/25 | 31/08/25 (configuration ignorée en juin) |
| **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** | tout | 2024 | 31/08/25 |
| **`com.adobe.granite.toggle.impl.dev.DynamicToggleProviderImpl`** | tout | 03/06/25 | 31/08/25 |
| **`org.apache.http.proxyconfigurator`** | tout | 03/06/25 | 31/08/25 |

### Configurations OSGi non modifiables {#unmodifiable-osgi-properties}

Les propriétés des PID des composants OSGi suivants ne peuvent pas être modifiées. Par conséquent, elles ne doivent pas être configurées.

| **ID de composant OSGI** | **Propriétés non modifiables** |
|---|---|
| **`com.day.cq.auth.impl.cug.CugSupportImpl`** |  |
| **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** | tout |
| **`com.adobe.granite.toggle.impl.ToggleRouterImpl`** | tout |
| **`org.apache.sling.engine.impl.log.RequestLoggerFilter`** | tout |
| **`org.apache.sling.feature.apiregions.impl`** | tout |
| **`org.apache.sling.jcr.resource.internal.helper.jcr.BinaryDownloadUriProvider`** | tout |
| **`com.adobe.cq.unifiedshell.impl.discovery.DiscoveryServlet`** | tout |
| **`com.adobe.cq.unifiedshell.impl.ui.FrameErrorHandler`** | tout |
| **`com.adobe.cq.unifiedshell.impl.config.UnifiedShellConfService`** | tout |
| **`com.adobe.cq.unifiedshell.impl.config.RepositoryIdentifier`** | tout |
| **`org.apache.sling.feature.apiregions.factory`** | tout |
| **`com.adobe.granite.toggle.monitor.systemproperty`** | tout |


### Futures restrictions de propriété OSGi appliquées {#future-restrictions-osgi-properties}

À l’avenir, Adobe appliquera les restrictions de propriétés OSGi suivantes. Pour les PID mentionnés, seules les propriétés répertoriées peuvent être configurées.

| PID de composant OSGi |   | Obligatoire | Type | Restriction (le cas échéant) |
|---|---|---|---|---|
| `com.day.cq.mailer.DefaultMailService` | `smtp.host` |   | chaîne |   |
|   | `smtp.port` | Oui | entier | « 465 », « 587 » ou « 25 » |
|   | `smtp.user` |   | chaîne |   |
|   | `smtp.password` |   | chaîne |   |
|   | `from.address` |   | chaîne |   |
|   | `smtp.ssl` |   | chaîne |   |
|   | `smtp.starttls` |   | booléen |   |
|   | `smtp.requiretls` |   | booléen |   |
|   | `debug.email` |   | booléen |   |
|   | `oauth.flow` |   | booléen |   |
| `org.apache.sling.commons.log.LogManager.factory.config` | `org.apache.sling.commons.log.level` | Oui | chaîne | « INFO », « DEBUG » ou « TRACE » |
|   | `org.apache.sling.commons.log.names` |   | séquence de chaînes de caractères |   |
|   | `org.apache.sling.commons.log.additiv` |   | booléen |   |
| `com.day.cq.commons.impl.ExternalizerImpl` | `externalizer.domains` | Non | chaîne[] |   |
|   | `externalizer.encodedpath` | Non | booléen |   |
|   | `externalizer.host` | Non | chaîne |   |
|   | `externalizer.contextpath` | Non | chaîne |   |

### Restrictions des propriétés OSGi {#restrictions-osgi-properties}

Les valeurs de ces propriétés OSGi sont limitées aux règles décrites ci-dessous.

| PID de composant OSGi |   | Obligatoire | Type | Restriction (le cas échéant) |
|---|---|---|---|---|
| `org.apache.felix.eventadmin.impl.EventAdmin` | `org.apache.felix.eventadmin.ThreadPoolSize` | Oui | entier | 2-100 |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | double | -- |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | entier | -- |
|   | `org.apache.felix.eventadmin.RequireTopic` |   | booléen | -- |
|   | `org.apache.felix.eventadmin.IgnoreTimeout` | Oui | séquence de chaînes de caractères | Doit inclure au moins tous les éléments `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*` |
|   | `org.apache.felix.eventadmin.IgnoreTopic` |   | séquence de chaînes de caractères | -- |
| `org.apache.felix.http` | `org.apache.felix.http.timeout` |   | entier |   |
|   | `org.apache.felix.http.session.timeout` |   | entier |   |
|   | `org.apache.felix.http.jetty.threadpool.max` |   | entier |   |
|   | `org.apache.felix.http.jetty.headerBufferSize` |   | entier |   |
|   | `org.apache.felix.http.jetty.requestBufferSize` |   | entier |   |
|   | `org.apache.felix.http.jetty.responseBufferSize` |   | entier |   |
|   | `org.apache.felix.http.jetty.maxFormSize` |   | entier |   |
|   | `org.apache.felix.https.jetty.session.cookie.httpOnly` |   | booléen |   |
|   | `org.apache.felix.https.jetty.session.cookie.secure` |   | booléen |   |
|   | `org.eclipse.jetty.servlet.SessionIdPathParameterName` |   | chaîne |   |
|   | `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding` |   | booléen |   |
|   | `org.eclipse.jetty.servlet.SessionCookie` |   | chaîne |   |
|   | `org.eclipse.jetty.servlet.SessionDomain` |   | chaîne |   |
|   | `org.eclipse.jetty.servlet.SessionPath` |   | chaîne |   |
|   | `org.eclipse.jetty.servlet.MaxAge` |   | entier |   |
|   | `org.eclipse.jetty.servlet.SessionScavengingInterval` |   | entier |   |
|   | `org.apache.felix.jetty.gziphandler.enable` |   | booléen |   |
|   | `org.apache.felix.jetty.gzip.minGzipSize` |   | entier |   |
|   | `org.apache.felix.jetty.gzip.compressionLevel` |   | entier |   |
|   | `org.apache.felix.jetty.gzip.inflateBufferSize` |   | entier |   |
|   | `org.apache.felix.jetty.gzip.syncFlush` |   | booléen |   |
|   | `org.apache.felix.jetty.gzip.excludedUserAgents` |   | chaîne |   |
|   | `org.apache.felix.jetty.gzip.includedMethods` |   | séquence de chaînes de caractères |   |
|   | `org.apache.felix.jetty.gzip.excludedMethods` |   | séquence de chaînes de caractères |   |
|   | `org.apache.felix.jetty.gzip.includedPaths` |   | séquence de chaînes de caractères |   |
|   | `org.apache.felix.jetty.gzip.excludedPaths` |   | séquence de chaînes de caractères |   |
|   | `org.apache.felix.jetty.gzip.includedMimeTypes` |   | séquence de chaînes de caractères |   |
|   | `org.apache.felix.http.session.invalidate` |   | booléen |   |
|   | `org.apache.felix.http.session.container.attribute` |   | séquence de chaînes de caractères |   |
|   | `org.apache.felix.http.session.uniqueid` |   | booléen |   |
| `org.apache.sling.scripting.cache` | `org.apache.sling.scripting.cache.size` | Oui | entier | >= 2048 |
|   | `org.apache.sling.scripting.cache.additional_extensions` | Oui | séquence de chaînes de caractères | doit inclure « js » |
| `org.apache.sling.engine.impl.log.RequestLogger` | `request.log.output` | Non | chaîne |   |
|   | `request.log.outputtype` | Non | chaîne |   |
|   | `request.log.entry.format` | Non | chaîne |   |
|   | `request.log.exit.format` | Non | chaîne |   |
|   | `request.log.enabled` | Non | chaîne |   |
|   | `access.log.output` | Non | chaîne |   |
|   | `access.log.outputtype` | Non | chaîne |   |
|   | `access.log.enabled` | Non | chaîne |   |
| `org.apache.sling.servlets.resolver.SlingServletResolver` | `servletresolver.servletRoot` | Non | chaîne |   |
|   | `servletresolver.cacheSize` | Non | entier |   |
|   | `servletresolver.paths` | Non | chaîne[] |   |
|   | `servletresolver.defaultExtensions` | Non | chaîne |   |
|   | `servletresolver.mountProviders` | Non | booléen |   |
|   | `servletresolver.scriptUser` | Non | chaîne | obsolète, ne pas utiliser |

## Mise à jour de Java Runtime vers la version 21 {#java-runtime-update-21}

Adobe Experience Manager as a Cloud Service passe à l’exécution Java 21. Pour garantir la compatibilité, il est essentiel de mettre à jour les versions de bibliothèque comme indiqué dans la section [Exigences d’exécution](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).


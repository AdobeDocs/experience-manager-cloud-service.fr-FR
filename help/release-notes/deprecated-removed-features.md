---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
feature: Release Information
role: Admin
source-git-commit: c5057120d68e1119211c7733a8eb0424590096bd
workflow-type: tm+mt
source-wordcount: '2172'
ht-degree: 98%

---

# Fonctionnalités et API obsolètes et supprimées {#deprecated-and-removed-features-apis}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Fonctionnalités obsolètes et supprimées dans AEM as a Cloud Service"
>abstract="AEM as a Cloud Service dispose d’un modèle de déploiement natif dans le cloud. Certaines fonctionnalités ont été remplacées par des homologues natifs du cloud et cet onglet affiche ces fonctionnalités."

Adobe évalue constamment les fonctionnalités du produit pour, au fil du temps, réinventer ou remplacer les fonctionnalités plus anciennes par des solutions plus modernes afin d’améliorer la valeur globale de la clientèle, en prenant toujours en compte la compatibilité ascendante. En outre, comme [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] fournit un modèle de déploiement natif au cloud, certaines capacités et fonctionnalités ont été remplacées par des homologues natives sur le cloud.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’[!DNL Experience Manager], les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Les capacités obsolètes demeurent disponibles, mais ne sont plus améliorées.
1. Les fonctionnalités annoncées comme obsolètes sont supprimées au plus tôt dans la version majeure qui suit. La date cible réelle de la suppression est annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été marquées comme obsolètes dans [!DNL Experience Manager] as a [!DNL Cloud Service]. En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont d’abord définies comme obsolètes, et une alternative est fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Fonctionnalités | Fonctionnalité obsolète | Remplacement |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | Propriétés des fragments d’expérience pour **Statut des médias sociaux**. | La fonctionnalité sera bientôt supprimée. |
| [!DNL Sites] | Fragments de contenu simples basés sur des modèles. | [Fragments de contenu structuré basés sur des modèles](/help/assets/content-fragments/content-fragments-models.md) maintenant. |
| [!DNL Assets] | Workflow `DAM Asset Update` pour traiter les images ingérées. | L’assimilation de ressources utilise maintenant les [microservices de ressources](/help/assets/asset-microservices-overview.md). |
| [!DNL Assets] | Chargez des ressources directement dans [!DNL Experience Manager]. Voir [API de chargement des ressources obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Utilisez le [chargement de binaire direct](/help/assets/add-assets.md). Pour plus d’informations techniques, consultez [API de chargement direct](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Certaines étapes](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) du workflow `DAM Asset Update` ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que [!DNL ImageMagick]. | [Les microservices de ressources](/help/assets/asset-microservices-overview.md) remplacent de nombreux workflows. Pour le traitement personnalisé, utilisez des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | Transcodage FFmpeg des vidéos. | Pour la génération de miniatures FFmpeg, utilisez les [microservices de ressources](/help/assets/asset-microservices-overview.md). Pour le transcodage FFmpeg, utilisez [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | Interface utilisateur de réplication de l’arborescence sous l’onglet Distribuer de l’agent de réplication (suppression après le 30 septembre 2021) | Approches [Gérer la publication](/help/operations/replication.md#manage-publication) ou [Workflow de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) |
| [!DNL Foundation] | Ni l’onglet Distribution de l’écran de l’administrateur ou de l’administratrice de l’agent de réplication, ni l’API de réplication ne peuvent être utilisés pour répliquer les packages de contenu de plus de 10 Mo. Utilisez plutôt l’une des méthodes suivantes : [Gérer la publication](/help/operations/replication.md#manage-publication) ou le [workflow Publier l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow). |
| [!DNL Foundation] | Les intégrations qui utilisent des informations d’identification générées à partir des projets Adobe Developer Console perdront progressivement la prise en charge des informations d’identification du compte de service (JWT). Les informations d’identification du nouveau compte de service (JWT) ne pourront pas être créées dans Adobe Developer Console après le 1er mai 2024 inclus. Cependant, les informations d’identification existantes du compte de service (JWT) pourront toujours être utilisées pour les intégrations déjà configurées jusqu’au 1er janvier 2025. À ce moment-là, les informations d’identification existantes du compte de service (JWT) ne fonctionneront plus. La clientèle devra alors migrer vers les informations OAuth serveur à serveur. [En savoir plus](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console). | [Migrez](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) vers les informations d’identification OAuth serveur à serveur. |

## Fonctionnalités supprimées {#removed-features}

Cette section répertorie les capacités et fonctionnalités qui ont été supprimées d’[!DNL Experience Manager] avec [!DNL Experience Manager] as a [!DNL Cloud Service].

| Domaine | Fonctionnalité | Remplacement | Date de suppression visée |
| ------------ | ------------------ | ----------- | ------------------- |
| Interface utilisateur | L’interface utilisateur Classic est supprimée de l’interface utilisateur du produit. Quelques boîtes de dialogue d’interface utilisateur Classic sont disponibles pour quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations de Cloud Service. Les [mises à jour de produit](/help/release-notes/home.md) à venir peuvent supprimer la disponibilité de l’interface utilisateur Classic. | Interface utilisateur standard | Supprimé |
| [!DNL Dynamic Media] | Les intégrations précédentes avec [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=fr#integration) et le [mode hybride de Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=fr#dynamic) ne sont pas disponibles dans [!DNL Experience Manager] as a [!DNL Cloud Service]. | Utilisez [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) fourni avec [!DNL Experience Manager] as a [!DNL Cloud Service]. | Supprimé |
| [!DNL Sites] | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans [!DNL Experience Manager] 6.4 et ont été supprimées d’[!DNL Experience Manager]. | Supprimé |
| [!DNL Sites] | Importateur de conception | Cette fonctionnalité a été supprimée, car les sections non modifiables du référentiel de [!DNL Experience Manager] ne sont pas accessibles au moment de l’exécution. | Supprimé |
| [!DNL Assets] | Le partage d’[!DNL Assets] avec le service principal Experience Cloud Assets et les services Creative Cloud n’est pas disponible. | Pour l’intégration à [!DNL Adobe Creative Cloud], utilisez [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html). | Supprimé |
| [!DNL Foundation] | Prise en charge des sources de données Apache Sling (offre spéciale OSGi org.apache.sling.datasource) | S/O | Supprimé |
| [!DNL Foundation] | Prise en charge des modèles de script JST (offre spéciale OSGi org.apache.sling.scripting.jst) | S/O | Supprimé |
| [!DNL Foundation] | Prise en charge d’Apache Felix Http Whiteboard | OSGi Http Whiteboard | Mars 2022 |
| [!DNL Foundation] | Prise en charge de com.adobe.granite.oauth.server | Intégration Adobe IMS | Mars 2023 |
| [!DNL Foundation] | Prise en charge de la fonctionnalité org.apache.sling.serviceusermapping pour [obtenir l’ID d’utilisateur ou d’utilisatrice du service](https://sling.apache.org/apidocs/sling12/org/apache/sling/serviceusermapping/ServiceUserMapper.html#getServiceUserID-org.osgi.framework.Bundle-java.lang.String-) | S/O | 30/08/24 |


## API d’AEM {#aem-apis}

Vous trouverez ci-dessous la liste exhaustive des API d’AEM obsolètes et leur date de suppression prévue. Il est attendu des clients qu’ils suppriment de leur code les API d’ici la date de suppression cible. Toute utilisation de l’API après la date de suppression générera des erreurs dans l’environnement de développement/SDK local et le processus de création Cloud Manager.

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
    <td>Utiliser les interfaces Auth Core / Auth Core SPI de Sling comme alternative</td>
    <td>2015</td>
    <td>30/07/2021</td>
  </tr>
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>30/07/2021</td>
  </tr>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>Utiliser l’API Discovery de Sling comme alternative</td>
    <td>2015</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
    <td>01/03/2021</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
    <td>05/03/2021</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>L’implémentation Apache Johnzon de <a href="https://johnzon.apache.org/index.html">javax.json</a> est recommandée et devrait être utilisée. </td>
    <td>30/04/2021</td>
    <td>31/12/2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Les gestionnaires de persistance personnalisée ne sont pas pris en charge dans AEM as a Cloud Service.</td>
    <td>30/04/2021</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2 est en mode de maintenance. Commons Lang 3 devrait être utilisé à la place.</td>
    <td>30/04/2021</td>
    <td>31/12/2021</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Commons Collections 3 est en mode de maintenance. Commons Collections 4 devrait être utilisé à la place.</td>
    <td>30/04/2021</td>
    <td>31/12/2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Il est recommandé d’utiliser l’API Apache Felix HealthCheck à la place</td>
    <td>30/04/2021</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n</td>
    <td>La console web Felix n’est pas prise en charge dans les environnements cloud</td>
    <td>30/04/2021</td>
    <td>30/07/2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml<br>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.client.util</td>
    <td>Les packages Eclipse Jetty et Felix Http Jetty ne sont plus pris en charge.</td>
    <td>27/05/2021</td>
    <td>26/08/2021</td>
  </tr>
  <tr>
    <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>L’utilisation de cette API n’est pas prise en charge dans AEM as a Cloud Service.</td>
    <td>27/05/2021</td>
    <td>30/07/2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info<br>org.apache.felix.scr.component</td>
    <td>Le métatype Apache Felix et les API SCR sont obsolètes.  Utilisez le métatype OSGi et les API Declarative Service à la place.</td>
    <td>27/05/2021</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.slf4j.impl</td>
    <td>Les classes de mise en œuvre du journal ne sont pas compatibles avec AEM as a Cloud Service.</td>
    <td>04/07/2021</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.apache.abdera<br>org.apache.abdera.model<br>org.apache.abdera.factory<br>org.apache.abdera.ext.media<br>org.apache.abdera.util<br>org.apache.abdera.i18n.iri<br>org.apache.abdera.writer<br>org.apache.abdera.i18n.rfc4646<br>org.apache.abdera.i18n.rfc4646.enums<br>org.apache.abdera.i18n.text<br>org.apache.abdera.filter<br>org.apache.abdera.xpath<br>org.apache.abdera.i18n.text.io<br>org.apache.abdera.i18n.text.data<br>org.apache.abdera.parser</td>
    <td>Cette API est obsolète, car le projet Apache Abdera a été supprimé en 2017.</td>
    <td>29/07/2021</td>
    <td>29/09/2021</td>
  </tr>
  <tr>
    <td>org.apache.abdera.ext.opensearch<br>org.apache.abdera.ext.opensearch.model<br>org.apache.abdera.ext.opensearch.server<br>org.apache.abdera.ext.opensearch.server.impl<br>org.apache.abdera.ext.opensearch.server.processors<br>org.apache.abdera.i18n.iri.data<br>org.apache.abdera.i18n.lang<br>org.apache.abdera.i18n.templates<br>org.apache.abdera.i18n.unicode.data<br>org.apache.abdera.parser.stax<br>org.apache.abdera.parser.stax.util<br>org.apache.abdera.protocol<br>org.apache.abdera.protocol.client<br>org.apache.abdera.protocol.client.cache<br>org.apache.abdera.protocol.client.util<br>org.apache.abdera.protocol.error<br>org.apache.abdera.protocol.server<br>org.apache.abdera.protocol.server.context<br>org.apache.abdera.protocol.server.filters<br>org.apache.abdera.protocol.server.impl<br>org.apache.abdera.protocol.server.multipart<br>org.apache.abdera.protocol.server.processors<br>org.apache.abdera.protocol.server.provider.basic<br>org.apache.abdera.protocol.server.provider.managed<br>org.apache.abdera.protocol.server.servlet<br>org.apache.abdera.protocol.util<br>org.apache.abdera.util.filter</td>
    <td>Cette API est obsolète, car le projet Apache Abdera a été supprimé en 2017.</td>
    <td>08/04/2019</td>
    <td>29/09/2021</td>
  </tr>
  <tr>
    <td>org.apache.sling.startupfilter<br>com.adobe.granite.crypto.spi<br>com.adobe.granite.crpyto.spi.base<br>com.adobe.agl.impl.data.icudt40b<br>com.adobe.agl.impl.data.icudt40b.brkitr<br>com.adobe.agl.impl.data.icudt40b.coll<br>com.adobe.agl.impl.data.icudt40b.rbnf<br>com.<br>adobe.agl.impl.data.icudt40b.translit<br>com.adobe.internal.pdf.tika<br>com.adobe.internal.pdftoolkit.color<br>com.adobe.internal.pdftoolkit.core.encryption<br>com.adobe.internal.pdftoolkit.core.encryption.impl<br>com.adobe.internal.pdftoolkit.core.traverser<br>com.adobe.internal.pdftoolkit.graphicsDOM<br>com.adobe.internal.pdftoolkit.graphicsDOM.shading<br>com.adobe.internal.pdftoolkit.graphicsDOM.utils<br>com.adobe.internal.pdftoolkit.image<br>com.adobe.internal.pdftoolkit.pdf.content<br>com.adobe.internal.pdftoolkit.pdf.content.processor<br>com.adobe.internal.pdftoolkit.pdf.content.processor.base14fontwidths<br>com.adobe.internal.pdftoolkit.pdf.contentmodify<br>com.adobe.internal.pdftoolkit.pdf.contentmodify.impl<br>com.adobe.internal.pdftoolkit.pdf.digsig<br>com.adobe.internal.pdftoolkit.pdf.document<br>com.adobe.internal.pdftoolkit.pdf.document.listener<br>com.adobe.internal.pdftoolkit.pdf.document.permissionhandlers<br>com.adobe.internal.pdftoolkit.pdf.filters<br>com.adobe.internal.pdftoolkit.pdf.graphics<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces.cmykresources<br>com.adobe.internal.pdftoolkit.pdf.graphics.font<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.encodings<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.optionalcontent<br>com.adobe.internal.pdftoolkit.pdf.graphics.patterns<br>com.adobe.internal.pdftoolkit.pdf.graphics.shading<br>com.adobe.internal.pdftoolkit.pdf.graphics.xobject<br>com.adobe.internal.pdftoolkit.pdf.impl<br>com.adobe.internal.pdftoolkit.pdf.inlineimage<br>com.adobe.internal.pdftoolkit.pdf.interactive<br>com.adobe.internal.pdftoolkit.pdf.interactive.action<br>com.adobe.internal.pdftoolkit.pdf.interactive.annotation<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms.impl<br>com.adobe.internal.pdftoolkit.pdf.interactive.geospatial<br>com.adobe.internal.pdftoolkit.pdf.interactive.markedcontent<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation.collection<br>com.adobe.internal.pdftoolkit.pdf.interactive.readerrequirements<br>com.adobe.internal.pdftoolkit.pdf.interactive.requirement<br>com.adobe.internal.pdftoolkit.pdf.interchange<br>com.adobe.internal.pdftoolkit.pdf.interchange.documentparts<br>com.adobe.internal.pdftoolkit.pdf.interchange.metadata<br>com.adobe.internal.pdftoolkit.pdf.interchange.prepress<br>com.adobe.internal.pdftoolkit.pdf.interchange.structure<br>com.adobe.internal.pdftoolkit.pdf.multimedia<br>com.adobe.internal.pdftoolkit.pdf.page<br>com.adobe.internal.pdftoolkit.pdf.rendering<br>com.adobe.internal.pdftoolkit.pdf.transparency<br>com.adobe.internal.pdftoolkit.pdf.utils<br>com.adobe.internal.pdftoolkit.services.Jpeg2000<br>com.adobe.internal.pdftoolkit.services.fontresources<br>com.adobe.internal.pdftoolkit.services.fontresources.subsetting<br>com.adobe.internal.pdftoolkit.services.interchange.structure<br>com.adobe.internal.pdftoolkit.services.optionalcontent<br>com.adobe.internal.pdftoolkit.services.optionalcontent.impl<br>com.adobe.internal.pdftoolkit.services.pdfParser<br>com.adobe.internal.pdftoolkit.services.permissions<br>com.adobe.internal.pdftoolkit.services.rasterizer<br>com.adobe.internal.pdftoolkit.services.readingorder<br>com.adobe.internal.pdftoolkit.services.security<br>com.adobe.internal.pdftoolkit.services.swf<br>com.adobe.internal.pdftoolkit.services.textextraction<br>com.adobe.internal.pdftoolkit.services.textextraction.impl<br>com.adobe.internal.pdftoolkit.services.xmp<br>com.adobe.internal.util.base64<br>com.adobe.internal.xmp.utils<br>com.day.crx.core.cluster<br>com.day.crx.packaging<br>com.day.crx.packaging.gfx<br>com.day.crx.query<br>com.day.crx.sling.server.jmx<br>com.day.durbo<br>com.day.durbo.io<br>com.day.imageio.plugins<br>org.apache.aries.jmx.codec<br>org.h2.mvstore<br>org.h2.mvstore.rtree<br>org.h2.mvstore.type<br>org.openxmlformats.schemas.drawingml.x2006.chart.impl<br>org.openxmlformats.schemas.drawingml.x2006.main.impl<br>org.openxmlformats.schemas.drawingml.x2006.picture.impl<br>org.openxmlformats.schemas.drawingml.x2006.spreadsheetDrawing.impl<br>org.openxmlformats.schemas.drawingml.x2006.wordprocessingDrawing.impl<br>org.openxmlformats.schemas.officeDocument.x2006.customProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.docPropsVTypes.impl<br>org.openxmlformats.schemas.officeDocument.x2006.extendedProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.relationships.impl<br>org.openxmlformats.schemas.presentationml.x2006.main.impl<br>org.openxmlformats.schemas.spreadsheetml.x2006.main.impl<br>org.openxmlformats.schemas.wordprocessingml.x2006.main.impl<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes.impl<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature.impl<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties.impl<br>org.openxmlformats.schemas.xpackage.x2006.relationships<br>org.openxmlformats.schemas.xpackage.x2006.relationships.impl<br>com.adobe.internal.afml<br>com.adobe.internal.agm<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es2<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es3<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.compoundtype<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.editablepdf<br>com.adobe.internal.pdftoolkit.services.ap<br>com.adobe.internal.pdftoolkit.services.ap.annot<br>com.adobe.internal.pdftoolkit.services.ap.extension<br>com.adobe.internal.pdftoolkit.services.ap.impl<br>com.adobe.internal.pdftoolkit.services.ap.spi<br>com.adobe.internal.pdftoolkit.services.digsig<br>com.adobe.internal.pdftoolkit.services.digsig.cryptoprovider<br>com.adobe.internal.pdftoolkit.services.digsig.docmodanalysis<br>com.adobe.internal.pdftoolkit.services.digsig.spi<br>com.adobe.internal.pdftoolkit.services.fdf<br>com.adobe.internal.pdftoolkit.services.formflattener<br>com.adobe.internal.pdftoolkit.services.forms<br>com.adobe.internal.pdftoolkit.services.imageconversion<br>com.adobe.internal.pdftoolkit.services.javascript<br>com.adobe.internal.pdftoolkit.services.javascript.extension<br>com.adobe.internal.pdftoolkit.services.manipulations<br>com.adobe.internal.pdftoolkit.services.manipulations.impl<br>com.adobe.internal.pdftoolkit.services.optimizer<br>com.adobe.internal.pdftoolkit.services.pdfa<br>com.adobe.internal.pdftoolkit.services.pdfa.error<br>com.adobe.internal.pdftoolkit.services.pdfa2<br>com.adobe.internal.pdftoolkit.services.pdfa2.error<br>com.adobe.internal.pdftoolkit.services.pdfa2.error.codes<br>com.adobe.internal.pdftoolkit.services.pdfa3<br>com.adobe.internal.pdftoolkit.services.pdfport<br>com.adobe.internal.pdftoolkit.services.portfolio<br>com.adobe.internal.pdftoolkit.services.rcg<br>com.adobe.internal.pdftoolkit.services.rcg.impl<br>com.adobe.internal.pdftoolkit.services.redaction<br>com.adobe.internal.pdftoolkit.services.redaction.handler<br>com.adobe.internal.pdftoolkit.services.sanitization<br>com.adobe.internal.pdftoolkit.services.xbm<br>com.adobe.internal.pdftoolkit.services.xdp<br>com.adobe.internal.pdftoolkit.services.xfa<br>com.adobe.internal.pdftoolkit.services.xfa.form<br>com.adobe.internal.pdftoolkit.services.xfatext<br>com.adobe.internal.pdftoolkit.services.xfdf<br>com.adobe.internal.pdftoolkit.services.xobjhandler<br>com.adobe.internal.pdftoolkit.xml<br>com.adobe.octopus.extract<br>opennlp.tools.doccat<br>opennlp.tools.entitylinker<br>opennlp.tools.formats<br>opennlp.tools.formats.ad<br>opennlp.tools.formats.brat<br>opennlp.tools.formats.convert<br>opennlp.tools.formats.frenchtreebank<br>opennlp.tools.formats.muc<br>opennlp.tools.formats.ontonotes<br>opennlp.tools.lemmatizer<br>opennlp.tools.parser<br>opennlp.tools.parser.chunking<br>opennlp.tools.parser.lang.en<br>opennlp.tools.parser.lang.es<br>opennlp.tools.parser.treeinsert<br>opennlp.tools.sentdetect<br>opennlp.tools.sentdetect.lang<br>opennlp.tools.sentdetect.lang.th<br>opennlp.tools.stemmer<br>opennlp.tools.stemmer.snowball<br>opennlp.tools.tokenize.lang.en<br>org.apache.commons.imaging.color<br>org.apache.commons.imaging.common<br>org.apache.commons.imaging.common.itu_t4<br>org.apache.commons.imaging.common.mylzw<br>org.apache.commons.imaging.formats.bmp<br>org.apache.commons.imaging.formats.dcx<br>org.apache.commons.imaging.formats.gif<br>org.apache.commons.imaging.formats.icns<br>org.apache.commons.imaging.formats.ico<br>org.apache.commons.imaging.formats.jpeg<br>org.apache.commons.imaging.formats.jpeg.decoder<br>org.apache.commons.imaging.formats.jpeg.exif<br>org.apache.commons.imaging.formats.jpeg.iptc<br>org.apache.commons.imaging.formats.jpeg.segments<br>org.apache.commons.imaging.formats.jpeg.xmp<br>org.apache.commons.imaging.formats.pcx<br>org.apache.commons.imaging.formats.png<br>org.apache.commons.imaging.formats.png.chunks<br>org.apache.commons.imaging.formats.png.scanlinefilters<br>org.apache.commons.imaging.formats.png.transparencyfilters<br>org.apache.commons.imaging.formats.pnm<br>org.apache.commons.imaging.formats.psd<br>org.apache.commons.imaging.formats.psd.dataparsers<br>org.apache.commons.imaging.formats.psd.datareaders<br>org.apache.commons.imaging.formats.rgbe<br>org.apache.commons.imaging.formats.tiff<br>org.apache.commons.imaging.formats.tiff.constants<br>org.apache.commons.imaging.formats.tiff.datareaders<br>org.apache.commons.imaging.formats.tiff.fieldtypes<br>org.apache.commons.imaging.formats.tiff.photometricinterpreters<br>org.apache.commons.imaging.formats.tiff.taginfos<br>org.apache.commons.imaging.formats.tiff.write<br>org.apache.commons.imaging.formats.wbmp<br>org.apache.commons.imaging.formats.xbm<br>org.apache.commons.imaging.formats.xpm<br>org.apache.commons.imaging.icc<br>org.apache.commons.imaging.palette<br>org.apache.commons.imaging.util<br>com.adobe.dam.print.ids.utils<br>com.day.cq.dam.api.reporting<br>com.day.cq.dam.entitlement.api<br>com.day.cq.dam.handler.standard.epub<br>com.day.cq.dam.handler.standard.keynote<br>com.day.cq.dam.handler.standard.mp3<br>com.day.cq.dam.handler.standard.msoffice<br>com.day.cq.dam.handler.standard.msoffice.wmf<br>com.day.cq.dam.handler.standard.ooxml<br>com.day.cq.dam.handler.standard.pdf<br>com.day.cq.dam.handler.standard.pict<br>com.day.cq.dam.handler.standard.ps<br>com.day.cq.dam.handler.standard.psd<br>com.day.cq.dam.handler.standard.zip<br>com.day.cq.dam.word.extraction<br>com.day.cq.dam.word.process<br>com.adobe.xmp.worker.files<br>com.adobe.cq.address.api<br>com.adobe.cq.address.api.location<br>com.day.cq.mcm.emailprovider.impl.types<br>com.day.io<br>com.day.io.disk<br>com.day.io.file<br>org.apache.commons.exec.environment<br>org.apache.commons.exec.launcher<br>org.apache.commons.exec.util<br>com.google.zxing<br>com.google.zxing.common<br>com.google.zxing.common.reedsolomon<br>com.google.zxing.qrcode.decoder<br>com.google.zxing.qrcode.encoder<br>com.adobe.cq.dam.dm.internalapi.image_server<br>com.day.cq.dam.api.s7dam.jobs<br>com.day.cq.dam.api.s7dam.omnisearch<br>com.day.cq.dam.api.s7dam.scene7<br>com.day.cq.dam.scene7<br>com.day.cq.dam.scene7.api.net<br>com.day.cq.analytics.sitecatalyst.rsmerger<br>com.day.cq.searchpromote<br>com.day.cq.searchpromote.xml<br>com.day.cq.searchpromote.xml.form<br>com.day.cq.searchpromote.xml.result&gt;</td>
    <td>API héritée d’AEM 6.x.</td>
    <td>08/04/2019</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.apache.sling.discovery.commons<br>org.apache.sling.discovery.commons.providers<br>org.apache.sling.discovery.commons.providers.base<br>org.apache.sling.discovery.commons.providers.spi<br>org.apache.sling.discovery.commons.providers.spi.base<br>org.apache.sling.discovery.commons.providers.util</td>
    <td>Cette API nʼest pas prise en charge dans Cloud Service.</td>
    <td>30/09/2021</td>
    <td>supprimée</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml<br>org.apache.jackrabbit.vault.util.xml.serialize</td>
    <td>Les classes util liées à Apache Xerces sont supprimées dans les versions ultérieures, ce qui entraîne un changement de version majeur. Comme ces utils sont destinés à un usage interne à Filevault, lʼAPI est dépréciée de lʼinterface de lʼAPI publique.</td>
    <td>01/09/2021</td>
    <td>supprimée</td>
  <tr>
    <td>org.apache.sling.atom.taglib<br>org.apache.sling.atom.taglib.media</td>
    <td>API héritée d’AEM 6.x.</td>
    <td>08/04/2019</td>
    <td>29/09/2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.whiteboard</td>
    <td>Le tableau blanc HTTP Apache Felix nʼest plus pris en charge. Migrez votre code vers le tableau blanc HTTP OSGI.</td>
    <td>27/01/2022</td>
    <td>24/03/2022</td>
  </tr>
  <tr>
    <td>org.apache.cocoon.xml.dom<br>org.apache.cocoon.xml.sax</td>
    <td>Cette API est obsolète, migrez votre code vers les API XML fournies par le JDK.</td>
    <td>27/01/2022</td>
    <td>24/03/2022</td>
  </tr>
  <tr>
    <td>ch.qos.logback.classic<br>ch.qos.logback.classic.boolex<br>ch.qos.logback.classic.db.names<br>ch.qos.logback.classic.db.script<br>ch.qos.logback.classic.encoder<br>ch.qos.logback.classic.filter<br>ch.qos.logback.classic.helpers<br>ch.qos.logback.classic.html<br>ch.qos.logback.classic.jmx<br>ch.qos.logback.classic.joran<br>ch.qos.logback.classic.joran.action<br>ch.qos.logback.classic.jul<br>ch.qos.logback.classic.layout<br>ch.qos.logback.classic.log4j<br>ch.qos.logback.classic.net<br>ch.qos.logback.classic.net.server<br>ch.qos.logback.classic.pattern<br>ch.qos.logback.classic.pattern.color<br>ch.qos.logback.classic.selector<br>ch.qos.logback.classic.selector.servlet<br>ch.qos.logback.classic.servlet<br>ch.qos.logback.classic.sift<br>ch.qos.logback.classic.spi<br>ch.qos.logback.classic.turbo<br>ch.qos.logback.classic.util<br>ch.qos.logback.core<br>ch.qos.logback.core.boolex<br>ch.qos.logback.core.encoder<br>ch.qos.logback.core.filter<br>ch.qos.logback.core.helpers<br>ch.qos.logback.core.hook<br>ch.qos.logback.core.html<br>ch.qos.logback.core.joran<br>ch.qos.logback.core.joran.action<br>ch.qos.logback.core.joran.conditional<br>ch.qos.logback.core.joran.event<br>ch.qos.logback.core.joran.event.stax<br>ch.qos.logback.core.joran.node<br>ch.qos.logback.core.joran.spi<br>ch.qos.logback.core.joran.util<br>ch.qos.logback.core.joran.util.beans<br>ch.qos.logback.core.layout<br>ch.qos.logback.core.net<br>ch.qos.logback.core.net.server<br>ch.qos.logback.core.net.ssl<br>ch.qos.logback.core.pattern<br>ch.qos.logback.core.pattern.color<br>ch.qos.logback.core.pattern.parser<br>ch.qos.logback.core.pattern.util<br>ch.qos.logback.core.property<br>ch.qos.logback.core.read<br>ch.qos.logback.core.recovery<br>ch.qos.logback.core.rolling<br>ch.qos.logback.core.rolling.helper<br>ch.qos.logback.core.sift<br>ch.qos.logback.core.spi<br>ch.qos.logback.core.status<br>ch.qos.logback.core.subst<br>ch.qos.logback.core.util</td>
    <td>Cette API interne Logback nʼest pas prise en charge par AEM as a Cloud Service.</td>
    <td>27/01/2022</td>
    <td>24/03/2022</td>
  </tr>
  <tr>
    <td>org.slf4j.spi</td>
    <td>Cette API interne Log4j nʼest pas prise en charge par AEM as a Cloud Service.</td>
    <td>27/01/2022</td>
    <td>24/03/2022</td>
  </tr>
  <tr>
    <td>org.apache.log4j<br>org.apache.log4j.helpers<br>org.apache.log4j.spi<br>org.apache.log4j.xml</td>
    <td>Apache Log4j 1 a atteint sa fin de vie en 2015 et n’est plus pris en charge.</td>
    <td>27/01/2022</td>
    <td>24/03/2022</td>
  </tr>
  <tr>
    <td>org.apache.sling.commons.log.logback<br>org.apache.sling.commons.log.logback.webconsole</td>
    <td>Cette API interne Logback nʼest pas prise en charge par AEM as a Cloud Service.</td>
    <td>27/01/2022</td>
    <td>supprimé</td>
  </tr>
  <tr>
    <td>com.github.jknack.handlebars.js</td>
    <td>Mise à niveau de Handlebars requise de la version 4.0.5 à la version 4.3.0 en raison d’une vulnérabilité de sécurité. Ce package n’est plus présent dans les mises à niveau de Handlebars.</td>
    <td>05/05/2022</td>
    <td>05/08/2022</td>
  </tr>
  <tr>
    <td>com.adobe.granite.resourceresolverhelper</td>
    <td>Cette API n’est plus prise en charge. Utilisez org.apache.sling.api.resource.ResourceResolverFactory à la place.</td>
    <td>29/09/2022</td>
    <td>24/11/2022</td>
  </tr>
  <tr>
    <td>com.day.cq.contentsync.handler.util</td>
    <td>Cette API est obsolète. Utilisez les créateurs de ressources d’Apache Sling à la place.</td>
    <td>31/10/2022</td>
    <td>01/01/2023</td>
  </tr>
  <tr><td>org.apache.sling.commons.json<br>org.apache.sling.commons.json.http<br>org.apache.sling.commons.json.io<br>org.apache.sling.commons.json.jcr<br>org.apache.sling.commons.json.sling<br>org.apache.sling.commons.json.util<br>org.apache.sling.commons.json.xml</td>
    <td>Cette API nʼest pas prise en charge par AEM as a Cloud Service.</td>
    <td>15/05/2023</td>
    <td>15/06/2023</td>
  </tr><td>com.google.common.annotations<br>com.google.common.base<br>com.google.common.cache<br>com.google.common.collect<br>com.google.common.escape<br>com.google.common.eventbus<br>com.google.common.hash<br>com.google.common.html<br>com.google.common.io<br>com.google.common.math<br>com.google.common.net<br>com.google.common.primitives<br>com.google.common.reflect<br>com.google.common.util.concurrent<br>com.google.common.xml</td>
    <td>Les bibliothèques principales de Google Guava sont obsolètes.</td>
    <td>15/05/2023</td>
    <td>15/06/2023</td>
  </tr>
  <tr>
    <td>org.slf4j.event	</td>
    <td>Cette API interne slf4j nʼest pas prise en charge par AEM as a Cloud Service.</td>
    <td>11/04/2022</td>
    <td>30/08/2024</td>
  </tr>
    <td>org.apache.sling.repoinit.jcr<br>org.apache.sling.repoinit.parser.operations</td>
    <td>L’utilisation de cette API n’est pas prise en charge dans AEM as a Cloud Service.</td>
    <td>17/05/2024</td>
    <td>30/06/2024</td>
  </tr>  
</tbody>
</table>
</details>

## Configuration OSGI {#osgi-configuration}

Les deux listes ci-dessous représentent la surface de configuration OSGi d’AEM as a Cloud Service, décrivant ce que les clients peuvent configurer.

1. Liste des configurations OSGi qui ne doivent pas être configurées par le code client
1. Liste des configurations OSGi dont les propriétés peuvent être configurées, mais doivent respecter les règles de validation indiquées. Ces règles indiquent si la déclaration de la propriété est requise, son type et, dans certains cas, sa plage de valeurs autorisée.

Si une configuration OSGI n’est pas répertoriée, elle peut être configurée par code client.

Ces règles sont validées pendant le processus de création de Cloud Manager. D’autres règles peuvent être ajoutées au fil du temps et la date prévue d’application est indiquée dans le tableau. Les clients doivent respecter ces règles avant la date d’application de la cible. Le fait de ne pas respecter les règles après la date de suppression génère des erreurs dans le processus de création de Cloud Manager. Les projets Maven doivent inclure le [module externe Maven Analyseur de build de SDK d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr) pour signaler les erreurs de configuration OSGI lors du développement du SDK local.

Vous trouverez des informations supplémentaires sur la configuration OSGI à [cet emplacement](/help/implementing/deploying/configuring-osgi.md).

+++Configurations OSGi qui ne peuvent pas être modifiées.
* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`org.apache.felix.http (Factory)`** (Date d’annonce : 30/04/2021, Date d’application : 31/07/2021)
* **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** (Date d’annonce : 25/08/2021, Date d’application : 26/11/2021)
+++

+++Configurations OSGi soumises aux règles de validation de version.
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
   * Obligatoire
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
      * Obligatoire
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
+++


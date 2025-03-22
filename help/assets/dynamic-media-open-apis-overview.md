---
title: Dynamic Media avec fonctionnalités OpenAPI
description: Découvrez les concepts clés, tels que les raisons d’utiliser Dynamic Media avec fonctionnalités OpenAPI et comment l’activer.
role: User
exl-id: 658b6eff-9f5a-4166-9ff6-5dc8eb92ada3
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 97%

---

# Dynamic Media avec fonctionnalités OpenAPI {#new-dynaminc-media-apis-overview}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>Le guide de Dynamic Media avec fonctionnalités OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Dynamic Media avec fonctionnalités OpenAPI]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Dans le monde numérique actuel, qui évolue rapidement, vous devez être en mesure d’exploiter tout le potentiel des ressources numériques de votre marque afin de garder une longueur d’avance sur la concurrence. La solution de gestion des ressources numériques (Digital Assets Management, DAM) globale facilite la gouvernance des ressources, favorise la cohérence de la marque et accélère la diffusion du contenu tout en assurant l’intégrité de la marque et des expériences client hors pair.

Dynamic Media avec fonctionnalités OpenAPI place la gestion des ressources numériques au cœur d’un écosystème de chaîne d’approvisionnement de contenu agile et efficace pour assurer la gouvernance et la diffusion des ressources.

## Pourquoi utiliser Dynamic Media avec fonctionnalités OpenAPI ? {#dynamic-media-open-api-features}

Dynamic Media avec fonctionnalités OpenAPI offre les avantages clés suivants :

* **Intégrations fluides** : Dynamic Media avec fonctionnalités OpenAPI offre un ensemble complet d’API de recherche et de diffusion. Cela permet à votre équipe de développement d’[ intégrer facilement la diffusion des ressources à leurs applications ](/help/assets/integrate-dynamic-media-open-apis.md). Les applications comprennent les applications d’Adobe et tierces. Il fournit une [interface de sélecteur de ressources micro frontend](/help/assets/overview-asset-selector.md) pour rechercher et sélectionner des ressources approuvées. Vous pouvez facilement intégrer le sélecteur à n’importe quelle application basée sur des frameworks JavaScript telles que React JS, Angular JS et Vanilla JS.

* **Gestion centralisée des ressources numériques** : la DAM est la source unique de vérité pour toutes les ressources numériques. Vos ressources numériques sont gérées de manière centralisée dans AEM Assets et diffusées vers les applications consommatrices par référence à l’aide d’URL de diffusion, sans copier de fichiers binaires de ressources.

* **Mises à jour en temps réel** : toute modification apportée aux ressources approuvées dans DAM y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une durée de vie (Time To Live, TTL) de 10 minutes configurée pour Dynamic Media avec fonctionnalités OpenAPI via CDN, les mises à jour deviennent visibles dans toutes les interfaces de création et de publication en moins de 10 minutes.

* **Cohérence de la marque** : seules les [ressources approuvées par la marque](/help/assets/approve-assets.md) sont exposées aux applications en aval. [Les responsables de marques et du marketing maintiennent un contrôle strict sur les ressources de la marque](/help/assets/restrict-assets-delivery.md). Seule la version approuvée et la plus récente de la ressource peut être utilisée, ce qui garantit la cohérence de la marque sur tous les canaux et applications.

* **Diffusion optimisée pour le web** : les ressources numériques sont diffusées dans des formats optimisés pour le web afin d’améliorer les principales valeurs web de vos expériences numériques. Cela inclut la prise en charge des rendus WebP pour les images, le streaming adaptatif via les protocoles HLS ou DASH pour les vidéos et les rendus originaux pour les documents.

* **Transformation de ressources dynamique** : notre système permet la transformation d’images à la volée à l’aide de paramètres d’URL connus sous le nom de modificateurs d’image. [Par exemple, largeur, hauteur, rotation, symétrie, qualité, recadrage, format et recadrage intelligent](/help/assets/deliver-assets-apis.md). Les rendus transformés sont générés dynamiquement et distribués de manière transparente via le réseau de diffusion de contenu.

* **Diffusion sécurisée des ressources** : Dynamic Media avec fonctionnalités OpenAPI fournit un mécanisme de contrôle d’accès à vos ressources numériques. Vous pouvez spécifier des rôles ou des groupes d’utilisateurs et utilisatrices comme métadonnées pour les ressources à sécuriser et définir un délai durant lequel [seuls les utilisateurs et utilisatrices autorisés peuvent accéder à ces ressources](/help/assets/restrict-assets-delivery.md). Les URL de diffusion des ressources sécurisées ne sont pas résolues pour les utilisateurs et les utilisatrices non autorisés au cours de la période limitée.

* **Informations sur les données pour prendre des décisions éclairées (à venir)** : au-delà de la gestion et de la diffusion des ressources, il capture les informations sur les données de diffusion dans les diffusions de ressources sur le CDN, ce qui permet aux responsables de marque de suivre les mesures de diffusion sur l’ensemble des canaux. Cela leur permet de prendre des décisions à partir des données pour optimiser continuellement la gouvernance des ressources et les stratégies de diffusion.

![ Diagramme de flux de données Dynamic Media OpenAPI](assets/dm-openapi-dfd.png)

## Conditions préalables pour accéder à Dynamic Media avec fonctionnalités OpenAPI {#prerequisites-dynaminc-media-open-apis}

Pour accéder à Dynamic Media avec fonctionnalités OpenAPI, vous devez disposer de licences pour :

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## Comment activer Dynamic Media avec fonctionnalités OpenAPI ? {#enable-dynamic-media-open-apis}

Avant d’envoyer une demande d’activation de Dynamic Media avec fonctionnalités OpenAPI sur AEM as a Cloud Service, vérifiez qu’il n’est pas déjà activé.

Une fois que les [conditions préalables](#prerequisites-dynaminc-media-open-apis) sont remplies et que Dynamic Media avec fonctionnalités OpenAPI est activé sur votre instance AEM as a Cloud Service, une URL de diffusion est disponible pour chaque ressource approuvée dans le référentiel. Pour plus d’informations sur la copie de l’URL de diffusion, voir [Copie de l’URL de diffusion pour les ressources approuvées](approve-assets.md#copy-delivery-url-approved-assets). Adobe recommande d’utiliser cette méthode pour vérifier que Dynamic Media avec fonctionnalités OpenAPIsont est activé sur AEM as a Cloud Service avant d’envoyer un ticket d’assistance.

Pour activer Dynamic Media avec fonctionnalités OpenAPI sur AEM as a Cloud Service, envoyez un ticket d’assistance Adobe contenant les informations suivantes :

* ID de programme et d’environnement Cloud Services

* Détails sur le cas d’utilisation à résoudre avec l’intégration de Dynamic Media avec fonctionnalités OpenAPI.

* Informations sur les applications en aval à intégrer à Dynamic Media avec fonctionnalités OpenAPI.

  >[!NOTE]
  >
  Pour l’intégrer à une application autre qu’Adobe, indiquez les noms de domaine à la liste autorisée où l’application est hébergée.

* Informations sur les principaux contacts clients impliqués dans le projet d’intégration.

* Liste des membres clés de l’équipe Adobe en charge des comptes (adresse e-mail).

Une fois que vous avez envoyé le ticket d’assistance, Adobe active Dynamic Media avec fonctionnalités OpenAPI dans votre environnement Cloud Services et partage les détails, tels que l’ID du client IMS, pour que vous puissiez poursuivre l’intégration.

>[!NOTE]
>
Excluez `/conf/global/settings/dam/assets-configurations/assetdelivery` de tous les modules de contenu, afin d’éviter la désactivation de Dynamic Media avec fonctionnalités OpenAPI.

## En savoir plus sur les principales fonctionnalités {#learn-more-key-capabilities}

<table>
<td>
   <a href="/help/assets/approve-assets.md">
   <img alt="Approuver des ressources dans Experience Manager Assets" src="./assets/approved-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/approve-assets.md">
 <strong>Approuver des ressources dans Experience Manager Assets</strong>
 </a>
   </div>
   <p>
      <em>Approuvez des ressources dans AEM Assets pour optimiser la gestion des ressources, en garantissant un processus contrôlé et efficace pour gérer les ressources.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="Intégrer AEM Assets à des applications en aval" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
 <strong>Intégrer AEM Assets à des applications en aval</strong>
 </a>
   </div>
   <p>
      <em>Intégrez votre propre interface d’utilisation personnalisée au référentiel Experience Manager Assets à l’aide des API de recherche et de diffusion ou utilisez le sélecteur de ressources micro front-end d’Adobe.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="Sélecteur de ressource d’Adobe" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
 <strong>Sélecteur de ressources micro front-end d’Adobe</strong>
 </a>
   </div>
   <p>
      <em>Interface d’utilisation qui interagit avec le référentiel AEM Assets pour rechercher des ressources, puis les utiliser dans votre expérience de création d’applications.</em>
   </p>
</td>
</table>
<table>



<table>
<td>
   <a href="/help/assets/search-assets-api.md">
   <img alt="Rechercher des ressources dans le référentiel Experience Manager Assets" src="./assets/search-assets-api-overview.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-api.md">
 <strong>Rechercher des ressources dans le référentiel Experience Manager Assets</strong>
 </a>
   </div>
   <p>
      <em>Recherchez des ressources dans le référentiel AEM Assets afin de les diffuser aux applications en aval.</em>
   </p>
</td>
<td>
   <a href="/help/assets/deliver-assets-apis.md">
   <img alt="Diffuser des ressources aux applications en aval" src="./assets/delivery-url.png" />
   </a>
   <div>
      <a href="/help/assets/deliver-assets-apis.md">
 <strong>Diffuser des ressources aux applications en aval</strong>
 </a>
   </div>
   <p>
      <em>Diffusez des ressources aux applications en aval intégrées à l’aide d’une URL de diffusion.</em>
   </p>
</td>
<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Limiter l’accès aux ressources dans Experience Manager" src="./assets/restricted-access.png" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
 <strong>Limiter l’accès aux ressources dans Experience Manager</strong>
 </a>
   </div>
   <p>
      <em>La personne chargée de l’administration de DAM ou les responsable de marques limitent l’accès en configurant des rôles pour les ressources approuvées sur l’instance de création AEM as a Cloud Service.</em>
   </p>
</td>

</table>
<table>
<td>
   <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
   <img alt="Intégrer AEM Assets distant à AEM Sites" src="./assets/connected-assets-rdam.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
 <strong>Intégrer AEMS Assets distant à AEM Sites</strong>
 </a>
   </div>
   <p>
      <em>Découvrez comment intégrer AEM Assets distant à l’environnement AEM Sites. </em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media-open-apis-faqs.md">
   <img alt="Questions fréquentes sur Dynamic Media avec fonctionnalités OpenAPI" src="./assets/dynamic-media-faqs.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-faqs.md">
 <strong>Questions fréquentes sur Dynamic Media avec fonctionnalités OpenAPI</strong>
 </a>
   </div>
   <p>
      <em>Découvrez les réponses aux questions fréquentes sur Dynamic Media avec fonctionnalités OpenAPI.</em>
   </p>
</td>
<td>
   <a href="/help/assets/configure-custom-domain.md">
   <img alt="Configurer un domaine personnalisé" src="./assets/configure-custom-domain.jpeg" />
   </a>
   <div>
      <a href="/help/assets/configure-custom-domain.md">
 <strong>Configurer un domaine personnalisé</strong>
 </a>
   </div>
   <p>
      <em>AEM as a Cloud Service est fourni avec un domaine par défaut, mais vous pouvez le personnaliser selon vos besoins.</em>
   </p>
</td>

</table>

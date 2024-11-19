---
title: Dynamic Media avec fonctionnalités OpenAPI
description: Découvrez les concepts clés, tels que les raisons d’utiliser Dynamic Media avec les fonctionnalités OpenAPI et comment l’activer.
role: User
exl-id: 658b6eff-9f5a-4166-9ff6-5dc8eb92ada3
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 2%

---

# Dynamic Media avec fonctionnalités OpenAPI {#new-dynaminc-media-apis-overview}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|-----|

>[!AVAILABILITY]
>
>Le guide des fonctionnalités de Dynamic Media avec OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE Dynamic Media avec OpenAPI Feature PDF ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Dans un monde numérique à rythme rapide, libérer tout le potentiel des ressources numériques de votre marque est essentiel pour rester en avance sur la concurrence. Une solution de gestion d’Assets numériques (DAM) globale facilite la gouvernance des ressources, favorise la cohérence de la marque et accélère la diffusion du contenu tout en assurant l’intégrité de la marque et des expériences client exceptionnelles.

Dynamic Media avec les fonctionnalités OpenAPI place la gestion des actifs numériques au coeur d’un écosystème de chaîne d’approvisionnement de contenu agile et efficace pour assurer la gouvernance et la diffusion des ressources.

## Pourquoi utiliser Dynamic Media avec les fonctionnalités OpenAPI ? {#dynamic-media-open-api-features}

Dynamic Media avec les fonctionnalités OpenAPI offre les avantages clés suivants :

* **Intégrations en toute transparence** : Dynamic Media avec fonctionnalités OpenAPI offre un ensemble complet d’API de recherche et de diffusion. Cela permet à vos développeurs d&#39;[ intégrer facilement la diffusion des ressources à leurs applications ](/help/assets/integrate-dynamic-media-open-apis.md). Les applications comprennent les applications d’Adobe ainsi que les applications tierces. Il fournit une [interface utilisateur du sélecteur de ressources Micro Frontend ](/help/assets/overview-asset-selector.md) pour rechercher et sélectionner des ressources approuvées. Le sélecteur peut être intégré sans effort à n’importe quelle application basée sur des structures JavaScript telles que React JS, Angular JS et Vanilla JS.

* **Gestion centralisée des ressources numériques** : DAM est la source unique de vérité pour toutes les ressources numériques. Vos ressources numériques sont gérées de manière centralisée dans AEM Assets et diffusées aux applications gourmandes par référence à l’aide d’URL de diffusion, sans copier de fichiers binaires de ressources.

* **Mises à jour en temps réel** : toute modification apportée aux ressources approuvées dans la gestion des actifs numériques, y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une valeur TTL (short Time-to-Live) de 10 minutes configurée pour Dynamic Media avec des fonctionnalités OpenAPI via CDN, les mises à jour deviennent visibles dans toutes les interfaces de création et de publication en moins de 10 minutes.

* **Cohérence des marques** : seuls les [actifs approuvés par la marque](/help/assets/approve-assets.md) sont exposés aux applications en aval. [Les responsables de marques et les marketeurs maintiennent un contrôle strict sur les ressources de marque](/help/assets/restrict-assets-delivery.md). Seule la version approuvée et la dernière version de la ressource peut être utilisée, ce qui garantit la cohérence de la marque sur tous les canaux et applications.

* **Diffusion optimisée pour le web** : les ressources numériques sont diffusées dans des formats optimisés pour le web afin d’améliorer les principales valeurs web de vos expériences numériques. Cela inclut la prise en charge des rendus WebP pour les images, la diffusion en continu adaptative via les protocoles HLS ou DASH pour les vidéos et les rendus originaux pour les documents.

* **Transformation de ressources dynamique** : notre système permet la transformation d’images à la volée à l’aide de paramètres d’URL connus sous le nom de modificateurs d’image. [Par exemple, largeur, hauteur, rotation, symétrie, qualité, recadrage, format et recadrage intelligent ](/help/assets/deliver-assets-apis.md). Les rendus transformés sont générés dynamiquement et distribués de manière transparente via le réseau de diffusion de contenu.

* **Livraison sécurisée des ressources** : Dynamic Media avec les fonctionnalités OpenAPI fournit un mécanisme de contrôle d’accès à vos ressources numériques. Vous pouvez spécifier des rôles ou des groupes d’utilisateurs comme métadonnées pour les ressources à sécuriser et définir une période prédéfinie pendant laquelle [ seuls les utilisateurs autorisés peuvent accéder à ces ressources](/help/assets/restrict-assets-delivery.md). Les URL de diffusion des ressources sécurisées ne sont pas résolues pour les utilisateurs non autorisés au cours de la période limitée.

* **Informations sur les données pour prendre des décisions éclairées (à venir)** : au-delà de la gestion des ressources et de la diffusion, il capture les informations sur les données de diffusion dans les diffusions de ressources sur le réseau de diffusion de contenu, ce qui permet aux gestionnaires de marque de suivre les mesures de diffusion sur l’ensemble des canaux. Il leur permet de prendre des décisions pilotées par les données pour optimiser continuellement la gouvernance des ressources et les stratégies de diffusion.

![ Diagramme de flux de données Dynamic Media Open API](assets/dm-openapi-dfd.png)

## Conditions préalables pour accéder à Dynamic Media avec les fonctionnalités OpenAPI {#prerequisites-dynaminc-media-open-apis}

Pour accéder à Dynamic Media avec des fonctionnalités OpenAPI, vous devez disposer de licences pour :

* AEM Assets as a Cloud Service

* Dynamic Media AEM

## Comment activer Dynamic Media avec les fonctionnalités OpenAPI ? {#enable-dynamic-media-open-apis}

Avant d’envoyer une demande d’activation de Dynamic Media avec les fonctionnalités OpenAPI sur AEM as a Cloud Service, vérifiez qu’elle n’est pas déjà activée.

Une fois que les [conditions préalables](#prerequisites-dynaminc-media-open-apis) sont remplies et que les fonctionnalités OpenAPI de Dynamic Media sont activées sur votre instance AEM as a Cloud Service, une URL de diffusion est disponible pour chaque ressource approuvée dans le référentiel. Pour plus d’informations sur la copie de l’URL de diffusion, voir [Copier l’URL de diffusion pour les ressources approuvées](approve-assets.md#copy-delivery-url-approved-assets) . Adobe recommande d’utiliser cette méthode pour vérifier que Dynamic Media avec les fonctionnalités OpenAPI est activé sur AEM as a Cloud Service avant d’envoyer un ticket d’assistance pour l’activer.

Pour activer Dynamic Media avec les fonctionnalités OpenAPI sur AEM as a Cloud Service, envoyez un ticket de support d’Adobe avec les détails suivants :

* Identifiant de programme et d’environnement des Cloud Service

* Détails du cas d’utilisation à résoudre avec Dynamic Media avec l’intégration des fonctionnalités OpenAPI.

* Détails des applications en aval à intégrer à Dynamic Media avec les fonctionnalités OpenAPI.

  >[!NOTE]
  >
  Pour l’intégrer à une application non Adobe, indiquez les noms de domaine à la liste autorisée où l’application est hébergée.

* Détails des principaux contacts clients impliqués dans le projet d’intégration.

* Liste des membres clés de l’équipe du compte d’Adobe (email).

Une fois que vous avez envoyé le ticket d’assistance, Adobe active Dynamic Media avec les fonctionnalités OpenAPI dans votre environnement Cloud Service et partage les détails, tels que l’identifiant du client IMS, pour que vous puissiez poursuivre l’intégration.

>[!NOTE]
>
Exclure `/conf/global/settings/dam/assets-configurations/assetdelivery` de tout module de contenu, afin d’éviter la désactivation de Dynamic Media avec les fonctionnalités OpenAPI.

## En savoir plus sur les principales fonctionnalités {#learn-more-key-capabilities}

<table>
<td>
   <a href="/help/assets/approve-assets.md">
   <img alt="Approbation des ressources dans Experience Manager Assets" src="./assets/approved-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/approve-assets.md">
      <strong>Approuver des ressources dans Experience Manager Assets</strong>
      </a>
   </div>
   <p>
      <em> Approuvez des ressources dans AEM Assets pour rationaliser la gestion des ressources, en veillant à un processus contrôlé et efficace pour gérer les ressources.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="Intégration d’AEM Assets aux applications en aval" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
      <strong>Intégrer AEM Assets aux applications en aval</strong>
      </a>
   </div>
   <p>
      <em>Intégrez votre propre interface utilisateur personnalisée au référentiel Experience Manager Assets à l’aide des API de recherche et de diffusion ou utilisez le sélecteur de ressources Micro-Frontend d’Adobe.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="Sélecteur de ressources d’Adobe" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong>Sélecteur de ressources micro-front d’Adobe</strong>
      </a>
   </div>
   <p>
      <em>Interface utilisateur qui interagit avec le référentiel AEM Assets pour rechercher des ressources, puis les utiliser dans votre expérience de création d’applications.</em>
   </p>
</td>
</table>
<table>



<table>
<td>
   <a href="/help/assets/search-assets-api.md">
   <img alt="Recherche de ressources dans le référentiel Experience Manager Assets" src="./assets/search-assets-api-overview.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-api.md">
      <strong>Recherche de ressources dans le référentiel Experience Manager Assets</strong>
      </a>
   </div>
   <p>
      <em>Recherchez des ressources dans le référentiel AEM Assets afin qu’elles puissent être diffusées aux applications en aval.</em>
   </p>
</td>
<td>
   <a href="/help/assets/deliver-assets-apis.md">
   <img alt="Diffuser des ressources vers les applications en aval" src="./assets/delivery-url.png" />
   </a>
   <div>
      <a href="/help/assets/deliver-assets-apis.md">
      <strong> Diffuser des ressources aux applications en aval</strong>
      </a>
   </div>
   <p>
      <em>Diffuser des ressources vers des applications en aval intégrées à l’aide d’une URL de diffusion.</em>
   </p>
</td>
<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Limitation de l’accès aux ressources dans Experience Manager" src="./assets/restricted-access.png" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Limiter l’accès aux ressources dans Experience Manager</strong>
      </a>
   </div>
   <p>
      <em> L’administrateur DAM ou les gestionnaires de marques limitent l’accès en configurant des rôles pour les ressources approuvées sur l’instance d’auteur AEM as a Cloud Service.</em>
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
      <strong>Intégrer AEM Assets distant avec AEM Sites</strong>
      </a>
   </div>
   <p>
      <em>Découvrez comment intégrer AEM Assets distant à l’environnement AEM Sites. </em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media-open-apis-faqs.md">
   <img alt="Questions fréquentes sur les fonctionnalités OpenAPI de Dynamic Media" src="./assets/dynamic-media-faqs.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-faqs.md">
      <strong> Questions fréquentes sur les fonctionnalités de Dynamic Media avec OpenAPI</strong>
      </a>
   </div>
   <p>
      <em>Obtenez une réponse aux questions les plus fréquemment posées sur les fonctionnalités Dynamic Media avec OpenAPI.</em>
   </p>
</td>
<td>
   <a href="/help/assets/configure-custom-domain.md">
   <img alt="Configurer des domaines personnalisés" src="./assets/configure-custom-domain.jpeg" />
   </a>
   <div>
      <a href="/help/assets/configure-custom-domain.md">
      <strong>Configurer un domaine personnalisé</strong>
      </a>
   </div>
   <p>
      <em>Lorsqu'AEM as a Cloud Service est fourni avec un domaine par défaut, vous pouvez le personnaliser selon vos besoins.</em>
   </p>
</td>

</table>

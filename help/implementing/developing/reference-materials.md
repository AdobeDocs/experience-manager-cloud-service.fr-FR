---
title: Documents de référence sur les API
description: AEM dispose d’API complètes et puissantes que vous pouvez utiliser pour votre projet d’expérience digitale.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 4182374ea9d603ed53e75511d34fdfcf69829200
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 78%

---

# Documents de référence sur les API {#api-reference-materials}

Adobe Experience Manager (AEM) fournit de nombreuses API pour développer des applications et étendre AEM. AEM s&#39;appuie sur plusieurs technologies open source, qui peuvent également être utilisées.

## API de base d’AEM {#core-aem-apis}

Les API suivantes sont essentielles pour AEM.

| API | Description |
|---|---|
| [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | abstractions de produits telles que pages, ressources, workflows, etc. |
| [IU Granite](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | Pile Open Web d’Adobe, fournissant divers composants essentiels (les matériaux Granite 6.5 s’appliquent à AEMaaCS) |
| [IU Coral](https://opensource.adobe.com/coral-spectrum/documentation/) | Style visuel d’Adobe pour les interfaces utilisateur cloud, conçu pour assurer la cohérence de l’expérience utilisateur |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

>[!NOTE]
>
>Pour obtenir les dernières informations sur les API Experience Manager, consultez également la page [API Adobe Experience Manager as a Cloud Service](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

## Autres frameworks {#additional-apis}

AEM repose sur plusieurs API open source supplémentaires.

| API | Description |
|---|---|
| [Apache Sling](https://sling.apache.org/apidocs/sling11/) | Structure web qui utilise un référentiel de contenu Java (JCR) pour stocker et gérer du contenu |
| [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Mise en œuvre d’un référentiel de contenu Java (JCR) hiérarchique évolutif et haute performance à utiliser comme base pour les sites web modernes de classe mondiale |
| [Référentiel de contenu Java](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | Spécification de la version 2.0 de JCR |
| [Apache Felix](https://felix.apache.org) | Mise en œuvre de la structure et de la plateforme de service Open Services Gateway Initiative (OSGi) |

## Instructions relatives aux préférences d’API {#guidelines}

AEM repose sur les quatre principaux ensembles d’API Java suivants, dans l’ordre décroissant de préférence.

| Priorité | API | Description |
|---|---|---|
| 1 | [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | abstractions de produits telles que pages, ressources, workflows, etc. |
| 2 | [Apache Sling](https://sling.apache.org/apidocs/sling11/) | REST et abstractions basées sur des ressources telles que des ressources, cartes de valeurs et requêtes HTTP. |
| 3 | [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Abstractions de données et de contenu telles que des nœuds, propriétés et sessions. |
| 4 | [Apache Felix](https://felix.apache.org/) | Abstractions du conteneur d’application OSGi telles que les services et les composants (OSGi). |

Si une API est fournie par AEM, préférez-la à Sling, JCR et OSGi. Si AEM ne fournit pas d’API, préférez Sling à JCR et OSGi.

>[!TIP]
>
>Pour plus d’informations sur ces directives, consultez le document [Présentation des bonnes pratiques de l’API Java.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=fr)

## Services et API de diffusion et de gestion de contenu AEM {#delivery-apis}

AEM propose des composants personnalisables et des options de diffusion de contenu.

| Fonctionnalité | Description |
|---|---|
| [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) | Composants de gestion de contenu web normalisé (WCM) pour AEM dont l’objectif est d’accélérer le développement et de réduire les coûts de maintenance de vos sites web |
| [Exportateur JSON](/help/implementing/developing/components/json-exporter.md)  | Diffuser le contenu d’une page AEM au format de modèle de données JSON |
| [Activation de l’exportateur JSON pour un composant](/help/implementing/developing/components/enabling-json-exporter.md) | Générer l’exportation JSON du contenu du composant en fonction d’une structure de modélisation |
| [ OpenAPI de modèle de fragment de contenu et de fragment de contenu ](/help/headless/content-fragment-openapis.md) | API ouvertes du modèle de fragment de contenu et de fragment de contenu |
| [API AEM REST OpenAPI pour la diffusion de fragments de contenu](/help/headless/aem-rest-openapi-content-fragment-delivery.md) | Une API HTTP REST sur les Edge Delivery Services d’AEM, conçue pour diffuser du contenu structuré à partir de fragments de contenu au format JSON. |
| [API GraphQL de fragments de contenu](/help/headless/graphql-api/content-fragments.md) | Activer la diffusion efficace de fragments de contenu vers les clients JavaScript dans les implémentations CMS découplées |
|  |  |
| [API Assets](/help/assets/mac-api-assets.md) | Permet d’effectuer des opérations CRUD (créer, lire, mettre à jour, supprimer) sur des ressources, y compris des fichiers binaires, des métadonnées, des rendus et des commentaires. Voir API HTTP AEM Assets |
| [API HTTP de fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md) | Accès au contenu de fragment de contenu directement via l’API HTTP via les opérations CRUD |
| [API HTTP ressources de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html?lang=fr) | Format exact des requêtes de ressources HTTP prises en charge |

>[!NOTE]
>
>Voir [AEM API pour la diffusion et la gestion de contenu structurées](/help/headless/apis-headless-and-content-fragments.md) pour un aperçu des différentes API disponibles et une comparaison de certains des concepts impliqués.

## API spécifiques à SPA {#spa-apis}

La structure du SDK de l’éditeur d’application monopage AEM fournit des références d’API JavaScript.

| API | Description |
|---|---|
| [Mappage de composant](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | Offre aux applications monopages le moyen de mapper les composants front-end avec les types de ressources Adobe Experience Manager (composants AEM). |
| [Gestionnaire de modèle de page](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Interpréteur entre l’éditeur Adobe Experience Manager et l’éditeur d’application monopage Adobe Experience Manager |
| [Composants modifiables React](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Fournit les composants React et la couche d’intégration pour vous familiariser avec l’éditeur de site Adobe Experience Manager |
| [Composants modifiables Angular](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Fournit les composants Angular et la couche d’intégration pour vous familiariser avec l’éditeur de site Adobe Experience Manager |

>[!TIP]
>
>Pour plus d’informations sur les applications d’une seule page (SPA), consultez la section [Introduction et présentation des applications monopage (SPA)](/help/implementing/developing/hybrid/introduction.md).

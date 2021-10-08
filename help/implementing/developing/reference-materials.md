---
title: Documents de référence sur les API
description: AEM dispose d’API complètes et puissantes que vous pouvez exploiter pour votre projet d’expérience numérique.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Documents de référence sur les API {#api-reference-materials}

Adobe Experience Manager (AEM) fournit de nombreuses API pour le développement d’applications et l’extension d’AEM. AEM repose sur un certain nombre de technologies open source, qui peuvent également être exploitées.

## AEM API Core {#core-aem-apis}

Les API suivantes sont essentielles pour AEM.

| API | Description |
|---|---|
| [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | abstractions de produits telles que pages, ressources, workflows, etc. |
| [IU Granite](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | Pile Web ouverte d’Adobe, fournissant divers composants essentiels (notez que les matériaux Granite 6.5 s’appliquent à AEMaaCS). |
| [IU Coral](https://opensource.adobe.com/coral-spectrum/documentation/) | Style visuel d’Adobe pour les interfaces utilisateur cloud, conçu pour assurer la cohérence de l’expérience utilisateur |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

## Autres frameworks {#additional-apis}

AEM repose sur un certain nombre d’API Open Source supplémentaires.

| API | Description |
|---|---|
| [Apache Sling](https://sling.apache.org/apidocs/sling11/) | Structure web qui utilise un référentiel de contenu Java (JCR) pour stocker et gérer du contenu |
| [Apache Jackrabbit Oak](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Mise en oeuvre d’un référentiel de contenu Java (JCR) hiérarchique évolutif et haute performance à utiliser comme base pour les sites web modernes de classe mondiale |
| [Référentiel de contenu Java](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | Spécification de la version 2.0 de JCR |
| [Apache Felix](https://felix.apache.org) | Mise en oeuvre de la structure et de la plateforme de service Open Services Gateway Initiative (OSGi) |

## Instructions relatives aux préférences d’API {#guidelines}

AEM repose sur les quatre principaux ensembles d’API Java suivants, dans l’ordre décroissant de préférence.

| Priorité | API | Description |
|---|---|---|
| 1 | [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | abstractions de produits telles que pages, ressources, workflows, etc. |
| 2 | [Apache Sling](https://sling.apache.org/apidocs/sling11/) | abstractions REST et basées sur des ressources telles que les ressources, les mappages de valeurs et les requêtes HTTP. |
| 3 | [Apache Jackrabbit Oak](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Extraits de données et de contenu tels que le noeud, les propriétés et les sessions. |
| 4 | [Apache Felix](https://felix.apache.org/) | abstractions du conteneur d’applications OSGi telles que les composants de services et (OSGi). |

Si une API est fournie par AEM, préférez-la à Sling, JCR et OSGi. Si AEM ne fournit pas d’API, préférez Sling à JCR et OSGi.

>[!TIP]
>
>Pour plus d’informations sur ces directives, consultez le document [Présentation des bonnes pratiques de l’API Java.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=fr)

## Services de diffusion AEM et de gestion de contenu et API {#delivery-apis}

AEM propose des composants personnalisables et des options de diffusion de contenu.

| Fonctionnalité | Description |
|---|---|
| [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) | Composants WCM (Web Content Management) normalisés pour AEM afin d’accélérer le développement et de réduire les coûts de maintenance de vos sites web |
| [Exportateur JSON](/help/implementing/developing/components/json-exporter.md)  | Diffuser le contenu d’une page AEM au format de modèle de données JSON |
| [Activation de l’exportateur JSON pour un composant](/help/implementing/developing/components/enabling-json-exporter.md) | Générer l’exportation JSON du contenu du composant en fonction d’une structure de modélisation |
| [API Assets](/help/assets/mac-api-assets.md) | Permet d’effectuer des opérations CRUD (créer, lire, mettre à jour, supprimer) sur des ressources, y compris des fichiers binaires, des métadonnées, des rendus et des commentaires. Voir API HTTP AEM Assets |
| [API HTTP de fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md) | Accès au contenu de fragment de contenu directement via l’API HTTP via les opérations CRUD |
| [API GraphQL de fragment de contenu](/help/assets/content-fragments/graphql-api-content-fragments.md) | Activer la diffusion efficace des fragments de contenu vers les clients JavaScript dans les implémentations CMS sans interface |
| [Fragments de contenu API HTTP Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html?lang=fr) | Format exact des requêtes de ressources HTTP prises en charge |

## API spécifiques à SPA {#spa-apis}

AEM structure du SDK de l’éditeur d’applications d’une seule page (SPA) fournit des références d’API JavaScript spécifiques.

| API | Description |
|---|---|
| [Mappage de composant](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | Permet à l’application d’une seule page de mapper les composants front-end aux types de ressources Adobe Experience Manager (composants AEM). |
| [Gestionnaire de modèle de page](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Un interpréteur entre Adobe Experience Manager Editor et Adobe Experience Manager Single Page Application (SPA) Editor |
| [Composants modifiables React](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Fournit les composants React et la couche d’intégration pour vous familiariser avec l’éditeur de site Adobe Experience Manager |
| [Composants modifiables Angular](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Fournit les composants d’Angular et la couche d’intégration pour vous familiariser avec Adobe Experience Manager Site Editor |

>[!TIP]
>
>Pour plus d’informations sur les applications d’une seule page, consultez la section [SPA Introduction et présentation](/help/implementing/developing/hybrid/introduction.md) .

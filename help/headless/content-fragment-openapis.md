---
title: API OpenAPI de fragments de contenu et de modèles de fragment de contenu
description: En savoir plus sur les API ouvertes Fragments de contenu et Modèles de fragment de contenu .
exl-id: 077eed73-a066-4273-b2f5-da4bf5cd900c
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 1fb1201fa976e4c0e3c87f22bd9327a55828efef
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 4%

---

# Fragments de contenu et Gestion des modèles de fragments de contenu OpenAPI {#content-fragments-and-content-fragment-models-management-openapis}

L’implémentation OpenAPI modernisée de l’API de gestion des fragments de contenu permet aux développeurs d’effectuer par programmation des opérations de création, de lecture, de mise à jour et de suppression sur AEM afin de gérer les modèles de fragment de contenu et les fragments de contenu stockés dans AEM. Ces API prennent en charge un certain nombre de cas d’utilisation.

Pour consulter la documentation complète, voir [API de gestion des fragments de contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/).

>[!NOTE]
>
>L’utilisation existante de l’[API HTTP Assets](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/admin/mac-api-assets) pour les fragments de contenu doit être migrée vers la nouvelle OpenAPI de gestion des fragments de contenu.

>[!NOTE]
>
>Une autorisation est requise pour accéder à l’OpenAPI lorsque vous n’êtes pas connecté à AEM ; par exemple, lorsque l’OpenAPI est utilisé à partir d’un autre produit dans le cadre d’une intégration.
>
>Voir [API OpenAPI-Based](/help/implementing/developing/open-api-based-apis.md) pour plus d’informations sur l’autorisation de votre accès à l’API OpenAPI.

>[!CAUTION]
>
>Par défaut, l’OpenAPI de gestion des fragments de contenu est désactivée lors de la publication. Au lieu de cela, pour les cas d’utilisation orientés diffusion, nous vous recommandons d’utiliser l’[OpenAPI de diffusion de fragments de contenu](/help/headless/aem-content-fragment-delivery-with-openapi.md).

>[!NOTE]
>
>Consultez [API AEM pour la diffusion et la gestion de contenu structuré](/help/headless/apis-headless-and-content-fragments.md) pour un aperçu des différentes API disponibles et une comparaison de certains des concepts impliqués.
---
title: Présentation d’AEM Screens as a Cloud Service
description: Cette page présente Adobe Experience Manager Screens as a Cloud Service.
exl-id: b1cc0a63-ecd3-4d89-ac49-f384cc610cdc
source-git-commit: a77e5dc4273736b969e9a4a62fcac75664495ee6
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 56%

---

# Présentation d’AEM Screens as a Cloud Service {#introduction-screens-cloud}

Avec Adobe Experience Manager (AEM) Screens as a Cloud Service, vous pouvez créer des expériences de signalétique digitale attrayantes et dynamiques destinées à être utilisées dans les espaces publics. Il s’agit de la prochaine évolution du produit AEM Screens et représente un grand bond en avant en termes de convivialité et d’évolutivité.

AEM Screens as a Cloud Service est une solution de signalétique numérique qui permet aux spécialistes marketing de créer et de gérer des expériences numériques dynamiques à grande échelle. Il implique également différents types d’écrans physiques dans le cadre d’une stratégie marketing numérique globale. Il étend l’offre omnicanale d’Adobe au-delà des canaux web et mobiles habituels afin d’inclure également les canaux de signalétique numérique qui nous entourent. AEM Screens as a Cloud Service offre aux utilisateurs des expériences plus pertinentes, contextuelles, productives et d’anticipation grâce à une compréhension approfondie de la création de contenu, de l’assemblage de contenu, de la gestion d’événements déclenchée et de la lecture multimédia pour tous les clients et visiteurs dans n’importe quel espace public.

## Présentation des composants dans Screens as a Cloud Service {#understanding-components}

Screens as a Cloud Service comporte deux composants principaux, à savoir :

* **[Fournisseur de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html)**, qui est le module complémentaire Screens s’exécutant sur AEM Cloud Service ou sur Adobe Managed Services (AMS). Le fournisseur de contenu Screens permet à l’auteur de contenu de créer et de gérer des canaux. Les auteurs de contenu peuvent ajouter du nouveau contenu et le modifier sans se soucier des détails de la création d’affichages ou de l’enregistrement du lecteur. Le fournisseur de contenu fournit une abstraction des détails sous-jacents du développement du contenu, des affichages ou de l’enregistrement du lecteur.

* **[Fournisseur de services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html)**, qui est le service de gestion de l’affichage numérique exécuté sur Adobe I/O Runtime. Le fournisseur de services Screens permet aux auteurs, développeurs et administrateurs de contenu de gérer les affichages et les lecteurs pour la lecture du contenu une fois le contenu ajouté aux canaux. En outre, le fournisseur de services Screens informe l’orchestrateur sur l’emplacement et le moment où le contenu va être lu à un niveau élevé.


## Aperçu de l’architecture {#architectural-overview}

En tant qu’utilisateur AEM Screens as a Cloud Service, vous pouvez ajouter et gérer du contenu dans les canaux. Vous pouvez enregistrer et gérer des affichages et des lecteurs à partir des interfaces conçues spécifiquement pour Screens as a Cloud Service, à savoir : **Fournisseur de services Screens** et **Fournisseur de contenu Screens**.

![image](/help/screens-cloud/assets/architecture-screenscloud.png)

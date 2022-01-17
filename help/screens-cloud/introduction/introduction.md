---
title: AEM Screens as a Cloud Service
description: Cette page présente AEM Screens as a Cloud Service.
exl-id: b1cc0a63-ecd3-4d89-ac49-f384cc610cdc
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%

---

# Présentation d’AEM Screens as a Cloud Service {#introduction-screens-cloud}

Avec AEM Screens as a Cloud Service, vous pouvez créer des expériences de signalétique numérique attrayantes et dynamiques destinées à être utilisées dans les espaces publics. Il s’agit de la prochaine évolution du produit AEM Screens et représente un grand bond en avant en termes de convivialité et d’évolutivité.

AEM Screens as a Cloud Service est une solution de signalétique numérique qui permet aux marketeurs de créer et de gérer des expériences numériques dynamiques à grande échelle. En outre, il implique différents types d’écrans physiques dans le cadre d’une stratégie marketing numérique globale. Il étend l’offre omnicanale d’Adobe au-delà des canaux web et mobiles habituels afin d’inclure également les canaux de signalétique numérique qui nous entourent. AEM Screens as a Cloud Service offre aux utilisateurs des expériences plus pertinentes, contextuelles, productives et d’anticipation grâce à une compréhension approfondie de la création de contenu, de l’assemblage de contenu, de la gestion d’événements déclenchée et de la lecture multimédia pour tous les clients et visiteurs dans n’importe quel espace public.

## Présentation des composants dans Screens as a Cloud Service {#understanding-components}

Screens as a Cloud Service comporte deux composants principaux, à savoir :

* **[Fournisseur de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=fr)**, qui est le module complémentaire Screens s’exécutant sur AEM Cloud Service ou sur Adobe Managed Services (AMS). Le fournisseur de contenu Screens permet à l’auteur de contenu de créer et de gérer des canaux. Les auteurs de contenu peuvent ajouter du nouveau contenu et le modifier sans se soucier des détails de la création d’affichages ou de l’enregistrement du lecteur. Le fournisseur de contenu fournit une abstraction des détails sous-jacents du développement du contenu, des affichages ou de l’enregistrement du lecteur.

* **[Fournisseur de services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html?lang=fr)**, qui est le service de gestion de la signalétique numérique s’exécutant sur Adobe I/O Runtime. Le fournisseur de services Screens permet à l’auteur aux développeurs et aux administrateurs de contenu de gérer les affichages et les lecteurs pour la lecture de contenu une fois le contenu ajouté aux canaux. En outre, le fournisseur de services Screens informe l’orchestrateur de l’endroit et du moment où le contenu va être lu à un niveau élevé.


## Présentation de l’architecture {#architectural-overview}

En tant qu’utilisateur AEM Screens as a Cloud Service, vous pouvez ajouter et gérer du contenu dans les canaux, enregistrer et gérer des affichages et des lecteurs à partir des interfaces conçues spécifiquement pour Screens as a Cloud Service, à savoir **Fournisseur de services Screens** et **Fournisseur de contenu Screens**.

![image](/help/screens-cloud/assets/architecture-screenscloud.png)

---
title: Utilisation de fragments de contenu avec Adobe Journey Optimizer
description: Découvrez comment les fragments de contenu peuvent être intégrés et utilisés avec Adobe Journey Optimizer.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: 4090ee41-80f1-4389-8961-e4af891f01ff
source-git-commit: 0fd7b2633488ceb14d34b1978a91a3a830d8762a
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 10%

---

# Fragments de contenu avec Adobe Journey Optimizer {#content-fragments-with-journey-optimizer}

[Adobe Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started) vous aide à proposer des expériences connectées, contextuelles et personnalisées à vos clients. En intégrant Adobe Experience Manager (AEM) as a Cloud Service à Adobe Journey Optimizer (AJO), vous pouvez réutiliser du contenu AEM dans vos canaux entrants AJO et vos canaux sortants AJO, notamment le web, les SMS, les e-mails, etc.

Par exemple, vous pouvez effectuer les actions suivantes :

* incorporez facilement vos [fragments de contenu AEM](/help/sites-cloud/administering/content-fragments/overview.md) dans votre [e-mail Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/email-landing-page) contenu
* prévisualisez l’expérience AJO directement depuis AEM

La connexion entre les fragments de contenu et AJO simplifie le processus d’accès au contenu AEM et d’utilisation de celui-ci, ce qui permet la création de campagnes et de parcours personnalisés et dynamiques.

Pour plus d’informations, commencez par consulter la documentation d’AJO :

* [Utilisation de fragments de contenu dans AJO](https://experienceleague.adobe.com/docs/journey-optimizer/using/integrations/aem-fragments.html#integrations)
* [Intégration des offres AJO au fragment de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/managing-offers-in-the-offer-library/configure-offers/add-representations#urls)

## Configuration du Dispatcher {#dispatcher-configuration}

Pour permettre à AJO d’accéder aux fragments de contenu d’AEM par le biais de l’[API de gestion des fragments de contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/), vous devez configurer le Dispatcher :

* En `dispatcher/src/conf.dispatcher.d/filters/filters.any` :

* Ajouter :

  ```xml
  # Allow Content Fragments API requests, required for integration with AJO 
  /200 {/type "allow" /url "/adobe/sites/cf/*" }
  ```

## Informations supplémentaires {#further-information}

Pour plus d’informations, consultez :

* Extension [Références externes AJO](/help/sites-cloud/administering/content-fragments/extension-content-fragment-ajo-external-references.md)

---
title: Outil convertisseur du Dispatcher AEM
description: Outil convertisseur du Dispatcher AEM
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 37%

---

# Convertisseur du Dispatcher AEM {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="Convertisseur du Dispatcher AEM"
>abstract="Le convertisseur du Dispatcher Adobe Experience Manager convertit les configurations existantes sur AEM Dispatcher en configurations sur AEM Dispatcher as a Cloud Service."

Le convertisseur du Dispatcher Adobe Experience Manager convertit les configurations existantes sur AEM Dispatcher en configurations sur AEM Dispatcher as a Cloud Service.

## Présentation du Dispatcher {#introduction-dispatcher}

Dispatcher est l’outil de mise en cache Adobe Experience Manager ou d’équilibrage de charge, ou les deux. L’utilisation de Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Par conséquent, vous pouvez augmenter la sécurité de votre instance AEM en utilisant Dispatcher avec un serveur web de niveau élevé.

>[!NOTE]
>L’utilisation la plus courante du Dispatcher consiste à mettre en cache les réponses d’une **instance de publication AEM** pour améliorer la réactivité et la sécurité du site web publié en externe.

Voir [Présentation de Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr) pour découvrir comment Dispatcher effectue la mise en cache, renvoie des documents et effectue l’équilibrage de charge.

### Configuration et test d’Apache et de Dispatcher {#dispatcher-configurations-cloud}

Découvrez comment structurer les configurations Apache et Dispatcher as a Cloud Service AEM, et comment valider et exécuter cette configuration localement avant son déploiement dans les environnements cloud.

Voir [Dispatcher en mode cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=fr) pour plus d’informations.

## Convertisseur du Dispatcher AEM {#aem-dispatcher-converter}

Le convertisseur du Dispatcher AEM permet de refactoriser les configurations existantes de Dispatcher On-Premise ou Adobe Managed Services en une configuration de Dispatcher compatible AEM as a Cloud Service.

## Utilisation du convertisseur du Dispatcher AEM {#using-dispatcher-converter}

* Au moyen de l’interface de ligne de commande d’Adobe Developer : Adobe vous recommande d’utiliser le convertisseur du Dispatcher AEM au moyen du `aio-cli-plugin-aem-cloud-service-migration` (AEM module externe de refactorisation du code as a Cloud Service pour l’interface de ligne de commande d’Adobe Developer).

  Voir **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** vous pouvez ainsi apprendre à installer et à utiliser le module externe.

* En tant qu’utilitaire autonome : L’outil AEM convertisseur du Dispatcher peut également être exécuté en tant qu’utilitaire autonome.

  Voir **[Ressource Git : Convertisseur du Dispatcher AEM Cloud Service](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** pour en savoir plus sur l’utilisation et la résolution des problèmes de cet outil.

>[!IMPORTANT]
>Le convertisseur du Dispatcher AEM est développé à l’aide de NodeJS. Adobe recommande que NodeJS 10.0+ soit installé.

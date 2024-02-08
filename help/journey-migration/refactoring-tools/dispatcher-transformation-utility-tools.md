---
title: Outil convertisseur du Dispatcher AEM
description: Découvrez comment convertir des configurations existantes sur AEM Dispatcher en configurations sur AEM Dispatcher as a Cloud Service.
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 94%

---

# Convertisseur du Dispatcher AEM {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="Convertisseur du Dispatcher AEM"
>abstract="Le convertisseur du Dispatcher Adobe Experience Manager convertit les configurations existantes du Dispatcher AEM en configurations du Dispatcher AEM as a Cloud Service."

Le convertisseur du Dispatcher Adobe Experience Manager convertit les configurations existantes du Dispatcher AEM en configurations du Dispatcher AEM as a Cloud Service.

## Présentation du Dispatcher {#introduction-dispatcher}

Le Dispatcher est l’outil de mise en cache d’Adobe Experience Manager ou d’équilibrage de charge, ou les deux. L’utilisation du Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Vous pouvez donc accroître la sécurité de l’instance AEM en utilisant le Dispatcher avec un serveur web de niveau entreprise.

>[!NOTE]
>L’utilisation la plus courante du Dispatcher consiste à mettre en cache les réponses d’une **instance de publication AEM** pour améliorer la réactivité et la sécurité du site web publié en externe.

Référez-vous à la [Présentation du Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr) pour savoir comment le Dispatcher effectue la mise en cache, renvoie des documents et réalise l’équilibrage de charge.

### Configuration et test d’Apache et du Dispatcher {#dispatcher-configurations-cloud}

Découvrez comment structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service, mais aussi comment valider et exécuter le service localement avant son déploiement dans les environnements cloud.

Pour plus d’informations, voir [Dispatcher en mode cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=fr).

## Convertisseur du Dispatcher AEM {#aem-dispatcher-converter}

Le convertisseur du Dispatcher AEM permet de refactoriser les configurations existantes de Dispatcher On-Premise ou Adobe Managed Services en une configuration de Dispatcher compatible AEM as a Cloud Service.

## Utilisation du convertisseur du Dispatcher AEM {#using-dispatcher-converter}

* Avec l’interface de ligne de commande d’Adobe Developer : Adobe vous recommande d’utiliser le convertisseur du Dispatcher AEM au moyen du `aio-cli-plugin-aem-cloud-service-migration` (plug-in de refactorisation du code AEM as a Cloud Service pour l’interface de ligne de commande d’Adobe Developer).

  Consultez **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour apprendre à installer et à utiliser le plug-in.

* Comme utilitaire autonome : l’outil de conversion du Dispatcher AEM peut également être exécuté comme utilitaire autonome.

  Pour en savoir plus sur l’utilisation et la résolution des problèmes de cet outil, voir **[Ressource Git : Convertisseur du Dispatcher AEM Cloud Service](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)**.

>[!IMPORTANT]
>Le convertisseur du Dispatcher AEM est développé à l’aide de NodeJS. Adobe recommande que NodeJS 10.0+ soit installé.

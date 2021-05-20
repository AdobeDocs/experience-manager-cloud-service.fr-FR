---
title: Outil convertisseur du Dispatcher AEM
description: Outil convertisseur du Dispatcher AEM
exl-id: 97eb4f3f-dc03-461a-8d7e-164065bd1e4c
source-git-commit: f6c700f82bc5a1a3edf05911a29a6e4d32dd3f72
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 100%

---

# Convertisseur du Dispatcher AEM {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="Convertisseur du Dispatcher AEM"
>abstract="Le convertisseur du Dispatcher Adobe Experience Manager convertit les configurations existantes du Dispatcher AEM en configurations du Dispatcher AEM as a Cloud Service."

Le convertisseur du Dispatcher Adobe Experience Manager convertit les configurations existantes du Dispatcher AEM en configurations du Dispatcher AEM as a Cloud Service.

## Présentation du Dispatcher {#introduction-dispatcher}

Le Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager. L’utilisation du Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Vous pouvez donc accroître la sécurité de l’instance AEM en utilisant le Dispatcher conjointement à un serveur web de niveau élevé.

>[!NOTE]
>L’utilisation la plus courante du Dispatcher consiste à mettre en cache les réponses d’une **instance de publication AEM** pour améliorer la réactivité et la sécurité du site web publié en externe.

Référez-vous à [Présentation de Dispatcher](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html) pour savoir comment le Dispatcher effectue la mise en cache, renvoie des documents et réalise l’équilibrage de charge.

### Configuration et test d’Apache et de Dispatcher {#dispatcher-configurations-cloud}

Vous devez savoir comment structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service, mais aussi comment valider et exécuter le service localement avant son déploiement dans les environnements cloud.

Pour plus d’informations, voir [Dispatcher en mode cloud](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html).

## Convertisseur du Dispatcher AEM {#aem-dispatcher-converter}

Le convertisseur du Dispatcher AEM permet de refactoriser les configurations existantes de Dispatcher On-Premise ou Adobe Managed Services en une configuration de Dispatcher compatible AEM as a Cloud Service.

## Utilisation du convertisseur du Dispatcher AEM {#using-dispatcher-converter}

* Via l’interface de ligne de commande d’Adobe I/O : il est recommandé d’utiliser le convertisseur du Dispatcher AEM via `aio-cli-plugin-aem-cloud-service-migration` (plug-in de refactorisation de code AEM as a Cloud Service pour l’interface de ligne de commande d’Adobe I/O).

   Voir la **[Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser ce module.

* Comme utilitaire autonome : l’outil de conversion de Dispatcher AEM peut également être exécuté comme utilitaire autonome.

   Pour en savoir plus sur l’utilisation et la résolution des problèmes de cet outil, voir **[Ressource Git : Convertisseur du Dispatcher AEM Cloud Service](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)**.

>[!IMPORTANT]
>Le convertisseur du Dispatcher AEM est développé à l’aide de NodeJS. Il est recommandé de disposer de NodeJS 10.0+.

---
title: Outil convertisseur du Dispatcher AEM
description: Outil convertisseur du Dispatcher AEM
translation-type: tm+mt
source-git-commit: 50d26dbec8281afec07ca56595b4b2a7b915eca9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 53%

---


# Convertisseur du Dispatcher AEM {#introduction}

Adobe Experience Manager Dispatcher Converter convertit en AEM les configurations de  Dispatcher existantes en configurations de Cloud Service Dispatcher.

## Présentation du Dispatcher {#introduction-dispatcher}

Le Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager. L’utilisation du Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Vous pouvez donc accroître la sécurité de l’instance AEM en utilisant le Dispatcher conjointement à un serveur web de niveau élevé.

>[!NOTE]
>L’utilisation la plus courante du Dispatcher consiste à mettre en cache les réponses d’une **instance de publication AEM** pour améliorer la réactivité et la sécurité du site web publié en externe.

Référez-vous à [Présentation de Dispatcher](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html) pour savoir comment le Dispatcher effectue la mise en cache, renvoie des documents et réalise l’équilibrage de charge.

### Configuration et test d’Apache et de Dispatcher {#dispatcher-configurations-cloud}

Vous devez savoir comment structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service, mais aussi comment valider et exécuter le service localement avant son déploiement dans les environnements cloud.

Pour plus d’informations, voir [Dispatcher en mode cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html).

## Convertisseur du Dispatcher AEM {#aem-dispatcher-converter}

aem Dispatcher Converter offre la possibilité de refactoriser les configurations existantes sur site ou Adobe Managed Services Dispatcher en AEM en tant que configuration de Répartiteur compatible Cloud Service.

## Utilisation du convertisseur du Dispatcher AEM {#using-dispatcher-converter}

* Par l&#39;intermédiaire de l&#39;interface de ligne de commande des E/S d&#39;Adobe : Il est recommandé d&#39;utiliser AEM Dispatcher Converter via `aio-cli-plugin-aem-cloud-service-migration` (AEM en tant que module externe de refactorisation du code Cloud Service pour l&#39;interface de ligne de commande E/S de l&#39;Adobe).

   Reportez-vous à la ressource **[Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** pour savoir comment installer et utiliser le module externe.

* En tant qu&#39;utilitaire autonome : L&#39;outil de conversion de répartiteur AEM peut également être exécuté en tant qu&#39;utilitaire autonome.

   Refer to **[Git Resource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** to learn about the usage and troubleshooting for this tool.

>[!IMPORTANT]
>aem Dispatcher Converter est développé à l&#39;aide de NodeJS. Il est recommandé d’installer NodeJS 10.0+.


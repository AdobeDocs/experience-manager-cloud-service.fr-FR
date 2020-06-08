---
title: Outil convertisseur du Dispatcher AEM
description: Outil convertisseur du Dispatcher AEM
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 100%

---


# Convertisseur du Dispatcher AEM{#introduction}

Le convertisseur du Dispatcher Adobe Experience Manager convertit les configurations existantes du Dispatcher AMS en configurations du Dispatcher AEM as a Cloud Service.

## Présentation du Dispatcher {#introduction-dispatcher}

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager. L’utilisation du Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Vous pouvez donc accroître la sécurité de l’instance AEM en utilisant le Dispatcher conjointement à un serveur web de niveau élevé.

>[!NOTE]
>L’utilisation la plus courante du Dispatcher consiste à mettre en cache les réponses d’une **instance de publication AEM** pour améliorer la réactivité et la sécurité du site web publié en externe.

Référez-vous à la section [Présentation de Dispatcher](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html) pour savoir comment le Dispatcher effectue la mise en cache, renvoie des documents et effectue l’équilibrage de charge.

### Configuration et test d’Apache et de Dispatcher {#dispatcher-configurations-cloud}

Vous devez savoir comment structurer les configurations Apache et Dispatcher d’AEM as a Cloud Service, mais aussi comment valider et exécuter le service localement avant son déploiement dans les environnements cloud.

Pour plus d’informations, voir la section [Dispatcher en mode cloud](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/dispatcher/overview.html).

## Convertisseur du Dispatcher AEM {#aem-dispatcher-converter}

Le convertisseur du Dispatcher AEM est un utilitaire permettant de convertir des configurations du Dispatcher AMS existantes en configurations du Dispatcher AEM as a Cloud Service. Cet utilitaire est destiné aux instances AMS.

Le convertisseur mis en œuvre est **AEMDispatcherConfigConverter**, en conformité avec les règles de transformation.

Reportez-vous à la section [Conversion d’une configuration AMS en configuration du Dispatcher Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/dispatcher/overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration) pour la conversion d’une configuration de Dispatcher entre AMS et Adobe Experience Manager as a Cloud Service.

## Utilisation du convertisseur du Dispatcher AEM {#using-dispatcher-converter}

La section suivante décrit les ressources et les informations requises pour utiliser le convertisseur du Dispatcher AEM.

Pour en savoir plus sur l’utilisation, les restrictions et la résolution des problèmes de cet outil, voir la section **[Ressource Git : Convertisseur du Dispatcher AEM Cloud Service](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**.

>[!IMPORTANT]
>Le convertisseur du Dispatcher AEM est développé à l’aide de Python 3.7.3. Il est recommandé d’installer Python 3.5, ou une version supérieure.

## Restrictions {#limitations}

Le convertisseur du Dispatcher AEM fonctionne en partant du principe que la structure du dossier de configuration du Dispatcher est similaire à celle décrite dans la configuration du Dispatcher Cloud Manager.



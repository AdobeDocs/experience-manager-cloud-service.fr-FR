---
title: Outil de conversion du répartiteur AEM
description: Outil de conversion du répartiteur AEM
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 17%

---


# Convertisseur répartiteur AEM {#introduction}

Adobe Experience Manager Dispatcher Converter convertit les configurations existantes du répartiteur AMS en AEM en tant que configurations du répartiteur de services Cloud.

## Présentation du répartiteur {#introduction-dispatcher}

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager. L’utilisation de Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Par conséquent, vous pouvez augmenter la sécurité de l’instance AEM en utilisant Dispatcher conjointement à un serveur web de niveau élevé.

>[!NOTE]
>The most common use of Dispatcher is to cache responses from an **AEM publish instance**, to increase the responsiveness and security of your externally facing published website.

Reportez-vous à la section Présentation [du](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html) répartiteur pour savoir comment le répartiteur effectue la mise en cache, renvoie des documents et effectue l’équilibrage de charge.

### Apache and Dispatcher Configuration and Testing {#dispatcher-configurations-cloud}

Vous devez apprendre à structurer AEM en tant que configurations Apache et Répartiteur de services Cloud, ainsi qu’à valider et à exécuter localement avant de procéder au déploiement sur des environnements Cloud.

Pour plus d’informations, voir [Répartiteur dans le Cloud](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/dispatcher/overview.html) .

## Convertisseur répartiteur AEM {#aem-dispatcher-converter}

AEM Dispatcher Converter est un utilitaire permettant de convertir des configurations de répartiteur AMS existantes en AEM en configurations de répartiteur de services Cloud. Cet utilitaire est destiné aux instances AMS.

Le convertisseur mis en oeuvre est **AEMDispatcherConfigConverter** qui suit les directives de transformation.

Reportez-vous à la section [Conversion d’un fichier AMS en un Adobe Experience Manager en tant que configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/dispatcher/overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration) du répartiteur de services Cloud pour la conversion d’un fichier AMS en un fichier Adobe Experience Manager en tant que configuration du répartiteur de services Cloud.

## Utilisation du convertisseur de répartiteur AEM {#using-dispatcher-converter}

La section suivante décrit les ressources et les informations requises pour utiliser l’outil AEM Dispatcher Converter.

Reportez-vous à la ressource **[Git : Convertisseur](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**de répartiteur de services AEM Cloud pour en savoir plus sur l’utilisation, les restrictions et la résolution des problèmes de cet outil.

>[!IMPORTANT]
>AEM Dispatcher Converter est développé à l&#39;aide de Python 3.7.3. Il est recommandé d&#39;installer Python 3.5 ou version supérieure.

## Restrictions {#limitations}

AEM Dispatcher Converter fonctionne en partant du principe que la structure du dossier de configuration du répartiteur fourni est similaire à celle décrite dans la configuration du répartiteur Cloud Manager.



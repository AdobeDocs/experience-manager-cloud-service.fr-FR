---
title: Phase de post-activation
description: Phase de post-activation
translation-type: tm+mt
source-git-commit: 0565d053b6040bc99ae79823711d56eb9aecdfb3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 82%

---


# Post-activation {#post-go-live}

Lors de la phase de post-activation, vous devez veiller à nettoyer les fichiers temporaires, revoir les bonnes pratiques de développement continu et gérer les journaux.

Les outils suivants sont disponibles pour résoudre les problèmes liés aux environnements AEM as a Cloud Service :

* **Developer Console**
* **CRX/DE Lite**
* **Gestion des journaux**


## Developer Console {#developer-console}

Des environnements de débogage pour développeur d’AEM as a Cloud Service sont disponibles dans Developer Console pour les environnements de développement, d’évaluation et de production.

Pour en savoir plus sur les outils de développement, voir [Implémentation pour AEM as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools).

## CRX/DE Lite {#crxde-lite}

En tant qu&#39;utilisateur, vous pouvez accéder à CRX/DE Lite sur l&#39;environnement de développement mais pas sur l&#39;étape ou la production.

>[IMPORTANT]
>L’écriture, au moment de l’exécution, dans des référentiels non modifiables tels que `/libs` et `/apps`, entraîne des erreurs. En outre, en tant que client, vous n’aurez pas accès aux outils de développement pour les environnements d’évaluation et de production.

Refer to [Developing with CRX/DE Lite](https://docs.adobe.com/help/fr-FR/experience-manager-65/developing/devtools/developing-with-crxde-lite.html) to learn how to develop your AEM application using CRX/DE Lite.

## Gestion des journaux {#managing-logs}

Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Pour savoir comment accéder aux journaux et les gérer via l’interface utilisateur ou à l’aide d’une API via Cloud Manager, voir [Accès aux journaux et leur gestion](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html).

### Assistance supplémentaire {#additional-support}

Si vous avez des questions concernant l’accès à Cloud Service, contactez votre représentant Adobe ou rendez-vous sur le portail d’assistance Adobe AEM CQ.

---
title: Phase post-migration
description: Phase post-migration
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 100%

---


# Post-migration {#post-migration}

Lors de la phase post-migration, vous devez veiller à nettoyer les fichiers temporaires, revoir les bonnes pratiques de développement continu et gérer les journaux.

Les outils suivants sont disponibles pour résoudre les problèmes liés aux environnements AEM as a Cloud Service :

* **Console développeur**
* **CRXDE Lite**
* **Gestion des journaux**


## Console développeur {#developer-console}

Un ensemble d’outils pour le débogage des environnements de développeur d’AEM as a Cloud Service est disponible dans la Console développeur pour les environnements de développement, d’évaluation et de production.

Pour en savoir plus sur les outils de développement, voir la section [Implémentation pour AEM as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools).

## CRXDE Lite {#crxde-lite}

En tant qu’utilisateur, vous pouvez accéder à **CRXDE Lite** dans l’environnement de développement, mais pas dans les environnements d’évaluation ou de production.

>[IMPORTANT]
>L’écriture, au moment de l’exécution, dans des référentiels non modifiables tels que `/libs` et `/apps` entraîne des erreurs. En outre, en tant que client, vous n’aurez pas accès aux outils de développement pour les environnements d’évaluation et de production.

Pour savoir comment développer votre application AEM à l’aide de CRXDE Lite, voir la section [Développement dans CRXDE Lite](https://docs.adobe.com/help/fr-FR/experience-manager-65/developing/devtools/developing-with-crxde-lite.html).

## Gestion des journaux {#managing-logs}

Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Pour savoir comment accéder aux journaux et les gérer via l’interface utilisateur ou à l’aide d’une API via Cloud Manager, voir la section [Accès aux journaux et leur gestion](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html).

### Assistance supplémentaire {#additional-support}

Si vous avez des questions concernant l’accès à Cloud Service, contactez votre représentant Adobe ou votre portail d’assistance Adobe AEM CQ.

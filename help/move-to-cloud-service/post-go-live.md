---
title: Phase de post-activation
description: Phase de post-activation
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 9%

---


# Post Go-live {#post-go-live}

Au cours de la phase post-mise en service, vous devriez veiller à nettoyer les fichiers temporaires, examiner les meilleures pratiques en matière de développement continu et gérer les journaux.

Les outils suivants sont disponibles pour résoudre les problèmes liés à AEM en tant qu’environnements de service Cloud :

* **Console Développeur**
* **CRXDE Lite**
* **Gestion des journaux**


## Console Développeur {#developer-console}

Le débogage d’AEM en tant qu’environnements de développement de services Cloud est disponible dans la Console développeur pour les environnements de développement, d’évaluation et de production.

Reportez-vous à [Mise en oeuvre d’AEM en tant que service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools) Cloud pour en savoir plus sur les outils de développement.

## CRXDE Lite {#crxde-lite}

En tant qu’utilisateur, vous pouvez accéder à **CRXDE Lite** sur l’environnement de développement, mais pas sur l’étape ou la production.

>[IMPORTANT]
>L&#39;écriture sur des référentiels immuables tels que `/libs` et `/apps` au moment de l&#39;exécution entraîne des erreurs. En outre, en tant que client, vous n’aurez pas accès à l’outil de développement pour les environnements d’évaluation et de production.

Reportez-vous à la section [Développement avec CRXDE Lite](https://docs.adobe.com/help/en/experience-manager-65/developing/devtools/developing-with-crxde-lite.html) pour savoir comment développer votre application AEM à l’aide de CRXDE Lite.

## Gestion des journaux {#managing-logs}

Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Reportez-vous à la section [Accès et gestion des journaux](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) pour savoir comment accéder aux journaux et les gérer via l’interface utilisateur ou depuis l’API via Cloud Manager.

### Assistance supplémentaire {#additional-support}

Si vous avez des questions sur l’accès au service Cloud, contactez votre représentant Adobe ou votre portail d’assistance Adobe AEM CQ.

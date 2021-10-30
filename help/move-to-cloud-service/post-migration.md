---
title: Phase post-migration
description: Phase post-migration
source-git-commit: 6fcde5440a5e2eec57b69b14dca93192634b3c3a
workflow-type: ht
source-wordcount: '222'
ht-degree: 100%

---


# Post-migration {#post-migration}

Lors de la phase post-migration, vous devez veiller à nettoyer les fichiers temporaires, revoir les bonnes pratiques de développement continu et gérer les journaux.

Les outils suivants sont disponibles pour résoudre les problèmes liés aux environnements AEM as a Cloud Service :

* **Developer Console**
* **CRXDE Lite**
* **Gestion des journaux**

## Developer Console {#developer-console}

Des environnements de débogage pour développeur d’AEM as a Cloud Service sont disponibles dans Developer Console pour les environnements de développement, d’évaluation et de production.

Pour en savoir plus sur les outils de développement, voir [Implémentation pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#aem-as-a-cloud-service-development-tools).

## CRXDE Lite {#crxde-lite}

En tant qu’utilisateur, vous pouvez accéder à **CRXDE Lite** dans l’environnement de développement, mais pas dans les environnements d’évaluation ni de production.

>[!IMPORTANT]
>L’écriture, au moment de l’exécution, dans des référentiels non modifiables tels que `/libs` et `/apps`, entraîne des erreurs. En outre, en tant que client, vous n’aurez pas accès aux outils de développement pour les environnements d’évaluation et de production.

Pour savoir comment développer votre application AEM à l’aide de CRXDE Lite, voir [Développement dans CRXDE Lite](/help/implementing/developing/tools/crxde.md).

## Gestion des journaux {#managing-logs}

Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Pour savoir comment accéder aux journaux et les gérer via l’interface utilisateur ou à l’aide d’une API via Cloud Manager, voir [Accès aux journaux et leur gestion](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=fr).

### Assistance supplémentaire {#additional-support}

Si vous avez des questions concernant l’accès à Cloud Service, contactez votre représentant Adobe ou rendez-vous sur le portail d’assistance Adobe AEM CQ.

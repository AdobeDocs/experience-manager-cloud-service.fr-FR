---
title: Phase de post-activation
description: Phase de post-activation
exl-id: f9b0b2fa-e29c-4faa-a5e7-e5edd04b25ca
source-git-commit: 6fcde5440a5e2eec57b69b14dca93192634b3c3a
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 70%

---

# Publication activée {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Résolution des incidents liés à AEM"
>abstract="Consultez les bonnes pratiques de développement continu et gérez les journaux avec des outils tels que Developer Console et CRXDE Lite pour résoudre les problèmes liés à AEM"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html" text="Accès aux journaux et leur gestion"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools" text="Outils de développement AEM as a Cloud Service"


Lors de la phase de post-activation, vous devez veiller à nettoyer les fichiers temporaires, revoir les bonnes pratiques de développement continu et gérer les journaux.

Les outils suivants sont disponibles pour résoudre les problèmes liés aux environnements AEM as a Cloud Service :

* **Developer Console**
* **CRX/DE Lite**
* **Gestion des journaux**


## Developer Console {#developer-console}

Des environnements de débogage pour développeur d’AEM as a Cloud Service sont disponibles dans Developer Console pour les environnements de développement, d’évaluation et de production.

Pour en savoir plus sur les outils de développement, voir [Implémentation pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools).

## CRX/DE Lite {#crxde-lite}

En tant qu’utilisateur, vous pouvez accéder à CRX/DE Lite dans l’environnement de développement, mais pas dans les environnements d’évaluation ni de production.

>[!IMPORTANT]
>L’écriture, au moment de l’exécution, dans des référentiels non modifiables tels que `/libs` et `/apps`, entraîne des erreurs. En outre, en tant que client, vous n’aurez pas accès aux outils de développement pour les environnements d’évaluation et de production.

Pour savoir comment développer votre application AEM avec CRX/DE Lite, voir [Développement dans CRX/DE Lite](/help/implementing/developing/tools/crxde.md).

## Gestion des journaux {#managing-logs}

Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Pour savoir comment accéder aux journaux et les gérer via l’interface utilisateur ou à l’aide d’une API via Cloud Manager, voir [Accès aux journaux et leur gestion](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=fr).

### Assistance supplémentaire {#additional-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Aide et assistance"
>abstract="Contactez notre équipe d’assistance AEM pour obtenir des éclaircissements ou pour répondre à toute question."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Prise en charge de l’Experience Cloud"

Si vous avez des questions sur l’accès à Cloud Service, contactez votre représentant d’Adobe ou [Assistance pour les Experience Cloud](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour plus d’informations.

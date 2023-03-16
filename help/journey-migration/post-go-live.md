---
title: Post-activation
description: Découvrez comment surveiller les problèmes et améliorer les performances
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---

# Post-activation {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Résolution des incidents liés à AEM"
>abstract="Consultez les bonnes pratiques de développement continu et gérez les journaux avec des outils tels que Developer Console et CRXDE Lite pour résoudre les problèmes liés à AEM"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=fr" text="Accès aux journaux et leur gestion"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#aem-as-a-cloud-service-development-tools" text="Outils de développement AEM as a Cloud Service"

Il s’agit de la dernière partie du parcours. Vous apprendrez ainsi à surveiller les problèmes et à améliorer les performances une fois la migration terminée. Vous devez veiller au nettoyage des fichiers temporaires, revoir les bonnes pratiques de développement continu et gérer les journaux.

## Un peu d’histoire… {#story-so-far}

À l’étape précédente du parcours, vous avez appris à effectuer la migration et à [Activer](/help/journey-migration/go-live.md) une fois le code et le contenu prêts à être déplacés vers AEM as a Cloud Service.

## Objectif {#objective}

Ce document décrit les outils disponibles pour résoudre les problèmes des environnements AEM as a Cloud Service :

* **Developer Console**
* **CRXDE Lite**
* **Gestion des journaux**

## Developer Console {#developer-console}

Le débogage des environnements de développeur d’AEM as a Cloud Service est disponible dans Developer Console pour les environnements de développement, d’évaluation et de production.

Pour en savoir plus sur les outils de développement, consultez la section [Implémenter pour AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools).

## CRXDE Lite {#crxde-lite}

En tant qu’utilisateur, vous pouvez accéder à CRXDE Lite dans l’environnement de développement, mais pas dans les environnements d’évaluation ni de production.

>[!IMPORTANT]
>L’écriture, au moment de l’exécution, dans des référentiels non modifiables tels que `/libs` et `/apps`, entraîne des erreurs. De plus, vous n’avez pas accès aux outils de développement pour les environnements d’évaluation et de production.

Pour savoir comment développer votre application AEM à l’aide de CRXDE Lite, consultez la section [Développer dans CRXDE Lite](/help/implementing/developing/tools/crxde.md).

## Gestion des journaux {#managing-logs}

Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Pour savoir comment accéder aux journaux et les gérer via l’interface utilisateur ou à l’aide d’une API via Cloud Manager, voir [Accès aux journaux et leur gestion](/help/implementing/cloud-manager/manage-logs.md).

## Contacter l’assistance {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Aide et assistance"
>abstract="Contactez notre équipe d’assistance AEM pour obtenir des clarifications ou des réponses à vos questions."
>additional-url="https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html" text="Assistance technique pour Experience Cloud"

Si vous avez des questions sur l’accès à Cloud Service, contactez votre représentant Adobe ou [l’Assistance pour Experience Cloud](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour plus d’informations.

## Apprentissage de documents {#document-learnings}

Une fois la migration terminée, vous devez documenter les connaissances acquises au cours de ce processus. Voici quelques questions qui peuvent faciliter le processus de documentation :

* Qu’est-ce qui a bien fonctionné et qu’est-ce qui n’a pas fonctionné ?
* Quels ont été les principaux problèmes ?
* Recommandations en cas de migration ultérieure.

Vous devez ensuite partager ces apprentissages post-migration avec les parties prenantes et les équipes de votre entreprise.

## Serait-ce la fin de notre voyage ?  {#journey-ends}

Félicitations ! Vous avez terminé le parcours de migration d’AEM as a Cloud Service ! Vous devez comprendre comment :

* Prendre en main la transition vers AEM as a Cloud Service.
* Déterminer si votre déploiement est prêt à être déplacé vers AEM as a Cloud Service.
* Préparer votre code et votre contenu pour le cloud.
* Effectuer la migration.
* Surveiller les problèmes et améliorer les performances

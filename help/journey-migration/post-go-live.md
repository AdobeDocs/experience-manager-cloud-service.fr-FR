---
title: Post-activation
description: Découvrez comment surveiller les problèmes et améliorer les performances.
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
feature: Migration
role: Admin
source-git-commit: bb2688701b80a560ea9078c2b7b6594ff55ce824
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 64%

---

# Post-activation {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Résolution des incidents liés à AEM"
>abstract="Examinez les bonnes pratiques pour le développement et la gestion continus des journaux. Découvrez des outils tels que Developer Console et CRXDE Lite pour vous aider à résoudre les problèmes liés à AEM."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs" text="Accéder aux journaux et les gérer"
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#aem-as-a-cloud-service-development-tools" text="Outils de développement AEM as a Cloud Service"

Ce parcours est la dernière partie. Vous apprenez donc à surveiller les problèmes et à améliorer les performances une fois la migration terminée. Assurez le nettoyage des fichiers temporaires, passez en revue les bonnes pratiques de développement continu et gérez les journaux.

## Un peu d’histoire… {#story-so-far}

À l’étape précédente du parcours, vous avez appris à effectuer la migration et à [Activer](/help/journey-migration/go-live.md) une fois le code et le contenu prêts à être déplacés vers AEM as a Cloud Service.

## Objectif {#objective}

Ce document décrit les outils disponibles pour résoudre les problèmes des environnements AEM as a Cloud Service :

* **Developer Console**
* **CRXDE Lite**
* **Gestion des journaux**

## Developer Console {#developer-console}

Le débogage des environnements de développeur d’AEM as a Cloud Service est disponible dans Developer Console pour les environnements de développement, d’évaluation et de production.

Pour en savoir plus sur les outils de développement, consultez la section [Implémentation pour AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools).

## CRXDE Lite {#crxde-lite}

En tant qu’utilisateur, vous pouvez accéder à CRXDE Lite dans l’environnement de développement, mais pas dans les environnements intermédiaire ou de production.

>[!IMPORTANT]
>L’écriture dans des référentiels non modifiables, tels que `/libs` et `/apps` au moment de l’exécution, entraîne des erreurs. En outre, vous n’avez pas accès aux outils de développement pour les environnements d’évaluation et de production.

Voir [Développement avec CRXDE Lite](/help/implementing/developing/tools/crxde.md) pour plus d’informations sur la manière de développer votre application AEM à l’aide de CRXDE Lite.

## Gestion des journaux {#managing-logs}

Les utilisateurs et utilisatrices peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Voir [Accès aux journaux et leur gestion](/help/implementing/cloud-manager/manage-logs.md) pour savoir comment accéder aux journaux et les gérer à l’aide de l’interface utilisateur ou de l’API par le biais de Cloud Manager.

## Contacter l’assistance {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Aide et assistance"
>abstract="Contactez l’équipe d’assistance AEM d’Adobe pour obtenir des éclaircissements ou pour répondre à toute question."
>additional-url="https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html" text="Assistance technique pour Experience Cloud"

Si vous avez des questions sur l’accès à Cloud Service, contactez votre représentant Adobe ou [l’Assistance pour Experience Cloud](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour plus d’informations.

## Apprentissage de documents {#document-learnings}

Une fois la migration terminée, documentez les connaissances acquises au cours de ce processus. Voici quelques questions qui peuvent faciliter le processus de documentation :

* Qu’est-ce qui a bien fonctionné et qu’est-ce qui n’a pas fonctionné ?
* Quels ont été les principaux problèmes ?
* Recommendations en cas de migration ultérieure.

Partagez ces leçons post-migration avec les parties prenantes et les équipes de votre entreprise.

## Serait-ce la fin de notre voyage ?  {#journey-ends}

Félicitations ! Vous avez terminé le parcours de migration d’AEM as a Cloud Service ! Vous devez comprendre comment :

* Prendre en main la transition vers AEM as a Cloud Service.
* Déterminer si votre déploiement est prêt à être déplacé vers AEM as a Cloud Service.
* Préparer votre code et votre contenu pour le cloud.
* Effectuer la migration.
* Surveiller les problèmes et améliorer les performances

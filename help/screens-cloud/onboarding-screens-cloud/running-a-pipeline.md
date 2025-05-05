---
title: Exécution d’un pipeline
description: Cette page décrit l’exécution d’un pipeline pour un projet Screens as a Cloud Service dans Cloud Manager.
exl-id: 3203cff7-5668-4f50-a2c5-80ae474b439d
feature: Screens Deployments
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 91%

---

# Exécution d’un pipeline pour programme Screens as a Cloud Service dans Cloud Manager {#run-pipeline-screens-cloud}

Cette section décrit comment exécuter le pipeline et déployer le code pour votre programme dans Cloud Manager.

>[!NOTE]
>Voir [Configuration de votre pipeline CI-CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html?lang=fr) et [Déployer votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=fr) pour savoir comment exécuter le pipeline pour votre programme dans Cloud Manager.

## Objectif {#objective}

La section suivante décrit comment configurer le pipeline CI/CD et déployer votre code pour votre programme dans Cloud Manager.

## Étapes d’exécution d’un pipeline pour votre projet Screens dans Cloud Manager {#steps-branch-creation}

1. Une fois la configuration de l’environnement terminée, la mise à jour de la carte d’appel à l’action s’affiche sur la page **Aperçu** de Cloud Manager.

   ![image](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. Cliquez sur **Configurer un pipeline** sur la page **Vue d’ensemble**.

1. Cliquez sur **Suivant** après avoir sélectionné la branche.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. Sélectionnez vos options dans l’assistant **Configurer le pipeline**. Cliquez sur **Enregistrer**.

   >[!NOTE]
   >Pour en savoir plus sur les options de l’assistant de configuration du pipeline, voir [Configuration des paramètres du pipeline à partir de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/configuring-production-pipelines.html?lang=fr) pour plus d’informations.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. Une fois le pipeline de configuration terminé, la carte d’appel à l’action est mise à jour.

   >[!NOTE]
   >Pour en savoir plus sur les étapes du déploiement dans Cloud Manager, voir [Déploiement de votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=fr) pour plus d’informations.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. Cliquez sur **Déployer**.

1. Cliquez sur **Créer** pour lancer le processus de création.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. Une fois le processus de création terminé, vous pouvez voir un lien d’auteur à partir de la carte **Environments** de la page **Overview** de Cloud Manager.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## Prochaines étapes {#whats-next}

Une fois que vous avez appris à configurer un environnement pour votre programme dans Cloud Manager, vous pouvez passer à l’étape suivante du processus d’intégration : [Accès au fournisseur de services Screens](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md).

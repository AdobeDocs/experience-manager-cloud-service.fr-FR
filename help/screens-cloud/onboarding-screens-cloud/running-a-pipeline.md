---
title: Exécution d’un pipeline
description: Cette page décrit l’exécution d’un pipeline pour un projet Screens as a Cloud Service dans Cloud Manager.
source-git-commit: b9b27c09b1f4a1799a8c974dfb846295664be998
workflow-type: ht
source-wordcount: '320'
ht-degree: 100%

---


# Exécution d’un pipeline pour programme Screens as a Cloud Service dans Cloud Manager {#run-pipeline-screens-cloud}

Cette section décrit comment exécuter le pipeline et déployer le code pour votre programme dans Cloud Manager.

>[!NOTE]
>Voir [Configuration de votre pipeline CD-CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=fr) et [Déployer votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr) pour savoir comment exécuter le pipeline pour votre programme dans Cloud Manager.

## Objectif {#objective}

La section suivante décrit comment configurer le pipeline CI/CD et déployer votre code pour votre programme dans Cloud Manager.

## Étapes d’exécution d’un pipeline pour votre projet Screens dans Cloud Manager {#steps-branch-creation}

1. Une fois la configuration de l’environnement terminée, la mise à jour de la carte d’appel à l’action s’affiche sur la page **Aperçu** de Cloud Manager.

   ![image](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. Cliquez sur **Configurer un pipeline** dans la page **Aperçu**.

1. Cliquez sur **Suivant** après avoir sélectionné la branche.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. Sélectionnez vos options dans l’assistant **Configurer le pipeline**. Cliquez sur **Enregistrer**.

   >[!NOTE]
   >Pour en savoir plus sur les options de l’assistant de configuration du pipeline, voir [Configuration des paramètres du pipeline à partir de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=fr) pour plus d’informations.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. Une fois le pipeline de configuration terminé, la carte d’appel à l’action est mise à jour, comme illustré ci-dessous. Cliquez sur Déployer.

   >[!NOTE]
   >Pour en savoir plus sur les étapes du déploiement dans Cloud Manager, voir [Déploiement de votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr) pour plus d’informations.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. Cliquez sur **Générer** pour lancer le processus de création.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. Une fois le processus de création terminé, un lien d’auteur s’affiche à partir de la carte **Environnements** de la page **Aperçu** de Cloud Manager.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## Et après ? {#whats-next}

Une fois que vous avez appris à configurer un environnement pour votre programme dans Cloud Manager, vous êtes prêt à passer à l’étape suivante du processus d’intégration : [Accès au fournisseur de services Screens](/help/screens-cloud/configuring/navigating-to-screens-services-provider.md).
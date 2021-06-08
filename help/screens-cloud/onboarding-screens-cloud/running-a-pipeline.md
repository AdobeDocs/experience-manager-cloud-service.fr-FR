---
title: Exécution d’un pipeline
description: Cette page décrit l’exécution d’un pipeline pour Screens en tant que projet Cloud Service dans Cloud Manager.
hide: true
hidefromtoc: true
index: false
source-git-commit: 371cfaeb0e526197fdf98dea65ed5bc2ca0481a2
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 7%

---


# Exécution d’un pipeline pour Screens en tant que programme de Cloud Service dans Cloud Manager {#run-pipeline-screens-cloud}

Cette section décrit comment exécuter le pipeline et déployer le code correspondant à votre programme dans Cloud Manager.

>[!NOTE]
>Voir [Configuration de votre pipeline CD-CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) et [Déployer votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr) pour savoir comment exécuter le pipeline pour votre programme dans Cloud Manager.

## Intention {#objective}

La section suivante décrit comment configurer le pipeline CI/CD et déployer votre code pour votre programme dans Cloud Manager.

## Étapes d’exécution d’un pipeline pour votre projet Screens dans Cloud Manager {#steps-branch-creation}

1. Une fois la configuration de l’environnement terminée, la mise à jour de la carte d’appel à l’action s’affiche sur la page **Aperçu** de Cloud Manager.

   ![image](/help/screens-cloud/assets/onboarding/add-environ3.png)

1. Cliquez sur **Configurer un pipeline** dans la page **Aperçu**.

1. Cliquez sur **Suivant** après avoir sélectionné la branche.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline1.png)

1. Sélectionnez vos options dans l’assistant **Configurer le pipeline**. Cliquez sur **Enregistrer**.

   >[!NOTE]
   >Pour en savoir plus sur les options de l’assistant de configuration du pipeline, voir [Configuration des paramètres du pipeline à partir de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en) pour plus d’informations.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline2-a.png)

1. Une fois le pipeline de configuration terminé, la carte d’appel à l’action est mise à jour, comme illustré dans la figure ci-dessous. Cliquez sur Déployer.

   >[!NOTE]
   >Pour en savoir plus sur les étapes du déploiement dans Cloud Manager, voir [Déploiement de votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en) pour plus d’informations.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline3.png)

1. Cliquez sur **Build** pour lancer le processus de création.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline4.png)

1. Une fois le processus de création terminé, un lien d’auteur s’affiche à partir de la carte **Environnements** de la page **Aperçu** de Cloud Manager.

   ![image](/help/screens-cloud/assets/onboarding/run-pipeline5.png)

## Suite {#whats-next}

Une fois que vous avez appris à exécuter le pipeline pour votre programme dans Cloud Manager, vous êtes prêt à passer à l’étape suivante. L’étape suivante est Configuration et configuration de votre projet Screens.
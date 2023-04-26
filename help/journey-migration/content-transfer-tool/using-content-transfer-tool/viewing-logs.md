---
title: Affichage des journaux d’un jeu de migration dans l’outil de transfert de contenu
description: Affichage des journaux d’un jeu de migration dans l’outil de transfert de contenu
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
source-git-commit: 9d236e459f13fec6f0aaf80f588d20760636b9bb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Affichage des journaux d’un jeu de migration {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Affichage des journaux"
>abstract="Une fois l’extraction de l’ingestion terminée, recherchez dans les journaux les erreurs/avertissements éventuels. Toute erreur doit être corrigée immédiatement soit en traitant les problèmes signalés, soit en contactant l’assistance d’Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#troubleshooting?lang=fr" text="Résolution des problèmes"
>additional-url="https://helpx.adobe.com/ca/enterprise/using/support-for-experience-cloud.html" text="Contacter le support technique d’Adobe"

Une fois chaque étape terminée (extraction et ingestion), vérifiez les journaux et recherchez les erreurs.  Toute erreur doit être corrigée immédiatement soit en traitant les problèmes signalés, soit en contactant l’assistance d’Adobe.

## Procédure d’affichage des journaux {#viewing-logs}

### Journaux d’extraction

Pour afficher les journaux d’extraction, accédez à votre instance source Adobe Experience Manager, puis sélectionnez le jeu de migration souhaité.

Suivez ensuite les étapes ci-dessous :

1. Sélectionnez un jeu de migration et cliquez sur **Afficher le journal** dans la barre d’actions. La boîte de dialogue Journaux s’affiche. Cliquez sur **Journaux d’extraction** pour afficher les journaux dans un nouvel onglet.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam25.png) \
   Ou cliquez sur le statut **TERMINÉ** pour afficher les journaux dans un nouvel onglet.

1. Pour consulter les dernières lignes des journaux sans utiliser l’interface utilisateur, vous pouvez vous connecter à votre environnement AEM source via SSH et exécuter la commande tail sur le fichier `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.

### Journaux d’ingestion

Pour afficher les journaux d’ingestion, accédez à la liste Tâches d’ingestion dans Cloud Acceleration Manager, puis recherchez la tâche de migration souhaitée et cliquez sur les trois points (**...**) de la tâche. Vous pouvez ensuite cliquer sur **Télécharger les journaux**.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam28.png)

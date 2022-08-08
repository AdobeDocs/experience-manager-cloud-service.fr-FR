---
title: Affichage des journaux d’un jeu de migration dans l’outil de transfert de contenu (hérité)
description: Affichage des journaux d’un jeu de migration dans l’outil de transfert de contenu
hide: true
hidefromtoc: true
exl-id: 01c8afd3-c594-4a41-b905-8c3a2d74db6f
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Affichage des journaux d’un jeu de migration (hérité) {#view-logs-content-transfer-tool}

Une fois chaque étape terminée (extraction et ingestion), vérifiez les journaux et recherchez les erreurs.  Toute erreur doit être corrigée immédiatement soit en traitant les problèmes signalés, soit en contactant l’assistance d’Adobe.

## Procédure d’affichage des journaux {#viewing-logs}

Vous pouvez afficher les journaux d’un jeu de migration existant à l’aide de la page *Overview*.
Suivez les étapes ci-dessous :

1. Accédez à la page *Overview*, sélectionnez le jeu de migration à supprimer, puis cliquez sur l’option **View Log** (Afficher le journal) dans la barre d’actions.

   ![image](/help/journey-migration/content-transfer-tool/assets/view-log1.png)

1. La boîte de dialogue **Logs** (Journaux) s’affiche. Cliquez sur **Extraction Logs** (Journaux d’extraction) pour voir les journaux dans un nouvel onglet.

   ![image](/help/journey-migration/content-transfer-tool/assets/view-log2.png)
ou,

   Vous pouvez également voir les journaux de votre jeu de migration à l’aide de l’écran *Overview*. Sélectionnez le jeu de migration et cliquez sur l’état sous le champ **EXTRACTION**. Dans ce cas, cliquez sur **FINISHED** (TERMINÉ) pour voir les journaux dans un nouvel onglet.

   ![image](/help/journey-migration/content-transfer-tool/assets/view-log3.png)

1. Pour consulter les dernières lignes des journaux sans utiliser l’interface utilisateur, vous pouvez vous connecter à votre environnement AEM source via SSH et exécuter la commande tail sur le fichier `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`.

---
title: Restaurer le code Source précédent déployé
description: Découvrez comment restaurer un environnement à sa dernière version &ndash; réussie ; aucune exécution de pipeline requise.
feature: Operations
role: Admin
badge: label="Alpha" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
source-git-commit: ae90f527d398af40cf9e6963d2e27de3368f2e8f
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 3%

---

# Restaurer le code source précédent déployé dans AEM as a Cloud Service {#restore-previous-code-deployed}

>[!NOTE]
>
>>La fonctionnalité décrite dans cet article n’est disponible que via le programme Alpha destiné aux utilisateurs et utilisatrices précoces. Pour vous inscrire à la version alpha, consultez [Restauration en un clic pour les déploiements de pipeline](/help/implementing/cloud-manager/release-notes/current.md##one-click-rollback).

Utilisez **Restaurer le code précédemment déployé** pour restaurer instantanément un environnement à sa dernière version réussie, aucune exécution de pipeline n’étant requise.

Il vous suffit d’ouvrir le menu ![Icône Plus ou icône du menu représentant des points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) de l’environnement sélectionné, puis de choisir **Restaurer** > **Code précédent déployé** pour restaurer le code source le plus récemment déployé en secondes.

>[!TIP]
>
>Vous pouvez afficher la version de code source active utilisée dans la vue des détails de l’environnement, sous l’onglet **Général**. Voir [Affichage des détails d’un environnement](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).
>
>![Version du code Source utilisée](/help/operations/assets/environments-view-details-sourcecodeversion.png)

La fonctionnalité **Restaurer le code précédent déployé** n’est disponible que lorsque **chaque** condition ci-dessous est remplie :

* Vous détenez l’autorisation **Créer une restauration d’environnement**. Pour plus d’informations sur la gestion des autorisations, voir [Autorisations personnalisées](/help/implementing/cloud-manager/custom-permissions.md).
* Votre entreprise est inscrite au programme des utilisateurs et utilisatrices précoces et l’indicateur de fonctionnalité est activé.
* Le programme s&#39;exécute sur **AEM as a Cloud Service**.
* L&#39;environnement choisi est un environnement **DEV** (limite temporaire d&#39;Alpha).
* Le dernier pipeline pour cet environnement s’est terminé **avec succès** et s’est exécuté **il y a moins de 10 jours**.
* Le statut de l’environnement est **En cours d’exécution** et aucun pipeline n’est en cours.
* La version du code source cible que vous souhaitez restaurer a été déployée **dans les 30 jours**.

Si une vérification échoue, Cloud Manager ouvre la boîte de dialogue suivante qui répertorie une ou plusieurs conditions non remplies et désactive **Confirmer**, empêchant la restauration.

![Boîte de dialogue Restaurer le code précédent déployé en échec](/help/operations/assets/restore-previous-code-deployment-not-allowed.png).

Si vous souhaitez simplement restaurer les données perdues, endommagées ou supprimées accidentellement à leur état d’origine, vous pouvez utiliser [Restaurer le contenu dans AEM as a Cloud Service](/help/operations/restore.md). Ce processus de restauration affecte uniquement le contenu, laissant votre code source et votre version d’AEM inchangés.

**Pour restaurer le code précédemment déployé, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez lancer une restauration.

1. Répertoriez tous les environnements du programme en effectuant l’une des opérations suivantes :

   * Dans le menu de gauche, sous **Services**, cliquez sur ![Icône Données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**.

     ![Onglet Environnements](assets/environments-1.png)

   * Dans le menu de gauche, sous **Programme**, cliquez sur **Aperçu**, puis, dans la vignette **Environnements**, cliquez sur ![Icône de workflow](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Tout afficher**.

     ![Option Tout afficher](assets/environments-2.png)

     >[!NOTE]
     >
     >La carte **Environnements** répertorie uniquement trois environnements. Cliquez sur **Tout afficher** dans la carte pour afficher *tous* les environnements du programme.

1. Dans le tableau Environnements , à droite d’un environnement dont vous souhaitez restaurer le code source, cliquez sur ![icône Plus ou icône de menu représentant des points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), puis cliquez sur **Restaurer** > **Code précédent déployé**.

   ![Option Restaurer le code déployé précédent à partir du menu représentant des points de suspension](/help/operations/assets/restore-previous-code-deployed-menu.png)

1. Dans la boîte de dialogue **Restaurer le code déployé précédent**, passez en revue la version actuellement déployée et la version à restaurer, puis cliquez sur **Confirmer**.

   ![Boîte de dialogue Restaurer le code déployé précédent](/help/operations/assets/restore-previous-code-deployed-dialogbox.png)

1. Cloud Manager restaure l’environnement à sa version précédente, conserve le contenu et la configuration intacts, et marque l’environnement **Restauration** sur la page Environnements jusqu’à ce que le déploiement soit terminé.

   ![Restauration de l’activation](/help/operations/assets/restore-previous-code-deployed-restoring.png)

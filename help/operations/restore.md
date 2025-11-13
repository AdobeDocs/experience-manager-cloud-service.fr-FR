---
title: Restaurer du contenu dans AEM as a Cloud Service
description: Découvrez comment restaurer votre contenu AEM as a Cloud Service à partir de la sauvegarde à l’aide de Cloud Manager.
exl-id: 921d0c5d-5c29-4614-ad4b-187b96518d1f
feature: Operations
role: Admin
source-git-commit: 4008b2f81bbd81cef343c6d2b04ba536b66d7d89
workflow-type: tm+mt
source-wordcount: '1358'
ht-degree: 24%

---


# Restaurer du contenu dans AEM as a Cloud Service {#content-restore}

Vous pouvez restaurer votre contenu AEM as a Cloud Service à partir de la sauvegarde à l’aide de Cloud Manager.



Le processus de restauration en libre-service de Cloud Manager copie les données des sauvegardes système d’Adobe et les restaure dans son environnement d’origine. Une restauration est effectuée pour renvoyer à leur état d’origine les données qui ont été perdues, endommagées ou supprimées accidentellement.

Le processus de restauration affecte uniquement le contenu, laissant votre code et votre version d’AEM inchangés. Vous pouvez lancer la restauration de différents environnements à tout moment.

Si vous devez restaurer le code source précédemment déployé de manière facile et rapide, sans avoir à démarrer une nouvelle exécution de pipeline, vous pouvez utiliser [Restaurer le code précédemment déployé](/help/operations/restore-previous-code-deployed.md).

Cloud Manager fournit deux types de sauvegardes à partir desquelles vous pouvez restaurer du contenu.

* **PIT (Point-In-Time) :** cette option restaure les sauvegardes continues capturées au cours des dernières 24 heures.
* **Semaine dernière :** ce type effectue une restauration à partir des sauvegardes système au cours des sept derniers jours, à l’exception des 24 heures précédentes.

Dans les deux cas, la version de votre code personnalisé et la version AEM restent inchangées.

>[!TIP]
>
>Il est également possible de restaurer des sauvegardes [à l’aide de l’API publique](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/).

>[!WARNING]
>
>* Cette fonctionnalité ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu.
>* La restauration d’une sauvegarde supprime toutes les données ajoutées après cette sauvegarde. L’évaluation revient également à sa version précédente.
>* Avant de lancer une restauration de contenu, envisagez d’autres options de restauration de contenu sélective.

## Options de restauration de contenu sélectif {#selective-options}

Avant de procéder à la restauration complète du contenu, prenez en compte les options suivantes pour restaurer plus facilement votre contenu.

* Si un package est disponible pour le chemin supprimé, réinstallez-le à l’aide du [Gestionnaire de packages](/help/implementing/developing/tools/package-manager.md).
* Si le chemin supprimé était une page dans Sites, utilisez la fonction [ Restaurer l’arborescence ](/help/sites-cloud/authoring/sites-console/page-versions.md).
* Si le chemin supprimé était un dossier de ressources et que les fichiers d’origine sont disponibles, chargez-les à nouveau via [la console Assets](/help/assets/add-assets.md).
* Si le contenu supprimé était des ressources, pensez à restaurer [ versions précédentes des ressources](/help/assets/manage-digital-assets.md).

Si aucune des options ci-dessus ne fonctionne et que le contenu du chemin supprimé est significatif, effectuez une restauration de contenu comme décrit dans les sections suivantes.

## Créer un rôle d’utilisateur {#user-role}

Par défaut, aucun utilisateur n’est autorisé à exécuter des restaurations de contenu dans les environnements de développement, de production ou d’évaluation. Pour déléguer cette autorisation à des utilisateurs ou groupes spécifiques, procédez comme suit.

1. Créez un profil de produit avec un nom expressif qui fait référence à la restauration de contenu.
1. Fournissez l’autorisation **Accès au programme** sur le programme requis.
1. Fournissez l’autorisation **Créer une restauration d’environnement** sur l’environnement requis ou sur tous les environnements du programme, selon votre cas d’utilisation.
1. Attribuez des utilisateurs à ce profil.

Pour plus d’informations sur la gestion des autorisations, voir [Autorisations personnalisées](/help/implementing/cloud-manager/custom-permissions.md).

## Restaurer le contenu d’un environnement {#restoring-content}

>[!NOTE]
>
>Un utilisateur doit disposer des [autorisations appropriées](#user-role) pour lancer une opération de restauration.

**Pour restaurer le contenu d’un environnement, procédez comme suit**

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

1. Dans le tableau Environnements , à droite d’un environnement dont vous souhaitez restaurer le contenu, cliquez sur ![Icône Plus ou icône du menu représentant des points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), puis cliquez sur **Restaurer le contenu**.

   ![Option Restaurer le contenu du menu représentant des points de suspension](/help/operations/assets/environments-ellipsis-menu.png)

1. Sous l’onglet **Restaurer le contenu** de la page de l’environnement, dans la liste déroulante **Temps de restauration** sélectionnez la période de restauration.

   ![Onglet Restaurer le contenu d’un environnement](/help/operations/assets/environments-content-restore-tab.png)

   * Si vous avez choisi **Dernières 24 heures**, dans le champ adjacent **Heure**, indiquez l’heure exacte des dernières 24 heures à partir de laquelle la restauration doit avoir lieu.
   * Si vous avez choisi **Semaine dernière**, dans le champ adjacent **Jour**, sélectionnez une date des sept derniers jours, à l’exclusion des 24 heures précédentes.

1. Une fois que vous avez sélectionné une date ou défini une heure, la section **Sauvegardes disponibles** ci-dessous présente une liste des sauvegardes disponibles qui peuvent être restaurées.

1. Cliquez sur ![icône d’informations](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) à côté d’une sauvegarde pour afficher sa version de code et la version d’AEM, puis évaluez l’impact de la restauration avant de sélectionner une sauvegarde (voir [ Choisir la bonne sauvegarde](#choosing-backup)).

   ![Informations de sauvegarde](assets/backup-info.png)

   L’horodatage affiché pour les options de restauration est basé sur le fuseau horaire de l’ordinateur de l’utilisateur.

1. À l’extrémité droite de la ligne représentant la sauvegarde que vous souhaitez restaurer, cliquez sur ![Rotation de l’CCW en gras, ou restaurer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_RotateCCWBold_18_N.svg) pour lancer le processus de restauration.

1. Vérifiez les détails dans la boîte de dialogue **Restaurer le contenu**, puis cliquez sur **Restaurer**.

   ![Confirmer la restauration](assets/backup-restore.png)

Le processus de sauvegarde est lancé. Vous pouvez consulter son statut dans la liste **[Restaurer l’activité](#restore-activity)**. Le temps nécessaire à l’achèvement d’une opération de restauration dépend de la taille et du profil du contenu restauré.

Une fois la restauration terminée, l’environnement effectue les opérations suivantes :

* Exécute le même code et la même version d’AEM qu’au moment de lancer l’opération de restauration.
* Il comporte le même contenu que celui qui était disponible à l’horodatage de l’instantané choisi, avec les index reconstruits pour correspondre au code actuel.

## Choisir la bonne sauvegarde {#choosing-backup}

Le processus de restauration en libre-service de Cloud Manager restaure uniquement le contenu vers AEM. Pour cette raison, vous devez soigneusement tenir compte des modifications de code effectuées entre le point de restauration souhaité et l’heure actuelle. Examinez l’historique de validation entre l’ID de validation actuel et celui vers lequel la restauration est effectuée.

Il existe plusieurs scénarios.

* Le code personnalisé d’environnement et la restauration se trouvent sur le même référentiel et la même branche.
* Le code personnalisé d’environnement et la restauration partagent un référentiel, utilisent une branche distincte et proviennent d’une validation commune.
* Le code personnalisé de l’environnement et la restauration se trouvent dans des référentiels différents.
   * Dans ce cas, un ID de validation ne s’affiche pas.
   * Adobe vous recommande vivement de cloner les deux référentiels et d’utiliser un outil de comparaison des branches.

En outre, gardez à l’esprit qu’une restauration peut entraîner une désynchronisation de vos environnements de production et d’évaluation. Vous êtes responsable des conséquences de la restauration du contenu.

## Restaurer l’activité {#restore-activity}

La liste **Restaurer l’activité** indique le statut des dix demandes de restauration les plus récentes, y compris les opérations de restauration actives.

![Restaurer l’activité](assets/backup-activity.png)

En cliquant sur ![icône d’informations](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) pour une sauvegarde, vous pouvez télécharger les journaux de cette sauvegarde et inspecter les détails du code, y compris les différences entre l’instantané et les données au moment où la restauration a été lancée.

## Sauvegarde hors site {#offsite-backup}

Des sauvegardes régulières protègent contre les risques de suppression accidentelle ou de défaillances techniques dans AEM Cloud Services, mais d’autres risques peuvent survenir en cas d’échec d’une région. Outre la disponibilité, le risque le plus important dans ce type de panne est principalement la perte de données.

AEM as a Cloud Service atténue ce risque pour tous les environnements de production AEM. En d’autres termes, il copie en continu tout le contenu AEM vers une région distante. Ce processus rend le contenu disponible pour la récupération pendant trois mois. Cette fonctionnalité est appelée sauvegarde hors site.

L’ingénierie de fiabilité du service AEM restaure les environnements d’évaluation et de production d’AEM Cloud Service à partir de sauvegardes hors site lors des pannes liées aux données.

## Limites {#limitations}

L’utilisation du mécanisme de restauration en libre-service est soumise aux restrictions suivantes.

* Les opérations de restauration sont limitées à sept jours, ce qui signifie qu’il n’est pas possible de restaurer un instantané antérieur à sept jours.
* Au maximum dix restaurations réussies sont autorisées dans tous les environnements au cours d’un programme par mois calendaire.
* Après la création de l’environnement, il faut six heures pour que le premier instantané de sauvegarde soit créé. Tant que cet instantané n’a pas été créé, aucune restauration ne peut être effectuée sur l’environnement.
* Une opération de restauration n’est pas lancée si un pipeline de configuration de niveau web ou de pile pleine est en cours d’exécution pour l’environnement.
* Une restauration ne peut pas être lancée si une autre est déjà en cours d’exécution sur le même environnement.
* Dans de rares cas, en raison de la limite de 24 heures/7 jours des sauvegardes, la sauvegarde sélectionnée peut ne plus être disponible en raison d’un délai entre le moment où elle a été sélectionnée et le moment où la restauration est lancée.
* Les données des environnements supprimés sont définitivement perdues et ne peuvent pas être récupérées.

---
title: Prise en main des outils de refactorisation
description: Découvrez comment commencer à utiliser les outils de refactorisation dans AEM as a Cloud Service
source-git-commit: 20bb756c4a2eb37341da4582f19cf41e4d60304a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 2%

---

# Prise en main des outils de refactorisation {#getting-started-refactoring-tools}

## Disponibilité {#availability}

<!-- Alexandru: duplicate contextualhelp id, drafting this for now

>[!CONTEXTUALHELP]
>id="aemcloud_rs_upload"
>title="Download"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=fr" text="Release Notes"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

-->

## Exécution des outils de refactorisation {#running-refactoring-tools}

Utilisez l’outil de refactorisation pour migrer votre code à des fins de compatibilité avec AEM as a Cloud Service.

1. Si vous n’avez pas encore créé de projet CAM, reportez-vous à [Création et gestion d’un projet dans CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md#create-project).
1. Cliquez sur la carte **Refactorisation du code** pour charger le code source.

   ![Image](/help/journey-migration/refactoring-tools/assets/rscam1.png)

1. Lorsque vous accédez pour la première fois à la vue de code **Source**, un état vide s’affiche vous invitant à charger votre code source.

   ![Image](/help/journey-migration/refactoring-tools/assets/rscam2.png)

&#x200B;---

## Chargement du code Source {#uploading}

Lorsque les clients accèdent pour la première fois aux **outils de refactorisation**, un statut vide s’affiche dans l’affichage du code **Source**. Suivez les étapes ci-dessous pour charger votre projet et commencer le processus d’inspection :

1. **Accéder à la page de chargement du projet**\
   Cliquez sur le bouton **Chargement du projet** à l’état vide pour lancer le processus de chargement.

   ![Image](/help/journey-migration/refactoring-tools/assets/rscam3.png)

1. **Chargez Votre Code Source**
   - Dans la boîte de dialogue de chargement, sélectionnez votre fichier ZIP de code source.
   - Cliquez sur **Télécharger** pour commencer.
   - La progression du chargement s’affiche dans la boîte de dialogue. La durée dépend de la taille de votre projet.

   ![Image](/help/journey-migration/refactoring-tools/assets/rscam4.png)

1. **Processus d&#39;inspection**
   - Après le chargement, le **Processus d&#39;inspection** commence automatiquement en arrière-plan.
   - L’affichage du code **Source** affiche désormais votre projet chargé et son statut d’inspection.

1. **Statut du contrôle** Le processus de contrôle est conçu pour simplifier l&#39;exécution des outils de refactorisation en réduisant la surcharge des configurations manuelles.

   L&#39;inspection affichera l&#39;un des statuts suivants :
   - **En cours** - L’inspection est en cours.
   - **Prêt** - L&#39;inspection est terminée ; vous pouvez maintenant exécuter les outils de refactorisation.
   - **Échec** - Une erreur s’est produite. Cliquez sur le projet pour examiner le rapport d&#39;inspection et résoudre les problèmes.

   ![Image](/help/journey-migration/refactoring-tools/assets/rscam5.png)

>[!NOTE]
>Le chargement d’un nouveau projet supprimera le projet existant. Assurez-vous que toutes les données nécessaires sont enregistrées avant de continuer.

>[!NOTE]
>Les tâches de refactorisation ne peuvent être exécutées que si le chargement du code source réussit.

&#x200B;---

## Traitements de refactorisation {#refactoring-jobs}

Lorsque vous cliquez sur l’onglet **Tâche de refactorisation**, une liste des tâches existantes s’affiche. Si aucune tâche n’a encore été créée, un état vide s’affiche pour demander la création de la tâche.

![Image](/help/journey-migration/refactoring-tools/assets/rscam6.png)

### &#x200B;1. Créer une tâche de refactorisation

- Cliquez sur le bouton **Créer une tâche**.
- Sélectionnez le ou les outils de refactorisation souhaités.
- Cliquez sur **Démarrer** pour lancer le processus de refactorisation.

![Image](/help/journey-migration/refactoring-tools/assets/rscam7.png)

>[!NOTE]
>Vous pouvez déclencher des tâches de refactorisation individuelles ou exécuter tous les outils disponibles en une seule fois à l’aide de l’option **Tous les outils ensemble**.

&#x200B;---

### &#x200B;2. Statut de la tâche

- **En cours d’exécution** - Le traitement est en cours. Le statut est automatiquement mis à jour à la fin ou en cas d’échec.
- **Terminé** - Le traitement est terminé. Vous pouvez maintenant consulter les résultats ou télécharger le code refactorisé.
- **Échec** - Le traitement a rencontré une erreur. Cliquez sur la tâche pour afficher les journaux détaillés et résoudre le problème.

![Image](/help/journey-migration/refactoring-tools/assets/rscam8.png)

Une fois la tâche terminée, le bouton **Télécharger** devient disponible et vous permet de récupérer les éléments suivants :

- **Le projet refactorisé** : il s’agit du code mis à jour après l’application de la transformation. Les clients peuvent télécharger le code le plus récent pour leur projet.
- **Journaux d’activité** : pendant l’exécution du traitement, toutes les étapes effectuées par l’outil et les modifications apportées sont consignées dans le cadre de cette opération.
- **Rapport des résultats** : ce rapport contient des éléments qui n’ont pas été entièrement exécutés par l’outil, mais qui doivent toujours être traités. Toutes ces modifications sont consignées ici.

![Image](/help/journey-migration/refactoring-tools/assets/rscam9.png)

>[!NOTE]
>Chaque tâche peut prendre jusqu’à 1 heure. Si le statut n’est pas mis à jour, contactez l’assistance Adobe.


---
title: À propos des profils d’image et vidéo Dynamic Media
description: Un profil d’image ou vidéo permet de déterminer les options à appliquer aux ressources que vous chargez dans un dossier. Par exemple, vous pouvez spécifier le codage vidéo à appliquer aux ressources vidéo Dynamic Media que vous chargez, ou le profil d’image à appliquer aux ressources d’image Dynamic Media afin de les recadrer correctement.
translation-type: tm+mt
source-git-commit: 5da0d4cc8c6d8781dd7cce8bbbde207568a6d10b
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 100%

---


# À propos des profils d’image et vidéo Dynamic Media{#about-dm-image-video-profiles}

Un profil d’image ou vidéo permet de déterminer les options à appliquer aux ressources que vous chargez dans un dossier. Par exemple, vous pouvez spécifier le codage vidéo à appliquer aux ressources vidéo Dynamic Media que vous chargez, ou le profil d’image à appliquer aux ressources d’image Dynamic Media afin de les recadrer correctement.

Dans Dynamic Media, vous pouvez créer deux types de profils, qui sont abordés en détail sous les liens suivants :

* [Profils d’image Dynamic Media](/help/assets/dynamic-media/image-profiles.md)
* [Profils vidéo Dynamic Media](/help/assets/dynamic-media/video-profiles.md)

Voir également à [Profils de métadonnées](/help/assets/metadata-profiles.md).

Vous devez disposer de droits d’administrateur pour créer, modifier et supprimer des profils d’images ou vidéo Dynamic Media.

Une fois votre profil d’image ou vidéo créé, vous pouvez l’affecter à un ou plusieurs dossiers utilisés comme destination des ressources Dynamic Media venant d’être chargées.

Voir également [Bonnes pratiques relatives à l’organisation de vos ressources numériques pour utiliser des profils d’image ou vidéo](/help/assets/dynamic-media/best-practices-for-file-management.md).

>[!NOTE]
>
>Les ressources que vous déplacez d’un dossier à un autre ne sont pas retraitées. Par exemple, supposons que vous ayez un dossier 1 auquel le profil A est affecté et un dossier 2 auquel le profil B est affecté. Si vous déplacez des ressources du dossier 1 au dossier 2, les ressources déplacées conservent leur traitement d’origine du dossier 1.
>
>C’est également le cas lorsque vous déplacez des ressources entre deux dossiers auxquels le même profil est affecté.

## Retraitement des ressources Dynamic Media dans un dossier {#reprocessing-assets}

Vous pouvez traiter une nouvelle fois des ressources dans un dossier qui comporte déjà un profil d’image Dynamic Media ou un profil vidéo Dynamic Media que vous avez ensuite modifié.

Supposons que vous ayez créé un profil d’image Dynamic Media et que vous l’ayez affecté à un dossier. Le profil d’image a été automatiquement appliqué aux ressources d’image que vous avez chargées dans le dossier. Cependant, vous décidez par la suite d’ajouter un nouveau rapport de recadrage intelligent au profil d’image. Désormais, au lieu de devoir sélectionner et charger à nouveau les ressources dans le dossier, il vous suffit d’exécuter le workflow *Scene7 : Retraiter les ressources*.

Vous pouvez exécuter le workflow de retraitement sur une ressource pour laquelle le traitement a échoué la première fois. Ainsi, même si vous n’avez pas modifié de profil d’image ou vidéo, ou si vous avez déjà appliqué un profil d’image ou vidéo, vous pouvez toujours exécuter le workflow de retraitement sur un dossier de ressources à tout moment.

Vous pouvez, au besoin, régler la taille de lot du workflow de retraitement sur une valeur comprise entre 50 (valeur par défaut) et 1 000 ressources. Lorsque vous exécutez le workflow _Scene7 : Retraiter les ressources_ sur un dossier, les ressources sont regroupées par lots, puis envoyées au serveur Dynamic Media en vue du traitement. Après le traitement, les métadonnées de chaque ressource de l’ensemble du jeu de lots sont mises à jour dans AEM. Si la taille du lot est très importante, le traitement peut être retardé. Si le lot est trop petit, cela peut entraîner un trop grand nombre d’allers-retours avec le serveur Dynamic Media.

Voir [Réglage de la taille du lot du workflow de retraitement](#adjusting-load).

>[!NOTE]
>
>Si vous effectuez une migration groupée des ressources de Dynamic Media Classic vers AEM, vous devez activer l’agent de réplication Migration sur le serveur Dynamic Media. Une fois la migration terminée, veillez à désactiver l’agent.
>
>L’agent de publication Migration doit être désactivé sur le serveur Dynamic Media afin que le workflow de retraitement fonctionne comme prévu.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**Pour retraiter des ressources Dynamic Media dans un dossier** :
1. Dans AEM, à partir de la page Assets, accédez à un dossier de ressources Dynamic Media auquel un profil d’image ou vidéo est affecté et pour lequel vous souhaitez appliquer le workflow **Scene7 : Retraiter les ressources**.

   Dans le cas des dossiers auxquels un profil d’image ou vidéo est déjà affecté, le nom du profil est affiché directement sous celui du dossier en mode Carte.

1. Sélectionnez un dossier.

   * Le workflow prend en compte tous les fichiers du dossier sélectionné, de manière récursive.
   * Si le dossier principal sélectionné contient un ou plusieurs sous-dossiers avec des ressources, le workflow retraite chaque ressource de la hiérarchie de dossiers.
   * Il est conseillé d’éviter d’exécuter ce workflow sur une hiérarchie de dossiers contenant plus de 1 000 ressources.

1. Dans la liste déroulante située dans le coin supérieur gauche de la page, cliquez sur **[!UICONTROL Chronologie]**.
1. Dans le coin inférieur gauche de la page, à droite du champ Commentaire, cliquez sur l’icône représentant un signe d’insertion (**^**).

   ![Workflow de retraitement des ressources 1](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Cliquez sur **[!UICONTROL Démarrer le processus]**.
1. Dans la liste déroulante **[!UICONTROL Démarrer le processus]**, sélectionnez **[!UICONTROL Scene7 : Retraiter les ressources]**.
1. (Facultatif) Dans la zone de texte **Entrer le titre du processus**, saisissez le nom du workflow. Si nécessaire, vous pouvez utiliser le nom pour faire référence à l’instance de workflow.

   ![Retraiter les ressources 2](/help/assets/dynamic-media/assets/reprocess-assets2.png)

1. Cliquez sur **[!UICONTROL Début]**, puis sur **[!UICONTROL Confirmer]**.

   Pour surveiller le workflow ou vérifier sa progression, cliquez sur **[!UICONTROL Outils > Workflow]** dans la page de console principale d’AEM. Sélectionnez un workflow dans la page Instances de processus. Dans la barre de menus, cliquez sur **[!UICONTROL Ouvrir l’historique]**. Vous pouvez également arrêter, suspendre ou renommer un workflow sélectionné à partir de la même page Instances de processus.

### Réglage de la taille du lot du workflow de retraitement {#adjusting-load}

(Facultatif) La taille de lot par défaut dans le workflow de retraitement est de 50 ressources par tâche. Cette taille optimale est déterminée par la taille moyenne des ressources et les types MIME des ressources sur lesquelles le retraitement est exécuté. Une valeur plus élevée signifie qu’une seule tâche de retraitement comprendra de nombreux fichiers. Par conséquent, la bannière de traitement reste plus longtemps sur AEM Assets. Cependant, si la taille de fichier moyenne est inférieure ou égale à 1 Mo, Adobe recommande de définir cette valeur sur plusieurs centaines de Mo, mais de ne jamais dépasser 1 000 Mo. Si la taille de fichier moyenne est élevée (de l’ordre de quelques centaines de Mo), Adobe recommande de réduire la taille du lot jusqu’à 10.

**Pour régler, si nécessaire, la taille de lot du workflow de retraitement, procédez comme suit :**

1. Dans Experience Manager, appuyez sur **[!UICONTROL Adobe Experience Manager]** pour accéder à la console de navigation globale, puis appuyez sur l’icône **[!UICONTROL Outils]** (marteau) > **[!UICONTROL Workflow > Modèles]**.
1. Sur la page Modèles de processus, en mode Carte ou Liste, sélectionnez **[!UICONTROL Scene7 : Retraiter les ressources]**.

   ![Page Modèles de processus avec le workflow Scene7 : Retraiter les ressources sélectionné en mode Carte](/help/assets/dynamic-media/assets/reprocess-assets7.png)

1. Dans la barre d’outils, cliquez sur **[!UICONTROL Modifier]**. Un nouvel onglet de navigateur ouvre la page du modèle de processus Scene7 : Retraiter les ressources.
1. Dans le coin supérieur droit de la page du modèle de processus Scene7 : Retraiter les ressources, appuyez sur **[!UICONTROL Modifier]** pour « déverrouiller » le workflow.
1. Dans le workflow, sélectionnez le composant Transfert par lots Scene7 pour ouvrir la barre d’outils, puis appuyez sur l’icône **[!UICONTROL Configurer]** de cette barre d’outils.

   ![Composant Transfert par lots Scene7](/help/assets/dynamic-media/assets/reprocess-assets8.png)

1. Dans la boîte de dialogue **[!UICONTROL Transfert par lots vers Scene7 – Propriétés des étapes]**, définissez les éléments suivants :
   * Dans les zones de texte **[!UICONTROL Titre]** et **[!UICONTROL Description]**, saisissez un titre et une description pour la tâche, le cas échéant.
   * Sélectionnez **[!UICONTROL Avance du gestionnaire]** si votre gestionnaire doit passer à l’étape suivante.
   * Dans le champ **[!UICONTROL Délai d’expiration]**, saisissez le délai d’expiration du processus externe (en secondes).
   * Dans le champ **[!UICONTROL Période]**, indiquez un intervalle d’interrogation (en secondes) pour tester la fin du processus externe.
   * Dans le champ **[!UICONTROL Lot]**, saisissez le nombre maximum de ressources (entre 50 et 1 000) à traiter dans une tâche de chargement par lots du serveur Dynamic Media.
   * Sélectionnez **[!UICONTROL Avancer sur dépassement de délai]** si vous souhaitez avancer à l’expiration du délai. Désélectionnez cette option si vous souhaitez passer à la boîte de réception à l’expiration du délai.

   ![Boîte de dialogue des propriétés](/help/assets/dynamic-media/assets/reprocess-assets3.png)

1. Dans le coin supérieur droit de la boîte de dialogue **[!UICONTROL Transfert par lots vers Scene7 – Propriétés des étapes]**, appuyez sur **[!UICONTROL Terminé]**.

1. Dans le coin supérieur droit de la page du modèle de workflow Scene7 : Retraiter les ressources, appuyez sur **[!UICONTROL Synchroniser]**. Lorsque **[!UICONTROL Synchronisé]** est affiché, cela signifie que le modèle d’exécution du workflow est correctement synchronisé et prêt à retraiter les ressources dans un dossier.

   ![Synchronisation du modèle de workflow](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Fermez l’onglet du navigateur qui affiche le modèle de workflow Scene7 : Retraiter les ressources.

<!-- MAY BE NEEDED IN THE FUTURE

1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, tap **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then tap the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/security/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, tap **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/security/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, tap **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, tap **[!UICONTROL CRXDE Lite]** to return to the main AEM console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.

-->

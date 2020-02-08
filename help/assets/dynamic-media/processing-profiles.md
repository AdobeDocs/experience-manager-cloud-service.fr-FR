---
title: Profils de traitement des métadonnées, des images et des vidéos
description: Un profil est un jeu de règles concernant les options à appliquer aux ressources téléchargées dans un dossier. Spécifiez le profil de métadonnées et le profil de codage vidéo à appliquer aux ressources vidéo que vous chargez. Pour les ressources d’images, vous pouvez également spécifier le profil d’imagerie qui doit leur être appliqué afin de les recadrer correctement.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Profiles for processing metadata, images, and videos{#profiles-for-processing-metadata-images-and-videos}

Un profil est une recette indiquant les options à appliquer aux ressources qui sont chargées dans un dossier. Par exemple, vous pouvez spécifier le profil de métadonnées et le profil de codage vidéo à appliquer aux fichiers vidéo que vous téléchargez. ou le profil d’image à appliquer aux ressources image afin de les recadrer correctement.

Ces règles peuvent inclure l’ajout de métadonnées, le recadrage intelligent des images ou la mise en place de profils de codage vidéo. AEM vous permet de créer trois types de profils, qui sont abordés en détail sous les liens suivants :

* [Profils de métadonnées](/help/assets/metadata-profiles.md)
* [Profils d’image](/help/assets/dynamic-media/image-profiles.md)
* [Profils vidéo](/help/assets/dynamic-media/video-profiles.md)

Vous devez disposer de droits d’administrateur pour créer, modifier et supprimer des profils vidéo, de métadonnées ou d’image.

Une fois votre profil vidéo, de métadonnées ou d’image créé, vous pouvez l’affecter à un ou plusieurs dossiers utilisés comme destination des ressources qui viennent d’être chargées.

Consultez également la section [Pratiques recommandées pour organiser vos ressources numériques en vue d’utiliser des profils de traitement](/help/assets/dynamic-media/best-practices-for-file-management.md).

>[!NOTE]
>
>Les ressources que vous déplacez d’un dossier à un autre ne sont pas retraitées. Supposons, par exemple, que le dossier 1 soit doté du profil A et que le dossier 2 soit doté du profil B. Si vous déplacez des fichiers du dossier 1 vers le dossier 2, les fichiers déplacés conservent leur traitement d’origine depuis le dossier 1.
>
>C’est également le cas lorsque vous déplacez des ressources entre deux dossiers auxquels le même profil est affecté.

## Retraitement des fichiers dans un dossier {#reprocessing-assets}

Vous pouvez retraiter des fichiers dans un dossier qui comporte déjà un profil de traitement existant que vous avez modifié ultérieurement.

Supposons, par exemple, que vous ayez créé un profil Image et l’ayez affecté à un dossier. Le profil Image était automatiquement appliqué aux fichiers d’image que vous avez téléchargés dans le dossier. Cependant, vous déciderez par la suite d’ajouter un nouveau ratio de recadrage intelligent au profil. Désormais, au lieu d’avoir sélectionné et de télécharger à nouveau les fichiers dans le dossier, il vous suffit d’exécuter *Scene7 : Processus de retraitement des ressources* .

Vous pouvez exécuter le processus de retraitement sur une ressource pour laquelle le traitement a échoué la première fois. Ainsi, même si vous n’avez pas modifié un profil de traitement ou appliqué un profil de traitement, vous pouvez toujours exécuter le processus de retraitement sur un dossier de ressources à tout moment.

Vous pouvez éventuellement ajuster la taille du lot du processus de retraitement d’une valeur par défaut de 50 fichiers à 1 000 fichiers. Lorsque vous exécutez _Scene7 : Processus de retraitement des ressources_ sur un dossier, les ressources sont regroupées par lots, puis envoyées au serveur Contenu multimédia dynamique pour traitement. Après le traitement, les métadonnées de chaque fichier dans l’ensemble du jeu de lots sont mises à jour dans AEM. Si la taille du lot est très importante, le traitement peut être retardé. Ou, si la taille du lot est trop petite, cela peut entraîner un trop grand nombre d’allers-retours vers le serveur Contenu multimédia dynamique.

Voir [Ajustement de la taille du lot du processus](#adjusting-load)de retraitement.

>[!NOTE]
>
>Si vous effectuez une migration en masse des ressources de Dynamic Media Classic vers AEM, vous devez activer l’agent de réplication de migration sur le serveur Dynamic Media. Une fois la migration terminée, veillez à désactiver l’agent.
L’agent de publication de migration doit être désactivé sur le serveur Contenu multimédia dynamique afin que le processus de retraitement fonctionne comme prévu.

<!-- LEAVE IN PLACE, MAY BE USED IN THE FUTURE

Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. 

-->

**Pour retraiter des fichiers dans un dossier**:
1. Dans AEM, à partir de la page Ressources, accédez à un dossier de ressources auquel un profil de traitement est affecté et pour lequel vous souhaitez appliquer **Scene7 : Processus de retraitement des ressources** ,

   Les dossiers auxquels un profil de traitement est déjà affecté sont indiqués par l’affichage du nom du profil directement sous le nom du dossier en mode Carte.

1. Sélectionnez un dossier.

   * Le flux de travaux considère tous les fichiers du dossier sélectionné de manière récursive.
   * S’il existe un ou plusieurs sous-dossiers avec des fichiers dans le dossier principal sélectionné, le processus retraite chaque fichier dans la hiérarchie de dossiers.
   * En règle générale, évitez d’exécuter ce processus sur une hiérarchie de dossiers contenant plus de 1 000 ressources.

1. Near the upper-left corner of the page, from the drop-down list, click **[!UICONTROL Timeline]**.
1. Près du coin inférieur gauche de la page, à droite du champ Commentaire, cliquez sur l&#39;icône en forme de carat ( **^** ).

   ![Processus de retraitement des ressources 1](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Cliquez sur **[!UICONTROL Démarrer le processus]**.
1. Dans la liste déroulante **[!UICONTROL Démarrer le flux de travail]** , sélectionnez **[!UICONTROL Scene7 : Retraitement des ressources]**.
1. (Facultatif) Dans le champ **Saisir le titre du flux de travail** , saisissez le nom du flux de travail. Si nécessaire, vous pouvez utiliser le nom pour référencer l’instance de processus.

   ![Retraitement des fichiers 2](/help/assets/dynamic-media/assets/reprocess-assets2.png)

1. Cliquez sur **[!UICONTROL Démarrer]**, puis sur **[!UICONTROL Confirmer]**.

   Pour surveiller le flux de travaux ou en vérifier la progression, dans la page de console principale d’AEM, cliquez sur **[!UICONTROL Outils > Processus]**. Dans la page Instances de processus, sélectionnez un processus. Dans la barre de menus, cliquez sur **[!UICONTROL Ouvrir l’historique]**. Vous pouvez également arrêter, suspendre ou renommer un processus sélectionné à partir de la même page Instances de processus.

### Ajustement de la taille du lot du processus de retraitement {#adjusting-load}

(Facultatif) La taille du lot par défaut dans le processus de retraitement est de 50 fichiers par tâche. Cette taille de lot optimale est régie par la taille moyenne des fichiers et les types MIME des fichiers sur lesquels le retraitement est exécuté. Une valeur plus élevée signifie que vous disposez de nombreux fichiers dans une seule tâche de retraitement. Par conséquent, la bannière de traitement reste sur les ressources AEM pendant une plus longue période. Toutefois, si la taille moyenne du fichier est inférieure ou égale à 1 Mo, Adobe vous recommande d’augmenter la valeur à plusieurs centaines, mais jamais plus de 1 000. Si la taille moyenne du fichier est de plusieurs centaines de mégaoctets, Adobe vous recommande de réduire la taille du lot jusqu’à 10.

**Pour ajuster éventuellement la taille du lot du processus de retraitement**

1. Dans Experience Manager, appuyez sur **[!UICONTROL Adobe Experience Manager]** pour accéder à la console de navigation globale, puis appuyez sur l’icône **[!UICONTROL Outils]** (marteau) > **[!UICONTROL Processus > Modèles]**.
1. Sur la page Modèles de processus, en mode Carte ou Liste, sélectionnez **[!UICONTROL Scene7 : Retraitement des ressources]**.

   ![Page Modèles de processus avec Scene7 : Processus de retraitement des fichiers sélectionné dans le mode Carte](/help/assets/dynamic-media/assets/reprocess-assets7.png)

1. Dans la barre d’outils, cliquez sur **[!UICONTROL Modifier]**. Un nouvel onglet de navigateur ouvre Scene7 : Retraitement de la page du modèle de processus Ressources.
1. Sur Scene7 : Retraitement de la page de flux de travaux Ressources, près du coin supérieur droit, appuyez sur **[!UICONTROL Modifier]** pour &quot;déverrouiller&quot; le flux de travaux.
1. Dans le flux de travaux, sélectionnez le composant Téléchargement par lot Scene7 pour ouvrir la barre d’outils, puis appuyez sur **[!UICONTROL Configurer]** dans la barre d’outils.

   ![Composant de téléchargement par lot Scene7](/help/assets/dynamic-media/assets/reprocess-assets8.png)

1. Dans la boîte de dialogue **[!UICONTROL Téléchargement par lots vers Scene7—Propriétés]** des étapes, définissez les options suivantes :
   * Dans les champs **[!UICONTROL Titre]** et **[!UICONTROL Description]** , saisissez un nouveau titre et une nouvelle description pour la tâche, le cas échéant.
   * Sélectionnez Avance du **[!UICONTROL gestionnaire]** si votre gestionnaire passe à l’étape suivante.
   * Dans le champ **[!UICONTROL Délai d’expiration]** , saisissez le délai d’expiration du processus externe (secondes).
   * Dans le champ **[!UICONTROL Période]** , entrez un intervalle d’interrogation (secondes) à tester pour la fin du processus externe.
   * Dans le champ **** Lot, saisissez le nombre maximal de fichiers (50 à 1 000) à traiter dans une tâche de téléchargement de traitement par lot du serveur de médias dynamiques.
   * Sélectionnez **[!UICONTROL Avancer à l’expiration]** si vous souhaitez avancer à l’expiration du délai. Désélectionnez cette option si vous souhaitez passer à la boîte de réception lorsque le délai d’expiration est atteint.
   ![Propriétés, boîte de dialogue](/help/assets/dynamic-media/assets/reprocess-assets3.png)

1. Dans le coin supérieur droit de la boîte de dialogue Téléchargement par **[!UICONTROL lot vers Scene7 - Propriétés]** des étapes, appuyez sur **[!UICONTROL Terminé]**.

1. Dans le coin supérieur droit de Scene7 : Retraitement de la page du modèle de processus des ressources, appuyez sur **[!UICONTROL Synchroniser]**. Lorsque vous voyez **[!UICONTROL Synchronisé]**, le modèle d’exécution du processus est correctement synchronisé et prêt à retraiter les fichiers dans un dossier.

   ![Synchronisation du modèle de processus](/help/assets/dynamic-media/assets/reprocess-assets1.png)

1. Fermez l’onglet du navigateur qui affiche Scene7 : Modèle de processus de retraitement des ressources.

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

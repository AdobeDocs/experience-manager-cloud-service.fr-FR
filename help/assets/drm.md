---
title: Gestion des droits numériques dans Adobe Experience Manager Assets
description: Découvrez comment gérer les informations d’expiration et d’état des ressources sous licence dans AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7141e42f53c556c0ac21def6085182ef400f5a71

---


# Gestion des droits numériques dans Experience Manager Assets {#digital-rights-management-in-assets}

Les actifs numériques sont souvent associés à une licence qui prévoit les conditions et la durée de leur utilisation. Les ressources Adobe Experience Manager (AEM) étant entièrement intégrées à la plate-forme AEM, vous pouvez gérer efficacement les informations d’expiration et les états des ressources. Vous pouvez également associer des informations de licence à des ressources.

## Expiration de ressources {#asset-expiration}

L’expiration de ressources est un moyen efficace de faire respecter les exigences en matière de licence pour les ressources. Elle garantit que la ressource qui est publiée ne l’est plus lorsqu’elle arrive à expiration, ce qui évite tout risque de violation de licence. Un utilisateur sans droits d’administration ne peut pas modifier, copier, déplacer, publier ni télécharger une ressource arrivée à expiration.

Vous pouvez afficher l’état d’expiration d’un fichier aux emplacements suivants :

* **Affichage** de carte : Dans le cas d’une ressource arrivée à expiration, un indicateur sur la carte indique qu’elle a expiré.
* **Affichage** par liste : Pour les fichiers expirés, la colonne **[!UICONTROL Etat]** affiche la bannière **[!UICONTROL Expiré]** .
* **Chronologie**: Vous pouvez afficher l’état d’expiration d’un fichier dans le plan de montage chronologique. Sélectionnez le fichier et choisissez Chronologie.
* **Rail** de références : Vous pouvez également afficher l’état d’expiration des ressources dans le rail **[!UICONTROL Références]** . Il gère les états d’expiration des ressources et les relations entre les ressources composites et les sous-ressources, les collections et les projets référencés.

1. Accédez à la ressource pour laquelle vous souhaitez voir les pages web de référencement et les ressources composites.
1. Sélectionnez le fichier, puis cliquez/appuyez sur l’icône de navigation globale.
1. Choose **[!UICONTROL References]** from the menu.
1. For expired assets, the References rail displays the expiry status **[!UICONTROL Asset is Expired]** at the top. If the asset has expired subassets, the References rail displays the status **[!UICONTROL Asset has Expired Sub-Assets]**.

### Recherche de ressources arrivées à expiration {#search-expired-assets}

Vous pouvez rechercher des ressources arrivées à expiration, y compris les sous-ressources expirées dans le panneau de recherche.

1. Dans la console Ressources, cliquez sur l&#39;icône Rechercher dans la barre d&#39;outils pour afficher le champ Omnisearch.

1. Avec le curseur dans la zone Omnisearch, appuyez sur la touche Entrée pour afficher la page des résultats de la recherche.

1. Cliquez sur l’icône de navigation globale pour afficher le panneau Recherche.

1. Cliquez/appuyez sur l’option **[!UICONTROL Etat d’expiration]** pour accéder aux informations.

1. Sélectionnez **[!UICONTROL Expiré]**. Les ressources arrivées à expiration sont visibles dans les résultats de la recherche.

When you choose the **[!UICONTROL Expired]** option, the Assets console only displays the expired assets and subassets that are referenced by compound assets. Les ressources composites qui référencent des sous-ressources expirées ne s’affichent pas immédiatement une fois que les sous-ressources arrivent à expiration. En réalité, elles sont affichées lorsque AEM Assets détecte qu’elles référencent des sous-ressources expirées, à la prochaine exécution du planificateur.

Si vous modifiez la date d’expiration d’une ressource publiée à une date antérieure au cycle du planificateur en cours, la planification détecte toujours cette ressource en tant que ressource expirée lors de sa prochaine exécution et elle reflète son état en conséquence.

En outre, si un problème ou une erreur empêche le planificateur de détecter les ressources expirées dans le cycle en cours, le planificateur réexamine ces ressources lors du cycle suivant et identifie leur statut expiré.

To enable the Assets console to display the referencing compound assets along with the expired subassets, configure an **[!UICONTROL Adobe CQ DAM Expiry Notification]** workflow in AEM Configuration Manager.

1. Ouvrez AEM Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time based Scheduler]** is selected, which schedules a job to check at a specific time whether an asset has expired subassets. Une fois la tâche terminée, les ressources qui possèdent des sous-ressources expirées et des ressources référencées sont affichées à l’état expiré dans les résultats de la recherche.

1. To run the job periodically, clear the **[!UICONTROL Time Based Scheduler Rule]** field and modify the time in seconds in the **[!UICONTROL Periodic Scheduler]** field. Par exemple, l’expression exemple &#39;0 0 0 &amp;ast; &amp;ast; ?&#39; déclenche la tâche à 00 heures.
1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

   >[!NOTE]
   >
   >Seul l’auteur de la ressource (la personne qui la charge dans AEM Assets) reçoit un e-mail lorsqu’elle arrive à expiration. Découvrez comment configurer la notification par courrier électronique pour plus d’informations sur la configuration des notifications par courrier électronique au niveau global d’AEM.

1. Dans le champ **[!UICONTROL Notification préalable en secondes]** indiquez l’intervalle de temps, en secondes, qui précède le moment auquel une ressource expire et pendant lequel vous souhaitez recevoir une notification concernant l’expiration. Si vous êtes administrateur ou l’auteur de la ressource, vous recevez un message avant son expiration vous informant qu’elle va expirer une fois le délai spécifié écoulé.

   Une fois la ressource arrivée à expiration, vous recevez une notification par courrier électronique qui confirme l’expiration. En outre, les ressources expirées sont désactivées.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## États d’une ressource {#asset-states}

La console Ressources d’Adobe Experience Manager (AEM) Assets peut afficher différents états pour les ressources. En fonction de l’état actuel d’une ressource donnée, le mode Carte affiche un libellé décrivant son état (par exemple, expiré, modifié, approuvé, rejeté, etc.).

1. Dans l’interface utilisateur Assets, sélectionnez une ressource.

1. Tap/click the **[!UICONTROL Publish]** icon from the toolbar. If you can&#39;t see the **Publish** icon on the toolbar, tap/click **[!UICONTROL More]** on the toolbar and locate the **[!UICONTROL Publish]** icon.

1. Choose **[!UICONTROL Publish]** from the menu, and then close the confirmation dialog.
1. Quittez le mode de sélection. L’état de publication de la ressource s’affiche au bas de sa miniature en mode d’affichage Carte. En mode Liste, la colonne Publié indique le moment auquel le fichier a été publié.

1. Dans l’interface utilisateur Assets, sélectionnez une ressource et appuyez/cliquez sur l’icône **[!UICONTROL Propriétés]** pour afficher sa page de détails.

1. In the Advanced tab, and set an expiration date for the asset from the **[!UICONTROL Expires]** field under.

1. Click **[!UICONTROL Save]** and then click **[!UICONTROL Close]** to display the Asset console.
1. L’état de publication de la ressource indique qu’elle a expiré au bas de sa miniature en mode d’affichage Carte. In the list view, the status of the asset is displayed as **[!UICONTROL Expired]**.

1. Dans la console Ressources, sélectionnez un dossier et créez une tâche de révision sur le dossier.
1. Review and approve/reject the assets in the review task and click **[!UICONTROL Complete]**.
1. Accédez au dossier pour lequel vous avez créé la tâche de révision. L’état des ressources que vous avez approuvées/rejetées s’affiche en bas du mode Carte. En mode Liste, les états d’approbation et d’expiration sont affichés dans les colonnes appropriées.

1. To search for assets based on their status, click/tap the **[!UICONTROL Search]** icon to display the Omnisearch bar.

1. Appuyez sur la touche Entrée, puis cliquez/appuyez sur l’icône AEM pour afficher le panneau Rechercher.
1. In the Search panel, tap/click **[!UICONTROL Publish Status]** and select **[!UICONTROL Published]** to search for published assets in AEM Assets.

1. Tap/click **[!UICONTROL Approval Status]** and click the appropriate option to search for approved or rejected assets.

1. To search for assets based on their expiration status, select **[!UICONTROL Expiry Status]** in the Search panel and choose the appropriate option.

1. Vous pouvez également rechercher des éléments en fonction de plusieurs états, sous diverses facettes de recherche. Par exemple, vous pouvez rechercher les ressources publiées qui ont été approuvées dans une tâche de révision et qui n’ont pas encore expiré, en sélectionnant les options correspondantes dans les facettes de recherche.

## Gestion des droits numériques dans Experience Manager Assets {#digital-rights-management-in-assets-1}

Cette fonction force l’acceptation du contrat de licence avant le téléchargement d’une ressource sous licence à partir du composant Adobe Experience Manager (AEM) Assets.

Si vous sélectionnez une ressource protégée et cliquez ensuite sur l’icône **[!UICONTROL Télécharger]**, vous êtes redirigé vers une page de licence dans laquelle vous acceptez le contrat de licence. Si vous n’en acceptez pas les termes, le bouton **[!UICONTROL Télécharger]** est désactivé.

Si la sélection contient plusieurs ressources protégées, sélectionnez-en une à la fois, acceptez le contrat de licence et procédez au téléchargement de la ressource.

Une ressource est considérée comme protégée si l’une des conditions suivantes est remplie :

* La propriété de métadonnées de la ressource `xmpRights:WebStatement` pointe vers le chemin d’accès de la page CQ qui contient le contrat de licence approprié.
* La valeur de la propriété de métadonnées de la ressource `adobe_dam:restrictions` est un code HTML brut qui spécifie le contrat de licence.

>[!NOTE]
>
>The location `/etc/dam/drm/licences` used for storing licenses in earlier releases of AEM is deprecated.
>
>Si vous créez ou modifiez des pages de licence, ou si vous les transférez à partir des versions précédentes d’AEM, Adobe vous recommande de les stocker dans `/apps/settings/dam/drm/licenses` ou `/conf/*/settings/dam/drm/licenses`.

### Téléchargement de fichiers DRM {#downloading-drm-assets}

1. Dans l’affichage en mode Carte, sélectionnez les ressources à télécharger et cliquez ensuite sur l’icône **[!UICONTROL Télécharger]**.
1. Sur la page **[!UICONTROL Gestion des droits d’auteur]**, sélectionnez la ressource que vous souhaitez télécharger dans la liste.
1. Dans le volet Licence, sélectionnez **[!UICONTROL Accepter]**. Une marque de sélection apparaît en regard de la ressource dont vous avez accepté le contrat de licence. Tap/click the **[!UICONTROL Download]** button.

   >[!NOTE]
   >
   >The **[!UICONTROL Download]** button is enabled only when you choose to agree to the license agreement for a protected asset. However, if your selection comprises both protected and unprotected assets, only the protected assets are listed in the left pane and the **[!UICONTROL Download]** button is enabled to download the unprotected assets. Pour accepter le contrat de licence de plusieurs ressources protégées en même temps, sélectionnez-les dans la liste puis cliquez sur **[!UICONTROL Accepter]**.

1. In the dialog, tap/click **[!UICONTROL Download]** to download the asset or its renditions.

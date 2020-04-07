---
title: Digital Rights Management dans Adobe Experience Manager Assets
description: Découvrez comment gérer les informations d’expiration et d’état des ressources sous licence dans AEM.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Digital Rights Management dans Adobe Experience Manager Assets {#digital-rights-management-in-assets}

Les ressources numériques sont souvent associées à une licence qui prévoit les conditions et la durée de leur utilisation. Dans la mesure où Adobe Experience Manager (AEM) Assets est entièrement intégré à la plate-forme AEM, vous pouvez contrôler efficacement les informations sur l’expiration et l’état des ressources. Vous pouvez également associer des informations de licence à des ressources.

## Expiration de ressources {#asset-expiration}

L’expiration de ressources est un moyen efficace de faire respecter les exigences en matière de licence pour les ressources. Elle garantit que la ressource qui est publiée ne l’est plus lorsqu’elle arrive à expiration, ce qui évite tout risque de violation de licence. Un utilisateur sans droits d’administration ne peut pas modifier, copier, déplacer, publier ni télécharger une ressource arrivée à expiration.

Vous pouvez consulter l’état d’expiration d’une ressource aux emplacements suivants :

* **Mode Carte** : lorsqu’une ressource arrive à expiration, un indicateur le signale sur la carte.
* **Mode Liste** : pour les ressources arrivées à expiration, la colonne **[!UICONTROL État]** affiche la bannière **[!UICONTROL Expiré]**.
* **Chronologie** : vous pouvez consulter l’état d’expiration d’une ressource dans la chronologie. Sélectionnez le fichier et choisissez ensuite Chronologie.
* **Rail Références** : vous pouvez également afficher l’état d’expiration des ressources dans le rail **[!UICONTROL Références]**. Il gère les états d’expiration des ressources et les relations entre les ressources composites et les sous-ressources, les collections et les projets référencés.

1. Accédez à la ressource pour laquelle vous souhaitez voir les pages web de référencement et les ressources composites.
1. Sélectionnez la ressource, puis cliquez/appuyez sur l’icône de navigation globale.
1. Sélectionnez **[!UICONTROL Références]** dans le menu.
1. Pour les ressources arrivées à expiration, le rail Références affiche l’état d’expiration **[!UICONTROL La ressource est arrivée à expiration]** en haut. Si la ressource contient des sous-ressources arrivées à expiration, le rail Références affiche l’état **[!UICONTROL La ressource contient des sous-ressources arrivées à expiration]**.

### Recherche de ressources arrivées à expiration {#search-expired-assets}

Vous pouvez rechercher des ressources arrivées à expiration, y compris les sous-ressources expirées dans le panneau de recherche.

1. Dans la console Ressources, cliquez sur l&#39;icône Rechercher dans la barre d&#39;outils pour afficher le champ Omnisearch.

1. Avec le curseur dans la zone Omnisearch, appuyez sur la touche Entrée pour afficher la page des résultats de la recherche.

1. Cliquez sur l’icône de navigation globale pour afficher le panneau Recherche.

1. Cliquez/appuyez sur l’option **[!UICONTROL État d’expiration]** pour la développer.

1. Sélectionnez **[!UICONTROL Expiré]**. Les ressources arrivées à expiration sont visibles dans les résultats de la recherche.

Quand vous choisissez l’option **[!UICONTROL Expiré]**, la console Ressources affiche seulement les ressources et les sous-ressources arrivées à expiration qui ont été référencées par des ressources composites. Les ressources composites qui référencent des sous-ressources expirées ne s’affichent pas immédiatement une fois que les sous-ressources arrivent à expiration. En réalité, elles sont affichées lorsque AEM Assets détecte qu’elles référencent des sous-ressources expirées, à la prochaine exécution du planificateur.

Si vous modifiez la date d’expiration d’une ressource publiée à une date antérieure au cycle du planificateur en cours, la planification détecte toujours cette ressource en tant que ressource expirée lors de sa prochaine exécution et elle reflète son état en conséquence.

En outre, si un problème ou une erreur empêche le planificateur de détecter les ressources expirées dans le cycle en cours, le planificateur réexamine ces ressources lors du cycle suivant et identifie leur statut expiré.

Pour que la console Ressources affiche les ressources composites référencées avec les sous-ressources expirées, configurez un workflow de **[!UICONTROL notification d’expiration d’Adobe CQ DAM]** dans AEM Configuration Manager.

1. Ouvrez AEM Configuration Manager.
1. Sélectionnez l’option de **[!UICONTROL notification d’expiration d’Adobe CQ DAM]**. Par défaut, le **[!UICONTROL planificateur basé temps]** est sélectionné. Il programme une tâche qui vérifie, à un moment précis, si une ressource contient des sous-ressources arrivées à expiration. Une fois la tâche terminée, les ressources qui possèdent des sous-ressources expirées et des ressources référencées sont affichées à l’état expiré dans les résultats de la recherche.

1. Pour exécuter la tâche périodiquement, décochez l’option de **[!UICONTROL planificateur basé sur le temps]** et modifiez la périodicité en secondes dans le champ du **[!UICONTROL planificateur de périodicité]**. Par exemple, l’expression « 0 0 0 * * ? » déclenche la tâche à 00 heures.

<!-- 1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

   >[!NOTE]
   >
   >Only the asset creator (the person who uploads a particular asset to AEM Assets) receives an email when the asset expires. See how to configure email notification for additional details around configuring email notifications at the overall AEM level.
-->

1. Dans le champ **[!UICONTROL Notification préalable en secondes]** indiquez l’intervalle de temps, en secondes, qui précède le moment auquel une ressource expire et pendant lequel vous souhaitez recevoir une notification concernant l’expiration. Si vous êtes administrateur ou l’auteur de la ressource, vous recevez un message avant son expiration vous informant qu’elle va expirer une fois le délai spécifié écoulé.

   Une fois la ressource arrivée à expiration, vous recevez une notification par courrier électronique qui confirme l’expiration. En outre, les ressources expirées sont désactivées.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## États d’une ressource {#asset-states}

La console Ressources d’Adobe Experience Manager (AEM) Assets peut afficher différents états pour les ressources. En fonction de l’état actuel d’une ressource donnée, le mode Carte affiche un libellé décrivant son état (par exemple, expiré, modifié, approuvé, rejeté, etc.).

1. Dans l’interface utilisateur Assets, sélectionnez une ressource.

1. Appuyez/cliquez sur l’icône **[!UICONTROL Publier]** dans la barre d’outils. Si l’icône **Publier** n’est pas visible dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Plus]** dans la barre d’outils et recherchez l’icône **[!UICONTROL Publier]**.

1. Sélectionnez **[!UICONTROL Publier]** dans le menu, puis fermez la boîte de dialogue de confirmation.
1. Quittez le mode de sélection. L’état de publication de la ressource s’affiche au bas de sa miniature en mode d’affichage Carte. En mode Liste, la colonne Publié indique le moment auquel la ressource a été publiée.

1. Dans l’interface utilisateur Assets, sélectionnez une ressource et appuyez/cliquez sur l’icône **[!UICONTROL Propriétés]** pour afficher sa page de détails.

1. Dans l’onglet Avancé, définissez une date d’expiration pour la ressource dans le champ **[!UICONTROL Date d’expiration]** en dessous.

1. Cliquez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL Fermer]** pour afficher la console Ressources.
1. L’état de publication de la ressource indique qu’elle a expiré au bas de sa miniature en mode d’affichage Carte. En mode Liste, l’état de la ressource s’affiche comme étant **[!UICONTROL arrivée à expiration]**.

1. Dans la console Ressources, sélectionnez un dossier et créez une tâche de révision sur le dossier.
1. Recherchez et approuvez/rejetez les ressources dans la tâche de révision, puis cliquez sur **[!UICONTROL Terminé]**.
1. Accédez au dossier pour lequel vous avez créé la tâche de révision. L’état des ressources que vous avez approuvées/rejetées s’affiche en bas du mode Carte. En mode Liste, les états d’approbation et d’expiration sont affichés dans les colonnes correspondantes.

1. Pour rechercher des ressources en fonction de leur état, cliquez/appuyez sur l’icône **[!UICONTROL Rechercher]** afin d’afficher la barre Omni-recherche.

1. Appuyez sur la touche Entrée, puis cliquez/appuyez sur l’icône AEM pour afficher le panneau Rechercher.
1. Dans le panneau de recherche, appuyez/cliquez sur **[!UICONTROL État de publication]** et sélectionnez ensuite **[!UICONTROL Publié]** pour rechercher des ressources publiées dans AEM Assets.

1. Appuyez/cliquez sur **[!UICONTROL État d’approbation]**, puis sur l’option appropriée pour rechercher des ressources approuvées ou rejetées.

1. Pour rechercher des ressources en fonction de leur état d’expiration, sélectionnez **[!UICONTROL État d’expiration]** dans le panneau de recherche et choisissez l’option appropriée.

1. Vous pouvez également rechercher des éléments en fonction de plusieurs états, sous diverses facettes de recherche. Par exemple, vous pouvez rechercher les ressources publiées qui ont été approuvées dans une tâche de révision et qui n’ont pas encore expiré, en sélectionnant les options correspondantes dans les facettes de recherche.

## Digital Rights Management dans Adobe Experience Manager Assets {#digital-rights-management-in-assets-1}

Cette fonction force l’acceptation du contrat de licence avant le téléchargement d’une ressource sous licence à partir du composant Adobe Experience Manager (AEM) Assets.

Si vous sélectionnez une ressource protégée et cliquez ensuite sur l’icône **[!UICONTROL Télécharger]**, vous êtes redirigé vers une page de licence dans laquelle vous acceptez le contrat de licence. Si vous n’en acceptez pas les termes, le bouton **[!UICONTROL Télécharger]** est désactivé.

Si la sélection contient plusieurs ressources protégées, sélectionnez-en une à la fois, acceptez le contrat de licence et procédez au téléchargement de la ressource.

Une ressource est considérée comme protégée si l’une des conditions suivantes est remplie :

* La propriété de métadonnées de la ressource `xmpRights:WebStatement` pointe vers le chemin d’accès de la page CQ qui contient le contrat de licence approprié.
* La valeur de la propriété de métadonnées de la ressource `adobe_dam:restrictions` est un code HTML brut qui spécifie le contrat de licence.

>[!NOTE]
>
>L’emplacement `/etc/dam/drm/licences` utilisé pour le stockage des licences dans les versions antérieures d’AEM est obsolète.
>
>Si vous créez ou modifiez des pages de licence, ou que vous les récupérez à partir de versions précédentes d’AEM, Adobe vous recommande de les stocker sous `/apps/settings/dam/drm/licenses` ou `/conf/*/settings/dam/drm/licenses`.

### Téléchargement de ressources DRM {#downloading-drm-assets}

1. Dans l’affichage en mode Carte, sélectionnez les ressources à télécharger et cliquez ensuite sur l’icône **[!UICONTROL Télécharger]**.
1. Dans la page **[!UICONTROL Gestion des droits d’auteur]**, sélectionnez le fichier à télécharger dans la liste.
1. Dans le volet Licence, sélectionnez **[!UICONTROL Accepter]**. Une marque de sélection apparaît en regard de la ressource dont vous avez accepté le contrat de licence. Appuyez/cliquez sur le bouton **[!UICONTROL Télécharger]**.

   >[!NOTE]
   >
   >Le bouton **[!UICONTROL Télécharger]** est activé uniquement lorsque vous choisissez d’accepter le contrat de licence d’une ressource protégée. Cependant, si votre sélection comprend à la fois des ressources non protégées et protégées, seules ces dernières sont répertoriées dans le volet de gauche, et le bouton **[!UICONTROL Télécharger]** est activé pour le téléchargement des ressources non protégées. Pour accepter le contrat de licence de plusieurs ressources protégées en même temps, sélectionnez-les dans la liste, puis cliquez sur **[!UICONTROL Accepter]**.

1. Appuyez/cliquez sur **[!UICONTROL Télécharger]** dans la boîte de dialogue pour télécharger la ressource ou ses rendus.

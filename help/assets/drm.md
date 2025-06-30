---
title: Gestion des droits numériques dans  [!DNL Assets]
description: Découvrez comment gérer les informations d’expiration et d’état des ressources sous licence dans [!DNL Experience Manager] as a [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management,DRM
role: User, Admin
exl-id: fa5f94df-1c15-4593-afcb-1d24508da2bf
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 100%

---

# Gestion des droits numériques pour les ressources numériques {#digital-rights-management-in-assets}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/drm.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Les ressources numériques sont souvent associées à une licence qui prévoit les conditions et la durée de leur utilisation. En utilisant la plateforme d’[!DNL Experience Manager], vous pouvez gérer efficacement les informations d’expiration et de licence des ressources.

## Expiration de ressources {#asset-expiration}

Pour appliquer les exigences de licence des ressources, utilisez leurs informations d’expiration. Les informations d’expiration garantissent que la ressource publiée est dépubliée à son expiration, ce qui empêche toute violation de licence. Sans autorisations d’administration, un utilisateur ne peut pas modifier, copier, déplacer, publier ni télécharger une ressource arrivée à expiration.

Vous pouvez consulter l’état d’expiration d’une ressource aux emplacements suivants :

* **Mode Carte** : lorsqu’une ressource arrive à expiration, un indicateur le signale sur la carte.
* **Vue Liste** : pour une ressource arrivée à expiration, la colonne **[!UICONTROL État]** affiche la bannière **[!UICONTROL Expiré]**.
* **Chronologie** : vous pouvez consulter l’état d’expiration d’une ressource dans la chronologie. Sélectionnez la ressource et choisissez ensuite Chronologie.
* **Rail Références** : vous pouvez également afficher l’état d’expiration des ressources dans le rail **[!UICONTROL Références]**. Il gère les états d’expiration des ressources et les relations entre les ressources composites et les sous-ressources, les collections et les projets référencés.

Pour afficher les pages web de référence et les ressources composites d’une ressource, procédez comme suit :

1. Accédez à la ressource, sélectionnez-la, puis cliquez sur l’![icône des références de contenu du rail gauche](assets/do-not-localize/content-rail-icon.png). Le rail de gauche s’ouvre.
1. Sélectionnez **[!UICONTROL Références]** dans le rail de gauche.
1. Pour les ressources arrivées à expiration, les [!UICONTROL Références] affichent l’état d’expiration **[!UICONTROL La ressource est expirée]**. Si la ressource contient des sous-ressources arrivées à expiration, le rail [!UICONTROL Références] affiche le statut **[!UICONTROL La ressource contient des sous-ressources arrivées à expiration]**.

### Recherche de ressources arrivées à expiration {#search-expired-assets}

Pour rechercher une ressource arrivée à expiration, y compris les sous-ressources expirées, procédez comme suit :

1. Dans la console [!DNL Assets], cliquez sur **[!UICONTROL Rechercher]** dans la barre d’outils, puis appuyez sur `Enter`.

1. Cliquez sur l’icône de navigation globale et sélectionnez l’option **[!UICONTROL État d’expiration]**.

1. Sélectionnez **[!UICONTROL Expiré]**. Les résultats de la recherche affichent les ressources expirées.

Quand vous choisissez l’option **[!UICONTROL Expiré]**, la console [!DNL Assets] affiche seulement les ressources et les sous-ressources arrivées à expiration qui ont été référencées par des ressources composites. Les ressources composites qui référencent des sous-ressources expirées ne s’affichent pas immédiatement une fois que les sous-ressources arrivent à expiration. En réalité, elles sont affichées lorsqu’[!DNL Experience Manager] détecte qu’elles référencent des sous-ressources expirées, lors de la prochaine exécution du planificateur.

Il est possible de modifier la date d’expiration d’une ressource publiée à une date antérieure du cycle du planificateur actuel. Cependant, le planning détectera toujours une ressource comme ressource expirée lorsqu’il s’exécutera la prochaine fois et [!DNL Experience Manager] reflète l’état dans son rapport. La date d’expiration d’une ressource s’affiche différemment pour les utilisateurs de différents fuseaux horaires.

En outre, si une erreur empêche le planificateur de détecter les ressources parvenues à expiration dans le cycle en cours, le planificateur réexamine ces ressources lors du cycle suivant et identifie leur état d’expiration.

Pour que la console [!DNL Assets] affiche les ressources composites référencées avec les sous-ressources expirées, configurez un workflow de **[!UICONTROL notification d’expiration d’Adobe CQ DAM]** dans [!DNL Experience Manager]. Le planificateur temporel planifie une tâche afin de vérifier à un moment précis si une ressource contient des sous-ressources arrivées à expiration. Une fois la tâche terminée, les ressources qui possèdent des sous-ressources expirées et des ressources référencées sont affichées à l’état expiré dans les résultats de la recherche.

1. Accédez au référentiel Git [!DNL Cloud Manager] associé à votre environnement.
1. Validez un fichier nommé `com.day.cq.dam.core.impl.ExpiryNotificationJobImpl.cfg.json` dans le référentiel avec le contenu suivant.

   ```json
   {
      "send_email":"false", "asset_expired_limit":"100", "prior_notification_seconds":"86400", "cq.dam.expiry.notification.url.protocol":"http", "cq.dam.expiry.notification.scheduler.istimebased":"true", "cq.dam.expiry.notification.scheduler.period.rule":"10", "cq.dam.expiry.notification.scheduler.timebased.rule":"0 0 0 * * ?"
   }
   ```

1. Suivez les instructions détaillées dans [Comment paramétrer une configuration OSGi dans [!DNL Experience Manager] as a [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md).

Vous pouvez configurer le planificateur à l’aide des propriétés suivantes :

* Le paramétrage de la propriété `cq.dam.expiry.notification.scheduler.istimebased` comme `true` lance le planificateur. * La valeur de la propriété `cq.dam.expiry.notification.scheduler.timebased.rule` est l’expression régulière qui définit l’heure. L’exemple ci-dessus lance la tâche du planificateur à minuit.
* Si `send_email` est défini sur `true`, l’auteur de la ressource (la personne qui la charge dans [!DNL Assets]) reçoit un e-mail lorsqu’elle arrive à expiration.
* Le nombre maximal de ressources expirées dans une seule itération du planificateur est la valeur de la propriété `asset_expired_limit`.
* Pour exécuter la tâche de façon périodique, définissez la valeur de la propriété `cq.dam.expiry.notification.scheduler.istimebased` sur `false` et définissez la valeur de la propriété `cq.dam.expiry.notification.scheduler.period.rule` avec l’heure en secondes.

<!-- TBD: Web Console not available in CS.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time-based Scheduler]** is selected, which 

1. For example, the example expression '0 0 0 &ast; &ast; ?' triggers the job at 0000 hrs.

1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

1. In the **[!UICONTROL Prior notification in seconds]** field, specify the time in seconds before the asset expiry when you want to receive a notification. If you are an administrator or the asset creator, you receive a message before the expiration of the asset. After the asset expiry, you receive another notification that confirms the expiration. In addition, the expired asset is deactivated.

1. Select **[!UICONTROL Save]**.
-->

## États d’un élément {#asset-states}

La console [!DNL Assets] peut afficher différents états des ressources. En fonction de l’état actuel d’une ressource donnée, le mode Carte affiche un libellé décrivant son état (par exemple, expiré, modifié, approuvé, rejeté, etc.).

1. Dans l’interface utilisateur [!DNL Assets], sélectionnez une ressource.

1. Sélectionnez **[!UICONTROL Publier]** dans la barre d’outils. Si vous ne voyez pas l’option [!UICONTROL Publier] dans la barre d’outils, cliquez sur **[!UICONTROL Plus]** dans la barre d’outils et recherchez l’option **[!UICONTROL Publier]**.

1. Sélectionnez **[!UICONTROL Publier]** dans le menu, puis fermez la boîte de dialogue de confirmation.

1. Quittez le mode de sélection. Le statut de publication de la ressource s’affiche dans la partie inférieure de sa miniature en mode Carte. Dans la vue Liste, la colonne Publié indique le moment auquel la ressource a été publiée.

1. Pour afficher la page de détails de la ressource, sélectionnez une ressource dans l’interface [!DNL Assets], puis cliquez sur **[!UICONTROL Propriétés]**.

1. Dans l’onglet [!UICONTROL Avancé], définissez une date d’expiration pour la ressource dans le champ **[!UICONTROL Date d’expiration]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL Fermer]** pour afficher la console Ressources.

1. L’état de publication de la ressource indique qu’elle a expiré au bas de sa miniature en mode d’affichage Carte. Dans la vue Liste, l’état de la ressource s’affiche comme étant **[!UICONTROL arrivée à expiration]**.

1. Dans la console [!DNL Assets], sélectionnez un dossier et créez une tâche de révision sur le dossier.

1. Recherchez et approuvez/rejetez les ressources dans la tâche de révision, puis cliquez sur **[!UICONTROL Terminé]**.

1. Accédez au dossier pour lequel vous avez créé la tâche de révision. Le statut des ressources que vous avez approuvées/rejetées s’affiche dans la partie inférieure en mode Carte. Dans la vue Liste, les états d’approbation et d’expiration sont affichés dans les colonnes correspondantes.

1. Pour rechercher des ressources en fonction de leur état, cliquez sur **[!UICONTROL Rechercher]** pour afficher la barre de recherche.

1. Sélectionnez `Return` et cliquez sur [!DNL Experience Manager].

1. Dans le panneau de recherche, cliquez sur **[!UICONTROL État de publication]** et choisissez **[!UICONTROL Publié]** pour rechercher des ressources publiées dans [!DNL Assets].

1. Pour rechercher des ressources approuvées ou rejetées, sélectionnez **[!UICONTROL État d’approbation]** puis l’option appropriée.

1. Pour rechercher des ressources en fonction de leur état d’expiration, sélectionnez **[!UICONTROL État d’expiration]** dans le panneau de recherche et sélectionnez l’option appropriée.

1. Vous pouvez également rechercher des éléments en fonction de plusieurs états, sous diverses facettes de recherche. Par exemple, vous pouvez rechercher des ressources publiées qui sont approuvées dans une tâche de révision et qui n’ont pas expiré. Pour rechercher ces ressources, sélectionnez les options appropriées dans les facettes de recherche.

## Gestion des droits numériques dans [!DNL Assets] {#digital-rights-management-in-assets-1}

La fonctionnalité de gestion des droits numériques force l’acceptation du contrat de licence avant le téléchargement d’une ressource sous licence à partir d’[!DNL Assets].

Si vous sélectionnez une ressource protégée et que vous cliquez ensuite sur **[!UICONTROL Télécharger]**, vous êtes redirigé vers une page de licence pour vous permettre d’accepter le contrat de licence. Si vous n’en acceptez pas les termes, l’option **[!UICONTROL Télécharger]** n’est pas disponible.

Si la sélection contient plusieurs ressources protégées, sélectionnez-en une à la fois, acceptez le contrat de licence et procédez au téléchargement de la ressource.

Une ressource est considérée comme protégée si l’une de ces conditions est remplie :

* La propriété de métadonnées de la ressource `xmpRights:WebStatement` pointe vers le chemin d’accès de la page qui contient le contrat de licence approprié.
* La valeur de la propriété de métadonnées de la ressource `adobe_dam:restrictions` est un code HTML brut qui spécifie le contrat de licence.

>[!NOTE]
>
>L’emplacement `/etc/dam/drm/licences` était utilisé pour stocker des licences dans les versions antérieures d’[!DNL Experience Manager]. Cet emplacement est désormais obsolète. Si vous créez ou modifiez des pages de licence, ou si vous transférez des pages à partir de versions précédentes d’[!DNL Experience Manager], Adobe vous recommande de stocker ces ressources dans `/apps/settings/dam/drm/licenses` ou `/conf/*/settings/dam/drm/licenses`.

### Téléchargement de ressources protégées par DRM {#downloading-drm-assets}

1. Dans l’affichage en mode Carte, sélectionnez les ressources à télécharger et sélectionnez **[!UICONTROL Télécharger]**.
1. Dans la page **[!UICONTROL Gestion des droits d’auteur]**, sélectionnez la ressource à télécharger dans la liste.
1. Dans le volet [!UICONTROL Licence], sélectionnez **[!UICONTROL Accepter]**. Une coche s’affiche en regard de la ressource. Sélectionnez l’option **[!UICONTROL Télécharger]**.

   >[!NOTE]
   >
   >L’option **[!UICONTROL Télécharger]** n’est activée que si vous choisissez d’accepter le contrat de licence d’une ressource protégée. Cependant, si votre sélection comprend à la fois des ressources protégées et non protégées, seules ces dernières sont répertoriées dans le volet, et l’option **[!UICONTROL Télécharger]** est disponible pour le téléchargement des ressources non protégées. Pour accepter le contrat de licence de plusieurs ressources protégées en même temps, sélectionnez-les dans la liste, puis cliquez sur **[!UICONTROL Accepter]**.

1. Pour télécharger la ressource ou ses rendus, sélectionnez **[!UICONTROL Télécharger]** dans la boîte de dialogue.

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

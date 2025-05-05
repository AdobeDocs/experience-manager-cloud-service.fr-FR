---
title: Configuration de Dynamic Media Cloud Services
description: Découvrez la configuration de Dynamic Media dans Adobe Experience Manager as a Cloud Service.
contentOwner: Rick Brough
feature: Configuration,Dynamic Media
role: Admin,User
exl-id: 8e07bc85-ef26-4df4-8e64-3c69eae91e11
source-git-commit: 2ca425f9a142432a5d3bcce8ce522c97e4c2cf2d
workflow-type: tm+mt
source-wordcount: '3721'
ht-degree: 83%

---

# À propos de la configuration de Dynamic Media Cloud Service {#configuring-dynamic-media}

{{work-with-dynamic-media}}

Si vous utilisez Adobe Experience Manager as a Cloud Service pour différents environnements, tels que le développement, l’évaluation et la production en direct, configurez les Cloud Services Dynamic Media pour chacun de ces environnements.

Voir aussi [Configuration d’un compte d’alias de société Dynamic Media](/help/assets/dynamic-media/dm-alias-account.md)

>[!IMPORTANT]
>
>**Dynamic Media (Scene7) non pris en charge dans les environnements de sécurité renforcée**
>
>Dynamic Media (Scene7) sur AEM as a Cloud Service n’est pas compatible avec la norme HIPAA et ne peut pas être utilisé dans les environnements AEM où la sécurité renforcée est activée.
>
>À compter de la version d’avril 2025 d’AEM as a Cloud Service, une restriction technique empêche Dynamic Media (Scene7) d’être configuré dans les environnements dotés d’une sécurité renforcée. Par conséquent, la vignette **Configuration Dynamic Media** sous **Outils** > **Services cloud** n’est plus visible dans ces environnements.
>
>En outre, les clients qui utilisent AEM 6.5 doivent savoir que la pile Dynamic Media (Scene7) n’est pas conforme à la norme HIPAA.

## Schéma de l’architecture de Dynamic Media {#architecture-diagram-of-dynamic-media}

Le schéma d’architecture suivant décrit le fonctionnement de Dynamic Media.

Avec la nouvelle architecture, Experience Manager est responsable des ressources issues de sources originales et des synchronisations avec Dynamic Media pour le traitement et la publication des ressources :

1. Lorsque la ressource source principale est chargée dans Adobe Experience Manager as a Cloud Service, elle est répliquée vers Dynamic Media. À ce stade, Dynamic Media gère l’intégralité du traitement des ressources et de la génération du rendu, comme le codage vidéo et les variantes dynamiques d’une image.
1. Une fois les rendus générés, Experience Manager as a Cloud Service peut accéder en toute sécurité aux rendus Dynamic Media distants et les prévisualiser (aucune donnée binaire n’est renvoyée au Experience Manager en tant qu’instance de Cloud Service).
1. Une fois que le contenu est prêt à être publié et approuvé, il déclenche l’envoi du contenu par le service Dynamic Media vers les serveurs de diffusion et la mise en cache du contenu sur le réseau de diffusion de contenu (CDN).

![chlimage_1-550](assets/chlimage_1-550.png)

>[!NOTE]
>
>Les fonctionnalités de la liste suivante nécessitent que vous utilisiez le réseau de diffusion de contenu prêt à l’emploi fourni avec Dynamic Media d’Adobe Experience Manager. Les autres réseaux de diffusion de contenu personnalisés ne sont pas pris en charge avec ces fonctionnalités.
>
>* [Imagerie dynamique](/help/assets/dynamic-media/imaging-faq.md)
>* [Invalidation du cache](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
>* [Protection des liens dynamiques](/help/assets/dynamic-media/hotlink-protection.md)
>* [Diffusion de contenu HTTP/2](/help/assets/dynamic-media/http2faq.md)
>* Redirection d’URL au niveau du réseau de diffusion de contenu
>* Akamai ChinaCDN (pour une diffusion optimale en Chine)

<!-- OBSOLETE CONTENT

## (Optional) Migrating Dynamic Media presets and configurations from 6.3 to 6.5 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

If you are upgrading Experience Manager as a Cloud Service Dynamic Media from 6.3 to 6.4 or 6.5 (which now includes the ability for zero downtime deployments), you are required to run the following curl command to migrate all your presets and configurations from `/etc` to `/conf` in CRXDE Lite.

>[!NOTE]
>
>If you run your Experience Manager as a Cloud Service instance in compatibility mode--that is, you have the compatibility packaged installed--you do not need to run these commands.

For all upgrades, either with or without the compatibility package, you can copy the default, out-of-the-box viewer presets that originally came with Dynamic Media by running the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

To migrate any custom viewer presets and configurations that you have created from `/etc` to `/conf`, run the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

-->

## Création d’une configuration Dynamic Media dans Cloud Services {#configuring-dynamic-media-cloud-services}

<!-- **Before you creating a Dynamic Media Configuration in Cloud Services**: After you receive your provisioning email with Dynamic Media credentials, you must open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account to change your password. The password provided in the provisioning email is system-generated and intended to be a temporary password only. It is important that you update the password so that Dynamic Media Cloud Service is set up with the correct credentials. -->

1. Dans Experience Manager as a Cloud Service, sélectionnez le logo Experience Manager as a Cloud Service pour accéder à la console de navigation globale.
1. Sur le côté gauche de la console, sélectionnez l’icône Outils, puis **[!UICONTROL Cloud Services > Configuration Dynamic Media]**.
1. Sur la page du navigateur de configuration Dynamic Media, dans le volet de gauche, sélectionnez **[!UICONTROL global]**. Ne sélectionnez pas l’icône de dossier située à gauche de **[!UICONTROL global]**. Sélectionnez ensuite **[!UICONTROL Créer]**.
1. Sur la page **[!UICONTROL Création d’une configuration Dynamic Media]**, saisissez le titre, l’e-mail du compte Dynamic Media et le mot de passe de l’administrateur de la société du compte Dynamic Media, puis sélectionnez votre région. Ces informations vous sont fournies par Adobe dans l’e-mail de mise en service. Contactez le service clientèle si vous n’avez pas reçu cet e-mail.
1. Sélectionnez **[!UICONTROL Connexion à Dynamic Media]**.
1. Dans la boîte de dialogue **[!UICONTROL Modifier le mot de passe]**, dans le champ **[!UICONTROL Nouveau mot de passe]**, saisissez un nouveau mot de passe composé de 8 à 25 caractères. Le mot de passe doit contenir au moins une occurrence de chacun des types de caractères suivants :

   * Lettre majuscule
   * Lettre minuscule
   * Nombre
   * Caractère spécial : `# $ & . - _ : { }`

   Le champ **[!UICONTROL Mot de passe actuel]** est délibérément prérempli et masqué vis-à-vis des interactions.

   Si nécessaire, vous pouvez vérifier l’orthographe d’un mot de passe saisi en sélectionnant l’icône en forme d’œil pour l’afficher. Sélectionnez de nouveau l’icône pour le masquer.

1. Dans le champ **[!UICONTROL Répéter le mot de passe]**, saisissez une deuxième fois le nouveau mot de passe, puis sélectionnez **[!UICONTROL Terminé]**.

   Le nouveau mot de passe est enregistré si vous sélectionnez **[!UICONTROL Enregistrer]** dans l’angle supérieur droit de la page **[!UICONTROL Créer une configuration Dynamic Media]**.

   Si vous avez sélectionné **[!UICONTROL Annuler]** dans la boîte de dialogue **[!UICONTROL Modifier le mot de passe]**, vous devez toujours saisir un nouveau mot de passe lorsque vous enregistrez la configuration Dynamic Media créée.

   Voir aussi [Modifier le mot de passe pour Dynamic Media](#change-dm-password).

1. Si la connexion est établie, vous pouvez définir les éléments suivants :

   | Propriété | Description |
   |---|---|
   | Entreprise | Nom du compte Dynamic Media.<br>**Important** : une seule configuration Dynamic Media dans Cloud Services est prise en charge sur une instance Experience Manager, n’ajoutez donc pas plusieurs configurations. Adobe ne prend *pas* en charge ou ne recommande pas de configurer plusieurs configurations Dynamic Media sur une seule instance Experience Manager.<!-- CQDOC-19579 and CQDOC-19612 --><br>Voir aussi [Configuration d’un compte d’alias de société Dynamic Media](/help/assets/dynamic-media/dm-alias-account.md). |
   | Chemin d’accès au dossier racine de l’entreprise | Chemin d’accès au dossier racine de votre entreprise. |
   | Publier les ressources | Vous pouvez choisir parmi les trois options suivantes :<br>**[!UICONTROL Immédiatement &#x200B;]** : lorsque des ressources sont chargées, le système les ingère et fournit instantanément le lien URL/Embed. Aucune intervention n’est nécessaire de la part de l’utilisateur pour publier des ressources.<br>**[!UICONTROL Lors de l’activation]** : vous devez publier explicitement la ressource avant qu’un lien URL/Embed ne soit fourni.<br>**[!UICONTROL Publication sélective &#x200B;]** : les ressources sont publiées automatiquement pour une prévisualisation sécurisée uniquement. Elles peuvent également être publiés explicitement vers Experience Manager as a Cloud Service sans publication dans DMS7 pour une diffusion dans le domaine public. À l’avenir, cette option aura pour objectif de publier des ressources vers Experience Manager as a Cloud Service et vers Dynamic Media de façon mutuellement exclusive. En d’autres termes, vous pouvez publier des ressources dans DMS7 afin d’utiliser des fonctionnalités telles que le recadrage intelligent ou les rendus dynamiques. Vous pouvez également publier des ressources exclusivement dans Experience Manager as a Cloud Service pour leur prévisualisation. Ces mêmes ressources ne sont pas publiées dans DMS7 pour diffusion dans le domaine public. |
   | Serveur d’aperçu sécurisé | Il vous permet de spécifier le chemin URL de votre serveur d’aperçu des rendus sécurisé. En d’autres termes, une fois les rendus générés, AEM as a Cloud Service peut accéder en toute sécurité aux rendus Dynamic Media distants et les prévisualiser (aucune donnée binaire n’est renvoyée à l’instance Experience Manager as a Cloud Service).<br>À moins que vous ayez pris des dispositions spéciales pour utiliser le serveur de votre entreprise ou un serveur spécial, Adobe vous conseille de conserver ce paramètre tel que spécifié. |
   | Synchroniser tout le contenu | Sélectionné par défaut. Désélectionnez cette option si vous souhaitez inclure ou exclure des ressources de manière sélective de la synchronisation avec Dynamic Media. Lorsque cette option est désélectionnée, vous pouvez choisir parmi les deux modes de synchronisation Dynamic Media suivants :<br>**[!UICONTROL Mode de synchronisation Dynamic Media]**<br>**[!UICONTROL Activer par défaut &#x200B;]**- La configuration est appliquée par défaut à tous les dossiers, sauf si vous marquez un dossier spécifique à exclure. <!-- you can then deselect the folders that you do not want the configuration applied to.--><br>**[!UICONTROL Désactivé par défaut]** : la configuration n’est appliquée à aucun dossier tant que vous ne marquez pas explicitement un dossier sélectionné pour synchronisation avec Dynamic Media.<br>Pour marquer un dossier sélectionné afin de le synchroniser avec Dynamic Media, sélectionnez un dossier de ressources, puis, dans la barre d’outils, sélectionnez **[!UICONTROL Propriétés]**. Sous l’onglet **[!UICONTROL Détails]**, dans la liste déroulante **[!UICONTROL Mode de synchronisation Dynamic Media]**, choisissez l’une des trois options suivantes. Une fois le choix effectué, sélectionnez **[!UICONTROL Enregistrer]**. _À retenir : ces trois options ne sont pas disponibles si vous avez sélectionné auparavant **Synchroniser tout le contenu**._ Voir aussi [Utilisation de la publication sélective au niveau du dossier dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).<br>**[!UICONTROL Hérité&#x200B;]** : aucune valeur de synchronisation explicite sur le dossier. Au lieu de cela, le dossier hérite de la valeur de synchronisation de l’un de ses dossiers ancêtres ou du mode par défaut dans la configuration du cloud. Le statut détaillé de l’héritage s’affiche par le biais d’une info-bulle.<br>**[!UICONTROL Activé pour les sous-dossiers]** : incluez tous les éléments de cette sous-arborescence dans la synchronisation avec Dynamic Media. Les paramètres propres au dossier remplacent le mode par défaut dans la configuration du cloud.<br>**[!UICONTROL Désactivé pour les sous-dossiers &#x200B;]** : excluez tous les éléments de cette sous-arborescence de la synchronisation avec Dynamic Media. |

   >[!NOTE]
   >
   >Le contrôle de version n’est pas pris en charge dans Dynamic Media. En outre, l’activation différée ne s’applique que si l’option **[!UICONTROL Publier des ressources]** dans la page de configuration de Dynamic Media est définie sur **[!UICONTROL Dès l’activation]**, puis uniquement jusqu’à la première activation de la ressource.
   >
   >
   >Une fois qu’une ressource est activée, toutes les mises à jour sont immédiatement publiées en direct sur la livraison S7.

   ![dynamicmediaconfiguration2updated](/help/assets/assets-dm/dynamicmediaconfigurationupdated.png)

1. Sélectionnez **[!UICONTROL Enregistrer]**. Le nouveau mot de passe et la nouvelle configuration de Dynamic Media sont enregistrés. Si vous avez sélectionné **[!UICONTROL Annuler]** à la place, aucune mise à jour du mot de passe ne se produit.
1. Dans la boîte de dialogue **[!UICONTROL Configuration de Dynamic Media]**, sélectionnez **[!UICONTROL OK]** pour commencer la configuration.

   >[!IMPORTANT]
   >
   >Une fois la nouvelle configuration Dynamic Media terminée, vous recevez une notification d’état dans la boîte de réception d’Experience Manager as a Cloud Service.
   >
   >Cette notification de boîte de réception vous informe si la configuration a réussi ou non.
   > Pour plus d’informations, voir [Dépannage d’une nouvelle configuration Dynamic Media](#troubleshoot-dm-config) et [Votre boîte de réception](/help/sites-cloud/authoring/inbox.md).

1. Pour prévisualiser le contenu Dynamic Media en toute sécurité avant qu’il ne soit publié, Experience Manager as a Cloud Service utilise la validation basée sur les jetons et donc l’auteur Experience Manager prévisualise le contenu Dynamic Media par défaut. Cependant, vous pouvez *placer sur la liste autorisée* adresses IP supplémentaires pour permettre aux utilisateurs d’accéder à l’aperçu du contenu en toute sécurité. Pour configurer cette action dans Experience Manager as a Cloud Service, consultez l’onglet [ Configurer la configuration de publication Dynamic Media pour Image Server - Sécurité ](/help/assets/dynamic-media/dm-publish-settings.md#security-tab). <!-- To securely preview Dynamic Media content before it gets published, you must "allowlist" the Experience Manager as a Cloud Service author instance to connect to Dynamic Media. To set up this action, do the following: -->

<!--
    * Open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account. Your credentials and sign-in details were provided by Adobe at the time of provisioning. If you do not have this information, contact Adobe Customer Support.
    * On the navigation bar near the upper right corner of the page, go to **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]**.
    * On the Image Server Publish page, in the **[!UICONTROL Publish Context]** drop-down list, select **[!UICONTROL Test Image Serving]**.
    * For the Client Address Filter, select **[!UICONTROL Add]**.
    * To enable (turn on) the address, select the check box, then enter the IP address of the Experience Manager Author instance (not Dispatcher IP).
    * Select **[!UICONTROL Save]**. -->

Vous avez à présent terminé la configuration de base ; vous pouvez utiliser Dynamic Media.

Si vous souhaitez personnaliser davantage votre configuration, en activant par exemple les autorisations des listes de contrôles d’accès (ACL), vous pouvez éventuellement effectuer l’une des tâches de la rubrique [Configurer les paramètres avancés dans Dynamic Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

### Résolution des problèmes liés à une nouvelle configuration Dynamic Media {#troubleshoot-dm-config}

Une fois la nouvelle configuration Dynamic Media terminée, vous recevez une notification d’état dans la boîte de réception d’Experience Manager as a Cloud Service. Cette notification vous informe si la configuration a réussi ou non, comme le montrent les images respectives suivantes de la boîte de réception.

![Succès de la boîte de réception Experience Manager](/help/assets/dynamic-media/assets/dmconfig-inbox-success.png)

![Échec de la boîte de réception du Experience Manager](/help/assets/dynamic-media/assets/dmconfig-inbox-failure.png)

Voir aussi [Votre boîte de réception](/help/sites-cloud/authoring/inbox.md).

**Pour résoudre les problèmes liés à une nouvelle configuration Dynamic Media :**

1. Dans l’angle supérieur droit de la page Experience Manager as a Cloud Service, sélectionnez l’icône en forme de cloche, puis **[!UICONTROL Afficher tout]**.
1. Sur la page Boîte de réception, sélectionnez la notification de succès pour accéder à un aperçu du statut et des journaux de la configuration.

   Si la configuration a échoué, sélectionnez la notification d’échec, similaire à la capture d’écran ci-dessous.

   ![Échec de la configuration de Dynamic Media](/help/assets/dynamic-media/assets/dmconfig-fail-notification.png)

1. Sur la page **[!UICONTROL DMSETUP]**, passez en revue les détails de configuration qui décrivent l’échec. En particulier, notez les messages d’erreur ou les codes d’erreur. Contactez le service clientèle d’Adobe et partagez ces informations.

   ![Page de configuration Dynamic Media](/help/assets/dynamic-media/assets/dmconfig-fail-page.png)

### Modification du mot de passe pour Dynamic Media {#change-dm-password}

L’expiration du mot de passe dans Dynamic Media est fixée sur 100 ans à compter de la date actuelle du système.

Le mot de passe doit contenir au moins une occurrence de chacun des types de caractères suivants :

* Lettre majuscule
* Lettre minuscule
* Nombre
* Caractère spécial : `# $ & . - _ : { }`

Si nécessaire, vous pouvez vérifier l’orthographe d’un mot de passe saisi en sélectionnant l’icône en forme d’œil pour l’afficher. Sélectionnez de nouveau l’icône pour le masquer.

Le mot de passe modifié est enregistré lorsque vous sélectionnez **[!UICONTROL Enregistrer]** dans l’angle supérieur droit de la page **[!UICONTROL Modifier la configuration Dynamic Media]**.

1. Dans Experience Manager as a Cloud Service, sélectionnez le logo Experience Manager as a Cloud Service pour accéder à la console de navigation globale.
1. Sur le côté gauche de la console, sélectionnez l’icône Outils, puis **[!UICONTROL Cloud Services > Configuration Dynamic Media]**.
1. Sur la page Navigateur de configuration Dynamic Media, dans le volet de gauche, sélectionnez **[!UICONTROL global]**. Ne sélectionnez pas l’icône de dossier située à gauche de **[!UICONTROL global]**. Sélectionnez ensuite **[!UICONTROL Modifier]**.
1. Sur la page **[!UICONTROL Modifier la configuration Dynamic Media]**, directement au-dessous du champ **[!UICONTROL Mot de passe]**, sélectionnez **[!UICONTROL Modifier le mot de passe]**.
1. Dans la boîte de dialogue **[!UICONTROL Modifier le mot de passe]**, procédez comme suit :

   * Dans le champ **[!UICONTROL Nouveau mot de passe]**, saisissez un nouveau mot de passe.

     Le champ **[!UICONTROL Mot de passe actuel]** est délibérément prérempli et masqué vis-à-vis des interactions.

   * Dans le champ **[!UICONTROL Répéter le mot de passe]**, saisissez une deuxième fois le nouveau mot de passe, puis sélectionnez **[!UICONTROL Terminé]**.

1. Dans l’angle supérieur droit de la page **[!UICONTROL Modifier la configuration Dynamic Media]**, sélectionnez **[!UICONTROL Enregistrer]**, puis **[!UICONTROL OK]**.

## (Facultatif) Configuration des paramètres avancés dans Dynamic Media{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Pour continuer à personnaliser l’installation et la configuration de Dynamic Media ou en optimiser les performances, vous pouvez effectuer une ou plusieurs des tâches _facultatives_ suivantes :

* [(Facultatif) Activer les autorisations ACL dans Dynamic Media.](#optional-enable-acl)
* [(Facultatif) Installation et configuration des paramètres Dynamic Media](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(Facultatif) Optimiser les performances de Dynamic Media](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

<!-- Removed as per CQDOC-20701 - May need to revisit and update. In Adobe Experience Manager (AEM) as a Cloud Service, enabling Access Control List (ACL) permissions for Dynamic Media requires a different approach compared to on-premise versions (which was described below), as direct editing of OSGi configurations via the UI is not supported. Not sure how this is done now. For example, you can manage ACLs using tools like the Netcentric Access Control Tool (AC Tool), which simplifies the specification and deployment of complex ACLs in AEM but I doubt that's the recommended method.

### (Optional) Enable Access Control List permissions in Dynamic Media {#optional-enable-acl}

When you run Dynamic Media on AEM as a Cloud Service, it currently forwards `/is/image` requests to Secure Preview Image Serving without checking ACL (Access Control List) permissions on the PlatformServerServlet. You can, however, _enable_ ACL permissions. Doing so forwards the authorized `/is/image` requests. If a user is not authorized to access the asset, a "403 - Forbidden" error is displayed.

**To enable Access Control List permissions in Dynamic Media on AEM as a Cloud Service:**

1. From Adobe Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. A new browser tab opens to the **[!UICONTROL Adobe Experience Manager Web Console Configuration]** page.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. On the page, scroll to the name _Adobe CQ Scene7 PlatformServer_.

1. To the right of the name, select the pencil icon (**[!UICONTROL Edit the configuration values]**).

1. On the **com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.name** page, select the check box for the following two settings:

   * `com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.cache.enable.name` &ndash; When enabled, this setting caches permission results for two minutes (default) to save.
   * `com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.validate.userAccess.name` &ndash; When enabled, this setting validates a user's access while they preview assets by way of Dynamic Media Image Server.

   ![Enable Access Control List settings in Dynamic Media - Scene7 mode](/help/assets/dynamic-media/assets/acl.png)

1. Near the lower-right corner of the page, select **[!UICONTROL Save]**.
-->

### (Facultatif) Installation et configuration des paramètres Dynamic Media {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Utilisez l’interface utilisateur de Dynamic Media Classic pour apporter des modifications à vos paramètres Dynamic Media.

<!-- Some of the tasks above require that you open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account. -->

Les tâches d’installation et de configuration incluent :

* [Configurer la configuration de publication Dynamic Media pour Image Server](#publishing-setup-for-image-server)
* [Configurer les paramètres généraux de Dynamic Media](#configuring-application-general-settings)
* [Configuration de la gestion des couleurs](#configuring-color-management)
* [Modification des types MIME pour les formats pris en charge](#editing-mime-types-for-supported-formats)
* [Ajout de types MIME pour les formats non pris en charge](#adding-mime-types-for-unsupported-formats)
<!-- OBSOLETE BUT LEAVE FOR POSSIBLE FUTURE* [Creating batch set presets to auto-generate Image Sets and Spin Sets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) -->

#### Configurer la configuration de publication Dynamic Media pour Image Server {#publishing-setup-for-image-server}

La page Configuration de la publication Dynamic Media établit les paramètres par défaut qui déterminent la manière dont les ressources sont diffusées des serveurs Dynamic Media d’Adobe vers les sites web ou les applications.

Voir [Configurer la configuration de publication Dynamic Media pour Image Server](/help/assets/dynamic-media/dm-publish-settings.md).

#### Configurer les paramètres généraux de Dynamic Media {#configuring-application-general-settings}

Configurez l’URL **[!UICONTROL Nom du serveur de publication]** et l’URL **[!UICONTROL Nom du serveur d’origine]** Dynamic Media. Vous pouvez également indiquer les paramètres **[!UICONTROL Téléchargement vers l’application]** et **[!UICONTROL Options de téléchargement par défaut]** en fonction de votre cas d’utilisation spécifique.

Voir [Configurer les paramètres généraux de Dynamic Media](/help/assets/dynamic-media/dm-general-settings.md).

#### Configuration de la gestion des couleurs {#configuring-color-management}

La gestion des couleurs de Dynamic Media vous permet de corriger les couleurs des ressources. Avec la correction des couleurs, les ressources ingérées conservent leur espace colorimétrique (RVB, CMJN, Gris) et leur profil de couleur intégré. Lorsque vous demandez un rendu dynamique, la couleur de l’image est corrigée dans l’espace colorimétrique cible en utilisant une sortie CMJN, RVB ou grise.

Consultez [Configuration des paramètres d’image prédéfinis](/help/assets/dynamic-media/managing-image-presets.md).

Pour configurer les propriétés de couleur par défaut afin d’activer la correction des couleurs lorsque vous demandez des images :

1. Ouvrez l’[application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/fr/docs/dynamic-media-classic/using/getting-started/signing-out#getting-started) puis connectez-vous à votre compte à l’aide des informations d’identification fournies lors de la mise en service.
1. Accédez à **[!UICONTROL Configuration > Configuration de l’application]**.
1. Développez la zone **[!UICONTROL Configuration de la publication]** et sélectionnez **[!UICONTROL Image Server]**. Définissez **[!UICONTROL Contexte de publication]** sur **[!UICONTROL Imager Server]** lors de la définition des paramètres par défaut des instances de publication.
1. Faites défiler l’écran jusqu’à la propriété que vous devez modifier, par exemple, une propriété de la zone **[!UICONTROL Attributs de gestion des couleurs]**.
Vous pouvez définir les propriétés de correction des couleurs suivantes :

   | Propriété | Description |
   |---|---|
   | Espace colorimétrique CMJN par défaut | Nom du profil colorimétrique CMJN par défaut. |
   | Espace colorimétrique en niveau de gris par défaut | Nom du profil colorimétrique de niveaux de gris par défaut. |
   | Espace colorimétrique RVB par défaut | Nom du profil colorimétrique RVB par défaut. |
   | Mode de rendu de conversion des couleurs | Indique le mode de rendu. Les valeurs possibles sont les suivantes : **[!UICONTROL perception]**, **[!UICONTROL colorimétrie relative]**, **[!UICONTROL saturation]** et **[!UICONTROL colorimétrie absolue]**. Adobe recommande d’utiliser **[!UICONTROL colorimétrie relative]** comme valeur par défaut. |

1. Sélectionnez **[!UICONTROL Enregistrer]**.

Par exemple, vous pouvez définir l’**[!UICONTROL Espace colorimétrique RVB par défaut]** sur *sRVB* et l’**[!UICONTROL Espace colorimétrique CMJN par défaut]** sur *WebCoated*.

Les conséquences sont les suivantes :

* Active la correction des couleurs pour les images RVB et CMJN.
* Les images RVB qui n’ont pas de profil colorimétrique sont considérées comme se trouvant dans l’espace colorimétrique *sRVB*.
* Les images CMJN qui n’ont pas de profil colorimétrique sont considérées comme se trouvant dans l’espace colorimétrique *WebCoated*.
* Les rendus dynamiques qui renvoient une sortie RVB le font dans l’espace colorimétrique *sRVB*.
* Les rendus dynamiques qui renvoient une sortie CMJN, la renvoient dans l’espace colorimétrique *WebCoated*.

#### Modification des types MIME pour les formats pris en charge {#editing-mime-types-for-supported-formats}

Vous pouvez spécifier les types de ressources que Dynamic Media traite et personnaliser les paramètres avancés de traitement des ressources. Vous pouvez, par exemple, spécifier les paramètres de traitement des ressources de façon à ce qu’ils effectuent les opérations suivantes :

* Conversion d’un Adobe PDF en ressource de catalogue électronique.
* Convertissez un document Adobe Photoshop (.PSD) en ressource de modèle de bannière pour la personnalisation.
* Pixellisation d’un fichier Adobe Illustrator (.ai) ou d’un fichier PostScript® encapsulé Adobe Photoshop (.eps).
* Des [profils vidéo](/help/assets/dynamic-media/video-profiles.md) et des [profils d’images](/help/assets/dynamic-media/image-profiles.md) peuvent être utilisés pour définir le traitement des vidéos et des images.

Voir [Chargement de ressources](/help/assets/add-assets.md).

**Pour modifier des types MIME pour les formats pris en charge :**

1. Connectez-vous à votre Experience Manager as a Cloud Service en tant qu’administrateur de produit.
1. Dans Experience Manager as a Cloud Service, sélectionnez le logo Experience Manager as a Cloud Service pour accéder à la console de navigation globale, puis accédez à **[!UICONTROL Général > CRXDE Lite]**.

   Si vous n’avez pas accès à CRXDE Lite, reportez-vous à la section [Utilisation de CRXDE Lite](/help/implementing/developing/tools/crxde.md).

1. Dans le rail de gauche, accédez à ce qui suit :

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![Types MIME](assets/mimetypes.png)

1. Sous le dossier mimeTypes, sélectionnez un type MIME.
1. Sur le côté droit de la page CRXDE Lite, dans la partie inférieure :

   * Sélectionnez deux fois le champ **[!UICONTROL activé]**. Par défaut, tous les types MIME des ressources sont activés (définis sur **[!UICONTROL true]**), ce qui signifie que les ressources sont synchronisées avec Dynamic Media pour le traitement. Si vous voulez exclure ce type MIME de ressource du traitement, définissez ce paramètre sur **[!UICONTROL false]**.

   * Appuyez deux fois sur **[!UICONTROL jobParam]** pour ouvrir le champ de texte associé. Consultez [Types MIME pris en charge](/help/assets/file-format-support.md) pour connaître la liste des valeurs de paramètres de traitement que vous pouvez utiliser pour un type MIME donné.

1. Utilisez l’une des méthodes suivantes :
   * Répétez les étapes 3 et 4 pour modifier d’autres types de MIME.
   * Dans la barre de menus de la page CRXDE Lite, sélectionnez **[!UICONTROL Enregistrer tout]**.

1. Dans l’angle supérieur gauche de la page, sélectionnez **[!UICONTROL CRXDE Lite]** pour revenir à Experience Manager as a Cloud Service.

#### Ajout de types MIME pour les formats non pris en charge {#adding-mime-types-for-unsupported-formats}

Vous pouvez ajouter des types de MIME personnalisés pour les formats non pris en charge dans Experience Manager Assets. Pour empêcher Experience Manager de supprimer tout nouveau nœud ajouté dans CRXDE Lite, déplacez le type MIME avant `image_`. Assurez-vous également que sa valeur activée est définie sur **[!UICONTROL false]**.

**Pour ajouter des types MIME pour des formats non pris en charge :**

1. Connectez-vous à votre Experience Manager as a Cloud Service en tant qu’administrateur de produit.
1. Dans Experience Manager as a Cloud Service, accédez à **[!UICONTROL Outils > Opérations > Console web]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Un nouvel onglet du navigateur s’ouvre sur la page **[!UICONTROL Adobe Experience Manager Web Console Configuration]** (Configuration de la console web Adobe Experience Manager).

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Sur la page, faites défiler l’écran jusqu’au nom *Service de type MIME de ressource Adobe CQ Scene7* comme illustré dans la capture d’écran suivante. À droite du nom, sélectionnez **[!UICONTROL Modifier les valeurs de configuration]** (icône en forme de crayon).

   ![Modifiez les valeurs de configuration](assets/2019-08-02_16-44-56.png)

1. Sur la page **Adobe CQ Scene7 Asset MIME type Service**, sélectionnez n’importe quelle icône &lt;+>. Dans le tableau, l’emplacement du signe + que vous sélectionnez pour ajouter le nouveau type MIME n’est pas important.

   ![Service Type MIME pour les ressources Adobe CQ Scene7](assets/2019-08-02_16-27-27.png)

1. Entrez `DWG=image/vnd.dwg` dans le champ de texte vide que vous venez d’ajouter.

   Le type MIME `DWG=image/vnd.dwg` n’est fourni qu’à titre d’exemple. Le type MIME que vous ajoutez ici peut être tout autre format non pris en charge.

   ![Ajout du type MIME DWG](assets/2019-08-02_16-36-36.png)

1. Dans l’angle inférieur droit de la page, sélectionnez **[!UICONTROL Enregistrer]**.

   À ce stade, vous pouvez fermer l’onglet du navigateur dans lequel la page de configuration de la console web d’Adobe Experience Manager est ouverte.

1. Revenez à l’onglet du navigateur qui contient votre console Experience Manager as a Cloud Service.
1. Dans Experience Manager as a Cloud Service, accédez à **[!UICONTROL Outils > Général > CRXDE Lite]**.

   Si vous n’avez pas accès à CRXDE Lite, reportez-vous à la section [Utilisation de CRXDE Lite](/help/implementing/developing/tools/crxde.md).

   ![Outils > Général > CRXDE Lite](assets/2019-08-02_16-55-41.png)

1. Dans le rail de gauche, accédez à ce qui suit :

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Faites glisser le type MIME `image_vnd.dwg` et déposez-le directement au-dessus de `image_` de l’arborescence, comme dans la capture d’écran suivante.

   ![Modification d’un fichier DWG dans CRXDE Lite](assets/crxdelite_cqdoc-14627.png)

1. Une fois le type MIME toujours sélectionné, dans l`image_vnd.dwg`onglet **[!UICONTROL Propriétés]**, au niveau de la ligne **[!UICONTROL enabled]**, sous l’en-tête de colonne **[!UICONTROL Valeur]**, sélectionnez deux fois la valeur. La liste déroulante **[!UICONTROL Valeur]** est ouverte.
1. Tapez `false` dans le champ (ou sélectionnez **[!UICONTROL false]** dans la liste déroulante).

   ![Modification des types MIME dans CRXDE Lite](assets/2019-08-02_16-60-30.png)

1. Dans le coin supérieur gauche de la page CRXDE Lite, sélectionnez **[!UICONTROL Tout enregistrer]**.

### (Facultatif) Optimisation des performances de Dynamic Media {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Pour garantir la bonne exécution de Dynamic Media, Adobe recommande les actions suivantes permettant d’optimiser les performances/l’évolutivité de la synchronisation :

* [Mettez à jour les paramètres de tâche prédéfinis pour le traitement de différents formats de fichier](#update-job-para).
* [Mettez à jour les threads de traitement de file d’attente de workflows Granite prédéfinis (ressources vidéo).](#update-granite-workflow-queue-worker-threads-video)
* [Mettez à jour les threads de traitement de file d’attente de workflows transitoires Granite prédéfinis (images et ressources non vidéo)](#update-granite-transient-workflow-queue-worker-threads-images).
* [Mettez à jour le nombre maximal de connexions de téléchargement au serveur Dynamic Media Classic (Scene7)](#update-max-s7-upload-connections).

#### Mettre à jour les paramètres de tâche prédéfinis pour le traitement de différents formats de fichier {#update-job-para}

Vous pouvez régler les paramètres de tâche pour accélérer le traitement des fichiers lors du chargement. Par exemple, si vous téléchargez des fichiers PSD, mais que vous ne souhaitez pas les traiter en tant que modèles, vous pouvez définir l’extraction du calque sur false (désactivé). Dans ce cas, le paramètre de tâche affiné se présente comme suit : `process=None&createTemplate=false`.

Si vous souhaitez activer la création de modèles, utilisez les paramètres suivants : `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`.

<!-- THIS PARAGRAPH WAS REPLACED WITH THE TWO PARAGRAPHS DIRECTLY ABOVE BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe recommande d’utiliser les paramètres de tâche « affiné » suivants pour les fichiers PDF, PostScript® et PSD :

| Type de fichier | Paramètres de tâche recommandés |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

Pour mettre à jour l’un de ces paramètres, voir la section [Modification des types MIME pour les formats pris en charge](#editing-mime-types-for-supported-formats).

Voir la section [Ajout de types MIME pour les formats non pris en charge](#adding-mime-types-for-unsupported-formats).

#### Mettez à jour les threads de traitement de file d’attente de workflows Granite prédéfinis (ressources vidéo). {#update-granite-workflow-queue-worker-threads-video}

La file d’attente de workflows Granite est utilisée pour les workflows non transitoires. Dans Dynamic Media, il est utilisé pour traiter la vidéo avec le workflow **[!UICONTROL Vidéo de codage de média dynamique]**.

>[!NOTE]
>
>Pour terminer cette tâche, vous devez être connecté à Experience Manager as a Cloud Service en tant qu’administrateur de produit.

Si vous n’avez pas accès à OSGi, reportez-vous à la section [Configuration OSGi](/help/implementing/developing/components/overview.md#osgi-configuration).

**Pour mettre à jour les threads de traitement de file d’attente de workflows Granite prédéfinis (ressources vidéo), procédez comme suit :**

1. Accédez à `https://<server>/system/console/configMgr` et recherchez **Queue: Granite Workflow Queue** (File d’attente : file d’attente de workflows Granite).

   >[!NOTE]
   >
   >Il est nécessaire d’effectuer une recherche par texte au lieu d’utiliser une URL directe, car le PID OSGi est généré dynamiquement.

1. Dans le champ **[!UICONTROL Maximum Parallel Jobs]** (Nombre maximal de tâches en parallèle), modifiez le nombre en fonction de la valeur souhaitée.

   Par défaut, le nombre maximal de tâches parallèles dépend du nombre de cœurs CPU disponibles. Par exemple, sur un serveur à 4 cœurs, 2 threads de traitement sont attribués. (Une valeur comprise entre 0,0 et 1,0 est basée sur un ratio ou tout nombre supérieur à attribuera le nombre de threads de traitement.)

   Dans la plupart des cas d’utilisation, le paramètre par défaut de 0,5 est suffisant.

   ![Configuration d’une file d’attente de traitement des tâches](assets/chlimage_1-1.jpeg)

1. Sélectionnez **[!UICONTROL Enregistrer]**.

#### Mise à jour des threads de traitement de file d’attente de workflows transitoires Granite prédéfinis {#update-granite-transient-workflow-queue-worker-threads-images}

La file d’attente de workflows Granite est utilisée pour le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques (DAM)]**. Dans Dynamic Media, elle est utilisée pour l’ingestion et le traitement des images et des ressources non vidéo.

>[!NOTE]
>
>Pour terminer cette tâche, vous devez être connecté à Experience Manager as a Cloud Service en tant qu’administrateur de produit.

**Pour mettre à jour les threads de traitement de file d’attente de workflows transitoires Granite prédéfinis, procédez comme suit :**

1. Accédez à la section **Configuration de la console web Adobe Experience Manager** sur `http://<host>:<port>/system/console/configMgr`.
1. Recherchez **File d’attente : file d’attente de workflows transitoires Granite**.

   >[!NOTE]
   >
   >Il est nécessaire d’effectuer une recherche par texte au lieu d’utiliser une URL directe, car le PID OSGi est généré dynamiquement.

1. Dans le champ **[!UICONTROL Maximum Parallel Jobs]** (Nombre maximal de tâches en parallèle), modifiez le nombre en fonction de la valeur souhaitée.

   Vous pouvez augmenter le **[!UICONTROL nombre maximal de tâches en parallèle]** afin de prendre en charge un chargement de fichiers suffisamment volumineux vers Dynamic Media. La valeur exacte dépend de la capacité matérielle. Dans certains cas, tels qu’une migration initiale ou un téléchargement massif ponctuel, vous pouvez utiliser une valeur importante. Sachez toutefois que l’utilisation d’une valeur élevée (par exemple deux fois le nombre de cœurs) peut avoir des effets négatifs sur les activités simultanées. Testez et ajustez la valeur en fonction de votre cas d’utilisation particulier.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Sélectionnez **[!UICONTROL Enregistrer]**.

#### Mise à jour du nombre maximal de connexions de téléchargement au serveur Dynamic Media Classic (Scene7) {#update-max-s7-upload-connections}

Le paramètre de connexion de téléchargement de Dynamic Media Classic (Scene7) permet de synchroniser Experience Manager Assets avec les serveurs de Dynamic Media Classic.

>[!NOTE]
>
>Pour terminer cette tâche, vous devez être connecté à Experience Manager as a Cloud Service en tant qu’administrateur de produit.

**Pour mettre à jour le nombre maximal de connexions de téléchargement au serveur Dynamic Media Classic (Scene7), procédez comme suit :**

1. Accédez à `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`.
1. Dans le champ **[!UICONTROL Nombre de connexions]** et **[!UICONTROL Délai d’expiration des tâches actives]**, modifiez le nombre en fonction de vos besoins.

   Le paramètre **[!UICONTROL Nombre de connexions]** contrôle le nombre maximal de connexions HTTP pour qu’Experience Manager peut charger dans Dynamic Media. En règle générale, la valeur prédéfinie de dix connexions est suffisante.

   Le paramètre **[!UICONTROL Délai d’expiration des tâches actives]** définit la durée pendant laquelle le système attend que le serveur de diffusion publie les ressources Dynamic Media chargées. Cette valeur est de 2 100 secondes ou 35 minutes, par défaut.

   Dans la plupart des cas d’utilisation, le paramètre de 2 100 est suffisant.

   ![Service de téléchargement Adobe Scene7](assets/chlimage_1-2.jpeg)

1. Sélectionnez **[!UICONTROL Enregistrer]**.

<!-- NOTE - OBSOLETE that customisations to replication agents to transform content are no longer used; the following content is obsolete now 

### (Optional) Filtering assets for replication {#optional-filtering-assets-for-replication}

In non-Dynamic Media deployments, you replicate *all* assets (both images and video) from your Experience Manager as a Cloud Service author environment to the Experience Manager as a Cloud Service publish node. This workflow is necessary because the Experience Manager as a Cloud Service publish servers also deliver the assets.

However, in Dynamic Media deployments, because assets are delivered by way of the cloud service, there is no need to replicate those same assets to Experience Manager as a Cloud Service publish nodes. Such a "hybrid publishing" workflow avoids extra storage costs and longer processing times to replicate assets. Other content, such as Site pages, continue to be served from the Experience Manager as a Cloud Service publish nodes.

The filters provide a way for you to *exclude* assets from being replicated to the Experience Manager as a Cloud Service publish node.

#### Using default asset filters for replication {#using-default-asset-filters-for-replication}

If you are using Dynamic Media for imaging and/or video, then you can use the default filters that we provide as-is. The following filters are active by default:

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Filter</strong></td>
   <td><strong>Mimetype</strong></td>
   <td><strong>Renditions</strong></td>
  </tr>
  <tr>
   <td>Dynamic Media Image Delivery</td>
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td>
   <td><p>Starts with <strong>image/</strong></p> <p>Contains <strong>application/</strong> and ends with <strong>set</strong>.</p> </td>
   <td>The out-of-the-box "filter-images" (applies to single images assets, including interactive images) and "filter-sets" (applies to Spin Sets, Image Sets, Mixed Media Sets, and Carousel Sets) will:
    <ul>
     <li>Exclude from replication the original image and static image renditions.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Dynamic Media Video Delivery</td>
   <td>filter-video</td>
   <td>Starts with <strong>video/</strong></td>
   <td>The out-of-the-box "filter-video" will:
    <ul>
     <li>Exclude from replication the original video and static thumbnail renditions.<br /> <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Filters apply to mime types and cannot be path specific.

#### Customizing asset filters for replication {#customizing-asset-filters-for-replication}

1. In Experience Manager as a Cloud Service, select the Experience Manager as a Cloud Service logo to access the global navigation console and select the **[!UICONTROL Tools > General > CRXDE Lite]**.
1. In the left folder tree, navigate to `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` to review the filters.

   ![chlimage_1-17](assets/chlimage_1-2.png)

1. To define the Mime Type for the filter, you can locate the Mime Type as follows:

   In the left rail, expand `content > dam > <locate_your_asset> > jcr:content > metadata`, and then in the table, locate `dc:format`.

   The following graphic is an example of an asset's path to `dc:format`.

   ![chlimage_1-18](assets/chlimage_1-3.png)

   Notice that the `dc:format` for the asset `Fiji Red.jpg` is `image/jpeg`.

   To have this filter apply to all images, regardless of their format, set the value to `image/*` where `*` is a regular expression that is applied to all images of any format.

   To have the filter apply only to images of the type JPEG, enter a value of `image/jpeg`.

1. Define what renditions you want to include or exclude from replication.

   Characters that you can use to filter for replication include the following:

<table>
 <tbody>
  <tr>
   <td><strong>Character to use</strong></td>
   <td><strong>How it filters assets for replication</strong></td>
  </tr>
  <tr>
   <td>*</td>
   <td>Wildcard character<br /> </td>
  </tr>
  <tr>
   <td>+</td>
   <td>Includes assets for replication.</td>
  </tr>
  <tr>
   <td>-</td>
   <td>Excludes assets from replication.</td>
  </tr>
 </tbody>
</table>

   Navigate to `content/dam/<locate your asset>/jcr:content/renditions`.

   The following graphic is an example of an asset's renditions.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   If you only wanted to replicate the original, then you would enter `+original`.

   -->

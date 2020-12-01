---
title: Configuration de Dynamic Media Cloud Service
description: Informations sur la configuration de Dynamic Media dans Adobe Experience Manager Cloud Service.
translation-type: tm+mt
source-git-commit: 4fe879d6d75d6e264d9f0b7d9d001b1426d59823
workflow-type: tm+mt
source-wordcount: '3861'
ht-degree: 95%

---


# À propos de la configuration de Dynamic Media Cloud Service {#configuring-dynamic-media-scene-mode}

Si Adobe Experience Manager est configuré dans des environnements différents, tels que le développement, l’évaluation et la production, vous devez configurer Dynamic Media Cloud Services pour chacun de ces environnements.

## Schéma de l’architecture de Dynamic Media {#architecture-diagram-of-dynamic-media-scene-mode}

Le schéma d’architecture suivant décrit le fonctionnement de Dynamic Media.

Avec la nouvelle architecture, AEM est responsable des ressources issues de sources originales et des synchronisations avec Dynamic Media pour le traitement et la publication des ressources :

1. Lorsque la ressource issue de sources originales est chargée dans AEM, elle est répliquée vers Dynamic Media. À ce stade, Dynamic Media gère l’intégralité du traitement des ressources et de la génération du rendu, comme le codage vidéo et les variantes dynamiques d’une image.
1. Une fois les rendus générés, AEM peut accéder de manière sécurisée aux rendus Dynamic Media distants et en afficher un aperçu (aucune donnée binaire n’est renvoyée à l’instance AEM).
1. Une fois que le contenu est prêt à être publié et approuvé, il déclenche l’envoi du contenu par le service Dynamic Media vers les serveurs de diffusion et la mise en cache du contenu sur le réseau de diffusion de contenu.

![chlimage_1-550](assets/chlimage_1-550.png)

<!-- OBSOLETE CONTENT

## (Optional) Migrating Dynamic Media presets and configurations from 6.3 to 6.5 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

If you are upgrading AEM Dynamic Media from 6.3 to 6.4 or 6.5 (which now includes the ability for zero downtime deployments), you are required to run the following curl command to migrate all your presets and configurations from `/etc` to `/conf` in CRXDE Lite.

>[!NOTE]
>
>If you run your AEM instance in compatibility mode--that is, you have the compatibility packaged installed--you do not need to run these commands.

For all upgrades, either with or without the compatibility package, you can copy the default, out-of-the-box viewer presets that originally came with Dynamic Media by running the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

To migrate any custom viewer presets and configurations that you have created from `/etc` to `/conf`, run the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

-->

## Création d’une configuration Dynamic Media dans Cloud Services {#configuring-dynamic-media-cloud-services}

<!-- **Before you creating a Dynamic Media Configuration in Cloud Services**: After you receive your provisioning email with Dynamic Media credentials, you must [log in](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) to Dynamic Media Classic to change your password. The password provided in the provisioning email is system-generated and intended to be a temporary password only. It is important that you update the password so that Dynamic Media Cloud Service is set up with the correct credentials. -->

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale.
1. Sur le côté gauche de la console, appuyez sur l’icône Outils, puis sur **[!UICONTROL Cloud Services > Configuration Dynamic Media]**.
1. Sur la page du navigateur de configuration Dynamic Media, dans le volet de gauche, appuyez sur **[!UICONTROL global]** (ne sélectionnez/n’appuyez pas sur l’icône de dossier située à gauche de **[!UICONTROL global]**), puis sur **[!UICONTROL Créer]**.
1. Sur la page **[!UICONTROL Créer une configuration Dynamic Media]**, saisissez un titre, l’adresse email du compte Dynamic Media et un mot de passe, puis sélectionnez votre région. Ces informations vous sont fournies par Adobe dans l’e-mail de mise en service. Veuillez contacter le support si vous ne l’avez pas reçu.
1. Cliquez sur **[!UICONTROL Connexion à Dynamic Media]**.
1. Dans la boîte de dialogue **[!UICONTROL Modifier le mot de passe]**, dans le champ **[!UICONTROL Nouveau mot de passe]**, saisissez un nouveau mot de passe composé de 8 à 25 caractères. Le mot de passe doit contenir au moins une occurrence de chacun des types de caractères suivants :

   * Lettre majuscule
   * Lettre minuscule
   * Nombre
   * Caractère spécial : `# $ & . - _ : { }`

   Notez que le champ **[!UICONTROL Mot de passe actuel]** est délibérément prérempli et masqué vis-à-vis des interactions.

   Si nécessaire, vous pouvez vérifier l’orthographe d’un mot de passe saisi en appuyant sur l’icône en forme d’œil pour l’afficher. Appuyez de nouveau sur l’icône pour le masquer.

1. Dans le champ **[!UICONTROL Répéter le mot de passe]**, saisissez une deuxième fois le nouveau mot de passe, puis appuyez sur **[!UICONTROL Terminé]**.

   Le nouveau mot de passe est enregistré lorsque vous appuyez sur **[!UICONTROL Enregistrer]** dans le coin supérieur droit de la page **[!UICONTROL Créer une configuration Dynamic Media]**.

   Si vous avez appuyé sur **[!UICONTROL Annuler]** dans la boîte de dialogue **[!UICONTROL Modifier le mot de passe]**, vous devez toujours saisir un nouveau mot de passe lorsque vous appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration Dynamic Media qui vient d’être créée.

   Voir aussi [Modification du mot de passe pour Dynamic Media](#change-dm-password).

1. Si la connexion est établie, vous pouvez définir les éléments suivants :

   | Propriété | Description |
   |---|---|
   | Entreprise | Nom du compte Dynamic Media. Il est possible que vous disposiez de plusieurs comptes Dynamic Media pour différentes sous-marques et divisions ou différents environnements d’évaluation/de production. |
   | Chemin d’accès au dossier racine de l’entreprise | Chemin d’accès au dossier racine de votre entreprise. |
   | Publier les ressources | Vous pouvez choisir parmi les trois options suivantes :<br>**[!UICONTROL Immédiatement ]** : lorsque des ressources sont chargées, le système les ingère et fournit instantanément l’URL/le code intégré. Aucune intervention n’est nécessaire de la part de l’utilisateur pour publier des ressources.<br>**[!UICONTROL Lors de l’activation]** : vous devez publier explicitement la ressource avant qu’un lien URL/code intégré ne soit fourni.<br>**[!UICONTROL Publication sélective ]** : signifie que les ressources sont publiées automatiquement pour un aperçu sécurisé uniquement et peuvent être publiées explicitement dans AEM sans publication dans DMS7 pour une diffusion dans le domaine public. À l’avenir, Adobe améliorera cette option pour publier des ressources vers AEM et vers Dynamic Media, qui sont mutuellement exclusifs. En d’autres termes, vous pouvez publier des ressources dans DMS7 afin d’utiliser des fonctionnalités telles que le recadrage intelligent ou les rendus dynamiques. Vous pouvez également publier des ressources exclusivement dans AEM pour un aperçu ; ces mêmes ressources ne sont pas publiées dans DMS7 pour une diffusion dans le domaine public. |
   | Serveur d’aperçu sécurisé | Permet de définir le chemin URL de votre serveur d’aperçu des rendus sécurisé. En d’autres termes, une fois les rendus générés, AEM peut accéder de manière sécurisée aux rendus Dynamic Media distants et en afficher un aperçu (aucune donnée binaire n’est renvoyée à l’instance AEM).<br>À moins que vous ayez pris des dispositions spéciales pour utiliser le serveur de votre entreprise ou un serveur spécial, Adobe Systems vous conseille de conserver ce paramètre tel que spécifié. |
   | Synchroniser tout le contenu | Sélectionné par défaut. Désélectionnez cette option si vous souhaitez inclure ou exclure des ressources de la synchronisation avec Dynamic Media. La désélection de cette option vous permet de choisir l’un des deux modes de synchronisation Dynamic Media :<br>**[!UICONTROL Mode de synchronisation Dynamic Media]**<br>**[!UICONTROL Activer par défaut ]** : la configuration s’applique par défaut à tous les dossiers, sauf si vous marquez un dossier spécifique à exclure. <!-- you can then deselect the folders that you do not want the configuration applied to.--><br>**[!UICONTROL Désactivé par défaut]** : la configuration n’est appliquée à aucun dossier tant que vous ne marquez pas explicitement un dossier sélectionné pour synchronisation avec Dynamic Media.<br>Pour marquer un dossier sélectionné afin de le synchroniser avec Dynamic Media, sélectionnez un dossier de ressources, puis, dans la barre d’outils, appuyez sur **[!UICONTROL Propriétés]**. Sous l’onglet **[!UICONTROL Détails]**, dans la liste déroulante **[!UICONTROL Mode de synchronisation Dynamic Media]**, choisissez l’une des trois options suivantes. Une fois le choix effectué, appuyez sur **[!UICONTROL Enregistrer]**. *À retenir : ces trois options ne sont pas disponibles si vous avez sélectionné auparavant **Synchroniser tout le contenu**.* Voir aussi [Utilisation de la publication sélective au niveau du dossier dans Dynamic Media.](/help/assets/dynamic-media/selective-publishing.md)<br>**[!UICONTROL Hérité&#x200B;]** : aucune valeur de synchronisation explicite sur le dossier ; au lieu de cela, le dossier hérite de la valeur de synchronisation de l’un de ses dossiers ancêtres ou du mode par défaut dans la configuration du cloud. Le statut détaillé de l’héritage s’affiche par le biais d’une info-bulle.<br>**[!UICONTROL Activé pour les sous-dossiers]** : incluez tous les éléments de cette sous-arborescence dans la synchronisation avec Dynamic Media. Les paramètres propres au dossier remplacent le mode par défaut dans la configuration du cloud.<br>**[!UICONTROL Désactivé pour les sous-dossiers ]** : excluez tous les éléments de cette sous-arborescence de la synchronisation avec Dynamic Media. |

   >[!NOTE]
   >
   >Le contrôle de version n’est pas pris en charge dans Dynamic Media. En outre, l’activation différée ne s’applique que si l’option **[!UICONTROL Publier des ressources]** dans la page de configuration de Dynamic Media est définie sur **[!UICONTROL Dès l’activation]**, puis uniquement jusqu’à la première activation de la ressource.
   >
   >
   >Une fois qu’une ressource est activée, toutes les mises à jour sont immédiatement publiées en direct sur la livraison S7.

   ![dynamicmediaconfiguration2updated](/help/assets/assets-dm/dynamicmediaconfigurationupdated.png)

1. Appuyez sur **[!UICONTROL Enregistrer]**. Le nouveau mot de passe et la nouvelle configuration de Dynamic Media sont enregistrés. Si vous avez appuyé sur **[!UICONTROL Annuler]** à la place, aucune mise à jour du mot de passe ne se produit.
1. Dans la boîte de dialogue **[!UICONTROL Configuration Dynamic Media]**, appuyez sur **[!UICONTROL OK]** pour commencer la configuration.

   >[!IMPORTANT]
   >
   >Une fois la nouvelle configuration Dynamic Media terminée, vous allez recevoir une notification d’état dans la boîte de réception d’AEM.
   >
   >Cette notification de boîte de réception vous informe si la configuration a réussi ou non.
   > Pour plus d’informations, voir [Dépannage d’une nouvelle configuration Dynamic Media](#troubleshoot-dm-config) et [Votre boîte de réception](/help/sites-cloud/authoring/getting-started/inbox.md).

1. Pour afficher l’aperçu du contenu Dynamic Media en toute sécurité avant qu’il ne soit modifié, il est nécessaire de placer dans une liste autorisée l’instance d’auteur AEM à connecter à Dynamic Media. Pour effectuer cette configuration, procédez comme suit :

   * Connectez-vous à votre compte Dynamic Media Classic : [https://www.adobe.com/fr/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/fr/marketing-cloud/experience-manager/scene7-login.html). Vos informations d’identification et de connexion vous ont été communiquées par Adobe au moment de la configuration. Si vous ne disposez pas de ces informations, contactez l’assistance technique.
   * Sur la barre de navigation située en haut à droite de la page, cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Image Server]**.

   * Sur la page Publication sur hébergeur d’images, dans la liste déroulante Contexte de publication, sélectionnez **[!UICONTROL Test de l’hébergeur d’images]**.
   * Pour l’option Filtre d’adresse client, appuyez sur **[!UICONTROL Ajouter]**.
   * Cochez la case permettant d’activer l’adresse, puis saisissez l’adresse IP de l’instance d’auteur AEM (et non l’IP du Dispatcher).
   * Cliquez sur **[!UICONTROL Enregistrer]**.

Vous avez à présent terminé la configuration de base ; vous êtes prêt à utiliser Dynamic Media.

Si vous souhaitez personnaliser davantage votre configuration, vous pouvez effectuer l’une des tâches de la rubrique [Configuration des paramètres avancés dans Dynamic Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

### Dépannage d’une nouvelle configuration Dynamic Media {#troubleshoot-dm-config}

Une fois la nouvelle configuration Dynamic Media terminée, vous allez recevoir une notification d’état dans la boîte de réception d’AEM. Cette notification vous informe si la configuration a réussi ou non, comme le montrent les images respectives suivantes de la boîte de réception.

![aeminboxsuccess](/help/assets/dynamic-media/assets/dmconfig-inbox-success.png)

![aeminboxfailure](/help/assets/dynamic-media/assets/dmconfig-inbox-failure.png)

Voir aussi [Votre boîte de réception](/help/sites-cloud/authoring/getting-started/inbox.md).

**Pour résoudre les problèmes liés à une nouvelle configuration Dynamic Media**

1. Près de l’angle supérieur droit de la page AEM, appuyez sur l’icône en forme de cloche, puis sur **[!UICONTROL Afficher tout]**.
1. Sur la page Boîte de réception, appuyez sur la notification de réussite pour accéder à un aperçu de l’état et des journaux de la configuration.

   Si la configuration a échoué, appuyez sur la notification d’échec, similaire à la capture d’écran ci-dessous.

   ![dmsetupfailed](/help/assets/dynamic-media/assets/dmconfig-fail-notification.png)

1. Sur la page **[!UICONTROL DMSETUP]**, passez en revue les détails de configuration qui décrivent l’échec. En particulier, notez les messages d’erreur ou les codes d’erreur. Vous devrez contacter l’Assistance clientèle d’Adobe avec ces informations.

   ![dmsetuppage](/help/assets/dynamic-media/assets/dmconfig-fail-page.png)

### Modification du mot de passe pour Dynamic Media {#change-dm-password}

L’expiration du mot de passe dans Dynamic Media est fixée sur 100 ans à compter de la date actuelle du système.

Le mot de passe doit contenir au moins une occurrence de chacun des types de caractères suivants :

* Lettre majuscule
* Lettre minuscule
* Nombre
* Caractère spécial : `# $ & . - _ : { }`

Si nécessaire, vous pouvez vérifier l’orthographe d’un mot de passe saisi en appuyant sur l’icône en forme d’œil pour l’afficher. Appuyez de nouveau sur l’icône pour le masquer.

Le mot de passe modifié est enregistré lorsque vous appuyez sur **[!UICONTROL Enregistrer]** dans le coin supérieur droit de la page **[!UICONTROL Modifier la configuration Dynamic Media]**.

1. Dans AEM, appuyez sur le logo AEM pour accéder à la console de navigation globale.
1. Sur le côté gauche de la console, appuyez sur l’icône Outils, puis sur **[!UICONTROL Cloud Services > Configuration Dynamic Media]**.
1. Sur la page du navigateur de configuration Dynamic Media, dans le volet de gauche, appuyez sur **[!UICONTROL global]** (ne sélectionnez/n’appuyez pas sur l’icône de dossier située à gauche de **[!UICONTROL global]**), puis sur **[!UICONTROL Modifier]**.
1. Sur la page **[!UICONTROL Modifier la configuration Dynamic Media]**, directement au-dessous du champ **[!UICONTROL Mot de passe]**, appuyez sur **[!UICONTROL Modifier le mot de passe]**.
1. Dans la boîte de dialogue **[!UICONTROL Modifier le mot de passe]**, procédez comme suit :

   * Dans le champ **[!UICONTROL Nouveau mot de passe]**, saisissez un nouveau mot de passe.

      Notez que le champ **[!UICONTROL Mot de passe actuel]** est délibérément prérempli et masqué vis-à-vis des interactions.

   * Dans le champ **[!UICONTROL Répéter le mot de passe]**, saisissez une deuxième fois le nouveau mot de passe, puis appuyez sur **[!UICONTROL Terminé]**.

1. Dans l’angle supérieur droit de la page **[!UICONTROL Modifier la configuration Dynamic Media]**, appuyez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL OK.]**

## (Facultatif) Configuration des paramètres avancés dans Dynamic Media{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Si vous souhaitez personnaliser davantage l’installation et la configuration de Dynamic Media, ou en optimiser les performances, vous pouvez effectuer une ou plusieurs des tâches *facultatives* suivantes :

* [Installation et configuration des paramètres Dynamic Media](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(Facultatif) Optimisation des performances de Dynamic Media](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (Facultatif) Installation et configuration des paramètres Dynamic Media {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Utilisez l’interface utilisateur de Dynamic Media Classic (Scene7) pour apporter des modifications à vos paramètres Dynamic Media.

Certaines des tâches ci-dessus nécessitent que vous vous connectiez à Dynamic Media Classic (Scene7) à l’adresse suivante : [https://www.adobe.com/fr/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

Les tâches d’installation et de configuration incluent :

* [Configuration de la publication pour Image Server](#publishing-setup-for-image-server)
* [Configuration des paramètres généraux de l’application](#configuring-application-general-settings)
* [Configuration de la gestion des couleurs](#configuring-color-management)
* [Modification des types MIME pour les formats pris en charge](#editing-mime-types-for-supported-formats)
* [Ajouter les types MIME pour les formats non pris en charge](#adding-mime-types-for-unsupported-formats)

<!-- * [Creating batch set presets to auto-generate Image Sets and Spin Sets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) -->

#### Configuration de la publication pour Image Server  {#publishing-setup-for-image-server}

Les paramètres de configuration de la publication déterminent comment les ressources sont diffusées par défaut à partir de Dynamic Media. Si aucun paramètre n’est spécifié, Dynamic Media diffuse une ressource selon les paramètres par défaut définis dans Configuration de la publication. Par exemple, une requête de diffusion d’image qui ne comporte pas d’attribut de résolution produit une image avec le paramètre de résolution d’objet par défaut.

Pour définir la configuration de la publication : dans Dynamic Media Classic, cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Image Server]**.

L’écran Image Server permet de définir les paramètres par défaut pour la diffusion des images. Voir l’écran de l’interface utilisateur pour la description de chaque paramètre.

**[!UICONTROL Attributs de requête]** : ces paramètres imposent des limites aux images qui peuvent être diffusées à partir du serveur.
**[!UICONTROL Attributs de requête par défaut]** : ces paramètres concernent l’aspect par défaut des images.
**[!UICONTROL Attributs de miniature courants]** : ces paramètres concernent l’aspect par défaut des images miniatures.
**[!UICONTROL Valeurs par défaut des champs de catalogue]** : ces paramètres concernent la résolution et le type de miniature par défaut des images.
**[!UICONTROL Attributs de gestion des couleurs]** : ces paramètres déterminent les profils de couleurs ICC utilisés.
**[!UICONTROL Attributs de compatibilité]** : ce paramètre permet aux paragraphes de début et de fin des calques de texte d’être traités tels qu’ils l’étaient dans la version 3.6, ce qui les rend rétrocompatibles.
**[!UICONTROL Aide à la localisation]** : ces paramètres vous permettent de gérer divers attributs de paramètres régionaux. Ils vous permettent également de définir une chaîne de mappage de paramètres régionaux afin de définir les langues à prendre en charge pour les différentes info-bulles dans les visionneuses. Pour plus d’informations sur la configuration de la **[!UICONTROL prise en charge de la localisation]**, voir [Considérations à prendre en compte lors de la configuration de la localisation des ressources](https://help.adobe.com/fr_FR/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html).

#### Configuration des paramètres généraux de l’application {#configuring-application-general-settings}

Pour ouvrir la page Paramètres généraux de l’application, dans la barre de navigation globale de Dynamic Media Classic, cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres généraux]**.

**[!UICONTROL Serveurs]** : au moment de la mise en service du compte, Dynamic Media fournit automatiquement les serveurs attribués à votre entreprise. Ces serveurs sont utilisés pour créer des chaînes URL pour votre site web et vos applications. Ces appels d’URL sont spécifiques à votre compte. Ne modifiez le nom d’aucun des serveurs à moins que le support AEM ne vous le demande explicitement.
**[!UICONTROL Écraser les images]** : Dynamic Media ne permet pas que deux fichiers portent le même nom. L’identifiant de l’URL de chaque élément (le nom de fichier sans l’extension) doit être unique. Ces options spécifient la manière dont les ressources de remplacement sont chargées : elles peuvent remplacer l’original ou devenir un doublon. Les ressources en double sont renommées en ajoutant « -1 » (par exemple, chaise.tif devient chaise-1.tif). Ces options affectent les ressources chargées dans un dossier autre que celui d’origine ou les ressources dont l’extension est différente de celle du fichier d’origine (telle que JPG, TIF ou PNG).
**[!UICONTROL Écraser dans dossier actuel, même nom/même extension de fichier de base]** : cette option est la règle la plus stricte pour le remplacement. Elle implique que vous chargiez l’image de remplacement dans le même dossier que l’original, et qu’elle ait la même extension que le fichier d’origine. Si ces conditions ne sont pas remplies, un doublon est créé. Pour préserver la compatibilité avec AEM, sélectionnez toujours **[!UICONTROL Écraser dans dossier actuel, même nom/même extension de fichier de base]**.
**[!UICONTROL Écraser dans un dossier, même nom/même extension de fichier de base]** : nécessite que l’image de remplacement ait la même extension que l’image d’origine (par exemple, chaise.jpg peut remplacer uniquement chaise.jpg, et non chaise.tif). Vous pouvez néanmoins télécharger l’image de remplacement dans un dossier différent de celui de l’image d’origine. L’image mise à jour se trouve dans le nouveau dossier ; le fichier d’origine n’est plus disponible à l’emplacement d’origine..
**[!UICONTROL Écraser dans un dossier, même nom de fichier, extension indépendante]** : cette option est la règle de remplacement la plus inclusive. Elle vous permet de charger une image de remplacement dans un dossier autre que celui de l’image d’origine, de charger un fichier dont l’extension est différente de celle du fichier d’origine et de remplacer le fichier d’origine. Si le fichier d’origine se trouve dans un dossier différent, l’image de remplacement est enregistrée dans le nouveau dossier où elle a été chargée.
**[!UICONTROL Profils de couleurs par défaut]** : voir [Configuration de la gestion des couleurs](#configuring-color-management) pour plus d’informations. Par défaut, le système affiche 15 rendus lorsque vous sélectionnez **[!UICONTROL Rendus]** et 15 paramètres prédéfinis de la visionneuse lorsque vous sélectionnez **[!UICONTROL Visionneuses]** dans la vue détaillée de la ressource. Vous pouvez augmenter cette limite. Voir [Augmentation ou diminution du nombre de paramètres d’image prédéfinis qui s’affichent](/help/assets/dynamic-media/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) ou [Augmentation ou diminution du nombre de paramètres prédéfinis de la visionneuse qui s’affichent](/help/assets/dynamic-media/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### Configuration de la gestion des couleurs {#configuring-color-management}

La gestion des couleurs de Dynamic Media vous permet de corriger les couleurs des ressources. Avec la correction des couleurs, les ressources intégrées conservent leur espace colorimétrique (RVB, CMJN, gris) et leur profil de couleur intégré. Lorsque vous demandez un rendu dynamique, la couleur de l’image est corrigée dans l’espace colorimétrique cible en utilisant une sortie CMJN, RVB ou grise. Reportez-vous à la section [Configuration des paramètres d’image prédéfinis](/help/assets/dynamic-media/managing-image-presets.md).

Pour configurer les propriétés de couleur par défaut afin d’activer la correction des couleurs lorsque vous demandez des images :

1. [Connectez-vous à Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) à l’aide des informations d’identification fournies lors de la mise en service. Accédez à **[!UICONTROL Configuration > Configuration de l’application]**.
1. Développez la zone **[!UICONTROL Configuration de la publication]** et sélectionnez **[!UICONTROL Image Server]**. Définissez **[!UICONTROL Contexte de publication]** sur **[!UICONTROL Imager Server]** lors de la définition des paramètres par défaut des instances de publication.
1. Faites défiler l’écran jusqu’à la propriété que vous devez modifier, par exemple, une propriété de la zone **[!UICONTROL Attributs de gestion des couleurs]**.
Vous pouvez définir les propriétés de correction des couleurs suivantes :

   | Propriété | Description |
   |---|---|
   | Espace colorimétrique CMJN par défaut | Nom du profil colorimétrique CMJN par défaut. |
   | Espace colorimétrique de niveaux de gris par défaut | Nom du profil colorimétrique de niveaux de gris par défaut. |
   | Espace colorimétrique RVB par défaut | Nom du profil colorimétrique RVB par défaut. |
   | Mode de rendu de conversion des couleurs | Indique le mode de rendu. Les valeurs possibles sont les suivantes : **[!UICONTROL perception]**, **[!UICONTROL colorimétrie relative]**, **[!UICONTROL saturation]** et **[!UICONTROL colorimétrie absolue.]** Adobe recommande d’utiliser **[!UICONTROL colorimétrie relative]** comme valeur par défaut. |

1. Appuyez sur **[!UICONTROL Enregistrer]**.

Par exemple, vous pouvez définir l’**[!UICONTROL Espace colorimétrique RVB par défaut]** sur *sRVB* et l’**[!UICONTROL Espace colorimétrique CMJN par défaut]** sur *WebCoated*.

Cela aura les effets suivants :

* Active la correction des couleurs pour les images RVB et CMJN.
* Les images RVB qui n’ont pas de profil colorimétrique seront considérées comme se trouvant dans l’espace colorimétrique *sRVB*.
* Les images CMJN qui n’ont pas de profil colorimétrique seront considérées comme se trouvant dans l’espace colorimétrique *WebCoated*.
* Les rendus dynamiques qui renvoient une sortie RVB le feront dans l’espace colorimétrique *sRVB*.
* Les rendus dynamiques qui renvoient une sortie CMJN, la renverront dans l’espace colorimétrique *WebCoated*.

#### Modification des types MIME pour les formats pris en charge {#editing-mime-types-for-supported-formats}

Vous pouvez définir les types de fichier qui sont traités par Contenu multimédia dynamique et personnaliser les paramètres avancés de traitement des fichiers. Vous pouvez, par exemple, spécifier les paramètres de traitement des ressources de façon à ce qu’ils effectuent les opérations suivantes :

* Conversion d’un PDF Adobe en ressource de catalogue électronique.
* Conversion d’un document Adobe Photoshop (.psd) en ressource de modèle de bannière afin de permettre la personnalisation.
* Pixellisation d’un fichier Adobe Illustrator (.ai) ou d’un fichier PostScript encapsulé Adobe Photoshop (.eps).
* [Les ](/help/assets/dynamic-media/video-profiles.md) profils vidéo et les  [profils ](/help/assets/dynamic-media/image-profiles.md) d’imagerie peuvent être utilisés pour définir le traitement des vidéos et des images, respectivement.

Voir la section [Chargement des ressources](/help/assets/add-assets.md).

**Pour modifier les types MIME pour les formats pris en charge**

1. Dans AEM, cliquez sur le logo AEM pour accéder à la console de navigation globale, puis cliquez sur **[!UICONTROL Général > CRXDE Lite]**.
1. Dans le rail de gauche, accédez à ce qui suit :

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. Sous le dossier mimeTypes, sélectionnez un type MIME.
1. Sur le côté droit de la page CRXDE Lite, dans la partie inférieure :

   * Doublon-cliquez sur le champ **[!UICONTROL enabled]**. Par défaut, tous les types MIME des ressources sont activés (définis sur **[!UICONTROL true]**), ce qui signifie que les ressources seront synchronisées avec Dynamic Media pour le traitement. Si vous souhaitez exclure le traitement de ce type MIME de ressource, modifiez ce paramètre en **[!UICONTROL false]**.

   * Cliquez avec le doublon **[!UICONTROL jobParam]** pour ouvrir le champ de texte associé. Voir [Types MIME pris en charge](/help/assets/file-format-support.md) pour connaître la liste des valeurs de paramètres de traitement que vous pouvez utiliser pour un type MIME donné.

1. Utilisez l’une des méthodes suivantes :
   * Répétez les étapes 3 et 4 pour modifier d’autres types MIME.
   * Dans la barre de menus de la page CRXDE Lite, cliquez sur **[!UICONTROL Enregistrer tout]**.

1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL CRXDE Lite]** pour revenir dans AEM.

#### Ajouter les types MIME pour les formats non pris en charge {#adding-mime-types-for-unsupported-formats}

Vous pouvez ajouter des types MIME personnalisés pour les formats non pris en charge dans AEM Assets. Pour vous assurer que tout nouveau nœud ajouté dans CRXDE Lite n’est pas supprimé par AEM, vous devez vous assurer que vous déplacez le type MIME avant `image_` et que sa valeur activée est définie sur **[!UICONTROL false]**.

**Pour ajouter des types MIME pour des formats non pris en charge**

1. Dans AEM, appuyez sur **[!UICONTROL Outils > Opérations > Console web]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Un nouvel onglet du navigateur s’ouvre sur la page **[!UICONTROL Adobe Experience Manager Web Console Configuration]** (Configuration de la console web Adobe Experience Manager).

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Sur la page, faites défiler l’écran jusqu’à atteindre *Adobe CQ Scene7 Asset MIME type Service*, comme illustré ci-dessous. À droite du nom, appuyez sur **[!UICONTROL Modifier les valeurs de configuration]** (icône en forme de crayon).

   ![2019-08-02_16-44-56](assets/2019-08-02_16-44-56.png)

1. Sur la page **Adobe CQ Scene7 Asset MIME type Service**, cliquez sur n’importe quel icône &lt;+>. Dans le tableau, l’emplacement du signe + sur lequel vous cliquez pour ajouter le nouveau type MIME n’est pas important.

   ![2019-08-02_16-27-27](assets/2019-08-02_16-27-27.png)

1. Entrez `DWG=image/vnd.dwg` dans le champ de texte vide que vous venez d’ajouter.

   Notez que l’exemple `DWG=image/vnd.dwg` est fourni à titre d’illustration uniquement. Le type MIME que vous ajoutez ici peut être tout autre format non pris en charge.

   ![2019-08-02_16-36-36](assets/2019-08-02_16-36-36.png)

1. Dans le coin inférieur droit de la page, appuyez sur **[!UICONTROL Save]** (Enregistrer).

   À ce stade, vous pouvez fermer l’onglet du navigateur dans lequel la page de configuration de la console web d’Adobe Experience Manager est ouverte.

1. Revenez à l’onglet du navigateur dans lequel votre console AEM est ouverte.
1. Dans AEM, appuyez sur **[!UICONTROL Outils > Général > CRXDE Lite]**.

   ![2019-08-02_16-55-41](assets/2019-08-02_16-55-41.png)

1. Dans le rail de gauche, accédez à ce qui suit :

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Faites glisser le type MIME `image_vnd.dwg` et déposez-le directement au-dessus de `image_` de l’arborescence, comme dans la capture d’écran suivante.

   ![crxdelite_cqdoc-14627](assets/crxdelite_cqdoc-14627.png)

1. Avec le type MIME `image_vnd.dwg` toujours sélectionné, dans l’onglet **[!UICONTROL Propriétés]**, au niveau de la ligne **[!UICONTROL enabled]**, sous l’en-tête de colonne **[!UICONTROL Valeur]**, double-cliquez sur la valeur pour ouvrir la liste déroulante **[!UICONTROL Valeur]**.
1. Tapez `false` dans le champ (ou sélectionnez **[!UICONTROL false]** dans la liste déroulante).

   ![2019-08-02_16-60-30](assets/2019-08-02_16-60-30.png)

1. Dans le coin supérieur gauche de la page CRXDE Lite, cliquez sur **[!UICONTROL Enregistrer tout]**.

<!-- #### Creating batch set presets to auto-generate Image Sets and Spin Sets {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

Use batch set presets to automate the creation of image sets or spin sets while assets are uploaded to Dynamic Media.

First, define the naming convention for how assets should be grouped together in a set. You can then create a batch set preset which is a uniquely named, self-contained set of instructions that defines how to construct the set using images that match the defined naming conventions in the preset recipe.

When you upload files, Dynamic Media automatically creates a set with all files that match the defined naming convention in the active presets.

**Configuring default naming**

Create a default naming convention that is used in any batch set preset recipe. The default naming convention selected in the batch set preset definition may be all your company needs to batch-generate sets. A batch set preset is created to use the default naming convention that you define. You are able to create as many Batch Set presets with alternate, custom naming conventions needed for a particular set of content in cases where there is an exception to the company-defined default naming.

While setting up a default naming convention is not required to use batch set preset functionality, best practice recommends that you use the default naming convention to define as many elements of your naming convention that you want grouped in a set so you can streamline batch set creation.

As an alternative, note that you can use **[!UICONTROL View Code]** with no form fields available. In this view you create your naming convention definitions entirely using regular expressions.

Two elements are available for definition, Match and Base Name. These fields let you define all elements of a naming convention and identify the part of the convention used to name the set in which they are contained. A company’s individual naming convention may make use of one or more lines of definition for each of these elements. You can use as many lines for your unique definition and group them into distinct elements, such as for Main Image, Color element, Alternate View element, and Swatch element.

**To configure default naming**

1. Log on to your Dynamic Media Classic (Scene7) account: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Your credentials and logon were provided by Adobe at the time of provisioning. If you do not have this information, contact Technical Support.

1. On the navigation bar near the top of the page, tap **[!UICONTROL Setup > Application Setup > Batch Set Presets > Default Naming]**.
1. Select **[!UICONTROL View Form]** or **[!UICONTROL View Code]** to specify how you want to view and enter information about each element.

   You can select the **[!UICONTROL View Code]** check box to view the regular expression value building alongside your form selections. You are able to enter or alter these values to help define the elements of the naming convention, if the form view limits you for any reason. If your values are unable to be parsed in the form view, the form fields become inactive.

   >[!NOTE]
   >
   >De-activated form fields perform no validation that your regular expressions are correct. You see results of the regular expression you are building for each element after the Result line. The complete regular expression is visible at the bottom of the page.

1. Expand each element as necessary and enter the naming conventions you want to use.
1. As necessary, do any of the following:

    * Tap **[!UICONTROL Add]** to add another naming convention for an element.
    * Tap **[!UICONTROL Remove]** to delete a naming convention for an element.

1. Do one of the following:

    * Tap **[!UICONTROL Save As]** and type a name for the preset.
    * Tap **[!UICONTROL Save]** if you are editing an existing preset.

**Creating a Batch Set Preset**

Dynamic Media uses batch set presets to organize assets into sets of images (alternate images, color options, 360 spin) for display in viewers. The batch set presets automatically run alongside the asset upload processes in Dynamic Media.

You can create, edit, and manage your batch set presets. There are two forms of batch set preset definitions: one for a default naming convention that you might have set up, and one for custom naming conventions that you create on the fly.

You can use either the form field method to define a batch set preset or the code method, which lets you use regular expressions. As in Default Naming, you can choose View Code at the same time you are defining in the Form View and use regular expressions to build your definitions. Alternately, you can uncheck either view to use one or the other exclusively.

**To create a Batch Set Preset**

1. Log on to your Dynamic Media Classic (Scene7) account: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Your credentials and logon were provided by Adobe at the time of provisioning. If you do not have this information, contact Technical Support.

1. On the navigation bar near the top of the page, tap **[!UICONTROL Setup > Application Setup > Batch Set Presets > Batch Set Preset]**.

   Note that **[!UICONTROL View Form]**, as set in the upper-right corner of the Details page, is the default view.

1. In the Preset List panel, tap **[!UICONTROL Add]** to activate the definition fields in the Details panel on the right hand side of the screen.
1. In the Details panel, in the Preset Name field, type a name for the preset.
1. In the Batch Set Type drop-down menu, select a preset type.
1. Do one of the following:

    * If you are using a default naming convention that you previously set up under **[!UICONTROL Application Setup > Batch Set Presets > Default Naming]**, expand **[!UICONTROL Asset Naming Conventions]**, and then in the File Naming drop-down list, tap **[!UICONTROL Default]**.

    * To define a new naming convention as you set up the preset, expand **[!UICONTROL Asset Naming Conventions]**, and then in the File Naming drop-down list, click **[!UICONTROL Custom]**.

1. For Sequence order, define the order in which images are displayed after the set is grouped together in Dynamic Media.

   By default, your assets are ordered alphanumerically. However, you can use a comma-separated list of regular expressions to define the order.

1. For Set Naming and Creation Convention, specify the suffix or prefix to the base name you defined in the Asset Naming Convention. Also, define where the set will be created within the Dynamic Media folder structure.

   If you define large numbers of sets, you may prefer to keep these separate from the folders that contain the assets themselves. For example, you can create an Image Sets folder and place generated sets here.

1. In the Details panel, tap **[!UICONTROL Save]**.
1. Tap **[!UICONTROL Active]** next to the new preset name.

   Activating the preset ensures that when you upload assets to Dynamic Media, the batch set preset is applied to generate the set.

**Creating a Batch Set Preset for the auto-generation of a 2D Spin Set**

You can use the Batch Set Type **[!UICONTROL Multi-Axis Spin Set]** to create a recipe that automates the generation of 2D Spin Sets. The grouping of images uses Row and Column regular expressions so that the image assets are properly aligned in the corresponding location in the multi-dimensional array. There is no minimum or maximum number of rows or columns that you must have in a multi-axis spin set.

As an example, suppose you want to create a multi-axis spin set named `spin-2dspin`. You have a set of spin set images that contain three rows, with 12 images per row. The images are named as follows:

```
spin-01-01
 spin-01-02
 …
 spin-01-12
 spin-02-01
 …
 spin-03-12
```

With this information, your Batch Set Type recipe might be created as follows:

![chlimage_1-560](assets/chlimage_1-560.png)

Grouping for the shared asset name part of the spinset is added to the **Match** field (as highlighted). The variable part of the asset name containing the row and column is added to the **Row** and **Column** fields, respectively.

When the Spin Set is uploaded and published, you would activate the name of the 2D Spin Set recipe that is listed under **Batch Set Presets** in the **Upload Job Options** dialog box.

**To create a Batch Set Preset for the auto-generation of a 2D Spin Set**

1. Log on to your Dynamic Media Classic (Scene7) account: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Your credentials and logon were provided by Adobe at the time of provisioning. If you do not have this information, contact Technical Support.

1. On the navigation bar near the top of the page, click **[!UICONTROL Setup > Application Setup] > [!UICONTROL Batch Set Presets] > [!UICONTROL Batch Set Preset]**.

   Note that **[!UICONTROL View Form]**, as set in the upper-right corner of the Details page, is the default view.

1. In the Preset List panel, click **[!UICONTROL Add]** to activate the definition fields in the Details panel on the right hand side of the screen.
1. In the Details panel, in the Preset Name field, type a name for the preset.
1. In the Batch Set Type drop-down menu, select **[!UICONTROL Asset Set]**.
1. In the Sub Type drop-down list, select **[!UICONTROL Multi-Axis Spin Set]**.
1. Expand **[!UICONTROL Asset Naming Conventions]**, and then in the File Naming drop-down list, click **[!UICONTROL Custom]**.
1. Use the **[!UICONTROL Match]** and, optionally, **[!UICONTROL Base Name]** attributes to define a regular expression for the naming of image assets that make up the grouping.

   For example, your literal Match regular expression might look like the following:

   `(w+)-w+-w+`

1. Expand **[!UICONTROL Row Column Position]**, and then define the name format for the position of the image asset within the 2D Spin Set array.

   Use the parenthesis to embrace the row or column position in the file name.

   For example, for your row regular expression, it might look like the following:

   `\w+-R([0-9]+)-\w+`

   or

   `\w+-(\d+)-\w+`

   For your column regular expression, it might look like the following:

   `\w+-\w+-C([0-9]+)`

   or

   `\w+-\w+-C(\d+)`

   Remember that these are only examples. You can create your regular expression however you want to suit your needs.

   >[!NOTE]
   >
   >If the combination of row and column regular expressions is unable to determine the position of the asset within the multi-dimensional spinset array, then that asset is not added to the set and an error is logged.

1. For Set Naming and Creation Convention, specify the suffix or prefix to the base name you defined in the Asset Naming Convention.

   Also, define where the spin set will be created within the Dynamic Media Classic folder structure.

   If you define large numbers of sets, you may prefer to keep these separate from the folders that contain the assets themselves. For example, create a Spin Sets folder to place generated sets here.

1. In the Details panel, click **[!UICONTROL Save]**.
1. Click **[!UICONTROL Active]** next to the new preset name.

   Activating the preset ensures that when you upload assets to Dynamic Media, the batch set preset is applied to generate the set. -->

### (Facultatif) Optimisation des performances de Dynamic Media{#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Pour garantir la bonne exécution de Dynamic Media <!--(with `dynamicmedia_scene7` run mode)-->, Adobe recommande les actions suivantes permettant d’optimiser les performances/l’évolutivité de la synchronisation :

* Mise à jour des paramètres de tâche prédéfinis pour le traitement de différents formats de fichier.
* Mise à jour des threads de traitement de file d’attente de workflows Granite prédéfinis (ressources vidéo).
* Mise à jour des threads de traitement de file d’attente de workflows Granite prédéfinis (images et ressources non vidéo).
* Mise à jour du nombre maximal de connexions de chargement au serveur Dynamic Media Classic.

#### Mise à jour des paramètres de tâche prédéfinis pour le traitement de différents formats de fichier

Vous pouvez régler les paramètres de tâche pour accélérer le traitement des fichiers lors du chargement. Par exemple, si vous téléchargez des fichiers PSD, mais que vous ne souhaitez pas les traiter en tant que modèles, vous pouvez définir l’extraction du calque sur false (désactivé). Dans ce cas, le paramètre de tâche affiné apparaîtra sous la forme `process=None&createTemplate=false`.

Adobe recommande d’utiliser les paramètres de tâche « affiné » suivants pour les fichiers PDF, Postscript et PSD :

| Type de fichier | Paramètres de tâche recommandés |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| Postscript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- To update any of these parameters, follow the steps in [Enabling MIME type-based Assets/Dynamic Media Classic upload job parameter support](#enabling-mime-type-based-assets-scene-upload-job-parameter-support). -->

#### Mise à jour de la file d’attente de workflows transitoires Granite {#updating-the-granite-transient-workflow-queue}

La file d’attente de workflows Granite est utilisée pour le workflow **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**. Dans Dynamic Media, elle est utilisée pour l’intégration et le traitement des images.

**Pour mettre à jour la file d’attente de workflows transitoires Granite**

1. Accédez à [https://&lt;serveur>/system/console/configMgr](https://localhost:4502/system/console/configMgr) et recherchez **Queue: Granite Transient Workflow Queue** (File d’attente : file d’attente de workflows transitoires Granite).

   >[!NOTE]
   >
   >Il est nécessaire d’effectuer une recherche par texte au lieu d’utiliser une URL directe, car le PID OSGi est généré dynamiquement.

1. Dans le champ **[!UICONTROL Maximum Parallel Jobs]** (Nombre maximal de tâches en parallèle), modifiez le nombre en fonction de la valeur souhaitée.

   Vous pouvez augmenter **[!UICONTROL le nombre maximal de tâches parallèles]** afin de prendre en charge un chargement important de fichiers dans Contenu multimédia dynamique. La valeur exacte dépend de la capacité matérielle. Dans certains cas, c’est-à-dire lors d’une migration initiale ou d’un transfert en vrac unique, vous pouvez utiliser une valeur importante. Sachez toutefois que l’utilisation d’une valeur élevée (par exemple deux fois le nombre de coeurs) peut avoir des effets négatifs sur d’autres activités simultanées. Vous devez donc tester et ajuster la valeur en fonction de votre cas d’utilisation particulier.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

#### Mise à jour de la file d’attente de workflows Granite {#updating-the-granite-workflow-queue}

La file d’attente de workflows Granite est utilisée pour les workflows non transitoires. Dans Dynamic Media, elle est utilisée pour le traitement de la vidéo avec le workflow **[!UICONTROL Vidéo de codage Dynamic Media]**.

Pour mettre à jour la file d’attente de workflows Granite :

1. Accédez à `https://<server>/system/console/configMgr` et recherchez **Queue: Granite Workflow Queue** (File d’attente : file d’attente de workflows Granite).

   >[!NOTE]
   >
   >Il est nécessaire d’effectuer une recherche par texte au lieu d’utiliser une URL directe, car le PID OSGi est généré dynamiquement.

1. Dans le champ **[!UICONTROL Maximum Parallel Jobs]** (Nombre maximal de tâches en parallèle), modifiez le nombre en fonction de la valeur souhaitée.

   Par défaut, le nombre maximal de tâches en parallèle dépend du nombre de cœurs de processeur disponibles. Par exemple, sur un serveur à 4 cœurs, 2 threads de traitement sont attribués. (Une valeur comprise entre 0,0 et 1,0 est basée sur un ratio, ou tout nombre supérieur à 1 attribuera le nombre de threads de traitement.)

   Dans la plupart des cas d’utilisation, le paramètre par défaut de 0,5 est suffisant.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

#### Mise à jour de la connexion de chargement vers Scene7 {#updating-the-scene-upload-connection}

Le paramètre de connexion de chargement vers Scene7 synchronise les ressources AEM avec les serveurs Dynamic Media Classic.

Pour mettre à jour la connexion de chargement vers Scene7 :

1. Accédez à `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`.
1. Dans le champ **[!UICONTROL Number of connections]** (Nombre de connexions) et/ou **[!UICONTROL Active job timeout]** (Délai d’expiration des tâches actives), modifiez le nombre en fonction de vos besoins.

   Le paramètre **[!UICONTROL Number of connections]** contrôle le nombre maximal de connexions HTTP autorisées pour le chargement d’AEM vers Dynamic Media. En règle générale, la valeur prédéfinie de 10 connexions est suffisante.

   Le paramètre **[!UICONTROL Active job timeout]** détermine le temps d’attente avant que les ressources Dynamic Media chargées ne soient publiées sur le serveur de diffusion. Cette valeur est de 2 100 secondes ou 35 minutes, par défaut.

   Dans la plupart des cas d’utilisation, le paramètre de 2 100 est suffisant.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

<!-- NOTE - OBSOLETE that customisations to replication agents to transform content are no longer used; the following content is obsolete now 

### (Optional) Filtering assets for replication {#optional-filtering-assets-for-replication}

In non-Dynamic Media deployments, you replicate *all* assets (both images and video) from your AEM author environment to the AEM publish node. This workflow is necessary because the AEM publish servers also deliver the assets.

However, in Dynamic Media deployments, because assets are delivered by way of the cloud service, there is no need to replicate those same assets to AEM publish nodes. Such a "hybrid publishing" workflow avoids extra storage costs and longer processing times to replicate assets. Other content, such as Site pages, continue to be served from the AEM publish nodes.

The filters provide a way for you to *exclude* assets from being replicated to the AEM publish node.

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

1. In AEM, tap the AEM logo to access the global navigation console and tap the **[!UICONTROL Tools > General > CRXDE Lite]**.
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


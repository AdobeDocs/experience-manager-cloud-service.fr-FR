---
title: Gestion des ressources vidéo
description: Charger, prévisualiser, annoter et publier des ressources vidéo dans [!DNL Adobe Experience Manager].
contentOwner: AG
feature: Asset Management, Publishing, Collaboration, Video
role: User
exl-id: 91edce4a-dfa0-4eca-aba7-d41ac907b81e
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '4983'
ht-degree: 95%

---

# Gestion des ressources vidéo {#manage-video-assets}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-video-assets.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Le format vidéo est un élément essentiel des ressources numériques d’une entreprise. [!DNL Adobe Experience Manager] propose des solutions et des fonctionnalités matures pour gérer l’ensemble du cycle de vie de vos ressources vidéo après leur création.

Découvrez comment gérer et modifier les ressources vidéo dans [!DNL Adobe Experience Manager Assets]. Le codage et le transcodage des vidéos, par exemple le transcodage FFmpeg, sont possibles à l’aide des profils de traitement et de l’intégration [!DNL Dynamic Media]. Sans licence [!DNL Dynamic Media], [!DNL Experience Manager] offre une prise en charge de base pour les vidéos (par exemple, le transcodage FFmpeg, l’extraction de miniatures d’aperçu pour les formats de fichiers pris en charge et l’aperçu dans l’interface utilisateur pour les formats directement pris en charge pour la lecture dans le navigateur).

## Chargement et prévisualisation des ressources vidéo {#upload-and-preview-video-assets}

Vous pouvez charger et prévisualiser des ressources vidéo au format pris en charge dans [!DNL Experience Manager Assets].
<!-- It generates previews for video assets with the extension MP4. -->

### Chargement de ressources vidéo

Pour charger une ressource vidéo, procédez comme suit :

1. Dans le ou les sous-dossiers de ressources numériques, accédez à l’emplacement où vous devez ajouter la ressource.
1. Cliquez sur **[!UICONTROL Créer]** dans la barre d’outils et choisissez **[!UICONTROL Fichiers]**. <br>Vous pouvez également faire glisser un fichier sur l’interface utilisateur.
En savoir plus sur le [chargement de ressources](manage-digital-assets.md#uploading-assets) dans [!DNL Experience Manager Assets].

<!-- 1. To preview a video in the card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. You can pause or play video in the card view only. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.
1. To preview the video in the asset details page, select **[!UICONTROL Edit]** on the card. The video plays in the native video player of the browser. You can play, pause, control the volume, and zoom the video to full screen. -->

### Prévisualisation de ressources vidéo

Vous pouvez prévisualiser les vidéos dans les rendus pris en charge dans l’interface utilisateur d’[!DNL Assets]. Pour prévisualiser une ressource vidéo, procédez comme suit :

1. Chargez une ressource vidéo d’un format pris en charge dans [!DNL Experience Manager Assets]. En savoir plus sur les [&#x200B; formats vidéo pris en charge &#x200B;](file-format-support.md#video-formats). <br>Une fois le chargement effectué, la ressource vidéo est traitée et un rendu d’aperçu est généré.
1. Cliquez sur la ressource, puis sélectionnez ![l’option Détails](assets/do-not-localize/details_icon.svg) **[!UICONTROL Détails]** dans la barre d’outils supérieure. La ressource vidéo s’ouvre dans la visionneuse de vidéos.
1. Cliquez sur l’icône ![option de lecture](assets/do-not-localize/play.png) sur la miniature de la vidéo. <br>Vous pouvez lire, mettre en pause, contrôler le volume et zoomer sur la vidéo en plein écran.

Pour les ressources vidéo existantes dans [!DNL Experience Manager Assets], vous devez **[!UICONTROL Retraiter]** les ressources dans [!DNL Experience Manager] pour activer la fonction d’aperçu vidéo. Découvrez comment [retraiter des ressources numériques](reprocessing.md) dans [!DNL Experience Manager].

### Limites de l’aperçu vidéo

* Les fichiers MXF n’affichent pas les aperçus vidéo, même si le rendu est généré.
* Les fichiers WebM ne génèrent pas de rendus d’aperçu, car ils peuvent être lus en mode natif par les navigateurs web.

## Publication de ressources vidéo {#publish-video-assets}

Après la publication, vous pouvez inclure les ressources vidéo dans une page web sous la forme d’une URL ou les incorporer directement. Pour plus d’informations, voir [Publication de ressources [!DNL Dynamic Media] .](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

## Publication de vidéos sur YouTube {#publishing-videos-to-youtube}

Vous pouvez publier des ressources vidéo gérées dans Experience Manager Assets directement sur une chaîne YouTube que vous avez précédemment créée.

Pour publier des ressources vidéo sur YouTube, vous devez les baliser dans Experience Manager Assets avec des balises. Vous associez ces balises à une chaîne YouTube. Si la balise d’une ressource vidéo correspond à la balise d’une chaîne YouTube, la vidéo est publiée sur YouTube. La publication sur YouTube se produit avec une publication normale de la vidéo à condition qu’une balise associée soit utilisée.

YouTube procède à son propre codage. De ce fait, le fichier vidéo d’origine chargé dans Experience Manager est publié sur YouTube et non pas dans un rendu vidéo créé par le codage Dynamic Media. Même s’il n’est pas nécessaire de traiter les vidéos à l’aide de Dynamic Media, il est supposé qu’elles le sont si un paramètre prédéfini de visionneuse est nécessaire pour la lecture.

Lorsque vous ignorez le profil de traitement vidéo et que vous effectuez directement la publication sur YouTube, votre ressource vidéo ne dispose pas de miniature visible dans Experience Manager Assets. Cela signifie également que les vidéos qui ne sont pas codées ne fonctionneront avec aucun type de ressource Dynamic Media.

Pour garantir une vérification serveur à serveur sécurisée avec YouTube, la publication des vidéos sur les serveurs YouTube implique les tâches suivantes :

1. [Configuration des paramètres de Google Cloud](#configuring-google-cloud-settings)
1. [Création d’une chaîne YouTube](#creating-a-youtube-channel)
1. [Ajout de balises pour la publication](#adding-tags-for-publishing)
1. [Configuration de YouTube dans Experience Manager](#setting-up-youtube-in-aem)
1. [(Facultatif) Automatisation de la définition des propriétés YouTube par défaut pour vos vidéos chargées](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Publication de vidéos sur votre chaîne YouTube](#publishing-videos-to-your-youtube-channel)
1. [(Facultatif) Vérification de la vidéo publiée sur YouTube](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [Liaison d’URL YouTube à votre application web](#linking-youtube-urls-to-your-web-application)

Vous pouvez également [dépublier des vidéos pour les supprimer de YouTube](#unpublishing-videos-to-remove-them-from-youtube).

### Configuration des paramètres de Google Cloud {#configuring-google-cloud-settings}

Pour effectuer une publication sur YouTube, vous avez besoin d’un compte Google. Si vous disposez d’un compte GMAIL, alors vous disposez déjà d’un compte Google ; si vous ne disposez pas d’un compte Google, vous pouvez facilement en créer un. Vous avez besoin du compte car vous avez besoin des informations d’identification pour publier des ressources vidéo dans YouTube. <!-- hidden March 3 2022 If you have an account already created, then skip this task and proceed directly to [Create a YouTube channel](#creating-a-youtube-channel). -->

Il n’est pas nécessaire que le compte utilisé avec Google Cloud et le compte Google utilisé pour YouTube soient les mêmes.

Google modifie régulièrement son interface utilisateur. De ce fait, les étapes de publication des vidéos sur YouTube peuvent varier légèrement des étapes présentées ci-dessous. Cet avertissement s’applique également à YouTube lorsque vous tentez de vérifier si des vidéos y sont téléchargées.

>[!NOTE]
>
>Les étapes suivantes étaient exactes au moment de leur rédaction. Cependant, Google met régulièrement à jour ses pages web cloud sans préavis. Par conséquent, certaines options de configuration peuvent être nommées légèrement différemment dans l’interface utilisateur de Google par rapport au nom utilisé dans les étapes.

**Pour configurer les paramètres de Google Cloud, procédez comme suit :**

1. Créez un compte Google.

   Si vous disposez déjà d’un compte Google, vous pouvez passer à l’étape suivante.

1. Accédez à [https://cloud.google.com/](https://cloud.google.com/).
1. Dans la page **[!UICONTROL Google Cloud]**, près du coin supérieur droit, sélectionnez **[!UICONTROL Console]**.

   Vous devrez peut-être vous **[!UICONTROL connecter]** à l’aide des informations d’identification de votre compte Google pour voir l’option **[!UICONTROL Console]**.

1. Sur la page **[!UICONTROL Tableau de bord]**, à droite de **[!UICONTROL Google Cloud Platform]**, sélectionnez la liste déroulante **[!UICONTROL Projet]** pour ouvrir la boîte de dialogue **[!UICONTROL Sélectionner un projet]**.
1. Dans la boîte de dialogue **[!UICONTROL Sélectionner un projet]**, sélectionnez **[!UICONTROL Nouveau projet]**.
1. Dans la boîte de dialogue **[!UICONTROL Nouveau projet]**, saisissez le nom de votre nouveau projet dans le champ **[!UICONTROL Nom du projet]**.

   Votre ID de projet est basé sur le nom du projet. Par conséquent, choisissez soigneusement le nom du projet ; il ne peut pas être modifié une fois créé. Vous devez également le saisir lors de la configuration ultérieure de YouTube dans Experience Manager. Par conséquent, prenez-le en note.

1. Sélectionnez **[!UICONTROL Créer]**.

1. Effectuez l’une des opérations suivantes :

   * Dans le tableau de bord de votre projet, dans la carte **[!UICONTROL Prise en main]**, sélectionnez **[!UICONTROL Explorer et activer les API]**.
   * Dans le tableau de bord de votre projet, dans la carte **[!UICONTROL API]**, sélectionnez **[!UICONTROL Accéder à l’aperçu des API]**.

1. En haut de la page **[!UICONTROL API &amp; services]**, sélectionnez **[!UICONTROL Activer les API et les services]**.<!-- NEXT STEP BELOW IS STEP 10 -->
1. Sur la page **[!UICONTROL Bibliothèque d’API]**, dans la partie gauche, sous **[!UICONTROL Catégorie]**, sélectionnez **[!UICONTROL YouTube]**. Sur le côté droit de la page, sélectionnez **[!UICONTROL YouTube]**.
1. Sur la page **[!UICONTROL YouTube]**, sélectionnez **[!UICONTROL API de données YouTube v3]**.
1. Sur la page **[!UICONTROL YouTube Data API v3]**, sélectionnez **[!UICONTROL GÉRER]**.

   ![6_5_googleaccount-apis-manage](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-manage.png)

1. Pour utiliser l’API, vous avez besoin d’identifiants. Si nécessaire, sur le côté gauche de la page **[!UICONTROL API et services]**, sélectionnez **[!UICONTROL Informations d’identification]**.
1. Sur la page **[!UICONTROL Informations d’identification]**, en haut, sélectionnez **[!UICONTROL CRÉER DES INFORMATIONS D’IDENTIFICATION]**, puis sélectionnez **[!UICONTROL Identifiant client OAuth]**.
1. Sur la page **[!UICONTROL Créer un identifiant client OAuth]**, dans la liste déroulante **[!UICONTROL Type d’application]**, sélectionnez **[!UICONTROL application web]**.

   ![6_5_googleaccount-apis-applicationtype](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-applicationtype.png)

1. Utilisez l’une des méthodes suivantes :

   * Dans le champ **[!UICONTROL Nom]**, saisissez un nom unique pour votre client OAuth 2.0.
   * Utilisez le nom par défaut que Google a déjà fourni dans le champ **[!UICONTROL Nom]**.

1. Sous l’en-tête **[!UICONTROL Origines JavaScript autorisées]**, sélectionnez **[!UICONTROL AJOUTER UN URI]**.

   ![6_5_googleaccount-apis-name-authorizations](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-nameauthorizations.png)

1. Dans le champ de texte **[!UICONTROL URI]**, saisissez le chemin suivant, en substituant vos propres domaine et numéro de port dans le chemin, puis appuyez sur **[!UICONTROL Entrée]** pour ajouter le chemin à la liste :

   `https://<servername.domain>:<port_number>`

   Par exemple, `https://1a2b3c.mycompany.com:4321`

   >[!NOTE]
   >
   >L’exemple de chemin d’URI ci-dessus est hypothétique et à titre d’explication uniquement.

1. Sous l’en-tête **[!UICONTROL URI de redirection autorisés]**, sélectionnez AJOUTER UN URI.
1. Dans le champ de texte **[!UICONTROL URI]**, saisissez le chemin suivant, en substituant vos propres domaine et numéro de port dans le chemin, puis appuyez sur **[!UICONTROL Entrée]** pour ajouter le chemin à la liste :

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Par exemple, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   >[!NOTE]
   >
   >L’exemple de chemin d’URI ci-dessus est hypothétique et à titre d’explication uniquement.

1. En bas de la page **[!UICONTROL Créer un identifiant client OAuth]**, sélectionnez **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Client OAuth créé]**, procédez comme suit :

   * (Facultatif) Copiez les valeurs dans les champs **[!UICONTROL Votre identifiant client]** et **[!UICONTROL Votre clé secrète client]** et enregistrez.
   * Sélectionnez **[!UICONTROL TÉLÉCHARGER JSON]**, puis enregistrez le fichier JSON.

   Vous en avez besoin lors de la configuration ultérieure de YouTube dans Adobe Experience Manager.

   ![6_5_googleaccount-apis-oauthclientcreated](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-oauthclientcreated.png)

1. Dans la boîte de dialogue **[!UICONTROL Client OAuth créé]**, cliquez sur **[!UICONTROL OK]**.
1. Déconnectez-vous de votre compte Google. Créez maintenant une chaîne YouTube.

### Création d’une chaîne YouTube {#creating-a-youtube-channel}

Pour publier des vidéos sur YouTube, vous devez disposer d’une ou de plusieurs chaînes. Si vous avez déjà créé une chaîne YouTube, vous pouvez ignorer cette étape et passer à la tâche [Ajout de balises pour la publication](/help/assets/dynamic-media/video.md#adding-tags-for-publishing).

>[!CAUTION]
>
>Vous devez avoir configuré une ou plusieurs chaînes dans YouTube *avant* d’ajouter des chaînes sous Paramètres YouTube dans Experience Manager (voir la section [Configuration de YouTube dans Experience Manager](#setting-up-youtube-in-aem) ci-dessous). Si vous ne parvenez pas à configurer le canal, vous n’êtes pas averti qu’aucun canal n’existe. La vérification Google a lieu lorsque vous ajoutez une chaîne mais il n’existe pas d’option permettant de choisir la chaîne vers laquelle la vidéo est envoyée.

**Pour créer une chaîne YouTube :**

1. Accédez à [https://www.youtube.com](https://www.youtube.com/), puis connectez-vous à l’aide des informations d’identification de votre compte Google.
1. Dans l’angle supérieur droit de la page YouTube, sélectionnez l’image de votre profil (peut également s’afficher sous la forme d’une lettre dans un cercle coloré uni), puis sélectionnez **[!UICONTROL Paramètres YouTube]** (icône sous forme d’engrenage rond).
1. Sur la page Présentation, sous l’en-tête Fonctionnalités supplémentaires, sélectionnez **[!UICONTROL Voir toutes mes chaînes ou créer une chaîne]**.
1. Depuis la page Chaînes, sélectionnez **[!UICONTROL Créer une chaîne]**.
1. Sur la page Compte de marque, dans le champ nom du compte de marque, saisissez un nom de société ou tout autre nom de canal de votre choix sous lequel vous souhaitez publier vos ressources vidéo, puis sélectionnez **[!UICONTROL Créer]**.

   Mémorisez le nom que vous entrez ici ; vous devrez le saisir à nouveau lorsque vous devrez configurer YouTube dans Experience Manager.

1. (Facultatif) Si nécessaire, ajoutez d’autres chaînes.

   Vous allez à présent ajouter des balises pour la publication.

### Ajout de balises pour la publication {#adding-tags-for-publishing}

Pour publier vos vidéos sur YouTube, Experience Manager associe des balises à une ou plusieurs chaînes YouTube. Pour ajouter des balises pour publication, voir [Administration des balises](/help/sites-cloud/authoring/sites-console/tags.md).

Ou, si vous prévoyez d’utiliser les balises par défaut dans Experience Manager, vous pouvez ignorer cette tâche et accéder à [Configuration de YouTube dans Experience Manager](#setting-up-youtube-in-aem).

>[!NOTE]
>
>Une fois le Cloud Service configuré, aucune configuration supplémentaire n’est nécessaire pour activer l’agent de réplication de publication YouTube à ce stade. La raison en est qu’elle a été activée lors de l’enregistrement de la configuration du Cloud Service.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, select **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, select the Experience Manager logo, then in the left rail, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, select **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, select **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Select **[!UICONTROL OK]**. -->

### Configuration de YouTube dans Experience Manager {#setting-up-youtube-in-aem}

À partir d’Experience Manager 6.4, une nouvelle méthode d’interface utilisateur tactile a été ajoutée pour configurer la publication YouTube dans Experience Manager. Selon l’instance d’Experience Manager que vous utilisez, effectuez l’une des opérations suivantes :

* Pour configurer YouTube dans une version d’Experience Manager antérieure à la version 6.4, consultez [Configuration de YouTube dans une version d’Experience Manager antérieure à la version 6.4](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before).
* Pour configurer YouTube dans Experience Manager 6.4 ou dans des versions ultérieures, reportez-vous à [Configuration de YouTube dans Experience Manager 6.4 et dans ses versions ultérieures](#setting-up-youtube-in-aem-and-later).

#### Configuration de YouTube dans Experience Manager 6.4 et dans ses versions ultérieures {#setting-up-youtube-in-aem-and-later}

1. Veillez à vous connecter à votre instance Dynamic Media en tant qu’administrateur.
1. Dans le coin supérieur gauche d’Experience Manager, sélectionnez le logo Experience Manager, puis, dans le rail de gauche, accédez à **[!UICONTROL Outils]** (icône Marteau) > **[!UICONTROL Services cloud]** > **[!UICONTROL Configuration de la publication sur YouTube]**.
1. Sélectionnez **[!UICONTROL global]** (sans sélectionner cette option).

1. Dans le coin supérieur droit de la page Global, sélectionnez **[!UICONTROL Créer]**.
1. Sur la page Créer une configuration YouTube, sous Paramètres de plateforme Google Cloud, dans le champ **[!UICONTROL Nom de l’application]**, saisissez l’ID de projet Google.

   Vous avez spécifié l’ID de projet lorsque vous avez précédemment configuré les paramètres de Google Cloud.
Laissez la boîte de dialogue Créer une configuration YouTube ouverte car vous y reviendrez dans quelques instants.

   ![6_5_youtubepublish-createyoutubeconfiguration](/help/assets/dynamic-media/assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. À l’aide d’un éditeur de texte brut, ouvrez le fichier JSON que vous avez téléchargé et enregistré au cours de la tâche [Configuration des paramètres de Google Cloud](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings).
1. Sélectionnez l’intégralité du texte JSON et copiez-le.
1. Revenez à la boîte de dialogue Paramètres du compte YouTube. Dans le champ **[!UICONTROL Configuration JSON]**, collez le texte JSON.
1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer]**.

   Configurez maintenant les canaux YouTube dans Experience Manager.

1. Sélectionnez **[!UICONTROL Ajouter un canal]**.
1. Dans la boîte de dialogue Paramètres de chaîne, saisissez le nom de la chaîne que vous avez créée lors de la tâche **[!UICONTROL Ajout d’une ou plusieurs chaînes YouTube]** précédemment.

   Vous pouvez éventuellement ajouter une description.

1. Sélectionnez **[!UICONTROL Ajouter]**.
1. La vérification YouTube/Google s’affiche. Si vous n’avez pas encore effectué de connexion au compte Google Cloud, ignorez cette étape.

   * Saisissez le nom d’utilisateur et le mot de passe Google associés à l’ID de projet Google et au texte JSON ci-dessus.
   * Selon le nombre de canaux de votre compte, deux éléments ou plus s’affichent. Sélectionnez un canal. Ne sélectionnez pas l’adresse e-mail ; ce n’est pas un canal.
   * Dans la page suivante, sélectionnez **[!UICONTROL Accepter]** pour autoriser l’accès à ce canal.

1. Sélectionnez **[!UICONTROL Autoriser]**.

   Configurez maintenant des balises pour publication.

1. **[!UICONTROL Configuration de balises pour publication]** : sur la page Services cloud > YouTube, sélectionnez l’icône en forme de crayon pour modifier la liste des balises que vous souhaitez utiliser.
1. Pour afficher la liste des balises disponibles dans Experience Manager, sélectionnez l’icône de liste déroulante (flèche pointant vers le bas).
1. Pour les ajouter, sélectionnez une ou plusieurs balises.

   Pour supprimer une balise que vous avez ajoutée, sélectionnez-la puis sélectionnez **[!UICONTROL X]**.

1. Lorsque vous avez terminé d’ajouter les balises souhaitées, sélectionnez **[!UICONTROL Enregistrer]**.

   Vous allez à présent publier des vidéos sur votre chaîne YouTube.

#### Configuration de YouTube dans une version d’Experience Manager antérieure à la version 6.4 {#setting-up-youtube-in-aem-before}

1. Veillez à vous connecter à votre instance Dynamic Media en tant qu’administrateur.

1. Dans le coin supérieur gauche d’Experience Manager, sélectionnez le logo Experience Manager, puis, dans le rail de gauche, accédez à **[!UICONTROL Outils]** (icône Marteau) > **[!UICONTROL Déploiement]** > **[!UICONTROL Cloud Services]**.
1. Sous le titre Services tiers, sélectionnez **[!UICONTROL Configurer maintenant]** sous YouTube.
1. Dans la boîte de dialogue Créer une configuration, saisissez un titre (obligatoire) et un nom (facultatif) dans les champs correspondants.
1. Sélectionnez **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue Paramètres du compte YouTube, dans le champ **[!UICONTROL Nom de l’application]**, saisissez l’ID de projet Google.

   Vous avez spécifié l’ID de projet lorsque vous avez précédemment [configuré les paramètres de Google Cloud](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings).
Laissez cette boîte de dialogue ouverte. Vous y retournerez dans quelques instants.

1. À l’aide d’un éditeur de texte brut, ouvrez le fichier JSON que vous avez téléchargé et enregistré au cours de la tâche Configuration des paramètres de Google Cloud.
1. Sélectionnez l’intégralité du texte JSON et copiez-le.
1. Revenez à la boîte de dialogue Paramètres du compte YouTube. Dans le champ **[!UICONTROL Configuration JSON]**, collez le texte JSON.
1. **[!UICONTROL Cliquez sur OK]**.

   Configurez maintenant les canaux YouTube dans Experience Manager.

1. À droite des **[!UICONTROL Chaînes disponibles]**, sélectionnez **+** (icône représentant un signe plus).
1. Dans la boîte de dialogue Paramètres de chaîne YouTube, dans le champ Titre, saisissez le nom de la chaîne que vous avez créée lors de la tâche **[!UICONTROL Ajout d’une ou plusieurs chaînes YouTube]** précédemment.

   Vous pouvez éventuellement ajouter une description.

1. **[!UICONTROL Cliquez sur OK]**.
1. La vérification YouTube/Google s’affiche. Si vous n’avez pas encore effectué de connexion au compte Google Cloud, ignorez cette étape.

   * Saisissez le nom d’utilisateur et le mot de passe Google associés à l’ID de projet Google et au texte JSON ci-dessus.
   * Selon le nombre de canaux de votre compte, deux éléments ou plus s’affichent. Sélectionnez un canal. Ne sélectionnez pas l’adresse e-mail ; ce n’est pas un canal.
   * Dans la page suivante, sélectionnez **[!UICONTROL Accepter]** pour autoriser l’accès à ce canal.

1. Sélectionnez **[!UICONTROL Autoriser]**.

   Configurez maintenant des balises pour publication.

1. **[!UICONTROL Configuration de balises pour publication]** : sur la page Services cloud > YouTube, sélectionnez l’icône en forme de crayon pour modifier la liste des balises que vous souhaitez utiliser.
1. Pour afficher la liste des balises disponibles dans Experience Manager, sélectionnez l’icône de liste déroulante (flèche pointant vers le bas).
1. Pour les ajouter, sélectionnez une ou plusieurs balises.

   Pour supprimer une balise que vous avez ajoutée, sélectionnez-la puis sélectionnez **X**.

1. Lorsque vous avez terminé d’ajouter les balises souhaitées, sélectionnez **[!UICONTROL OK]**.

   Vous allez à présent publier des vidéos sur votre chaîne YouTube.

### (Facultatif) Automatisation de la définition des propriétés YouTube par défaut pour vos vidéos chargées {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

Vous pouvez si vous le souhaitez automatiser la définition des propriétés YouTube lors du chargement de vos vidéos. Créez un profil de traitement des métadonnées dans Experience Manager.

Pour créer le profil de traitement des métadonnées, vous allez d’abord copier les valeurs des champs **[!UICONTROL Étiquette de champ]**, **[!UICONTROL Associer à la propriété]** et **[!UICONTROL Choix]**, tous situés dans les schémas de métadonnées pour la vidéo. Ensuite, vous allez créer votre propre profil de traitement des métadonnées vidéo YouTube en y ajoutant ces valeurs.

**Pour automatiser la définition des propriétés YouTube par défaut pour vos vidéos chargées :**

1. Dans le coin supérieur gauche d’Experience Manager, sélectionnez le logo Experience Manager, puis, dans le rail de gauche, accédez à **[!UICONTROL Outils]** (icône Marteau) > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Sélectionnez **[!UICONTROL default]**. (Ne cochez pas la case de sélection à gauche de l’option « Par défaut ».)
1. Sur la page **[!UICONTROL par défaut]**, cochez la case à gauche de **[!UICONTROL vidéo]**, puis sélectionnez **[!UICONTROL Modifier]**.
1. Sur la page Éditeur de schéma de métadonnées, sélectionnez l’onglet **[!UICONTROL Avancé]**.
1. Sous l’en-tête Publication YouTube, sélectionnez **[!UICONTROL Catégorie YouTube]**.
1. Dans la partie droite de la page, sous l’onglet **[!UICONTROL Paramètres]**, procédez comme suit :

   * Dans le champ de texte **[!UICONTROL Associer à la propriété]**, sélectionnez la valeur et copiez-la.
Collez la valeur copiée dans l’éditeur de texte ouvert. Vous allez avoir besoin de cette valeur plus tard, lorsque vous allez créer votre profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Sous **[!UICONTROL Choix]**, sélectionnez la valeur par défaut à utiliser (comme « Personnes et blogs » ou « Science et technologie ») et copiez-la.
Collez la valeur copiée dans l’éditeur de texte ouvert. Vous allez avoir besoin de cette valeur plus tard, lorsque vous allez créer votre profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

1. Sous l’en-tête Publication YouTube, sélectionnez **[!UICONTROL Confidentialité YouTube]**.
1. Dans la partie droite de la page, sous l’onglet **[!UICONTROL Paramètres]**, procédez comme suit :

   * Dans le champ de texte **[!UICONTROL Associer à la propriété]**, sélectionnez la valeur et copiez-la.
Collez la valeur copiée dans l’éditeur de texte ouvert. Vous allez avoir besoin de cette valeur plus tard, lorsque vous allez créer votre profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Sous **[!UICONTROL Choix]**, sélectionnez et copiez la valeur par défaut à utiliser. Notez que les choix sont groupés par paires. Le champ inférieur de la paire correspond à la valeur par défaut que vous souhaitez copier, comme valeur publique, non répertoriée ou privée.
Collez la valeur copiée dans l’éditeur de texte ouvert. Vous allez avoir besoin de cette valeur plus tard, lorsque vous allez créer votre profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

1. Près du coin supérieur droit de la page Éditeur de schéma de métadonnées, sélectionnez **[!UICONTROL Annuler]**.
1. Dans le coin supérieur gauche d’Experience Manager, sélectionnez le logo Experience Manager, puis, dans le rail de gauche, sélectionnez **[!UICONTROL Outils]** (icône Marteau) > **[!UICONTROL Ressources]** > **[!UICONTROL Profils de métadonnées]**.

1. Sur la page Profils de métadonnées, près du coin supérieur droit de la page, sélectionnez **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue Ajouter un profil de métadonnées, dans le champ de texte **[!UICONTROL Titre du profil]**, saisissez le nom `YouTube Video`, puis sélectionnez **[!UICONTROL Créer]**.
1. Sur la page Éditeur de profil de métadonnées, sélectionnez l’onglet **[!UICONTROL Avancé]**.
1. Ajoutez les valeurs de publication YouTube copiées au profil en procédant comme suit :

   * Dans la partie droite de la page, sélectionnez l’onglet **[!UICONTROL Créer le formulaire]**.
   * (Facultatif) Faites glisser le composant appelé **[!UICONTROL En-tête de section]** vers la gauche et déposez-le dans la zone de formulaire.
   * (Facultatif) Sélectionnez **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * (Facultatif) Dans la partie droite de la page, sous l’onglet Paramètres, dans le champ de texte Libellé du champ, saisissez `YouTube Publishing`.
   * Sélectionnez l’onglet **[!UICONTROL Créer le formulaire]**, puis faites glisser le composant appelé **[!UICONTROL Texte à plusieurs valeurs]** et déposez-le sous l’en-tête **[!UICONTROL Publication YouTube]** que vous avez créé.

   * Pour sélectionner le composant, sélectionnez **[!UICONTROL Libellé du champ]**.
   * Dans la partie droite de la page, sous l’onglet Paramètres, collez les valeurs de publication YouTube (valeur Libellé du champ et Associer à la propriété) copiées précédemment, dans les champs respectifs du formulaire. Collez la valeur Choix dans le champ Valeur par défaut.

1. Ajoutez les valeurs de confidentialité Youtube copiées dans le profil en procédant comme suit :

   * Dans la partie droite de la page, sélectionnez l’onglet **[!UICONTROL Créer le formulaire]**.
   * (Facultatif) Faites glisser le composant appelé **[!UICONTROL En-tête de section]** vers la gauche et déposez-le dans la zone de formulaire.
   * (Facultatif) Sélectionnez **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * (Facultatif) Dans la partie droite de la page, sous l’onglet Paramètres, dans le champ de texte Libellé du champ, saisissez `YouTube Privacy`.
   * Sélectionnez l’onglet **[!UICONTROL Créer le formulaire]**, puis faites glisser le composant appelé **[!UICONTROL Texte à plusieurs valeurs]** et déposez-le sous l’en-tête **[!UICONTROL Confidentialité YouTube]** que vous avez créé.

   * Pour sélectionner le composant, sélectionnez **[!UICONTROL Libellé du champ]**.
   * Dans la partie droite de la page, sous l’onglet Paramètres, collez les valeurs de publication YouTube (valeur Libellé du champ et Associer à la propriété) copiées précédemment, dans les champs respectifs du formulaire. Collez la valeur Choix dans le champ Valeur par défaut.

1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer]**.
1. Appliquez le profil des métadonnées de publication YouTube aux dossiers dans lesquels vous allez charger des vidéos. Vous devez avoir configuré le profil des métadonnées et le profil vidéo.

   Voir [Profils de métadonnées](/help/assets/metadata-profiles.md) et [Profils vidéo](/help/assets/dynamic-media/video-profiles.md).

### Publication de vidéos sur votre chaîne YouTube {#publishing-videos-to-your-youtube-channel}

Vous devez maintenant associer les balises que vous avez précédemment ajoutées aux ressources vidéo. Ce processus permet à Experience Manager de déterminer les ressources à publier sur votre chaîne YouTube.

>[!NOTE]
>
>Publier « Immédiatement » ne publie pas automatiquement les ressources sur YouTube. Lorsque Dynamic Media est configuré, il existe deux options de publication parmi lesquelles choisir : **[!UICONTROL Immédiatement]** ou **[!UICONTROL Lors de l’activation]**.
>
>Dans le mode de publication **[!UICONTROL Immédiatement]**, la ressource chargée (une fois synchronisée avec IPS) est automatiquement publiée sur le système de diffusion. Cela vaut pour Dynamic Media, mais pas pour YouTube. Pour publier sur YouTube, vous devez publier par le biais d’Experience Manager Author.

>[!NOTE]
>
>Pour publier du contenu depuis YouTube, Experience Manager utilise le workflow **[!UICONTROL Publier sur YouTube]**, qui vous permet de surveiller la progression et de consulter toutes les informations d’échec.
>
>Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).
>
>Pour obtenir des informations de progression plus détaillées, vous pouvez surveiller le journal YouTube sous la réplication. Sachez toutefois que ce type de surveillance nécessite un accès administrateur.

**Pour publier des vidéos sur votre chaîne YouTube, procédez comme suit :**

1. Dans Experience Manager, accédez à la ressource vidéo que vous souhaitez publier sur votre chaîne YouTube.
1. Sélectionnez la ressource vidéo (visionneuse de vidéos adaptative).
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Propriétés]**.
1. Dans l’onglet De base, sous l’en-tête Métadonnées, sélectionnez **[!UICONTROL Boîte de dialogue Ouvrir la sélection]** à droite du champ Balises.
1. Accédez aux balises à utiliser sur la page Sélectionner des balises, puis sélectionnez une ou plusieurs balises.

   N’oubliez pas que les balises doivent être associées à la chaîne YouTube.

1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Sélectionner]**.
1. Dans le coin supérieur droit de la page des propriétés de la vidéo, sélectionnez **[!UICONTROL Enregistrer et fermer]**.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**.

   Consultez également [Utilisation de la gestion de la publication avec Experience Manager Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html?lang=fr#page-authoring).

   Vous avez la possibilité de vérifier la vidéo publiée sur votre chaîne YouTube.

### (Facultatif) Vérification de la vidéo publiée sur YouTube {#optional-verifying-the-published-video-on-youtube}

Vous pouvez si vous le souhaitez surveiller la progression de votre publication YouTube (ou sa dépublication).

Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

Le délai de publication peut varier considérablement en fonction de nombreux facteurs, comme le format de la vidéo source originale, la taille du fichier et le trafic de chargement. La publication peut prendre de quelques minutes à plusieurs heures. En outre, les formats de haute résolution sont rendus beaucoup plus lentement. Par exemple, les vidéos en 720p et en 1 080p prennent plus de temps à s’afficher que les vidéos en 480p.

Au bout de huit heures, si un message de statut indiquant **[!UICONTROL Téléchargé (en cours de traitement, veuillez patienter)]** s’affiche toujours, essayez de supprimer la vidéo de votre site et chargez-la à nouveau.

### Liaison d’URL YouTube à votre application web {#linking-youtube-urls-to-your-web-application}

Une fois que vous avez publié la vidéo, une chaîne URL YouTube est générée par Dynamic Media. Lorsque vous copiez l’URL Youtube, cette dernière est conservée dans le presse-papiers, ce qui vous permet de la coller dans les pages de votre site web ou de votre application.

>[!NOTE]
>
>L’URL YouTube ne peut pas être copiée tant que vous n’avez pas publié la ressource vidéo sur YouTube.

Pour lier des URL YouTube à votre application web, procédez comme suit :

1. Accédez à la ressource vidéo *publiée sur YouTube* dont vous souhaitez copier l’URL, puis sélectionnez-la.

   N’oubliez pas que les URL YouTube peuvent être copiées uniquement *après* la *publication* des ressources vidéo sur YouTube.

1. Dans la barre d’outils, sélectionnez **[!UICONTROL Propriétés]**.
1. Sélectionnez l’onglet **[!UICONTROL Avancé]**.
1. Sous l’en-tête Publication YouTube, dans la liste des URL YouTube, sélectionnez le texte de l’URL et copiez-le dans votre navigateur web pour prévisualiser la ressource ou l’ajouter à votre page de contenu web.

### Dépublication de vidéos afin de les supprimer de YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Lorsque vous dépubliez une ressource vidéo dans Experience Manager, la vidéo est supprimée de YouTube.

>[!CAUTION]
>
>Si vous supprimez une vidéo directement sur YouTube, Experience Manager l’ignore et continue de se comporter comme si la vidéo était toujours publiée sur YouTube. Veillez toujours à dépublier une ressource vidéo sur YouTube via Experience Manager.

>[!NOTE]
>
>Pour supprimer du contenu depuis YouTube, Experience Manager utilise le processus **[!UICONTROL Dépublier sur YouTube]**, qui vous permet de surveiller la progression et de consulter toutes les informations d’échec.
>
>Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

**Pour dépublier des vidéos afin de les supprimer de YouTube, procédez comme suit :**

1. Accédez aux ressources vidéo que vous souhaitez dépublier de votre chaîne YouTube.
1. Dans un mode de sélection de ressources, sélectionnez une ou plusieurs ressources vidéo publiées.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**. Si nécessaire, sélectionnez l’icône des trois petits points (`. . .`) dans la barre d’outils pour afficher **[!UICONTROL Gérer la publication]**.
1. Sur la page Gérer la publication, sélectionnez **[!UICONTROL Dépublier]**.
1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Suivant]**.
1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Dépublier]**.

## Surveillance du codage vidéo et de la progression de la publication sur YouTube {#monitoring-video-encoding-and-youtube-publishing-progress}

Lorsque vous téléchargez une nouvelle vidéo vers un dossier auquel un codage vidéo a été appliqué ou que vous publiez votre vidéo sur YouTube, contrôlez la manière dont votre codage vidéo/publication YouTube progresse (ou échoue). La progression réelle de la publication YouTube n’est disponible que dans les journaux. Cependant, qu’elle échoue ou qu’elle réussisse, elle est répertoriée d’autres manières décrites dans la procédure suivante. En outre, vous recevez des notifications par e-mail lorsqu’un workflow de publication YouTube ou un codage vidéo est terminé ou interrompu.

### Surveillance de la progression {#monitoring-progress}

Il est possible de surveiller la progression, notamment l’échec du codage ou de la publication YouTube.

1. Consultez la progression du codage vidéo dans votre dossier de ressources :

   * En mode Carte, la progression du codage vidéo s’affiche sur la ressource en pourcentage. En cas d’erreur, ces informations s’affichent également sur la ressource.

   ![chlimage_1-429](/help/assets/dynamic-media/assets/chlimage_1-429.png)

   * Dans la vue Liste, la progression du codage vidéo s’affiche dans la colonne **[!UICONTROL État du traitement]**. Si une erreur se produit, le message suivant s’affiche dans la même colonne.

   ![chlimage_1-430](/help/assets/dynamic-media/assets/chlimage_1-430.png)

   Cette colonne ne s’affiche pas par défaut. Pour activer la colonne, sélectionnez l’option **[!UICONTROL Paramètres d’affichage]** dans le menu contextuel des affichages et ajoutez la colonne **[!UICONTROL État du traitement]** et sélectionnez **[!UICONTROL Mettre à jour]**.

   ![chlimage_1-431](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. Consultez la progression dans les détails de la ressource. Lorsque vous sélectionnez une ressource, ouvrez le menu contextuel et sélectionnez **[!UICONTROL Chronologie]**. Pour le réduire à des activités de processus comme le codage ou la publication YouTube, sélectionnez **[!UICONTROL Processus]**.

   ![chlimage_1-432](/help/assets/dynamic-media/assets/chlimage_1-432.png)

   Toutes les informations de workflow, telles que le codage, s’affichent dans la chronologie. Pour la publication YouTube, la chronologie du workflow comprend également le nom de la chaîne YouTube et l’URL de la vidéo YouTube. En outre, vous pouvez consulter toutes les notifications d’échec dans le journal du workflow une fois la publication terminée.

   >[!NOTE]
   >
   >L’enregistrement des messages d’erreur ou d’échec peut prendre un certain temps en raison des différentes configurations de workflows pour les **[!UICONTROL nouvelles tentatives]**, l’**[!UICONTROL intervalle entre deux tentatives]** et le **[!UICONTROL délai d’attente]** de [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), par exemple :
   >
   >* Configuration de la file d’attente des tâches Apache Sling
   >* Gestionnaire de tâches de processus externe du workflow Adobe Granite
   >* File d’attente d’expiration du workflow Granite
   >
   >Vous pouvez ajuster les propriétés **[!UICONTROL reprises]**, **[!UICONTROL délai de reprise]** et **[!UICONTROL délai d’expiration]** dans ces configurations.

1. Pour les workflows en cours, consultez les instances de workflow disponibles sous **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Instances]**.

   >[!NOTE]
   >
   >Vous aurez peut-être besoin de droits administratifs pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-433](/help/assets/dynamic-media/assets/chlimage_1-433.png)

   Sélectionnez l’instance et sélectionnez **[!UICONTROL Ouvrir l’historique]**.

   ![chlimage_1-434](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   Depuis la section instances de workflow, vous pouvez également suspendre, arrêter ou renommer les workflows. Voir [Administration des workflows](/help/sites-cloud/authoring/workflows/overview.md) pour plus d’informations.

1. Pour les tâches qui ont échoué, consultez la section Échecs des processus disponible sous **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Échecs]**. L’**[!UICONTROL échec du processus]** répertorie toutes les activités du processus ayant échoué.

   >[!NOTE]
   >
   >Vous aurez peut-être besoin de droits administratifs pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-435](/help/assets/dynamic-media/assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >L’enregistrement du message d’erreur peut prendre un certain temps en raison des différentes configurations de workflows pour les **[!UICONTROL nouvelles tentatives]**, l’**[!UICONTROL intervalle entre deux tentatives]** et le **[!UICONTROL délai d’attente]** de [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), par exemple :
   >
   >* Configuration de la file d’attente des tâches Apache Sling
   >* Gestionnaire de tâches de processus externe du workflow Adobe Granite
   >* File d’attente d’expiration du workflow Granite
   >
   >Vous pouvez ajuster les propriétés **[!UICONTROL reprises]**, **[!UICONTROL délai de reprise]** et **[!UICONTROL délai d’expiration]** dans ces configurations.

1. Pour les workflows terminés, consultez l’archive de workflow sous **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Archive]**. La liste **[!UICONTROL Archive de workflow]** répertorie toutes les activités de workflow qui ont réussi.

   >[!NOTE]
   >
   >Vous aurez peut-être besoin de droits administratifs pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-436](/help/assets/dynamic-media/assets/chlimage_1-436.png)

1. Vous recevez des notifications par courrier électronique sur les tâches de processus annulées ou qui ont échoué. Ces notifications peuvent être configurées par un administrateur. Voir [Configuration des notifications par e-mail](#configuring-e-mail-notifications).

<!-- EMAIL NOT AVAILABLE IN SKYLINE

#### Configuring e-mail notifications {#configuring-e-mail-notifications}

>[!NOTE]
>
>You may need administrative rights to access the **[!UICONTROL Tools]** menu.

How you configure notification depends on whether you want notifications for YouTube publishing jobs.

* For encoding jobs, you can access the configuration page for all Experience Manager workflow email notifications at **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and by searching for **[!UICONTROL Day CQ Workflow Email Notification Service]**. You can select or clear the check boxes for **[!UICONTROL Notify on Abort]** or **[!UICONTROL Notify on Complete]** accordingly.

For YouTube publishing jobs, do the following:

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. On the Workflow Models page, select **[!UICONTROL Publish to YouTube]**, then select **[!UICONTROL Edit]** on the toolbar.
1. Near the upper-right corner of the Publish to YouTube workflow page, select **[!UICONTROL Edit]**.
1. Hover the mouse pointer on the YouTube Upload component, then select once to display the inline toolbar.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. On the inline toolbar, select the Configuration icon (wrench). Select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. In the YouTube Upload Process - Step Properties dialog box, select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. You can select or clear the following check boxes:

    * Publish Start
    * Publish Failure
    * Publish Completion - includes information on channels and URLs

   Clearing a check box means that you will not receive the specified email notification from the YouTube Publish workflow.

   >[!NOTE]
   >
   >These emails are specific to YouTube and are in addition to the generic workflow email notifications. As a result, you may receive two sets of email notification - the generic notification available in the **[!UICONTROL Day CQ Workflow Email Notification Service]** and one specific to YouTube depending on your configuration settings.

1. When you are finished, near the upper-right corner of the dialog box, select the **[!UICONTROL Done]** icon (check mark).
1. On the Publish to YouTube workflow page, near the upper-right corner, select **[!UICONTROL Sync]**.

-->

## Transcodage à l’aide du profil de traitement {#transcode-video}

[!DNL Experience Manager] as a [!DNL Cloud Service] permet de réaliser un transcodage de base des fichiers vidéo MP4 à l’aide de profils de traitement. Cette fonctionnalité vous permet non seulement de télécharger, mais également de prévisualiser et de mettre à l’échelle un fichier vidéo MP4.

![Création d’un profil de traitement pour le transcodage vidéo dans [!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)

*Figure : Profil de traitement pour le transcodage vidéo dans [!DNL Experience Manager].*

Si vous indiquez uniquement la largeur ou uniquement la hauteur et laissez l’autre champ vide, les rendus conservent les proportions. Le codec vidéo H.264 est disponible pour le transcodage.

Pour traiter des ressources à l’aide d’un profil de traitement, ajoutez un profil à un dossier. Voir [Utilisation de profils de traitement pour traiter des ressources](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## Annotation de ressources vidéo {#annotate-video-assets}

Vous pouvez ajouter des annotations aux ressources vidéo. Lorsque vous annotez des vidéos, le lecteur se met en pause pour vous permettre d’ajouter une annotation sur une image. Pour plus d’informations, voir [Gestion de ressources vidéo](manage-video-assets.md).

>[!NOTE]
>
>Le format vidéo MXF n’est pas encore pris en charge avec les annotations de ressources vidéo.

1. Dans la console [!DNL Assets], sélectionnez **[!UICONTROL Modifier]** sur la carte de ressources pour afficher la page de détails de la ressource.
1. Pour lire la vidéo, cliquez sur **[!UICONTROL Aperçu]**.
1. Pour annoter la vidéo, cliquez sur **[!UICONTROL Annoter]**. Une annotation est ajoutée à ce moment de la vidéo. Lorsque vous annotez, vous pouvez dessiner sur le canevas et inclure un commentaire avec le dessin. Les commentaires sont automatiquement enregistrés. Pour quitter l’assistant d’annotation, cliquez sur **[!UICONTROL Fermer]**.
1. Pour passer à un point spécifique de la vidéo, indiquez le moment en secondes dans le champ **texte** et cliquez sur **Aller**. Par exemple, pour sauter les 20 premières secondes de la vidéo, saisissez 20 dans le champ texte.
1. Pour l’afficher dans le journal, cliquez sur une annotation. Pour supprimer l’annotation du journal, cliquez sur **[!UICONTROL Supprimer]**.

## Bonnes pratiques et restrictions {#tips-limitations}

* En l’absence de licence [!DNL Dynamic Media], vous pouvez seulement traiter les fichiers MP4 à l’aide de profils de traitement.
* Lors du transcodage de fichiers MP4 à l’aide de profils de traitement, les instructions et restrictions suivantes s’appliquent :

   * Les fichiers Apple ProRes ne peuvent transcoder qu’avec une résolution maximale de 1080p.
   * Si le fichier source a un débit > 200 Mbit/s, vous ne pouvez transcoder que jusqu’à une résolution maximale de 1080p.
   * Si la cadence source est supérieure ou égale à 60 ips, alors la taille maximale du fichier source que vous pouvez utiliser est

      * 400 Mo pour le transcodage 4k.
      * 800 Mo pour le transcodage 1080p.
      * 8 Go pour le transcodage 720p.

   * La taille de fichier maximale que vous pouvez transcoder en résolution 4k est un fichier MP4 de 2,55 Go de résolution 4k, un débit de 12 Mbit/s et de 23 i/s.

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

>[!MORELIKETHIS]
>
>* [Documentation vidéo de Dynamic Media](/help/assets/dynamic-media/video.md).
>* [En savoir plus sur l’utilisation, les types et la configuration des profils de traitement](/help/assets/asset-microservices-configure-and-use.md).

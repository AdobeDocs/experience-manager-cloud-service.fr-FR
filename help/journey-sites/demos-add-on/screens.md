---
title: Activation d’AEM Screens pour votre site de démonstration
description: Découvrez les étapes pour activer l’expérience as a Cloud Service AEM Screens complète sur votre site de démonstration.
exl-id: 369eea9f-2e81-4b87-841c-188b67657bab
source-git-commit: cdc60627bac17166c12ebdb77e7cf5b0ed92dc80
workflow-type: tm+mt
source-wordcount: '2671'
ht-degree: 4%

---

# Activation d’AEM Screens pour votre site de démonstration {#enable-screens}

Découvrez les étapes pour activer l’expérience as a Cloud Service AEM Screens complète sur votre site de démonstration.

## Un peu d’histoire… {#story-so-far}

Dans le document précédent du parcours de module complémentaire de démonstration de référence d’AEM, [Créer un site de démonstration,](create-site.md) vous avez créé un nouveau site de démonstration basé sur les modèles du module complémentaire de démonstration de référence. Vous devez maintenant :

* Découvrir comment accéder à l’environnement de création AEM.
* Savoir comment créer un site à partir d’un modèle.
* Découvrir les principes de base de la navigation dans la structure du site et de la modification d’une page.

Maintenant que vous disposez de votre propre site de démonstration pour explorer et comprendre les outils disponibles pour vous aider à gérer vos sites de démonstration, vous pouvez activer l’expérience as a Cloud Service AEM Screens complète pour vos sites de démonstration.

## Objectif {#objective}

Le module complémentaire de démonstration de référence d’AEM contient du contenu AEM Screens pour We.Cafe, un business vertical du café. Ce document vous aide à comprendre comment exécuter la configuration de démonstration We.Cafe dans le contexte d’AEM Screens. Après avoir lu ce document, vous devriez :

* Connaître les principes de base d’AEM Screens.
* Découvrez le contenu de démonstration de We.Cafe.
* Découvrez comment configurer AEM Screens pour We.Cafe.
   * Découvrez comment créer un projet Screens pour We.Cafe.
   * Vous pouvez configurer un service météorologique simulé à l’aide des feuilles de calcul Google Sheets et des API.
   * Simulez le contenu Screens qui change dynamiquement en fonction de votre &quot;service météo&quot;.
   * Installez et utilisez le lecteur Screens.

## Présentation de Screens {#understand-screens}

AEM Screens as a Cloud Service est une solution de signalétique numérique qui permet aux marketeurs de créer et de gérer des expériences numériques dynamiques à grande échelle. Avec AEM Screens as a Cloud Service, vous pouvez créer des expériences de signalétique numérique attrayantes et dynamiques destinées à être utilisées dans les espaces publics.

>[!TIP]
>
>Pour plus d’informations sur AEM Screens as a Cloud Service, reportez-vous à la section [Ressources supplémentaires](#additional-resources) à la fin de ce document.

En installant le module complémentaire de démonstration de référence d’AEM, vous disposez automatiquement du contenu We.Cafe pour AEM Screens dans votre environnement de création de démonstration. Les étapes décrites dans la section [Déploiement d’un projet Demo Screens](#deploy-project) vous permettent d’activer l’expérience AEM Screens complète en publiant ce contenu et en le déployant sur les lecteurs multimédia, etc.

## Présentation du contenu de démonstration {#demo-content}

Le café We.Cafe se compose de trois boutiques situées à trois endroits des États-Unis. Les trois magasins ont trois expériences similaires :

* Une carte au-dessus du compteur avec deux ou trois panneaux verticaux
* Un affichage d’entrée faisant face à la rue avec un panneau horizontal ou vertical invitant les clients à entrer dans la boutique
* Boutique de kiosque à commande automatique rapide pour contourner la file d’attente avec une tablette verticale

>[!NOTE]
>
>Seul l’affichage de l’entrée peut être testé dans la version actuelle de la démonstration. D’autres affichages suivront dans une version ultérieure.
>
>Le kiosque n’est pas inclus dans la version actuelle de la démonstration. Il sera inclus dans une version ultérieure.

L’emplacement de New York est supposé se trouver dans un magasin plus petit qui n’a pas beaucoup d’espace, et donc :

* La carte ne comporte que deux panneaux verticaux au lieu de trois pour San Francisco et San Jose.
* L’affichage de l’entrée est positionné verticalement au lieu de horizontalement.

>[!NOTE]
>
>Si vous décidez de vous connecter au Cloud Service Screens dans le [Connexion à Screens as a Cloud Service](#connect-screens) , créez les emplacements sous forme de dossiers sous les affichages. Voir [Ressources supplémentaires](#additional-resources) à la fin de ce document pour plus d’informations sur les affichages.

### Cafe Layers {#care-layouts}

Les emplacements We.Cafe présentent les dispositions suivantes.

![Dispositions We.Cafe](assets/cafe-layouts.png)

>[!NOTE]
>
>Les mesures pour les écrans sont en pouces.

### Entrée {#entrance}

L’affichage de l’entrée est divisé par le jour et change simplement la première image du matin à l’après-midi. À chaque passage de la séquence, il fait également la publicité d’une préparation spéciale de café différente, en utilisant une séquence incorporée limitée pour lire un article différent à chaque fois.

La dernière image des canaux d’entrée est également ciblée (c’est-à-dire modifiée dynamiquement) en fonction de la température extérieure, qui peut être simulée comme décrit dans la section [Création d’une source de données simulée](#data-source) .

## Déploiement d’un projet Demo Screens {#deploy-project}

Pour utiliser le contenu de démonstration dans l’environnement de test que vous avez créé dans la variable [Créer un programme](create-program.md) , un site doit être créé à partir d’un modèle.

Si vous n’avez pas encore créé de site de démonstration We.Cafe, procédez simplement comme indiqué dans la section [Créer un site de démonstration](create-site.md) . Lors de la sélection du modèle, il vous suffit de choisir la variable **Modèle de site Web We.Cafe**.

![Modèle We.Cafe](assets/wecafe-template.png)

Une fois l’assistant terminé, vous trouverez le contenu déployé sous Sites et vous pouvez parcourir et explorer comme vous le feriez pour tout autre contenu.

![Contenu We.Cafe](assets/wecafe-content.png)

Maintenant que vous disposez du contenu de démonstration We.Cafe, vous avez le choix de la manière dont vous souhaitez tester AEM Screens :

* Si vous souhaitez uniquement explorer le contenu dans la console AEM Sites, commencez simplement à explorer et à en découvrir plus dans la [Ressources supplémentaires](#additional-resources) section . aucune autre action n’est requise.
* Si vous souhaitez découvrir toutes les fonctionnalités dynamiques d’AEM Screens, passez à la section suivante, [Modifiez dynamiquement Le Contenu Screens.](#dynamically-change)

## Modification dynamique du contenu Screens {#dynamically-change}

Tout comme AEM Sites, AEM Screens peut modifier le contenu de manière dynamique en fonction du contexte. La démonstration We.Cafe comporte des canaux configurés pour afficher un contenu différent en fonction de la température actuelle. Pour simuler cela, nous devrons créer notre propre service météorologique simple.

### Création d’une source de données simulée {#data-source}

Comme il est très difficile de modifier le temps pendant une démonstration ou pendant les tests, les changements de température doivent être simulés. Nous simulerons un service météorologique en stockant une valeur de température dans une feuille de calcul Google, que AEM ContextHub appellera pour récupérer la température.

#### Création d’une clé API Google {#create-api-key}

Tout d’abord, nous devrons créer une clé d’API Google pour faciliter l’échange de données.

1. Connectez-vous à un compte Google.
1. Ouvrez la console Cloud à l’aide de ce lien. `https://console.cloud.google.com`.
1. Créez un projet en cliquant sur le nom actuel du projet dans le coin supérieur gauche de la barre d’outils, après l’événement **Google Cloud Platform** libellé.

   ![Console Google Cloud](assets/google-cloud-console.png)

1. Dans la boîte de dialogue du sélecteur de projet, cliquez sur **NOUVEAU PROJET**.

   ![Nouveau projet](assets/new-project.png)

1. Attribuez un nom au projet et cliquez sur **CREATE**.

   ![Créer un projet](assets/create-project.png)

1. Assurez-vous que votre nouveau projet est sélectionné, puis, à l’aide du menu hamburger du tableau de bord de la console cloud, sélectionnez **API et services**.

   ![API et services](assets/apis-services.png)

1. Dans le panneau de gauche de la fenêtre APIs &amp; Services , cliquez sur **Informations d’identification** dans la partie supérieure de la fenêtre, puis cliquez sur **CRÉATION D’INFORMATIONS D’IDENTIFICATION** et **Clé API**.

   ![Informations d’identification](assets/credentials.png)

1. Dans la boîte de dialogue, copiez votre nouvelle clé API et enregistrez-la pour une utilisation ultérieure. Cliquez sur **CLOSE** pour fermer la boîte de dialogue.

#### Activation de l’API Google Sheets {#enable-sheets}

Pour permettre l’échange de données de feuilles de calcul Google à l’aide de votre clé d’API, vous devez activer l’API de feuilles de calcul Google.

1. Revenez à la console cloud Google à l’adresse `https://console.cloud.google.com` pour votre projet, puis utilisez le menu hamburger pour sélectionner **API et services -> Bibliothèque**.

   ![Bibliothèque d’API](assets/api-library.png)

1. Dans l’écran Bibliothèque d’API, faites défiler l’écran pour rechercher **API Google Sheets**. Cliquez dessus.

   ![Recherche de bibliothèque d’API](assets/api-library-search.png)

1. Dans le **API Google Sheets** clic sur la fenêtre **ACTIVER**.

   ![API de feuilles de calcul Google](assets/sheets-api.png)

#### Création d’une feuille de calcul Google Sheets {#create-spreadsheet}

Vous pouvez maintenant créer une feuille de calcul Google Sheets pour stocker vos données météorologiques.

1. Accédez à `https://docs.google.com` et créez une feuille de calcul Google Sheets.
1. Définissez la température en saisissant `32` dans la cellule A2.
1. Partager le document en cliquant sur **Partager** en haut à droite de la fenêtre et en dessous **Obtenir le lien** click **Modifier**.

   ![Partager la feuille](assets/share-sheet.png)

1. Copiez le lien de l’étape suivante.

   ![Lien de partage](assets/share-link.png)

1. Recherchez l’ID de la feuille.

   * L’ID de la feuille est la chaîne de caractères aléatoire dans le lien de la feuille que vous avez copié après `d/` et avant `/edit`.
   * Par exemple :
      * Si votre URL est `https://docs.google.com/spreadsheets/d/1cNM7j1B52HgMdsjf8frCQrXpnypIb8NkJ98YcxqaEP30/edit#gid=0`
      * L’ID de la feuille est `1cNM7j1B52HgMdsjf8frCQrXpnypIb8NkJ98YcxqaEP30`.

1. Copiez l’ID de la feuille pour une utilisation ultérieure.

#### Test de votre service météorologique {#test-weather-service}

Maintenant que vous avez créé votre source de données en tant que feuille de calcul Google Sheets et que vous avez activé l’accès via l’API, testez-la pour vous assurer que votre &quot;service météorologique&quot; est accessible.

1. Ouvrez un navigateur web.

1. Saisissez la requête suivante, en remplaçant les valeurs d’ID de feuille et de clé API que vous avez enregistrées précédemment.

   ```
   https://sheets.googleapis.com/v4/spreadsheets/<yourSheetID>/values/Sheet1?key=<yourAPIKey>
   ```

1. Si vous recevez des données JSON similaires à ce qui suit, vous pouvez les configurer correctement.

   ```json
   {
     "range": "Sheet1!A1:Z1000",
     "majorDimension": "ROWS",
     "values": [
       [],
       [
         "32"
       ]
     ]
   }
   ```

AEM Screens peut utiliser ce même service pour accéder aux données météorologiques simulées. Cette configuration sera effectuée à l’étape suivante.

### Configuration de ContextHub {#configure-contexthub}

AEM Screens peut modifier le contenu de manière dynamique en fonction du contexte. La démonstration We.Cafe comporte des canaux configurés pour afficher différents contenus en fonction de la température actuelle, en exploitant AEM ContextHub.

>[!TIP]
>
>Pour plus d’informations sur ContextHub, voir [Ressources supplémentaires](#additional-resources) à la fin de ce document.

Lorsque le contenu de l’écran s’affiche, ContextHub appelle votre service météo pour trouver la température actuelle afin de déterminer le contenu à afficher.

À des fins de démonstration, les valeurs de la feuille peuvent être modifiées. ContextHub le reconnaîtra et le contenu s’ajustera dans le canal en fonction de la température mise à jour.

1. Sur l’instance d’auteur AEMaaCS, accédez à **Navigation globale -> Outils -> Sites -> ContextHub**.
1. Sélectionnez le conteneur de configuration qui porte le même nom que celui que vous avez donné au projet lorsque vous avez créé le projet Screens à partir de la propriété **Modèle de site Web We.Cafe**.
1. Sélectionner **Configuration -> Configuration ContextHub -> Google Sheets** puis cliquez sur **Suivant** en haut à droite.
1. La configuration doit déjà comporter des données JSON préconfigurées. Deux valeurs doivent être modifiées :
   1. Remplacer `[your Google Sheets id]` avec l’ID de feuille [vous avez précédemment enregistré.](#create-spreadsheet)
   1. Remplacer `[your Google API Key]` avec la clé API [vous avez précédemment enregistré.](#create-api-key)
1. Cliquez sur **Enregistrer**.

Vous pouvez désormais modifier la valeur de température dans votre feuille de calcul Google Sheet. ContextHub met à jour Screens de manière dynamique lorsqu’il &quot;voit le changement de température&quot;.

### Test des données dynamiques {#test-dynamic}

Maintenant qu’AEM Screens et ContextHub sont connectés à votre service météorologique, vous pouvez le tester pour voir comment les écrans peuvent mettre à jour le contenu de manière dynamique.

1. Accédez à votre instance de création sandbox.
1. Accédez à la console Sites via **Navigation globale -> Sites** et sélectionnez la page suivante : **Screens -> &lt;project-name> -> Canaux -> Matin d’entrée (portrait)**.

   ![Sélectionner le contenu du projet de démonstration](assets/project-content.png)

1. Cliquez sur Modifier dans la barre d’outils ou saisissez la touche de raccourci `e` pour modifier la page.

1. Dans l’éditeur, vous pouvez voir le contenu. Notez qu’une image est fortement éclairée en bleu avec une icône de ciblage dans le coin.

   ![Contenu Screens dans l’éditeur](assets/screens-content-editor.png)

1. Modifiez la température que vous avez saisie dans votre feuille de calcul de 32 à 70 et observez le changement de contenu.

   ![Contenu Screens dans l’éditeur](assets/screens-content-editor-2.png)

En fonction de la température passant d&#39;une température glaciale de 32°F (0°C) à une température confortable de 70°F (21°C), l&#39;image en vedette est passée d&#39;une tasse de thé chauffante à un café fraîchement glacé.

>[!IMPORTANT]
>
>Utilisez uniquement la solution Google Sheets décrite à des fins de démonstration. Adobe ne prend pas en charge l’utilisation de feuilles de calcul Google pour les environnements de production.

## Connexion à Screens as a Cloud Service {#connect-screens}

Si vous souhaitez également configurer une véritable expérience de signalétique digitale, y compris un lecteur qui s’exécute sur un périphérique de signalétique digitale ou sur votre ordinateur, procédez comme suit.

Vous pouvez également prévisualiser la démonstration simplement dans l’éditeur de canal sur AEMaaCS.

>[!TIP]
>
>Pour plus d’informations sur l’éditeur de canal, reportez-vous à la section [Ressources supplémentaires](#additional-resources) à la fin de ce document.

### Configuration d’AEM Screens as a Cloud Service {#configure-screens}

Tout d’abord, vous devez publier votre contenu de démonstration Screens sur AEM Screens as a Cloud Service et configurer le service.

1. Publiez le contenu de votre projet d’écrans de démonstration.
1. Accédez à Screens as a Cloud Service à l’adresse `https://experience.adobe.com/screens` et connectez-vous.
1. Dans le coin supérieur droit de l’écran, vérifiez que vous vous trouvez dans la bonne organisation.

   ![Vérifiez votre organisation Screens](assets/screens-org.png)

1. En haut à gauche, cliquez sur le **Modifier les paramètres** en forme d&#39;engrenage.

   ![Modifier les paramètres](assets/screens-edit-settings.png)

1. Indiquez les URL des instances d’auteur et de publication AEMaaCS dans lesquelles vous avez créé votre site de démonstration, puis cliquez sur **Enregistrer**.

   ![Paramètre Screens](assets/screens-settings.png)

1. Une fois connecté à vos instances de démonstration, Screens extrait le contenu de votre canal. Cliquez sur **Canaux** dans le panneau de gauche pour afficher les canaux publiés. Il faudra peut-être un moment pour que l&#39;information soit renseignée. Vous pouvez cliquer sur le bouton bleu **Synchronisation** en haut à droite de l’écran pour mettre à jour les informations.

   ![Informations sur le canal de démonstration](assets/screens-channels.png)

1. Cliquez sur **Affichages** dans le panneau de gauche. Vous n’en avez pas encore créé pour votre démonstration. Nous simulerons l’emplacement de We.Cafe en créant des dossiers pour chacun d’eux. Cliquez sur **Créer** dans le coin supérieur droit de l’écran, puis sélectionnez **Dossier**.

   ![Créer un affichage](assets/screens-displays.png)

1. Dans la boîte de dialogue, indiquez un nom de dossier tel que **San Jose** et cliquez sur **Créer**.

1. Ouvrez le dossier en cliquant dessus, puis cliquez sur **Créer** en haut à droite et sélectionnez **Affichage**.

1. Indiquez un nom d’affichage et cliquez sur **Créer**.

   ![Créer un affichage](assets/create-display.png)

1. Une fois l’affichage créé, cliquez sur son nom pour ouvrir l’écran des détails de l’affichage. Un canal synchronisé à partir de votre site de démonstration doit être affecté à l’affichage. Cliquez sur **Attribuer le canal** en haut à droite de l’écran.

   ![Détails du canal](assets/channel-detail.png)

1. Dans la boîte de dialogue, sélectionnez le canal et cliquez sur **Attribuer**.

   ![Attribuer le canal](assets/assign-channel.png)

Vous pouvez répéter ces étapes pour vos autres emplacements et affichages. Une fois terminé, vous avez lié votre site de démonstration à AEM Screens et terminé la configuration nécessaire.

Vous pouvez prévisualiser la démonstration simplement dans l’éditeur de canal sur AEMaaCS.

### Utilisation du lecteur Screens {#screens-player}

Pour afficher le contenu tel qu’il se trouve sur un écran réel, vous pouvez télécharger le lecteur et le configurer localement. AEM Screens as a Cloud Service diffuse ensuite le contenu sur votre lecteur

#### Génération d’un code d’enregistrement {#registration-code}

Vous devez d’abord créer un code d’enregistrement pour connecter un lecteur à AEM Screens as a Cloud Service en toute sécurité.

1. Accédez à Screens as a Cloud Service à l’adresse `https://experience.adobe.com/screens` et connectez-vous.
1. Dans le coin supérieur droit de l’écran, vérifiez que vous vous trouvez dans la bonne organisation.

   ![Vérifiez votre organisation Screens](assets/screens-org.png)

1. Dans le panneau de gauche, cliquez sur **Gestion du lecteur -> Codes d’enregistrement** puis cliquez sur **Créer du code** en haut à droite de l’écran.

![Codes d’enregistrement](assets/registration-codes.png)

1. Saisissez le nom du code, puis cliquez sur **Créer**.

   ![Créer du code](assets/create-code.png)

1. Une fois le code créé, il apparaît dans la liste. Cliquez sur pour copier le code.

   ![Code d’enregistrement](assets/registration-code.png)

#### Installation et configuration du lecteur {#install-player}

1. Téléchargez le lecteur correspondant à votre plateforme depuis `https://download.macromedia.com/screens/` et installez-le.
1. Exécutez le lecteur et passez à la **Configuration** , faites défiler la page vers le bas pour cliquer et confirmer les deux **Réinitialiser à l’usine** puis **Passage en mode cloud**.

   ![Paramètres du lecteur](assets/player-configuration.png)

1. Le lecteur se transforme automatiquement en **Enregistrement du lecteur** . Saisissez le code que vous avez généré précédemment et cliquez sur **Enregistrer**.

   ![Enregistrement du lecteur](assets/player-registration-code.png)

1. Basculez vers le **Informations système** pour confirmer que le lecteur a été enregistré.

   ![Lecteur enregistré](assets/player-registered.png)

#### Attribution d’un lecteur à un affichage {#assign-player}

1. Accédez à Screens as a Cloud Service à l’adresse `https://experience.adobe.com/screens` et connectez-vous.
1. Dans le coin supérieur droit de l’écran, vérifiez que vous vous trouvez dans la bonne organisation.

   ![Vérifiez votre organisation Screens](assets/screens-org.png)

1. Dans le panneau de gauche, cliquez sur **Gestion du lecteur -> Lecteurs** et vous verrez le lecteur que vous avez installé et enregistré précédemment.

   ![Lecteurs](assets/players.png)

1. Cliquez sur le nom du lecteur pour en ouvrir les détails, puis cliquez sur **Attribuer à l’affichage** dans le coin supérieur droit de l’écran.

   ![Attribuer le lecteur à afficher](assets/assign-to-display.png)

1. Dans la boîte de dialogue, sélectionnez l’affichage que vous avez créé précédemment, puis cliquez sur **Sélectionner**.

   ![Attribuer un affichage](assets/assign-a-display.png)

#### Lecture! {#playback}

Une fois que vous avez attribué un affichage à un lecteur, AEM Screens as a Cloud Service diffuse le contenu sur votre lecteur là où il est visible.

![Portrait d’entrée](assets/entrance-portrait.jpg)

![Paysage d’entrée](assets/entrance-landscape.jpg)

## Prochaines étapes {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de module complémentaire de démonstration de référence d’AEM, vous devez :

* Connaître les principes de base d’AEM Screens.
* Découvrez le contenu de démonstration de We.Cafe.
* Découvrez comment configurer AEM Screens pour We.Cafe.

Vous êtes maintenant prêt à explorer les fonctionnalités d’AEM Screens à l’aide de vos propres sites de démonstration. Passez à la section suivante du parcours, [Gérer vos sites de démonstration,](manage.md) où vous découvrirez les outils disponibles pour vous aider à gérer vos sites de démonstration et comment les supprimer.

Vous pouvez également extraire certaines des ressources supplémentaires disponibles dans le [Section Ressources supplémentaires](#additional-resources) pour en savoir plus sur les fonctionnalités que vous avez vues dans ce parcours.

## Ressources supplémentaires {#additional-resources}

* [Documentation ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md) - Découvrez comment ContextHub peut être utilisé pour personnaliser le contenu en fonction du contexte utilisateur au-delà des conditions météorologiques.
* [Utilisation des clés API - Documentation Google](https://developers.google.com/maps/documentation/javascript/get-api-key) - Référence pratique pour plus d’informations sur l’utilisation des clés d’API Google.
* [Affichages](/help/screens-cloud/creating-content/creating-displays-screens-cloud.md) - En savoir plus sur l’affichage dans AEM Screens et sur ce qu’il peut faire.
* [Télécharger le lecteur](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md) - Découvrez comment accéder au lecteur Screens et comment l’installer.
* [Enregistrer le lecteur](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) - Découvrez comment configurer et enregistrer un lecteur avec votre projet AEM Screens.
* [Attribution d’un lecteur à un affichage](/help/screens-cloud/managing-players-registration/assigning-player-display.md) - Configurez un lecteur pour afficher votre contenu.

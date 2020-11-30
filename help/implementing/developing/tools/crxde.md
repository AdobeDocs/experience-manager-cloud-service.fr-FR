---
title: 'Utilisation de CRXDE Lite '
description: CRXDE Lite fait partie de l'AEM démarrage rapide et vous permet d'accéder et de modifier le référentiel dans vos environnements de développement locaux dans le navigateur.
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 21%

---


# Utilisation de CRXDE Lite  {#using-crxde-lite}

CRXDE Lite fait partie de l&#39;AEM démarrage rapide et vous permet d&#39;accéder et de modifier le référentiel dans vos environnements de développement locaux dans le navigateur. Avec CRXDE Lite, vous pouvez modifier des fichiers, des dossiers, des noeuds et des propriétés. Le référentiel entier est accessible dans cette interface conviviale.

>[!NOTE]
>
>Le CRXDE Lite est disponible uniquement dans vos environnements de développement local. Il n&#39;est pas disponible en AEM en tant que Cloud Service.

## Prise en main de CRXDE Lite {#getting-started-with-crxde-lite}

Pour commencer avec le CRXDE Lite :

1. Débuts rapidement votre développement AEM local.
1. In your browser, open the URL `https://<host>:<port>/crx/de`.
1. Entrez votre **nom d’utilisateur** et votre **mot de passe**.
1. Cliquez sur **OK**.

L’interface utilisateur de CRXDE Lite est la suivante dans votre navigateur : 

![Interface du CRXDE Lite](assets/crxde-lite.png)

Vous pouvez désormais utiliser CRXDE Lite pour développer votre application.

>[!TIP]
>
>Vous pouvez également accéder au CRXDE Lite à partir du menu AEM. Dans le menu principal, sélectionnez **Outils** -> **Général** -> **CRXDE Lite**.

## Présentation de l’interface utilisateur {#overview-of-the-user-interface}

L&#39;interface utilisateur du CRXDE Lite comporte de nombreuses parties et de nombreuses fonctions.

### Barre de commutation supérieure {#top-switcher-bar}

La barre de commutation supérieure vous permet de basculer rapidement entre CRXDE Lite, Package Manager et Package Share.

### Node Path Widget {#node-path-widget}

Le widget Chemin d’accès au noeud affiche le chemin d’accès au noeud actuellement sélectionné.

Vous pouvez également l’utiliser pour accéder à un noeud en entrant le chemin manuellement ou en le collant à partir d’un autre emplacement et en appuyant sur Entrée.

Il permet aussi de rechercher des nœuds par nom de nœud. Saisissez le nom du noeud que vous souhaitez rechercher et attendez (ou sélectionnez l’icône de recherche sur la droite). Si un ou plusieurs noeuds donnés sont chargés dans le volet explorateur, la liste s’affiche et vous pouvez sélectionner le chemin et appuyer sur Entrée pour y accéder. Notez que la recherche ne fonctionne que pour les nœuds actuellement chargés dans l’application cliente CRXDE dans le navigateur. If you want to search the whole repository, use **Tools** -&amp;gt: **Query**.

### Explorer Pane {#explorer-pane}

Le volet **** Explorateur affiche une arborescence de tous les noeuds du référentiel.

Cliquez sur un nœud pour afficher ses propriétés dans l’onglet **Propriétés**. Après avoir cliqué sur un nœud, vous pouvez sélectionner une action dans la barre d’outils. Cliquez à nouveau sur le nœud pour le renommer.

Tree Navigation Filter (l&#39;icône de jumelles) permet de filtrer les noeuds du référentiel pour lesquels le nom contient le texte d&#39;entrée. S’applique uniquement aux nœuds qui ont été chargés localement.

### Edit Pane {#edit-pane}

Le volet **Modifier** vous permet de vue le contenu du fichier actuellement sélectionné dans le référentiel. Chaque fichier ouvert sera représenté sous la forme de son propre onglet dans le volet.

L’onglet **Accueil** vous permet de rechercher du contenu et/ou de la documentation et d’accéder à la documentation destinée aux développeurs et à la prise en charge des Adobes.

Cliquez avec le doublon sur un fichier dans le volet **** Explorateur pour afficher son contenu dans le volet de **modification**. Vous pouvez ensuite le modifier et enregistrer les modifications.

Once a file is edited in the **Edit Pane**, the following tools are available on the toolbar:

* **Afficher dans l&#39;arborescence** : affiche le fichier dans l&#39;arborescence du référentiel.
* **Search/Replace** : effectue une recherche ou un remplacement.

Double-click on the status line of the **Edit Pane** opens the **Go to line** dialog so you can enter a specific line number.

### Onglet Propriétés {#properties-tab}

L’onglet **** Propriétés affiche les propriétés du noeud que vous avez sélectionné. Vous pouvez ajouter de nouvelles propriétés ou supprimer celles qui existent déjà.

### Access Control Tab {#access-control-tab}

L’onglet **** Contrôle d&#39;accès affiche les autorisations en fonction du chemin d’accès, du référentiel ou de l’entité de sécurité actuelle.

Les autorisations sont ventilées en catégories suivantes.

* **Stratégie** de Contrôle d&#39;accès applicable - Stratégies qui peuvent être appliquées à la sélection actuelle
* **Stratégies** de Contrôle d&#39;accès local - Stratégies appliquées localement à la sélection actuelle
* **Stratégies** de Contrôle d&#39;accès efficaces - Stratégies appliquées actuellement à la sélection actuelle, qui peuvent être définies localement ou héritées des noeuds parents

>[!NOTE]
Pour pouvoir afficher les informations du contrôle d&#39;accès, l’utilisateur connecté au CRXDE Lite doit disposer des droits de lecture des entrées de liste de contrôle d’accès.

### Replication Tab {#replication-tab}

L&#39;onglet **** Réplication affiche l&#39;état de réplication du noeud actif. Vous pouvez répliquer et supprimer la réplication du nœud actif.

###  Console Tab {#console-tab}

L&#39;onglet **** Console affiche les messages des journaux. Vous pouvez configurer le niveau de journalisation, effacer la console, épingler à la position de défilement sélectionnée et activer/désactiver l’affichage des messages.

### Build Info Tab {#build-info-tab}

L’onglet **Informations de** création affiche des informations lorsqu’un lot est en cours de création.

### Bouton Actualiser {#refresh-button}

Le bouton **Actualiser** actualise la sélection en cours. Les modifications des autres utilisateurs sont mises à jour dans votre vue du référentiel. Les modifications que vous avez apportées ne sont pas concernées.

### Bouton Enregistrer tout {#save-all-button}

Le bouton **Enregistrer tout** enregistre toutes les modifications que vous avez apportées. Tant que vous n’avez pas choisi d’enregistrer, les modifications sont temporaires et seront perdues lorsque vous quitterez la console.

* **Rétablir** : ignore toutes les modifications que vous avez apportées au noeud sélectionné depuis la dernière action d&#39;enregistrement, puis recharge l&#39;état actuel du référentiel pour le noeud sélectionné.
* **Annuler tout** - Ignore toutes les modifications que vous avez effectuées dans tout le référentiel depuis la dernière action d&#39;enregistrement, puis recharge l&#39;état actuel du référentiel.

### Bouton Créer {#create-button}

Le bouton **** Créer est un menu déroulant qui permet de créer les éléments suivants sous le noeud sélectionné :

* Noeud - un noeud avec un type de noeud arbitraire
* File - an `nt:file` node and its nt:resource subnode
* Dossier - un `nt:folder` noeud

### Delete Button {#delete-button}

Le bouton **Supprimer** supprime le noeud sélectionné.

### Copy Button {#copy-button}

Le bouton **Copier** copie le noeud sélectionné.

## Paste Button {#paste-button}

Le bouton **** Coller colle le noeud copié sous le noeud sélectionné.

### Move Button {#move-button}

The **Move Button** moves the selected node to the node that is set through the dialog.

### Renommer {#rename-button}

Le bouton **Renommer** renomme le noeud sélectionné.

### Mixins {#mixins-button}

Le bouton **** Mélanges vous permet d’ajouter des types de mixins au type de noeud. Les types de mixin sont principalement utilisés pour ajouter des fonctions avancées.

### Outils {#tools-button}

Le bouton **** Outils est un menu déroulant contenant les outils suivants :

* **Configuration** du serveur - pour accéder à la console Felix (également disponible sur `https://<host>:<port>/system/console/configMgr`)
* **Requête** - requête du référentiel
* **Privilèges** - vue et ajout de privilèges
* **Contrôle d&#39;accès** de test : pour tester l&#39;autorisation pour un chemin et/ou une entité principale
* **Exporter le type** de noeud - pour exporter les types de noeud dans le système sous forme de notation CND
* **Importer le type** de noeud - pour importer les types de noeud à l&#39;aide de la notation CND.

### Login Widget {#login-widget}

Le widget **de** connexion affiche l’utilisateur actuellement connecté.

Cliquez dessus pour vous connecter ou vous reconnecter en tant qu’autre utilisateur. Le `@crx.default` indique que vous vous trouvez dans l’espace de travail par défaut (et uniquement) du référentiel.

L&#39;option **Préférences** permet de définir la langue de l&#39;interface utilisateur, de vue et de personnaliser les touches d&#39;accès rapide pour diverses actions telles que l&#39;enregistrement, la recherche, la création de notes, etc.

## Création d’un dossier {#creating-a-folder}

Pour créer un dossier avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. In the Navigation pane, right-click the folder under which you want to create the new folder, select **Create ...**, then **Create Folder ...**.

1. Entrez le **nom** du dossier et cliquez sur **OK**.

1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications sur le serveur.

## Création d’un nœud {#creating-a-node}

Pour créer un nœud avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. In the [**Exploerer Pane**,](#explorer-pane) right-click the node where you want to create the new node, select **Create**, then **Create Node**.
1. Enter the **Name** and select the **Type**.
1. Cliquez sur **OK**.
1. Click the [**Save All Button**](#save-all-button) to save the changes on the server.

Vous pouvez désormais adapter le nœud à vos besoins en modifiant les propriétés ou en ajoutant de nouveaux nœuds.

>[!NOTE]
Most of the edit operations, including **Create Node**, keeps all the changes in memory, and only stores them in the repository upon saving (using the [**Save All Button**](#save-all-button)). Cependant, certaines opérations telles que le déplacement sont automatiquement conservées.
La validation quant à savoir si le noeud nouvellement créé est autorisé par le type de noeud du noeud parent est également effectuée par le référentiel lors de l’enregistrement des modifications. If you receive an error message while saving a node, please check if the content structure is valid (e.g. you cannot create an `nt:unstructured` node as a child of `nt:folder` node).

## Création d’une propriété {#creating-a-property}

Pour créer une propriété avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. In the [**Exploerer Pane**,](#explorer-pane) select the node where you want to add the new property.
1. In the [**Properties Tab**](#properties-tab) in the bottom pane, enter the **Name**, the **Type**, and the **Value**.
1. Cliquez sur **Ajouter**.
1. Click the [**Save All Button**](#save-all-button) to save the changes on the server.

## Création d’un fichier {#creating-a-file}

Pour créer un fichier avec un CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. In the [**Exploerer Pane**,](#explorer-pane) right-click the component where you want to create the file, select **Create**, then **Create File**.
1. Enter the file **Name** including its extension.
1. Cliquez sur **OK**.
1. The new file opens as a tab in the [**Edit Pane**.](#edit-pane)
1. Modifiez le fichier.
1. Click the [**Save All Button**](#save-all-button) to save the changes.

## Exportation et importation de types de nœuds {#exporting-and-importing-node-types}

With CRXDE Lite you can import and/or export node type definitions in [Compact Namespace and Node Type Definition (CND) notation](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Pour exporter une définition de type de noeud dans le CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Sélectionnez le nœud en question.
1. Sélectionnez **Outils**, puis **Exporter le type de nœud**.
1. La définition s&#39;affichera en notation CND dans un nouvel onglet de votre navigateur.
1. Enregistrez les informations si nécessaire.

Pour importer une définition de type de nœud :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Sélectionnez **Outils**, puis **Importer le type de nœud**.
1. Un nouvel onglet s&#39;ouvre dans le volet de [**modification**](#edit-pane) intitulé **Importer le type** de noeud.
1. Saisissez la notation CND pour la définition dans la zone de texte de l’onglet Type **de noeud** d’importation.
1. Cochez **Autoriser la mise à jour** si vous mettez à jour une définition existante.
1. Cliquez sur **Importer**.

## Journalisation {#logging}

With CRXDE Lite you can display the file `error.log` that is located on the file system at `<aem-install-dir>/crx-quickstart/logs` and filter it with the appropriate log level. Procédez comme suit :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le menu déroulant situé à droite de l&#39;onglet [****](#console-tab) Console au bas de la fenêtre, sélectionnez Journaux **** serveur.
1. Cliquez sur l’icône **Stop** pour afficher les messages.

Vous pouvez :

* Adjust the log parameters in the Felix Console by clicking the **Logging Configurations** icon.
* Clear the messages by clicking the **Clear Console** icon.
* Pin the message at the current selection by clicking the **Pin Console** icon.
* Activer ou désactiver l’affichage des messages en cliquant sur l’icône **Stop**.

---
title: 'Utilisation de CRXDE Lite '
description: CRXDE Lite fait partie de l'AEM démarrage rapide et vous permet d'accéder et de modifier le référentiel dans vos environnements de développement locaux dans le navigateur.
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 21%

---


# Utilisation de CRXDE Lite   {#using-crxde-lite}

CRXDE Lite fait partie de l&#39;AEM démarrage rapide et vous permet d&#39;accéder et de modifier le référentiel dans vos environnements de développement locaux dans le navigateur. Avec CRXDE Lite, vous pouvez modifier des fichiers, des dossiers, des noeuds et des propriétés. Le référentiel entier est accessible dans cette interface conviviale.

>[!NOTE]
>
>Le CRXDE Lite est disponible uniquement dans vos environnements de développement local. Il n&#39;est pas disponible en AEM en tant que Cloud Service.

## Prise en main de CRXDE Lite {#getting-started-with-crxde-lite}

Pour commencer avec le CRXDE Lite :

1. Débuts rapidement votre développement AEM local.
1. Dans votre navigateur, ouvrez l’URL `https://<host>:<port>/crx/de`.
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

### Widget de chemin de noeud {#node-path-widget}

Le widget Chemin d’accès au noeud affiche le chemin d’accès au noeud actuellement sélectionné.

Vous pouvez également l’utiliser pour accéder à un noeud en entrant le chemin manuellement ou en le collant à partir d’un autre emplacement et en appuyant sur Entrée.

Il permet aussi de rechercher des nœuds par nom de nœud. Saisissez le nom du noeud que vous souhaitez rechercher et attendez (ou sélectionnez l’icône de recherche sur la droite). Si un ou plusieurs noeuds donnés sont chargés dans le volet explorateur, la liste s’affiche et vous pouvez sélectionner le chemin et appuyer sur Entrée pour y accéder. Notez que la recherche ne fonctionne que pour les nœuds actuellement chargés dans l’application cliente CRXDE dans le navigateur. Si vous souhaitez effectuer une recherche dans l&#39;ensemble du référentiel, utilisez **Outils** -&amp;gt: **Requête**.

### Volet Explorateur {#explorer-pane}

Le **volet Explorateur** affiche une arborescence de tous les noeuds du référentiel.

Cliquez sur un nœud pour afficher ses propriétés dans l’onglet **Propriétés**. Après avoir cliqué sur un nœud, vous pouvez sélectionner une action dans la barre d’outils. Cliquez à nouveau sur le nœud pour le renommer.

Tree Navigation Filter (l&#39;icône de jumelles) permet de filtrer les noeuds du référentiel pour lesquels le nom contient le texte d&#39;entrée. S’applique uniquement aux nœuds qui ont été chargés localement.

### Volet Modifier {#edit-pane}

Le **volet de modification** vous permet de vue du contenu du fichier actuellement sélectionné dans le référentiel. Chaque fichier ouvert sera représenté sous la forme de son propre onglet dans le volet.

L&#39;onglet **Accueil** vous permet de rechercher du contenu et/ou de la documentation et d&#39;accéder à la documentation destinée aux développeurs et à la prise en charge des Adobes.

Cliquez sur un fichier dans le **volet Explorateur** pour afficher son contenu dans le **volet Edition**. Vous pouvez ensuite le modifier et enregistrer les modifications.

Une fois qu&#39;un fichier est modifié dans le **volet de modification**, les outils suivants sont disponibles sur la barre d&#39;outils :

* **Afficher dans l&#39;arborescence**  : affiche le fichier dans l&#39;arborescence du référentiel.
* **Search/Replace**  : effectue une recherche ou un remplacement.

Cliquez doublon sur la ligne d&#39;état du **volet de modification** pour ouvrir la boîte de dialogue **Atteindre la ligne** afin de pouvoir entrer un numéro de ligne spécifique.

### Onglet Propriétés {#properties-tab}

L&#39;onglet **Propriétés** affiche les propriétés du noeud que vous avez sélectionné. Vous pouvez ajouter de nouvelles propriétés ou supprimer celles qui existent déjà.

### Onglet contrôle d&#39;accès {#access-control-tab}

L&#39;onglet **Contrôle d&#39;accès** affiche les autorisations en fonction du chemin d&#39;accès, du référentiel ou de l&#39;entité de sécurité actuelle.

Les autorisations sont ventilées en catégories suivantes.

* **Stratégie**  de Contrôle d&#39;accès applicable - Stratégies qui peuvent être appliquées à la sélection actuelle
* **Stratégies**  de Contrôle d&#39;accès local - Stratégies appliquées localement à la sélection actuelle
* **Stratégies**  de Contrôle d&#39;accès efficaces - Stratégies appliquées actuellement à la sélection actuelle, qui peuvent être définies localement ou héritées des noeuds parents

>[!NOTE]
Pour pouvoir afficher les informations du contrôle d&#39;accès, l’utilisateur connecté au CRXDE Lite doit disposer des droits de lecture des entrées de liste de contrôle d’accès.

### Onglet Réplication {#replication-tab}

L&#39;onglet **Réplication** affiche l&#39;état de réplication du noeud actuel. Vous pouvez répliquer et supprimer la réplication du nœud actif.

###  Onglet Console {#console-tab}

L&#39;**onglet Console** affiche les messages des journaux. Vous pouvez configurer le niveau de journalisation, effacer la console, épingler à la position de défilement sélectionnée et activer/désactiver l’affichage des messages.

### Onglet Infos de création {#build-info-tab}

L&#39;onglet **Infos sur la création** affiche des informations lorsqu&#39;un lot est en cours de création.

### Bouton Actualiser {#refresh-button}

Le **bouton Actualiser** actualise la sélection actuelle. Les modifications des autres utilisateurs sont mises à jour dans votre vue du référentiel. Les modifications que vous avez apportées ne sont pas concernées.

### Bouton Enregistrer tout {#save-all-button}

Le bouton **Enregistrer tout** enregistre toutes les modifications que vous avez apportées. Tant que vous n’avez pas choisi d’enregistrer, les modifications sont temporaires et seront perdues lorsque vous quitterez la console.

* **Rétablir**  - Ignore toutes les modifications que vous avez effectuées sur le noeud sélectionné depuis la dernière action d&#39;enregistrement, puis recharge l&#39;état actuel du référentiel pour le noeud sélectionné.
* **Annuler tout**  - Ignore toutes les modifications que vous avez effectuées dans tout le référentiel depuis la dernière action d&#39;enregistrement, puis recharge l&#39;état actuel du référentiel.

### Bouton Créer {#create-button}

Le **bouton Créer** est un menu déroulant qui permet de créer les éléments suivants sous le noeud sélectionné :

* Noeud - un noeud avec un type de noeud arbitraire
* Fichier : un noeud `nt:file` et son sous-noeud nt:resource
* Dossier - un noeud `nt:folder`

### Bouton Supprimer {#delete-button}

Le **bouton Supprimer** supprime le noeud sélectionné.

### Bouton Copier {#copy-button}

Le **bouton Copier** copie le noeud sélectionné.

## Bouton Coller {#paste-button}

Le **bouton Coller** colle le noeud copié sous le noeud sélectionné.

### Bouton Déplacer {#move-button}

Le **bouton Déplacer** déplace le noeud sélectionné vers le noeud défini dans la boîte de dialogue.

### Renommer {#rename-button}

**Renommer le bouton** renomme le noeud sélectionné.

### Mixins {#mixins-button}

Le bouton **Mixins** vous permet d’ajouter des types de mixin au type de noeud. Les types de mixin sont principalement utilisés pour ajouter des fonctions avancées.

### Outils {#tools-button}

Le **bouton Outils** est un menu déroulant avec les outils suivants disponibles :

* **Configuration**  du serveur - pour accéder à la console Felix (également disponible sur  `https://<host>:<port>/system/console/configMgr`)
* **Requête**  - vers la requête du référentiel
* **Privilèges**  - vue et ajout de privilèges
* **Contrôle d&#39;accès**  de test : pour tester l&#39;autorisation pour un chemin et/ou une entité de sécurité
* **Exporter le type**  de noeud - pour exporter les types de noeud dans le système sous forme de notation CND
* **Importer un type**  de noeud - pour importer des types de noeud à l&#39;aide de la notation CND.

### Widget de connexion {#login-widget}

Le **widget de connexion** affiche l&#39;utilisateur actuellement connecté.

Cliquez dessus pour vous connecter ou vous reconnecter en tant qu’autre utilisateur. `@crx.default` indique que vous vous trouvez dans l&#39;espace de travail par défaut (et uniquement) du référentiel.

L&#39;option **Préférences** permet de définir la langue de l&#39;interface utilisateur et de vue et de personnaliser les touches d&#39;accès rapide pour diverses actions telles que l&#39;enregistrement, la recherche, la création de notes, etc.

## Création d’un dossier {#creating-a-folder}

Pour créer un dossier avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, cliquez avec le bouton droit sur le dossier sous lequel vous souhaitez créer le nouveau dossier, sélectionnez **Créer ...**, puis **Créer un dossier...**.

1. Entrez le **nom** du dossier et cliquez sur **OK**.

1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications sur le serveur.

## Création d’un nœud {#creating-a-node}

Pour créer un nœud avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le [**volet Exploerer**,](#explorer-pane) cliquez avec le bouton droit de la souris sur le noeud où vous souhaitez créer le nouveau noeud, sélectionnez **Créer**, puis **Créer un noeud**.
1. Saisissez le **nom** et sélectionnez le **type**.
1. Cliquez sur **OK**.
1. Cliquez sur le bouton [**Enregistrer tout**](#save-all-button) pour enregistrer les modifications sur le serveur.

Vous pouvez désormais adapter le nœud à vos besoins en modifiant les propriétés ou en ajoutant de nouveaux nœuds.

>[!NOTE]
La plupart des opérations de modification, y compris **Créer un noeud**, conservent toutes les modifications en mémoire et les stockent uniquement dans le référentiel lors de l&#39;enregistrement (à l&#39;aide du bouton [**Enregistrer tout**](#save-all-button)). Cependant, certaines opérations telles que le déplacement sont automatiquement conservées.
La validation quant à savoir si le noeud nouvellement créé est autorisé par le type de noeud du noeud parent est également effectuée par le référentiel lors de l’enregistrement des modifications. Si vous recevez un message d’erreur lors de l’enregistrement d’un noeud, vérifiez si la structure de contenu est valide (par exemple, vous ne pouvez pas créer un noeud `nt:unstructured` comme enfant d’un noeud `nt:folder`).

## Création d’une propriété {#creating-a-property}

Pour créer une propriété avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le [**volet Exploerer**,](#explorer-pane) sélectionnez le noeud sur lequel vous souhaitez ajouter la nouvelle propriété.
1. Dans l&#39;onglet [**Propriétés**](#properties-tab) du volet inférieur, saisissez **Nom**, **Type** et **Valeur**.
1. Cliquez sur **Ajouter**.
1. Cliquez sur le bouton [**Enregistrer tout**](#save-all-button) pour enregistrer les modifications sur le serveur.

## Création d&#39;un fichier {#creating-a-file}

Pour créer un fichier avec un CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le [**Volet de l&#39;explorateur**,](#explorer-pane) cliquez avec le bouton droit de la souris sur le composant dans lequel vous souhaitez créer le fichier, sélectionnez **Créer**, puis **Créer un fichier**.
1. Saisissez le fichier **Name**, y compris son extension.
1. Cliquez sur **OK**.
1. Le nouveau fichier s&#39;ouvre sous forme d&#39;onglet dans le [**volet de modification**.](#edit-pane)
1. Modifiez le fichier.
1. Cliquez sur le bouton [**Enregistrer tout**](#save-all-button) pour enregistrer les modifications.

## Exportation et importation de types de nœuds {#exporting-and-importing-node-types}

Avec CRXDE Lite, vous pouvez importer et/ou exporter des définitions de type de noeud dans [Node Type Definition (CND) et Espace de nommage compact ](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Pour exporter une définition de type de noeud dans le CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Sélectionnez le nœud en question.
1. Sélectionnez **Outils**, puis **Exporter le type de nœud**.
1. La définition s&#39;affichera en notation CND dans un nouvel onglet de votre navigateur.
1. Enregistrez les informations si nécessaire.

Pour importer une définition de type de nœud :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Sélectionnez **Outils**, puis **Importer le type de nœud**.
1. Un nouvel onglet s&#39;ouvre dans le [**volet de modification**](#edit-pane) intitulé **Type de noeud d&#39;importation**.
1. Saisissez la notation CND pour la définition dans la zone de texte de l’onglet **Type de noeud d’importation**.
1. Cochez **Autoriser la mise à jour** si vous mettez à jour une définition existante.
1. Cliquez sur **Importer**.

## Journalisation {#logging}

Avec CRXDE Lite, vous pouvez afficher le fichier `error.log` situé sur le système de fichiers à `<aem-install-dir>/crx-quickstart/logs` et le filtrer au niveau de journal approprié. Procédez comme suit :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le menu déroulant situé à droite de l&#39;[**onglet Console**](#console-tab) au bas de la fenêtre, sélectionnez **Journaux du serveur**.
1. Cliquez sur l’icône **Stop** pour afficher les messages.

Vous pouvez :

* Réglez les paramètres de journal dans la console Felix en cliquant sur l&#39;icône **Configurations de journalisation**.
* Effacez les messages en cliquant sur l&#39;icône **Effacer la console**.
* Epinglez le message sur la sélection en cours en cliquant sur l&#39;icône **Épingler la console**.
* Activer ou désactiver l’affichage des messages en cliquant sur l’icône **Stop**.

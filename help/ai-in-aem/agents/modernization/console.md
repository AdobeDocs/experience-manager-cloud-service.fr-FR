---
title: Console de modernisation de l’expérience
description: Guide de référence de l’interface et des fonctionnalités de la console de modernisation de l’expérience
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: c2f258bfcfff8392af2863d874d4a4235f042193
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---


# Console de modernisation de l’expérience {#console-reference}

Guide de référence de l’interface et des fonctionnalités de la console de modernisation de l’expérience

>[!NOTE]
>
>Si vous souhaitez utiliser la console de modernisation de l’expérience, vous pouvez demander l’accès pour garantir une expérience d’intégration fluide.

## Vue d’ensemble {#overview}

La console de modernisation de l’expérience est un environnement de développement hébergé et assisté par l’IA pour Edge Delivery Services, exposé sous forme d’interface web à l’adresse [`aemcoder.adobe.io`.](https://aemcoder.adobe.io) Une fois connecté à son projet GitHub, vous pouvez commencer immédiatement à demander des modifications en langage naturel sans configuration supplémentaire ni configuration de l’environnement local.

>[!TIP]
>
>Si vous souhaitez commencer immédiatement à utiliser la console, consultez le document [Prise en main de l’agent de modernisation de l’expérience](/help/ai-in-aem/agents/modernization/getting-started.md).

## Fonctionnalités {#capabilities}

Fonctionnalités principales de la console :

* Panneau de conversation interactif avec l’agent et ses compétences
* Aperçu AEM en direct pour un retour visuel immédiat sur les modifications
* Explorateur de fichiers de contenu et visionneuse Markdown
* Synchronisation de contenu avec [la création de documents](https://da.live)
* Explorateur de code et visionneuse diff pour la révision des modifications apportées
* Intégration GitHub avec la possibilité de créer des demandes d’extraction à partir de modifications

Les développeurs gardent le contrôle total sur les navires. Toutes les modifications apportées par le biais de la console doivent être examinées et approuvées avant le déploiement, afin d’assurer la gouvernance, la cohérence de la marque et la sécurité.

## Navigation {#navigation}

Après vous être connecté à la console à l’adresse [`aemcoder.adobe.io`,](https://aemcoder.adobe.io) vous accédez à l’écran d’accueil de la console.

![Écran d’accueil de la console ](assets/console-home.png)

### Barre de menus {#menu-bar}

La barre de menus supérieure affiche les éléments suivants :

* Bouton **Ouvrir le menu** sur la gauche pour développer et réduire le détail du panneau latéral gauche
* Un bouton **Compte** à droite pour passer en mode sombre et vous déconnecter de la console

### Barre latérale gauche {#sidebar}

La barre latérale gauche permet d’accéder rapidement aux vues importantes de la console.

* **[Vue d’accueil](#home-view)** (icône maison) - Votre point de départ pour utiliser la console
* **[Affichage du contenu](#content-view)** (icône de fichier) - Contenu que vous avez importé
* **[Affichage du code](#code-view)** (icône `</>`) - Code du site sur lequel vous travaillez
* **[Vue Paramètres](#settings-view)** (icône d’engrenage) - Paramètres de la console

## Affichage de l’accueil {#home-view}

La vue **Accueil** est le point de départ pour utiliser la console.

* En haut se trouve un [panneau d’invite](#prompt-panel) permettant d’envoyer des requêtes à la console.
* Sous le panneau d’invite se trouvent des invites à utiliser pour démarrer votre projet.

### Panneau d’invite {#prompt-panel}

Le panneau d’invite fournit des commandes permettant d’interagir avec l’IA.

* **Modes de planification/d’exécution** (icône d’ampoule et de baguette magique) : basculez entre les modes de planification et d’exécution, respectivement
   * **Mode Plan** : l’IA analyse les requêtes et décrit une approche sans apporter de modifications, ce qui est utile pour comprendre la stratégie avant la validation.
   * **Mode d’exécution** : l’IA exécute le plan et apporte des modifications réelles au fichier.
* **Joindre les fichiers** (icône de trombone) : chargez et joignez des fichiers à l’invite pour obtenir un contexte supplémentaire (par exemple, conceptions de référence, captures d’écran, spécifications).
* **Paramètres** (icône d’engrenage) : choisissez d’ignorer les questions de confirmation de l’IA.
* **Effacer la conversation** : permet de réinitialiser la conversation et d’effacer la fenêtre contextuelle de l’IA. Utilisez cette option pour démarrer une nouvelle tâche sans rapport avec la conversation précédente.

## Mode Contenu {#content-view}

La **vue Contenu** fournit des outils pour parcourir et prévisualiser le contenu. Par défaut, la vue est divisée en trois panneaux, de gauche à droite :

* Panneau d’invite pour interagir avec la console et le projet
* Explorateur de fichiers pour un aperçu de vos fichiers de contenu (basculement affichant ce panneau avec l’icône en forme de chevron)
* Panneau d’aperçu pour visualiser le contenu sélectionné dans l’explorateur de fichiers

![Vue Contenu](assets/content-imported.png)

Le panneau d’aperçu propose trois modes :

* **Aperçu** (document avec icône de loupe) pour visualiser le contenu HTML rendu
* **vue HTML** (icône de document) pour afficher respectivement la structure de contenu de création de documents sous-jacente
* **Mode de conception** (icône de pinceau) pour sélectionner des éléments de la page à des fins de contexte pour votre invite

Vous pouvez toujours cliquer sur l’icône **Actualiser l’aperçu** pour mettre à jour le panneau d’aperçu.

Le bouton **Charger le contenu** ouvre une fenêtre modale pour charger des fichiers vers AEM Document Authoring.

* Les champs **Organisation** et **Référentiel** sont préremplis si votre projet comporte un fichier `fstab.yaml`
* La sélection de fichiers fournit des chemins d’accès cibles modifiables
* Le chargement vers JCR (pour l’éditeur universel) n’est pas pris en charge

![Chargement du contenu](assets/upload-content.png)

## Affichage du code {#code-view}

L’**affichage du code** fournit des outils pour parcourir le code et gérer les modifications de code. La vue est divisée en trois panneaux, de gauche à droite :

* Panneau d’invite pour interagir avec la console et le projet
* Explorateur de fichiers pour un aperçu de vos fichiers de code ou de vos modifications en tant que diffs
* Panneau d&#39;aperçu pour visualiser un fichier de code ou une comparaison sélectionnée dans l&#39;explorateur de fichiers

![Affichage du code](assets/code-view.png)

Le panneau d’aperçu propose deux modes différents :

* **fichiers Workspace** pour parcourir les fichiers de code dans l&#39;espace de travail actuel
* **Modifications Git** pour afficher les différences entre les modifications de fichiers créées par votre travail sur le projet
   * Cliquez sur l’icône `+` pour préparer le fichier modifié
   * Cliquez sur l’icône de flèche pour ignorer le fichier modifié

L’icône **Informations** répertorie le compte et le projet GitHub actuellement connectés.

Le menu **Actions GitHub** (en haut à droite) fournit des opérations sur le référentiel.

* **Connexion/Reconnexion** : lance GitHub OAuth.
* **Changer de référentiel** : remplace l’espace de travail par un autre référentiel. Tout travail non engagé sera perdu.
* **Changer de branche** : change de branche dans le même référentiel
* **Sync** : extrait les dernières modifications de l’origine distante.
* **Push** : ouvre une boîte de dialogue modale pour pousser les modifications de l’espace de travail vers GitHub
* **Déconnexion** : se déconnecte de GitHub

Lors de l’envoi des modifications, vous devez d’abord disposer de modifications intermédiaires à inclure dans l’envoi. Lors du transfert, vous pouvez choisir de créer une requête de tirage ou de transférer directement vers la branche actuelle

![Intégrer les modifications](assets/push-changes.png)

## Mode Paramètres {#settings-view}

La vue Paramètres permet de gérer les paramètres de base de la console.

![Vue Paramètres](assets/settings-view.png)

* **Informations d’identification** vous permet de spécifier un jeton d’accès personnel pour Figma afin que la console puisse accéder aux blocs de conception de votre projet.
* **Réinitialiser l’espace de travail** rétablit l’état de départ de la console et toutes les modifications annulées ou annulées seront perdues.

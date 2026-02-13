---
title: Prise en main de l’agent de modernisation de l’expérience
description: Découvrez les premières étapes pour devenir rapidement productif avec l’agent de modernisation de l’expérience à l’aide de la console de modernisation de l’expérience.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 612c211e-43bf-47dc-89a8-9995a960e4d7
source-git-commit: 76c0f41acb5c2e4e0f0a292f8205b0b9de5cda81
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---


# Prise en main de l’agent de modernisation de l’expérience {#getting-started}

Découvrez les premières étapes pour devenir rapidement productif avec l’agent de modernisation de l’expérience à l’aide de la console de modernisation de l’expérience.

>[!NOTE]
>
>Si vous souhaitez utiliser la console de modernisation de l’expérience, vous pouvez demander l’accès pour garantir une expérience d’intégration fluide.

## Préparation d’un référentiel GitHub Edge Delivery {#prepare-repo}

1. Sélectionnez un référentiel [Edge Delivery Services](/help/edge/overview.md) à utiliser avec la console de modernisation de l’expérience.
   * Il peut s’agir d’un projet Edge Delivery Services existant ou vous pouvez en créer un en suivant le tutoriel de développement [developer tutorial](https://www.aem.live/developer/tutorial) à l’aide du [boilerplate repository.](https://github.com/adobe/aem-boilerplate)
1. Assurez-vous que le [AEM Code Connector](https://github.com/apps/aem-code-connector) est installé dans le référentiel.
   * Cela permet à la console d’inspecter votre code.
1. Assurez-vous que l’application [GitHub de synchronisation du code AEM](https://github.com/apps/aem-code-sync) est installée dans le référentiel.
   * Cela permet à Edge Delivery Services de synchroniser votre code.
   * Si votre référentiel est basé sur le tutoriel, cette étape est déjà terminée.

## Ouvrir la console de modernisation de l’expérience {#open-console}

1. Accéder à [`aemcoder.adobe.io`.](https://aemcoder.adobe.io)
1. Connectez-vous avec votre Adobe ID.

## Connexion de votre référentiel GitHub {#connect-repo}

La console vous invite à spécifier un référentiel lorsque vous vous connectez pour la première fois.

![Premier écran de connexion de la console](assets/first-sign-on.png)

1. Cliquez sur **Connecter le référentiel**.
1. L’application AEM Code Connector s’ouvre alors dans un nouvel onglet du navigateur. Cliquez sur **Autoriser AEM Code Connector**.
1. De retour dans la console, sélectionnez **Propriétaire**, **Référentiel** et **Sélection de branche**, puis cliquez sur **Extraire dans l’espace de travail**.
   ![Connexion à un projet GitHub](assets/connect-to-github-project.png)
1. Lorsque vous êtes invité à **Remplacer l’espace de travail existant**, cliquez sur **Remplacer l’espace de travail**.
   ![Remplacer l’espace de travail existant](assets/replace-existing-workspace.png)

Votre projet GitHub est maintenant connecté à la console et vous êtes sur l’écran d’accueil.

![Console d’accueil](assets/console-home.png)

## Démarrer l&#39;invite {#start-prompting}

Maintenant que votre console peut accéder à votre code, vous êtes prêt à démarrer l&#39;invite.

1. Pour commencer, vous pouvez importer le contenu d’un site :
   * « Migrer la page `https://wknd-trendsetters.site`. »
1. Le contenu du site est ainsi importé.
   * La console observe une séparation des préoccupations et gère le contenu et la présentation séparément.
   * L’importation initiale du contenu d’un site peut prendre plusieurs minutes.
   * La console vous présente des commentaires au fur et à mesure qu’elle commence son travail, y compris un aperçu de ses étapes planifiées.
     ![Import de contenu](assets/content-import.png)
1. Une fois le site importé, le panneau **Workspace** affiche les pages. Sélectionnez une page pour la prévisualiser dans le panneau de droite.
   ![ Contenu importé ](assets/content-imported.png)
1. Maintenant que vous disposez de contenu, vous pouvez demander à importer les styles à partir de la même source.
   * « Importez les styles généraux à partir de `https://wknd-trendsetters.site`. »
1. Comme pour l’importation de contenu initiale, l’importation peut prendre plusieurs minutes et la console fournit des commentaires pendant le traitement de votre demande et l’importation des styles. Une fois la tâche terminée, cliquez sur **Actualiser l’aperçu** dans le panneau de droite pour afficher le contenu stylisé.
   ![ Styles importés ](assets/styles-imported.png)

Le contenu et les styles sont maintenant importés dans la console.

## Chargement du contenu {#upload-content}

Pour charger le contenu vers [Création de documents](https://da.live) :

1. Assurez-vous que vous êtes dans la vue **Contenu**, puis cliquez sur le bouton **Charger le contenu** en haut à droite.
   * Par défaut, vous êtes dans la vue **Contenu** lorsque vous accédez à la console.
   * Votre affichage est indiqué par l’icône en surbrillance dans la barre latérale le long du côté gauche de la console.
1. La boîte de dialogue **Télécharger le contenu** s’ouvre avec l’organisation de destination et le référentiel préremplis à partir de votre `fstab.yaml`.
   * Si un `fstab.yaml` n’est pas présent dans votre référentiel connecté, vous devez saisir manuellement les valeurs **Organisation** et **Référentiel**..
   * Si vous avez utilisé la plaque chauffante, un `fstab.yaml` est fourni.
1. Sélectionnez les fichiers à charger, puis cliquez sur **Charger**.
   ![Boîte de dialogue Charger le contenu](assets/upload-content.png)
1. La console indique le processus de chargement en grisant le bouton **Charger**.
   ![Chargement](assets/uploading.png)
1. Une fois l’opération terminée, une notification s’affiche au bas de la console.
   ![Afficher dans AEM](assets/view-in-aem.png)

Pour accéder au contenu chargé dans la création de documents, vous pouvez cliquer sur **Afficher dans AEM** dans la notification une fois le chargement terminé ou accéder à `https://da.live/#/{organization}/{repository}`.

![Contenu dans la création de documents](assets/content-in-document-authoring.png)

Le contenu que vous avez importé se trouve maintenant dans l’instance de création de documents.

## Modifications du code push {#push-code-changes}

Une fois que vous êtes satisfait des modifications apportées à votre code, vous pouvez les pousser vers votre référentiel GitHub.

1. Passez en mode **Code** (icône `</>` dans la barre latérale gauche), puis dans l’onglet **Modifications Git** (icône de branche en haut à droite).
   ![Affichage du code](assets/code-view-git-changes.png)
1. Dans la liste des fichiers modifiés, si certains fichiers s’affichent comme non suivis, cliquez sur leur bouton `+` pour les préparer.
1. Cliquez sur le bouton **Actions GitHub** en haut à droite, puis sélectionnez **Push** dans la liste déroulante.
1. Dans la boîte de dialogue **Pousser les modifications**, choisissez de pousser les modifications vers une nouvelle RP (par défaut) ou la branche actuelle et cliquez sur **Confirmer** pour pousser.
   * En cas de doute, vous pouvez pousser vers la branche actuelle pour garder les choses simples.
1. Une fois l’opération terminée, une notification s’affiche au bas de la console.
   ![Afficher PR](assets/view-pr.png)

Si vous souhaitez accéder directement aux modifications transmises dans GitHub, cliquez sur **Afficher PR** dans la notification une fois la transmission terminée.

![Code dans GitHub](assets/code-in-github.png)

Votre code se trouve désormais dans GitHub.

## Aperçu du site {#preview-site}

Pour afficher les modifications dans l’environnement de prévisualisation :

1. Revenez à la création de documents.
   * Il se peut qu’il soit toujours ouvert dans un onglet du navigateur que vous avez ouvert après avoir cliqué sur **Afficher dans AEM** après avoir chargé le contenu.
   * Ou accédez à `https://da.live/#/{organization}/{repository}`
1. Ouvrez l’une des pages que vous avez précédemment chargées dans AEM.
1. Cliquez sur l’icône du plan de papier (en haut à droite) et sélectionnez **Aperçu**.
   ![Publier pour prévisualisation](assets/publish-to-preview.png)

Félicitations. Le contenu et les styles migrés sont désormais en ligne dans l’environnement d’aperçu AEM.

![Contenu de prévisualisation publié](assets/published-preview.png)

Si vous avez poussé votre code vers une branche autre que `main`, l’aperçu ouvert à partir de l’instance de création de document n’affiche pas les styles. Remplacez par la branche en mettant à jour l’URL de l’aperçu pour afficher vos styles.

## Ressources supplémentaires {#additional-resources}

Les documents suivants peuvent s’avérer utiles lorsque vous continuez à explorer l’agent de modernisation d’expérience et sa console.

* [Console de modernisation de l’expérience](/help/ai-in-aem/agents/modernization/console.md) - Détails sur la console, ses vues, options et fonctionnalités
* [Tutoriel de développement Edge Delivery Services ](https://www.aem.live/developer/tutorial) - Utile si vous êtes un débutant dans les projets AEM et Edge Delivery Services
* [Création de documents](https://da.live) - Utile si vous êtes un débutant dans la création de documents pour la gestion de contenu

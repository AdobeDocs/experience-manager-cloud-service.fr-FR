---
title: Configuration des règles de traduction
description: Découvrez comment définir des règles de traduction pour identifier le contenu à traduire.
index: true
hide: false
hidefromtoc: false
source-git-commit: 08127d72c84d6f47f5058ef631dc3128114f1953
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 4%

---


# Configuration des règles de traduction {#configure-translation-rules}

Découvrez comment définir des règles de traduction pour identifier le contenu à traduire.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours de traduction AEM Sites, [Configurer le connecteur de traduction](configure-connector.md) vous avez appris à installer et configurer votre connecteur de traduction et vous devez maintenant :

* Découvrez les paramètres importants de la structure d’intégration de traduction dans AEM.
* Vous pouvez configurer votre propre connexion à votre service de traduction.

Maintenant que votre connecteur est configuré, cet article vous guide tout au long de l’étape suivante pour identifier le contenu à traduire.

## Objectif {#objective}

Ce document vous aide à comprendre comment utiliser AEM règles de traduction pour identifier votre contenu de traduction. Après avoir lu ce document, vous devriez :

* Comprendre ce que font les règles de traduction.
* Vous pouvez définir vos propres règles de traduction.

## Règles de traduction {#translation-rules}

Les pages AEM Sites peuvent contenir de nombreuses informations. Selon les besoins de votre projet, il est probable que toutes les informations d’une page ne doivent pas être traduites.

Les règles de traduction identifient le contenu qui est inclus dans les projets de traduction ou qui en est exclu. Lorsque le contenu est traduit, AEM extrait ou récupère le contenu en fonction de ces règles. Ainsi, seul le contenu à traduire est envoyé au service de traduction.

Les règles de traduction incluent les informations suivantes :

* Chemin d’accès au contenu auquel la règle s’applique
   * La règle s’applique également aux descendants du contenu.
* Les noms des propriétés qui contiennent le contenu à traduire
   * Cette propriété peut être spécifique à un type de ressource en particulier ou à tous les types de ressource

AEM crée automatiquement des règles de traduction pour les pages de sites. Toutefois, comme les exigences de chaque projet sont différentes, il est important de savoir comment réviser et adapter les règles selon les besoins de votre projet.

## Création de règles de traduction {#creating-rules}

Plusieurs règles peuvent être créées pour prendre en charge des exigences de traduction complexes. Par exemple, un projet sur lequel vous travaillez nécessite la traduction de toutes les informations de la page, mais sur une autre page, seules les descriptions doivent être traduites tandis que les titres ne sont pas traduits.

Les règles de traduction sont conçues pour gérer de tels scénarios. Cependant, dans cet exemple, nous illustrons comment créer des règles en se concentrant sur une configuration simple et unique.

Une console **Configuration de traduction** est disponible pour la configuration des règles de traduction.

Pour y accéder :

1. Accédez à **Outils** -> **Général**.
1. Appuyez ou cliquez sur **Configuration de traduction**.

AEM crée automatiquement des règles de traduction pour tout le contenu. Pour afficher ces règles :

1. Sélectionnez le contexte `/content` , puis l’option **Modifier** dans la barre d’outils.
1. L’éditeur de règles de traduction s’ouvre avec les règles qui AEM automatiquement créées pour le chemin `/content`.

   ![Éditeur de règles de traduction](assets/translation-rules-editor.png)

1. Les propriétés de page qui seront traduites se trouvent sous la section **Général** de la liste. Vous pouvez ajouter ou mettre à jour des noms de propriété existants que vous souhaitez inclure explicitement dans la traduction.
   1. Saisissez le nom de la propriété dans le champ **Nouvelle propriété** .
   1. Les options **Traduire** et **Hériter** sont cochées automatiquement.
   1. Appuyez ou cliquez sur **Ajouter**.
   1. Répétez ces étapes pour tous les champs que vous devez traduire.
   1. Cliquez ou appuyez sur **Enregistrer**.

Vous avez maintenant configuré vos règles de traduction.

>[!NOTE]
>
>AEM crée automatiquement des règles de traduction. Pour une configuration de traduction simple ou pour tester un workflow de traduction, il n’est pas nécessaire de créer de nouvelles règles, ni même de modifier les règles existantes créées automatiquement. Les détails de ces étapes sont présentés pour expliquer le fonctionnement des règles et donner un contexte à la manière dont AEM traite les traductions.

>[!TIP]
>
>Il est également possible de créer des règles uniquement pour votre chemin ou projet spécifique en appuyant ou en cliquant sur le bouton **Ajouter le contexte** dans la console Configuration de traduction. Cela va au-delà de la portée de ce parcours.

## Utilisation avancée {#advanced-usage}

Plusieurs propriétés supplémentaires peuvent être configurées dans le cadre de vos règles de traduction. En outre, vous pouvez spécifier vos règles manuellement au format XML, ce qui vous permet d’obtenir plus de précision et de flexibilité.

Ces fonctionnalités ne sont généralement pas nécessaires pour commencer à localiser votre contenu, mais vous pouvez en apprendre davantage à ce sujet dans la section [Ressources supplémentaires](#additional-resources) si vous le souhaitez.

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de traduction AEM Sites, vous devez :

* Comprendre ce que font les règles de traduction.
* Vous pouvez définir vos propres règles de traduction.

Tirez parti de ces connaissances et poursuivez votre parcours de traduction AEM Sites en consultant le document [Traduire le contenu](translate-content.md) dans lequel vous découvrirez comment votre connecteur et vos règles fonctionnent ensemble pour traduire le contenu.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de traduction en consultant le document [Traduire le contenu,](translate-content.md) les ressources suivantes sont facultatives et supplémentaires, qui approfondissent certains concepts mentionnés dans ce document, mais ne sont pas requises pour continuer le parcours.

* [Identification du contenu à traduire](/help/sites-cloud/administering/translation/rules.md)  : découvrez comment les règles de traduction identifient le contenu à traduire.

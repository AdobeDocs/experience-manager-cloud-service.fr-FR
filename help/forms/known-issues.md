---
title: Quels sont les problèmes connus et les limites de l’environnement as a Cloud Service d’AEM Forms ?
description: Problèmes connus et limites de l’environnement  [!DNL AEM Forms] as a Cloud Service.
contentOwner: khsingh
role: Admin, Developer, User
feature: Adaptive Forms
topic: Administration
exl-id: 871f294d-f251-4966-a021-39df65b613f0
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 93%

---

# Problèmes connus et limites {#known-issues-and-limitations}

Avant de commencer à utiliser [!DNL AEM Forms] as a Cloud Service, passez en revue les problèmes et limites connus suivants :

## Problèmes connus {#known-issues}

* Vous ne devez pas ajouter ni exécuter un test qui envoie un formulaire adaptatif d’une instance de publication à un processus AEM s’exécutant sur une instance d’auteur jusqu’à nouvel ordre.

* Lorsque vous importez un formulaire adaptatif qui utilise un modèle contenant le bouton **[!UICONTROL Enregistrer]**, le bouton **[!UICONTROL Enregistrer]** continue à apparaître dans le formulaire adaptatif même après sa suppression du modèle correspondant. Supprimez le bouton **[!UICONTROL Enregistrer]** de votre formulaire adaptatif avant de le publier. Consultez les notes de mise à jour pour connaître la disponibilité de la fonctionnalité Portail Formulaires et Enregistrer en tant que brouillon pour restaurer le bouton et l’utiliser.

* L’étape **[!UICONTROL Définir la variable]** des processus AEM ne prend pas en charge les variables de type liste de tableau. Vous pouvez utiliser l’étape de processus pour définir des variables de type liste de tableau.

* Lorsque vous envoyez un formulaire adaptatif contenant un champ de chargement HTML standard à partir d’un appareil iOS d’Apple, le contenu du fichier n’est pas envoyé et un fichier de 0 octet est reçu à l’autre bout. Le problème se produit par intermittence et uniquement lors d’envois synchrones. Il s’agit d’un [problème connu](https://feedbackassistant.apple.com/feedback/9117687) dans Apple iOS.

* Lorsque vous envoyez un formulaire contenant un champ de chargement HTML standard d’un appareil iOS d’Apple, le contenu du fichier n’est parfois pas envoyé et un fichier de 0 octet est reçu à l’autre bout. Il s’agit d’un problème connu dans Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

* AEM Forms as a Cloud Service ne génère pas de miniatures pour les fichiers de schéma XDP et JSON. Le service affiche les icônes par défaut à la place des miniatures.

  ![Problème connu de la miniature Forms](/help/forms/assets/forms-tumbnail-known-issue.png)

* Lorsque vous utilisez un schéma avec des éléments répétables pour créer un formulaire adaptatif basé sur des composants principaux, l’option de glisser-déposer des éléments répétables de l’arborescence du modèle de données dans l’éditeur de formulaires adaptatif ne fonctionne pas.

## Limites {#limitations}

* La prise en charge des formulaires adaptatifs basés sur XFA n’est pas disponible sans configuration supplémentaire. Si vous envisagez d’utiliser des formulaires adaptatifs basés sur XFA, contactez l’assistance Adobe pour expliquer votre cas d’utilisation et vos exigences spécifiques.


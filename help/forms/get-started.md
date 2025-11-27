---
title: Prise en main des formulaires HTML5
description: Pour commencer, déployez le pack complémentaire AEM Forms et importez les formulaires HTML5 existants dans AEM.
content-type: reference
topic-tags: hTML5_forms
discoiquuid: f276d150-8936-4bfb-8475-7ca36815b233
feature: HTML5 Forms,Mobile Forms
exl-id: a3245f05-6ea3-4f90-8981-bfa89d2e7335
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 56%

---

# Prise en main des formulaires HTML5 {#getting-started-with-html-forms}

<span class="preview"> La fonctionnalité Forms d’HTML5 est proposée dans le cadre du programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à l’adresse aem-forms-ea@adobe.com à partir de votre ID d’e-mail officiel (professionnel).
</span>

Les formulaires HTML5 proposent de nombreuses fonctionnalités compatibles avec les périphériques mobiles. Cela vous permet d’étendre vos solutions et workflows actuels aux tablettes ou smartphones disposant de navigateurs HTML5. Exemple de fonctionnalités disponibles :

* **Rendu au format HTML5 des modèles de formulaires XFA :** outre les formulaires PDF standard, vous pouvez désormais générer vos formulaires XFA existants au format HTML5. Cette fonctionnalité vous aide à développer votre plateforme cliente sur les appareils mobiles (iPad d’Apple, tablettes Android, smartphones, etc.) qui prennent en charge le format HTML5 et ne prennent pas en charge les formulaires XFA sous Adobe Reader. Pour plus d’informations sur la fonctionnalité de rendu au format HTML5, voir [Introduction aux formulaires HTML5](/help/forms/introductionhtml5.md). 

* **Gestion des formulaires :** en outre, AEM comprend de nouvelles fonctionnalités pour simplifier le processus d’organisation et de gestion des formulaires. Vous pouvez activer, désactiver, publier et prévisualiser des formulaires.<!--For more information, see [Introduction to managing forms](/help/forms/using/introduction-managing-forms.md).-->

## Configuration de votre environnement pour HTML Forms {#installing-html-forms}

Pour activer les envois de formulaire et le rendu correct du Forms HTML5, procédez comme suit :

* **Ajouter des filtres du Dispatcher :** mettez à jour votre fichier `src/conf.dispatcher.d/filters/filters.any` pour autoriser les requêtes nécessaires pour HTML5 Forms. Ajoutez les règles de filtrage suivantes :

  ```
  /0103 { /type "allow" /method '(HEAD|POST)' /url "/content/xfaforms/profiles/default.submit.html" }  # allow POSTs to form selectors under content
  /0104 { /type "allow" /method '(GET|HEAD|POST)' /url "/*.xdp.html" }
  ```

* **Ajouter un package pour l’envoi :** dans votre projet, ajoutez un package dans le dossier `src/main/content/jcr_root/content` pour prendre en charge la fonctionnalité d’envoi de formulaire.

* **Importer HTML5 Forms :** permet d’importer vos formulaires de votre système de fichiers local vers AEM Forms.

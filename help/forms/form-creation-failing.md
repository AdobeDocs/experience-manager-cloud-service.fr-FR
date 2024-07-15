---
title: Comment résoudre les problèmes de création de formulaires ?
description: Résolution des problèmes liés à la création de formulaires dans l’environnement AEM Forms as a Cloud Service.
feature: Adaptive Forms
role: User
exl-id: 169ea727-0941-4a1d-bc33-d9fe208b27ab
source-git-commit: 0b693cb51a96011235fa87a5899426c6b0c2509a
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 5%

---

# Problème lors de la publication de formulaires{#form-creation-fails}

Après la mise à jour des utilisateurs vers AEM Forms as a Cloud Service `2024.5.16461` :

**Certains utilisateurs** peuvent rencontrer des problèmes lors de la création de formulaires. Le problème est tel que, lorsqu’un utilisateur crée un formulaire, le message d’erreur suivant s’affiche dans la boîte de dialogue de création :

`A server error occurred. Try again after sometime.`

## Cause {#cause-form-creation-fails}

Le problème se produit car l’auteur publie le formulaire sans **publier au préalable le modèle** utilisé dans celui-ci. Cela entraîne l’ajout de `jcr:uuid` et d’autres propriétés protégées et générées par le système au noeud `<template-path>/initial/jcr:content`, ce qui entraîne des échecs lors de la création ultérieure du formulaire.

## Solution {#resolution-form-creation-fails}

Pour résoudre le problème, procédez comme suit :

1. Assurez-vous que le modèle que vous utilisez dans votre formulaire ne comporte pas les propriétés protégées `jcr:uuid` et d’autres propriétés générées par le système sur le chemin `<template-path>/initial/jcr:content node`.
1. Publish le modèle de manière explicite à l’aide de la console de modèles.
1. Maintenant, lorsque votre modèle est publié, essayez de créer de nouveaux formulaires à l’aide de ce modèle.
1. Si le modèle que vous avez utilisé est mis à jour dans les prochaines versions, Publish à nouveau le modèle (comme indiqué à l’étape 2) afin d’éviter des problèmes d’échec de création de formulaire.


<!--

# Issue {#form-creation-fails}

After updating to AEM Forms as a Cloud Service version `2024.5.16461.20240524T172309Z`, When a user publishes a form using an unpublished template, it fails to create a form and shows an error:

`Property is protected: jcr:uuid = 09e0d6be-f619-4405-b021-27eb1c5326d3`

## Solution {#troubleshoot-form-creation-fails}

To resolve the issue, perform the following workaround steps:

1. Publish the template explicitly using the template console.
    
    >[!NOTE]
    > Prior to this step ensure that the (unpublished) template does not have `jcr:uuid` and other system generated properties under the initial content's `jcr:content node`. To sort out it, first, sanitize the template to publish it explicitly.

    >[!NOTE]
    > This action doesn't replicate the initial content node.
1. Now, when your template is published, try creating new forms using the template.
1. If the template is changed in the future, publish it again as mentioned in the step 1.

-->

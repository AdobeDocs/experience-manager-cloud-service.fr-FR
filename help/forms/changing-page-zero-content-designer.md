---
title: Comment modifier le contenu de la page zéro dans Designer ?
description: Modifiez le message affiché sur la page zéro d’un PDF XFA pour les visionneuses non Adobe PDF.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms
role: User
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 80%

---


# Modifier le contenu de la page zéro dans Designer {#changing-page-zero-content-in-designer}

Le contenu de la page zéro s’affiche par défaut lorsqu’un programme de visualisation PDF autre que celui d’Adobe, tel que la visionneuse de fichiers PDF par défaut dans [!DNL Chrome] ou [!DNL Firefox], ne peut pas lire le contenu d’un formulaire PDF/XFA. Le message par défaut de la page zéro est affiché ci-dessous.

![defaultpage0message](assets/defaultpage0message.png)

La version [!DNL AEM Forms] de Designer vous permet de modifier le message affiché sur la page zéro. Pour modifier le message de la page zéro, procédez comme suit :

1. Assurez-vous que la version [!DNL AEM Forms] de Designer est installée. Vous pouvez vérifier la version dans l’écran A propos de Designer.

1. Ouvrez le formulaire dont vous souhaitez modifier le contenu de la page zéro.

1. Cliquez sur **[!UICONTROL Fichier]** > **[!UICONTROL Propriétés du formulaire]**.

1. Dans la boîte de dialogue [!UICONTROL Propriétés du formulaire], cliquez sur le signe ![plus](assets/plus.png) (icône plus) pour ajouter une propriété personnalisée.

1. Spécifiez **_pagezerocontent** en tant que nom de propriété.
1. Ajoutez le nouveau message de la page zéro, au format de texte enrichi, en tant que valeur. Par exemple :


   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. Enregistrez le formulaire au format PDF.

1. Affichez le formulaire PDF dans le navigateur pour vous assurer que le message a été mis à jour. La valeur d’exemple évoquée ci-dessus apparaît comme suit :

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>La propriété personnalisée que vous avez créée peut ne pas s’afficher correctement dans la boîte de dialogue Propriétés du formulaire lors de la réouverture du formulaire. Cependant, elle fonctionne correctement et le formulaire affiche le message mis à jour de la page zéro.

>[!MORELIKETHIS]
>
>* [ Télécharger et installer Forms Designer pour créer des modèles de document d’enregistrement](/help/forms/installing-configuring-designer.md)
>* [Utilisez Forms Designer pour créer des modèles de document d’enregistrement et des fragments de formulaire ?](/help/forms/use-forms-designer.md)

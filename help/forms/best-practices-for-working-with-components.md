---
title: 'Bonnes pratiques pour l’utilisation des composants '
seo-title: Best practices for working with components
description: Bonnes pratiques et points clés à prendre en compte lors de l’utilisation de composants de formulaire adaptatifs
seo-description: Some best practices and key points to remember when working with Adaptive Form components
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 100%

---


# Bonnes pratiques pour l’utilisation des composants {#best-practices-for-working-with-components}

Les bonnes pratiques et les points clés suivants sont à prendre en compte lors de l’utilisation de composants de formulaire adaptatifs :

* Chaque composant est associé à des propriétés qui contrôlent son apparence et ses fonctionnalités. Pour configurer les propriétés d’un composant, cliquez sur celui-ci et sélectionnez ![propriétés](assets/Smock_Wrench_18_N.svg) pour ouvrir les propriétés du composant dans l’explorateur de propriétés.
* Un composant est identifié par son nom d’élément. Lorsque vous appuyez sur ![propriétés](assets/Smock_Wrench_18_N.svg), vous pouvez changer le nom du composant en modifiant la valeur du champ **[!UICONTROL Nom de l’élément]** dans l’explorateur de propriétés. Vous pouvez saisir uniquement des lettres, des chiffres, des traits d’union (-) et des traits de soulignement (_) dans le champ Nom de l’élément. D’autres caractères spéciaux ne sont pas autorisés et le nom de l’élément doit commencer par une lettre.

* Vous pouvez modifier la propriété de titre d’un composant de formulaire adaptatif inséré dans l’éditeur de formulaire sans ouvrir le navigateur de propriétés tant que le titre est visible sur le formulaire. Pour ce faire :

   1. Appuyez pour sélectionner un composant qui a une propriété **[!UICONTROL Titre]** et dont la propriété **[!UICONTROL Masquer le titre]** est désactivée.

   1. Appuyez sur ![Modifier l’icône](assets/Smock_Edit_18_N.svg) pour rendre le titre modifiable.

   1. Modifiez le titre et appuyez sur la touche Retour ou appuyez n’importe où en dehors du composant pour enregistrer les modifications. Appuyez sur la touche Échap pour annuler les modifications.

* Certains composants de formulaire adaptatifs, tels que Courrier électronique et Téléphone, incluent des modèles de validation prêts à l’emploi. Toutefois, vous pouvez spécifier une validation personnalisée en mettant à jour le champ **[!UICONTROL Modèle de validation]** sous l’accordéon Modèles dans les propriétés du composant. Voir les descriptions des composants dans le tableau ci-dessus pour plus d’informations sur les validations par défaut.

* Les champs de formulaires adaptatifs, tels que Zone numérique et Adresse électronique, peuvent être configurés de façon à inclure des types spécifiques d’entrée HTML5. Lorsque ces champs sont actifs sur les appareils mobiles et les tablettes, le clavier affiche un alphabet, des chiffres et des caractères spécifiques qui sont généralement utilisés pour saisir des informations dans les champs. Cela permet aux utilisateurs de saisir les informations rapidement sans avoir à basculer entre les jeux de caractères sur le clavier. Pour activer une entrée spécifique pour un composant, cochez la case **[!UICONTROL Utiliser un numéro de type HTML]** dans ses propriétés de composant.

* Vous pouvez activer un composant de zone de texte afin de permettre la prise en charge du texte brut. Pour activer le texte enrichi pour une zone de texte, activez la case à cocher **[!UICONTROL Autoriser le texte enrichi]** dans les propriétés du composant.

* Vous pouvez activer les composants Zone de texte, Adresse électronique et Téléphone pour remplir automatiquement les champs tels que le nom, l’adresse, la carte de crédit, le téléphone et l’adresse électronique à partir des informations stockées dans les paramètres de remplissage automatique du navigateur. Pour activer cette fonctionnalité, sélectionnez **[!UICONTROL Activer le remplissage automatique]** dans les propriétés du composant et sélectionnez un **[!UICONTROL attribut de remplissage automatique]**. Lorsqu’un utilisateur remplit un formulaire adaptatif, les valeurs sont suggérées à partir du profil de remplissage automatique dans le navigateur ou en fonction des valeurs précédemment renseignées par l’utilisateur. Notez que le remplissage automatique fonctionne si les paramètres de remplissage automatique dans le navigateur de l’utilisateur sont activés.

* Spécifiez des valeurs pour les éléments Bouton radio et Case à cocher au format `{value}={text}` dans les propriétés du composant.
* Le composant de pièce jointe, par défaut, permet à un utilisateur de joindre un seul fichier. Toutefois, vous pouvez configurer les propriétés du composant pour prendre en charge plusieurs pièces jointes. En outre, si un utilisateur joint plusieurs fichiers avec le même nom de fichier, les pièces jointes peuvent provoquer des problèmes. Par conséquent, il est recommandé d’associer un identificateur unique pour chaque pièce jointe envoyée à l’envoi du formulaire. Pour ce faire :

   1. Sur votre serveur [!DNL AEM Forms], accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console web]**.
   1. Recherchez **[!UICONTROL Service de configuration de formulaires adaptatifs]** et appuyez dessus.
   1. Dans la boîte de dialogue Service de configuration de formulaires adaptatifs, activez l’option **[!UICONTROL Rendre les noms de fichier uniques]**. Par défaut, elle est désactivée.

* Pour permettre aux utilisateurs de joindre un fichier PDF à l’aide du navigateur Safari, veillez à ajouter **application/pdf** à la propriété Types de fichiers pris en charge du composant Pièce jointe. Les formulaires adaptatifs créés avec la version précédente d’[!DNL AEM Forms] peuvent contenir **.pdf** au lieu de **application/pdf** dans la propriété Types de fichiers pris en charge.

>[!NOTE]
>
>Les composants de formulaire adaptatif ne prennent pas en charge les langues de droite à gauche (RTL) comme l’hébreu.
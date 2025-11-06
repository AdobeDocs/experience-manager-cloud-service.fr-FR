---
title: Comment appliquer des signatures électroniques à un formulaire à l’aide de signatures tactiles ?
description: Découvrez comment appliquer des signatures électroniques à un formulaire à l’aide de signatures tactiles.
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
role: User, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 64%

---

# Signer électroniquement un formulaire à l’aide de signatures tactiles{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/signing-forms-using-scribble.html?lang=fr) |
| AEM as a Cloud Service | Cet article |


Vous pouvez utiliser le composant **Signature tactile** pour tracer la signature (saisie tactile) sur un formulaire adaptatif. <!-- The Signature step component displays a PDF version of the Adaptive Form. You require a Document of Record option enabled or form template based Adaptive Forms to use the Signature step component. -->

![Boîte de dialogue de signature tactile](assets/scribble-signature.png)

## Diverses options disponibles dans la fenêtre de signature.

* **A :** cliquez sur l’icône **Pinceau** pour tracer votre signature sur la zone de travail.
* **B :** cliquez sur l’icône **Effacer** pour effacer la signature sur la zone de travail.
* **C :** cliquez sur l’icône **Géolocalisation** pour ajouter une géolocalisation avec la signature.
* **D :** cliquez sur l’icône **Clavier** pour saisir votre nom sur la zone de travail.

Une fois que vous avez sélectionné l’icône Terminé ![aem_forms_save](assets/aem_forms_save.png) dans la fenêtre de signature tactile, vous ne pouvez plus modifier la signature. Si vous souhaitez modifier la signature, vous devez ignorer la signature actuelle et la signer à nouveau à l’aide de l’option Pinceau/Clavier ci-dessus.

Vous pouvez sélectionner l’icône **Configurer** ![configurer](assets/configure.png) pour définir les proportions de la zone de travail de signature tactile.

* Lorsque le rapport d’aspect de la zone de travail de signature tactile est inférieur à 1, les informations de géolocalisation sont ajoutées au bas de la zone de travail de signature tactile.
* Lorsque le rapport d’aspect de la zone de travail de signature tactile est supérieur à 1, les informations de géolocalisation sont ajoutées au côté droit de la zone de travail de signature tactile.


![Bas de la signature tactile](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>Les signatures sont toujours enregistrées au format PNG.

## Configuration d’un formulaire adaptatif pour utiliser la signature tactile {#configure-an-adaptive-form-to-use-scribble-signature}

1. Ouvrez un formulaire adaptatif en mode d’édition.
1. Faites glisser le composant **Signature tactile** depuis le navigateur de composant et déposez-le dans le formulaire adaptatif.
1. Sélectionnez l’icône **Configurer** ![configurer](assets/configure.png). Vous ouvrez ainsi le navigateur de propriétés qui affiche les propriétés du composant Signature tactile. [Configurez les propriétés de la signature tactile](#properties-of-scribble-signature-component) comme décrit dans la section suivante.

   ![Signature tactile](/help/forms/assets/scribblesig.png)

1. Sélectionnez l’icône Terminé ![aem_forms_save](assets/aem_forms_save.png) pour enregistrer les modifications. La signature a été configurée avec succès.

## Configurer les propriétés du composant Signature tactile

Vous pouvez facilement personnaliser votre composant Signature tactile pour les visiteurs et les visiteuses en utilisant la boîte de dialogue de configuration.

### Onglet De base

![Onglet De base](/help/forms/assets/scribblesig-basic.png)

* **Nom** - Vous pouvez identifier facilement un composant de formulaire en lui attribuant un nom unique dans le formulaire et dans l’éditeur de règles, mais le nom ne doit pas contenir d’espaces ni de caractères spéciaux.

* **Titre** - Avec son titre, vous pouvez facilement identifier un composant dans un formulaire. Par défaut, le titre s’affiche au-dessus du composant. Si vous n’ajoutez pas de titre, le nom du composant s’affiche à la place du texte du titre.

* **Autoriser le texte enrichi pour le titre** - Cette fonctionnalité permet aux personnes de mettre en forme les titres en texte brut en y incorporant des fonctionnalités telles que le texte en gras, en italique et souligné, diverses polices, tailles de police et couleurs, et d’autres options pour améliorer la présentation visuelle et la personnalisation. Elle offre une plus grande flexibilité et un contrôle créatif pour faire ressortir les titres dans les documents, sites web ou applications.\
  Lorsque vous cochez la case **Autoriser le texte enrichi pour le titre**, les options de formatage deviennent visibles pour appliquer un style au titre du composant. Pour accéder à toutes les options de formatage disponibles, vous pouvez cliquer sur l’onglet ![Fullscreen icon](/help/forms/assets/fullscreen-icon.png).

  ![Prise en charge de texte enrichi](/help/forms/assets/richtext-support-title.png)

* **Masquer le titre** - Sélectionnez cette option pour masquer le titre du composant.
* **Champ obligatoire** - Sélectionnez cette option pour rendre le champ obligatoire.
* **Message de champ obligatoire** - Le **Message de champ obligatoire** est un message personnalisable qui s’affiche pour les utilisateurs et utilisatrices qui tentent d’envoyer un formulaire sans remplir de champ obligatoire.
* **Référence de liaison du modèle de données** - Une référence de liaison est une référence à un élément de données stocké dans une source de données externe et utilisée dans un formulaire. La référence de liaison vous permet de lier dynamiquement les données aux champs du formulaire, de sorte que le formulaire puisse afficher les données les plus récentes de la source de données. Par exemple, une référence de liaison peut être utilisée pour afficher le nom et l’adresse d’un client ou d’une cliente dans un formulaire, en fonction de l’identifiant du client ou de la cliente saisi dans le formulaire. La référence de liaison peut également être utilisée pour mettre à jour la source de données avec les données saisies dans le formulaire. Ainsi, AEM Forms vous permet de créer des formulaires qui interagissent avec des sources de données externes, offrant ainsi une expérience utilisateur fluide pour la collecte et la gestion des données.
* **Masquer l’objet** - Sélectionnez cette option pour masquer le composant du formulaire. Le composant reste accessible à d’autres fins, par exemple pour les calculs dans l’éditeur de règles. Cela s’avère utile lorsque vous devez stocker des informations qui n’ont pas besoin d’être affichées ou directement modifiées par les utilisateurs ou les utilisatrices.
* **Désactiver l’objet** - Sélectionnez l’option pour désactiver le composant. Le composant désactivé n’est pas actif ni modifiable par l’utilisateur final ou l’utilisatrice finale. L’utilisateur ou l’utilisatrice peut voir la valeur du champ mais ne peut pas la modifier. Le composant reste accessible à d’autres fins, par exemple pour les calculs dans l’éditeur de règles.
* **Format** - Le format dans un composant Signature tactile définit la relation proportionnelle entre sa largeur et sa hauteur.
* **Disposition du champ** - L’option **Disposition du champ** détermine la manière dont les éléments de formulaire, y compris les libellés (légendes) et les messages d’erreur, sont positionnés par rapport au composant. Le **Légende et Erreur en haut du widget** place la légende (libellé) du champ et les messages d’erreur au-dessus du composant. **Hériter de la configuration de formulaire adaptatif** utilise les paramètres de disposition de champ par défaut spécifiés dans la configuration de formulaire adaptatif.
* **Classe CSS** - La classe **CSS** vous permet d’appliquer des styles personnalisés à un composant en attribuant une ou plusieurs classes CSS définies dans votre feuille de style. Il permet une personnalisation cohérente du style et de la disposition dans votre formulaire adaptatif.

### Contenu de l&#39;aide

![Onglet Contenu d’aide](/help/forms/assets/scribblesig-help.png)

* **Description courte** : Une description courte est une brève explication textuelle qui fournit des informations supplémentaires ou une clarification sur l’objectif d’un champ de formulaire spécifique. Il permet à l’utilisateur ou l’utilisatrice de comprendre le type de données à saisir dans le champ et peut fournir des conseils ou des exemples pour s’assurer que les informations saisies sont valides et répondent aux critères souhaités. Par défaut, les descriptions courtes restent masquées. Activez l’option **Toujours afficher une description courte** pour l’afficher sous le composant.

* **Toujours afficher une description courte** - Activez cette option pour afficher la description courte sous le composant.

* **Description longue** - Elle fait référence à des informations ou des conseils supplémentaires fournis à l’utilisateur ou à l’utilisatrice pour l’aider à remplir correctement un champ de formulaire. Il s’affiche lorsque l’utilisateur ou l’utilisatrice clique sur l’icône d’aide (i) placée à côté du composant. Il fournit des informations plus détaillées que le texte du libellé ou de l’espace réservé d’un champ de formulaire et est conçu pour aider l’utilisateur ou l’utilisatrice à comprendre les exigences ou les contraintes du champ. Il peut également proposer des suggestions ou des exemples pour faciliter le remplissage du formulaire et le rendre plus précis.

### Onglet Accessibilité {#accessibility}

![Onglet Accessibilité](/help/forms/assets/scribblesig-acc.png)

Dans l’onglet **Accessibilité**, les valeurs peuvent être définies pour les libellés d’[accessibilité ARIA](https://www.w3.org/WAI/standards-guidelines/aria/) du composant. Plusieurs options sont disponibles pour l’utilisation du texte pour le lecteur d’écran :

* **Précédence du Reader d’écran** - La priorité du Reader d’écran fait référence à un texte supplémentaire spécialement conçu pour être lu par les technologies d’assistance, comme les lecteurs d’écran, utilisées par les personnes malvoyantes. Ce texte fournit une description audio de l’objectif du champ de formulaire et peut inclure des informations sur le titre, la description, le nom du champ et tout message pertinent (texte personnalisé). Le texte du lecteur d’écran permet de s’assurer que le formulaire est accessible à tous les utilisateurs et utilisatrices, y compris celles et ceux ayant une déficience visuelle, et leur permet de bien comprendre le champ du formulaire et ses exigences.

   * **Texte personnalisé** : sélectionnez cette option pour utiliser le texte personnalisé pour les libellés d’accessibilité ARIA. Cette option affiche la boîte de dialogue Texte personnalisé. Vous pouvez ajouter des informations pertinentes dans la boîte de dialogue Texte personnalisé.
   * **Description courte** : sélectionnez cette option pour utiliser la description des libellés d’accessibilité ARIA.
   * **Titre** : sélectionnez cette option pour utiliser le titre pour les libellés d’accessibilité ARIA.
   * **Nom** : sélectionnez cette option pour utiliser le nom pour les libellés d’accessibilité ARIA.
   * **Aucun** : sélectionnez cette option si vous ne souhaitez pas ajouter de texte supplémentaire pour les libellés d’accessibilité ARIA.

<!--

 * **Element Name**: Specify name of the component.

    * **Title:** Specify unique title of the component.
    * **Template message:** Specify the message to be displayed while the signature PDF is being loaded. Adobe Sign services take some time to prepare and load signature PDF.
    * **Signing Service:** Select the **Scribble Signature** option.

    * **CSS Class**: Specify CSS class of the client library, if any. Adobe recommends using [themes](themes.md) and [in-line styles](inline-style-adaptive-forms.md) instead of CSS Class.
## Sign an Adaptive Form using Scribble Signature {#sign-an-adaptive-form-using-scribble-signature}

1. After you fill an Adaptive Form and reach the Signature Step page, the signature screen is displayed.

   ![Signature screen for EchoSign page](assets/esignscribblesign.jpg)

1. Click **[!UICONTROL Sign]**. The scribble sign dialog appears. Sign the form and click the Done ![aem_forms_save](assets/aem_forms_save.png) icon to save the signature.

   ![Scribble sign dialog](assets/scribblewidget.png)

1. Click complete to finish the signing process.

   ![Complete the signing process](assets/scribblecomplete.jpg)

The signatures are added to the form and the form control moves to the next panel. -->

## Voir également {#see-also}

{{see-also}}
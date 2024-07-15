---
title: Composants de formulaire AEM Forms Edge Delivery Services
description: Les services AEM Forms Edge Delivery Services, conçus pour des performances élevées, vous permettent d’envisager l’avenir d’une collecte de données et d’une interaction client rationalisées. L’article répertorie tous les composants de formulaire disponibles prêts à l’emploi pour les formulaires EDD.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: bae9a5178c025b3bafa8ac2da75a1203206c16e1
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 9%

---




# Composants HTML pris en charge dans Edge Delivery de bloc de formulaire

AEM Forms Edge Delivery comprend un bloc de formulaire. Le bloc de formulaire vous permet de créer facilement des formulaires pour capturer et stocker des données capturées.

Le bloc Formulaire prend en charge les composants HTML-5 prêts à l’emploi tels que le texte, l’email, le numéro, la date, etc. Il prend également en charge les éléments de zone de texte, de sélection et d’ensemble de champs. Il comprend également des fonctionnalités de validation d’entrée natives à HTML-5. Le bloc de formulaire crée une structure d’HTML uniforme pour tous les types de champs et conteneurs, assurant ainsi la cohérence. Vous [stylisez également les types de champ](https://adobe-rnd.github.io/form-block/customization/styling_form) à l’aide du fichier `form.css`.

## Types d’entrée d’HTML pris en charge 5 dans le bloc de formulaire

Le bloc de formulaire prend en charge divers types d’entrée d’HTML 5 et effectue le rendu transparent des formulaires créés avec les composants principaux d’AEM.

Le tableau suivant décrit la manière dont les composants principaux correspondent à leurs types d’entrée HTML-5 dans Edge Delivery :

<table>
 <tbody>
  <tr>
   <td><b>Composants principaux</b> </td>
   <td><b>Type d’entrée d’HTML 5</b> </td>
   <td><b>Détails</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">Conteneur de formulaire</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">formulaire </td>
   <td> Créez un formulaire pour capturer les entrées utilisateur.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">Entrée de texte</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">texte</a></td>
   <td> Définit un champ de saisie de texte d’une seule ligne. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">Entrée de nombre</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">nombre</a></td>
   <td>Permet à l’utilisateur de saisir un nombre. Vous pouvez également ajouter une validation intégrée pour rejeter les entrées non numériques. Permet à l’utilisateur de saisir un nombre. Vous pouvez également ajouter une validation intégrée pour rejeter les entrées non numériques. Au départ, le champ de saisie s'affiche sous forme d'une entrée numérique. Si un utilisateur applique un modèle d’affichage, celui-ci se transforme en texte pour permettre à l’auteur d’appliquer le formatage des nombres, car l’HTML 5 ne prend pas en charge les modèles d’affichage. Cependant, lorsque l’utilisateur clique dessus, il revient à saisir des nombres.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">Sélecteur de date</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">date </a></td>
   <td> Créez un champ de saisie pour saisir une date. Vous avez la possibilité de saisir la date soit par le biais d’une zone de texte, qui valide l’entrée, soit par le biais d’une interface de sélecteur de date dédiée. Au départ, le champ de saisie de date natif s’affiche. Si un utilisateur applique un modèle d’affichage, celui-ci se transforme en texte pour permettre à l’utilisateur d’appliquer une mise en forme, car l’HTML 5 ne prend pas en charge les modèles d’affichage. Cependant, lorsque l’utilisateur clique dessus, il revient à saisir une date.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">Pièce jointe</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">Fichier</a></td>
   <td> Permet à l’utilisateur de choisir un ou plusieurs fichiers dans le stockage de l’appareil. Il prend en charge les validations d’entrée de fichier améliorées, telles que les types de fichiers acceptés, les restrictions de taille de fichier et les limites de sélection de fichier minimales/maximales. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> Liste déroulante</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a></td>
   <td> Permet aux utilisateurs de sélectionner une ou plusieurs options dans une liste d’options prédéfinies. Les options peuvent être de type Chaîne, Nombre ou Valeur booléenne.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">Groupe de cases à cocher</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">case à cocher multiple</a></td>
   <td> Permet aux utilisateurs de sélectionner une ou plusieurs options dans une liste. Plusieurs cases à cocher sont générées avec des noms identiques, chacune correspondant à un élément de l’énumération. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">Groupe de boutons radio</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">radio multiple</a></td>
   <td> Permet à un utilisateur de sélectionner une option dans un groupe d’options associées. Plusieurs boutons radio sont générés avec des noms identiques, chacun correspondant à un élément de l’énumération.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">Bouton</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">button</a></td>
   <td>Elément de l’interface utilisateur qui permet aux utilisateurs de déclencher une action lorsqu’ils cliquent dessus. </td>
  </tr>
  <tr>
   <td><a href="" https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">Panneau</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">champ avec légende</a></td>
   <td> Regrouper des sections dans un formulaire, où un élément *légende* imbriqué ajoute une légende pour le formulaire.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html#features?lang=fr">Assistant</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a></td>
   <td>Groupe les sections associées dans un formulaire. Il contrôle également la disposition, en prenant en charge les options d’affichage pour les positionner en haut ou à gauche. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">Texte</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">p</a></td>
   <td>Une balise p marque un paragraphe. Dans le contenu visuel, les paragraphes sont des blocs de texte séparés par des lignes vides ou une première ligne mise en retrait.</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Bouton Envoyer</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">submit</a></td>
   <td> Elément de l’interface utilisateur qui permet aux utilisateurs d’envoyer un formulaire au serveur en cliquant dessus. Si un utilisateur ajoute une règle d’envoi à un bouton, elle fonctionne comme un bouton d’envoi. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">Bouton de réinitialisation</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">reset</a></td>
   <td>Elément de l’interface utilisateur qui réinitialise un formulaire en cliquant dessus. Si un utilisateur ajoute une règle de réinitialisation à un bouton, elle fonctionne comme un bouton de réinitialisation. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">Entrée de messagerie</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">email</a></td>
   <td> Permet à l’utilisateur de saisir et de modifier une adresse électronique. Si l’utilisateur ajoute plusieurs attributs, une liste d’adresses email peut être ajoutée ou modifiée.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">Entrée téléphonique</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">tel</a></td>
   <td>Permet à l’utilisateur de saisir et de modifier un numéro de téléphone.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">En-tête</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> en-tête</a></td>
   <td>Il comprend du contenu d’introduction, généralement un groupe d’aide à la navigation ou d’introduction. Il est pris en charge en dehors du conteneur de formulaires. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">Pied de page</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">pied de page</a></td>
   <td> Contient des informations telles que des données de copyright ou des liens vers des documents associés. Il est pris en charge en dehors du conteneur de formulaires.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html#features?lang=fr">Accordéon<a></td>
   <td><i>Pas encore pris en charge dans le bloc de formulaire</i></td>
   <td> Permet à l’utilisateur de créer des sections extensibles et réductibles dans un formulaire. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html#features?lang=fr">Onglets horizontaux</a></td>
   <td><i>Pas encore pris en charge dans le bloc de formulaire</i></td>
   <td>Organise plusieurs sections d’un formulaire dans des onglets distincts, affichés horizontalement.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">Image</a></td>
   <td><i>Pas encore pris en charge dans le bloc de formulaire</i></td>
   <td> Permet aux utilisateurs d’inclure des images dans un formulaire.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">Titre</a></td>
   <td><i>Pas encore pris en charge dans le bloc de formulaire</i></td>
   <td> Fait référence au texte qui s’affiche en haut du formulaire. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Basculer</td>
   <td><i>Pas encore pris en charge dans le bloc de formulaire</i></td>
   <td> Bascule à deux états qui permet à l’utilisateur de sélectionner deux états, comme activer ou désactiver une fonctionnalité, un paramètre ou une fonctionnalité.</td>
  </tr>
 </tbody>
</table>



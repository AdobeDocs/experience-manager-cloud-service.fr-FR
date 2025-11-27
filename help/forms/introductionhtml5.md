---
title: Présentation des formulaires HTML5
description: HTML5 forms est une nouvelle fonctionnalité du logiciel Adobe Experience Manager qui permet d’effectuer le rendu des modèles de formulaire XFA au format HTML5.
topic-tags: hTML5_forms
feature: HTML5 Forms,Mobile Forms
exl-id: 0facca18-ffa1-420c-859a-6f1f2c449d71
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 79%

---

# Présentation des formulaires HTML5{#introduction-to-html-forms}

<span class="preview"> La fonctionnalité Forms d’HTML5 est proposée dans le cadre du programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à l’adresse aem-forms-ea@adobe.com à partir de votre ID d’e-mail officiel (professionnel).
</span>

HTML5 forms est une nouvelle fonctionnalité du logiciel Adobe Experience Manager qui permet d’effectuer le rendu des modèles de formulaire XFA au format HTML5. Cette fonctionnalité permet le rendu des formulaires sur les appareils mobiles et les navigateurs de bureau ne prenant pas en charge les documents XFA en PDF. Les formulaires HTML5 prennent en charge les fonctionnalités existantes des modèles de formulaires XFA, mais ajoutent également de nouvelles fonctionnalités, telles que la signature manuscrite, pour les appareils mobiles.

Les formulaires HTML5 génèrent des documents basés sur des éléments HTML5 standards. Vous pouvez afficher les formulaires HTML5 dans tous les navigateurs récents prenant en charge le format HTML5. Il n’est pas nécessaire d’installer de plug-ins de navigateur supplémentaires pour les navigateurs. <!--For more information about supported browsers, see [Supported client platforms](https://adobe.com/go/learn_aemforms_supportedplatforms_63_fr).-->

![Aperçu du formulaire HTML5](assets/mobile_form_on_an_ipad_date_14.png)

## Fonctionnalités essentielles des formulaires HTML5 {#key-capabilities-of-html-forms-br}

* Rendu des formulaires XFA existants en HTML5 pris en charge sur tous les navigateurs compatibles.
* Exploitation des fonctionnalités standard de conception des formulaires XFA pour les appliquer aux formulaires sur périphériques mobiles.
* Utilisation des fonctionnalités XFA dynamiques au format HTML5.
* Utilisation de la mise en page haute précision SVG (SVG 1.1) pour une correspondance parfaite avec la mise en page de textes PDF.
* Prise en charge de Javascript et de FormCalc.
* Assemblage dynamique de fragments dans des formulaires interactifs en fonction d’événements basés sur des données ou des entrées saisies par l’utilisateur ou l’utilisatrice.
* Prise en charge des CSS personnalisées pour correspondre à l’aspect standard des formulaires de votre entreprise.
* Prise en charge de widgets personnalisés pour une expérience de capture de données riche.
* Prise en charge de l’intégration avec des applications Web.

### Publication multicanal {#multichannel-publishing}

Les développeurs et développeuses de formulaires peuvent utiliser un modèle XFA pour effectuer le rendu des formulaires aux formats PDF et HTML5. Cette fonctionnalité peut s’avérer utile dans les cas où vous avez un jeu de formulaires XFA important nécessitant des modifications mineures pour s’adapter aux pratiques de conception des formulaires HTML5. Vous pouvez générer les formulaires XFA existants au format HTML5 pour cibler différents périphériques ne prenant pas encore en charge le format PDF basé sur XFA.

## Gestion des formulaires HTML5 {#manage-html-forms}

AEM fournit également un affichage unifié permettant de répertorier et gérer tous les modèles de formulaires à l’aide de l’interface utilisateur d’AEM Forms. Vous pouvez activer, désactiver, publier et prévisualiser des formulaires. <!--For more information, see [Introduction to managing forms](../../forms/using/introduction-managing-forms.md).-->

### Personnalisation des formulaires {#forms-customization}

Mobile Forms effectue le rendu des modèles de formulaires à l’aide d’éléments HTML5 standard. Cela facilite la personnalisation et l’extension des formulaires au format HTML5 à l’aide de technologies Web, principalement CSS et JavaScript. Vous pouvez facilement personnaliser l’apparence de widgets existants, créer vos propres widgets personnalisés ou utiliser des styles personnalisés dans les formulaires. Pour plus d’informations sur la création de widgets personnalisés et la personnalisation de widgets existants, consultez la section [Ajout de widgets personnalisés aux formulaires HTML5](/help/forms/custom-widgets.md).

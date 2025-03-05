---
title: Éditeur universel pour Edge Delivery Services for Forms
description: Utilisez l’éditeur universel pour Edge Delivery Services for Forms afin de créer un Forms adaptatif.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: d711e0d1-a2fc-4aa6-af87-6e77a7bc5d2e
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 70%

---


# Éditeur universel pour Edge Delivery Services for Forms

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> avec le nom de votre organisation GitHub et le nom du référentiel. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>

L’éditeur universel révolutionne la création de formulaires pour Adobe Edge Delivery Services en offrant une interface What You See Is What You Get simple, visuelle et intuitive (WYSIWYG). Conçu pour les créateurs et créatrices de contenu et les auteurs et autrices de formulaires, il facilite les processus de création de formulaires traditionnels et les rend accessibles même aux utilisateurs et utilisatrices n’ayant pas de connaissances techniques.

L’éditeur universel vous permet de concevoir rapidement des formulaires réactifs et interactifs à l’aide de composants préconfigurés tels que des champs de texte, des cases à cocher et des boutons radio. Son solide ensemble de fonctionnalités prend en charge des règles dynamiques, une intégration facile des données et une personnalisation avancée, afin que chaque formulaire soit adapté à vos besoins.

Que vous gériez un rendu léger côté client, assuriez la compatibilité entre les navigateurs ou respectiez des normes d’accessibilité strictes, l’éditeur universel fournit une solution rationalisée pour la création et la gestion des formulaires.

![Éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80 %, align-center}

## Fonctionnalités clés de l’éditeur universel pour Edge Delivery Services for Forms



| ![Interface WYSIWYG](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg) | ![Éditeur de règles](/help/edge/docs/forms/universal-editor/assets/rule-editor.svg) | ![Actions Envoyer](/help/edge/docs/forms/universal-editor/assets/submit-actions.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Interface WYSIWYG**](/help/edge/docs/forms/universal-editor/universal-editor-user-interface.md) | [**Éditeur de règles**](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) | [**Actions Envoyer**](/help/edge/docs/forms/universal-editor/submit-action.md) |
| L’éditeur universel fournit une interface WYSIWYG pour la conception de formulaire avec une bibliothèque de composants préconfigurée, une conception réactive, une création basée sur des modèles et des modifications de champs en temps réel. | L’éditeur de règles permet aux utilisateurs et utilisatrices de créer des interactions de formulaires dynamiques à l’aide de règles pilotées par les événements, de validations instantanées et de gestion des erreurs via JavaScript et JSON légers. | Les actions Envoyer prennent en charge l’intégration du serveur principal, la logique d’envoi conditionnel, les points d’entrée sécurisés et les préprocesseurs, ce qui simplifie les workflows d’envoi. |

| ![Publication/Dépublication](/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg) | ![Mode réactif](/help/edge/docs/forms/universal-editor/assets/responsive.svg) | ![ Composants personnalisés ](/help/edge/docs/forms/universal-editor/assets/custom-components.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Publication/Dépublication**](/help/edge/docs/forms/universal-editor/publish-forms.md) | [**Mode réactif**](/help/edge/docs/forms/universal-editor/responsive-layout.md) | [**Composants personnalisés**](/help/edge/docs/forms/universal-editor/create-custom-component.md) |
| Contrôlez facilement la visibilité de vos formulaires : publiez ou dépubliez-les directement à partir de l’éditeur en quelques clics seulement. | Concevez des formulaires qui s’adaptent facilement à tous les appareils (ordinateurs de bureau, tablettes et appareils mobiles). Utilisez le mode réactif pour prévisualiser et tester les formulaires pour différentes tailles d’écran. | Les composants personnalisés permettent aux développeurs et aux développeuses d’étendre les fonctionnalités de formulaire en créant des éléments uniques adaptés à des cas d’utilisation organisationnels spécifiques. |

| ![Style](/help/edge/docs/forms/universal-editor/assets/personalization.svg) | ![Services de préremplissage](/help/edge/docs/forms/universal-editor/assets/prefill-services.svg) | ![Test A/B](/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Style**](/help/edge/docs/forms/universal-editor/style-theme-forms.md) | **Services De Préremplissage** (Bientôt Disponible) | [**Test A/B**](https://github.com/adobe/aem-experimentation/blob/main/documentation/experiments.md) |
| L’utilisation de styles CSS permet aux développeurs et aux développeuses de personnaliser l’aspect des éléments de formulaire et de créer une conception attrayante sur le plan visuel, en harmonie avec l’esthétique du site web. | Les services de préremplissage renseignent automatiquement les champs de formulaire avec des données d’utilisateurs ou d’utilisatrices pertinentes provenant de diverses sources, ce qui réduit la saisie manuelle et améliore l’expérience d’utilisation. | Les tests A/B permettent aux entreprises de tester différentes conceptions, dispositions et fonctionnalités de formulaire afin d’identifier les variantes les plus performantes. |

| ![Analytics et tracking](/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg) | ![ Fragments de formulaire ](/help/edge/docs/forms/universal-editor/assets/form-fragments.svg) | ![Liaison de données](/help/edge/docs/forms/universal-editor/assets/data-binding.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Analytics et tracking**](https://www.aem.live/developer/martech-integration) | **Fragments De Formulaire** (Bientôt Disponible) | **Liaison De Données** (Bientôt Disponible) |
| Obtenez des informations sur le comportement des utilisateurs et utilisatrices, les interactions des formulaires et les taux d’envoi grâce aux analyses et au tracking intégrés pour permettre une optimisation des formulaires pilotée par les données. | Les fragments de formulaire permettent la réutilisation en permettant de créer une seule fois des sections couramment utilisées et de les réutiliser dans plusieurs formulaires, ce qui garantit la cohérence et réduit les efforts de maintenance. | La liaison de données permet des connexions directes entre les champs de formulaire et les sources de données principales, ce qui permet la mise à jour en temps réel et le mappage de données avancé. |

| ![ CAPTCHA ](/help/edge/docs/forms/universal-editor/assets/captcha.svg) | ![Intégration de Forms](/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg) | ![Configuration de remerciement](/help/edge/docs/forms/universal-editor/assets/thank-you.svg) |
|:-------------:|:-------------:|:-------------:|
| [**CAPTCHA**](/help/edge/docs/forms/universal-editor/recaptcha-forms.md) | **Intégration De Forms** (Bientôt Disponible) | [**Configuration de remerciement**](/help/edge/docs/forms/universal-editor/submit-action.md#show-a-custom-thank-you-message-on-adaptive-form-submission-submit-action-message-ue) |
| Utilisez reCAPTCHA pour protéger les formulaires contre les robots automatisés, en assurant une collecte de données sécurisée et fiable. | Incorporez des formulaires directement dans des pages Edge Delivery Services Sites à l’aide du composant intégré de l’éditeur universel. | Personnalisez facilement le message ou la page d’accusé de réception affiché aux utilisateurs et utilisatrices après l’envoi du formulaire. |


<!-- ![Universal Editor](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg)  **WYSIWYG interface for Form creation**: Universal Editor provides a WYSIWYG interface for form design. It provides pre-built component library, responsive design support, and template-based form creation. You can instantly add or remove form fields and modify field properties (like label, data binding, validation). You can also plugin custom form components to Universal Editor.


* **Rule editor**: The rule editor stands out as a powerful mechanism for creating sophisticated form interactions. It supports event-driven rules, instant validation, and error handling through lightweight JavaScript and JSON-based definitions. This allows developers to implement complex form logic, such as conditional field visibility, automatic calculations, and dynamic form behaviour without extensive coding.

* **Submit actions**: Submit Actions enable form submission workflows. These actions provide comprehensive backend integration options, supporting protocols like REST API. The system allows you configure data pre-processors for automatic data transformation, conditional submission logic based on form field values, and secure endpoint connections. Organizations can define complex submission rules that validate data, and manage form responses with granular control.

* **Pre-fill services:** Pre-fill Services enhance user experience by intelligently populating form fields with relevant data. These services connect to various data sources, including user profiles, browser local storage, and external databases. The mechanism supports dynamic data population, enabling automatic completion of form fields based on contextual information. Users benefit from reduced manual data entry, while administrators gain flexibility in configuring pre-fill rules across different form types and scenarios. The pre-fill functionality adapts to different authentication methods, including session-based approaches and token-based systems, ensuring both convenience and security.

* **Data binding capabilities**: Data binding in the Universal Editor enables direct, dynamic connections between form fields and backend data sources. This feature allows real-time synchronization of form data, supporting complex data mapping scenarios. The system supports transforming form inputs into structured database records with minimal configuration. Advanced mapping supports nested data structures, allowing complex form designs to interact seamlessly with intricate data models.

* **Internationalization/localization capabilities**: Internationalization support ensures global accessibility, with multi-language rendering, right-to-left language compatibility, and locale-specific formatting.

* **Analytics and tracking mechanisms**: The built-in analytics and tracking mechanisms provide comprehensive insights into form interactions, submission rates, and user behavior, enabling continuous optimization of form design and performance. 

* **Experimentation (A/B Testing)**: The Universal Editor supports experimentation by allowing organizations to run A/B tests on form designs to identify the best-performing layouts or features.

* **Task Management via Adobe Workfront**: Integration with Adobe Workfront allows teams to manage tasks related to form creation and maintenance, ensuring streamlined collaboration and efficient workflows.

* **Editor Customization via UI Extension**: Developers can extend the functionality of the Universal Editor through UI extensions, enabling tailored solutions that fit specific organizational needs. -->

## Composants de formulaire préconfigurés

L’éditeur universel fournit les composants de formulaire suivants prêts à l’emploi :

<table>
  <thead>
    <tr>
      <th></th> 
      <th>Composants de formulaire</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="22"><img src="/help/edge/docs/forms/universal-editor/assets/adaptive-forms-components.png" alt="Composants de formulaire" style="width: 100%;"></td> 
      <td><b>Accordéon</b></td>
      <td>Structure de panneau réductible pour organiser le contenu.</td>
    </tr>
    <tr>
      <td><b>Bouton</b></td>
      <td>Ajoute des éléments interactifs pour des actions telles que la navigation ou une logique personnalisée.</td>
    </tr>
    <tr>
      <td><b>Captcha</b></td>
      <td>Empêche les spams en demandant aux utilisateurs et utilisatrices d’effectuer une tâche de vérification humaine à l’aide de Google reCaptcha ou HCaptcha.</td>
    </tr>
    <tr>
      <td><b>Case à cocher</b></td>
      <td>Permet aux utilisateurs et utilisatrices de configurer une case à cocher.</td>
    </tr>
    <tr>
      <td><b>Groupe de cases à cocher</b></td>
      <td>Permet aux utilisateurs et utilisatrices de sélectionner plusieurs options dans un groupe.</td>
    </tr>
    <tr>
      <td><b>Sélecteur de date</b></td>
      <td>Permet aux utilisateurs et utilisatrices de sélectionner une date à l’aide d’une interface de calendrier.</td>
    </tr>
    <tr>
      <td><b>Listes déroulantes</b></td>
      <td>Propose des options à sélection unique ou multiple dans une liste prédéfinie.</td>
    </tr>
    <tr>
      <td><b>E-mail</b></td>
      <td>Capture les adresses e-mail avec validation du format de base.</td>
    </tr>
    <tr>
      <td><b>Pièce jointe</b></td>
      <td>Permet de charger des documents, des images ou d’autres types de fichiers.</td>
    </tr>
    <tr>
      <td><b>Fragments de formulaire</b></td>
      <td>Composants de formulaire réutilisables pour des sections telles que les champs d’adresse ou les coordonnées.</td>
    </tr>
    <tr>
      <td><b>Image</b></td>
      <td>Prend en charge le chargement et l’affichage d’images dans les formulaires.</td>
    </tr>
    <tr>
      <td><b>Boîte de dialogue modale</b></td>
      <td>Affiche une boîte de dialogue contextuelle, souvent utilisée pour les alertes, les informations supplémentaires ou la confirmation.</td>
    </tr>
    <tr>
      <td><b>Champ numérique</b></td>
      <td>Capture une entrée numérique, ce qui permet de valider des nombres ou des plages.</td>
    </tr>
    <tr>
      <td><b>Panneau</b></td>
      <td>Organise les sections de formulaire avec des panneaux extensibles/réductibles.</td>
    </tr>
    <tr>
      <td><b>Cases d’option</b></td>
      <td>Active la sélection à choix unique à partir d’un groupe d’options.</td>
    </tr>
    <tr>
      <td><b>Évaluation</b></td>
      <td>Permet aux utilisateurs et utilisatrices de fournir une évaluation par étoiles.</td>
    </tr>
    <tr>
      <td><b>Bouton de réinitialisation</b></td>
      <td>Réinitialise les champs de formulaire à leur état par défaut.</td>
    </tr>
    <tr>
      <td><b>Bouton Envoyer</b></td>
      <td>Déclenche l’envoi du formulaire et lance les workflows définis.</td>
    </tr>
    <tr>
      <td><b>Champ Numéro de téléphone</b></td>
      <td>Capture les numéros de téléphone avec une mise en forme basée sur le pays.</td>
    </tr>
    <tr>
      <td><b>Texte</b></td>
      <td>Fournit une section dédiée pour afficher les termes juridiques et collecter les contrats d’utilisation via des cases à cocher.</td>
    </tr>
    <tr>
      <td><b>Champ de texte</b></td>
      <td>Capture une entrée sur une seule ligne, telle que des noms ou des adresses e-mail.</td>
    </tr>
    <tr>
      <td><b>Assistant</b></td>
      <td>Guide les utilisateurs et utilisatrices pas à pas tout au long d’un processus de formulaire en plusieurs parties.</td>
    </tr>
  </tbody>
</table>

<!-- * Footer: Adds a footer section for consistent design or additional information.
* Form Container: Wraps all form elements and manages overall form properties.
* Header: Adds a header section for form titles, branding, or instructions.-->
<!-- * 
* Prefillable Fields: Automatically populates form fields with data from predefined sources such as user profiles or APIs. 

* Switches/Toggle Buttons: Provides binary on/off choices for user input.


* Title: Adds a text-based heading or label to improve form clarity and organization.


In-addtion to pre-built form components, the Universal editor also provides support for:

* **Embedding Forms in Another Webpage**: The Universal Editor supports embedding forms directly into Edge Deliver Services Sites pages. This can be done using the embed component provided out of the box.

* **Validation Messages**: Validation messages provide real-time feedback to users when they enter incorrect or incomplete data. Features include:
    * Dynamic Error Display: Instantly alerts users to errors, such as invalid email addresses or missing required fields.
    * Customizable Messages: Allows form authors to define user-friendly error texts.
    * Rule-Based Validation: Supports advanced validation logic, such as checking dependencies between fields or implementing conditional rules.

* **Hidden Fields**: Hidden fields store data invisibly within the form, often for backend processing or prefilled values. Use cases include:
    * Passing contextual information (e.g., user ID or session data) to the backend without displaying it to users.
    * Capturing metadata like timestamps or tracking IDs.
    * Hidden fields are not visible to end-users but can be prefilled, updated dynamically, or used in workflows.

* **Custom Components**: Custom components allow developers to extend the functionality of forms by creating specialized or third-party integrations. Features include:
    * Flexibility: Developers can design unique form elements tailored to specific use cases.
    * Third-Party Integration: Embed widgets or tools like payment gateways, analytics trackers, or AI-driven input fields.
    * Seamless Compatibility: Custom components can integrate with the Universal Editor's drag-and-drop interface and existing features like data binding or validation.

* **Thank you Configuration**: Customize the acknowledgment message or page shown after form submission.
-->


## Intégration

Pour activer l’éditeur universel et ses fonctionnalités avancées telles que l’éditeur de règles, écrivez-nous à l’adresse aem-forms-ea@adobe.com à partir de votre ID d’e-mail officiel. L’équipe d’Adobe est là pour vous aider à transformer votre expérience de création de formulaires.

## Questions fréquentes

**Q : Qui peut utiliser l’éditeur universel ?**
L’éditeur universel est conçu pour un large public, notamment :

* Les créateurs et créatrices de contenu qui souhaitent créer des formulaires attrayants visuellement.
* Le développeurs et développeuses ayant besoin de fonctionnalités de personnalisation et d’intégration avancées.
* Les entreprises à la recherche de solutions de formulaires évolutives, sécurisées et conformes.

**Q : Puis-je intégrer des formulaires créés avec l’éditeur universel dans mes systèmes existants ?**
Absolument. L’éditeur universel prend en charge la liaison de données transparente avec les systèmes backend, ce qui permet des mises à jour en temps réel et un mappage de données avancé. Il s’intègre également à des outils tels qu’Adobe Workfront pour la gestion des tâches et prend en charge les points d’entrée sécurisés pour les workflows d’envoi de données.

**Q : Est-il possible de personnaliser les composants de formulaire ?**
Oui, l’éditeur universel permet aux développeurs et aux développeuses de créer des composants personnalisés et adaptés aux besoins spécifiques de l’entreprise. De plus, vous pouvez étendre les fonctionnalités de l’éditeur par le biais d’extensions d’interface d’utilisation et de workflows personnalisés.

**Q : Comment l’éditeur universel gère-t-il l’accessibilité ?**
L’éditeur universel est conçu dans le strict respect des normes d’accessibilité, y compris les directives d’accessibilité du contenu web (WCAG). Cela permet de s’assurer que les formulaires sont utilisables par les personnes en situation de handicap, et offre ainsi une expérience inclusive.

**Q : Quel type d’analyse puis-je obtenir des formulaires ?**
L’éditeur universel comprend des outils d’analyse et de suivi intégrés pour surveiller les interactions utilisateur, les taux d’envoi de formulaires et les mesures de conversion. Ces informations vous aident à optimiser vos formulaires pour de meilleures performances.


## Commencer à créer des formulaires

{{universal-editor-see-also}}


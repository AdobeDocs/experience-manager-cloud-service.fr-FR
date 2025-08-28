---
title: Éditeur universel d’Edge Delivery Services pour AEM Forms
description: Utilisez l’éditeur universel d’Edge Delivery Services pour AEM Forms afin de créer des formulaires adaptatifs.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: d711e0d1-a2fc-4aa6-af87-6e77a7bc5d2e
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: ht
source-wordcount: '984'
ht-degree: 100%

---


# Éditeur universel d’Edge Delivery Services pour AEM Forms

L’éditeur universel révolutionne la création de formulaires pour Adobe Edge Delivery Services en offrant une interface What You See Is What You Get (WYSIWYG) simple, visuelle et intuitive. Conçu pour les créateurs et créatrices de contenu et les auteurs et autrices de formulaires, il facilite les processus de création de formulaires traditionnels et les rend accessibles même aux utilisateurs et utilisatrices n’ayant pas de connaissances techniques.

L’éditeur universel vous permet de concevoir rapidement des formulaires réactifs et interactifs à l’aide de composants préconfigurés tels que des champs de texte, des cases à cocher et des boutons radio. Son solide ensemble de fonctionnalités prend en charge des règles dynamiques, une intégration facile des données et une personnalisation avancée, afin que chaque formulaire soit adapté à vos besoins.

Que vous gériez un rendu léger côté client, assuriez la compatibilité entre les navigateurs ou respectiez des normes d’accessibilité strictes, l’éditeur universel fournit une solution rationalisée pour la création et la gestion des formulaires.

![Éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center}

## Principales fonctionnalités de l’éditeur universel d’Edge Delivery Services pour AEM Forms



| ![Interface WYSIWYG](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg) | ![Éditeur de règles](/help/edge/docs/forms/universal-editor/assets/rule-editor.svg) | ![Actions Envoyer](/help/edge/docs/forms/universal-editor/assets/submit-actions.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Interface WYSIWYG**](/help/edge/docs/forms/universal-editor/universal-editor-user-interface.md) | [**Éditeur de règles**](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) | [**Actions Envoyer**](/help/edge/docs/forms/universal-editor/submit-action.md) |
| L’éditeur universel fournit une interface WYSIWYG pour la conception de formulaire avec une bibliothèque de composants préconfigurée, une conception réactive, une création basée sur des modèles et des modifications de champs en temps réel. | L’éditeur de règles permet aux utilisateurs et utilisatrices de créer des interactions de formulaires dynamiques à l’aide de règles pilotées par les événements, de validations instantanées et de gestion des erreurs via JavaScript et JSON légers. | Les actions Envoyer prennent en charge l’intégration du serveur principal, la logique d’envoi conditionnel, les points d’entrée sécurisés et les préprocesseurs, ce qui simplifie les workflows d’envoi. |

| ![Publication/dépublication](/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg) | ![Mode réactif](/help/edge/docs/forms/universal-editor/assets/responsive.svg) | ![Composants personnalisés](/help/edge/docs/forms/universal-editor/assets/custom-components.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Publication/dépublication**](/help/edge/docs/forms/universal-editor/publish-forms.md) | [**Mode réactif**](/help/edge/docs/forms/universal-editor/responsive-layout.md) | [**Composants personnalisés**](/help/edge/docs/forms/universal-editor/create-custom-component.md) |
| Contrôlez facilement la visibilité de vos formulaires : publiez ou dépubliez-les directement à partir de l’éditeur en quelques clics seulement. | Concevez des formulaires qui s’adaptent facilement à tous les appareils (ordinateurs de bureau, tablettes et appareils mobiles). Utilisez le mode réactif pour prévisualiser et tester les formulaires pour différentes tailles d’écran. | Les composants personnalisés permettent aux développeurs et aux développeuses d’étendre les fonctionnalités de formulaire en créant des éléments uniques adaptés à des cas d’utilisation organisationnels spécifiques. |

| ![Style](/help/edge/docs/forms/universal-editor/assets/personalization.svg) | ![Services de préremplissage](/help/edge/docs/forms/universal-editor/assets/prefill-services.svg) | ![Tests A/B](/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Style**](/help/edge/docs/forms/universal-editor/style-theme-forms.md) | **[Préremplir des formulaires](/help/edge/docs/forms/universal-editor/prefill-form.md)** | [**Tests A/B**](https://github.com/adobe/aem-experimentation/blob/main/documentation/experiments.md) |
| L’utilisation de styles avec les CSS permet aux équipes de développement de personnaliser l’aspect des éléments de formulaire et de créer une conception visuellement attrayante, en harmonie avec l’esthétique du site web. | Les services de préremplissage renseignent automatiquement les champs de formulaire avec des données d’utilisateurs ou d’utilisatrices pertinentes provenant de diverses sources, ce qui réduit la saisie manuelle et améliore l’expérience d’utilisation. | Les tests A/B permettent aux entreprises de tester différentes conceptions, dispositions et fonctionnalités de formulaire afin d’identifier les variantes les plus performantes. |

| ![Analyses et tracking](/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg) | ![Fragments de formulaire](/help/edge/docs/forms/universal-editor/assets/form-fragments.svg) | ![Liaison de données](/help/edge/docs/forms/universal-editor/assets/data-binding.svg) |
|:-------------:|:-------------:|:-------------:|
| [**Analyses et tracking**](https://www.aem.live/developer/martech-integration) | **Fragments de formulaire** (prochainement) | [**Liaison de données**](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) |
| Obtenez des informations sur le comportement des utilisateurs et utilisatrices, les interactions des formulaires et les taux d’envoi grâce aux analyses et au tracking intégrés pour permettre une optimisation des formulaires pilotée par les données. | Les fragments de formulaire permettent la réutilisation : il est ainsi possible de créer une seule fois des sections couramment utilisées et de les réutiliser dans plusieurs formulaires, ce qui garantit la cohérence et réduit les efforts de maintenance. | La liaison des données permet des connexions directes entre les champs de formulaire et les sources de données back-end, prenant en charge les mises à jour en temps réel et le mappage de données avancé. |

| ![CAPTCHA](/help/edge/docs/forms/universal-editor/assets/captcha.svg) | ![Incorporation de formulaires](/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg) | ![Configuration du remerciement](/help/edge/docs/forms/universal-editor/assets/thank-you.svg) |
|:-------------:|:-------------:|:-------------:|
| [**CAPTCHA**](/help/edge/docs/forms/universal-editor/recaptcha-forms.md) | **Intégration de formulaires** (prochainement) | [**Configuration du remerciement**](/help/edge/docs/forms/universal-editor/submit-action.md#show-a-custom-thank-you-message-on-adaptive-form-submission-submit-action-message-ue) |
| Utilisez reCAPTCHA pour protéger les formulaires contre les robots automatisés, en assurant une collecte de données sécurisée et fiable. | Incorporez des formulaires directement dans des pages de sites Edge Delivery Services à l’aide du composant d’incorporation intégré de l’éditeur universel. | Personnalisez facilement le message ou la page d’accusé de réception affiché aux utilisateurs et utilisatrices après l’envoi du formulaire. |



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

## Questions fréquentes

**Q : Qui peut utiliser l’éditeur universel ?**
L’éditeur universel est conçu pour un large public, notamment :

- Les créateurs et créatrices de contenu qui souhaitent créer des formulaires attrayants visuellement.
- Le développeurs et développeuses ayant besoin de fonctionnalités de personnalisation et d’intégration avancées.
- Les entreprises à la recherche de solutions de formulaires évolutives, sécurisées et conformes.

**Q : Puis-je intégrer des formulaires créés avec l’éditeur universel dans mes systèmes existants ?**
Absolument. L’éditeur universel prend en charge la liaison de données transparente avec les systèmes backend, ce qui permet des mises à jour en temps réel et un mappage de données avancé. Il s’intègre également à des outils tels qu’Adobe Workfront pour la gestion des tâches et prend en charge les points d’entrée sécurisés pour les workflows d’envoi de données.

**Q : Est-il possible de personnaliser les composants de formulaire ?**
Oui, l’éditeur universel permet aux développeurs et aux développeuses de créer des composants personnalisés et adaptés aux besoins spécifiques de l’entreprise. De plus, vous pouvez étendre les fonctionnalités de l’éditeur par le biais d’extensions d’interface d’utilisation et de workflows personnalisés.

**Q : Quel type d’analyse puis-je obtenir des formulaires ?**
L’éditeur universel comprend des outils d’analyse et de suivi intégrés pour surveiller les interactions utilisateur, les taux d’envoi de formulaires et les mesures de conversion. Ces informations vous aident à optimiser vos formulaires pour de meilleures performances.

**Q : Comment l’éditeur universel gère-t-il l’accessibilité ?**
L’éditeur universel est conçu dans le strict respect des normes d’accessibilité, y compris les directives d’accessibilité du contenu web (WCAG). Cela permet de s’assurer que les formulaires sont utilisables par les personnes en situation de handicap, et offre ainsi une expérience inclusive.







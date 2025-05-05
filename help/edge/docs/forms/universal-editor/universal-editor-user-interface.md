---
title: Présentation de l’éditeur universel
description: Ce tutoriel vous permet de vous familiariser avec l’interface de l’éditeur universel. Il permet de comprendre l’interface utilisateur de création de vos propres formulaires Edge Delivery Services dans l’éditeur universel.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 11%

---


# Exploration de l’interface de l’éditeur universel (WYSIWYG)

L’[Éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) offre une interface What You See Is What You Get (WYSIWYG) simple, visuelle et intuitive pour les formulaires Adobe Edge Delivery Services (EDS) pour AEM Forms. Il fournit une interface moderne et par glisser-déposer pour une création de formulaire efficace.

![Interface utilisateur de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Ce que vous apprendrez

À la fin de ce tutoriel, vous aurez :

- Comprendre les principaux composants de l’interface de l’éditeur universel
- Naviguez en toute confiance dans les différentes sections de l’interface
- Savoir comment accéder aux outils de création de formulaires essentiels et les utiliser
- Familiarisez-vous avec les raccourcis clavier qui augmentent la productivité

## Présentation de l’interface de l’éditeur universel

Lorsque vous modifiez un formulaire à l’aide de l’éditeur universel, la console ouvre une interface WYSIWYG interactive qui vous permet de commencer immédiatement la modification. Cette interface fournit des commentaires visuels en temps réel au fur et à mesure que vous travaillez et montre exactement comment votre formulaire apparaîtra aux utilisateurs finaux.

>[!NOTE]
>
> Pour découvrir comment créer des formulaires à l’aide de l’éditeur universel, consultez l’article [Prise en main d’Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel (WYSIWYG)](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

![Interface utilisateur de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

L’interface de l’éditeur universel est divisée en quatre parties logiques :

- **[A : en-tête Experience Cloud](#experience-cloud-header)**
- **[B : barre d’outils de l’éditeur universel](#universal-editor-toolbar)**
- **[C : panneau Propriétés](#properties-panel)**
- **[D : éditeur](#editor)**

Explorons chaque section en détail.

### En-tête Experience Cloud

L’en-tête Experience Cloud s’affiche en haut de la console et fournit un contexte de navigation dans l’écosystème Adobe Experience Cloud au sens large. Il indique votre emplacement actuel et permet un accès rapide à d’autres applications Experience Cloud.

![En-tête Experience Cloud de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)

Examinons chaque composant :

- **Adobe Experience Cloud**

  Cliquer sur le lien **Adobe Experience Cloud** sur le côté gauche de l’écran vous permet d’accéder à la racine de la solution Experience Manager. De là, vous pouvez accéder à d’autres outils tels que Experience Manager Sites, Experience Manager Assets et Experience Manager Guides.

  ![Adobe Experience Manager](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png)

- **Nom de l’organisation**

  Le **Nom de l’organisation** affiche le nom de l’organisation Identity Management System (IMS) dans laquelle vous êtes actuellement connecté. Si vous avez accès à plusieurs organisations, vous pouvez passer d’une organisation à l’autre à l’aide de ce menu déroulant. Par exemple, dans la capture d’écran, l’organisation IMS actuellement sélectionnée est « AEM Forms Internal01 ».

  ![Organisation](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png)

- **Aide**

  L’icône Aide permet d’accéder rapidement aux ressources d’apprentissage et de support. Cela s’avère particulièrement utile lorsque vous rencontrez des difficultés ou que vous avez besoin de conseils sur des fonctionnalités spécifiques. Vous pouvez également envoyer des commentaires par le biais de cette section.

  ![Aide](/help/edge/docs/forms/universal-editor/assets/ue-help.png)

- **Notifications**

  La section **Notifications** affiche le nombre de notifications incomplètes, de demandes et de tâches actuelles actuellement affectées dans votre organisation IMS. Garder un œil sur cette section vous permet de garder une longueur d’avance sur votre workflow.

  ![Notification.](/help/edge/docs/forms/universal-editor/assets/ue-notification.png)

- **Solutions**

  Le menu **Solutions** vous permet de passer à d’autres solutions Adobe Experience Cloud, ce qui facilite le passage d’un outil à l’autre dans votre workflow.

  ![Solutions](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png)

- **Profil utilisateur**

  Cette icône affiche vos informations de profil, ainsi que le nom de l’organisation IMS dans laquelle vous êtes actuellement connecté. Cliquez sur cette icône pour accéder aux paramètres du compte et aux options de déconnexion.

  ![Auteur](/help/edge/docs/forms/universal-editor/assets/ue-author.png)

### Barre d’outils de l’éditeur universel

La barre d’outils fournit des outils de navigation et d’édition essentiels. Il vous permet de vous déplacer entre les formulaires, de publier ou de dépublier des formulaires, de modifier les propriétés des formulaires et d’accéder à l’éditeur de règles pour ajouter des comportements dynamiques.

![Barre d’outils de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

Voici ce que chaque composant offre :

- **Bouton Accueil**

  Le bouton Accueil vous renvoie à la page de démarrage de l’éditeur universel. Cela s’avère utile lorsque vous devez commencer à travailler sur un autre formulaire. Vous pouvez également saisir directement une URL dans la barre d’emplacement pour accéder à n’importe quel formulaire à modifier.

  ![Accueil de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/ue-home.png)

- **Barre d’emplacement**

  La **barre d’emplacement** affiche l’adresse du formulaire que vous êtes en train de modifier. Pour passer à un autre formulaire, il vous suffit de cliquer sur la barre d’emplacement et de saisir son URL. Le raccourci clavier permettant de placer le focus sur la barre d’emplacement est `l`.

  ![ Barre d’emplacement ](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png)

- **Éditeur de règles**

  L’**éditeur de règles** vous permet d’ajouter des comportements dynamiques à vos formulaires par le biais d’une interface visuelle intuitive. Il vous permet de créer des conditions, des validations et des actions qui répondent aux entrées des utilisateurs et utilisatrices, rendant vos formulaires interactifs et intelligents.

  ![Éditeur de règles](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > - L’extension Éditeur de règles n’est pas activée par défaut dans l’éditeur universel. Pour activer cette puissante fonctionnalité, contactez-nous à l&#39;adresse [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) à partir de votre adresse e-mail officielle.
  > - Pour savoir comment créer et gérer des règles, reportez-vous à l’article [Présentation de l’éditeur de règles dans la création WYSIWYG](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

- **Modifier les propriétés du formulaire**

  L’option **Modifier les propriétés du formulaire** vous permet de configurer des paramètres de formulaire importants, tels que le modèle de données de formulaire (FDM) et la date de publication. Ces propriétés influencent le comportement de votre formulaire et l’intégration aux systèmes back-end.

  ![Modifier les propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)

- **Paramètres d’en-tête d’authentification**

  L’option **Paramètres d’en-tête d’authentification** vous permet de définir des en-têtes d’authentification personnalisés à des fins de développement local. Cela s’avère particulièrement utile lors du test de formulaires nécessitant des informations d’authentification.

  ![ En-tête d’authentification ](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png)

- **Mode réactif**

  La fonctionnalité **Mode réactif** vous permet de tester l’aspect de votre formulaire sur différents appareils. Par défaut, l’éditeur s’ouvre en mode Bureau, mais vous pouvez passer en mode mobile pour vous assurer que votre formulaire reste utilisable et attrayant sur des écrans plus petits.

  ![Mode réactif](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png)

- **Mode Aperçu**

  Le **mode Aperçu** affiche votre formulaire tel qu’il apparaîtra une fois publié. Vous pouvez ainsi interagir avec le formulaire en cliquant sur des liens et des boutons, comme le feraient vos utilisateurs et utilisatrices. Il s’agit d’une étape essentielle avant la publication pour vérifier que tout fonctionne comme prévu. Basculez entre les modes d’édition et de prévisualisation à l’aide du raccourci clavier `p`.

  ![Aperçu](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

- **Ouvrir la page**

  Le bouton **Ouvrir la page** ouvre votre formulaire dans un nouvel onglet du navigateur pour l’aperçu. Vous obtenez ainsi un affichage plein écran de votre formulaire sans l’interface de l’éditeur. Le raccourci clavier pour cette action est `o`.

  ![Ouvrir la page](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

- **Publier**

  Une fois que votre formulaire est prêt pour les utilisateurs et utilisatrices, le bouton **Publier** le rend actif et disponible pour votre audience. Il s’agit de la dernière étape de votre processus de création de formulaire.

  ![Publier](/help/edge/docs/forms/universal-editor/assets/ue-publish.png)

- **Menu Points de suspension**

  Cliquez sur les points de suspension (...) pour afficher d’autres options, y compris la possibilité de **Dépublier** un formulaire actuellement actif. Cela s’avère utile lorsque vous devez supprimer temporairement un formulaire de l’accès public ou le remplacer par une version mise à jour.

  ![Points de suspension](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png)

### Panneau Propriétés

Le **panneau Propriétés** s’affiche sur le côté droit de l’interface et affiche des informations contextuelles en fonction de ce que vous avez sélectionné dans le formulaire. Lorsqu’aucun composant n’est sélectionné, il affiche la structure globale du formulaire.

![Panneau Propriétés](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

Explorons ses composants clés :

- **Mode Propriétés**

  Le mode **Propriétés** affiche les paramètres et les options du composant actuellement sélectionné. C’est là que vous personnalisez les éléments individuels de votre formulaire pour répondre à vos besoins spécifiques. Le raccourci clavier permettant d’ouvrir les propriétés d’un composant sélectionné est `d`.

  ![Propriétés](/help/edge/docs/forms/universal-editor/assets/ue-properties.png)

- **Arborescence de contenu**

  L’**Arborescence de contenu** affiche la structure hiérarchique de votre formulaire. Cette représentation visuelle vous aide à comprendre comment les composants sont imbriqués les uns dans les autres. Cliquez sur un élément de l’arborescence pour le sélectionner dans l’éditeur et le faire défiler jusqu’à son emplacement. Cela s’avère particulièrement utile pour les formulaires complexes. Activez/désactivez la vue arborescente du contenu à l’aide du raccourci clavier `f`.

  ![Arborescence de contenu](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png)

- **Générer des variations**

  La fonction **Générer des variations** exploite l’intelligence artificielle pour créer différentes versions de votre formulaire en fonction d’invites spécifiques. Cela vous permet de tester différentes approches et conceptions sans créer manuellement chaque variation. Les invites peuvent être fournies par Adobe ou personnalisées par vous.

  ![Générer des variations](/help/edge/docs/forms/universal-editor/assets/ue-variations.png)

  >[!NOTE]
  >
  > Pour obtenir des instructions détaillées sur l’utilisation de l’option Générer des variations pour les formulaires, reportez-vous à l’article [Générer des variations](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/generative-ai/generate-variations).

- **Expérimentation**

  La fonctionnalité **Expérimentation** vous permet d’exécuter des tests contrôlés comparant différentes conceptions de formulaire et mises en page. En analysant la manière dont les utilisateurs interagissent avec chaque variante, vous pouvez prendre des décisions basées sur les données afin d’optimiser les taux de conversion et l’expérience utilisateur.

  ![ Expérimentation ](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png)

- **Personnalisation**

  Les paramètres **Personalization** vous permettent de connecter vos formulaires à Adobe Experience Platform (AEP) ou à des applications externes. Cette connexion vous permet de créer des expériences de formulaire personnalisées en fonction des données et des comportements des utilisateurs et utilisatrices, ce qui accroît la pertinence et l’engagement.

  ![Personnalisation](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png)

- **Tests A/B**

  Le **Test A/B** vous aide à comparer des variations spécifiques de votre formulaire afin de déterminer laquelle est la plus performante. Contrairement à l’expérimentation au sens large, les tests A/B se concentrent généralement sur la comparaison d’éléments ou de modifications spécifiques afin d’identifier l’option la plus efficace.

  ![Tests A/B](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png)

- **Gestion des tâches**

  La fonctionnalité **Gestion des tâches** simplifie la collaboration en aidant votre équipe à organiser, suivre et exécuter des tâches liées à la création et à l’optimisation des formulaires. Cela permet de faire avancer les projets de manière efficace et d’établir clairement les responsabilités.

  ![Gestion des tâches](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png)

- **Brouillons de contenu**

  La fonction **Brouillons de contenu** vous permet de créer et d’enregistrer des versions préliminaires d’éléments de texte dans votre formulaire. Vous pouvez créer des brouillons à l’aide du texte de formulaire existant ou commencer à partir de zéro, puis les modifier ou les supprimer selon vos besoins. Par défaut, vous verrez trois brouillons, mais si vous cliquez sur **Tout afficher** d’autres brouillons s’affichent.

  ![Brouillons de contenu](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png)

- **Source de données**

  L’option **Source de données** permet de configurer et de sélectionner les sources de données pour votre modèle de données de formulaire (FDM). Cette intégration rend tous les objets, propriétés et services de modèle de données provenant des sources sélectionnées disponibles pour une utilisation dans le formulaire, ce qui permet la récupération et l’envoi dynamiques des données.

  ![Source de données](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png)

- **Ajouter**

  Le bouton **Ajouter** affiche une liste déroulante des composants qui peuvent être ajoutés au conteneur actuellement sélectionné. Par exemple, lorsqu’une section de formulaire adaptatif est sélectionnée, cette liste affiche tous les composants qui peuvent être ajoutés à cette section. Le raccourci clavier permettant d’ouvrir cette liste de composants est `a`.

  ![Icône Ajouter](/help/edge/docs/forms/universal-editor/assets/ue-add.png)

- **Dupliquer**

  L’option **Dupliquer** crée une copie exacte du composant sélectionné. Cela vous permet de gagner du temps lorsque vous avez besoin de plusieurs éléments similaires, car vous pouvez dupliquer et modifier au lieu de créer à partir de zéro.

  ![Icône Dupliquer](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png)

- **Supprimer**

  L’option **Supprimer** supprime le composant sélectionné de votre formulaire. Soyez prudent lorsque vous utilisez cette option, car elle supprime immédiatement l’élément sans invite de confirmation.

  ![Supprimer](/help/edge/docs/forms/universal-editor/assets/ue-delete.png)

### Éditeur

L’éditeur est l’espace de travail central dans lequel vous créez et modifiez votre formulaire. Il affiche le formulaire spécifié dans la barre d’emplacement et fournit une expérience WYSIWYG qui montre exactement comment votre formulaire apparaîtra aux utilisateurs. En mode Aperçu , vous pouvez interagir avec le formulaire comme vos utilisateurs le feraient, en testant la navigation à travers les boutons et les liens.

![Éditeur](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

L’éditeur est l’endroit où vous allez passer le plus de temps : vous allez ajouter des composants, configurer leurs propriétés et les organiser pour créer une expérience de formulaire intuitive et efficace.

## Résumé des raccourcis clavier

Pour accroître votre productivité, rappelez-vous ces raccourcis clavier essentiels :

- `l` : sélection de la barre d’emplacement.
- `p` - Basculer entre les modes d’édition et de prévisualisation
- `o` - Ouvrir le formulaire dans un nouvel onglet
- `d` - Ouvrir les propriétés du composant sélectionné
- `f` - Activer/désactiver l’arborescence de contenu
- `a` - Ouvrez la liste des composants à ajouter.



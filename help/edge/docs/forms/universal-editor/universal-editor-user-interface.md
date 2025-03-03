---
title: 'Présentation de l’éditeur universel : tutoriel destiné aux équipes de développement'
description: Ce tutoriel vous permet de vous familiariser avec l’interface de l’éditeur universel. Il permet de comprendre l’interface utilisateur de création de vos propres formulaires Edge Delivery Services dans l’éditeur universel.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: 744f505c8e97b6ca6947b685ddb1eba41b370cfa
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 96%

---

# Exploration de l’interface de l’éditeur universel (WYSIWYG)

L’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) offre une interface What You See Is What You Get (WYSIWYG) simple, visuelle et intuitive pour Adobe Edge Delivery Services Forms. Il fournit une interface moderne et par glisser-déposer pour une création de formulaire efficace.

![Interface utilisateur de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Présentation de l’interface de l’éditeur universel

Lorsque le créateur ou la créatrice du formulaire modifie celui-ci à l’aide de l’éditeur universel, la console ouvre une interface WYSIWYG interactive permettant de modifier le formulaire.

>[!NOTE]
>
> Pour découvrir comment créer des formulaires à l’aide de l’éditeur universel, consultez l’article [Prise en main d’Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel (WYSIWYG)](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

![Interface utilisateur de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

L’interface de l’éditeur universel est divisée en quatre parties :

* **[A : en-tête Experience Cloud](#experience-cloud-header)**
* **[B : barre d’outils de l’éditeur universel](#universal-editor-toolbar)**
* **[C : panneau Propriétés](#properties-panel)**
* **[D : éditeur](#editor)**

### En-tête Experience Cloud

L’en-tête Experience Cloud est présent en haut de la console. Il indique l’emplacement actuel dans Experience Cloud. Il permet également d’accéder à d’autres applications Experience Cloud.

![En-tête Experience Cloud de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)


Comprenons chacun de ses composants.

* **Adobe Experience Cloud**

  Vous pouvez cliquer sur le lien **Adobe Experience Cloud** sur le côté gauche de l’écran pour accéder à la racine de la solution Experience Manager et aux outils tels qu’Experience Manager Sites, Experience Manager Assets et Experience Manager Guides.

  ![Adobe Experience Manager](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager.png){width=50%,height=50%}

* **Nom de l’organisation**

  Le **Nom de l’organisation** affiche le nom de l’organisation IMS dans laquelle la connexion est active. Vous pouvez passer à une autre organisation IMS, si vous avez accès à d’autres organisations, en la sélectionnant dans la liste déroulante. Par exemple, le nom de l’organisation IMS actuellement sélectionnée est `AEM Forms Internal01`.

  ![Organisation](/help/edge/docs/forms/universal-editor/assets/universal-editor-organization.png){width=50%,height=50%}


* **Aide**

  L’icône d’aide permet d’accéder rapidement aux ressources de formation et de support. Le créateur ou la créatrice du formulaire peut également ajouter ses commentaires dans la section **Aide**.
  ![Aide](/help/edge/docs/forms/universal-editor/assets/ue-help.png){width=50%,height=50%}


* **Notifications**

  La section **Notification** indique le nombre de notifications incomplètes actuellement attribuées, les demandes et les tâches actuelles dans l’organisation IMS.

  ![Notification](/help/edge/docs/forms/universal-editor/assets/ue-notification.png){width=50%,height=50%}


* **Solutions**

  Vous pouvez passer à d’autres solutions Experience Cloud à l’aide du lien **Solutions**.
  ![Solutions](/help/edge/docs/forms/universal-editor/assets/ue-solutions.png){width=50%,height=50%}


* **Créteur ou créatrice**
L’icône représente les détails de la personne créatrice du formulaire, ainsi que le nom de l’organisation IMS avec connexion active.
  ![Créateur ou créatrice](/help/edge/docs/forms/universal-editor/assets/ue-author.png){width=50%,height=50%}

### Barre d’outils de l’éditeur universel

La barre d’outils vous permet d’accéder à d’autres formulaires et de les modifier. Elle permet également de publier ou d’annuler la publication du formulaire, d’en modifier les propriétés et d’accéder à l’éditeur de règles.
![Barre d’outils de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

Comprenons chacun de ses composants.

* **Bouton Accueil**
Le bouton Accueil vous permet d’accéder à la page de démarrage de l’éditeur universel. Vous pouvez également saisir directement l’adresse URL du formulaire à modifier à l’aide de l’éditeur universel.
  ![Accueil de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/ue-home.png)



* **Barre d’emplacement**
La **barre d’emplacement** affiche l’adresse du formulaire modifié par le créateur ou la créatrice. Vous pouvez également saisir une autre adresse URL de formulaire en cliquant sur la barre d’emplacement. La touche de raccourci permettant d’ouvrir la barre d’emplacement est `l`.
  ![Barre d’emplacement](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png){width=50%,height=50%}



* **Éditeur de règles**

  L’**Éditeur de règles** offre une interface visuelle intuitive pour la création et la gestion des règles. Vous pouvez ajouter un comportement de formulaire dynamique à l’aide de l’Éditeur de règles.

  ![Éditeur de règles](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

  >[!NOTE]
  >
  > * Dans l’éditeur universel, l’extension Éditeur de règles n’est pas activée par défaut. Pour activer l’extension Éditeur de règles, envoyez-nous un e-mail à l’adresse [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) à partir de votre ID d’e-mail officiel.
  > * Pour découvrir comment créer des règles, reportez-vous à l’article [Présentation de l’éditeur de règles dans la création WYSIWYG](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

* **Modifier les propriétés du formulaire**
Vous pouvez modifier les propriétés du formulaire, telles que le modèle de données du formulaire et la date de publication, en cliquant sur l’option **Modifier les propriétés du formulaire**.
  ![Modifier les propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)



* **Paramètres d’en-tête d’authentification**
Les **paramètres d’en-tête d’authentification** permettent au créateur ou à la créatrice de définir un en-tête d’authentification personnalisé à des fins de développement local.
  ![en-tête d’authentification](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png){width=50%,height=50%}



* **Mode réactif**
  L’option **Mode réactif** permet de définir la manière dont l’éditeur universel effectue le rendu du formulaire. Par défaut, l’éditeur s’ouvre dans une disposition de bureau, où la hauteur et la largeur sont automatiquement déterminées par le navigateur. Vous pouvez également choisir d’émuler un appareil mobile et vérifier l’aspect du formulaire sur les appareils mobiles.

  ![Mode réactif](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png){width=50%,height=50%}


* **Mode Aperçu**
En mode Aperçu , le formulaire s’affiche dans l’éditeur exactement comme il est publié. Cela permet à la personne en charge de la création de parcourir le formulaire en cliquant sur des liens et des boutons. Une fois les modifications apportées, la personne en charge de la création peut publier le formulaire pour les utilisateurs et utilisatrices. La touche de raccourci permettant de basculer entre les modes de modification et d’aperçu est `p`.
  ![Aperçu](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

* **Ouvrir la page**
L’option **Ouvrir la page** ouvre le formulaire dans un nouvel onglet pour l’aperçu. La touche de raccourci permettant d’ouvrir le formulaire en mode Aperçu dans un nouvel onglet est `o`.
  ![Ouvrir la page](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

* **Publier**

  Vous pouvez mettre le formulaire à la disposition des utilisateurs et utilisatrices actifs à l’aide du bouton **Publier**.
  ![Publier](/help/edge/docs/forms/universal-editor/assets/ue-publish.png){width=50%,height=50%}

* **Points de suspension**
Lorsque la personne en charge de la création clique sur les points de suspension (...), l’option **Annuler la publication** s’affiche. Vous pouvez annuler la publication d’un formulaire à l’aide de l’option **Annuler la publication**.
  ![Points de suspension](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png){width=50%,height=50%}

### Panneau Propriétés

Le **Panneau Propriétés** est situé sur le côté droit de l’éditeur. Il affiche les détails du composant sélectionné dans la hiérarchie du formulaire. Il s’agit de la structure par défaut lorsqu’aucun composant n’est sélectionné.
![ue-properties panel](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png){width=50%,height=50%}


Comprenons chacun de ses composants.


* **Mode Propriétés**
L’option **Propriétés** affiche les propriétés du composant sélectionné dans l’éditeur. Par exemple, l’image montre les propriétés du composant d’entrée de nombre sélectionné. Vous pouvez modifier les propriétés du composant à l’aide de cette option. La touche de raccourci permettant d’ouvrir les propriétés du composant est `d`.

  ![ue-properties](/help/edge/docs/forms/universal-editor/assets/ue-properties.png){width=50%,height=50%}


* **Arborescence de contenu**
L’option **Arborescence de contenu** affiche la hiérarchie du formulaire. Lorsque la personne en charge de la création clique sur un élément de l’arborescence de contenu, l’éditeur le sélectionne et fait défiler l’écran jusqu’à ce composant. La touche de raccourci permettant de basculer entre les vues de l’arborescence de contenu est `f`.

  ![Arborescence de contenu](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png){width=50%,height=50%}


* **Générer des variations**
  L’option **Générer des variations** utilise l’intelligence artificielle pour produire différentes versions de formulaires en fonction de prompts spécifiques. Ces prompts peuvent être fournis par Adobe ou conçus et gérés par la personne en charge de la création du formulaire.

  ![variation](/help/edge/docs/forms/universal-editor/assets/ue-variations.png){width=50%,height=50%}


  >[!NOTE]
  >
  > Pour obtenir des instructions sur l’utilisation de l’option Générer des variations pour les formulaires, reportez-vous à l’article [Générer des variations](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/generative-ai/generate-variations).

* **Expérimentation** :

  L’**Expérimentation** fait référence aux techniques utilisées pour tester différentes variations de formulaires et de mises en page afin d’optimiser l’expérience client et les performances.
  ![expérimentation](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png){width=50%,height=50%}


* **Personnalisation**
L’option **Personnalisation** configure les paramètres afin d’établir une connexion entre les formulaires et Adobe Experience Platform (AEP) qui font partie de l’écosystème Adobe ou des applications externes.
  ![Personnalisation](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png){width=50%,height=50%}


* **Tests A/B** :
  Les **Tests A/B** font référence aux techniques utilisées pour tester différentes variations de formulaires et de mises en page afin d’optimiser l’expérience client et les performances.
  ![Tests A/B](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png){width=50%,height=50%}



* **Gestion des tâches** :
La fonctionnalité **Gestion des tâches** vous permet de rationaliser les workflows et de collaborer plus efficacement en permettant aux équipes de gérer, de suivre et d’exécuter des tâches liées à la personnalisation et à l’optimisation des formulaires.
  ![gestion des tâches](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png){width=50%,height=50%}

.
* **Brouillons de contenu**

  L’option **Brouillons de contenu** vous permet de créer des brouillons pour les éléments de texte enrichi. Les brouillons peuvent être créés à l’aide de texte de formulaire existant ou en partant de zéro. Vous pouvez modifier ou supprimer des brouillons selon vos besoins. Par défaut, seuls trois brouillons sont visibles, mais cliquez sur **Tout afficher** pour afficher le reste.

  ![gestion des tâches](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png){width=50%,height=50%}


* **Source de données**

  L’option **Source de données** vous permet de configurer des sources de données et de les sélectionner lors de la création d’un modèle de données de formulaire (FDM). Il met à disposition tous les objets, propriétés et services de modèle de données issus des sources de données sélectionnées dans le modèle de données de formulaire.
  ![Source de données](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png){width=50%,height=50%}

* **Ajouter**

  L’option **Ajouter** ouvre une liste déroulante des composants qui peuvent être ajoutés au conteneur sélectionné. Par exemple, dans une section de formulaire adaptatif, la liste affiche les composants disponibles qui peuvent être ajoutés à un formulaire. La touche de raccourci permettant d’ouvrir la liste des composants est `a`.
  ![Ajouter une icône](/help/edge/docs/forms/universal-editor/assets/ue-add.png){width=50%,height=50%}

* **Dupliquer**

  L’option **Dupliquer** crée une copie du composant sélectionné dans l’arborescence de contenu ou dans l’éditeur.
  ![Icône Dupliquer](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png){width=50%,height=50%}


* **Supprimer**
L’option **Supprimer** permet de supprimer un composant sélectionné dans l’arborescence de contenu ou dans l’éditeur.

  ![Supprimer](/help/edge/docs/forms/universal-editor/assets/ue-delete.png){width=50%,height=50%}

### Éditeur

L’éditeur vous permet de modifier le formulaire. Le rendu du formulaire spécifié dans la barre d’emplacement est effectué dans la zone de modification. Si l’éditeur est en mode Aperçu, vous pouvez parcourir le formulaire à l’aide des boutons et liens disponibles.
![Éditeur](/help/edge/docs/forms/universal-editor/assets/ue-editor.png){width=50%,height=50%}

## Voir également

{{universal-editor-see-also}}

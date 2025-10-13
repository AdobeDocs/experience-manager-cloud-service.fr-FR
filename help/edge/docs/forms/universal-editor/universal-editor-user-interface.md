---
title: Naviguer dans l’interface de l’éditeur universel pour AEM Forms
description: Maîtrisez l’interface de l’éditeur universel pour créer des formulaires AEM avec Edge Delivery Services. Découvrez les outils, raccourcis et workflows essentiels pour créer efficacement des formulaires grâce à ce guide d’interface complet.
keywords: Éditeur universel, formulaires AEM, edge delivery services, guide de l’interface, création de formulaires, éditeur WYSIWYG, outils du créateur de formulaires, navigation dans l’interface d’utilisation
feature: Edge Delivery Services
role: User, Developer, Admin
level: Beginner
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: ht
source-wordcount: '2390'
ht-degree: 100%

---


# Naviguer dans l’interface de l’éditeur universel pour AEM Forms

L’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) fournit une interface visuelle pour créer des formulaires AEM avec Edge Delivery Services. Il offre une expérience **What You See Is What You Get (WYSIWYG)** qui affiche vos formulaires exactement de la manière dont ils apparaîtront aux utilisateurs et utilisatrices.

![Vue d’ensemble de l’interface de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

Ce guide vous aide à comprendre l’interface pour créer efficacement des formulaires. Que vous débutiez dans la création de formulaires ou que vous ayez de l’expérience, ce guide vous aidera avec les éléments suivants :

**Acquérir les compétences essentielles :**

- Naviguer dans l’interface en toute confiance et efficacement
- Utiliser les outils appropriés pour les tâches courantes de création de formulaires
- Utiliser les raccourcis clavier pour augmenter la productivité
- Résoudre les problèmes courants liés à l’interface

**Maîtriser les principaux workflows :**

- Configurer votre espace de travail pour une productivité optimale
- Créer des formulaires du concept à la publication
- Tester et prévisualiser des formulaires sur plusieurs appareils
- Collaborez avec des personnes membres de l’équipe sur des projets de formulaire.



## Prise en main rapide

**Nouveaux utilisateurs et utilisatrices :** commencez par [Outils essentiels](#essential-tools-for-form-building) pour découvrir les fonctionnalités de base que vous utiliserez le plus souvent.

**Utilisateurs et utilisatrices ayant de l’expérience :** accédez à [Fonctionnalités avancées](#advanced-features-and-integrations) pour des outils et des intégrations spécialisés.

**Référence rapide :** utilisez les sections [Vue d’ensemble de l’interface](#interface-overview) et [Raccourcis clavier](#keyboard-shortcuts) pour effectuer des recherches rapides.

>[!NOTE]
>
> Vous débutez dans la création de formulaires ? Consultez [Prise en main d’Edge Delivery Services pour AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) pour obtenir des conseils détaillés sur la création de formulaires.

## Vue d’ensemble de l’interface

L’interface de l’éditeur universel est organisée en quatre zones principales, chacune conçue pour des tâches spécifiques :

![Disposition de l’interface de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

| **Zone** | **Objectif** | **Utilisation principale** |
|----------|-------------|----------------|
| **[A : en-tête Experience Cloud](#experience-cloud-header)** | Navigation et gestion de compte | Basculer entre les outils Adobe, accéder à l’aide, gérer les notifications |
| **[B : barre d’outils de l’éditeur universel](#universal-editor-toolbar)** | Modification et publication de formulaires | Créer, modifier, prévisualiser et publier des formulaires |
| **[C : panneau Propriétés](#properties-panel)** | Configuration du composant | Configurer des champs de formulaire, gérer la structure de contenu, accéder aux fonctionnalités avancées |
| **[D : zone de travail de l’éditeur](#editor-canvas)** | Création de formulaires visuels | Ajouter des composants, organiser la disposition, afficher une prévisualisation en temps réel |

**Flux de l’interface :** la plupart des utilisateurs et utilisatrices travaillent principalement dans les **Zone de travail de l’éditeur** (D) et le **Panneau Propriétés** (C), à l’aide de la **Barre d’outils** (B) pour des actions telles que la prévisualisation et la publication.

## Outils essentiels à la création de formulaires

Commencez ici si vous découvrez l’éditeur universel. Voici les outils principaux que vous utiliserez pour la plupart des tâches de création de formulaires :

### **1. Zone de travail de l’éditeur : votre principal espace de travail**

La **Zone de travail de l’éditeur** permet de créer vos formulaires visuellement. Elle affiche exactement l’apparence que votre formulaire aura pour les utilisateurs et les utilisatrices.

![Zone de travail de l’éditeur](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

**Actions principales :**

- **Ajoutez des composants** en cliquant sur le bouton **Ajouter** dans le panneau Propriétés.
- **Sélectionnez des éléments** en cliquant directement dessus dans la zone de travail.
- **Affichez les modifications en temps réel** lorsque vous configurez des composants.
- **Testez les interactions** en mode Aperçu.

### **2. Panneau Propriétés : configurer des composants**

Le **panneau Propriétés** (côté droit) vous permet de personnaliser les composants sélectionnés et de gérer la structure de votre formulaire.

![Panneau Propriétés](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

**Fonctionnalités essentielles :**

- **Mode Propriétés** (raccourci `d`) : configurez les paramètres du composant sélectionné.
- **Arborescence de contenu** (raccourci `f`) : parcourez la structure du formulaire.
- **Ajouter des composants** (raccourci `a`) : insérez de nouveaux champs de formulaire.
- **Actions des composants** : dupliquez ou supprimez les éléments sélectionnés.

### **3. Éléments essentiels de la barre d’outils : prévisualiser et publier**

La **barre d’outils de l’éditeur universel** fournit des actions clés pour tester et publier vos formulaires.

![Barre d’outils de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

**Outils à connaître :**

- **Mode Aperçu** (raccourci `p`) : testez votre formulaire tel que les utilisateurs et les utilisatrices le verront.
- **Mode réactif** : vérifiez l’apparence de votre formulaire sur les appareils mobiles.
- **Ouvrir la page** (raccourci `o`) : affichez le formulaire dans un nouvel onglet.
- **Publier** : mettez votre formulaire en ligne pour les utilisateurs et utilisatrices.

### **4. Workflow de démarrage rapide**

**Pour votre premier formulaire :**

1. **Ajouter un composant de formulaire adaptatif** : insérez le composant `Adaptive Form` dans une section.
2. **Commencer la création**: ajoutez des composants à l’aide du bouton **Ajouter** (`a`).
3. **Configurer les champs** : sélectionnez les composants et utilisez le **mode Propriétés** (`d`).
4. **Tester le formulaire** : utilisez le **mode Aperçu** (`p`) pour interagir avec le formulaire.
5. **Vérifier la vue mobile** : basculez vers le **mode réactif** pour les tests mobiles.
6. **Mettre en ligne** : cliquez sur **Publier** lorsque vous avez terminé.

>[!NOTE]
>
> Pour connaître les étapes détaillées afin de créer des formulaires dans l’éditeur universel, voir [Créer et publier des formulaires adaptatifs avec Edge Delivery Services](/help/edge/docs/forms/universal-editor/create-forms.md).

**Points de contrôle de validation :**

- Pouvez-vous ajouter et configurer des champs de formulaire ?
- Le mode Aperçu fonctionne-t-il correctement ?
- Tous les champs obligatoires sont-ils correctement configurés ?
- Le formulaire s’affiche-t-il correctement sur les appareils mobiles ?

## En-tête Experience Cloud

L’**en-tête Experience Cloud** fournit des outils de navigation et de gestion de compte. La plupart des créateurs et créatrices de formulaires l’utilisent occasionnellement pour basculer entre les outils Adobe ou accéder à l’aide.

![En-tête Experience Cloud](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)

**Éléments principaux :**

| **Élément** | **Objectif** | **Quand utiliser cette option** |
|-------------|-------------|----------------|
| **Adobe Experience Cloud** | Accéder à d’autres outils Adobe | Basculer entre Sites, Assets et Forms |
| **Organisation** | Basculer entre les organisations | Scénarios d’accès à plusieurs organisations |
| **Aide** | Accéder à la documentation et à l’assistance | Lorsque vous avez besoin de conseils ou souhaitez soumettre des commentaires |
| **Notifications** | Afficher des tâches affectées et des alertes | Vérification du statut du workflow |
| **Solutions** | Accéder rapidement à d’autres solutions Adobe | Passer d’un produit Adobe à l’autre |
| **Profil d’utilisateur ou d’utilisatrice** | Paramétrer le compte et se déconnecter | Gestion du compte ou changement d’utilisateur ou d’utilisatrice |

**Utilisations les plus courantes :**

- **Obtention d’aide** : cliquez sur l’icône Aide pour accéder à la documentation et à l’assistance.
- **Changement d’organisation** : utilisez la liste déroulante des organisations si vous disposez d’un accès multiorganisation.

## Barre d’outils de l’éditeur universel

La **barre d’outils de l’éditeur universel** contient vos outils principaux d’édition et de publication de formulaire. Ils sont organisés par fréquence d’utilisation et par workflow type.

![Barre d’outils de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

### **Outils de workflow quotidiens**

**Ces outils sont utilisés dans la plupart des sessions de création de formulaires :**

#### **Mode Aperçu** (raccourci `p`)

**Objectif :** tester votre formulaire exactement comme les utilisateurs et utilisatrices le verront.\
**Quand utiliser cette option :** avant de publier, après avoir apporté des modifications, pour tester la fonctionnalité de formulaire.

![Mode Aperçu](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

**Bonne pratique :** prévisualisez après chaque modification majeure pour détecter les problèmes rapidement.

#### **Mode réactif**

**Objectif :** vérifier l’affichage de votre formulaire sur les appareils mobiles.\
**Quand utiliser cette option :** après la création de votre formulaire, avant sa publication.

![Mode réactif](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png)

**Bonne pratique :** testez toujours la vue mobile : de nombreux utilisateurs et utilisatrices accéderont aux formulaires sur leurs téléphones.

#### **Ouvrir la page** (raccourci `o`)

**Objectif :** afficher votre formulaire dans un nouvel onglet sans l’interface de l’éditeur.\
**Quand utiliser cette option :** pour les tests en plein écran, partage avec les parties prenantes pour révision.

![Ouvrir la page](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

#### **Publier**

**Objectif :** rendre votre formulaire actif et accessible aux utilisateurs et utilisatrices.\
**Quand utiliser cette option :** après des tests approfondis en modes Aperçu et Réactif.

![Publier](/help/edge/docs/forms/universal-editor/assets/ue-publish.png)

**Liste de contrôle de validation avant publication :**

- Le formulaire a été testé en mode Aperçu.
- La réactivité mobile a été vérifiée.
- Tous les champs obligatoires ont été configurés.
- Les actions Envoyer fonctionnent correctement.

### **Outils de navigation**

#### **Bouton Accueil**

**Objectif :** revenir à la page de démarrage de l’éditeur universel.\
**Quand utiliser cette option :** lorsque vous commencez à travailler sur un autre formulaire.

![Bouton Accueil](/help/edge/docs/forms/universal-editor/assets/ue-home.png)

#### **Barre d’emplacement** (raccourci `l`)

**Objectif :** accéder directement à un formulaire par URL.\
**Quand utiliser cette option :** lorsque vous souhaitez basculer rapidement entre des formulaires spécifiques.

![Barre d’emplacement](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png)

### **Outils de configuration avancée**

**Ces outils sont utilisés pour des scénarios spécifiques ou des configurations avancées :**

#### **Propriétés du formulaire AEM**

**Objectif :** configurer des paramètres au niveau du formulaire tels que le modèle de données de formulaire (FDM) et les dates de publication.\
**Quand utiliser cette option :** lorsque vous configurez des intégrations de données et planifiez la publication.

![Propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)

![Assistant des propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/form-properties-ue.png)

Le panneau Propriétés du formulaire comprend les sections suivantes :

- **Envoi** : définissez ce qui se passe après l’envoi du formulaire par un utilisateur ou une utilisatrice. Faites votre choix parmi plusieurs actions d’envoi, telles que l’envoi de données par e-mail, l’envoi à SharePoint, l’utilisation d’un modèle de données de formulaire ou l’intégration à des services tels qu’Adobe Experience Platform ou Microsoft Power Automate. Pour obtenir la liste complète des actions d’envoi prises en charge, reportez-vous à l’article [Action d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md).

- **Préremplissage** : configurez la manière dont les champs de formulaire sont automatiquement renseignés avant que l’utilisateur ou l’utilisatrice interagisse avec le formulaire. Vous pouvez vous connecter à des sources de données telles qu’un modèle de données de formulaire (FDM) ou utiliser des paramètres d’URL pour préremplir des champs, ce qui améliore l’expérience d’utilisation et réduit la saisie manuelle. Pour en savoir plus, consultez l’article [Service de préremplissage](/help/edge/docs/forms/universal-editor/prefill-form.md).

- **Remerciement** : personnalisez ce que voient les utilisateurs et utilisatrices après l’envoi du formulaire. Vous pouvez afficher un message de confirmation ou les rediriger vers une autre page web, et ainsi garantir une expérience de remplissage fluide et professionnelle. Pour savoir comment configurer un message de remerciement pour les formulaires, consultez l’article [Configurer un message de remerciement](/help/edge/docs/forms/universal-editor/configure-thankyou-message.md).

#### **Éditeur de règles** (accès anticipé)

**Objectif :** ajouter des comportements dynamiques, des validations et une logique conditionnelle.\
**Quand utiliser cette option :** lorsque vous créez des formulaires interactifs avec une logique commerciale complexe.

![Éditeur de règles](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

>[!IMPORTANT]
>
> **Fonctionnalité d’accès anticipé :** l’éditeur de règles nécessite un accès spécial. Pour activer cette fonctionnalité, contactez [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com).
>
> **En savoir plus:** consultez le [Guide de l’éditeur de règles](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) pour obtenir des instructions détaillées.

#### **Paramètres d’en-tête d’authentification**

**Objectif :** définir des en-têtes d’authentification personnalisés pour les tests de développement.\
**Quand utiliser cette option :** lors d’un développement local avec des formulaires nécessitant une authentification.

![En-têtes d’authentification](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png)

#### **Options supplémentaires** (menu représentant des points de suspension)

**Objectif :** accéder aux actions moins courantes telles que la dépublication.\
**Quand utiliser cette option :** mise hors ligne de formulaires, accès aux options avancées.

![Options supplémentaires](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png)

## Panneau Propriétés

Le **Panneau Propriétés** (côté droit) est votre centre de contrôle pour la création et la configuration de formulaires. Il change en fonction de ce que vous sélectionnez et fournit différents outils pour diverses tâches.

![Panneau Propriétés](/help/edge/docs/forms/universal-editor/assets/text-properties-ue.png)

### **Principaux outils de création de formulaires**

**Ces outils sont essentiels pour créer et organiser vos formulaires :**

#### **Ajouter des composants** (raccourci `a`)

**Objectif :** insérer de nouveaux champs et éléments de formulaire.\
**Fonctionnement :** affiche les composants disponibles pour le conteneur sélectionné.

![Ajouter des composants](/help/edge/docs/forms/universal-editor/assets/ue-add.png)

**Composants courants :**

- Champs Entrée de texte, E-mail, Téléphone
- Liste déroulante, boutons radio, cases à cocher
- Chargement de fichier, sélecteur de date
- Panneaux et sections pour l’organisation

#### **Mode Propriétés** (raccourci `d`)

**Objectif :** configurer les paramètres des composants sélectionnés.\
**Quand utiliser cette option :** après l’ajout d’un composant pour personnaliser son comportement.

![Mode Propriétés](/help/edge/docs/forms/universal-editor/assets/ue-properties.png)

**Paramètres clés :**

- Libellés de champ et texte d’espace réservé
- Règles de validation (obligatoire, format, longueur)
- Valeurs par défaut et texte d’aide
- Règles de visibilité conditionnelles

#### **Arborescence de contenu** (raccourci `f`)

**Objectif :** parcourir et organiser la structure de votre formulaire.\
**Quand utiliser cette option :** pour les formulaires complexes comportant plusieurs sections, la recherche de composants spécifiques.

![Arborescence de contenu](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png)

**Avantages :**

- Navigation rapide vers un composant
- Hiérarchie visuelle des formulaires
- Réorganisation facile des éléments

#### **Actions des composants**

**Objectif :** gérer les composants existants.\
**Actions disponibles :**

- **Dupliquer** : copier rapidement les composants ![Dupliquer](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png)
- **Supprimer** : supprimer les composants (pas d’invite de confirmation) ![Supprimer](/help/edge/docs/forms/universal-editor/assets/ue-delete.png)

### **Fonctionnalités et intégrations avancées**

**Ces outils offrent des fonctionnalités de formulaire sophistiquées :**

+++Intégration de données

#### **Source de données**

**Objectif :** connecter des formulaires aux systèmes de données principaux.\
**Quand utiliser cette option :** pour les formulaires qui doivent être en lecture/écriture dans des bases de données ou des services externes.

![Source de données](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png)

**Fonctionnalités :**

- Configuration du modèle de données de formulaire (FDM)
- Population de données dynamique
- Envoi à des systèmes externes

+++

+++Outils optimisés par l’IA

#### **Générer des variations**

**Objectif :** utiliser l’IA pour créer différentes versions du contenu du formulaire.\
**Quand utiliser cette option :** lorsque vous testez différents textes et différentes mises en page ou approches.

    .[Générer des variations](/help/edge/docs/forms/universal-editor/assets/ue-variations.png)

**En savoir plus :** [Guide de génération des variations](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/generative-ai/generate-variations)

#### **Brouillons de contenu**

**Objectif :** créer et enregistrer des versions préliminaires de texte.\
**Quand utiliser cette option :** itération sur une copie de formulaire, enregistrement des options de texte secondaire.

![Brouillons de contenu](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png)

+++

+++Tests et optimisation

#### **Tests A/B**

**Objectif :** comparer des variations de formulaire pour optimiser les performances.\
**Quand utiliser cette option :** optimisation des taux de conversion, test de différentes conceptions.

![Tests A/B](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png)

#### **Expérimentation**

**Objectif :** exécuter des tests contrôlés sur les conceptions de formulaire.\
**Quand utiliser cette option :** optimisation des formulaires pilotés par les données, test de l’expérience d’utilisation.

    .[Expérimentation](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png)

+++

+++Outils de collaboration

#### **Gestion des tâches**

**Objectif :** organiser le workflow de l’équipe pour les projets de formulaire.\
**Quand utiliser cette option :** développement de formulaires pour plusieurs personnes, suivi de projet.

![Gestion des tâches](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png)

#### **Personnalisation**

**Objectif :** se connecter à Adobe Experience Platform pour des expériences personnalisées.\
**Quand utiliser cette option :** création de formulaires personnalisés basés sur des données d’utilisation.

    .[Personnalisation](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png)

+++

## Zone de travail de l’éditeur

La **zone de travail de l’éditeur** est votre espace de travail principal dans lequel vous créez visuellement des formulaires. Elle affiche exactement l’apparence que votre formulaire aura auprès des utilisateurs et utilisatrices et fournit des commentaires en temps réel au fur et à mesure que vous apportez des modifications.

![Zone de travail de l’éditeur](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

**Fonctions clés :**

- **Modification WYSIWYG** : voyez immédiatement les modifications au fur et à mesure que vous les apportez.
- **Interaction directe** : cliquez sur un composant pour le sélectionner et le modifier.
- **Prévisualisation en temps réel** : basculez vers le mode Aperçu pour tester la fonctionnalité.
- **Affichage réactif** : activez/désactivez les vues d’appareil pour vérifier la compatibilité mobile.

**Bonnes pratiques :**

- **Commencer par la structure** : ajoutez les sections principales avant les composants détaillés.
- **Tester fréquemment** : utilisez régulièrement le mode Aperçu pour détecter les problèmes rapidement.
- **Penser d’abord à la version mobile** : cochez le mode réactif tout au long du processus de conception.

## Raccourcis clavier

Maîtrisez ces raccourcis pour créer des formulaires plus rapidement et plus efficacement :

| **Raccourci** | **Action** | **Quand l’utiliser** |
|--------------|------------|----------------|
| `a` | Ouvrir la liste des composants | Ajout de nouveaux champs de formulaire |
| `d` | Ouvrir les propriétés du composant | Configuration des éléments sélectionnés |
| `f` | Activer/désactiver l’arborescence de contenu | Navigation dans des formulaires complexes |
| `p` | Activer/désactiver le mode Aperçu | Test de la fonctionnalité de formulaire |
| `o` | Ouvrir le formulaire dans un nouvel onglet | Tests en plein écran |
| `l` | Mettre le focus sur la barre d’emplacement | Basculement vers des formulaires différents |

**Conseil de pro :** utilisez ces raccourcis en les combinant ; par exemple, sélectionnez un composant, appuyez sur `d` pour le configurer, puis `p` pour tester les modifications.

## Workflows courants

### **Création de votre premier formulaire**

1. **Ajouter la structure** : utilisez `a` pour ajouter un panneau pour les sections de formulaire.
2. **Ajouter des champs** : insérez un champ d’entrée de texte, un e-mail et d’autres composants.
3. **Configurer les propriétés** : sélectionnez chaque champ et appuyez sur `d` pour définir les libellés et la validation.
4. **Tester la fonctionnalité** : appuyez sur `p` pour prévisualiser et tester le formulaire.
5. **Vérifier la vue mobile** : utilisez le mode réactif pour vérifier l’affichage mobile.
6. **Publier** : cliquez sur Publier lorsque vous souhaitez mettre en ligne.

### **Modification des formulaires existants**

1. **Naviguer dans la structure** : utilisez l’arborescence de contenu (`f`) pour rechercher rapidement des composants.
2. **Sélectionner et modifier** : cliquez directement sur les composants ou utilisez l’arborescence de contenu.
3. **Tester les modifications** : prévisualisez (`p`) après chaque modification significative.
4. **Valider le workflow** : testez le flux de formulaire complet avant la republication.

### **Collaboration avec des équipes**

1. **Utiliser la gestion des tâches** : attribuez des sections de formulaire spécifiques aux personnes membres de l’équipe.
2. **Partager pour révision** : utilisez Ouvrir la page (`o`) pour partager des prévisualisations claires.
3. **Tester ensemble** : utilisez le mode Aperçu pour les sessions de test collaboratives.
4. **Suivre la progression** : consultez les notifications des mises à jour de tâches.

## Résolution des problèmes courants

### **Problèmes d’interface**

+++Les éléments de l’interface ne se chargent pas

**Problème :** les boutons de la barre d’outils, le panneau Propriétés ou d’autres éléments d’interface n’apparaissent pas.

**Solutions :**

- **Actualiser la page** : une simple actualisation du navigateur résout souvent les problèmes de chargement.
- **Vérifier la compatibilité du navigateur** : utilisez Chrome, Firefox ou Safari.
- **Effacer la mémoire cache du navigateur** : supprimez les fichiers mis en cache qui peuvent être obsolètes.
- **Vérifier les autorisations** : assurez-vous que vous disposez d’un accès approprié pour modifier les formulaires.

+++

+++Les composants ne répondent pas

**Problème :** impossible de sélectionner les composants ou le panneau Propriétés ne se met pas à jour.

**Solutions :**

- **Cliquer directement sur les composants** : évitez de cliquer sur des zones vides.
- **Utiliser l’arborescence de contenu** : appuyez sur `f` et sélectionnez les composants dans l’arborescence.
- **Rechercher les éléments qui se chevauchent** : certains composants peuvent en bloquer d’autres.
- **Recharger le formulaire** : utilisez la barre d’emplacement (`l`) pour recharger le formulaire actif.

+++

+++Problèmes du mode Aperçu

**Problème :** le mode Aperçu ne fonctionne pas correctement ou affiche des erreurs.

**Solutions :**

- **Vérifier la validation du formulaire** : assurez-vous que tous les champs obligatoires sont correctement configurés.
- **Tester d’abord en mode modification** : vérifiez que les composants fonctionnent avant de les prévisualiser.
- **Effacer la mémoire cache du navigateur** : les scripts mis en cache peuvent interférer avec la prévisualisation.
- **Vérifier la configuration du composant** : examinez les paramètres du mode Propriétés pour identifier les erreurs.

+++

## Bonnes pratiques pour créer efficacement des formulaires

### **Conseils d’organisation**

- **Utiliser des noms descriptifs** : étiquetez les composants clairement en mode Propriétés.
- **Regrouper les champs associés** : utilisez les panneaux pour organiser logiquement les sections de formulaire.
- **Planifier avant de créer** : esquissez la structure du formulaire avant de commencer.
- **Faire simple** : évitez de submerger les utilisateurs et utilisatrices avec trop de champs.

### **Expérience clientèle**

- **Tester fréquemment** : utilisez le mode Aperçu après chaque modification majeure.
- **Penser comme les utilisateurs et utilisatrices** : tenez compte de l’expérience de remplissage complète du formulaire.
- **Fournir des libellés clairs** : rendez les fonctions de champ évidentes pour les utilisateurs et les utilisatrices.
- **Ajouter du texte utile** : utilisez du texte d’aide pour les champs complexes.

### **Optimisation des performances**

- **Réduire les composants** : utilisez uniquement les champs de formulaire nécessaires.
- **Optimiser les images** : compressez les images utilisées dans les formulaires.
- **Tester sur mobile** : garantissez de bonnes performances sur les connexions mobiles plus lentes.
- **Valider de manière anticipée** : configurez une validation appropriée pour éviter les erreurs d’envoi.

## Étapes suivantes

Maintenant que vous connaissez l’interface de l’éditeur universel, procédez comme suit :

1. **S’exercer avec un formulaire simple** : commencez par les champs de base pour vous familiariser.
2. **Explorer les fonctionnalités avancées** : essayez les outils et intégrations optimisés par l’IA lorsque vous êtes prêt ou prête.
3. **Découvrir la création de formulaires** :consultez le [Guide de prise en main](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).
4. **Maîtriser l’éditeur de règles** : ajoutez des comportements dynamiques avec le [Guide de l’éditeur de règles](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

**À retenir** : l’éditeur universel est conçu pour rendre la création de formulaires intuitive. Commencez par les éléments essentiels et explorez progressivement les fonctionnalités avancées à mesure que vos besoins évoluent.

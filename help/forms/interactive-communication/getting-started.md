---
title: Prise en main de l’éditeur de communication interactive (IC)
description: La communication interactive permet aux entreprises de concevoir et de diffuser des communications personnalisées basées sur les données.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: d24e88b545a17e50c1e80e1aedbb1d0adf55f609
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 12%

---


# Prise en main de l’éditeur de communication interactive (IC)

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

L’**éditeur de communication interactive (IC)** de Adobe Experience Manager (AEM) Forms permet aux entreprises de concevoir et de diffuser des communications personnalisées basées sur les données, telles que des relevés, des factures et des courriers sur les canaux numériques et d’impression. Ce guide présente un aperçu de la prise en main, de l’intégration à la navigation dans l’interface d’IC Editor.


## Intégration et accès

### Conditions d’accès

Pour utiliser la communication interactive, assurez-vous que votre environnement AEM Forms as a Cloud Service inclut le module complémentaire **AEM Forms** et que votre compte dispose des autorisations appropriées.

### Vérification du navigateur

Pour connaître les navigateurs et les plateformes clientes pris en charge, consultez l’article associé [Plateformes clientes prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/overview/supported-platforms)

>[!NOTE]
>
> **Prise en charge des navigateurs avec des cycles de version rapides :**
> Firefox, Chrome et Edge publient régulièrement des mises à jour. Adobe s’engage à maintenir le niveau de prise en charge comme indiqué ci-dessus pour les versions ultérieures de ces navigateurs.

### Configuration des rôles utilisateur et des autorisations

L’accès aux fonctionnalités de l’éditeur IC est régi par [rôles utilisateur dans AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions). Les principaux rôles impliqués dans la création et la gestion des communications interactives sont les suivants :

| **Rôle** | **Description** | **Autorisations clés** |
| --------------------- | ---------------------------------------------------------- | -------------------------------------------- |
| **Auteur du formulaire** | Crée et modifie des communications interactives. | Créer, modifier, prévisualiser et publier des CI. |
| **Créateur de modèles** | Conçoit des modèles réutilisables pour les communications interactives. | Créer et verrouiller des modèles, définir des mises en page. |
| **Administrateur** | Gère l’accès utilisateur, les autorisations et les configurations. | Attribuez des rôles, gérez des modèles et publiez des ID. |
| **Auteur FDM** | [Crée et gère des modèles de données de formulaire (FDM)](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/create-form-data-models) pour l’intégration de données. | Créer, modifier et configurer des sources de données et des modèles. |

>[!NOTE]
>
> Assurez-vous que les utilisateurs font partie des groupes AEM appropriés (par exemple, `forms-user`, `fdm-author`, `template-authors`) pour accéder aux fonctionnalités correspondantes.

## Accès à l’éditeur IC

1. Connectez-vous à votre instance **AEM Forms as a Cloud Service**.
2. Accédez à **Forms > Communications interactives**.
3. Cliquez sur **Créer** → **Communication interactive**.
4. Choisissez un **Modèle**, configurez les sources de données, puis cliquez sur **Créer** pour ouvrir l’**Éditeur de communication interactive**.

L’éditeur fournit un environnement unifié pour concevoir, prévisualiser et gérer les versions imprimées et web des communications.

## Navigation dans l’interface

L’interface **Éditeur de communication interactive** est conçue pour donner aux auteurs un accès intuitif à tous les outils de conception et options de configuration.

![Rechercher un document IC](/help/forms/interactive-communication/assets/navigate-the-interface.png)

### &#x200B;1. Barre d’outils supérieure

![Rechercher un document IC](/help/forms/interactive-communication/assets/tool-bar.png)

**Emplacement :** la section la plus élevée

**Objectif :** fournit un accès à l’environnement et des actions globales.

**Inclut :**

Affiche l’environnement **Adobe Experience Cloud** (par exemple, Évaluation), ainsi que le **titre du projet**, les **commentaires Beta**, les **notifications** et les **contrôles de profil** pour gérer les paramètres utilisateur et l’accès à l’environnement.

### &#x200B;2. Barre d&#39;onglets (onglets Conception/Principal et commandes de fichier)

![Rechercher un document IC](/help/forms/interactive-communication/assets/tab-bar.png)

**Emplacement :** sous l’en-tête supérieur

**Objectif :** gérer les vues et les fichiers de communication.

**Inclut :**

**Onglets :** basculer entre le **mode Création** et le **mode Principal Page** pour la mise en page et la conception d’éléments réutilisables

**Nom de fichier :** affiche le titre de la communication actuelle (par exemple, ic-11)

**Afficher les contrôles :** options telles que règle, création, Zoom (85 %), Annuler/rétablir, Supprimer, Aperçu PDF et Enregistrer

### &#x200B;3. Panneau De Gauche (Navigation Et Outils De Composants)

![Rechercher un document IC](/help/forms/interactive-communication/assets/left-panel.png)

**Emplacement :** côté gauche de l’interface

**Objectif :** accéder à la structure du projet, aux ressources réutilisables et aux liaisons de données.

**Inclut :**

* **Page d’accueil :** dirige l’utilisateur vers l’écran d’accueil principal de la communication interactive (CI), où vous pouvez afficher et gérer les CI et dossiers existants.

* **Panneau de menu :** affiche les options de vue telles que les règles, les limites d’objet, l’alignement sur la grille, l’alignement sur l’objet de la fonction et la fonction d’importation XDP.

* **Vue Hiérarchie :** affiche la structure des composants de la communication, en indiquant l’organisation des pages, des panneaux et des sous-formulaires.

* **Bibliothèque de composants :** contient des éléments de conception tels que du texte, une image, un sous-formulaire et un code-barres qui peuvent être déplacés sur la zone de travail.

* **Fragments :** permet la réutilisation de blocs de conception et de contenu prédéfinis dans plusieurs communications.

* **Modèle de données :** connecte la communication aux modèles de données de formulaire (FDM) sous-jacents pour lier les données dynamiques.

### &#x200B;4. Central Workspace (Zone De Travail De Conception)

![Rechercher un document IC](/help/forms/interactive-communication/assets/canvas.png)

**Emplacement :** centre de l’interface

**Objectif :** espace de travail de Principal pour la conception de communications interactives.

**Fonctionnalités :**

* Glisser-déposer des composants depuis la bibliothèque

* Organiser et formater la disposition visuelle

* Ajouter ou modifier des pages, des sous-formulaires et des champs

* Naviguez entre les pages (par exemple, « 1 sur 1 ») à l’aide des commandes en bas à gauche

* Prévisualiser la mise en page finale avant publication

### &#x200B;5. Panneau de droite (panneau Propriétés)

![Rechercher un document IC](/help/forms/interactive-communication/assets/right-panel.png)

**Emplacement :** côté droit de l’écran

**Objectif :** personnaliser le comportement et le style des composants.

**Inclut :**

* Paramètres généraux (nom, type, distribué/positionné)

* Options de disposition et d’aspect

* Contrôles de pagination, de position, de présence et de liaison de données
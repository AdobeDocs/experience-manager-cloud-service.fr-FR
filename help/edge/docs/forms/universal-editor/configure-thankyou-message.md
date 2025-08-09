---
title: Comment configurer une page de redirection ou un message de remerciement
description: Découvrez comment les utilisateurs et utilisatrices peuvent voir affiché un message de remerciement ou être redirigés vers une page web que les personnes chargées de la création de formulaires peuvent configurer lors de la phase de création.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '1682'
ht-degree: 40%

---


# Configuration des messages de remerciement et des URL de redirection

Les fragments de formulaire sont des composants réutilisables qui éliminent le travail de développement répétitif et assurent la cohérence entre les formulaires de votre entreprise. Au lieu de recréer des sections courantes telles que les informations de contact, les détails d’adresse ou les accords de consentement pour chaque formulaire, vous pouvez créer ces éléments une fois sous forme de fragments et les réutiliser dans plusieurs formulaires.

**Ce que vous accomplirez dans cet article**

- Comprendre la valeur commerciale et les fonctionnalités techniques des fragments de formulaire
- Créer des fragments de formulaire réutilisables à l’aide de l’éditeur universel
- Intégration de fragments dans des formulaires existants avec la configuration appropriée
- Gérer le cycle de vie des fragments et maintenir la cohérence entre les formulaires

**Avantages commerciaux :**

- **Temps de développement réduit** : créez des sections de formulaire communes une fois, réutilisez-les partout.
- **Amélioration de la cohérence** : dispositions et contenu normalisés dans tous les formulaires
- **Maintenance simplifiée** : mettez à jour un fragment une seule fois pour refléter les modifications dans tous les formulaires qui l’utilisent
- **Conformité améliorée** : assurez-vous que les sections réglementaires restent cohérentes et à jour

Les fragments de formulaire dans Edge Delivery Services prennent en charge des fonctionnalités avancées, notamment des fragments imbriqués, plusieurs instances au sein d’un seul formulaire et une intégration transparente aux sources de données.

## Comprendre les fragments de formulaire

Les fragments de formulaire dans Edge Delivery Services offrent de puissantes fonctionnalités pour le développement de formulaires modulaires :

**Fonctionnalités principales :**

- **Gestion de cohérence** : les fragments conservent des dispositions et un contenu identiques dans plusieurs formulaires. Grâce à l’approche « Modifier une fois, refléter partout », les mises à jour d’un fragment s’appliquent automatiquement à tous les formulaires en mode Aperçu.
- **Utilisation multiple** : ajoutez le même fragment plusieurs fois dans un seul formulaire, chacun avec des données indépendantes se liant à différentes sources de données ou éléments de schéma.
- **Structures imbriquées** : créez des hiérarchies complexes en incorporant des fragments dans d’autres fragments pour des architectures de formulaire sophistiquées.

**Exigences techniques :**

- **Cohérence d’URL GitHub** : le fragment et tout formulaire l’utilisant doivent spécifier la même URL de référentiel GitHub
- **Modification autonome** : les fragments ne peuvent être modifiés que dans leur formulaire autonome ; les modifications ne peuvent pas être apportées dans le formulaire hôte

**Comportement de la publication :**

>[!IMPORTANT]
>
>En mode Aperçu , les modifications de fragment sont immédiatement répercutées sur tous les formulaires. En mode de publication, vous devez republier le fragment et les formulaires qui l’utilisent pour afficher les mises à jour.

>[!CAUTION]
>
>Évitez les références de fragment récursives (imbrication d’un fragment dans lui-même), car cela entraîne des erreurs de rendu et un comportement inattendu.

## Prérequis

**Exigences en matière de configuration technique :**

- [Référentiel GitHub configuré](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) avec une connexion établie entre votre environnement AEM et le référentiel GitHub
- [Dernier bloc de Forms adaptatif](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) ajouté à votre référentiel GitHub (pour les projets Edge Delivery Services existants)
- Instance d’auteur AEM Forms avec modèle Edge Delivery Services disponible
- Accès à l’URL de votre instance d’auteur AEM Forms as a Cloud Service et à l’URL du référentiel GitHub

**Connaissances et autorisations requises :**

- Compréhension de base des concepts de conception de formulaire et de la hiérarchie des composants
- Familiarité avec l’interface de l’éditeur universel et les workflows de création de formulaires
- Autorisations au niveau de l’auteur dans AEM Forms pour créer et gérer des ressources de formulaire
- Compréhension des normes de formulaire de votre entreprise et des exigences en matière de composants réutilisables

## Utilisation de fragments de formulaire Edge Delivery Services

Vous pouvez créer des fragments de formulaire Edge Delivery Services dans l’éditeur universel et ajouter les fragments créés aux formulaires Edge Delivery Services. Vous pouvez effectuer les actions suivantes avec les fragments de formulaire Edge Delivery Services :

- [Création de fragments de formulaire](#creating-form-fragments)
- [Ajout de fragments de formulaire à un formulaire](#adding-form-fragments-to-a-form)
- [Gestion de fragments de formulaire](#managing-form-fragments)

+++ Création de fragments de formulaire

Pour créer un fragment de formulaire dans l’éditeur universel, procédez comme suit :

1. Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Cliquez sur **Créer > Fragment de formulaire adaptatif**.

   ![Création d’un fragment](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   L’assistant **Créer un fragment de formulaire adaptatif** s’affiche.
1. Sélectionnez le modèle basé sur Egde Delivery Services dans l’onglet **Sélectionner le modèle** et cliquez sur **[!UICONTROL Suivant]**.
   ![Sélection de modèle Edge Delivery Services](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. Indiquez le titre, le nom, la description et les balises du fragment. Assurez-vous de spécifier un nom unique pour le fragment. S’il existe déjà un autre fragment portant le même nom, la création du fragment échoue.
1. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, l’URL est `https://github.com/wkndforms/edsforms`.

   ![Propriétés de base](/help/edge/docs/forms/universal-editor/assets/fragment-basic-properties.png)

1. (Facultatif) Cliquez pour ouvrir l’onglet **Modèle de formulaire**, puis dans le menu déroulant **Choisir parmi**, sélectionnez l’un des modèles de fragment suivants :

   ![Affichage du type de modèle dans l’onglet Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/select-fdm-for-fragment.png)

   - **Modèle de données de formulaire (FDM)** : intégrez des objets et des services de modèle de données provenant de sources de données dans votre fragment. Choisissez le modèle de données de formulaire (FDM) si votre formulaire nécessite la lecture et l’écriture de données provenant de plusieurs sources.

   - **Schéma JSON** : intégrez votre formulaire à un système back-end en associant un schéma JSON qui définit la structure des données. Cela vous permet d’ajouter du contenu dynamique à l’aide des éléments de schéma.
   - **Aucun** : indique que le fragment doit être créé de zéro sans utiliser de modèle de formulaire.

   >[!NOTE]
   >
   > Pour savoir comment intégrer des formulaires ou des fragments à un modèle de données de formulaire (FDM) dans l’éditeur universel afin d’utiliser diverses sources de données principales, consultez [Intégration de formulaires à un modèle de données de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

1. (Facultatif) Spécifiez la **Date de publication** ou la **Date de dépublication** du fragment dans l’onglet **Avancé**.

   ![Onglet avancé](/help/edge/docs/forms/universal-editor/assets/advanced-properties-fragment.png)
1. Cliquez sur **Créer** pour générer le fragment. Une boîte de dialogue de réussite s’affiche avec les options de modification.

   ![Modification de fragment](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. Cliquez sur **Modifier** pour ouvrir le fragment dans l’éditeur universel avec le modèle par défaut appliqué.

   ![Fragment dans l’éditeur universel pour la création](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

1. **Concevoir le contenu de votre fragment** : ajoutez des composants de formulaire (champs de texte, listes déroulantes, cases à cocher) pour créer la section réutilisable. Pour obtenir des conseils détaillés sur les composants, voir [Prise en main de Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

1. **Configurer les propriétés du composant** : définissez les noms de champ, les règles de validation et les valeurs par défaut en fonction de votre cas d’utilisation.

1. **Enregistrer et prévisualiser** : enregistrez votre fragment et utilisez le mode Prévisualisation pour vérifier la disposition et la fonctionnalité.

   ![Copie d’écran d’un fragment de formulaire de coordonnées terminé dans l’éditeur universel, affichant les champs Nom, Téléphone, E-mail et Adresse qui peuvent être réutilisés dans plusieurs formulaires.](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

**Point de contrôle de validation :**

- Le fragment se charge sans erreur dans l’éditeur universel.
- Tous les composants de formulaire s’affichent correctement
- Les propriétés des champs et les règles de validation fonctionnent comme prévu
- Le fragment est enregistré et disponible dans la console Forms et documents

Une fois votre fragment terminé, vous pouvez l’intégrer [dans n’importe quel formulaire Edge Delivery Services](#adding-form-fragments-to-a-form).

+++


+++ Ajout de fragments de formulaire à un formulaire

Cet exemple illustre la création d&#39;un formulaire `Employee Details` qui utilise le fragment de `Contact Details` pour les sections d&#39;informations employé et superviseur. Cette approche garantit la cohérence de la collecte de données tout en réduisant les efforts de développement.

Pour intégrer un fragment de formulaire dans votre formulaire :

1. Ouvrez le formulaire en mode d’édition.
1. Ajoutez le composant Fragment de formulaire au formulaire.
1. Ouvrez l’explorateur de contenu et accédez au composant **[!UICONTROL Formulaire adaptatif]** dans l’**arborescence de contenu**.
1. Accédez à la section dans laquelle vous avez l’intention d’ajouter un fragment. Par exemple, accédez au panneau **Détails de la personne employée**.

   ![Accès à la section](/help/edge/docs/forms/universal-editor/assets/navigate-to-section.png)

1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez le composant **[!UICONTROL Fragment de formulaire]** dans la liste **Composants de formulaire adaptatif**.
   ![Ajout d’un fragment de formulaire](/help/edge/docs/forms/universal-editor/assets/add-fragment.png)

   Lorsque vous sélectionnez le composant **[!UICONTROL Fragment de formulaire]**, le fragment est ajouté à votre formulaire. Vous pouvez configurer les propriétés du fragment ajouté en ouvrant ses **Propriétés**. Par exemple, masquez le titre du fragment à partir de ses **Propriétés**.

   ![Configuration des propriétés du fragment](/help/edge/docs/forms/universal-editor/assets/fragment-properties.png)

1. Sélectionnez la **Référence de fragment** dans l’onglet **De base**. Tous les fragments de formulaires disponibles pour votre formulaire, selon le modèle du formulaire, s’affichent.

   Par exemple, accédez à `/content/forms/af` et sélectionnez le fragment `Contact Details`.

   ![Sélection d’un fragment](/help/edge/docs/forms/universal-editor/assets/select-fragment.png)

1. Cliquez sur **[!UICONTROL Sélectionner]**.

   Le fragment de formulaire est ajouté par référence au formulaire et reste synchronisé avec le fragment de formulaire autonome.

   ![Capture d’écran montrant le fragment relatif aux coordonnées, intégré au formulaire des effectifs d’une entreprise dans l’éditeur universel, présentant la façon dont les fragments conservent leur structure lorsqu’ils sont réutilisés](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   Vous pouvez prévisualiser le formulaire pour découvrir comment il s’affiche en mode **Prévisualisation**.

   ![Prévisualisation](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   De même, vous pouvez répéter les étapes 3 à 7 pour insérer le fragment `Contact Details` pour le panneau `Supervisor Details`.

   ![Formulaire Détails de l&#39;employé](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

+++



+++ Gestion de fragments de formulaire

Vous pouvez effectuer plusieurs opérations sur des fragments de formulaire depuis l’interface d’utilisation d’AEM Forms.

1. Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

1. Sélectionnez un fragment de formulaire et la barre d’outils affiche les opérations suivantes que vous pouvez effectuer sur le fragment sélectionné.

   ![Gestion du fragment](/help/edge/docs/forms/universal-editor/assets/manage-fragment.png)

   <table>
    <tbody>
    <tr>
   <td><p><strong>Opération</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
    </tr>
    <tr>
   <td><p>Modifier</p> </td>
   <td><p>Ouvre le fragment de formulaire en mode d’édition.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Propriétés</p> </td>
   <td><p>Fournit des options pour modifier les propriétés du fragment de formulaire.<br /> <br /> </p> </td>
    </tr>
    <td><p>Copier</p> </td>
   <td><p> Fournit des options pour copier le fragment de formulaire et le coller à l’emplacement souhaité. <br /> <br /> </p> </td>
    </tr>
   <tr>
   <td><p>Prévisualisation</p> </td>
   <td><p>Fournit des options de prévisualisation du fragment en HTML ou une prévisualisation personnalisée en fusionnant les données d’un fichier XML avec le fragment. <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Téléchargement</p> </td>
   <td><p>Télécharge le fragment sélectionné.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Démarrer la révision/Gérer la révision</p> </td>
   <td><p>Permet de lancer et de gérer la révision du fragment sélectionné.<br /> <br /> </p> </td>
    </tr>
    <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
    </tr>-->
    <tr>
   <td><p>Publier/Dépublier</p> </td>
   <td><p>Publie/annule la publication du fragment sélectionné.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Supprimer</p> </td>
   <td><p>Supprime le fragment sélectionné.<br /> <br /> </p> </td>
    </tr>
    <tr>
   <td><p>Comparer</p> </td>
   <td><p>Compare deux fragments de formulaire différents à des fins de prévisualisation.<br /> <br /> </p> </td>
    </tr>
    </tbody>
    </table>

+++

## Bonnes pratiques

**Conception de fragment et dénomination :**

- **Utiliser des noms descriptifs et uniques** : choisissez des noms qui indiquent clairement l’objectif du fragment (par exemple, « contact-details-with-validation » plutôt que « fragment1 »)
- **Planifier la réutilisation** : concevez les fragments de manière à ce qu’ils soient indépendants du contexte et fonctionnent ainsi sur différents types de formulaires
- **Garder les fragments concentrés** : créez des fragments à usage unique plutôt que des composants complexes et multifonctions

**Workflow de développement :**

- **Tester les fragments indépendamment** : vérifiez la fonctionnalité de fragment avant de l’intégrer aux formulaires
- **Maintenir la cohérence des URL GitHub** : assurez-vous que la même URL de référentiel est utilisée sur tous les fragments et formulaires associés
- **Objectif du fragment de document** : incluez des descriptions et des balises claires pour aider les membres de l’équipe à comprendre quand utiliser chaque fragment

**Publication et maintenance :**

- **Coordonner la publication** : lors de la mise à jour des fragments, prévoyez de republier simultanément tous les formulaires dépendants
- **Gestion de version** : utilisez des messages de validation significatifs lors de la mise à jour des fragments pour suivre les modifications au fil du temps
- **Surveiller les dépendances** : suivez les formulaires qui utilisent chaque fragment pour évaluer l’impact de la mise à jour

>[!TIP]
>
>Les styles, scripts et expressions de fragment sont conservés lorsqu’ils sont incorporés. Concevez donc avec cet héritage à l’esprit.

## Résumé

Vous avez appris à exploiter les fragments de formulaire dans Edge Delivery Services pour améliorer l’efficacité du développement et maintenir la cohérence entre les formulaires de votre entreprise.

**Principales réalisations :**

- **Présentation** : compréhension de la valeur commerciale et des fonctionnalités techniques des fragments de formulaire.
- **Création** : création de fragments de formulaire réutilisables à l’aide de l’éditeur universel avec la configuration appropriée
- **Intégration** : ajout de fragments aux formulaires avec une configuration de référence et de propriété correcte
- **Gestion** : opérations et workflows de maintenance relatifs au cycle de vie des fragments explorés

**Étapes suivantes :**

- Créez une bibliothèque de fragments couramment utilisés pour votre organisation
- Définir des conventions de nommage et des politiques de gouvernance pour l’utilisation des fragments
- Explorez une intégration avancée avec les [modèles de données de formulaire](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) pour les fragments dynamiques pilotés par les données
- Implémenter des modèles de formulaire basés sur des fragments pour des expériences utilisateur cohérentes

Vos formulaires bénéficient désormais d’une architecture modulaire et gérable qui s’adapte efficacement à l’ensemble des projets tout en assurant des expériences utilisateur cohérentes.


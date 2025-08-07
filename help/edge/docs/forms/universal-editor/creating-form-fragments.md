---
title: Comment créer des fragments de formulaire pour la création basée sur WYSIWYG
description: Découvrez comment créer des fragments de formulaire dans l’éditeur universel et les ajouter aux formulaires.
feature: Edge Delivery Services
role: Admin, User, Developer
exl-id: 7b0d4c7f-f82f-407b-8e25-b725108f8455
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 97%

---

# Création de fragments de formulaire dans l’éditeur universel

<span class="preview"> Cette fonctionnalité est disponible par le biais du programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail avec le nom de votre organisation et le nom de votre référentiel GitHub à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>

<span class="preview">Il s’agit d’une fonctionnalité de version préliminaire accessible par le biais de notre [canal de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features). </span>

Les formulaires comprennent souvent des sections courantes telles que les coordonnées, les détails d’identification ou les accords de consentement. Les développeurs et développeuses de formulaires créent ces sections à chaque création de formulaire, ce qui est répétitif et prend beaucoup de temps.
Pour éliminer cette duplication des efforts, l’éditeur universel permet de créer des segments de formulaire réutilisables, tels que des panneaux ou des groupes de champs, une seule fois et de les réutiliser dans différents formulaires. Ces segments réutilisables, modulaires et autonomes s’appellent des fragments de formulaire. Par exemple, le même fragment de contact d’urgence peut être utilisé dans différentes sections d’un formulaire, comme pour les coordonnées des personnes employées et en charge de la supervision.

À la fin de l’article, vous saurez créer et utiliser des fragments dans des formulaires à l’aide de l’éditeur universel.

## Fonctionnalités des fragments de formulaire Edge Delivery Services

- **Conservation de la cohérence avec les fragments de formulaire**
Vous pouvez intégrer des fragments à différents formulaires, ce qui vous permet de maintenir des dispositions cohérentes et un contenu normalisé.

  >[!NOTE]
  >
  > Avec une approche « Modifier une fois, refléter partout », toute mise à jour apportée à un fragment s’applique automatiquement à tous les formulaires en mode de prévisualisation. Cependant, en mode de publication, vous devez publier le fragment ou republier le formulaire pour refléter les modifications.

- **Ajout de fragments de formulaire plusieurs fois dans un formulaire**
Vous pouvez ajouter plusieurs fois un fragment de formulaire dans un formulaire et configurer ses propriétés de liaison de données aux sources de données ou aux schémas.

- **Utilisation de fragments dans des fragments**
Vous pouvez créer des fragments de formulaire imbriqués, ce qui signifie que vous pouvez faire glisser un fragment dans un autre fragment, et avoir une structure de fragment imbriquée.

  >[!NOTE]
  >
  > Vous ne pouvez pas imbriquer un fragment à l’intérieur de lui-même, car cela peut causer des références récursives et un comportement inattendu, ce qui entraîne des erreurs ou des problèmes de rendu.

## Remarques concernant l’utilisation des fragments de formulaire Edge Delivery Services

- Vous devez ajouter la même URL GitHub à la fois dans le fragment et dans le formulaire dans lequel vous avez l’intention d’utiliser le fragment.
- Vous ne pouvez pas modifier un fragment de formulaire dans un formulaire. Pour apporter des modifications, modifiez le fragment de formulaire autonome.

## Prérequis

- [Configurez votre référentiel GitHub](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) pour établir une connexion entre votre environnement AEM et le référentiel GitHub.
- Si vous utilisez déjà Edge Delivery Services, ajoutez la dernière version du [bloc de formulaires adaptatifs](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) à votre référentiel GitHub.
- L’instance de création AEM Forms comprend un modèle basé sur Edge Delivery Services.
- Conservez à portée de main l’URL de votre instance de création AEM Forms as a Cloud Service et de votre référentiel GitHub.

## Utilisation de fragments de formulaire Edge Delivery Services

Vous pouvez créer des fragments de formulaire Edge Delivery Services dans l’éditeur universel et ajouter les fragments créés aux formulaires Edge Delivery Services. Vous pouvez effectuer les actions suivantes avec les fragments de formulaire Edge Delivery Services :

- [Création de fragments de formulaire](#creating-form-fragments)
- [Ajout de fragments de formulaire à un formulaire](#adding-form-fragments-to-a-form)
- [Gestion de fragments de formulaire](#managing-form-fragments)

### Création de fragments de formulaire

Pour créer un fragment de formulaire dans l’éditeur universel, procédez comme suit :

1. Connectez-vous à votre instance de création AEM Forms as a Cloud Service.
1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Cliquez sur **Créer > Fragment de formulaire adaptatif**.

   ![Création d’un fragment](/help/edge/docs/forms/universal-editor/assets/create-fragment.png)

   L’assistant **Créer un fragment de formulaire adaptatif** s’affiche.
1. Sélectionnez le modèle basé sur Egde Delivery Services dans l’onglet **Sélectionner le modèle** et cliquez sur **[!UICONTROL Suivant]**.
   ![Sélection de modèle Edge Delivery Services](/help/edge/docs/forms/universal-editor/assets/create-form-fragment.png)

1. Indiquez le titre, le nom, la description et les balises du fragment. Assurez-vous de spécifier un nom unique pour le fragment. S’il existe déjà un autre fragment portant le même nom, la création du fragment échoue.
1. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, avec l’URL `https://github.com/wkndforms/edsforms`.

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
1. Cliquez sur **Créer** et un assistant s’affiche.

   ![Modification de fragment](/help/edge/docs/forms/universal-editor/assets/edit-fragment.png)

1. Cliquez sur **Modifier** et le fragment créé avec un modèle par défaut s’ouvre dans l’éditeur universel en vue de la création.

   ![Fragment dans l’éditeur universel en vue de la création](/help/edge/docs/forms/universal-editor/assets/fragment-in-ue.png)

   En mode d’édition, vous pouvez ajouter n’importe quel composant de formulaire au fragment. Pour découvrir comment créer un formulaire dans l’éditeur universel, consultez l’article [Commencer avec Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

   La capture d’écran ci-dessous affiche le `contact fragment` créé dans l’éditeur universel.

   ![Copie d’écran d’un fragment de formulaire de coordonnées terminé dans l’éditeur universel, affichant les champs Nom, Téléphone, E-mail et Adresse qui peuvent être réutilisés dans plusieurs formulaires.](/help/edge/docs/forms/universal-editor/assets/contact-fragment.png)

   Une fois le fragment créé, vous pouvez [ajouter le fragment créé dans les formulaires Edge Delivery Services](#adding-form-fragments-in-forms).

### Ajout de fragments de formulaire à un formulaire

Créons un formulaire `Employee Details` simple qui comprend des informations sur la personne employée et celle en charge de la supervision. Vous pouvez utiliser le fragment `Contact Details` dans les panneaux de la personne employée et de celle en charge de la supervision. Pour utiliser le fragment de formulaire dans votre formulaire, procédez comme suit :

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

   Le fragment de formulaire est ajouté par référence au formulaire et est synchronisé avec le fragment de formulaire autonome.

   ![Capture d’écran montrant le fragment relatif aux coordonnées, intégré au formulaire des effectifs d’une entreprise dans l’éditeur universel, présentant la façon dont les fragments conservent leur structure lorsqu’ils sont réutilisés](/help/edge/docs/forms/universal-editor/assets/fragment-in-form.png)

   Vous pouvez prévisualiser le formulaire pour découvrir comment il s’affiche en mode **Prévisualisation**.

   ![Prévisualisation](/help/edge/docs/forms/universal-editor/assets/preview-form-with-fragment.png)

   De même, vous pouvez répéter les étapes 3 à 7 pour insérer le fragment `Contact Details` pour le panneau `Supervisor Details`.

   ![Formulaire Détails de la personne employée](/help/edge/docs/forms/universal-editor/assets/employee-detail-form-with-fragments.png)

### Gestion de fragments de formulaire

Vous pouvez effectuer plusieurs opérations sur des fragments de formulaire depuis l’interface d’utilisation d’AEM Forms.

1. Connectez-vous à votre instance de création AEM Forms as a Cloud Service.
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

## Bonnes pratiques

- Assurez-vous que le nom du fragment est unique. La création du fragment échoue si un fragment portant le même nom existe déjà.
- Toute expression, tout script ou tout style d’un fragment de formulaire autonome est conservé lorsqu’il est inséré par référence ou incorporé dans un formulaire.
- Lorsque vous publiez un formulaire, les fragments de formulaire insérés par référence dans le formulaire sont automatiquement publiés.



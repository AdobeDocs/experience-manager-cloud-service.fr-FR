---
title: Gestion des versions de formulaire dans Forms Manager
description: Découvrez comment créer et gérer des versions de Forms adaptatif, des fragments de formulaire, des thèmes et d’autres ressources dans l’interface utilisateur de Forms Manager.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: cd2c6e15-99a6-4b4e-bfd1-8291a2001ebe
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 7%

---

# Gestion des versions d’Assets de formulaire dans l’interface utilisateur de Forms Manager

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com). </span>

Forms Manager prend désormais en charge le contrôle de version pour les ressources de formulaire. Vous pouvez créer des versions, afficher l’historique des versions et restaurer des versions antérieures de vos ressources à partir de l’interface utilisateur de Forms Manager.

## Types de ressource pris en charge {#supported-asset-types}

Vous pouvez créer et gérer des versions pour les types de ressources suivants :

| Type de ressource | Description |
|---|---|
| Forms adaptatif (composants principaux) | Forms adaptatif créé à l’aide des composants principaux |
| Forms adaptatif (composants de base) | Forms adaptatif créé à l’aide des composants de base |
| Fragments de formulaire | Sections de formulaire réutilisables partagées dans plusieurs formulaires |
| Thèmes | Définitions de style visuel appliquées au Forms adaptatif |
| Modèles XDP | Modèles de formulaire basés sur XFA |
| Ressources binaires | Autres fichiers stockés dans le référentiel de gestion des ressources numériques de formulaires |

## Créer une version {#create-version-forms-manager}

Pour créer une version d’une ressource de formulaire :

1. Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez le formulaire ou la ressource.
1. Dans le panneau de gauche, sélectionnez **[!UICONTROL Chronologie]**.
1. Cliquez sur **[!UICONTROL Enregistrer comme version]** dans la barre d’outils de la chronologie.
   ![Enregistrer comme version](/help/forms/assets/create-version.png)
1. Saisissez un **[!UICONTROL Libellé]** et un **[!UICONTROL Commentaire]** facultatif pour décrire les modifications.
1. Cliquez sur **[!UICONTROL Créer]**.
   ![Enregistrer comme version 2](/help/forms/assets/create-version1.png)

La version s’affiche dans le panneau Chronologie avec son libellé, son commentaire et son horodatage.

## Version d’une ressource lors du chargement {#version-on-upload}

Lorsque vous chargez une ressource portant le même nom qu’une ressource existante, Forms Manager affiche une boîte de dialogue **Chargement de fichier** qui répertorie les ressources à mettre à jour. La boîte de dialogue affiche le nom, la section et le chemin d’accès de la ressource.

Lorsqu’une ressource portant le même nom existe déjà, le chargement remplace la ressource existante et en crée automatiquement une nouvelle version. Vous pouvez afficher la version créée dans le journal.

![Boîte de dialogue de chargement de fichier affichant le chargement avec version](/help/forms/assets/version-upload.png)

## Afficher l’historique des versions {#view-version-history}

Pour afficher l’historique des versions d’une ressource :

1. Sélectionnez la ressource dans Forms Manager.
1. Dans le panneau de gauche, sélectionnez **[!UICONTROL Chronologie]**.
   ![Historique des versions](/help/forms/assets/version-history.png)

La chronologie affiche toutes les entrées de version avec les événements d’activité. Chaque entrée affiche le libellé, le commentaire, l’auteur et l’horodatage.

## Restaurer une version précédente {#restore-version}

Pour restaurer une version antérieure d’une ressource :

1. Sélectionnez la ressource dans Forms Manager.
1. Dans le panneau de gauche, sélectionnez **[!UICONTROL Chronologie]**.
1. Sélectionnez la version à restaurer.
1. Cliquez sur **[!UICONTROL Revenir à cette version]**.
   ![Rétablir la version](/help/forms/assets/revert-version.png)

>[!NOTE]
>
>Les images ne peuvent pas être rétablies à une version précédente. Tous les autres types de ressources, y compris les Forms adaptatifs, les fragments de formulaire, les thèmes et les modèles XDP, prennent en charge la restauration des versions.

## Voir également {#see-also}

* [Contrôle de version, révision et commentaires sur un formulaire adaptatif](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)
* [Importation et exportation de formulaires et de ressources connexes](/help/forms/import-export-forms-templates.md)
* [Publication et dépublication de formulaires](/help/forms/publishing-unpublishing-forms.md)

---
title: Comment créer une séquence de formulaires à plusieurs étapes ?
description: Avec  [!DNL Experience Manager Forms], vous pouvez définir une séquence de panneaux de formulaires pour que les utilisateurs puissent naviguer entre ceux-ci et remplir un formulaire adaptatif.
role: User, Developer
level: Intermediate
feature: Adaptive Forms, Foundation Components
exl-id: 6b3f9131-db6b-451b-a932-b57d809222eb
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 69%

---

# Présentation de la séquence de formulaires à plusieurs étapes {#introduction-to-multi-step-form-sequence}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/introduction-form-sequence.html) |
| AEM as a Cloud Service | Cet article |

Les formulaires adaptatifs permettent aux auteurs de formulaires de créer un environnement de capture de données simple d’emploi à plusieurs étapes. Cela s’accompagne d’une prise en charge intégrée pour la création de plusieurs panneaux et l’association de chaque panneau à différents modèles de navigation. Les auteurs et autrices de formulaires peuvent regrouper les champs de formulaire dans des sections logiques et représenter un groupe sous la forme d’un panneau. La navigation globale entre les panneaux est contrôlée à l’aide de la disposition des panneaux. Les auteurs peuvent réorganiser les panneaux selon différentes dispositions en les plaçant, par exemple, de manière séquentielle à l’aide de la disposition Assistant ou de manière improvisée avec la disposition Onglets. Pour plus d’informations sur les dispositions de panneaux, voir [Fonctionnalités de disposition des formulaires adaptatifs](layout-capabilities-adaptive-forms.md).

Dans une expérience de remplissage de formulaire type, il y a plus d’étapes impliquées que la simple capture de données. Un envoi de formulaire complet peut inclure d’autres étapes, telles que la signature numérique du formulaire, la vérification des informations renseignées dans le formulaire, le traitement des paiements, etc. Cela diffère d’un cas à l&#39;autre.

Si votre scénario d’utilisation requiert un ensemble d’étapes pour l’acquisition de données ou si des règles prévoient l’exécution de certaines étapes, [!DNL Experience Manager Forms] vous offre la possibilité d’appliquer cette structure commune au sein des formulaires. L’implémentation prédéfinie de la structure de formulaires détermine la séquence d’étapes d’un formulaire. ![Exemple de séquence de formulaires à plusieurs étapes](assets/formpipeline.png)

Exemple de séquence de formulaires à plusieurs étapes

Supposons que vous deviez créer une séquence pour les étapes de remplissage, de vérification, de signature et de confirmation d’un formulaire. Les étapes de création d’une telle séquence sont les suivantes :

1. Définissez un modèle de formulaire et ajoutez-y le panneau requis. Notez qu’il doit y avoir un seul panneau par étape dans la séquence. Vous pouvez toutefois inclure des sous-panneaux dans un panneau.

   Dans cet exemple, nous pouvons ajouter les panneaux suivants :

   * **[!UICONTROL Remplir]** : contient des champs de formulaire pour l’acquisition de données. Vous pouvez inclure des sous-panneaux imbriqués afin de créer des sections pour différents types d’information ; personnel, famille ou financier, par exemple.

   <!--* **[!UICONTROL Verify]**: It contains the **[!UICONTROL Verify]** component that can be used in an XFA-based Adaptive Form. It displays the information captured in the Fill panel in read-only mode for verification.-->


   * **[!UICONTROL Signer électroniquement]** : contient le composant **[!UICONTROL Sign]** qui peut être utilisé dans un formulaire adaptatif XFA. Ce panneau fournit les services de signature suivants :

      * Services Adobe Document Cloud eSign
      * Signature tactile

   * **[!UICONTROL Confirmation]** : contient le composant **[!UICONTROL Résumé]** qui affiche un message de conformation d’envoi du formulaire lorsqu’un utilisateur l’a signé et a atteint l’étape de confirmation (Résumé) dans la séquence. Les auteurs peuvent configurer le texte du composant de [!UICONTROL Résumé], afficher un message de remerciement et un lien vers le PDF généré, etc.

1. Sélectionnez la disposition du panneau racine en tant qu’**[!UICONTROL Assistant]**.
1. Suivez les étapes restantes pour créer le modèle de formulaire. <!-- For more information, see [Creating a custom Adaptive Form template](custom-adaptive-forms-templates.md). -->

Après avoir défini la séquence des formulaires dans le modèle de formulaire, vous pourrez vous en servir pour créer des formulaires dont la séquence active sera utilisée comme structure de base. Cependant, vous pourrez toujours personnaliser le formulaire en fonction de vos besoins.


## Voir également {#see-also}

{{see-also}}
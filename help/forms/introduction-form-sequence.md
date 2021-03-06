---
title: Comment créer une séquence de formulaires à plusieurs étapes ?
description: 'Avec [!DNL Experience Manager Forms], vous pouvez définir une séquence de panneaux de formulaires pour que les utilisateurs puissent naviguer entre ceux-ci et remplir un formulaire adaptatif. Explorez ce thème en profondeur en prenant comme exemple un cas d’utilisation pour créer une séquence de formulaires à plusieurs étapes. '
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 6b3f9131-db6b-451b-a932-b57d809222eb
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 100%

---

# Présentation de la séquence de formulaires à plusieurs étapes {#introduction-to-multi-step-form-sequence}

Les formulaires adaptatifs permettent aux auteurs de formulaires de créer un environnement de capture de données simple d’emploi à plusieurs étapes. Ce module s’accompagne d’une prise en charge intégrée pour la création de plusieurs panneaux et l’association de chacun d’eux à des schémas de navigation différents. Les auteurs de formulaires peuvent regrouper des champs de formulaire dans des sections logiques et représenter un groupe sous la forme d’un panneau. La navigation globale entre les panneaux est contrôlée à l’aide de la disposition des panneaux. Les auteurs peuvent réorganiser les panneaux selon différentes dispositions en les plaçant, par exemple, de manière séquentielle à l’aide de la disposition Assistant ou de manière ad hoc avec la disposition Onglets. Pour plus d’informations sur les dispositions de panneaux, voir [Fonctionnalités de disposition des formulaires adaptatifs](layout-capabilities-adaptive-forms.md).

Dans le cadre d’un remplissage normal de formulaires, la procédure ne se limite pas à la simple acquisition de données. Une procédure d’envoi de formulaires complète peut inclure d’autres étapes, comme par exemple signer le formulaire sous forme numérique, vérifier les informations renseignées dans le formulaire, traiter des paiements, etc. Elle peut être différente suivant les cas.

Si votre scénario d’utilisation requiert un ensemble d’étapes pour l’acquisition de données ou si des règles prévoient l’exécution de certaines étapes, [!DNL Experience Manager Forms] vous offre la possibilité d’appliquer cette structure commune au sein des formulaires. L’implémentation prédéfinie de la structure de formulaires détermine la séquence d’étapes d’un formulaire. ![Exemple de séquence de formulaires à plusieurs étapes](assets/formpipeline.png)

Exemple de séquence de formulaires à plusieurs étapes

Supposons que vous deviez créer une séquence pour les étapes de remplissage, de vérification, de signature et de confirmation d’un formulaire. Les étapes de création d’une telle séquence sont les suivantes :

1. Définissez un modèle de formulaire et ajoutez-y le panneau requis. Notez qu’il doit y avoir un seul panneau par étape dans la séquence. Vous pouvez toutefois inclure des sous-panneaux dans un panneau.

   Dans cet exemple, nous pouvons ajouter les panneaux suivants :

   * **[!UICONTROL Remplir]** : contient des champs de formulaire pour l’acquisition de données. Vous pouvez inclure des sous-panneaux imbriqués afin de créer des sections pour différents types d’information ; personnel, famille ou financier, par exemple.

   <!--* **[!UICONTROL Verify]**: It contains the **[!UICONTROL Verify]** component that can be used in an XFA-based Adaptive Form. It displays the information captured in the Fill panel in read-only mode for verification.-->


   * **[!UICONTROL Signer électroniquement]** : contient le composant **[!UICONTROL Sign]** qui peut être utilisé dans un formulaire adaptatif XFA. Ce panneau fournit les services de signature suivants :

      * Services Adobe Document Cloud eSign
      * Signature tactile
   * **[!UICONTROL Confirmation]** : contient le composant **[!UICONTROL Résumé]** qui affiche un message de conformation d’envoi du formulaire lorsqu’un utilisateur l’a signé et a atteint l’étape de confirmation (Résumé) dans la séquence. Les auteurs peuvent configurer le texte du composant de [!UICONTROL Résumé], afficher un message de remerciement et un lien vers le PDF généré, etc.



1. Sélectionnez la disposition du panneau racine **[!UICONTROL Assistant]**.
1. Effectuez les étapes suivantes pour créer le modèle de formulaire. <!-- For more information, see [Creating a custom Adaptive Form template](custom-adaptive-forms-templates.md). -->

Après avoir défini la séquence des formulaires dans le modèle de formulaire, vous pourrez vous en servir pour créer des formulaires dont la séquence active sera utilisée comme structure de base. Cependant, vous pourrez toujours personnaliser le formulaire en fonction de vos besoins.

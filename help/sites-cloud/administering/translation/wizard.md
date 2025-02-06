---
title: Assistant Copie de la langue
description: Découvrez comment utiliser l’Assistant Copie de la langue dans AEM.
feature: Language Copy
role: Admin
exl-id: bf8bdc53-0248-47de-bb9d-c884a7179ab0
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 46%

---

# Assistant Copie de la langue {#language-copy-wizard}

L’assistant Copie de la langue est une expérience guidée pour créer et gérer la structure du contenu multilingue. L’assistant facilite et accélère la création d’une copie de langue.

>[!TIP]
>
>Si vous êtes un débutant dans la traduction de contenu, reportez-vous à la section [Parcours de traduction de sites](/help/journey-sites/translation/overview.md), qui vous guide sur le chemin de la traduction de votre contenu AEM Sites à l’aide d’AEM de puissants outils de traduction, idéaux pour ceux qui ne disposent pas d’une expérience concernant AEM ou la traduction.

>[!NOTE]
>
>L’utilisateur doit être membre du groupe `project-administrators` pour créer une copie de langue d’un site.

Pour accéder à cet assistant :

1. Dans la console Sites, sélectionnez une page, puis sélectionnez **Créer** et **Copier la langue**.

   ![Création d’une copie de langue à partir de l’assistant](../assets/language-copy-wizard.png)

1. L’assistant s’ouvre à l’étape **Sélectionner le Source** qui vous permet d’ajouter ou de supprimer des pages. Vous avez également la possibilité d’inclure ou d’exclure les sous-pages. Sélectionnez les pages à inclure et sélectionnez **Suivant**.

   ![Ajout de pages avec l’assistant](../assets/language-copy-wizard-add-pages.png)

1. L’étape **Configurer** de l’assistant vous permet d’ajouter ou de supprimer des langues et de sélectionner la méthode de traduction. Sélectionnez **Suivant**.

   ![Étape Configurer de l’assistant](../assets/language-copy-wizard-configure.png)

   >[!NOTE]
   >
   >Par défaut, il n’y a qu’un seul paramètre de traduction. Pour pouvoir sélectionner d’autres paramètres, vous devez d’abord configurer les configurations cloud. Voir [Configuration de la structure d’intégration de traduction](integration-framework.md).

1. À l’étape **Traduire** de l’assistant, vous pouvez choisir entre créer uniquement la structure, créer un projet de traduction ou ajouter la structure à un projet de traduction existant.

   >[!NOTE]
   >
   >Si vous avez sélectionné plusieurs langues à l’étape précédente, plusieurs projets de traduction sont créés.

   ![Étape de traduction de l’assistant](../assets/language-copy-wizard-translate.png)

1. Le bouton **Créer** ferme l’assistant. Sélectionnez **Terminé** pour fermer l’assistant ou **Ouvrir** pour afficher le résultat du projet de traduction.

   ![Terminer l’assistant](../assets/language-copy-wizard-done.png)

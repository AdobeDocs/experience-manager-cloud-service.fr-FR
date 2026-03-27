---
title: Activer et configurer l’interface utilisateur associée pour les communications interactives
description: Découvrez comment activer la vue Associé et configurer un workflow pour les mises à jour dans les paramètres de communication interactive afin que les associés puissent utiliser l’interface utilisateur Associer.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 7c3e8a2b-5f21-4a1e-9e2d-8a4b6c7d8e9f
source-git-commit: a41459520feb03594212b91e68cfd8e2b1e610c4
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 1%

---

# Activer et configurer l’interface utilisateur associée pour les communications interactives

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

Cet article décrit comment activer l’interface utilisateur associée pour une communication interactive (IC) et éventuellement configurer un workflow AEM pour les envois. Les auteurs effectuent ces étapes dans **Paramètres de communication interactive**.

Pour une présentation de l’interface utilisateur associée et des rôles utilisateur, voir [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md).

## Conditions préalables

Avant d’activer et de configurer l’interface utilisateur associée, vérifiez les points suivants :

- **Accès de création** à l’éditeur de communication interactive.
- Une **communication interactive** créée avec la mise en page et les liaisons de données requises.
- **Associer des utilisateurs** ajouté au groupe **forms-associates** (nécessaire pour que les associés accèdent à l’interface utilisateur d’Associate).
- **Auteurs** ajoutés au groupe **forms-associates** (requis pour que les auteurs accèdent à l’interface utilisateur d’Associate).

Lorsque vous êtes prêt à intégrer l’interface utilisateur associée à votre application et à l’appeler sur l’instance de publication, vous aurez également besoin d’un navigateur avec la prise en charge des fenêtres contextuelles activée et l’interface utilisateur publiée. Voir [Intégrer l’interface utilisateur associée à votre application](/help/forms/interactive-communication/invoke-associate-ui.md) pour connaître les conditions préalables à l’intégration complète.

## Activer la vue Associer (interface utilisateur Associer)

Activez l’interface utilisateur d’Associate au niveau du document afin que les communications interactives puissent être utilisées par les associés.

1. Ouvrez votre communication interactive dans l’éditeur.
1. Dans la barre d’actions supérieure ou les options du document, ouvrez **Paramètres de communication interactive** (ou **Paramètres**).

   ![Paramètres de communication interactive - Associer les propriétés à Activer la modification des vues associées](/help/forms/assets/associate-ui-settings.png)

1. Dans le panneau de gauche, assurez-vous que l’option **Associer les propriétés** est sélectionnée.
1. Sur la droite, cochez **Activer la modification des vues associées**.
1. Cliquez sur **Appliquer les modifications**, puis enregistrez le document.

   ![Paramètres de communication interactive - Associer les propriétés à Activer la modification des vues associées](/help/forms/assets/associate-ui-enable-view.png)

Un message peut vous rappeler d&#39;appliquer des modifications et d&#39;enregistrer le document pour activer la vue associée. Après l’enregistrement, l’IC est disponible pour une utilisation pilotée par les associés.

### Autoriser la modification de l’interface utilisateur associée par composant

Une fois que la vue Associé est activée pour l&#39;IC, vous devez activer **Autoriser la modification par associé** pour chaque composant que les associés doivent pouvoir modifier. Les composants sans ce paramètre activé restent en lecture seule dans l’interface utilisateur d’Association.

1. Dans l’éditeur IC, sélectionnez le composant (par exemple, un champ de texte) dans la zone de travail ou dans la hiérarchie de composants.
1. Dans le panneau **Propriétés** de droite, développez **Associer les propriétés**.
1. Activez **Autoriser la modification par associé** **Activé** pour ce composant.
1. Répétez l’opération pour chaque composant que vous souhaitez modifier, puis enregistrez le document.

![Autoriser la modification par associé dans les propriétés du composant](/help/forms/assets/associate-ui-allow-editing-by-associate.png)

>[!NOTE]
>
> **Associer les propriétés** inclut également des options telles que **Typographie** (police, taille et style du champ dans l’interface utilisateur associée), **Info-bulle** et **Modèles** (validations). Utilisez-les pour contrôler l’aspect et le comportement du composant lorsque des associés le modifient ; par exemple, définissez des modèles de validation afin que les associés saisissent les données au format requis.

## Configurer le workflow pour l’interface utilisateur associée

Pour exécuter un workflow AEM lorsque les utilisateurs envoient ou mettent à jour des données à partir de l’interface utilisateur associée, configurez les éléments suivants :

1. Dans **Paramètres de communication interactive**, sélectionnez **Workflow** dans le panneau de gauche (sous Propriétés associées).
1. Activer **Configurer le workflow pour la mise à jour** **Activé**.
1. Dans **Sélectionner le modèle de workflow**, choisissez le modèle de workflow AEM à exécuter (par exemple, `conversionWorkflow` ou un chemin d’accès tel que `/var/workflow/models/submit-workflow-1`).
1. Définissez éventuellement **Message de succès du workflow** (affiché à l’utilisateur ou à l’utilisatrice une fois le workflow terminé).
1. Vous pouvez éventuellement définir **URL de redirection** pour envoyer l’utilisateur vers une page spécifique après l’envoi.
1. Cliquez sur **Appliquer les modifications** et enregistrez le document.

   ![Paramètres de communication interactive - Configuration du workflow pour l’interface utilisateur associée](/help/forms/assets/associate-ui-configure-workflow.png)

Lorsque vous activez un workflow, il s’exécute chaque fois que les utilisateurs effectuent une soumission depuis l’interface utilisateur associée. Pour le fonctionnement de l’envoi et du workflow (où ils s’exécutent, qui utilise quelle instance et les points clés), consultez la section [Workflow d’envoi pour l’interface utilisateur associée](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md#submission-and-workflow-behavior). Cet article comprend également un exemple de workflow qui génère PDF à partir des envois IC.

## Terminer la configuration de l’interface utilisateur associée

Après avoir activé la vue Associé et éventuellement configuré le workflow :

1. **Activer les champs modifiables :** dans les sections requises de la carte d’interface utilisateur, activez les champs que les associés sont autorisés à modifier. Définissez les validations et le comportement obligatoire/en lecture seule selon les besoins.
1. **Publiez l’IC** afin qu’il soit disponible sur l’instance de publication pour les associés.
1. Partagez le lien IC publié avec les associés. Ils s’authentifient (par exemple, via l’ID d’entrée Microsoft [](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id)) et ouvrent l’interface utilisateur associée, saisissent ou confirment les données client et génèrent la communication finale. Si vous avez configuré un workflow, il s’exécute lors de l’envoi. Pour connaître le fonctionnement de l’envoi et du workflow, voir [ Workflow d’envoi pour l’interface utilisateur associée ](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md#submission-and-workflow-behavior).

## Voir également

- [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Intégrer l’interface utilisateur associée à votre application](/help/forms/interactive-communication/invoke-associate-ui.md)
- [Workflow d’envoi pour l’interface utilisateur associée - Sortie IC Generate PDF](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md) - Fonctionnement de l’envoi et du workflow, ainsi qu’un exemple de workflow qui génère du PDF à partir des envois IC.

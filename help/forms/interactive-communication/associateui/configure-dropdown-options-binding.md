---
title: Configurer les options de liste déroulante pour l’interface utilisateur associée
description: Découvrez comment configurer les options de liaison ou les options statiques manuelles pour les champs déroulants dans l’éditeur de communication interactive afin que les choix s’affichent correctement dans l’interface utilisateur associée.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: configure-dropdown-options-associate-ui
source-git-commit: b817bcb02c4ff6ac369973ef658d9fcbdce95c51
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 2%

---


# Configurer les options de liste déroulante pour l’interface utilisateur associée

Les champs déroulants de l’éditeur de communication interactive utilisent un modèle **Liaison d’options** ciblé pour les choix dynamiques pilotés par les données dans l’interface utilisateur d’Associate. La **liaison de données** n’est plus prise en charge pour les champs de liste déroulante. Les auteurs configurent les options **Liaison à partir des données** (source de données liée) ou statique manuelle dans le panneau **Propriétés**.

| Qui | Avantage |
|-----|---------|
| **Auteur (concepteur de communication interactive)** | Proposez des choix de liste déroulante précis et pilotés par les données aux associés sans configurations de liaison de données non prises en charge. |
| **Associé (agent/représentant de service)** | Afficher la liste d’options correcte et la valeur présélectionnée lors de l’exécution des communications client dans l’interface utilisateur d’Associate. |

## Avant de commencer

Activez la **vue associée** sur la communication interactive avant de configurer le comportement de liste déroulante pour l’interface utilisateur d’Associate. Voir [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md).

Les associés doivent être membres du groupe **forms-associates**.

## Liaison à partir des données activée (options dynamiques)

Lorsque **Options Source** est défini sur **Liaison à partir des données** :

- Les options de liste déroulante sont entièrement pilotées par la source de données liée configurée dans **Réf Options**.
- Les options sont rendues et disponibles pour sélection dans l’interface utilisateur associée.
- **Valeur par défaut** non disponible — la première valeur des options liées est automatiquement présélectionnée lorsque le formulaire est présenté à l&#39;associé.

## Options manuelles (options statiques)

Lorsque **Options Source** n’est pas défini sur **Liaison à partir des données** :

- Les auteurs ajoutent manuellement des options via le panneau **Propriétés**.
- **Valeur par défaut** reste disponible — le concepteur du formulaire peut sélectionner explicitement l’option qui apparaît comme valeur présélectionnée dans l’interface utilisateur d’Associate.

## Configurer les options de liste déroulante

1. Ouvrez la communication interactive dans l’éditeur de communication interactive.

1. Dans l’onglet **Conception**, sélectionnez le composant **Liste déroulante** sur la zone de travail de conception.

1. Ouvrez le panneau **Propriétés**.

1. Configurez la liste déroulante pour l’interface utilisateur associée :

   - Définissez **Légende** sur le libellé associé à voir dans le panneau de saisie de données de gauche. Par exemple, saisissez **Mois du versement**.
   - Sous **Options Source**, choisissez **Liaison à partir des données** pour renseigner les options de votre modèle de données ou ajoutez des options manuelles pour une liste statique.
   - Si vous avez sélectionné **Lier à partir des données**, définissez **Référence des options** sur le chemin d’accès aux données qui fournit la liste des options. Par exemple, liez à `$.GMFletter.installmentDetails.installmentMonth`.

   Ne configurez pas la **liaison de données** sur les champs de liste déroulante. Utilisez uniquement les options **Lier à partir des données** ou manuelle.

   ![Configurer la liaison des options de liste déroulante](/help/forms/interactive-communication/assets/associate-ui-configure-drop-down1.png)

1. Activez **Autoriser la modification par associé** pour que les associés puissent sélectionner une valeur dans l’interface utilisateur associée.

1. Vous pouvez éventuellement configurer **Info-bulle** et **Validations** sous **Associer les propriétés**.

1. Si vous utilisez des options manuelles, définissez **Valeur par défaut** selon les besoins.

1. Cliquez sur **Enregistrer** et publiez la communication interactive.

## Vérifier dans l’interface utilisateur associée

1. Ouvrez la communication interactive dans la vue **Associer**.

1. Confirmez que la liste déroulante qui s’affiche dans le panneau de saisie de données de gauche avec la légende que vous avez configurée. Par exemple, la mention **Mois du versement** indique les options liées telles que **Juin 2026**, **Juillet 2026** et **Août 2026**.

1. Vérifiez que la première option de liaison est présélectionnée au chargement de l’interface utilisateur associée.

1. Sélectionnez une autre option et confirmez les mises à jour des valeurs dans l’aperçu de droite. Par exemple, si vous sélectionnez **Juin 2026**, le texte du document est mis à jour sur **Mois de versement, juin 2026**.

   ![Vérification des options de liste déroulante dans l’interface utilisateur associée](/help/forms/interactive-communication/assets/associate-ui-configure-drop-down2.png)

## Considérations

- **La liaison de données n’est pas prise en charge** pour les champs de liste déroulante. Utilisez **Lier à partir des données** pour les listes dynamiques ou des options manuelles pour les listes statiques.
- Lorsque la fonction **Lier à partir des données** est activée, les associés ne peuvent pas définir de valeur par défaut personnalisée ; la première option de liaison est toujours présélectionnée.
- Avec des options manuelles, testez la **Valeur par défaut** dans l’aperçu de l’interface utilisateur associée pour confirmer que l’option attendue s’affiche avant la publication.
- **Autoriser la modification par associé** doit être activé pour que la liste déroulante s’affiche en tant que champ modifiable sur le côté gauche de l’interface utilisateur d’associé.

## Questions fréquentes

**Pourquoi la valeur par défaut n’est-elle pas disponible pour ma liste déroulante ?**
**Valeur par défaut** est désactivé lorsque **Options Source** est défini sur **Lier à partir des données**. La première valeur de la source de données liée est présélectionnée automatiquement dans l’interface utilisateur d’Associate.

**Puis-je utiliser la liaison de données et la liaison d’options dans une liste déroulante ?**
Non. Les champs déroulants prennent uniquement en charge les options **Liaison à partir des données** ou manuelle . La **liaison de données** n’est pas prise en charge pour les champs de liste déroulante.

**En quoi consiste la réf. Options ?**
**Référence des options** est le chemin de référence des données qui fournit la liste des choix lorsque **Source des options** est défini sur **Liaison à partir des données**. Sélectionnez le chemin d’accès qui pointe vers la collection de valeurs d’option dans votre modèle de données de formulaire.

**Comment vérifier les options de liste déroulante avant que les associés n’utilisent la communication interactive ?**
Publiez la communication interactive et ouvrez l’aperçu de l’interface utilisateur associée. Vérifiez que les options liées ou manuelles apparaissent dans le panneau de saisie de gauche et que la valeur présélectionnée correspond à votre configuration.

## Voir également

- [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Configuration des variables liées et non liées pour l’interface utilisateur associée](/help/forms/interactive-communication/associateui/configure-bound-unbound-variables-associate-ui.md)
- [Créer une communication interactive](/help/forms/interactive-communication/create-interactive-communication.md)


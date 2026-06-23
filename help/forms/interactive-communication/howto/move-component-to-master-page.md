---
title: Déplacer un composant vers la page de Principal
description: Découvrez comment déplacer un composant d’une page de conception vers le gabarit de page afin qu’il apparaisse de manière cohérente sur toutes les pages d’une communication interactive.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: move-component-to-master-page-ic-editor
source-git-commit: 38a10bc5caaa1615188d2e6623b9d432bd4c3d69
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---


# Déplacer un composant vers la page de Principal

Le gabarit de page d’une communication interactive définit des éléments qui se répètent sur chaque page, en-têtes, pieds de page, filigranes, numéros de page et tout autre contenu qui doit apparaître de manière cohérente dans l’ensemble du document. Les composants qui se trouvent sur des pages de conception individuelles s’affichent uniquement sur ces pages spécifiques.

Si vous concevez un composant sur une page normale et que vous décidez par la suite qu’il appartient à chaque page, vous pouvez le déplacer directement du canevas vers le gabarit de page sans avoir à le supprimer ni à le recréer. Le composant est placé à la même position visuelle qu’il occupait sur la page de conception.

| Qui | Avantage |
|-----|---------|
| **Auteur (concepteur de communication interactive)** | Promouvez un composant sur chaque page en une seule action au lieu de le dupliquer manuellement sur plusieurs pages de conception. |
| **Concepteur de modèles** | Affiner la structure du modèle après la conception initiale sans recréer les composants à partir de zéro. |

## Déplacer un composant vers le gabarit de page

Un cas d’utilisation courant consiste à déplacer des éléments d’en-tête qui se répètent, tels qu’un **logo bancaire** et une **adresse bancaire**, d’une page de conception vers le gabarit de page afin qu’ils apparaissent sur chaque page de la communication interactive.

1. Ouvrez la communication interactive dans l’éditeur de communication interactive.

1. Dans l’onglet **Conception**, accédez à la page de conception qui contient les composants à déplacer.

1. Cliquez avec le bouton droit sur le composant dans la zone de travail.

   Par exemple, cliquez avec le bouton droit de la souris sur le bloc de texte adresse de la banque.

1. Dans le menu contextuel, sélectionnez **Déplacer vers**, puis choisissez la page de Principal **&#x200B;**.

   ![Déplacer vers le gabarit de page &#x200B;](/help/forms/interactive-communication/assets/move-to-master-page.png)

   Le composant est supprimé de la page de conception et ajouté au gabarit de page à la même position visuelle. Il apparaît désormais sur chaque page qui utilise ce gabarit.

1. Répétez les étapes 3 et 4 pour chaque composant souhaité dans le gabarit de page.

   Par exemple, après avoir déplacé l’adresse de la banque, répétez les mêmes étapes pour déplacer le logo de la banque.

1. Sélectionnez l&#39;onglet **Principal** pour vérifier que le logo et l&#39;adresse de la banque apparaissent dans les positions prévues.

   ![Déplacer vers le gabarit de page &#x200B;](/help/forms/interactive-communication/assets/move-to-master-page2.png)

## Composants éligibles

Tous les types de composant ne peuvent pas être déplacés vers le gabarit de page. Les types suivants ne sont **pas éligibles** pour cette action :

| Type de composant non éligible | Raison |
|---------------------------|--------|
| Zones de contenu | Définir les zones où le contenu des pages de conception circule ; doit rester sur les pages de conception |
| Zones de page | Conteneurs de pages structurelles liés à des pages individuelles |
| Ensembles de pages | Regroupements de plusieurs pages ; déplacement impossible indépendamment |
| Fragments | Blocs de documents réutilisables gérés indépendamment |
| Sous-formulaire | Composants de conteneur avec leur propre portée de disposition. |
| Lignes du tableau | Éléments au niveau des lignes appartenant à une structure de tableau |
| Cellules de tableau | Éléments au niveau de la cellule appartenant à une structure de tableau |
| Cases d’option | Contrôles de sélection faisant partie d’une structure de données de formulaire |

Les composants dotés d’un **verrouillage de contenu** ou **verrouillage de mise en page** appliqué ne sont pas éligibles non plus. Supprimez le verrouillage avant de le déplacer ou planifiez le placement du composant sur le gabarit de page lors de la conception du modèle. Voir [Verrouillage de modèle dans l’éditeur de communication interactive](/help/forms/interactive-communication/enable-template-lock.md).

## Questions fréquentes

**Quelle est la différence entre placer un composant sur le gabarit de page et le copier sur chaque page de conception ?**
Un composant du gabarit de page est géré à un seul endroit : toute modification que vous y apportez s’applique automatiquement à chaque page qui utilise ce gabarit de page. Les copies des différentes pages de conception doivent être mises à jour séparément, ce qui rend la maintenance fastidieuse et source d’erreurs.

**Puis-je redéplacer un composant du gabarit de page vers une page de conception ?**
Il n’existe aucune action directe de « retour en arrière ». Pour renvoyer un composant à une page de conception spécifique, ajoutez une nouvelle instance de ce type de composant à la page de conception et supprimez-la du gabarit de page.

**Pourquoi le menu contextuel de mon composant n’affiche-t-il pas Déplacer vers > page Principal ?**
Il se peut que le type de composant ne soit pas éligible (consultez le tableau d’éligibilité ci-dessus) ou qu’un verrouillage de contenu ou de mise en page soit appliqué au composant. Vérifiez les deux conditions et supprimez tout verrou avant de réessayer. Déplacez chaque composant éligible séparément, par exemple, déplacez le logo et l’adresse de la banque un par un.

## Voir également

- [Implémentation de la numérotation dynamique de page dans l’éditeur de communication interactive](/help/forms/interactive-communication/implement-dynamic-page-numbering.md)
- [Verrouillage de modèle dans l’éditeur de communication interactive](/help/forms/interactive-communication/enable-template-lock.md)
- [Créer un modèle de communication interactive](/help/forms/interactive-communication/create-interactive-communication-template.md)
- [Créer une communication interactive](/help/forms/interactive-communication/create-interactive-communication.md)

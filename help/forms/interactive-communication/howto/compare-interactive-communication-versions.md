---
title: Comparer les versions de la communication interactive
description: Découvrez comment ouvrir deux versions d’une communication interactive côte à côte en tant qu’aperçus PDF pour examiner les différences de disposition et de contenu avant de publier.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: compare-interactive-communication-versions
source-git-commit: b817bcb02c4ff6ac369973ef658d9fcbdce95c51
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---


# Comparer les versions de la communication interactive

Lorsqu’une communication interactive subit plusieurs cycles de modification, il peut être difficile de savoir exactement ce qui a changé entre deux états enregistrés. Vous pouvez afficher deux versions côte à côte en tant qu’aperçus PDF, ce qui permet d’identifier facilement les changements de disposition, les ajouts ou suppressions de composants et les modifications de contenu statique, sans avoir à ouvrir chaque version individuellement ou à comparer manuellement les captures d’écran.

| Qui | Avantage |
|-----|---------|
| **Auteur (concepteur/propriétaire de la communication interactive)** | Vérifiez que les modifications entre les cycles de révision ont produit les modifications attendues avant la publication. |
| **Réviseur de contenu** | Vérifiez que les révisions de l’auteur ont pris en compte les commentaires d’une version précédente sans introduire de nouveaux problèmes. |

>[!NOTE]
>
> Cette comparaison couvre **mise en page et contenu statique uniquement**. Les valeurs de champ dynamique renseignées au moment de l’exécution ne sont pas rendues dans la vue de comparaison.

## Avant de commencer

Assurez-vous d’avoir enregistré au moins une version de la communication interactive que vous souhaitez comparer à la conception actuelle.

Pour créer une version, ouvrez **Forms et documents**, sélectionnez la communication interactive, ouvrez le panneau **Chronologie** dans le rail gauche, puis cliquez sur **Enregistrer comme version**. Consultez [ Contrôle de version et commentaires dans l’éditeur de communication interactive ](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md) pour obtenir des instructions détaillées.

Après avoir enregistré la version, mettez à jour la communication interactive dans l’éditeur afin que la conception actuelle diffère de la version enregistrée. Vous avez besoin d’une version enregistrée et d’un état actuel modifié avant de pouvoir les comparer.

## Mettre à jour la communication interactive

Après avoir créé une version, ouvrez la communication interactive dans l’éditeur de communication interactive et mettez à jour votre conception.

Par exemple, après avoir enregistré la **communication interactive bancaire version 1**, vous pouvez mettre à jour le logo de la banque, réviser les détails du prêt et modifier les informations sur le véhicule dans le tableau :

- Remplacez l’en-tête de banque textuel par une image de logo de banque
- Mettez à jour les détails du prêt, tels que le numéro de référence de la demande, le montant du prêt approuvé, la durée du prêt et la date de début des mensualités
- Mettez à jour la valeur **Marque et modèle** et le nom du concessionnaire dans le tableau Détails du véhicule

![ Communication interactive mise à jour ](/help/forms/interactive-communication/assets/compare-ic1.png)

Cliquez sur **Enregistrer** lorsque vous avez terminé la modification. La conception actuelle est maintenant prête à être comparée à la version enregistrée.

## Comparer deux versions

1. Accédez à **Forms et documents** et sélectionnez la communication interactive à comparer.

1. Ouvrez le panneau **Chronologie** dans le rail de gauche.

1. Dans la chronologie, recherchez la version enregistrée que vous souhaitez comparer. Par exemple, sélectionnez **Communication interactive bancaire version 1** avec le commentaire **Cette version comprend le nouveau logo de la banque et des détails mis à jour**.

1. Cliquez sur **Comparer avec la version actuelle**.

   ![Comparer avec la version actuelle](/help/forms/interactive-communication/assets/compare-ic2.png)

   Un nouvel onglet s’ouvre avec les deux versions affichées côte à côte en tant qu’aperçus PDF. La version enregistrée s’affiche à gauche et la version actuelle à droite.

   ![Comparaison côte à côte](/help/forms/interactive-communication/assets/comapre-ic3.png)

   Parcourez les deux aperçus pour examiner les différences de disposition et de contenu page par page. Par exemple, la comparaison met en évidence les modifications apportées au logo de la banque, aux détails du prêt et aux informations sur le véhicule, telles que le modèle de voiture et le nom du concessionnaire.

## Considérations

- **Blocs de texte volumineux :** si un paragraphe ou un bloc de texte a été réécrit ou réorganisé, les deux pages sont rendues de la même manière que leur PDF source. Il n’existe pas de comparaison de texte intégrée, la comparaison est visuelle uniquement et le texte modifié n’est pas marqué.

- **Données dynamiques :** les valeurs des champs dynamiques ne sont pas incluses dans la comparaison. Seules la mise en page statique et le contenu de chaque version sont visibles.

## Questions fréquentes

**Combien de versions puis-je comparer à la fois ?**
Vous pouvez comparer deux versions à la fois : la version que vous sélectionnez et la version actuelle. Elles s’ouvrent côte à côte dans un nouvel onglet.

**Puis-je comparer une version à une version autre que la version actuelle ?**
Le sélecteur de version effectue toujours une comparaison avec la version actuelle. Pour comparer deux versions non actuelles, revenez temporairement à l’ancienne version, puis utilisez de nouveau **Comparer avec la version actuelle**.

**Est-il possible de télécharger ou d’exporter la vue de comparaison ?**
Non. La comparaison côte à côte est uniquement un outil de révision visuelle ; elle n’est pas exportable à partir de l’éditeur.

## Voir également

- [Contrôle de version et commentaires dans l’éditeur de communication interactive](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md)
- [Vérifier et annoter une communication interactive](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md)
- [Créer une communication interactive](/help/forms/interactive-communication/create-interactive-communication.md)


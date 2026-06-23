---
title: Configuration des variables liées et non liées pour l’interface utilisateur associée
description: 'Découvrez comment configurer des variables liées et non liées dans des composants de texte pour l’interface utilisateur associée : modifiez l’ensemble du bloc de texte dans l’aperçu du document ou modifiez des variables individuelles dans le panneau de saisie de données.'
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: configure-bound-unbound-variables-associate-ui
source-git-commit: b817bcb02c4ff6ac369973ef658d9fcbdce95c51
workflow-type: tm+mt
source-wordcount: '1405'
ht-degree: 1%

---


# Configuration des variables liées et non liées pour l’interface utilisateur associée

Les variables liées et non liées dans les composants **Texte** permettent aux associés de saisir ou de confirmer des valeurs dans l’interface utilisateur associée. Une **variable liée** est liée à un champ dans le modèle de données de formulaire. Une **variable non liée** est définie dans le document et n’est pas liée au modèle de données.

Les auteurs activent la modification associée avec **Autoriser la modification par associé** soit sur le composant **Texte** soit sur des variables individuelles, mais pas les deux dans le même composant **Texte**.

| Qui | Avantage |
|-----|---------|
| **Auteur (concepteur de communication interactive)** | Choisissez si associe la modification en ligne dans l’aperçu ou champ par champ dans le panneau de saisie de données. |
| **Associé (agent/représentant de service)** | Saisissez dans le workflow les données qui correspondent le mieux à la communication : modification en ligne ou entrée de panneau structuré. |

## Avant de commencer

Activez **Associer la vue** sur la communication interactive avant de configurer des variables pour l’interface utilisateur d’Associer. Voir [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md).

Les associés doivent être membres du groupe **forms-associates**.

## Variables liées

Une variable liée est mappée à un champ dans le modèle de données de formulaire (par exemple, `deptName` sous `GMFletter`).

- Insérez en faisant glisser un champ du panneau **Modèle de données** vers un composant **Texte**.
- Le panneau **Champ** propriétés affiche **Nom**, **Valeur**, **Type d’affichage** et **Liaison**.

## Variables non liées

Une variable non liée est créée directement dans un composant **Texte** et n’est pas liée au modèle de données de formulaire (par exemple, `unboundvar`).

- Le panneau **Champ** propriétés affiche **Nom**, **Valeur**, **Type d’affichage** et **Liaison**.
- Sous **Associer les propriétés**, vous pouvez configurer **Info-bulle** et **Validations**.

## Modifier l’ensemble du composant Texte dans l’aperçu du document

Activez **Autoriser la modification par associé** sur le composant **Texte** et laissez-le désactivé pour chaque variable liée et non liée à l’intérieur du texte. Dans la vue Associé, l&#39;associé sélectionne le bloc de texte dans l&#39;aperçu du document. L’ensemble du composant **Texte** s’affiche avec une bordure violette et une barre d’outils de mise en forme.

### Configurer

1. Ouvrez la communication interactive dans l’éditeur de communication interactive sur l’onglet **Conception**.

1. Dans le panneau **Hiérarchie des composants**, sélectionnez le composant **Texte** qui contient vos variables liées et non liées, par exemple **Texte7**.

1. Vérifiez que le texte inclut des variables liées et non liées. Par exemple :

   - **Liaison de données : deptName**
   - **Unbound : unbound var**

   ![Sélection du composant Texte avec des variables liées et non liées](/help/forms/interactive-communication/assets/bound-unbound-variable1.png)

1. Dans le panneau des propriétés **Texte**, confirmez **Autoriser la modification par l’associé** est **désactivé** pour chaque variable liée et non liée à l’intérieur du texte.

1. Avec le composant **Texte** toujours sélectionné, activez **Autoriser la modification par associé** dans le panneau des propriétés **Texte**.

1. Cliquez sur **Enregistrer** et publiez la communication interactive.

### Vérifier dans l’interface utilisateur associée

1. Ouvrez la communication interactive dans **Vue associée**.

1. Sélectionnez le bloc de texte dans l&#39;aperçu du document. Confirmez que le composant **Texte** s’affiche avec une bordure violette et une barre d’outils de mise en forme.

1. Modifiez le contenu directement dans l’aperçu, par exemple, mettez à jour **Lié aux données : Service de l’application** et saisissez une valeur après **Non lié :**. Confirmez la mise à jour des variables liées et non liées en place.

   ![Modification du composant Texte entier en ligne dans l’interface utilisateur associée](/help/forms/interactive-communication/assets/bound-unbound-variable2.png)

1. Sélectionnez éventuellement **Aperçu de l’impression** pour confirmer que la sortie générée correspond à l’aperçu.

## Modifier des variables individuelles dans le panneau de saisie de données

Désactivez **Autoriser la modification par associé** sur le composant **Texte**. Activez-la pour chaque variable liée ou non liée que vous souhaitez que les associés modifient. Dans la vue Associer, chaque variable activée apparaît comme un champ distinct dans le panneau de saisie de données de gauche.

### Configurer

1. Ouvrez la communication interactive dans l’éditeur de communication interactive sur l’onglet **Conception**.

1. Dans le panneau **Hiérarchie des composants**, sélectionnez la variable liée, par exemple **deptName[1]**.

1. Dans le panneau des propriétés **Champ** :

   - Vérifiez que **Nom** est défini sur `deptName`.
   - Définissez **Type d’affichage** selon vos besoins (par exemple, **Aucun modèle**).
   - Activez **Autoriser la modification par associé**.

   ![Configurer la variable liée deptName pour l’interface utilisateur associée](/help/forms/interactive-communication/assets/bound-unbound-variable3.png)

1. Dans le panneau **Hiérarchie des composants**, sélectionnez la variable non liée, par exemple **unbound var**.

1. Dans le panneau des propriétés **Champ** :

   - Vérifiez que **Nom** est défini sur `unboundvar`.
   - Activez **Autoriser la modification par associé**.
   - Vous pouvez éventuellement configurer **Info-bulle** et **Validations** sous **Associer les propriétés**.

   ![Configurer la variable non liée unbound var pour l’interface utilisateur associée](/help/forms/interactive-communication/assets/bound-unbound-variable4.png)

1. Confirmez **Autoriser la modification par associé** est **désactivé** sur le composant **Texte** parent.

1. Cliquez sur **Enregistrer** et publiez la communication interactive.

### Vérifier dans l’interface utilisateur associée

1. Ouvrez la communication interactive dans **Vue associée**.

1. Confirmez chaque variable en activant l’option **Autoriser la modification par associé** qui apparaît dans le panneau de saisie de données de gauche, par exemple **deptName** et **unboundvar**.

1. Entrez **Département APP** pour **nomDépartement**. Laissez le champ **unboundvar** vide et confirmez que l’aperçu du document affiche le nom de la variable comme espace réservé, par exemple **Unbound: unboundvar**.

   ![Vérifier les variables liées et non liées dans le panneau de saisie de données de l’interface utilisateur associée](/help/forms/interactive-communication/assets/bound-unbound-variable5.png)

1. Saisissez **Variable non liée** pour **unbound var** et confirmez les mises à jour de l’aperçu du document en temps réel :

   - **Lié aux données : service de l’application** reflète la valeur saisie pour la variable liée.
   - **Non lié : Variable non liée** reflète la valeur saisie pour la variable non liée.

   ![Vérifier la valeur de variable non liée dans l’interface utilisateur associée](/help/forms/interactive-communication/assets/bound-unbound-variable6.png)

1. Sélectionnez éventuellement **Aperçu de l’impression** pour confirmer que la sortie générée correspond à l’aperçu.

## Noms de variables en double (liés et non liés)

Lorsque des variables liées et non liées portant le même nom apparaissent à plusieurs emplacements sur la zone de travail de conception, une seule instance de chaque nom de variable apparaît dans le panneau de saisie de données de gauche. L’associé saisit chaque valeur une fois ; il se propage automatiquement à toutes les occurrences correspondantes dans l’aperçu du document.

### Configurer

1. Ouvrez la communication interactive dans l’éditeur de communication interactive sur l’onglet **Conception**.

1. Ajoutez un **sous-formulaire** ou des composants **Texte** supplémentaires sur la zone de travail de conception et insérez des variables liées et non liées en double dans chaque emplacement. Par exemple, ajoutez deux blocs qui contiennent chacun :

   - **Liaison de données : deptName**
   - **Unbound : unbound var**

   ![Configurer des variables liées et non liées en double dans des sous-formulaires](/help/forms/interactive-communication/assets/bound-unbound-variable7.png)

1. Dans le panneau **Hiérarchie des composants**, sélectionnez chaque variable liée et non liée et activez **Autoriser la modification par associé** dans le panneau des propriétés **Champ**.

1. Confirmez **l’option Autoriser la modification par associé** est **désactivée** sur les composants **Texte** parents.

1. Cliquez sur **Enregistrer** et publiez la communication interactive.

### Vérifier dans l’interface utilisateur associée

1. Ouvrez la communication interactive dans **Vue associée**.

1. Confirmez qu’un seul champ **deptName** et qu’un champ **unboundvar** s’affichent dans le panneau de saisie de données de gauche, même si chaque variable se trouve à plusieurs emplacements sur la zone de travail de conception.

1. Entrez **Département APP** pour **nomDépartement**. Laissez **unbound var** vide et confirmez les deux occurrences dans la mise à jour de l’aperçu du document, par exemple, chaque bloc affiche **Data bound: APP Department** et **Unbound: unbound: unbound var**.

   ![Vérification de la propagation des variables en double dans l’interface utilisateur associée](/help/forms/interactive-communication/assets/bound-unbound-variable8.png)

1. Sélectionnez éventuellement **Aperçu de l’impression** pour confirmer que la sortie générée correspond à l’aperçu.

## Considérations

**Noms de variables en double (liés et non liés)**

Lorsque les variables liées et non liées partagent le même nom de variable :

- Une seule instance apparaît dans le panneau de saisie de données de gauche.
- Seules les variables pour lesquelles la modification associée est activée sont mises à jour dans l’aperçu du document.
- L’associé saisit la valeur une fois dans le panneau de saisie des données ; elle se propage automatiquement à toutes les occurrences correspondantes dans l’aperçu du document.

**Variables non liées portant le même nom mais ayant des valeurs par défaut différentes**

Lorsque plusieurs variables non liées partagent un nom de variable mais utilisent des valeurs par défaut différentes, l’interface utilisateur associée affiche la valeur par défaut de la première variable pour laquelle la modification associée est activée dans le panneau de saisie de données de gauche.

**Variables liées portant le même nom mais ayant des chemins de référence de données différents**

Lorsque plusieurs variables liées partagent un nom de variable mais utilisent différents chemins de référence de données, le panneau de saisie de données de gauche affiche la valeur de la première variable pour laquelle la modification associée est activée. Toute valeur saisie ou mise à jour par l’associé dans le panneau de saisie de données se propage à toutes les variables portant ce nom, quels que soient leurs chemins de référence de données.

**Exclusivité mutuelle**

**Autoriser la modification par associé** sur le composant **Texte** et sur les variables individuelles liées ou non liées qu’il contient s’excluent mutuellement. Activez une approche par composant **Texte**.

**Variables non liées sans valeur**

Lorsque la modification associée est activée pour une variable non liée, mais qu’aucune valeur n’est saisie, l’aperçu du document peut afficher le nom de la variable (par exemple, `unboundvar`) jusqu’à ce que l’associé fournisse une valeur dans le panneau de saisie de données.

## Questions fréquentes

**Quelle est la différence entre la modification de l’ensemble du composant Texte et la modification de variables individuelles ?**
Lorsque vous activez l’édition associée sur le composant **Texte**, l’utilisateur associé modifie l’ensemble du bloc de texte en ligne dans l’aperçu du document (bordure violette). Lorsque vous activez la modification associée sur des variables individuelles, chaque variable activée apparaît comme un champ distinct dans le panneau de saisie de données de gauche.

**Pourquoi ne puis-je pas activer la modification associée à la fois sur le composant Texte et sur les variables individuelles ?**
Les modifications apportées au composant **Texte** et aux variables liées ou non liées qu’il contient s’excluent mutuellement. Activez la modification sur l’ensemble du bloc de texte ou sur des variables individuelles, mais pas sur les deux.

**Pourquoi ma variable non liée affiche-t-elle le nom de la variable au lieu d’une valeur dans l’aperçu ?**
L’associé n’a probablement pas encore saisi de valeur. Lorsque la modification associée est activée sur des variables individuelles et qu’aucune valeur **Value** par défaut n’est configurée, l’aperçu peut afficher le nom de la variable jusqu’à ce que les données soient saisies dans le panneau de saisie de données.

**Quelle est la différence entre une variable liée et une variable non liée ?**
Une variable liée est liée à un champ de modèle de données de formulaire par le biais de la configuration **Binding**. Une variable non liée est définie dans le document et n’est pas liée au modèle de données.

**Que se passe-t-il lorsque deux variables partagent le même nom ?**
Une seule instance apparaît dans le panneau de saisie de données de gauche. L’associé saisit la valeur une fois dans le panneau de saisie des données et la propage automatiquement à toutes les occurrences correspondantes dans l’aperçu du document.

## Voir également

- [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Configurer les options de liste déroulante pour l’interface utilisateur associée](/help/forms/interactive-communication/associateui/configure-dropdown-options-binding.md)
- [Activer et configurer l’interface utilisateur associée pour les communications interactives](/help/forms/interactive-communication/enable-configure-associate-ui.md)
- [Composant de variable non lié dans l’éditeur de communication interactive](/help/forms/interactive-communication/unbound-variable.md)



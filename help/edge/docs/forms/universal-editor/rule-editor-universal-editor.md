---
title: Éditeur de règles pour Dynamic Forms dans l’éditeur universel
description: Créez des formulaires dynamiques et intelligents à l’aide de l’éditeur de règles dans l’éditeur universel. Ajoutez une logique conditionnelle, des calculs et des comportements interactifs sans codage.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '3597'
ht-degree: 23%

---


# Éditeur de règles pour Dynamic Forms dans l’éditeur universel

L’éditeur de règles de l’éditeur universel vous permet de créer des formulaires dynamiques intelligents qui répondent en temps réel aux entrées de l’utilisateur. Vous pouvez transformer des formulaires statiques en expériences interactives avec une visibilité de champ conditionnelle, des calculs automatisés et une logique d’entreprise complexe, le tout sans avoir à écrire de code.

## Ce que vous apprendrez :

À la fin de ce guide, vous pourrez :

- Comprendre le fonctionnement des règles et quand utiliser différents types de règle
- Activation et accès à l’éditeur de règles dans l’éditeur universel
- Créer une logique conditionnelle pour afficher ou masquer dynamiquement les champs de formulaire
- Implémenter des calculs automatisés et la validation des données
- Créer des fonctions personnalisées pour des règles métier complexes
- Appliquer les bonnes pratiques pour optimiser les performances des formulaires

## Pourquoi utiliser l’éditeur de règles ?

**Transformer le Forms statique en expériences intelligentes :**

- **Logique conditionnelle** : afficher les champs pertinents en fonction des sélections de l’utilisateur ou de l’utilisatrice
- **Calculs dynamiques** : calculez automatiquement les valeurs lorsque les utilisateurs saisissent
- **Validation des données** : fournissez des commentaires en temps réel et évitez les erreurs
- **Amélioration de l’expérience utilisateur** : réduit la complexité des formulaires et guide les utilisateurs et utilisatrices à travers les flux logiques
- **Aucun codage requis** : interface visuelle accessible aux non-développeurs.

**Cas d’utilisation courants :**

- Formulaires de calcul des taxes avec des déductions conditionnelles
- Assistants à plusieurs étapes avec chemins d’embranchement
- Formulaires d&#39;assurance avec calcul des taux
- Formulaires d&#39;enquête avec questions conditionnelles
- Formulaires de commerce électronique avec tarification dynamique

## Fonctionnement des règles

Les règles sont des instructions automatisées qui rendent vos formulaires intelligents et réactifs. Ils précisent ce qui doit se passer lorsque certaines conditions sont remplies.

### **Composants de règle**

**Condition** : test logique qui renvoie true ou false.

- « Le revenu de l’utilisateur est-il supérieur à 50 000 $ ? »
- « L’utilisateur a-t-il sélectionné « Oui » pour la couverture d’assurance ? »
- « Le champ de formulaire est-il vide ? »

**Action** : résultat qui se produit lorsque la condition est remplie.

- Afficher ou masquer des champs de formulaire
- Calculer les valeurs automatiquement
- Afficher les messages de validation
- Activation ou désactivation de composants

### **Modèles logiques de règle**

**1. Condition-Action (Alors)**

```
WHEN gross salary > 50000
THEN show "Additional Deduction" field
```

*Idéal pour :* visibilité de champ conditionnelle, contenu dynamique

**2. Action-Condition (Set-If)**

```
SET taxable income = gross salary - deductions
IF deductions are applicable
```

*Idéal pour :* calculs, transformations de données

**3. Action-Condition-Alternative (If-Then-Else)**

```
IF income > 50000
THEN show "High Income" fields
ELSE show "Standard Income" fields
```

*Idéal pour :* logique de branchement, options s’excluant mutuellement

### **Exemple concret**

**Scénario** : Formulaire de calcul de la taxe

- **Condition** : « Le salaire brut dépasse 50 000 $ »
- **Action de Principal** : afficher le champ « Déduction supplémentaire »
- **Autre action** : masquer le champ « Déduction supplémentaire »
- **Résultat** : les utilisateurs ne voient que les champs pertinents en fonction de leur niveau de revenu

## Prérequis

Avant de commencer à utiliser l’éditeur de règles, vérifiez que vous disposez des éléments suivants :

### **Conditions d’accès**

- Accès en création à **AEM as a Cloud Service**
- **Éditeur universel** avec l’extension d’éditeur de règles activée
- Autorisations d’édition de formulaires dans votre environnement AEM

### **Exigences techniques**

- **Connaissances de base en matière de conception de formulaire** : connaissance des composants de formulaire et de leurs propriétés
- **Familiarité avec la logique commerciale** : capacité à définir des exigences conditionnelles
- **Connaissances de base de JavaScript** (uniquement requises pour les fonctions personnalisées)

### **Activer l’extension de l’éditeur de règles**

L’extension Éditeur de règles n’est pas activée par défaut dans l’éditeur universel. Vous pouvez l’activer à partir de [Extension Manager](/help/implementing/developing/extending/extension-manager.md).

**Après avoir activé l’extension :**
L’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg) s’affiche dans le coin supérieur droit lorsque vous sélectionnez des composants de formulaire.

![Éditeur universel de règles](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
*Image : l’icône Éditeur de règles s’affiche lorsque vous sélectionnez des composants de formulaire*

**Pour accéder à l’éditeur de règles, procédez comme suit**

1. Sélectionnez un composant de formulaire dans l’éditeur universel.
2. Cliquez sur l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg) qui s’affiche.
3. L’interface de l’éditeur de règles s’ouvre dans un nouveau panneau.

![Interface utilisateur de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-for-field.png)
*Image : interface de l’éditeur de règles pour la modification des règles de composant*

>[!NOTE]
>
> Dans cet article, « composant de formulaire » et « objet de formulaire » se rapportent aux mêmes éléments (tels que les champs de saisie, les boutons, les panneaux, etc.).

## Aperçu de l’interface de l’éditeur de règles

L’éditeur de règles offre une interface visuelle conviviale pour la création et la gestion des règles :

![Interface utilisateur de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-interface.png)
*Image : interface complète de l’éditeur de règles avec des composants numérotés*

### **Composants d’interface**

**1. Titre du composant et type de règle**

- **Objectif** : affiche le nom du composant sélectionné et le type de règle actuel.
- **Exemple** : « Saisir le salaire brut » (entrée de texte) avec la règle « Lorsque » sélectionnée.
- **Conseil** : vérifiez toujours que vous modifiez le composant approprié.

**2. Panneau Objets de formulaire et fonctions**

- **Onglet Objets de formulaire** : fournit une vue hiérarchique de tous les composants de formulaire.
   - À utiliser pour : référencer d’autres champs dans vos règles.
   - Navigation : développez ou réduisez pour localiser des composants spécifiques.
- **Onglet Fonctions** : contient des fonctions mathématiques et logiques intégrées.
   - Utiliser pour : effectuer des calculs et des manipulations de données complexes.
   - Catégories : Fonctions mathématiques, chaîne, date et validation.

**3. Bouton Bascule Du Panneau**

- **Objectif** : affiche ou masque le panneau des objets et des fonctions.
- **Conseil** : basculez hors du panneau pour augmenter l’espace de travail de modification des règles.
- **Raccourci clavier** : utile lorsque vous travaillez avec des règles complexes.

**4. Créateur de règles visuel**

- **Objectif** : zone principale pour la création d’une logique de règle.
- **Fonctions** : interface glisser-déposer et sélecteurs de liste déroulante.
- **Workflow** : sélectionnez le type de règle → Définir des conditions → Définir des actions.

**5. Boutons de contrôle**

- **Terminé** : enregistre la règle et ferme l’éditeur.
- **Annuler** : ignore les modifications et ferme l’éditeur sans enregistrer.
- **Conseil** : testez toujours vos règles avant de cliquer sur Terminé.

### **Gestion des règles**

Lorsque vous ouvrez l’éditeur de règles pour un composant qui comporte déjà des règles :

![afficher les règles disponibles de l’objet de formulaire](/help/edge/docs/forms/assets/rule-editor15.png)
*Image : gestion des règles existantes pour un composant de formulaire*

**Actions disponibles :**

- **Afficher** : consulter les résumés et la logique des règles.
- **Modifier** : permet de modifier des conditions ou des actions de règle existantes.
- **Réorganiser** : permet de modifier l’ordre d’exécution des règles (qui s’exécutent de haut en bas).
- **Activer/désactiver** : activer ou désactiver temporairement les règles à des fins de test.
- **Supprimer** : supprimez définitivement des règles.

>[!TIP]
>
> **L’ordre d’exécution des règles est important** : les règles sont exécutées de haut en bas. Placez des conditions plus spécifiques avant des conditions générales.

## Types de règle disponibles

L’éditeur de règles propose un ensemble complet de types de règle organisés par fonctionnalité. Sélectionnez le type approprié en fonction de votre cas d’utilisation spécifique :

### **Règles de logique conditionnelle**

**Lorsque**

- **Objectif** : sert de règle conditionnelle principale pour l’implémentation d’une logique complexe.
- **Cas d’utilisation** : par exemple, « Lorsque l’utilisateur sélectionne « Marié(e) », afficher les champs d’informations sur le conjoint ».
- **Modèle logique** : condition → action (avec une autre action facultative)

**Masquer/Afficher**

- **Objectif** : contrôle la visibilité du champ en fonction de conditions spécifiées.
- **Cas d’utilisation** : masquer les sections non pertinentes ou permettre la divulgation progressive.
- **Bonne pratique** : permet de créer une expérience utilisateur nette et ciblée.

**Activer/Désactiver**

- **Objectif** : contrôle si un champ peut faire l’objet d’une interaction, en fonction de conditions.
- **Cas d’utilisation** : désactivez le bouton d’envoi jusqu’à ce que tous les champs obligatoires soient remplis.
- **Bonne pratique** : envoyez des commentaires visuels clairs aux utilisateurs et utilisatrices.

### **Règles de manipulation des données**

**Définir la valeur de**

- **Objectif** : renseigne automatiquement les valeurs de champ.
- **Cas d’utilisation** : définir la date d’aujourd’hui, calculer des totaux ou copier des valeurs entre des champs.
- **Bonne pratique** : utilisez pour réduire l’effort de l’utilisateur et garantir la précision.

**Effacer la valeur de**

- **Objectif** : supprime les données des champs lorsque les conditions changent.
- **Cas d’utilisation** : effacer les champs dépendants lorsqu’une sélection parent est modifiée.
- **Bonne pratique** : préserver l’intégrité des données et empêcher les valeurs orphelines.

**Format**

- **Objectif** : permet de transformer l’affichage des valeurs.
- **Cas d’utilisation** : mise en forme de la devise, des numéros de téléphone ou des dates.
- **Bonne pratique** : améliorez la lisibilité sans modifier les données sous-jacentes.

### **Règles de validation**

**Valider**

- **Objectif** : implémente une logique de validation personnalisée.
- **Cas d’utilisation** : appliquer des règles métier complexes ou une validation entre champs.
- **Bonne pratique** : fournissez des messages d’erreur clairs et exploitables.

### **Règles de calcul**

**Expression mathématique**

- **Objectif** : effectue des calculs automatisés.
- **Cas pratique** : calculs de taxe, totaux ou pourcentages.
- **Bonne pratique** : mettez à jour les calculs en temps réel au fur et à mesure que les utilisateurs saisissent des données.

### **Règles de l’interface utilisateur**

**Définir le focus**

- **Objectif** : dirige l’attention de l’utilisateur ou de l’utilisatrice vers des champs spécifiques.
- **Cas d’utilisation** : concentrez-vous sur les champs d’erreur ou guidez les utilisateurs tout au long des étapes de l’assistant.
- **Bonne pratique** : utilisez cette option avec parcimonie afin d’éviter de perturber le flux utilisateur.

**Définir la propriété**

- **Objectif** : modifie de manière dynamique les propriétés du composant.
- **Cas d’utilisation** : modifiez le texte de l’espace réservé ou les options dans une liste déroulante.
- **Bonne pratique** : améliorez l’expérience utilisateur grâce aux modifications contextuelles.

### **Règles de contrôle de formulaire**

**Envoyer le formulaire**

- **Objectif** : déclenche l’envoi du formulaire par programmation.
- **Cas d’utilisation** : envoi automatique une fois les conditions spécifiques remplies.
- **Bonne pratique** : validez toujours le formulaire avant envoi.

**Réinitialiser le formulaire**

- **Objectif** : efface toutes les données du formulaire et réinitialise le formulaire à son état initial.
- **Cas d’utilisation** : fonctionnalité « Recommencer ».
- **Bonne pratique** : confirmez l’action avec l’utilisateur ou l’utilisatrice avant la réinitialisation.

**Enregistrer le formulaire**

- **Objectif** : enregistre le formulaire en tant que brouillon pour une saisie ultérieure.
- **Cas pratique** : utile pour les formulaires longs ou les workflows multi-sessions.
- **Bonne pratique** : fournissez des commentaires clairs sur le statut d’enregistrement.

### **Règles avancées**

**Appeler le service**

- **Objectif** : appelle des API ou des services externes.
- **Cas d’utilisation** : recherche d’adresses, validation en temps réel ou enrichissement des données.
- **Bonne pratique** : gérez les états de chargement et les scénarios d’erreur de manière appropriée.

**Ajouter/Supprimer une instance**

- **Objectif** : gère de manière dynamique les sections répétables.
- **Cas d’utilisation** : ajoutez des membres de la famille ou plusieurs adresses.
- **Bonne pratique** : fournissez des commandes claires pour l’ajout ou la suppression d’instances.

**Accéder À**

- **Objectif** : redirige les utilisateurs vers d’autres formulaires ou pages.
- **Cas pratique** : workflows à formulaires multiples ou routage conditionnel.
- **Bonne pratique** : conserver les données de formulaire avant la navigation.

**Navigation Dans Les Panneaux**

- **Objectif** : contrôle la navigation dans les formulaires de type assistant.
- **Cas pratique** : formulaires à plusieurs étapes ou saut d’étape conditionnel.
- **Bonne pratique** : afficher des indicateurs de progression clairs.

**Distribuer l’événement**

- **Objectif** : déclenche des événements personnalisés pour les intégrations avancées.
- **Cas d’utilisation** : suivi Analytics ou intégrations tierces.
- **Bonne pratique** : à utiliser uniquement pour les actions non bloquantes.


## Tutoriel détaillé : Créer un calculateur d&#39;impôt intelligent

Cette section fournit un exemple pratique pour démontrer les fonctionnalités de l’éditeur de règles. Cet exemple vous guide tout au long de la création d&#39;un formulaire de calcul des taxes qui utilise une logique conditionnelle et des calculs automatisés.

![Capture d’écran de l’interface de l’éditeur de règles présentant la création d’une règle conditionnelle avec la logique de date et heure pour la visibilité des champs de formulaire](/help/edge/docs/forms/assets/rule-editor-1.png)
*Image : formulaire de calcul des taxes avec des champs conditionnels intelligents*

### **Présentation du tutoriel**

Dans ce tutoriel, vous allez créer un formulaire qui :

1. **S’adapte à la saisie utilisateur** : affiche les champs pertinents en fonction du niveau de revenu.
2. **Calcule automatiquement** : Calcule la dette fiscale en temps réel.
3. **Valide les données** : garantit des calculs et une saisie de données précis.

### **Structure de formulaire**

| Nom du champ | Type | Objectif | Comportement |
|------------|------|---------|----------|
| **Salaire brut** | Entrée de nombre | L’utilisateur saisit son revenu annuel | Déclenche une logique conditionnelle |
| **Déduction supplémentaire** | Entrée de nombre | Déductions supplémentaires (le cas échéant) | S&#39;affiche lorsque le salaire > 50 000 $ |
| **Revenu imposable** | Entrée de nombre | Calculé automatiquement | Mises à jour des modifications d’entrée |
| **Impôt à payer** | Entrée de nombre | Montant final de la taxe | Calcule au taux de 10 % |

### **Logique commerciale à mettre en œuvre**

**Règle 1 : Affichage Conditionnel Des Champs**

```
WHEN Gross Salary > 50,000
THEN Show "Additional Deduction" field
ELSE Hide "Additional Deduction" field
```

**Règle 2 : Calcul Du Revenu Imposable**

```
SET Taxable Income = Gross Salary - Additional Deduction
(When Additional Deduction is applicable)
```

**Règle 3 : Calcul de l&#39;impôt**

```
SET Tax Payable = Taxable Income × 10%
(Simplified flat rate for demonstration)
```

### **Étapes d’implémentation**

Pour créer votre formulaire de déclaration intelligent, procédez comme suit :



+++ 1 : créer le formulaire de base

**Objectif** : créer la structure de formulaire de base avec tous les composants requis.

Pour créer votre formulaire de calcul des taxes dans l&#39;éditeur universel :

1. **Ouvrir l’éditeur universel**
   - Accédez à la console AEM Sites
   - Sélectionnez la page où vous souhaitez ajouter le formulaire
   - Cliquez sur **Modifier** pour ouvrir l’éditeur universel

2. **Ajouter des composants de formulaire**

   Ajoutez ces composants dans l’ordre :

   | Composant | Type | Libellé | Paramètres |
   |-----------|------|-------|----------|
   | Titre | Titre | « Formulaire de calcul des taxes » | Niveau de titre H2 |
   | Entrée de nombre | Entrée de nombre | « Salaire Brut » | Obligatoire : Oui, Espace réservé : « Saisir le salaire annuel » |
   | Entrée de nombre | Entrée de nombre | « Déduction supplémentaire » | Obligatoire : Non, Espace réservé : « Saisir des déductions supplémentaires » |
   | Entrée de nombre | Entrée de nombre | « Revenu imposable » | Obligatoire : Non, Lecture seule : Oui |
   | Entrée de nombre | Entrée de nombre | « Impôt à payer » | Obligatoire : Non, Lecture seule : Oui |
   | Bouton Envoyer | Envoyer | « Calculer la taxe » | Type : Envoyer |

3. **Configurer les paramètres initiaux**

   - **Masquez le champ Déduction supplémentaire** :
      - Sélectionnez le composant « Déduction supplémentaire »
      - Dans le panneau Propriétés, définissez **Visible** sur **Non**
      - Ce champ s’affiche de manière conditionnelle en fonction des règles

   - **Rendre les champs calculés en lecture seule** :
      - Sélectionnez les champs « Revenu imposable » et « Impôt à payer »
      - Définissez **Lecture seule** sur **Oui** dans Propriétés

     ![Capture d’écran d’un formulaire de calcul des impôts avec des champs de saisie pour le salaire brut, la situation de famille et les enfants à charge, présentant la structure du formulaire avant l’application des règles](/help/edge/docs/forms/assets/rule-editor2.png)
     *Image : structure de formulaire initiale avec composants de base configurés*

**Point de contrôle** : vous devez maintenant disposer d’un formulaire avec tous les champs obligatoires, où la « Déduction supplémentaire » est masquée et les champs calculés sont en lecture seule.

+++

+++ 2. Ajouter une règle conditionnelle pour un champ de formulaire

Une fois que vous avez créé le formulaire, écrivez la première règle pour n’afficher le champ `Additional Deduction` que si le salaire brut dépasse 50 000 $. Pour ajouter une règle conditionnelle, procédez comme suit :

1. Ouvrez un formulaire dans l’éditeur universel pour le modifier, puis sélectionnez le champ **[!UICONTROL Salaire brut]** dans l’arborescence de contenu et sélectionnez ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Vous pouvez également sélectionner le champ **[!UICONTROL Salaire brut]** directement dans le volet **[!UICONTROL Objet Forms]**.
   ![Exemple 1 de l’Éditeur de règles](/help/edge/docs/forms/assets/rule-editor3.png)
L’interface visuelle de l’Éditeur de règles s’affiche.
1. Cliquez sur **[!UICONTROL Créer]** pour créer des règles.
   ![Exemple 2 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor4.png)
Par défaut, le type de règle `Set Value Of` est sélectionné. Bien que vous ne puissiez pas changer ou modifier l’objet sélectionné, vous pouvez utiliser la liste déroulante de règles pour sélectionner un autre type de règle.\
   ![Exemple 3 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor5.png)
1. Ouvrez la liste déroulante des types de règles et sélectionnez le type de règle **[!UICONTROL Lorsque]**.
   ![Exemple 4 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor6.png)
1. Sélectionnez le menu déroulant **[!UICONTROL Sélectionner l’état]** et choisissez **[!UICONTROL est supérieur à]**. Le champ **[!UICONTROL Saisissez un nombre]** s’affiche.
   ![Exemple 5 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor7.png)
1. Saisissez `50000` dans le champ **[!UICONTROL Saisissez un nombre]** de la règle.
   ![Exemple 6 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor8.png)
Vous avez défini la condition comme `When Gross Salary is greater than 50000`. Définissez ensuite l’action à effectuer si cette condition est `True`.
1. Dans l’instruction `Then`, sélectionnez **[!UICONTROL Afficher]** dans le menu déroulant **[!UICONTROL Sélectionner une action]**.
   ![Exemple 7 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor9.png)
1. Faites glisser et déposez le champ **[!UICONTROL Déduction supplémentaire]** de l’onglet Objets de formulaire vers le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**. Vous pouvez également sélectionner le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**, puis le champ **[!UICONTROL Déduction supplémentaire]** dans le menu contextuel, qui répertorie tous les objets de formulaire dans le formulaire.
   ![Exemple 8 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor10.png)
1. Cliquez sur **[!UICONTROL Ajouter une section Else]** pour ajouter une autre condition pour le champ **[!UICONTROL Salaire brut]**, au cas où vous saisissez un salaire inférieur à `50000`.
   ![Exemple 9 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor11.png)
1. Sélectionnez **[!UICONTROL Masquer]** dans le menu déroulant **[!UICONTROL Sélectionner une action]** de l’instruction `Else`.
   ![Exemple 10 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor12.png)
1. Faites glisser et déposez le champ **[!UICONTROL Déduction supplémentaire]** de l’onglet Objets de formulaire vers le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**. Vous pouvez également sélectionner le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**, puis le champ **[!UICONTROL Déduction supplémentaire]** dans le menu contextuel, qui répertorie tous les objets de formulaire dans le formulaire.
   ![Exemple 11 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor13.png)
1. Sélectionnez **[!UICONTROL Terminé]** pour enregistrer la règle.
La règle s’affiche comme suit dans l’éditeur de règles.
   ![Exemple 12 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> Vous pouvez également créer une règle Afficher dans le champ Déduction supplémentaire, au lieu d’une règle Lorsque dans le champ Salaire brut pour mettre en œuvre le même comportement.

+++

+++ &#x200B;3. Ajouter des règles de calcul pour les champs du formulaire

Ensuite, créez une règle pour calculer le `Taxable Income`, qui est la différence entre `Gross Salary` et `Additional Deduction` (le cas échéant). Pour ajouter une règle de calcul dans le champ **[!UICONTROL Revenu imposable]**, procédez comme suit :

1. En mode Création, sélectionnez le champ **[!UICONTROL Revenu imposable]**, puis l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Vous pouvez également sélectionner le champ **[!UICONTROL Revenu imposable]** directement à partir du volet **[!UICONTROL Objet Forms]**.
1. Sélectionnez ensuite **[!UICONTROL Créer]** pour créer la règle.
   ![Exemple 13 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor16.png)
1. Choisissez **[!UICONTROL Sélectionner l’option]** et sélectionnez **[!UICONTROL Expression mathématique]**. Un champ permettant de saisir l’expression mathématique s’ouvre.
   ![Exemple 14 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor17.png)

1. Dans le champ de l’expression mathématique :

   - Sélectionnez ou glissez-déposez, depuis l’onglet Objets de formulaire, le champ **[!UICONTROL Salaire brut]** dans le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   - Sélectionnez **[!UICONTROL Moins]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   - Sélectionnez ou faites glisser et déposez, depuis l’onglet Objet de formulaire, le champ **[!UICONTROL Déduction supplémentaire]** dans l’autre champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.
     ![Exemple 15 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor18.png)

1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

   Ajoutez à présent une règle pour le champ `Tax Payable `, qui est déterminée en multipliant le revenu imposable par le taux de taxation. Pour plus de simplicité, prenons un taux de taxation fixe de `10%`.

1. En mode Création, sélectionnez le champ **[!UICONTROL Impôt à payer]**, puis l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Sélectionnez ensuite **[!UICONTROL Créer]** pour créer des règles.
   ![Exemple 16 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor19.png)
1. Choisissez **[!UICONTROL Sélectionner l’option]** et sélectionnez **[!UICONTROL Expression mathématique]**. Un champ permettant de saisir l’expression mathématique s’ouvre.
   ![Exemple 17 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor20.png)
1. Dans le champ de l’expression mathématique :

   - Sélectionnez ou glissez-déposez, depuis l’onglet Objets de formulaire, le champ **[!UICONTROL Revenu imposable]** dans le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   - Sélectionnez **[!UICONTROL Multiplié par]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   - Sélectionnez **Nombre** dans le champ **[!UICONTROL Sélectionner une option]** et saisissez la valeur `10` dans le champ **[!UICONTROL Saisir un nombre]**.
     ![Exemple 18 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor21.png)
1. Ensuite, sélectionnez la zone en surbrillance autour du champ Expression et choisissez **[!UICONTROL Étendre l’expression]**.
   ![Exemple 19 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor22.png)
1. Dans le champ d’expression étendue, sélectionnez **[!UICONTROL divisé par]** dans le champ **[!UICONTROL Sélectionner un opérateur]** et **[!UICONTROL Nombre]** dans le champ **[!UICONTROL Sélectionner une option]**. Spécifiez ensuite la valeur `100` dans le champ Nombre.
   ![Exemple 20 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor23.png)
1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

+++

+++ &#x200B;4. Prévisualiser un formulaire

Désormais, lorsque vous prévisualisez le formulaire et saisissez `60,000` pour le **Salaire brut**, le champ **Déduction supplémentaire** s’affiche et les champs **Revenu imposable** et **Impôt à payer** sont calculés en conséquence.

![Prévisualiser un formulaire](/help/edge/docs/forms/assets/rule-editor-form.png)

+++

Outre les fonctions intégrées telles que Somme et Moyenne, vous pouvez créer des fonctions personnalisées pour implémenter une logique commerciale complexe adaptée à vos besoins spécifiques.

## Avancé : fonctions personnalisées

**Utilisation des fonctions personnalisées :**

- Pour les calculs complexes qui vont au-delà des fonctionnalités des fonctions intégrées
- Pour mettre en œuvre des règles de validation spécifiques à l’entreprise
- Pour les transformations et la mise en forme de données
- Pour l’intégration à des systèmes ou des API externes

**Avantages :**

- **Réutilisation** : écrivez la fonction une seule fois et utilisez-la dans plusieurs formulaires et règles
- **maintenabilité** : logique centralisée facile à mettre à jour
- **Performance** : exécution JavaScript optimisée
- **Flexibilité** : capacité à gérer des scénarios complexes non pris en charge par les règles standard

### **Création de fonctions personnalisées**

**Emplacement du fichier** : `/blocks/form/functions.js` dans votre projet AEM

**Workflow de développement :**

1. **Déclaration de fonction**
   - Définir des noms et des paramètres de fonction clairs et descriptifs
   - Utilisez des noms qui indiquent l’objectif de la fonction
   - Paramètres du document et types de retour

2. **Implémentation logique**
   - Écrire du code JavaScript propre et efficace
   - Gérer les cas de périphérie et les scénarios d’erreur
   - Respect des bonnes pratiques en matière de codage

3. **Exportation de fonction**
   - Fonctions d’exportation pour les rendre disponibles dans l’éditeur de règles
   - Utiliser les exportations nommées pour une meilleure organisation
   - Fonctions de test avant le déploiement

4. **Documentation**
   - Ajout de commentaires JSDoc à la documentation des fonctions
   - Inclure des exemples d’utilisation
   - Spécifier les types de paramètres et les valeurs de retour

L’exemple suivant illustre deux fonctions personnalisées : `getFullName` et `days`.

```JavaScript
/**
 - Get Full Name
 - @name getFullName Concats first name and last name
 - @param {string} firstname in Stringformat
 - @param {string} lastname in Stringformat
 - @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 - Calculate the number of days between two dates.
 - @param {*} endDate
 - @param {*} startDate
 - @name days Calculates the numebr of days between two dates
 - @returns {number} returns the number of days between two dates
 */
function days(endDate, startDate) {
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // return zero if dates are valid
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// eslint-disable-next-line import/prefer-default-export
export { getFullName, days };
```

![Ajout d’une fonction personnalisée](/help/edge/docs/forms/assets/create-custom-function.png)

### Utiliser une fonction personnalisée dans l’éditeur de règles

Pour utiliser une fonction personnalisée dans l’éditeur de règles :

1. **Ajouter la fonction** : ajoutez votre fonction personnalisée au fichier `../[blocks]/form/functions.js`. Veillez à l’inclure dans l’instruction `export` du fichier .
2. **Déployer le fichier** : déployez le fichier `functions.js` mis à jour sur votre projet GitHub et vérifiez que la version s’est terminée correctement.
3. **Utilisation de la fonction** : dans l’éditeur de règles de votre formulaire, accédez à la fonction en sélectionnant l’option `Function Output` dans le champ **[!UICONTROL Sélectionner une action]**.

   ![Fonctions personnalisées dans l’éditeur de règles](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

4. **Prévisualiser le formulaire** : prévisualisez votre formulaire pour vérifier que la nouvelle fonction implémentée fonctionne comme prévu.

## Bonnes pratiques pour le développement de règles

### **Optimisation des performances**

**Réduire la complexité des règles**

- Veillez à ce que les règles individuelles restent simples et ciblées.
- Divisez une logique complexe en plusieurs règles plus petites.
- Dans la mesure du possible, évitez les conditions profondément imbriquées.

**Optimiser l’exécution des règles**

- Placez d’abord les règles les plus fréquemment déclenchées.
- Utilisez des conditions spécifiques pour réduire les évaluations inutiles.
- Tenez compte de l’impact des règles sur le temps de chargement des formulaires.

**Gestion des ressources**

- Limitez le nombre de règles par composant de formulaire.
- Utilisez des fonctions personnalisées pour une logique répétée au lieu de dupliquer des règles.
- Testez les performances avec des volumes de données réalistes.

### **Consignes relatives à l’expérience utilisateur**

**Fournir des commentaires clairs**

- Utilisez des messages de validation qui guident les utilisateurs vers une entrée correcte.
- Affichez les indicateurs de chargement pour les règles qui impliquent des services externes.
- Mettre en œuvre la divulgation progressive pour réduire la charge cognitive.

**Conserver La Réactivité Du Formulaire**

- Évitez les règles qui provoquent des changements visuels brusques.
- Implémentez des transitions lisses pour les opérations d’affichage/masquage.
- Testez des règles sur différents appareils et tailles d’écran.

**Gestion des erreurs**

- Fournissez un comportement de secours en cas d’échec des règles.
- Afficher des messages d’erreur conviviaux.
- Consigner les erreurs pour le débogage tout en conservant une expérience utilisateur positive.

### **Meilleures pratiques de développement**

**Stratégie de test**

- Testez des règles avec des cas de périphérie et des valeurs limites.
- Vérifiez le comportement des règles dans différents navigateurs.
- Testez la fonctionnalité de formulaire avec et sans JavaScript activé.

**Documentation**

- Documentez la logique commerciale derrière des règles complexes.
- Tenez à jour un inventaire des règles pour les formulaires volumineux.
- Utilisez des conventions de nommage cohérentes pour les composants et les règles.

**Contrôle de version**

- Suivi des modifications apportées aux fonctions personnalisées dans le contrôle de version.
- Testez les règles dans un environnement de développement avant la production.
- Conservez les copies de sauvegarde des configurations de règles de travail.

## Résolution des problèmes courants

### **Problèmes d’exécution des règles**

**Règles non déclenchées**

- **Vérifier les noms des composants** : vérifiez que les composants référencés existent et portent des noms corrects.
- **Vérifier l’ordre des règles** : les règles s’exécutent de haut en bas ; à réorganiser si nécessaire.
- **Valider les conditions** : tester les conditions avec des valeurs connues pour vérifier la logique.
- **Console du navigateur** : recherchez les erreurs JavaScript susceptibles de bloquer l’exécution.

**Comportement de règle incorrect**

- **Vérifier les opérateurs logiques** : les conditions ET/OU sont correctement structurées.
- **Tester avec des exemples de données** : utilisez des valeurs connues pour isoler les problèmes.
- **Vérifier les types de données** : assurez-vous que les comparaisons numériques utilisent des nombres, et non des chaînes.
- **Valider les expressions** : testez séparément les expressions mathématiques.

### **Problèmes de performances**

**Réponse de formulaire lente**

- **Réduire la complexité des règles** : simplifiez la logique conditionnelle complexe.
- **Optimiser les fonctions personnalisées** : définissez un profil et optimisez le code JavaScript.
- **Limiter les appels externes** : réduisez les appels de service dans les règles.
- **Utilisation de sélecteurs efficaces** : assurez-vous que les références à l’objet de formulaire sont spécifiques.

**Utilisation de la mémoire**

- **Nettoyer les écouteurs d’événement** : supprimer les liaisons de règle inutilisées.
- **Optimisation des fonctions personnalisées** : évitez les fuites de mémoire dans le code JavaScript.
- **Limiter la portée de la règle** : utilisez des règles ciblées au lieu de conditions globales.

### **Problèmes de fonction personnalisée**

**Fonctions Non Disponibles**

- **Vérifier le chemin d’accès au fichier** : vérifiez `functions.js` se trouve à l’emplacement correct : `/blocks/form/functions.js`.
- **Vérifier les exportations** : assurez-vous que les fonctions sont correctement exportées.
- **Processus de création** : vérifiez que la création du projet comprend le fichier de fonctions mis à jour.
- **Effacement du cache** : effacez le cache du navigateur après le déploiement de nouvelles fonctions.

**Erreurs de fonction**

- **Validation des paramètres** : vérifiez que les paramètres de fonction correspondent aux types attendus.
- **Gestion des erreurs** : ajoutez des blocs try-catch pour gérer les exceptions de manière appropriée.
- **Journalisation de la console** : utilisez console.log pour l’exécution de la fonction de débogage.
- **Validation JSDoc** : assurez-vous que la documentation de la fonction correspond à l’implémentation.

### **Intégration de l’éditeur universel**

**L’Éditeur De Règles N’Apparaît Pas**

- **Extension activée** : vérifiez que l’extension de l’éditeur de règles est activée.
- **Sélection de composant** : vérifiez que vous avez sélectionné un composant de formulaire pris en charge.
- **Compatibilité des navigateurs** : test dans les navigateurs pris en charge (Chrome, Firefox, Safari).
- **Autorisations d’accès** : vérifiez que l’utilisateur dispose des autorisations AEM nécessaires.

**Problèmes d’interface**

- **Visibilité du panneau** : utilisez le bouton de basculement pour afficher ou masquer le panneau des objets de formulaire.
- **Enregistrement des règles** : assurez-vous que les règles sont enregistrées avant de fermer l’éditeur.
- **Zoom du navigateur** : réinitialisez le zoom du navigateur sur 100 % pour un affichage optimal de l’interface.

## Limites importantes

>[!IMPORTANT]
>
> **Restrictions des fonctions personnalisées** :
>
> - Les imports statiques et dynamiques ne sont pas pris en charge dans les scripts de fonction personnalisée.
> - Tout le code doit être inclus directement dans le fichier `/blocks/form/functions.js`.
> - Les fonctions doivent être synchrones (pas d’async/await ni de promesse).
> - L’accès aux API du navigateur est limité pour des raisons de sécurité.

>[!WARNING]
>
> **Considérations relatives à la production** :
>
> - Testez minutieusement toutes les règles dans un environnement d’évaluation.
> - Surveillez les performances des formulaires après le déploiement de règles complexes.
> - Disposer d’un plan de restauration pour les problèmes liés aux règles.
> - Tenez compte de l’impact sur les utilisateurs et utilisatrices disposant de connexions réseau lentes.

## Résumé

L’éditeur de règles de l’éditeur universel vous permet de créer des formulaires dynamiques intelligents qui offrent des expériences utilisateur exceptionnelles. En implémentant une logique conditionnelle, des calculs automatisés et des règles métier personnalisées, vous pouvez :

**Transformer le Forms statique** :

- Ajoutez une visibilité de champ conditionnelle pour des interfaces plus propres et plus ciblées.
- Mettez en œuvre des calculs en temps réel et la validation des données.
- Créez une logique commerciale sophistiquée sans codage.

**Améliorer l’expérience utilisateur** :

- Guidez les utilisateurs à travers les flux de formulaires logiques.
- Réduisez les erreurs grâce à une validation intelligente.
- Fournissez une assistance et des commentaires immédiats.

**Améliorez l’efficacité** :

- Automatisez les calculs répétitifs et la saisie de données.
- Rationalisez les workflows complexes avec le routage intelligent.
- Réduisez la charge de support grâce à des fonctionnalités en libre-service.

### **Étapes suivantes**

Maintenant que vous comprenez les principes de base de l’éditeur de règles :

1. **Démarrer simplement** : commencez par utiliser les règles de base d’affichage/masquage avant de passer à des calculs complexes.
1. **Pratiquez avec des exemples** : utilisez le tutoriel sur le calculateur d’impôt comme base.
1. **Explorer les fonctionnalités avancées** : tester les fonctions personnalisées en fonction des besoins spécifiques.
1. **Tester minutieusement** : toujours valider les règles dans différents scénarios et appareils.
1. **Surveiller les performances** : assurez-vous que les règles améliorent l’expérience utilisateur plutôt que de la gêner.

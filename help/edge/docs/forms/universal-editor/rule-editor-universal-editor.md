---
title: Éditeur de règles pour les formulaires Edge Delivery Services
description: Créez des formulaires dynamiques et intelligents à l’aide de l’éditeur de règles dans l’éditeur universel. Ajoutez une logique conditionnelle, des calculs et des comportements interactifs sans codage.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 0d088d4e3b4e27fac0a05ff93a7fd01535bba6af
workflow-type: ht
source-wordcount: '2824'
ht-degree: 100%

---


# Éditeur de règles pour les formulaires Edge Delivery Services

L’éditeur de règles permet aux créateurs et aux créatrices de transformer des formulaires statiques en expériences réactives et intelligentes, sans avoir à écrire de code. Vous pouvez afficher des champs de manière conditionnelle, effectuer des calculs, valider des données, guider les utilisateurs et les utilisatrices tout au long des flux et intégrer une logique commerciale qui s’adapte lors de la saisie des personnes.

## Ce que vous apprendrez :

À la fin de ce guide, vous serez en mesure d’accomplir ce qui suit :

- Comprendre le fonctionnement des règles et quand utiliser différents types de règles
- Activer l’éditeur de règles dans l’éditeur universel et y accéder
- Créer une logique conditionnelle pour afficher ou masquer les champs de manière dynamique
- Implémenter des calculs automatisés et la validation des données
- Créer des fonctions personnalisées pour des règles métier complexes
- Appliquer les bonnes pratiques en matière de performances, de facilité de maintenance et d’expérience d’utilisation

## Pourquoi utiliser l’éditeur de règles ?

- **Logique conditionnelle** : affichez les champs pertinents uniquement lorsque cela est nécessaire pour réduire le bruit et la charge cognitive.
- **Calculs dynamiques** : calculez automatiquement les valeurs (totaux, taux, taxes) au fur et à mesure de la saisie des utilisateurs et utilisatrices.
- **Validation des données** : évitez les erreurs de manière précoce grâce à des contrôles en temps réel et à des messages clairs.
- **Expériences guidées** : guidez les utilisateurs et utilisatrices à travers des étapes logiques (assistants, branchements).
- **Création sans code** : configurez un comportement puissant par le biais d’une interface visuelle.

Les scénarios courants comprennent les calculateurs de taxes, les estimateurs de prêts et de primes, les flux d’éligibilité, les demandes à plusieurs étapes et les enquêtes avec des questions conditionnelles.

## Fonctionnement des règles

Une règle définit ce qui doit se produire lorsqu’une condition est remplie. Théoriquement, une règle comprend deux parties :

- **Condition** : instruction qui renvoie true ou false.
   - Par exemple : « Revenu > 50 000 », « Couverture = &#39;Oui&#39; », « Le champ est vide »
- **Action** : ce qui se produit lorsque la condition est true (et éventuellement, lorsqu’elle est false).
   - Par exemple : afficher/masquer un champ, définir/effacer une valeur, valider l’entrée, activer/désactiver un bouton

+++ Modèles de logique de règle

- **Condition → Action (When/Then [Lorsque/Alors])**

  ```text
  WHEN Gross Salary > 50000
  THEN Show "Additional Deduction"
  ```

  Idéal pour une visibilité conditionnelle et une divulgation progressive.

- **Action ← Condition (Set If/Only if [Définir si/Seulement si])**

  ```text
  SET Taxable Income = Gross Salary - Deductions
  IF Deductions are applicable
  ```

  Idéal pour les calculs et les transformations de données.

- **If → Then → Else (Si > Alors > Sinon) (Autre action)**

  ```text
  IF Income > 50000
  THEN Show "High Income" fields
  ELSE Show "Standard Income" fields
  ```

  Idéal pour la logique de branchement et les flux s’excluant mutuellement.

+++

+++ Exemple concret

- **Condition** : « Le salaire brut dépasse 50 000 $ »
- **Action principale** : Afficher la « Déduction supplémentaire »
- **Autre action** : Masquer la « Déduction supplémentaire »
- **Résultat** : les utilisateurs et utilisatrices voient uniquement les champs qui s’appliquent à eux

+++

## Prérequis


+++ Conditions d’accès

**Autorisations essentielles et configuration** :

- **AEM as a Cloud Service** : accès en création avec des autorisations de modification de formulaire.
- **Éditeur universel** : installé et configuré sur votre environnement.
- **Extension de l’éditeur de règles** : activée via [Extension Manager](/help/implementing/developing/extending/extension-manager.md).
- **Autorisations d’édition de formulaire** : possibilité de créer et de modifier des composants de formulaire dans l’éditeur universel.

**Étapes de vérification** :

1. Confirmer que vous pouvez accéder à l’éditeur universel à partir de votre console AEM Sites.
2. Vérifier que vous pouvez créer et modifier des composants de formulaire.
3. Vérifier que l’icône de l’éditeur de règles ![edit-rules](/help/forms/assets/edit-rules-icon.svg) s’affiche lors de la sélection des composants de formulaire.

+++

+++ Exigences techniques

**Connaissances et compétences requises** :

- **Maîtrise de l’éditeur universel** : expérience dans la création de formulaires avec des entrées de texte, des listes déroulantes et des propriétés de champ de base
- **Compréhension de la logique commerciale** : capacité à définir des exigences conditionnelles et des règles de validation pour votre cas d’utilisation spécifique
- **Maîtrise des composants de formulaire** : connaissance des types de champs (texte, nombre, liste déroulante), des propriétés (obligatoires, visibles, en lecture seule) et de la structure des formulaires

**Facultatif pour une utilisation avancée** :

- **Concepts de base de JavaScript** : uniquement pour la création de fonctions personnalisées (types de données, fonctions, syntaxe de base)
- **Compréhension de JSON** : utile pour la manipulation de données complexes et les intégrations d’API

**Questions d’évaluation** :

- Pouvez-vous créer un formulaire de base avec des entrées de texte et un bouton d’envoi dans l’éditeur universel ?
- Savez-vous quand les champs doivent être obligatoires ou facultatifs dans le contexte de votre activité ?
- Pouvez-vous identifier les éléments de formulaire qui nécessitent une visibilité conditionnelle dans votre cas d’utilisation ?

+++

+++ Activer l’extension de l’éditeur de règles

**Important** : l’extension de l’éditeur de règles n’est pas activée par défaut dans l’éditeur universel.

**Étapes d’activation** :

1. Accéder à [Extension Manager](/help/implementing/developing/extending/extension-manager.md) dans votre environnement AEM
2. Recherchez l’extension « Éditeur de règles » dans la liste des extensions disponibles.
3. Cliquer sur **Activer** et confirmer l’activation
4. Attendez que le système s’actualise (cela peut prendre 1 à 2 minutes).

**Vérification** :

- Après l’activation, l’icône Éditeur de règles s’affiche lorsque vous sélectionnez un composant de formulaire : ![edit-rules](/help/forms/assets/edit-rules-icon.svg).

![Éditeur de règles de l’éditeur universel](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
Image : l’icône Éditeur de règles s’affiche lorsque vous sélectionnez des composants de formulaire.

Pour ouvrir l’éditeur de règles :

1. Sélectionnez un composant de formulaire dans l’éditeur universel.
2. Cliquez sur l’icône Éditeur de règles.
3. L’éditeur de règles s’ouvre dans un panneau latéral.

![Interface d’utilisation de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-for-field.png)
Image : interface de l’éditeur de règles pour la modification des règles de composant.

>[!NOTE]
>
> Dans cet article, « composant de formulaire » et « objet de formulaire » se rapportent aux mêmes éléments (entrées, boutons, panneaux, par exemple).

## Vue d’ensemble de l’interface de l’éditeur de règles

![Interface d’utilisation de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-interface.png)
Image : interface complète de l’éditeur de règles avec des composants numérotés.

1. **Titre du composant et type de règle** : confirme le composant sélectionné et le type de règle actif.
2. **Panneau Objets de formulaire et Fonctions** :

   - Objets de formulaire : vue hiérarchique des champs et des conteneurs pour le référencement dans les règles.
   - Fonctions : assistants intégrés de mathématiques, de chaînes, de dates et de validation

3. **Basculement de panneau** : affichez/masquez le panneau Objets et fonctions pour augmenter l’espace de travail.
4. **Créateur visuel de règles** : création de règles par glisser-déposer et menus déroulants.
5. **Contrôles** : Terminé (enregistrer), Annuler (ignorer). Testez toujours les règles avant d’enregistrer.

+++

+++ Gestion des règles existantes

Lorsqu’un composant comporte déjà des règles, vous pouvez :

- **Afficher** : voir la logique et les résumés des règles.
- **Modifier** : modifier des conditions et des actions.
- **Réorganiser** : modifier l’ordre d’exécution (du haut vers le bas).
- **Activer/désactiver** : activer/désactiver les règles pour le test.
- **Supprimer** : supprimer les règles en toute sécurité.

>[!TIP]
>
> Faites passer les règles spécifiques avant les règles générales. L’exécution s’effectue de haut en bas.

+++

## Types de règle disponibles

Choisissez le type de règle qui correspond le mieux à votre intention.

+++ Logique conditionnelle

- **When (Lorsque)** : règle principale pour un comportement conditionnel complexe (Condition → Action ± Else [Sinon]).
- **Masquer/Afficher** : contrôle la visibilité en fonction d’une condition (divulgation progressive).
- **Activer/Désactiver** : contrôle si un champ est interactif (par exemple, désactiver Envoyer jusqu’à ce que les champs obligatoires soient valides).

+++

+++ Manipulation des données

- **Définir la valeur de** : permet de renseigner automatiquement les valeurs (par exemple, dates, totaux, copies).
- **Effacer la valeur de** : permet de supprimer des données lorsque les conditions changent.
- **Formater** : permet de transformer la mise en forme de l’affichage (devise, téléphone, date) sans modifier les valeurs stockées.

+++

+++ Validation

- **Valider** : logique de validation personnalisée, y compris les vérifications entre champs et les règles métier.

+++

+++ Calcul

- **Expression mathématique** : permet de calculer des valeurs en temps réel (totaux, taxes, ratios).

+++

+++ Interface d’utilisation

- **Définir la cible d’action** : permet de cibler un champ spécifique (à utiliser avec parcimonie).
- **Définir la propriété** : permet de modifier les propriétés du composant de manière dynamique (espace réservé, options, etc.).

+++

+++ Contrôle de formulaire

- **Envoyer le formulaire** : permet d’envoyer le formulaire par programmation (uniquement lorsque les validations ont abouti).
- **Réinitialiser le formulaire** : permet d’effacer et de rétablir l’état initial (confirmer avant de l’utiliser).
- **Enregistrer le formulaire** : permet d’enregistrer en tant que brouillon pour une utilisation ultérieure (formulaires longs, sessions multiples).

+++

+++ Avancé

- **Appeler le service** : permet d’appeler des API/services externes (gestion du chargement et des erreurs).
- **Ajouter/supprimer une instance** : permet de gérer les sections répétables (par exemple, les dépendances, les adresses).
- **Accéder à** : permet d’accéder à d’autres formulaires/pages (conserver les données avant la navigation).
- **Naviguer entre les panneaux** : permet de parcourir les étapes de l’assistant et d’en ignorer.
- **Distribuer l’événement** : permet de déclencher des événements personnalisés pour les intégrations ou l’analyse.

+++

## Tutoriel détaillé : créer un calculateur de taxes intelligent

+++ Vue d’ensemble du tutoriel

Cet exemple illustre la visibilité conditionnelle et les calculs automatiques.

![Capture d’écran de l’interface de l’éditeur de règles présentant la création d’une règle conditionnelle avec la logique WHEN-THEN (LORSQUE-ALORS) pour la visibilité des champs de formulaire](/help/edge/docs/forms/assets/rule-editor-1.png)
Figure : formulaire de calcul de taxes avec des champs conditionnels intelligents

Vous allez créer un formulaire qui :

1. S’adapte aux entrées utilisateur et utilisatrice en affichant les champs pertinents.
2. Calcule les valeurs en temps réel.
3. Valide les données pour améliorer la précision.

+++

+++ Structure du formulaire

| Nom du champ | Type | Objectif | Comportement |
|-------------------------|---------------|--------------------------------|-----------------------------------------|
| Salaire brut | Entrée numérique | Revenu annuel de l’utilisateur ou l’utilisatrice | Déclenche une logique conditionnelle |
| Déduction supplémentaire | Entrée numérique | Déductions supplémentaires (si éligibles) | Visible uniquement lorsque Salaire > 50 000 $ |
| Revenu imposable | Entrée numérique | Valeur calculée | Lecture seule, mises à jour lors des modifications |
| Taxes à payer | Entrée numérique | Valeur calculée | Lecture seule, calculé à un taux uniforme |

+++

+++ Logique commerciale

- **Règle 1 : affichage conditionnel**

  ```text
  WHEN Gross Salary > 50,000
  THEN Show "Additional Deduction"
  ELSE Hide "Additional Deduction"
  ```

- **Règle 2 : calcul du revenu imposable**

  ```text
  SET Taxable Income = Gross Salary - Additional Deduction
  (Only when Additional Deduction applies)
  ```

- **Règle 3 : calcul des taxes à payer**

  ```text
  SET Tax Payable = Taxable Income × 10%
  (Simplified flat rate)
  ```

+++

+++ Étape 1 : créer le formulaire

**Objectif** : créer le formulaire de base avec tous les champs et paramètres initiaux.

1. **Ouvrez l’éditeur universel** :
   - Accédez à la console AEM Sites, sélectionnez votre page, puis cliquez sur **Modifier**.
   - Vérifiez que l’[éditeur universel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html) est correctement configuré.

2. **Ajoutez les composants de formulaire dans cet ordre** :
   - Titre (H2) : « Formulaire de calcul des taxes »
   - Entrée numérique : « Salaire brut » (Obligatoire : oui, Espace réservé : « Saisir le salaire annuel »)
   - Entrée numérique : « Déduction supplémentaire » (Obligatoire : non, Espace réservé : « Saisir des déductions supplémentaires »)
   - Entrée numérique : « Revenu imposable » (Lecture seule : oui)
   - Entrée numérique : « Taxes à payer » (Lecture seule : oui)
   - Bouton Envoyer : « Calculer la taxe »

3. **Configurez les propriétés initiales du champ** :
   - Masquez « Déduction supplémentaire » (définissez la valeur Visible : non dans le panneau Propriétés)
   - Définissez « Revenu imposable » et « Taxes à payer » sur Lecture seule : oui

![Capture d’écran d’un formulaire de calcul des impôts avec des champs de saisie pour le salaire brut, la situation de famille et les enfants à charge, présentant la structure du formulaire avant l’application des règles](/help/edge/docs/forms/assets/rule-editor2.png)
Image : structure initiale du formulaire avec configuration des composants de base

**Point de contrôle** : tous les champs obligatoires de votre formulaire devraient être remplis, le champ « Déduction supplémentaire » devrait être masqué et les champs calculés devraient être en lecture seule.

+++

+++ Étape 2 : ajout d’une règle de visibilité conditionnelle

**Objectif** : afficher le champ « Déduction supplémentaire » uniquement lorsque le salaire brut dépasse 50 000 $.

1. **Sélectionnez le champ Salaire brut** et cliquez sur l’icône de l’éditeur de règles ![edit-rules](/help/forms/assets/edit-rules-icon.svg).
2. **Créez une règle** :
   - Cliquer sur **Créer**
   - Remplacez le type de règle de « Définir la valeur de » par **« Lorsque »**.
3. **Configurez la condition** :
   - Sélectionnez **« est supérieur à »** dans la liste déroulante.
   - Saisissez `50000` dans le champ numérique.
4. **Définissez l’action Alors** :
   - Choisissez **« Afficher »** dans le menu déroulant Sélectionner une action.
   - Faites glisser ou sélectionnez le champ **« Déduction supplémentaire »** à partir des objets de formulaire.
5. **Ajoutez l’action Sinon** :
   - Cliquez sur **« Ajouter une section Sinon »**.
   - Sélectionnez **« Masquer »** dans le menu déroulant Sélectionner une action.
   - Sélectionnez le champ **« Déduction supplémentaire »**.
6. **Enregistrez la règle** : cliquez sur **Terminé**.

>[!NOTE]
>
> Autre méthode : vous pouvez obtenir le même résultat en créant une règle Afficher/Masquer directement dans le champ « Déduction supplémentaire » au lieu d&#39;une règle Lorsque dans « Salaire brut ».

+++

+++ Étape 3 : Ajout de règles de calcul

**Objectif** : calculez automatiquement le « Revenu imposable » et les « Taxes à payer » en fonction des données saisies par l’utilisateur ou l’utilisatrice.

**Configurez le calcul du revenu imposable** :

1. **Sélectionnez le champ « Revenu imposable »** et ouvrez l’éditeur de règles.
2. **Créez une expression mathématique** :
   - Cliquez sur **Créer** → Sélectionnez **« Expression Mathématique »**.
   - Créez une expression : **Salaire brut − Déduction supplémentaire**.
   - Faites glisser « Salaire brut » dans le premier champ.
   - Sélectionnez l’opérateur **« Moins »**.
   - Faites glisser « Déduction supplémentaire » dans le deuxième champ.
3. **Enregistrer** : cliquez sur **Terminé**.

**Configurer le calcul des taxes à payer** :

1. **Sélectionnez le champ « Taxe à payer »**, puis ouvrez l’éditeur de règles.
2. **Créer une expression mathématique** :
   - Cliquez sur **Créer** → Sélectionnez **« Expression Mathématique »**.
   - Créez une expression : **Revenu imposable × 10 ÷ 100**.
   - Faites glisser « Revenu imposable » dans le premier champ.
   - Sélectionnez l’opérateur **« Multiplié par »**.
   - Saisissez le nombre `10`.
   - Cliquez sur **« Étendre l’expression »**.
   - Sélectionnez l’opérateur **« Divisé par »**.
   - Saisissez le nombre `100`.
3. **Enregistrer** : cliquez sur **Terminé**.

+++

+++ Étape 4 : tester le formulaire

**Vérifiez votre implémentation en testant le flux complet** :

1. **Prévisualiser le formulaire** : cliquez sur le mode Aperçu dans l’éditeur universel.
2. **Tester la logique conditionnelle** :
   - Saisissez Salaire brut = `30000` → « Déduction supplémentaire » doit rester masqué.
   - Saisissez Salaire brut = `60000` → « Déduction supplémentaire » doit apparaître.
3. **Tester les calculs** :
   - Si Salaire brut = `60000`, saisissez Déduction supplémentaire = `5000`.
   - Vérifiez que Revenu imposable = `55000` (60000 - 5000).
   - Vérifiez que Taxe à payer = `5500` (55000 × 10 %).

![Prévisualiser un formulaire](/help/edge/docs/forms/assets/rule-editor-form.png)
Image : calculateur de taxe terminé avec champs conditionnels et calculs automatiques.

**Critères de réussite** : le formulaire doit afficher/masquer les champs de manière dynamique et calculer les valeurs en temps réel au fur et à mesure que les utilisateurs et utilisatrices saisissent des informations.


+++

## Avancé : fonctions personnalisées

Pour une logique commerciale complexe au-delà des fonctionnalités intégrées, vous pouvez créer des fonctions JavaScript personnalisées qui s’intègrent de manière transparente à l’éditeur de règles.

+++ Quand utiliser des fonctions personnalisées

**Scénarios idéaux pour les fonctions personnalisées** :

- **Calculs complexes** : calculs à plusieurs étapes difficiles à exprimer dans la règle d’expression mathématique.
- **Validations spécifiques à l’entreprise** : logique de validation personnalisée spécifique à votre organisation ou à votre secteur d’activité.
- **Transformations de données** : conversions de formats, manipulations de chaînes ou analyse de données.
- **Intégrations externes** : appels à des API internes ou à des services tiers (avec limitations).

**Avantages des fonctions personnalisées** :

- **Réutilisation** : écrivez-les une seule fois et réutilisez-les dans plusieurs formulaires et règles.
- **Maintenabilité** : logique centralisée, plus facile à mettre à jour et à déboguer.
- **Performances** : exécution JavaScript optimisée par rapport aux chaînes de règles complexes.
- **Flexibilité** : gérez les cas particuliers et les scénarios complexes non gérés par des règles standard.

+++

+++ Création et déploiement des fonctions personnalisées

**Emplacement du fichier** : toutes les fonctions personnalisées doivent être définies dans `/blocks/form/functions.js` dans votre projet Edge Delivery Services.

**Workflow de développement** :

1. **Conception de fonction**
   - Utilisez des noms de fonction descriptifs et orientés vers l’action.
   - Définissez des types de paramètres clairs et des valeurs de retour.
   - Gérez les cas particuliers et les entrées non valides de manière appropriée.

2. **Mise en œuvre**
   - Écrivez du code JavaScript clair et bien commenté.
   - Incluez la validation des entrées et la gestion des erreurs.
   - Testez les fonctions indépendamment avant l’intégration.

3. **Documentation**
   - Ajoutez des commentaires JSDoc complets.
   - Incluez des exemples d’utilisation et des descriptions de paramètres.
   - Documentez toute limite ou dépendance.

4. **Déploiement**
   - Exportez les fonctions à l’aide d’exports nommés.
   - Déployez sur le référentiel du projet.
   - Vérifiez que la génération est terminée avant de procéder au test.

**Exemple d’implémentation** :

```javascript
/**
 * Concatenates first and last name with proper formatting
 * @name getFullName
 * @description Combines first and last name, handles edge cases like missing values
 * @param {string} firstName - The person's first name
 * @param {string} lastName - The person's last name  
 * @returns {string} Formatted full name or empty string if both inputs are invalid
 */
function getFullName(firstName, lastName) {
  // Handle null, undefined, or empty string inputs
  const first = (firstName || '').toString().trim();
  const last = (lastName || '').toString().trim();
  
  return `${first} ${last}`.trim();
}

/**
 * Calculates the number of days between two dates
 * @name days
 * @description Computes absolute difference in days, handles various date input formats
 * @param {Date|string} endDate - End date (Date object or ISO string)
 * @param {Date|string} startDate - Start date (Date object or ISO string)
 * @returns {number} Number of days between dates, 0 if inputs are invalid
 */
function days(endDate, startDate) {
  // Convert string inputs to Date objects
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // Validate date objects
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  // Calculate absolute difference in milliseconds, then convert to days
  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// Export functions for use in Rule Editor
export { getFullName, days };
```

![Ajout d’une fonction personnalisée](/help/edge/docs/forms/assets/create-custom-function.png)
Image : ajout de fonctions personnalisées au fichier functions.js.

+++

+++ Utilisation des fonctions personnalisées dans l’éditeur de règles

**Étapes d’intégration** :

1. **Ajouter une fonction au projet**
   - Créez ou modifiez `/blocks/form/functions.js` dans votre projet.
   - Incluez votre fonction dans l’instruction d’export.

2. **Déployer et créer**
   - Validez les modifications dans votre référentiel.
   - Vérifiez que le processus de création s’exécute correctement.
   - Attendez l’actualisation du cache CDN.

3. **Accéder à l’éditeur de règles**
   - Ouvrez l’éditeur de règles pour n’importe quel composant de formulaire.
   - Sélectionnez **« Sortie de fonction »** dans le menu déroulant **Sélectionner une action**.
   - Choisissez votre fonction personnalisée dans la liste des fonctions disponibles.
   - Configurez les paramètres de la fonction à l’aide des champs de formulaire ou de valeurs statiques.

4. **Tester minutieusement**
   - Prévisualisez le formulaire pour vérifier le comportement de la fonction.
   - Testez plusieurs combinaisons d’entrées, y compris des cas particuliers.
   - Vérifiez l’impact des performances sur le chargement et l’interaction du formulaire.

![Fonction personnalisée dans l’éditeur de règles](/help/edge/docs/forms/assets/custom-function-rule-editor.png)
Image : sélection et configuration de fonctions personnalisées dans l’interface de l’éditeur de règles.

>
>
> Les améliorations apportées à l’éditeur de règles, notamment les règles basées sur un événement personnalisé, la prise en charge des variables dynamiques et l’intégration d’API, sont également disponibles pour les formulaires Edge Delivery Services. Pour en savoir plus sur ces améliorations et sur leur utilisation, consultez l’article [Améliorations de l’éditeur de règles et cas d’utilisation](/help/forms/rule-editor-enhancements-use-cases.md).

**Bonnes pratiques relatives à l’utilisation des fonctions** :

- **Gestion des erreurs** : incluez toujours un comportement de secours pour les échecs de fonction.
- **Performances** : profilez les fonctions avec des volumes de données réalistes.
- **Sécurité** : validez toutes les entrées pour éviter les vulnérabilités de sécurité.
- **Tests** : créez des cas de test couvrant les cas normaux et les cas particuliers.

+++


### Imports statiques pour les fonctions personnalisées

L’éditeur de règles de l’éditeur universel prend en charge les imports statiques, ce qui vous permet d’organiser une logique réutilisable dans plusieurs fichiers et formulaires. Au lieu de conserver toutes les fonctions personnalisées dans un seul fichier (/blocks/form/functions.js), vous pouvez importer des fonctions d’autres modules.
Par exemple : import de fonctions à partir d’un fichier externe
Tenez compte de la structure de dossiers suivante :

```
      form
      ┣ commonLib
      ┃ ┗ functions.js
      ┣ rules
      ┃ ┗ _form.json
      ┣ form.js
      ┗ functions.js
```

Vous pouvez importer des fonctions de `commonLib/functions.js` dans votre fichier `functions.js` principal, comme indiqué ci-dessous :

```
`import {days} from './commonLib/functions';
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in String format
 * @param {string} lastname in String format
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

// Export multiple functions for use in Rule Editor
export { getFullName, days};
```

### Organisation de fonctions personnalisées dans différents formulaires

Vous pouvez créer différents ensembles de fonctions dans des fichiers ou des dossiers distincts et les exporter selon vos besoins:

- Si vous souhaitez que certaines fonctions ne soient disponibles que dans des formulaires spécifiques, vous pouvez fournir le chemin d’accès au fichier de fonctions dans la configuration du formulaire.

- Si la zone de texte du chemin n’est pas renseignée, l’éditeur de règles charge par défaut les fonctions à partir de `/blocks/form/functions.js`.

![Fonction personnalisée dans l’éditeur universel](/help/forms/assets/custom-function-in-ue.png){width=50%}

Dans la copie d’écran ci-dessus, le chemin d’accès de la fonction personnalisée est ajouté à la zone de texte Chemin d’accès de la fonction personnalisée. Les fonctions personnalisées de ce formulaire sont chargées à partir du fichier spécifié (`cc_function.js`).

Vous bénéficiez ainsi d’une certaine flexibilité en partageant des fonctions entre plusieurs formulaires ou en les isolant pour chaque formulaire.

## Bonnes pratiques en matière de développement de règles


+++ Optimisation des performances

- Réduisez la complexité des règles ; divisez une logique volumineuse en règles petites et ciblées.
- Classez les règles par fréquence (les plus courantes en premier).
- Maintenez gérables les jeux de règles par composant.
- Préférez les fonctions personnalisées réutilisables à la duplication de logique.

+++

+++ Expérience clientèle

- Fournissez une validation claire et des commentaires intégrés.
- Évitez les modifications visuelles discordantes ; utilisez l’option Afficher/masquer avec précaution.
- Testez sur plusieurs appareils et dispositions.

+++

+++ Qualité du développement

- Testez avec des cas particuliers et des valeurs connues.
- Vérifiez sur plusieurs navigateurs.
- Documentez l’intention derrière des règles complexes, pas seulement la mécanique.
- Tenez à jour un inventaire de règles pour les formulaires volumineux.
- Utilisez des noms cohérents pour les composants et les règles.
- Gérez les versions des fonctions personnalisées et testez-les dans des environnements hors production.

+++

## Résolution des problèmes courants


+++ Règles ne se déclenchant pas

- Vérifiez les noms et les références des composants.
- Vérifiez l’ordre d’exécution (de haut en bas).
- Validez les conditions avec des valeurs connues.
- Inspectez la console du navigateur pour détecter les erreurs de blocage.

+++

+++ Comportement incorrect

- Vérifiez les opérateurs et le regroupement (ET/OU).
- Testez individuellement les fragments d’expression.
- Confirmez les types de données (nombres ou chaînes).

+++

+++ Problèmes de performances

- Simplifiez les conditions profondément imbriquées.
- Profilez les fonctions personnalisées.
- Réduisez les appels externes dans les règles.
- Utilisez des sélecteurs et des références spécifiques.

+++

+++ Problèmes des fonctions personnalisées

- Vérifiez le chemin d’accès au fichier : `/blocks/form/functions.js`.
- Vérifiez que les exports nommés sont corrects.
- Vérifiez que la version inclut vos modifications.
- Effacez la mémoire cache du navigateur après le déploiement.
- Validez les types de paramètres et la gestion des erreurs.

+++

+++ Intégration de l’éditeur universel

- Vérifiez que l’extension de l’éditeur de règles est activée.
- Sélectionnez un composant pris en charge.
- Utilisez un navigateur pris en charge (Chrome, Firefox, Safari).
- Vérifiez que vous disposez des autorisations requises.

## Limites importantes

>[!IMPORTANT]
>
> Contraintes des fonction personnalisées :
>
> - Les imports statiques/dynamiques ne sont pas pris en charge.
> - Toute la logique doit résider dans `/blocks/form/functions.js`.
> - Les fonctions doivent être synchrones (les fonctions asynchrones avec async/await ou Promise ne sont pas autorisées).
> - L’accès à l’API du navigateur est limité.

>[!WARNING]
>
> Considérations relatives à la production :
>
> - Testez minutieusement lors de l’évaluation.
> - Surveillez les performances après le déploiement.
> - Disposez d’un plan de restauration pour les problèmes de règle.
> - Prenez en compte les réseaux lents et les appareils peu performants.

## Résumé

L’éditeur de règles de l’éditeur universel transforme les formulaires statiques en expériences intelligentes et réactives qui s’adaptent à la saisie des utilisateurs et utilisatrices en temps réel. En utilisant une logique conditionnelle, des calculs automatisés et des règles d’entreprise personnalisées, vous pouvez créer des workflows de formulaire sophistiqués sans écrire de code d’application.

**Fonctionnalités clés que vous avez apprises** :

- **Logique conditionnelle** : afficher et masquer des champs en fonction des entrées de l’utilisateur ou de l’utilisatrice pour créer des expériences ciblées et pertinentes.
- **Calculs dynamiques** : calculer automatiquement les valeurs (taxes, totaux, taux) lorsque les utilisateurs et utilisatrices interagissent avec le formulaire.
- **Validation des données** : implémenter la validation en temps réel avec des messages de commentaires clairs et exploitables.
- **Fonctions personnalisées** : étendre les fonctionnalités de JavaScript pour une logique commerciale et des intégrations complexes.
- **Optimisation des performances** : appliquer les bonnes pratiques pour un développement durable et efficace des règles.

**Valeur apportée** :

- **Expérience d’utilisation améliorée** : réduire la charge cognitive grâce à la divulgation progressive et aux flux de formulaires intelligents.
- **Réduction des erreurs** : empêcher les envois non valides par le biais de la validation en temps réel et de l’entrée guidée.
- **Efficacité améliorée** : automatiser les calculs et la saisie des données pour réduire les efforts des utilisateurs et utilisatrices.
- **Solutions gérables** : créer des règles réutilisables et bien documentées qui s’appliquent à l’ensemble de votre entreprise.

**Impact commercial** :

Les formulaires deviennent des outils puissants pour la collecte de données, la qualification des prospects et l’interaction client. L’éditeur de règles permet aux créateurs et créatrices non spécialistes d’implémenter une logique commerciale sophistiquée, réduisant les coûts de développement tout en améliorant les taux de remplissage des formulaires et la qualité des données.

+++

## Étapes suivantes

**Parcours de formation recommandé** :

1. **Commencer par les principes de base** : créez des règles simples d’affichage/masquage pour comprendre les concepts de base.
2. **Pratiquer avec des tutoriels** : utilisez l’exemple du calculateur d’impôts comme base de vos propres formulaires.
3. **Développer progressivement** : ajoutez des expressions mathématiques et des règles de validation à mesure que vous prenez de l’assurance.
4. **Implémenter des fonctions personnalisées** : développez des fonctions JavaScript pour les besoins métier spécifiques.
5. **Optimiser et mettre à l’échelle** : appliquez les bonnes pratiques de performances et tenez à jour la documentation des règles.

**Ressources supplémentaires** :

- [Documentation de l’éditeur universel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html) pour un contexte plus large
- [Guide d’Extension Manager](/help/implementing/developing/extending/extension-manager.md) pour activer des fonctionnalités supplémentaires
- [Formulaires Edge Delivery Services](/help/edge/docs/forms/overview.md) pour des conseils exhaustifs sur la création de formulaires


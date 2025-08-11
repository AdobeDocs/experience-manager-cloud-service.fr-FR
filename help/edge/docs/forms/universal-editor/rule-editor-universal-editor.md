---
title: Éditeur de règles pour Dynamic Forms dans l’éditeur universel
description: Créez des formulaires dynamiques et intelligents à l’aide de l’éditeur de règles dans l’éditeur universel. Ajoutez une logique conditionnelle, des calculs et des comportements interactifs sans codage.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '2598'
ht-degree: 1%

---


# Éditeur de règles pour Dynamic Forms dans l’éditeur universel

L’éditeur de règles permet aux créateurs et créatrices de transformer des formulaires statiques en expériences réactives et intelligentes, sans avoir à écrire de code. Vous pouvez afficher des champs de manière conditionnelle, effectuer des calculs, valider des données, guider les utilisateurs et les utilisatrices à travers les flux et intégrer une logique commerciale qui s’adapte lors de la saisie de personnes.

## Ce que vous apprendrez

À la fin de ce guide, vous serez en mesure de :

- Comprendre le fonctionnement des règles et quand utiliser différents types de règle
- Activation et accès à l’éditeur de règles dans l’éditeur universel
- Création d’une logique conditionnelle pour afficher ou masquer les champs de manière dynamique
- Implémenter des calculs automatisés et la validation des données
- Créer des fonctions personnalisées pour des règles métier complexes
- Appliquer les bonnes pratiques en matière de performances, de maintenabilité et d’expérience utilisateur

## Pourquoi utiliser l’éditeur de règles ?

- **Logique conditionnelle** : affichez les champs pertinents uniquement lorsque cela est nécessaire pour réduire le bruit et la charge cognitive.
- **Calculs dynamiques** : calculez automatiquement les valeurs (totaux, taux, taxe) au fur et à mesure que les utilisateurs saisissent ces valeurs.
- **Validation des données** : prévenez rapidement les erreurs grâce à des contrôles en temps réel et à des messages clairs.
- **Expériences guidées** : guide les utilisateurs à travers des étapes logiques (assistants, embranchements).
- **Création sans code** : configurez un comportement puissant par le biais d’une interface visuelle.

Les scénarios courants comprennent les calculateurs d&#39;impôt, les estimateurs de prêts et de primes, les flux d&#39;éligibilité, les demandes à plusieurs étapes et les enquêtes avec des questions conditionnelles.

## Fonctionnement des règles

Une règle définit ce qui doit se produire lorsqu’une condition est remplie. Conceptuellement, une règle se compose de deux parties :

- **Condition** : instruction qui renvoie true ou false.
   - Exemples : « Revenu > 50 000 », « Couverture = « Oui », « Champ vide »
- **Action** : ce qui se produit lorsque la condition est vraie (et éventuellement, lorsqu’elle est fausse).
   - Exemples : afficher/masquer un champ, définir/effacer une valeur, valider l’entrée, activer/désactiver un bouton

+++ Modèles de logique de règle

- **Condition → Action (Lorsque/Alors)**

  ```text
  WHEN Gross Salary > 50000
  THEN Show "Additional Deduction"
  ```

  Idéal pour une visibilité conditionnelle et une divulgation progressive.

- **Action ← condition (définir si/uniquement si)**

  ```text
  SET Taxable Income = Gross Salary - Deductions
  IF Deductions are applicable
  ```

  Idéal pour les calculs et les transformations de données.

- **If → Then → Else (Autre action)**

  ```text
  IF Income > 50000
  THEN Show "High Income" fields
  ELSE Show "Standard Income" fields
  ```

  Idéal pour l’embranchement de la logique et les flux s’excluant mutuellement.

+++

+++ Exemple concret

- **Condition** : « Le salaire brut dépasse 50 000 $ »
- **Action de Principal** : afficher la « déduction supplémentaire »
- **Autre action** : masquer la « Déduction supplémentaire »
- **Résultat** : les utilisateurs voient uniquement les champs qui s’appliquent à eux

+++

## Prérequis


+++ Exigences d’accès

**Autorisations et configuration essentielles** :

- **AEM as a Cloud Service** : accès de création avec des autorisations de modification de formulaire
- **éditeur universel** : installé et configuré sur votre environnement.
- **Extension de l’éditeur de règles** : activé via [Extension Manager](/help/implementing/developing/extending/extension-manager.md)
- **Autorisations d’édition de formulaire** : possibilité de créer et de modifier des composants de formulaire dans l’éditeur universel

**Étapes de vérification** :

1. Confirmer que vous pouvez accéder à l’éditeur universel à partir de votre console AEM Sites
2. Vérifier que vous pouvez créer et modifier des composants de formulaire
3. Vérifiez que l’icône de l’éditeur de règles ![edit-rules](/help/forms/assets/edit-rules-icon.svg) s’affiche lors de la sélection des composants de formulaire

+++

+++ Exigences techniques

**Connaissances et compétences requises** :

- **Compétence de l’éditeur universel** : expérience de création de formulaires avec des entrées de texte, des listes déroulantes et des propriétés de champ de base
- **Compréhension de la logique commerciale** : capacité à définir des exigences conditionnelles et des règles de validation pour votre cas d’utilisation spécifique
- **Connaissance des composants de formulaire** : connaissance des types de champs (texte, nombre, liste déroulante), des propriétés (obligatoires, visibles, en lecture seule) et de la structure des formulaires

**facultatif pour une utilisation avancée** :

- **Principes de base de JavaScript** : requis uniquement pour la création de fonctions personnalisées (types de données, fonctions, syntaxe de base)
- **Présentation de JSON** : utile pour la manipulation de données complexes et les intégrations d’API

**Questions d’évaluation** :

- Pouvez-vous créer un formulaire de base avec des entrées de texte et un bouton d’envoi dans l’éditeur universel ?
- Savez-vous quand les champs doivent être obligatoires ou facultatifs dans votre contexte commercial ?
- Pouvez-vous identifier les éléments de formulaire qui nécessitent une visibilité conditionnelle dans votre cas d’utilisation ?

+++

+++ Activation de l’extension de l’éditeur de règles

**Important** : l’extension Éditeur de règles n’est pas activée par défaut dans les environnements de l’éditeur universel.

**Étapes d’activation** :

1. Accédez à [Extension Manager](/help/implementing/developing/extending/extension-manager.md) dans votre environnement AEM
2. Recherchez l’extension « Éditeur de règles » dans la liste des extensions disponibles
3. Cliquez sur **Activer** et confirmez l’activation
4. Attendez que le système s’actualise (cela peut prendre 1 à 2 minutes).

**Vérification**

- Après l’activation, l’icône Éditeur de règles s’affiche lorsque vous sélectionnez un composant de formulaire : ![edit-rules](/help/forms/assets/edit-rules-icon.svg)

![Éditeur universel de règles](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
Image : l’icône Éditeur de règles s’affiche lorsque vous sélectionnez des composants de formulaire

Pour ouvrir l’éditeur de règles :

1. Sélectionnez un composant de formulaire dans l’éditeur universel.
2. Cliquez sur l’icône Éditeur de règles .
3. L’éditeur de règles s’ouvre dans un panneau latéral.

![Interface utilisateur de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-for-field.png)
Image : interface de l’éditeur de règles pour la modification des règles de composant

>[!NOTE]
>
> Dans cet article, « composant de formulaire » et « objet de formulaire » se rapportent aux mêmes éléments (par exemple, entrées, boutons, panneaux).

## Présentation de l’interface de l’éditeur de règles

![Interface utilisateur de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-interface.png)
Image : interface complète de l’éditeur de règles avec des composants numérotés

- **Titre du composant et type de règle** : confirme le composant sélectionné et le type de règle actif.
- **Panneau Objets de formulaire et fonctions** :
   - Objets de formulaire : vue hiérarchique des champs et des conteneurs pour le référencement dans les règles
   - Fonctions : assistants intégrés de mathématiques, de chaînes, de dates et de validation
- **Basculement de panneau** : affichez/masquez le panneau Objets et fonctions pour augmenter l’espace de travail
- **Créateur visuel de règles** : glisser-déposer, compositeur de règles piloté par une liste déroulante
- **Contrôles** : Terminé (enregistrement), Annuler (ignorer). Testez toujours les règles avant d’enregistrer.

+++

+++ Gestion des règles existantes

Lorsqu’un composant comporte déjà des règles, vous pouvez :

- **Afficher** : voir la logique et les résumés des règles.
- **Modifier** : modification des conditions et actions
- **Réorganiser** : modifier l’ordre d’exécution (du haut vers le bas)
- **Activer/désactiver** : basculer les règles pour le test
- **Supprimer** : supprimez les règles en toute sécurité.

>[!TIP]
>
> Faire passer les règles spécifiques avant les règles générales. L’exécution s’effectue de haut en bas.

+++

## Types de règle disponibles

Choisissez le type de règle qui correspond le mieux à votre intention.

+++ Logique conditionnelle

- **Lorsque** : règle de Principal pour un comportement conditionnel complexe (condition → action ± Sinon)
- **Masquer/Afficher** : contrôle la visibilité en fonction d’une condition (divulgation progressive).
- **Activer/Désactiver** : contrôle si un champ est interactif (par exemple, désactivez Envoyer jusqu’à ce que les champs obligatoires soient valides).

+++

+++ Manipulation des données

- **Définir la valeur de** : renseignez automatiquement les valeurs (par exemple, les dates, les totaux, les copies)
- **Effacer la valeur de** : permet de supprimer des données lorsque les conditions changent
- **Format** : transformez le formatage de l’affichage (devise, téléphone, date) sans modifier les valeurs stockées

+++

+++ Validation

- **Valider** : logique de validation personnalisée, y compris les contrôles entre champs et les règles métier.

+++

+++ Calcul

- **Expression mathématique** : calcule des valeurs en temps réel (totaux, impôts, ratios)

+++

+++ Interface d’utilisation

- **Définir la cible d’action** : déplace la cible d’action vers un champ spécifique (utilise avec parcimonie)
- **Définir la propriété** : modifiez dynamiquement les propriétés du composant (espace réservé, options, etc.)

+++

+++ Contrôle de formulaire

- **Envoyer le formulaire** : envoyez le formulaire par programmation (uniquement après la réussite des validations)
- **Réinitialiser le formulaire** : effacer et rétablir l’état initial (confirmer avant utilisation)
- **Enregistrer le formulaire** : enregistrez-le en tant que brouillon pour une utilisation ultérieure (formulaires longs, sessions multiples).

+++

+++ Avancé

- **Appeler le service** : appel des API/services externes (gestion du chargement et des erreurs).
- **Ajouter/supprimer une instance** : gérez les sections répétables (par exemple, les personnes à charge, les adresses).
- **Accéder à** : accéder à d’autres formulaires/pages (conserver les données avant la navigation)
- **Naviguer parmi les panneaux** : navigation et omission des étapes de l’assistant de contrôle
- **Distribuer l’événement** : déclencher des événements personnalisés pour les intégrations ou les analyses

+++

## Tutoriel détaillé : Créer un calculateur d&#39;impôt intelligent

+++ Présentation du tutoriel

Cet exemple illustre la visibilité conditionnelle et les calculs automatiques.

![Capture d’écran de l’interface de l’éditeur de règles présentant la création d’une règle conditionnelle avec la logique de date et heure pour la visibilité des champs de formulaire](/help/edge/docs/forms/assets/rule-editor-1.png)
Image : formulaire de calcul des taxes avec des champs conditionnels intelligents

Vous allez créer un formulaire qui :

1. S’adapte aux entrées utilisateur en affichant les champs pertinents
2. Calcule les valeurs en temps réel
3. Valide les données pour améliorer la précision

+++

+++ Structure d’un formulaire

| Nom du champ | Type | Objectif | Comportement |
|-------------------------|---------------|--------------------------------|-----------------------------------------|
| Salaire Brut | Entrée de nombre | Revenu annuel de l&#39;utilisateur | Déclenche une logique conditionnelle |
| Déduction supplémentaire | Entrée de nombre | Déductions supplémentaires (si éligibles) | Visible uniquement lorsque Salaire > 50 000 $ |
| Revenu Imposable | Entrée de nombre | Valeur calculée | Lecture seule, mises à jour lors des modifications |
| Impôt À Payer | Entrée de nombre | Valeur calculée | Lecture seule, calculée à un taux forfaitaire |

+++

+++ Logique commerciale

- **Règle 1 : Affichage conditionnel**

  ```text
  WHEN Gross Salary > 50,000
  THEN Show "Additional Deduction"
  ELSE Hide "Additional Deduction"
  ```

- **Règle 2 : Calcul du revenu imposable**

  ```text
  SET Taxable Income = Gross Salary - Additional Deduction
  (Only when Additional Deduction applies)
  ```

- **Règle 3 : Calcul de l&#39;impôt à payer**

  ```text
  SET Tax Payable = Taxable Income × 10%
  (Simplified flat rate)
  ```

+++

+++ Étape 1 : créer le formulaire de base

**Objectif** : créer le formulaire de base avec tous les champs et paramètres initiaux.

1. **Ouvrez l’éditeur universel** :
   - Accédez à la console AEM Sites, sélectionnez votre page, puis cliquez sur **Modifier**
   - Vérifiez que l’[éditeur universel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html?lang=fr) est correctement configuré

2. **Ajoutez les composants de formulaire dans cet ordre** :
   - Titre (H2) : « Formulaire de calcul de l&#39;impôt »
   - Entrée de nombre : « Salaire brut » (Obligatoire : Oui, Espace réservé : « Saisir le salaire annuel »)
   - Entrée de nombre : « Déduction supplémentaire » (Obligatoire : Non, Espace réservé : « Saisir des déductions supplémentaires »)
   - Entrée de nombre : « Revenu imposable » (Lecture seule : Oui)
   - Entrée de nombre : « Impôt à payer » (Lecture seule : Oui)
   - Bouton Envoyer : « Calculer la taxe »

3. **Configurez les propriétés initiales du champ** :
   - Masquer « Déduction supplémentaire » (définir Visible : Non dans le panneau Propriétés)
   - Définissez « Revenu imposable » et « Impôt à payer » sur Lecture seule : Oui

![Capture d’écran d’un formulaire de calcul des impôts avec des champs d’entrée pour le salaire brut, la situation de famille et les enfants à charge, présentant la structure du formulaire avant l’application des règles](/help/edge/docs/forms/assets/rule-editor2.png)
Image : structure de formulaire initiale avec composants de base configurés

**Point de contrôle** : vous devez disposer d’un formulaire avec tous les champs obligatoires où la « Déduction supplémentaire » est masquée et les champs calculés sont en lecture seule.

+++

+++ Étape 2 : ajouter une règle de visibilité conditionnelle

**Objectif** : afficher le champ « Déduction supplémentaire » uniquement lorsque le salaire brut dépasse 50 000 $.

1. **Sélectionnez le champ Salaire brut** puis cliquez sur l’icône de l’éditeur de règles ![edit-rules](/help/forms/assets/edit-rules-icon.svg)
2. **Créez une règle** :
   - Cliquez sur **Créer**.
   - Remplacez le type de règle de « Définir la valeur de » par **« Lorsque »**
3. **Configurez la condition** :
   - Sélectionnez **« est supérieur à »** dans la liste déroulante
   - Saisissez `50000` dans le champ numérique
4. **Définissez l’action Then** :
   - Choisissez **« Afficher »** dans le menu déroulant Sélectionner une action
   - Faites glisser ou sélectionnez **champ « Déduction supplémentaire »** à partir des objets de formulaire
5. **Ajoutez l’action Sinon** :
   - Cliquez sur **« Ajouter une section Else »**
   - Sélectionnez **« Masquer »** dans le menu déroulant Sélectionner une action
   - Sélectionnez **champ « Déduction supplémentaire »**
6. **Enregistrez la règle** : cliquez sur **Terminé**

>[!NOTE]
>
> Autre approche : Vous pouvez obtenir le même résultat en créant une règle Afficher/Masquer directement dans le champ « Déduction supplémentaire » au lieu d&#39;une règle Lorsque dans « Salaire brut ».

+++

+++ Etape 3 : Ajouter les règles de calcul

**Objectif** : Calculez automatiquement le « Revenu imposable » et l’« Impôt à payer » en fonction des données saisies par l’utilisateur.

**Configurer le calcul du revenu imposable** :

1. **Sélectionnez le champ « Revenu imposable »** et ouvrez l’éditeur de règles
2. **Créer une expression mathématique** :
   - Cliquez Sur **Créer** → Sélectionnez **« Expression Mathématique »**
   - Expression de build : **Salaire brut − Déduction supplémentaire**
   - Faire glisser « Salaire brut » dans le premier champ
   - Sélectionnez l’opérateur **« Moins »**
   - Faire glisser « Déduction supplémentaire » dans le deuxième champ
3. **Enregistrer** : Cliquez Sur **Terminé**

**Configurer le calcul des taxes à payer** :

1. **Sélectionnez le champ « Taxe à payer »** puis ouvrez l’éditeur de règles
2. **Créer une expression mathématique** :
   - Cliquez Sur **Créer** → Sélectionnez **« Expression Mathématique »**
   - Expression de build : **Revenu imposable × 10 ÷ 100**
   - Faites glisser « Revenu imposable » dans le premier champ
   - Sélectionnez l’opérateur **« Multiplié par »**
   - Saisir le `10` sous forme de nombre
   - Cliquez Sur **« Étendre L’Expression »**
   - Sélectionnez l’opérateur **« divisé par »** .
   - Saisir le `100` sous forme de nombre
3. **Enregistrer** : Cliquez Sur **Terminé**

+++

+++ Étape 4 : tester le formulaire

**Vérifiez votre implémentation en testant le flux complet** :

1. **Prévisualiser le formulaire** : cliquez sur le mode Aperçu dans l’éditeur universel
2. **Testez la logique conditionnelle** :
   - Saisir le salaire brut = `30000` → « Déduction supplémentaire » doit rester masqué
   - Entrez Salaire brut = `60000` → « Déduction supplémentaire » doit apparaître
3. **Calculs de test** :
   - Si Salaire brut = `60000`, saisissez Déduction supplémentaire = `5000`
   - Vérifier le revenu imposable = `55000` (60000 - 5 000)
   - Vérifier la taxe à payer = `5500` (55000 × 10 %)

![Prévisualiser un formulaire](/help/edge/docs/forms/assets/rule-editor-form.png)
Image : calculateur de taxe terminé avec champs conditionnels et calculs automatiques

**Critères de réussite** : le formulaire doit afficher/masquer les champs de manière dynamique et calculer les valeurs en temps réel au fur et à mesure que les utilisateurs saisissent des informations.


+++

## Avancé : fonctions personnalisées

Pour une logique commerciale complexe au-delà des fonctionnalités intégrées, vous pouvez créer des fonctions JavaScript personnalisées qui s’intègrent de manière transparente à l’éditeur de règles.

+++ Quand utiliser des fonctions personnalisées

**Scénarios idéaux pour les fonctions personnalisées** :

- **Calculs complexes** : calculs à plusieurs étapes difficiles à exprimer dans la règle d’expression mathématique
- **Validations spécifiques à l’entreprise** : logique de validation personnalisée spécifique à votre organisation ou à votre secteur d’activité
- **Transformations de données** : conversions de formats, manipulations de chaînes ou analyse de données
- **Intégrations externes** : appels à des API internes ou à des services tiers (avec limitations)

**Avantages des fonctions personnalisées** :

- **Réutilisation** : permet d’écrire une seule fois, utiliser dans plusieurs formulaires et règles.
- **Maintenabilité** : logique centralisée, plus facile à mettre à jour et à déboguer
- **Performances** : exécution JavaScript optimisée par rapport aux chaînes de règles complexes
- **Flexibilité** : gérez les cas de périphérie et les scénarios complexes non gérés par des règles standard

+++

+++ Création et implémentation de fonctions personnalisées

**Emplacement du fichier** : toutes les fonctions personnalisées doivent être définies en `/blocks/form/functions.js` dans votre projet Edge Delivery Services.

**Workflow de développement** :

1. **Conception de fonction**
   - Utiliser des noms de fonction descriptifs et orientés vers l’action
   - Définir des types de paramètres clairs et des valeurs de retour
   - Gérer les cas Edge et les entrées non valides de manière appropriée

2. **Mise en œuvre**
   - Écrire du code JavaScript propre et bien commenté
   - Inclure la validation des entrées et la gestion des erreurs
   - Tester les fonctions indépendamment avant l’intégration

3. **Documentation**
   - Ajout de commentaires JSDoc complets
   - Incluez des exemples d’utilisation et des descriptions de paramètres.
   - Documentez toute limite ou dépendance

4. **Déploiement**
   - Fonctions d’exportation à l’aide d’exportations nommées
   - Déployer sur le référentiel du projet
   - Vérifier que la génération est terminée avant de procéder au test

**Exemple d’implémentation** :

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

![Ajouter une fonction personnalisée](/help/edge/docs/forms/assets/create-custom-function.png)
Image : ajout de fonctions personnalisées au fichier functions.js

+++

+++ Utilisation de fonctions personnalisées dans l’éditeur de règles

**Étapes d’intégration** :

1. **Ajouter une fonction au projet**
   - Créer ou modifier des `/blocks/form/functions.js` dans votre projet
   - Inclure votre fonction dans l’instruction d’exportation

2. **Déployer et créer**
   - Validation des modifications dans votre référentiel
   - Vérifiez que le processus de création est terminé
   - Autoriser le temps pour les mises à jour du cache du réseau CDN

3. **Accès dans l’éditeur de règles**
   - Ouvrez l’éditeur de règles pour n’importe quel composant de formulaire.
   - Sélectionnez **« Sortie de fonction »** dans le menu déroulant **Sélectionner une action**
   - Choisissez votre fonction personnalisée dans la liste des fonctions disponibles
   - Configurer des paramètres de fonction à l’aide de champs de formulaire ou de valeurs statiques

4. **Tester minutieusement**
   - Prévisualiser le formulaire pour vérifier le comportement de la fonction
   - Testez avec diverses combinaisons d’entrée, y compris des cas de périphérie
   - Vérification de l’impact des performances sur le chargement et l’interaction des formulaires

![Fonction personnalisée dans l’éditeur de règles](/help/edge/docs/forms/assets/custom-function-rule-editor.png)
Figure : Sélection et configuration de fonctions personnalisées dans l’interface de l’éditeur de règles

**Bonnes pratiques relatives à l’utilisation des fonctions** :

- **Gestion des erreurs** : incluez toujours un comportement de secours pour les échecs de fonction
- **Performances** : fonctions de profil avec des volumes de données réalistes
- **Sécurité** : validez toutes les entrées pour éviter les vulnérabilités de sécurité.
- **Tests** : créez des cas de test couvrant les cas normaux et les cas de périphérie

+++

## Bonnes pratiques pour le développement de règles


+++ Optimisation des performances

- Réduire la complexité des règles ; diviser une logique volumineuse en règles petites et ciblées
- Classer les règles par fréquence (les plus courantes en premier)
- Conserver les ensembles de règles gérables par composant
- Préférez les fonctions personnalisées réutilisables à la duplication de logique

+++

+++ Expérience des utilisateurs et utilisatrices

- Fournir une validation claire et des commentaires intégrés
- Évitez les modifications visuelles discordantes ; utilisez l’option Afficher/masquer avec précaution.
- Test sur plusieurs appareils et mises en page

+++

+++ Hygiène du développement

- Tester avec des cas de périphérie et des valeurs connues
- Vérification sur plusieurs navigateurs
- L’intention du document derrière des règles complexes, pas seulement la mécanique
- Tenir à jour un inventaire de règles pour les formulaires volumineux
- Utiliser des noms cohérents pour les composants et les règles
- Fonctions et tests personnalisés de version dans les environnements hors production

+++

## Résolution des problèmes courants


+++ Règles ne se déclenchant pas

- Vérifier les noms et références des composants
- Vérifier l’ordre d’exécution (de haut en bas)
- Validation de conditions avec des valeurs connues
- Inspecter la console du navigateur pour détecter les erreurs de blocage

+++

+++ Comportement incorrect

- Vérifier les opérateurs et le regroupement (ET/OU)
- Test individuel des fragments d’expression
- Confirmer les types de données (nombres ou chaînes)

+++

+++ Problèmes de performances

- Simplifier les conditions profondément imbriquées
- Fonctions personnalisées de profil
- Réduire les appels externes dans les règles
- Utilisation de sélecteurs et de références spécifiques

+++

+++ Problèmes de fonction personnalisée

- Confirmer le chemin d&#39;accès au fichier : `/blocks/form/functions.js`
- Vérifiez que les exportations nommées sont correctes.
- Vérifiez que la version inclut vos modifications.
- Effacer le cache du navigateur après le déploiement
- Valider les types de paramètres et la gestion des erreurs

+++

+++ Intégration de l’éditeur universel

- Vérifiez que l’extension de l’éditeur de règles est activée.
- Sélectionner un composant pris en charge
- Utiliser un navigateur pris en charge (Chrome, Firefox, Safari)
- Vérifiez que vous disposez des autorisations requises.

## Limites importantes

>[!IMPORTANT]
>
> Contraintes de fonction personnalisées :
>
> - Les imports statiques/dynamiques ne sont pas pris en charge
> - Toute la logique doit résider dans `/blocks/form/functions.js`
> - Les fonctions doivent être synchrones (pas de synchronisation/attente ni de promesse)
> - L’accès à l’API du navigateur est limité.

>[!WARNING]
>
> Considérations relatives à la production :
>
> - Tester minutieusement lors de l’évaluation
> - Surveillance des performances après le déploiement
> - Disposer d’un plan de restauration pour les problèmes de règle
> - Prenez en compte les réseaux lents et les appareils à faible spécification de performance

## Résumé

L’éditeur de règles de l’éditeur universel transforme les formulaires statiques en expériences intelligentes et réactives qui s’adaptent à la saisie utilisateur en temps réel. En utilisant une logique conditionnelle, des calculs automatisés et des règles d’entreprise personnalisées, vous pouvez créer des workflows de formulaire sophistiqués sans écrire de code d’application.

**Fonctionnalités clés que vous avez apprises** :

- **Logique conditionnelle** : affichez et masquez des champs en fonction des entrées de l’utilisateur ou de l’utilisatrice pour créer des expériences ciblées et pertinentes
- **Calculs dynamiques** : calculez automatiquement les valeurs (taxes, totaux, taux) lorsque les utilisateurs interagissent avec le formulaire
- **Validation des données** : implémentez la validation en temps réel avec des messages de commentaires clairs et exploitables.
- **Fonctions personnalisées** : étendez les fonctionnalités de JavaScript pour une logique commerciale et des intégrations complexes
- **Optimisation des performances** : appliquez les bonnes pratiques pour le développement durable et efficace des règles

**Valeur diffusée** :

- **Expérience utilisateur améliorée** : réduisez la charge cognitive grâce à la divulgation progressive et aux flux de formulaires intelligents
- **Réduction des erreurs** : empêchez les envois non valides par le biais de la validation en temps réel et de l’entrée guidée
- **Efficacité améliorée** : automatisez les calculs et la saisie des données pour réduire les efforts des utilisateurs.
- **Solutions gérables** : créez des règles réutilisables et bien documentées qui s’appliquent à l’ensemble de votre entreprise

**Impact commercial** :

Forms deviennent des outils puissants pour la collecte de données, la qualification des prospects et l’interaction client. L’éditeur de règles permet aux auteurs non techniques d’implémenter une logique commerciale sophistiquée, ce qui réduit les coûts de développement tout en améliorant les taux de remplissage des formulaires et la qualité des données.

+++

## Étapes suivantes

**Parcours d’apprentissage recommandé** :

1. **Commencer par les principes de base** : créez des règles simples d’affichage/masquage pour comprendre les concepts de base
2. **Pratiquez avec des tutoriels** : utilisez l’exemple du calculateur d’impôts comme base de vos propres formulaires
3. **Développer progressivement** : ajoutez des expressions mathématiques et des règles de validation à mesure que votre confiance augmente
4. **Implémenter des fonctions personnalisées** : développez des fonctions JavaScript pour les besoins métier spécifiques.
5. **Optimiser et mettre à l’échelle** : appliquer les bonnes pratiques de performances et tenir à jour la documentation des règles

**Ressources supplémentaires** :

- [Documentation sur l’éditeur universel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html?lang=fr) pour un contexte plus large
- [guide d’Extension Manager](/help/implementing/developing/extending/extension-manager.md) pour activer des fonctionnalités supplémentaires
- [Edge Delivery Services forms](/help/edge/docs/forms/overview.md) pour des conseils complets sur le développement de formulaires


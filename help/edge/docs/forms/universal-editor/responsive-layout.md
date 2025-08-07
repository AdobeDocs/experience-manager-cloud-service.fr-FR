---
title: Création d’un Forms réactif avec l’éditeur universel
description: Découvrez comment concevoir, tester et optimiser des formulaires réactifs pour tous les appareils à l’aide de l’éditeur universel. Principal des tests d’appareil, des modèles de disposition et des techniques d’optimisation mobile pour AEM Forms avec Edge Delivery Services.
keywords: formulaires réactifs, formulaires mobiles, test d’appareil, éditeur universel, mise en page adaptative, optimisation des formulaires, conception mobile, conception réactive, mises en page de formulaire, émulateur d’appareil
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1815'
ht-degree: 1%

---


# Création d’un Forms réactif avec l’éditeur universel

Les utilisateurs accèdent aux formulaires sur de nombreux appareils, notamment des ordinateurs de bureau, des tablettes et des smartphones. La conception de formulaires réactifs garantit une expérience optimale à tous les utilisateurs et utilisatrices, quel que soit l’appareil. Ce guide explique comment concevoir, tester et optimiser des formulaires pour n’importe quelle taille d’écran à l’aide de l’éditeur universel.

La création de formulaires réactifs implique deux activités principales :

- **Tests réactifs :** prévisualisez et testez vos formulaires sur différentes tailles d’écran à l’aide d’émulateurs d’appareil.
- **Responsive Design :** permet de sélectionner et d’implémenter des modèles de disposition qui s’adaptent de manière transparente aux différents appareils.

**Dans ce guide, vous apprendrez à**

- Tester des formulaires sur des ordinateurs de bureau, des tablettes et des appareils mobiles
- Sélectionner les modèles de disposition appropriés pour votre contenu
- Application des bonnes pratiques relatives au Responsive Design
- Résolution des problèmes courants liés aux formulaires réactifs
- Optimiser les formulaires pour les performances mobiles

## Importance des Forms réactifs

**Impact de l’expérience utilisateur :**

- Plus de 60 % des utilisateurs accèdent aux formulaires sur des appareils mobiles
- Les mauvaises expériences mobiles entraînent un taux d’abandon 67 % plus élevé
- Les formulaires réactifs peuvent augmenter les taux d’achèvement de jusqu’à 25 %

**Avantages commerciaux :**

- Taux de remplissage de formulaire plus élevés
- Amélioration de la satisfaction des utilisateurs
- Amélioration de la conformité en matière d’accessibilité
- Réduction des coûts de développement et de maintenance

>[!TIP]
>
> **Approche mobile d’abord :** commencez à concevoir pour les appareils mobiles, puis améliorez pour les écrans plus grands. Cela permet de s’assurer que les fonctionnalités de base fonctionnent dans l’environnement le plus limité.

## Partie 1 : Test de Forms sur plusieurs appareils

Le test de vos formulaires sur différents appareils vous permet d’identifier et de résoudre les problèmes de réactivité avant que les utilisateurs et utilisatrices ne les rencontrent. L’éditeur universel fournit un mode émulateur pour simuler différentes tailles et orientations d’écran.

### Comment tester votre Forms

**Étape 1 : ouvrir l’émulateur d’appareil**

1. Ouvrez votre formulaire dans l’éditeur universel.
2. Cliquez sur l’icône ![Émulateur](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%} **Émulateur** de la barre d’outils.
3. Le menu du sélecteur d’appareil s’affiche.

![Interface de test réactive de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

**Étape 2 : sélectionner un appareil à tester**

- **Bureau** (largeur de 1 200 px+) : vue d’édition par défaut
- **Tablette** (largeur de 768 px à 1 199 px) : test d’écran Medium
- **Mobile** (largeur de 320 px à 767 px) : tests sur petit écran
- **Personnalisé** : spécifiez les dimensions exactes pour des appareils spécifiques

**Étape 3 : Tester les orientations de l’appareil**

Utilisez l’icône **Rotateur d’écran** pour tester les deux éléments :

- **Mode Portrait** : orientation mobile standard
- **Mode Paysage** : Vue pivotée de la tablette ou du téléphone

### Résultats des tests de l’appareil

Chaque type d’appareil présente des comportements réactifs uniques :

| **Type d’appareil** | **Largeur d’écran** | **Que vérifier** | **Problèmes courants** |
|-----------------|------------------|-------------------|-------------------|
| **Bureau** | 1200 px+ | Disposition complète, toutes les fonctionnalités visibles | Espaces excessifs, dispositions trop larges |
| **Tablette** | 768px-1199px | Empilage de composants, convivialité de la navigation | Dimensionnement inadapté, problèmes de ciblage tactile |
| **Mobile** | 320 px-767 px | Disposition à une seule colonne, navigation de pouces | Boutons de petit texte étroitement espacés |
| **Personnalisé** | Défini par l’utilisateur | Exigences spécifiques à l’appareil | Cas de périphérie de point d’arrêt |

### Exemples visuels par appareil

**Vue Bureau (1 200 px+) :**
![Vue Formulaire de bureau](/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png)
*Disposition pleine largeur avec champs de formulaire côte à côte.*

**Vue tablette (768 px-1199 px) :**
![Vue de formulaire de tablette](/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png)
*Disposition de largeur Medium avec espacement ajusté des composants.*

**Vue mobile (320 px-767 px) :**
![Vue de formulaire mobile](/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png)
*Disposition à une seule colonne avec composants empilés.*

**Vue d’appareil personnalisée :**
![Vue d’appareil personnalisée](/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png)
*Dimensions spécifiées par l’utilisateur pour les tests ciblés.*

### Workflow de test

**Pour le nouveau Forms :**

1. **Créer dans la vue de bureau :** Commencer avec des fonctionnalités complètes.
2. **Test sur tablette :** vérifier les adaptations pour les écrans moyens.
3. **Valider sur le mobile :** garantir la convivialité sur les petits écrans.
4. **Correction des problèmes de réactivité :** ajustez les dispositions selon les besoins.
5. **Tester à nouveau tous les appareils :** confirmer les correctifs pour toutes les tailles.

**Pour le Forms existant :**

1. **Vérification mobile rapide :** le formulaire fonctionne-t-il sur les téléphones ?
2. **Identifier les zones problématiques :** noter les problèmes de mise en page et de convivialité.
3. **Test systématique :** testez minutieusement la taille de chaque appareil.
4. **Problèmes de document :** suivez les éléments à corriger.
5. **Implémenter des correctifs :** résoudre les problèmes de manière méthodique.

## Partie 2 : Sélection de modèles de mise en page réactifs

Les modèles de disposition déterminent la manière dont le contenu du formulaire s’adapte aux différentes tailles d’écran. Le bon modèle améliore à la fois l’expérience utilisateur et les performances mobiles.

### Aperçu du modèle de mise en page

| **Type de disposition** | **Idéal pour** | **Performances mobiles** | **Complexité** |
|---------------------|-------------------------------------------|------------------------|----------------|
| **Disposition de panneau** | Contenu classé, formulaires de type tableau de bord | Bon | Faible |
| **Disposition de l’Assistant** | Processus à plusieurs étapes, workflows complexes | Excellent | Moyenne |
| **Disposition en accordéon** | Contenu de style FAQ, sections facultatives | Excellent | Faible |

### Guide de décision rapide

**Utiliser la disposition de panneau quand :**

- Votre contenu est divisé en catégories distinctes
- Les utilisateurs doivent afficher plusieurs sections à la fois
- Le contenu est relativement simple

**Utiliser la disposition Assistant quand :**

- Le formulaire comporte plusieurs étapes logiques
- Vous voulez réduire la charge cognitive
- Les utilisateurs mobiles constituent une audience principale

**Utiliser la disposition en accordéon lorsque :**

- Le formulaire contient du contenu facultatif ou secondaire
- La conservation de l&#39;espace est importante
- Le contenu peut être regroupé de manière logique

### Disposition de panneau

**Objectif :** organise le contenu associé en sections visuellement distinctes pouvant être affichées simultanément.

![Exemple de disposition de panneau](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Comportement réactif :**

- **Ordinateur de bureau (1 200 px+) :** les panneaux s’affichent côte à côte ou dans une grille
- **Tablette (768 px-1199 px) :** Les panneaux s’empilent verticalement avec un espacement
- **Mobile (320 px-767 px) :** disposition sur une seule colonne avec des sauts de section clairs

**Étapes d’implémentation :**

1. Utilisez le [composant Panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).
2. Regroupez les champs associés dans chaque panneau.
3. Ajoutez des en-têtes clairs pour chaque section.
4. Assurer un espacement adéquat entre les panneaux.

**Bonnes pratiques :**

- Limitez-vous à 3 ou 4 panneaux sur le bureau pour éviter de surcharger les utilisateurs.
- Utilisez des titres descriptifs pour chaque panneau.
- Regroupez logiquement les champs liés afin de réduire la charge cognitive.
- Tester la navigation du panneau sur les appareils tactiles.

**Exemples de cas d’utilisation :**

- **Poste :** Informations personnelles, Éducation, Expérience, Références
- **Enregistrement du produit :** informations de base, spécifications techniques, informations sur la garantie
- **Survey Forms : Données démographiques** Préférences, Commentaires, Contact

### Disposition de l’Assistant

**Objectif :** guide les utilisateurs à travers des processus complexes étape par étape, en réduisant la charge cognitive et en améliorant les taux d&#39;achèvement.

![Exemple de mise en page Assistant](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Comportement réactif :**

- **Tous les appareils :** maintient le focus en une seule étape pour une expérience mobile optimale.
- **Contenu de l’étape :** s’adapte à chaque étape (empilement ou côte à côte).
- **Navigation :** boutons tactiles suffisamment espacés.
- **Indicateur de progression :** se met à l’échelle en fonction de la taille de l’écran.

**Étapes d’implémentation :**

1. Utilisez le composant [Wizard](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).
2. Divisez les formulaires complexes en étapes logiques (3 à 7 étapes sont optimales).
3. Incluez des indicateurs de progression pour l’orientation de l’utilisateur.
4. Fournissez des commandes de navigation claires (Suivant, Précédent, Enregistrer).

**Optimisation mobile :**

- Utilisez des cibles tactiles de grande taille (minimum 44 px) pour les boutons de navigation.
- Assurez-vous que les indicateurs d’étape sont clairs et visibles sur les petits écrans.
- Limitez le nombre de champs par étape pour réduire le défilement.
- Activez l’enregistrement automatique pour éviter la perte de données.

**Bonnes pratiques :**

- Assurez la progression logique des étapes : chaque étape doit s’appuyer sur la précédente.
- Utilisez des titres d’étape clairs afin que les utilisateurs sachent à quoi s’attendre.
- Validez l’entrée à chaque étape pour détecter les erreurs de manière précoce.
- Autoriser les utilisateurs à revenir en arrière pour consulter ou modifier des informations.

**Exemples de cas d’utilisation :**

- **Réclamations d&#39;assurance :** Incident → Preuve → Examen des → personnelles
- **Configuration du compte :** informations de base → préférences → confirmation de la → de sécurité
- **Processus de commande :** Produits → Expédition → Paiement → Synthèse

### Disposition en accordéon

**Objectif :** permet d’économiser de l’espace en organisant le contenu en sections réductibles, idéales pour les informations facultatives ou secondaires.

![Exemple de disposition en accordéon](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Comportement réactif :**

- **Excellentes performances mobiles :** seul le contenu pertinent est affiché.
- **En-têtes optimisés pour les écrans tactiles :** sections faciles à appuyer et à développer.
- **Animations fluides :** fournit un retour visuel pour les interactions.
- **Gain d’espace :** réduit le défilement sur tous les appareils.

**Étapes d’implémentation :**

1. Utilisez le composant [Accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion).
2. Regroupez les contenus facultatifs associés dans chaque section.
3. Utilisez des en-têtes de section descriptifs.
4. Définissez les états d’ouverture/de fermeture par défaut appropriés.

**Avantages mobiles :**

- Réduit le défilement en réduisant les sections inutilisées.
- Interaction conviviale avec des mouvements naturels de développement/réduction.
- Chargement plus rapide : seul le contenu actif est visible.
- Meilleure concentration : les utilisateurs ne voient que ce dont ils ont besoin.

**Bonnes pratiques :**

- Utilisez des en-têtes de section clairs afin que les utilisateurs sachent ce qu’il contient avant de développer.
- Regroupez logiquement les contenus associés dans chaque section.
- Définissez les sections importantes à développer si nécessaire.
- Fournissez de brefs aperçus des sections pour aider les utilisateurs à décider quoi développer.

**Exemples de cas d’utilisation :**

- **Configuration du produit :** de base → accessoires → avancés → support
- **FAQ Forms :** Facturation des → de compte → → technique Général
- **Paramètres Forms :** Confidentialité → Notifications → Apparence → Avancé

## Partie 3 : bonnes pratiques en matière de conception réactive

### Bonnes pratiques par type d’appareil

+++Optimisation mobile (320 px-767 px)

**Pratiques essentielles :**

- Utilisez une disposition sur une seule colonne pour tout le contenu.
- Fournissez de grands boutons tactiles (hauteur minimale de 44 px).
- Simplifiez la navigation avec des options de retour/suivant claires.
- Réduire le défilement dans chaque section.
- Mise au point automatique sur le premier champ pour afficher le clavier.

**Instructions Spécifiques Au Champ :**

- **Entrées de texte :** pleine largeur avec une marge intérieure suffisante.
- **Listes déroulantes :** utilisez des éléments de sélection natifs pour une meilleure expérience tactile.
- **Sélecteurs de date :** utilisez des entrées de date natives pour la compatibilité mobile.
- **Chargements de fichiers :** fournissez des zones de chargement larges et claires.

+++

+++Optimisation des tablettes (768 px-1 199 px)

**Stratégies de mise en page :**

- Utilisez des dispositions à deux colonnes pour les champs associés.
- Testez les orientations portrait et paysage.
- Prise en charge des interactions tactiles et souris.
- Fournissez des zones de contenu plus vastes tout en préservant la lisibilité.

+++

+++Optimisation de l’ordinateur de bureau (1 200 px+)

**Fonctionnalités avancées :**

- Utilisez des dispositions à plusieurs colonnes pour une utilisation efficace de l’espace.
- Proposez des raccourcis clavier aux utilisateurs expérimentés.
- Implémentez les états de survol pour les commentaires interactifs.
- Fournissez une validation avancée avec des messages d’erreur détaillés.

+++

## Dépannage complet

### Problèmes de mise en page

+++Sauts de disposition de formulaire sur mobile

**Causes fréquentes :**

- Eléments à largeur fixe qui ne sont pas mis à l’échelle
- CSS conçu pour des dispositions bureau-first
- Images ou contenu qui débordent de leurs conteneurs

**Solutions:**

- Assurez-vous que les images et les conteneurs s’adaptent à la taille de l’écran.
- Utilisez une conception mobile-first avec amélioration progressive.
- Testez avec des émulateurs d’appareil et des appareils réels.
- Utilisez un dimensionnement flexible au lieu de dimensions fixes.

+++

+++Toucher les cibles trop petites

**Causes fréquentes :**

- Boutons de moins de 44 px × 44 px
- Éléments interactifs placés trop près les uns des autres
- CSS personnalisé remplaçant les paramètres par défaut de l’éditeur tactile

**Solutions:**

- Assurez-vous que tous les éléments interactifs font au moins 44 px × 44 px.
- Ajouter un espacement entre les boutons et les liens.
- Testez l’interaction tactile avec les doigts réels, pas seulement avec une souris.
- Augmentez les zones cibles tactiles pour faciliter la touche.

+++

+++Problèmes de dépassement de capacité du contenu

**Causes fréquentes :**

- Texte long ou étiquettes qui ne sont pas renvoyées à la ligne
- Conteneurs à largeur fixe
- Images qui ne sont pas correctement dimensionnées

**Solutions:**

- Activez l’habillage du texte pour le contenu long.
- Utilisez des images réactives à l’échelle appropriée.
- Mettez en œuvre des dispositions flexibles qui s’adaptent au contenu.
- Testez avec différentes longueurs de contenu.

+++

### Problèmes de performances

+++Chargement lent sur Mobile

**Causes fréquentes :**

- Images volumineuses non optimisées pour les appareils mobiles
- Exécution excessive de JavaScript
- Trop de champs de formulaire à la fois

**Solutions:**

- Optimisez les images pour différentes tailles d’écran.
- Chargez du contenu non critique uniquement lorsque cela est nécessaire.
- Utilisez des techniques pour accélérer le chargement mobile.
- Réduisez les scripts et widgets tiers.

+++

### Tests et validations

+++Différences entre émulateur et appareil réel

**Causes fréquentes :**

- Différences de rendu spécifiques au navigateur
- Différences entre les interactions tactile et souris
- Variations de vitesse du réseau

**Solutions:**

- Testez sur les appareils réels chaque fois que possible.
- Utilisez plusieurs navigateurs pour les tests d’émulateur.
- Simulez différentes vitesses de réseau pendant les tests.
- Effectuez une validation avec des utilisateurs réels dans des environnements cibles.

+++

## Mesures de succès pour le Forms réactif

+++Indicateurs clés de performance

**Mesures d’expérience utilisateur :**

- **Taux d’achèvement du formulaire :** Cible 85 %+ sur mobile
- **Délai d’exécution :** le délai d’exécution mobile doit être inférieur à 20 % du bureau.
- **Taux d’erreur :** erreurs de validation inférieures à 5 %
- **Points d’abandon :** identifier l’endroit où les utilisateurs abandonnent

**Performances techniques :**

- **Temps de chargement des pages :** moins de 3 secondes sur les réseaux 3G
- **Core Web Vitals :** tous les benchmarks de performances de Google
- **Score d’accessibilité :** conformité WCAG 2.1 AA
- **Compatibilité entre navigateurs :** plus de 98 % de fonctionnalités dans les principaux navigateurs

+++

+++Liste de contrôle de test

**Avant publication :**

- Testez le formulaire sur les appareils mobiles réels.
- Assurez-vous que toutes les cibles tactiles sont au moins de 44 px × 44 px.
- Vérifiez la lisibilité du texte à toutes les tailles d’écran.
- Confirmez que la validation du formulaire fonctionne sur tous les appareils.
- Vérifiez que le temps de chargement est inférieur à 3 secondes sur le mobile.
- Vérifiez que tous les éléments interactifs sont accessibles.
- Testez l’envoi du formulaire sur tous les appareils pris en charge.

+++

## Étapes suivantes

**Actions immédiates :**

1. **Contrôler vos formulaires actuels :** tester les formulaires existants à l’aide de l’émulateur d’appareil.
2. **Identifier les gains rapides :** commencez par résoudre les problèmes évidents d’utilisation mobile.
3. **Donner la priorité aux formulaires à trafic élevé :** vous concentrer sur les formulaires ayant le plus d’impact sur les utilisateurs.
4. **Implémentez une approche mobile-first :** commencez par la conception d’écran la plus petite.

**Optimisation avancée :**

- **Surveillance des performances :** configurez des analyses pour effectuer le suivi des mesures de formulaire.
- **Tests A/B :** expérimentez différentes dispositions et approches.
- **Collecte des commentaires des utilisateurs :** permet de recueillir des informations auprès d’utilisateurs réels.
- **Amélioration continue :** révisez et optimisez régulièrement les formulaires.



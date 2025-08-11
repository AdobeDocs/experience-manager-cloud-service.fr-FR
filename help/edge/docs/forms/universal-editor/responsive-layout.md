---
title: Création d’un Forms réactif avec l’éditeur universel
description: Découvrez comment concevoir, tester et optimiser des formulaires réactifs pour tous les appareils à l’aide de l’éditeur universel. Principal des tests d’appareil, des modèles de disposition et des techniques d’optimisation mobile pour AEM Forms avec Edge Delivery Services.
keywords: formulaires réactifs, formulaires mobiles, test d’appareil, éditeur universel, mise en page adaptative, optimisation des formulaires, conception mobile, conception réactive, mises en page de formulaire, émulateur d’appareil
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '2382'
ht-degree: 1%

---


# Création d’un Forms réactif avec l’éditeur universel

Le paysage web moderne exige des formulaires qui fonctionnent de manière transparente sur un spectre sans cesse croissant d’appareils et de tailles d’écran. Des grands écrans de bureau aux écrans de smartphones compacts, les utilisateurs attendent des expériences homogènes et intuitives, quel que soit l’appareil qu’ils choisissent. La création de formulaires réactifs n’est plus facultative. Il s’agit d’une exigence fondamentale pour fournir des expériences digitales professionnelles, accessibles et optimisées pour la conversion.

L’éditeur universel fournit des outils et des méthodologies complets pour développer des formulaires réactifs qui s’adaptent intelligemment à diverses dimensions d’écran, méthodes de saisie et contextes utilisateur. Ce guide explore les bases techniques, les stratégies d’implémentation et les techniques d’optimisation nécessaires à la création de formulaires offrant des performances exceptionnelles sur tous les appareils, tout en préservant la convivialité, l’accessibilité et l’attrait visuel.

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

La disposition Panneau organise le contenu associé en sections visuellement distinctes, ce qui permet aux utilisateurs et aux utilisatrices d’afficher plusieurs sections à la fois. Cette disposition est idéale pour les formulaires contenant des informations classées qui bénéficient d’une présentation côte à côte sur des écrans plus grands.

![Exemple de disposition de panneau](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**comportement réactif**

- **Ordinateur de bureau (1 200 px et plus) :** les panneaux sont affichés côte à côte ou dans une grille pour une visibilité maximale.
- **Tablette (768 px-1199 px) :** Les panneaux s’empilent verticalement avec un espacement approprié pour maintenir la clarté.
- **Mobile (320 px-767 px) :** les panneaux sont présentés dans une disposition à une seule colonne, avec une séparation nette entre les sections pour une navigation facile.

**Mise en œuvre**

1. Ajoutez le [composant Panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) à votre formulaire.
2. Regroupez les champs associés dans chaque panneau pour conserver une organisation logique.
3. Attribuez des en-têtes explicites et clairs à chaque section de panneau.
4. Assurez-vous que l’espacement entre les panneaux est suffisant pour éviter tout encombrement visuel.

**Bonnes pratiques**

- Limitez le nombre de panneaux à 3 ou 4 sur le bureau pour éviter de surcharger les utilisateurs.
- Utilisez des titres concis et descriptifs pour chaque panneau afin de faciliter la compréhension de l’utilisateur.
- Organisez les champs dans les panneaux de manière logique pour réduire la charge cognitive.
- Testez la navigation du panneau sur les appareils tactiles pour garantir sa convivialité sur toutes les plateformes.

**Cas d’utilisation courants**

- **Application de la fonction :** sections pour les informations personnelles, l’éducation, l’expérience et les références.
- **Enregistrement du produit :** des panneaux pour des informations de base, des spécifications techniques et des informations sur la garantie.
- **Survey Forms : regroupements** données démographiques, de préférences, de commentaires et d’informations de contact.

### Disposition de l’Assistant

La disposition « Assistant » guide les utilisateurs et utilisatrices tout au long d’un processus à plusieurs étapes, présentant une section à la fois. Cette disposition est particulièrement efficace pour les formulaires complexes, car elle réduit la charge cognitive et augmente les taux d’achèvement en divisant le processus en étapes gérables.

![Exemple de mise en page Assistant](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**comportement réactif**

- **Tous les appareils :** permet de garder le focus en une seule étape, ce qui est optimal pour les utilisateurs d’appareils mobiles.
- **Contenu de l’étape :** chaque étape s’adapte de manière réactive, en empilant les champs ou en les organisant côte à côte en fonction de la taille de l’écran.
- **Navigation :** comprend des boutons tactiles avec un espacement adéquat pour une interaction facile.
- **Indicateur de progression :** les barres de progression ou les indicateurs d’étape se dimensionnent de manière appropriée pour différents appareils, fournissant ainsi des commentaires clairs sur le statut d’achèvement.

**Mise en œuvre**

1. Insérez le [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) dans votre formulaire.
2. Divisez le formulaire en étapes logiques, idéalement entre 3 et 7, pour que chaque étape reste ciblée et gérable.
3. Ajoutez des indicateurs de progression pour aider les utilisateurs et utilisatrices à comprendre leur position dans le processus.
4. Fournissez des commandes de navigation claires, telles que les boutons Suivant, Précédent et Enregistrer.

**Conseils d’optimisation pour Mobile**

- Utilisez des cibles tactiles de grande taille (au moins 44 pixels de hauteur) pour les commandes de navigation afin d’améliorer l’accessibilité.
- Assurez-vous que les indicateurs d’étape sont visibles et lisibles sur les petits écrans.
- Limitez le nombre de champs par étape pour minimiser le défilement et améliorer la mise au point.
- Activez la fonctionnalité d’enregistrement automatique pour éviter la perte de données si les utilisateurs quittent le formulaire.

**Bonnes pratiques**

- Concevez des étapes pour suivre une progression logique, chaque étape s’appuyant sur la précédente.
- Utilisez des titres clairs et descriptifs pour chaque étape afin de définir les attentes des utilisateurs.
- Validez les entrées utilisateur à chaque étape pour détecter les erreurs au plus tôt et réduire la frustration.
- Permet aux utilisateurs de revenir en arrière pour consulter ou modifier les informations précédentes sans perdre de données.

**Cas d’utilisation courants**

- **Réclamations d’assurance :** procédure à suivre pour les détails sur l’incident, la soumission des preuves, les informations personnelles et l’examen.
- **Configuration du compte :** étapes pour les informations de base, les préférences, les paramètres de sécurité et la confirmation.
- **Processus de commande :** étapes de sélection des produits, des informations d’expédition, des détails de paiement et de la synthèse de la commande.

### Disposition en accordéon

La disposition en accordéon permet de gagner de l’espace en organisant le contenu en sections réductibles, ce qui le rend idéal pour les informations facultatives ou secondaires. Cette disposition est particulièrement efficace pour les formulaires dont le contenu peut être regroupé logiquement et n’a pas besoin d’être affiché en une seule fois.

![Exemple de disposition en accordéon](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**comportement réactif**

- **Performances mobiles :** seule la section appropriée est développée, ce qui réduit la nécessité de faire défiler l’écran et améliore les temps de chargement.
- **En-têtes optimisés pour les écrans tactiles :** les en-têtes de section sont faciles à appuyer et à développer et prennent en charge les gestes naturels sur les appareils mobiles.
- **Animations lissées :** le développement et la réduction des sections fournissent un retour visuel pour les interactions utilisateur.
- **Efficacité de l’espace :** les sections réduites réduisent l’espace vertical, ce qui facilite la navigation dans le formulaire sur tous les appareils.

**Mise en œuvre**

1. Ajoutez le [composant d’accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) à votre formulaire.
2. Regroupez les contenus secondaires ou facultatifs associés dans chaque section d’accordéon.
3. Utilisez des en-têtes clairs et descriptifs pour chaque section afin d’aider les utilisateurs et les utilisatrices à comprendre les informations qu’elles contiennent.
4. Définissez les états d’ouverture ou de fermeture par défaut appropriés pour chaque section en fonction de l’importance et des besoins de l’utilisateur.

**Avantages mobiles**

- Réduit le défilement en réduisant les sections inutilisées, ce qui permet aux utilisateurs de se concentrer sur une section à la fois.
- L’interaction tactile prend en charge les mouvements naturels de développement/réduction.
- Chargement plus rapide, car seul le contenu actif est visible.
- Amélioration de la cible d’action, car les utilisateurs et utilisatrices ne voient que les informations dont ils ont besoin à un moment donné.

**Bonnes pratiques**

- Utilisez des en-têtes de section clairs afin que les utilisateurs sachent à quoi s’attendre avant de développer une section.
- Regroupez logiquement le contenu associé dans chaque section pour faciliter la compréhension.
- Définissez les sections importantes à développer si une attention immédiate est requise.
- Fournissez de brefs aperçus ou des résumés des sections pour aider les utilisateurs et les utilisatrices à décider quelles sections développer.

**Cas d’utilisation courants**

- **Configuration du produit :** sections pour les options de base, les paramètres avancés, les accessoires et l’assistance.
- **FAQ Forms :** regroupements pour les questions relatives au compte, à la facturation, aux aspects techniques et aux aspects généraux.
- **Paramètres Forms :** sections pour les options Confidentialité, Notifications, Apparence et Avancé.


## Partie 3 : bonnes pratiques en matière de conception réactive

### Bonnes pratiques par type d’appareil

+++Optimisation mobile (320 px-767 px)

**Disposition et interaction :**

- Utilisez une disposition à une seule colonne pour tout le contenu du formulaire afin d’optimiser la lisibilité et la facilité d’utilisation.
- Assurez-vous que tous les boutons et éléments interactifs ont une hauteur d’au moins 44 pixels pour une interaction tactile fiable.
- Fournissez une navigation claire et simple avec des boutons Précédent et Suivant visibles.
- Réduisez le besoin de faire défiler chaque section en divisant les formulaires longs.
- Concentrez-vous automatiquement sur le premier champ de saisie pour demander le clavier mobile.

**Instructions relatives aux champs :**

- Les champs de texte doivent couvrir toute la largeur de l’écran avec une marge intérieure suffisante pour l’entrée tactile.
- Utilisez des éléments de liste déroulante/sélection natifs pour une convivialité mobile optimale.
- Implémentez des sélecteurs de date natifs pour une expérience mobile cohérente.
- Agrandissez les zones de chargement de fichiers et donnez-leur des libellés clairs pour un accès facile.

+++

+++Optimisation des tablettes (768 px-1 199 px)

**Disposition et convivialité :**

- Utilisez des dispositions à deux colonnes pour les champs connexes afin de tirer parti de l’espace d’écran accru.
- Testez l’aspect et la convivialité du formulaire dans les orientations portrait et paysage.
- Conçu pour les entrées tactiles et de souris, il garantit que toutes les commandes sont facilement accessibles.
- Augmentez la taille de la zone de contenu tout en conservant une hiérarchie visuelle et une lisibilité claires.

+++

+++Optimisation de l’ordinateur de bureau (1 200 px+)

**Fonctionnalités avancées et mise en page :**

- Utilisez des dispositions à plusieurs colonnes pour utiliser efficacement l’espace horizontal et réduire le défilement vertical.
- Fournissez des raccourcis clavier pour des actions fréquentes afin de prendre en charge les utilisateurs expérimentés.
- Implémentez des états de survol et un retour visuel pour les éléments interactifs.
- Proposez une validation avancée avec des messages d’erreur clairs et détaillés pour les formulaires complexes.

+++

## Résolution des problèmes

### Problèmes de mise en page

+++Sauts de disposition de formulaire sur mobile

**Causes possibles :**

- Éléments à largeur fixe qui ne s’adaptent pas aux écrans plus petits
- Desktop-first CSS qui remplace les styles mobiles
- Des images ou du contenu débordant de leurs conteneurs

**Comment corriger :**

- Assurez-vous que toutes les images et tous les conteneurs utilisent un dimensionnement relatif ou en pourcentage.
- Commencez par une approche CSS mobile-first et superposez les améliorations pour les écrans plus grands.
- Testez des formulaires à l’aide d’émulateurs d’appareil et d’appareils réels.
- Évitez les cotes fixes et utilisez des mises en page flexibles.

+++

+++Toucher les cibles trop petites

**Causes possibles :**

- Boutons ou liens de moins de 44 px par 44 px
- Éléments interactifs placés trop près les uns des autres
- CSS personnalisé réduisant la taille cible tactile par défaut

**Comment corriger :**

- Assurez-vous que chaque élément interactif fait au moins 44 px par 44 px.
- Ajoutez un espacement adéquat entre les boutons, les liens et les autres commandes.
- Testez avec de vrais appareils tactiles, pas seulement avec une souris.
- Développez les zones cibles tactiles selon vos besoins pour l’accessibilité.

+++

+++Problèmes de dépassement de capacité du contenu

**Causes possibles :**

- Texte long ou étiquettes qui ne sont pas renvoyées à la ligne
- Conteneurs à largeurs fixes
- Images qui ne sont pas dimensionnées de manière réactive

**Comment corriger :**

- Activez l’habillage du texte pour tous les libellés et contenus.
- Utilisez des images réactives qui s’adaptent au conteneur.
- Concevez des dispositions flexibles qui s’adaptent à des longueurs de contenu variables.
- Testez avec du contenu court et long pour garantir l’adaptabilité.

+++

### Problèmes de performances

+++Chargement lent sur Mobile

**Causes possibles :**

- Images volumineuses non optimisées
- JavaScript lourde ou excessive
- Trop de champs de formulaire chargés simultanément

**Comment corriger :**

- Optimisez les images pour les appareils mobiles et utilisez les formats de fichiers appropriés.
- Différer ou charger en différé du contenu non critique.
- Réduisez l’utilisation de scripts et de widgets tiers.
- Rationalisez les champs de formulaire pour ne charger que ce qui est nécessaire.

+++

### Tests et validations

+++Différences entre émulateur et appareil réel

**Causes possibles :**

- Différences dans les moteurs de rendu du navigateur
- L’interaction tactile n’est pas simulée avec précision par la souris
- Incohérences de vitesse réseau

**Comment corriger :**

- Toujours effectuer des tests sur des appareils réels en plus des émulateurs.
- Utilisez plusieurs navigateurs et appareils pour effectuer des tests complets.
- Simulez différentes vitesses de réseau pour identifier les goulots d’étranglement en termes de performances.
- Recueillez les commentaires de véritables utilisateurs de votre audience cible.

+++

## Mesures de succès pour le Forms réactif

+++Indicateurs clés de performance

**Expérience utilisateur :**

- **Taux de remplissage des formulaires :** visez un taux de 85 % ou plus sur les appareils mobiles.
- **Délai d’exécution :** les utilisateurs mobiles doivent remplir les formulaires dans un délai de 20 % du temps d’exécution du bureau.
- **Taux d’erreur :** conserver les erreurs de validation en dessous de 5 %.
- **Points d’abandon :** identifier et gérer les étapes de restitution des utilisateurs.

**Performances techniques :**

- **Temps de chargement de la page :** moins de 3 secondes sur une connexion 3G.
- **Core Web Vitals :** atteignez ou dépassez les seuils recommandés pour le Google.
- **Accessibilité :** respecter la norme WCAG 2.1 AA.
- **Compatibilité des navigateurs :** garantir plus de 98 % de fonctionnalités sur tous les principaux navigateurs.

+++

+++Liste de contrôle de test

**Liste de contrôle de pré-publication :**

- Testez le formulaire sur des appareils mobiles réels (pas seulement des émulateurs).
- Assurez-vous que toutes les cibles tactiles sont au moins de 44 px × 44 px.
- Vérifiez la lisibilité du texte pour toutes les tailles d’écran prises en charge.
- Vérifiez que la validation des formulaires fonctionne de manière cohérente sur tous les appareils et navigateurs.
- Assurez-vous que le temps de chargement du mobile est inférieur à 3 secondes.
- Vérifiez que tous les éléments interactifs sont accessibles via le clavier et les lecteurs d’écran.
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



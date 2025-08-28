---
title: Créer des formulaires réactifs avec l’éditeur universel
description: Découvrez comment concevoir, tester et optimiser des formulaires réactifs pour tous les appareils à l’aide de l’éditeur universel. Maîtrisez les tests d’appareil, les modèles de mise en page et les techniques d’optimisation mobile pour AEM Forms avec Edge Delivery Services.
keywords: Formulaires réactifs, formulaires mobiles, test d’appareil, éditeur universel, mise en page adaptative, optimisation des formulaires, conception mobile, conception réactive, mises en page de formulaire, émulateur d’appareil
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: ht
source-wordcount: '2382'
ht-degree: 100%

---


# Créer des formulaires réactifs avec l’éditeur universel

Le paysage web moderne exige des formulaires qui fonctionnent de manière transparente sur un éventail toujours croissant d’appareils et de tailles d’écran. Des grands écrans de bureau aux écrans compacts des smartphones, les utilisateurs et utilisatrices attendent des expériences homogènes et intuitives, quel que soit l’appareil qu’ils choisissent. La création de formulaires réactifs n’est plus facultative. Il s’agit d’une exigence fondamentale pour fournir des expériences numériques professionnelles, accessibles et optimisées pour la conversion.

L’éditeur universel fournit des outils et des méthodologies complets pour développer des formulaires réactifs qui s’adaptent intelligemment à diverses dimensions d’écran, méthodes de saisie et contextes d’utilisation. Ce guide explore les bases techniques, les stratégies d’implémentation et les techniques d’optimisation nécessaires à la création de formulaires offrant des performances exceptionnelles sur tous les appareils, tout en préservant la convivialité, l’accessibilité et l’attrait visuel.

La création de formulaires réactifs implique deux activités principales :

- **Test réactif :** prévisualisez et testez vos formulaires sur différentes tailles d’écran à l’aide d’émulateurs d’appareil.
- **Conception réactive :** sélectionnez et implémentez des modèles de mise en page qui s’adaptent de manière transparente aux différents appareils.

**Dans ce guide, vous allez apprendre à accomplir ce qui suit :**

- Tester des formulaires sur des ordinateurs de bureau, des tablettes et des appareils mobiles
- Sélectionner les modèles de mise en page appropriés pour votre contenu.
- Appliquer des bonnes pratiques relatives à la conception réactive.
- Résoudre des problèmes courants liés aux formulaires réactifs.
- Optimiser les formulaires pour les performances mobiles.

## Importance des formulaires réactifs

**Impact sur l’expérience d’utilisation :**

- Plus de 60 % des utilisateurs et utilisatrices accèdent aux formulaires sur des appareils mobiles
- Les mauvaises expériences mobiles entraînent un taux d’abandon 67 % plus élevé
- Les formulaires réactifs peuvent augmenter les taux de remplissage jusqu’à 25 %

**Avantages commerciaux :**

- Taux de remplissage de formulaire plus élevés
- Amélioration de la satisfaction des utilisateurs et utilisatrices
- Amélioration de la conformité en matière d’accessibilité
- Réduction des coûts de développement et de maintenance

>[!TIP]
>
> **Approche « Le mobile d’abord » :** commencez par concevoir pour les appareils mobiles, puis améliorez pour les écrans plus grands. Cela permet de s’assurer que les fonctionnalités de base fonctionnent dans l’environnement limité.

## Partie 1 : test de formulaires sur plusieurs appareils

Le test de vos formulaires sur différents appareils vous permet d’identifier et de résoudre les problèmes de réactivité avant que les utilisateurs et utilisatrices ne les rencontrent. L’éditeur universel fournit un mode émulateur pour simuler différentes tailles et orientations d’écran.

### Test de vos formulaires

**Étape 1 : ouvrir l’émulateur d’appareil**

1. Ouvrez votre formulaire dans l’éditeur universel.
2. Cliquez sur l’icône ![icône Émulateur](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%} **Émulateur** dans la barre d’outils.
3. Le menu du sélecteur d’appareil s’affiche.

![Interface de test réactif de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

**Étape 2 : sélectionner un appareil à tester**

- **Bureau** (largeur de +1 200 pixels) : vue de modification par défaut.
- **Tablette** (largeur de 768 à 1 199 pixels) : test d’écran de moyenne taille.
- **Mobile** (largeur de 320 à 767 pixels) : test d’écran de petite taille.
- **Personnalisé** : spécifiez des dimensions exactes pour des appareils spécifiques.

**Étape 3 : tester les orientations d’appareil**

Utilisez l’icône **Rotation d’écran** pour tester les deux éléments suivants :

- **Mode Portrait** : orientation mobile standard
- **Mode Paysage** : vue de tablette ou de téléphone tournée

### Résultats de test d’appareil

Chaque type d’appareil présente des comportements réactifs uniques :

| **Type d’appareil** | **Largeur d’écran** | **Éléments à vérifier** | **Problèmes courants** |
|-----------------|------------------|-------------------|-------------------|
| **Bureau** | + 1 200 pixels | Mise en page complète, toutes les fonctionnalités sont visibles | Espaces excessifs, mises en page trop larges |
| **Tablette** | 768 à 1 199 pixels | Empilement de composants, convivialité de la navigation | Dimensionnement inadapté, problèmes de ciblage tactile |
| **Mobile** | 320 à 767 pixels | Mise en page à une seule colonne, navigation au pouce | Texte de petite taille, boutons trop rapprochés |
| **Personnalisé** | Défini par l’utilisateur ou l’utilisatrice | Exigences spécifiques à l’appareil | Bords de points d’arrêt |

### Exemples visuels par appareil

**Vue Bureau (+ 1 200 pixels) :**
![Vue de formulaire sur ordinateur de bureau](/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png)
*Mise en page pleine largeur avec champs de formulaire côte à côte.*

**Vue Tablette (768 à 1 199 pixels) :**
![Vue de formulaire sur tablette](/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png)
*Mise en page mi-largeur avec espacement ajusté des composants.*

**Vue Mobile (320 à 767 pixels) :**
![Vue de formulaire mobile](/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png)
*Mise en page à une seule colonne avec composants empilés.*

**Vue d’appareil personnalisée :**
![Vue d’appareil personnalisée](/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png)
*Dimensions spécifiées par l’utilisateur pour les tests ciblés.*

### Workflow de test

**Pour les nouveaux formulaires :**

1. **Créer dans la vue Bureau :** commencez avec des fonctionnalités complètes.
2. **Tester sur tablette :** vérifiez les adaptations pour les écrans de taille moyenne.
3. **Valider sur mobile :** garantissez la convivialité sur les écrans de petite taille.
4. **Corriger les problèmes de réactivité :** ajustez les mises en page selon les besoins.
5. **Tester à nouveau tous les appareils :** confirmez les correctifs sur toutes les tailles.

**Pour les formulaires existants :**

1. **Vérification mobile rapide :** le formulaire fonctionne-t-il sur les téléphones ?
2. **Identifier les zones posant problème :** notez les problèmes de mise en page et de convivialité.
3. **Test systématique :** testez minutieusement sur chaque taille d’appareil.
4. **Documenter les problèmes :** suivez les éléments à corriger.
5. **Implémenter des correctifs :** résolvez les problèmes de manière méthodique.

## Partie 2 : sélection de modèles de mise en page réactifs

Les modèles de mise en page déterminent la manière dont le contenu de votre formulaire s’adapte aux différentes tailles d’écran. Le choix du modèle approprié améliore à la fois l’expérience d’utilisation et les performances mobiles.

### Vue d’ensemble du modèle de disposition

| **Type de disposition** | **Idéal pour** | **Performances mobiles** | **Complexité** |
|---------------------|-------------------------------------------|------------------------|----------------|
| **Mise en page Panneau** | Contenu classé, formulaires de type tableau de bord | Bon | Faible |
| **Mise en page Assistant** | Processus à plusieurs étapes, workflows complexes | Excellent | Moyenne |
| **Mise en page Accordéon** | Contenu de style Questions fréquentes, sections facultatives | Excellent | Faible |

### Guide de décision rapide

**Utiliser la mise en page Panneau dans les situations suivantes :**

- Votre contenu est divisé en catégories distinctes.
- Les utilisateurs et les utilisatrices doivent afficher plusieurs sections à la fois.
- Le contenu est relativement simple

**Utiliser la mise en page Assistant dans les situations suivantes :**

- Le formulaire comporte plusieurs étapes logiques.
- Vous voulez réduire la charge cognitive
- Les utilisateurs et les utilisatrices mobiles constituent une audience principale.

**Utiliser la mise en page Accordéon dans les situations suivantes :**

- Le formulaire contient du contenu facultatif ou secondaire
- La conservation de l’espace est importante
- Le contenu peut être regroupé de manière logique

### Mise en page Panneau

La mise en page Panneau organise le contenu associé en sections visuellement distinctes, ce qui permet aux utilisateurs et aux utilisatrices d’afficher plusieurs sections à la fois. Cette mise en page est idéale pour les formulaires contenant des informations classées qui bénéficient d’une présentation côte à côte sur des écrans plus grands.

![Exemple de mise en page Panneau](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Comportement réactif**

- **Ordinateur de bureau (1 200 px et plus) :** les panneaux sont affichés côte à côte ou dans une grille pour une visibilité maximale.
- **Tablette (768 px-1199 px) :** les panneaux s’empilent verticalement avec un espacement approprié pour maintenir la clarté.
- **Mobile (320 px-767 px) :** les panneaux sont présentés dans une mise en page à une seule colonne, avec une séparation nette entre les sections pour une navigation facile.

**Implémentation**

1. Ajoutez le [composant Panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) au formulaire.
2. Regroupez les champs associés dans chaque panneau pour conserver une organisation logique.
3. Attribuez des en-têtes explicites et clairs à chaque section de panneau.
4. Assurez-vous que l’espacement entre les panneaux est suffisant pour éviter tout encombrement visuel.

**Bonnes pratiques**

- Limitez le nombre de panneaux à 3 ou 4 sur le bureau pour éviter de surcharger les utilisateurs et les utilisatrices.
- Utilisez des titres concis et descriptifs pour chaque panneau afin de faciliter la compréhension de l’utilisateur ou de l’utilisatrice.
- Organisez les champs dans les panneaux de manière logique pour réduire la charge cognitive.
- Testez la navigation du panneau sur les appareils tactiles pour garantir sa convivialité sur toutes les plateformes.

**Cas d’utilisation courants**

- **Candidature :** sections pour les informations personnelles, la formation, l’expérience et les références.
- **Enregistrement du produit :** des panneaux pour les informations de base, les spécifications techniques et les informations sur la garantie.
- **Formulaires d’enquête :** regroupements pour les données démographiques, les préférences, les commentaires et les coordonnées.

### Mise en page Assistant

La mise en page Assistant guide les utilisateurs et les utilisatrices tout au long d’un processus à plusieurs étapes, présentant une section à la fois. Cette mise en page est particulièrement efficace pour les formulaires complexes, car elle réduit la charge cognitive et augmente les taux d’achèvement en divisant le processus en étapes gérables.

![Exemple de mise en page Assistant](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Comportement réactif**

- **Tous les appareils :** conserve un thème à une étape, ce qui est optimal pour les utilisateurs et les utilisatrices d’appareils mobiles.
- **Contenu de l’étape :** chaque étape s’adapte de manière réactive, en empilant les champs ou en les organisant côte à côte en fonction de la taille de l’écran.
- **Navigation :** comprend des boutons tactiles avec un espacement adéquat pour une interaction facile.
- **Indicateur de progression :** les barres de progression ou les indicateurs d’étape se dimensionnent de manière appropriée pour différents appareils, fournissant ainsi des commentaires clairs sur le statut d’achèvement.

**Implémentation**

1. Insérez le [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) dans votre formulaire.
2. Divisez le formulaire en étapes logiques, idéalement entre 3 et 7, pour que chaque étape reste ciblée et gérable.
3. Ajoutez des indicateurs de progression pour aider les utilisateurs et les utilisatrices à comprendre leur position dans le processus.
4. Fournissez des commandes de navigation claires, telles que les boutons Suivant, Précédent et Enregistrer.

**Conseils d’optimisation pour Mobile**

- Utilisez de grandes zones tactiles (d’au moins 44 px de hauteur) pour les contrôles de navigation afin d’améliorer l’accessibilité.
- Assurez-vous que les indicateurs d’étape sont visibles et lisibles sur les petits écrans.
- Limitez le nombre de champs par étape pour minimiser le défilement et améliorer la mise au point.
- Activez la fonctionnalité d’enregistrement automatique pour éviter la perte de données si les utilisateurs ou les utilisatrices quittent le formulaire.

**Bonnes pratiques**

- Concevez des étapes pour suivre une progression logique, chaque étape s’appuyant sur la précédente.
- Utilisez des titres clairs et descriptifs pour chaque étape afin de définir les attentes des utilisateurs et des utilisatrices.
- Validez les entrées des utilisateurs et des utilisatrices à chaque étape pour détecter les erreurs au plus tôt et réduire la frustration.
- Permettez aux utilisateurs et aux utilisatrices de revenir en arrière pour consulter ou modifier les informations précédentes sans perdre de données.

**Cas d’utilisation courants**

- **Déclarations de sinistre :** étapes pour les détails de l’incident, la soumission des preuves, les informations personnelles et la révision.
- **Configuration du compte :** étapes pour les informations de base, les préférences, les paramètres de sécurité et la confirmation.
- **Processus de commande :** étapes de sélection des produits, des informations d’expédition, des détails de paiement et de la synthèse de la commande.

### Mise en page Accordéon

La mise en page Accordéon permet de gagner de l’espace en organisant le contenu en sections réductibles, ce qui le rend idéal pour les informations facultatives ou secondaires. Cette mise en page est particulièrement efficace pour les formulaires dont le contenu peut être regroupé logiquement et n’a pas besoin d’être affiché en une seule fois.

![Exemple de mise en page Accordéon](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Comportement réactif**

- **Performances mobiles :** seule la section appropriée est développée, ce qui réduit la nécessité de faire défiler l’écran et améliore les temps de chargement.
- **En-têtes optimisés pour les écrans tactiles :** les en-têtes de section sont faciles à appuyer et à développer et prennent en charge les gestes naturels sur les appareils mobiles.
- **Animations fluides :** l’expansion et la réduction des sections offrent un retour visuel lors des interactions des utilisatrices et des utilisateurs.
- **Utilisation efficace de l’espace :** les sections réduites minimisent l’espace vertical, ce qui rend le formulaire plus facile à parcourir sur tous les appareils.

**Implémentation**

1. Ajoutez le [composant Accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) à votre formulaire.
2. Regroupez les contenus secondaires ou facultatifs associés dans chaque section d’accordéon.
3. Utilisez des en-têtes clairs et descriptifs pour chaque section afin d’aider les utilisateurs et les utilisatrices à comprendre les informations qu’elles contiennent.
4. Définissez les états d’ouverture ou de fermeture par défaut appropriés pour chaque section en fonction de l’importance et des besoins de l’utilisateur et de l’utilisatrice.

**Avantages mobiles**

- Réduit le défilement en réduisant les sections inutilisées, ce qui permet aux utilisateurs et aux utilisatrices de se concentrer sur une section à la fois.
- L’interaction optimisée pour le tactile prend en charge les gestes naturels d’expansion et de réduction.
- Chargement plus rapide, car seul le contenu actif est visible.
- Concentration améliorée, puisque les utilisateurs et les utilisatrices voient uniquement les informations dont ils ont besoin à un moment donné.

**Bonnes pratiques**

- Utilisez des en-têtes de section clairs afin que les utilisateurs et les utilisatrices sachent à quoi s’attendre avant de développer une section.
- Regroupez logiquement le contenu associé dans chaque section pour faciliter la compréhension.
- Définissez les sections importantes à développer si une attention immédiate est requise.
- Fournissez de brefs aperçus ou des résumés des sections pour aider les utilisateurs et les utilisatrices à décider quelles sections développer.

**Cas d’utilisation courants**

- **Configuration du produit :** sections pour les options de base, les paramètres avancés, les accessoires et l’assistance.
- **Formulaires de FAQ :** regroupements pour les questions de compte, de facturation, techniques et générales.
- **Formulaires de configuration :** sections pour la confidentialité, les notifications, l’apparence et les options avancées.


## Partie 3 : bonnes pratiques en matière de conception réactive

### Bonnes pratiques par type d’appareil

+++Optimisation mobile (320 px-767 px)

**Mise en page et interaction :**

- Utilisez une disposition à une seule colonne pour tout le contenu du formulaire afin d’optimiser la lisibilité et la facilité d’utilisation.
- Assurez-vous que tous les boutons et éléments interactifs ont une hauteur d’au moins 44 pixels pour une interaction tactile fiable.
- Fournissez une navigation claire et simple avec des boutons Précédent et Suivant visibles.
- Réduisez le besoin de faire défiler chaque section en divisant les longs formulaires.
- Concentrez-vous automatiquement sur le premier champ de saisie pour demander le clavier mobile.

**Instructions relatives aux champs :**

- Les champs de texte doivent couvrir toute la largeur de l’écran avec une marge intérieure suffisante pour l’entrée tactile.
- Utilisez des éléments de liste déroulante/sélection natifs pour une convivialité mobile optimale.
- Implémentez des sélecteurs de date natifs pour une expérience mobile cohérente.
- Agrandissez les zones de chargement de fichiers et donnez-leur des libellés clairs pour un accès facile.

+++

+++Optimisation des tablettes (768 px-1199 px)

**Disposition et convivialité :**

- Utilisez des dispositions à deux colonnes pour les champs connexes afin de tirer parti de l’espace d’écran accru.
- Testez l’aspect et la convivialité du formulaire dans les orientations portrait et paysage.
- Concevez pour les saisies tactiles et à la souris, en veillant à ce que tous les contrôles soient facilement accessibles.
- Augmentez la taille de la zone de contenu tout en conservant une hiérarchie visuelle claire et une bonne lisibilité.

+++

+++Optimisation de l’ordinateur de bureau (1200 px+)

**Fonctionnalités avancées et mise en page :**

- Utilisez des mises en page à plusieurs colonnes pour utiliser efficacement l’espace horizontal et réduire le défilement vertical.
- Fournissez des raccourcis clavier pour des actions fréquentes afin de prendre en charge les utilisateurs et les utilisatrices expérimentés.
- Implémentez des états de survol et un retour visuel pour les éléments interactifs.
- Proposez une validation avancée avec des messages d’erreur clairs et détaillés pour les formulaires complexes.

+++

## Résolution des problèmes

### Problèmes de mise en page

+++Sauts de mise en page de formulaire sur mobile

**Causes possibles :**

- Éléments à largeur fixe qui ne s’adaptent pas aux écrans plus petits
- CSS conçu pour ordinateur de bureau qui remplace les styles mobiles
- Des images ou du contenu débordant de leurs conteneurs

**Résolution :**

- Assurez-vous que toutes les images et tous les conteneurs utilisent un dimensionnement relatif ou en pourcentage.
- Commencez par une approche CSS mobile-first et ajoutez des améliorations pour les écrans plus grands.
- Testez les formulaires à l’aide d’émulateurs d’appareils et d’appareils réels.
- Évitez les dimensions fixes ; utilisez des mises en page flexibles.

+++

+++Cibles tactiles trop petites

**Causes possibles :**

- Boutons ou liens de moins de 44 px par 44 px
- Éléments interactifs placés trop près les uns des autres
- CSS personnalisé réduisant la taille cible tactile par défaut

**Résolution :**

- Assurez-vous que chaque élément interactif fait au moins 44 px par 44 px.
- Ajoutez un espacement adéquat entre les boutons, les liens et les autres commandes.
- Testez avec de vrais appareils tactiles, pas seulement avec une souris.
- Développez les zones cibles tactiles selon vos besoins pour l’accessibilité.

+++

+++Problèmes de dépassement de capacité du contenu

**Causes possibles :**

- Texte long ou étiquettes qui ne sont pas renvoyées à la ligne
- Conteneurs à largeurs fixes
- Images qui ne sont pas dimensionnées de manière réactive

**Résolution :**

- Activez l’habillage du texte pour tous les libellés et contenus.
- Utilisez des images réactives qui s’adaptent au conteneur.
- Concevez des mises en page flexibles qui s’adaptent à des longueurs de contenu variables.
- Testez avec du contenu court et long pour garantir l’adaptabilité.

+++

### Problèmes de performances

+++Chargement lent sur Mobile

**Causes possibles :**

- Images volumineuses non optimisées
- JavaScript lourd ou excessif
- Trop de champs de formulaire chargés simultanément

**Résolution :**

- Optimisez les images pour les appareils mobiles et utilisez les formats de fichiers appropriés.
- Différez ou chargez en différé du contenu non critique.
- Réduisez l’utilisation de scripts et de widgets tiers.
- Rationalisez les champs de formulaire pour ne charger que ce qui est nécessaire.

+++

### Problèmes de test et de validation

+++Différences entre émulateur et appareil réel

**Causes possibles :**

- Différences entre moteurs de rendu des navigateurs
- L’interaction tactile n’est pas simulée avec précision par la souris
- Incohérences de vitesse réseau

**Résolution :**

- Testez toujours sur des appareils réels en complément des émulateurs.
- Utilisez plusieurs navigateurs et appareils pour effectuer des tests complets.
- Simulez différentes vitesses de réseau pour identifier les goulots d’étranglement en termes de performances.
- Recueillez les commentaires de véritables utilisateurs et utilisatrices de votre audience cible.

+++

## Mesures de réussite pour les formulaires réactifs

+++Indicateurs clés de performance

**Expérience client :**

- **Taux de remplissage des formulaires :** visez un taux de 85 % ou plus sur les appareils mobiles.
- **Délai d’exécution :** les utilisateurs et les utilisatrices d’appareils mobiles doivent remplir les formulaires dans un délai inférieur de 20 % à celui des ordinateurs de bureau.
- **Taux d’erreur :** conserver les erreurs de validation en dessous de 5 %.
- **Points d’abandon :** identifiez et corrigez les étapes où les utilisateurs et les utilisatrices quittent le processus.

**Performances techniques :**

- **Temps de chargement de la page :** moins de 3 secondes sur une connexion 3G.
- **Core Web Vitals :** atteignez ou dépassez les seuils recommandés par Google.
- **Accessibilité :** respectez la norme WCAG 2.1 AA.
- **Compatibilité des navigateurs :** garantissez plus de 98 % de fonctionnalités sur tous les principaux navigateurs.

+++

+++Liste de contrôle des tests

**Liste de contrôle prépublication :**

- Testez le formulaire sur de véritables appareils mobiles (pas uniquement sur des émulateurs).
- Assurez-vous que toutes les zones tactiles mesurent au moins 44 px × 44 px.
- Vérifiez la lisibilité du texte sur toutes les tailles d’écran prises en charge.
- Vérifiez que la validation des formulaires fonctionne de manière cohérente sur tous les appareils et navigateurs.
- Assurez-vous que le temps de chargement du mobile est inférieur à 3 secondes.
- Vérifiez que tous les éléments interactifs sont accessibles via le clavier et les lecteurs d’écran.
- Testez l’envoi du formulaire sur tous les appareils pris en charge.


+++

## Étapes suivantes

**Actions immédiates :**

1. **Contrôler vos formulaires actuels :** testez les formulaires existants à l’aide de l’émulateur d’appareil.
2. **Identifier les gains rapides :** corrigez d’abord les problèmes évidents d’utilisabilité mobile.
3. **Donner la priorité aux formulaires à trafic élevé :** concentrez-vous sur les formulaires ayant le plus d’impact pour les utilisateurs et les utilisatrices.
4. **Implémenter une approche mobile-first :** commencez par la conception pour le plus petit écran.

**Optimisation avancée :**

- **Suivi des performances :** configurez l’analytique pour suivre les indicateurs des formulaires.
- **Tests A/B :** expérimentez différentes mises en page et approches.
- **Collecte des commentaires des utilisateurs et des utilisatrices :** recueillez des informations auprès d’utilisateurs et d’utilisatrices réels.
- **Amélioration continue :** révisez et optimisez régulièrement les formulaires.



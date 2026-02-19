---
title: Créer des règles dans l’éditeur de communication interactive
description: Créer des règles dans l’éditeur de communication interactive permet aux auteurs de définir des comportements dynamiques qui rendent les communications interactives et intelligentes.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 9538ae2e-e0f5-4e85-943e-00fe99a64725
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# Éditeur de règles dans l’éditeur de communication interactive


>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.


## &#x200B;1. Présentation


L’éditeur de règles de l’éditeur de communication interactive permet aux auteurs de définir des comportements dynamiques qui rendent les communications interactives et intelligentes. Les règles contrôlent le comportement, l’affichage ou le calcul des champs en fonction des actions de l’utilisateur ou des données sous-jacentes, en veillant à ce que chaque communication soit personnalisée et adaptée au contexte.


Des paramètres de visibilité simples à la logique conditionnelle complexe, les règles permettent aux créateurs et aux créatrices de fournir des expériences qui s’adaptent en temps réel, améliorant ainsi la convivialité, la précision et l’engagement.


![Rechercher document IC](/help/forms/interactive-communication/assets/rule-creation.png)


## &#x200B;2. Propriétés


2.1 Configuration des propriétés et des comportements des champs


- **Types d’entrée :** permet de définir le type de données qu’un champ accepte, comme du texte, des nombres, des dates ou des valeurs booléennes, en veillant à une validation et une mise en forme correctes.


- **Règles de visibilité :** permet de déterminer si un champ est visible, masqué ou affiché de manière dynamique en fonction de conditions (par exemple, « Afficher le champ de remise uniquement si le code promotion est appliqué »).


- **Valeurs par défaut :** prédéfinissez des valeurs dans les champs (par exemple, la date du jour, le nom du client du modèle de données) pour gagner du temps et améliorer la précision.


2.2 Mettre en œuvre les calculs, les validations et la logique des règles


- **Logique de champ :** automatisez les calculs et les relations de champs, comme le calcul des montants de facture ou le remplissage automatique des champs dépendants.


- **Règles personnalisées :** créez une logique avancée à l’aide de l’éditeur de règles pour des scénarios complexes tels que les contrôles d’éligibilité ou la tarification basée sur le niveau.


- **Actions conditionnelles :** définissez des déclencheurs qui répondent aux valeurs d’entrée ou de données de l’utilisateur, comme l’activation/la désactivation de champs, l’affichage de messages ou l’embranchement vers différentes sections.


![Rechercher document IC](/help/forms/interactive-communication/assets/rule-creation1.png)


## &#x200B;3. Utilisation


L’éditeur de règles est largement utilisé pour s’assurer que les formulaires et les communications sont réactifs et basés sur le contexte :


- **Affichage dynamique :** masque ou affiche les sections en fonction du type de client ou des options sélectionnées.


- **Validation :** prévenir les erreurs en vérifiant les formats, les plages ou les entrées obligatoires.


- **Calculs automatiques :** simplifiez les tâches utilisateur à l’aide de formules (par exemple, taxe, totaux ou remises).


- **Contrôle de workflow :** activez des boutons, des champs ou des actions spécifiques uniquement lorsque les conditions préalables sont remplies.


- **Personalization :** adaptez la communication au profil, aux préférences ou aux critères d’éligibilité du destinataire.


## &#x200B;4. Bonnes Pratiques


- **Gardez les règles simples :** divisez les logiques complexes en règles plus petites et modulaires pour une maintenance plus facile.


- **Classez par priorité la logique de visibilité :** masquez rapidement les champs inutiles pour rationaliser l’expérience utilisateur.


- **Tester minutieusement :** permet de prévisualiser des règles avec plusieurs jeux de données pour confirmer l’exactitude et éviter les conflits.


- **Utilisez judicieusement les valeurs par défaut :** préremplissez des champs qui changent rarement, mais qui offrent une certaine flexibilité pour les modifications.


- **Tirez parti des actions conditionnelles** Appliquez-les pour améliorer l’interactivité, mais sans surcharger les utilisateurs.


- **Règles de document :** conservez un enregistrement de la logique commerciale pour garantir la clarté pour les développeurs et les parties prenantes.


En configurant les règles de manière réfléchie, les auteurs peuvent créer des communications qui répondent intelligemment aux données et aux actions des utilisateurs, en rationalisant les processus, en réduisant les erreurs et en offrant une expérience personnalisée et transparente.

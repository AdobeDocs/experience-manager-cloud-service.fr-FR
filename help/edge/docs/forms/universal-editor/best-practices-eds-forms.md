---
title: Bonnes pratiques relatives à la conception de formulaires haute performance
description: Découvrez les bonnes pratiques essentielles pour créer des formulaires conviviaux, accessibles et hautement performants à l’aide d’AEM Forms. Améliorez la qualité des données, l’expérience clientèle et les taux de réussite des envois.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: 67b6873b-bb93-4d38-963c-2ca65a1a644b
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: ht
source-wordcount: '761'
ht-degree: 100%

---

# Bonnes pratiques en matière de création de formulaires

## Vue d’ensemble

La création de formulaires efficaces va bien au-delà de la simple mise en œuvre technique : elle nécessite de comprendre l’état d’esprit des utilisateurs et utilisatrices, les normes d’accessibilité et l’optimisation des performances. Ce guide complet propose les bonnes pratiques qui ont fait leurs preuves, afin de concevoir des formulaires que les utilisateurs et utilisatrices souhaiteront réellement remplir.

### Ce que vous apprendrez :

À la fin de ce document, vous aurez appris à :

- Concevoir des formulaires conviviaux et accessibles qui conviennent à tous
- Optimiser les performances et les temps de chargement des formulaires
- Gérer les données des utilisateurs et utilisatrices de manière responsable et transparente
- Implémenter une gestion des erreurs et une validation correctes
- Créer des formulaires qui atteignent des taux de réalisation élevés

### Audience cible

Ce guide est conçu pour les publics suivants :

- **Personnes spécialistes de la conception de formulaires** qui souhaitent créer de meilleures expériences d’utilisation
- **Développeurs et développeuses** qui implémentent une fonctionnalité de formulaire
- **Personnes spécialisées dans l’expérience d’utilisation** qui optimisent les workflows de formulaires
- **Parties prenantes dans l’entreprise** cherchant à améliorer les taux de conversion des formulaires

### Principes de base

Les meilleurs formulaires respectent ces principes de base :

1. **Conception centrée sur l’utilisateur ou l’utilisatrice** - Concentrez-vous sur ce que les personnes doivent réaliser.
2. **Priorité à l’accessibilité** - Assurez-vous que tout le monde puisse utiliser vos formulaires.
3. **Optimisation des performances** - Les formulaires rapides ont plus de chances d’être remplis.
4. **Responsabilité des données** - Respectez la confidentialité des personnes et réduisez au minimum la collecte de données.
5. **Communication claire** - Guidez attentivement les personnes tout au long du processus.

La création de formulaires efficaces n’est pas qu’une question de technologie. Voici comment créer des formulaires conviviaux et pertinents :

## Concevoir des formulaires conviviaux et accessibles

- **Utilisez des libellés clairs et visibles :** chaque champ de formulaire nécessite un `<label>`. Ne vous fiez pas uniquement au texte des espaces réservés (texte dans le champ de saisie), car il disparaît lorsque les utilisateurs et utilisatrices saisissent du texte. En outre, il pose des problèmes ’accessibilité.
   - *Bien :* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
   - *Mauvais :* `<input type="email" placeholder="Email Address">`
- **Restez simple :** utilisez des types d’entrée HTML standard (`<input type="date">`, `<input type="tel">`) si possible. Ils offrent souvent une meilleure prise en charge et accessibilité mobiles que les widgets personnalisés complexes.
- **Ordre logique et regroupement logiques :** organisez les champs de manière logique pour les personnes. Regroupez les champs associés à l’aide de `<fieldset>` et de `<legend>`.
- **Fournissez des instructions claires :** pour les champs qui peuvent prêter à confusion, proposez un texte d’aide concis ou des info-bulles.
- **Navigation au clavier :** assurez-vous que votre formulaire puisse être parcouru à l’aide du clavier uniquement (Tabulation, Maj+Tabulation, Entrée, Barre d’espace).
- **Gestion des erreurs :** permet de rendre les erreurs évidentes et faciles à corriger. Affichez des messages d’erreur en regard du champ approprié et expliquez les problèmes à résoudre.

- **Chargement rapide et visibilité de vos formulaires**

   - **Placez les formulaires en évidence :** si un formulaire est important, assurez-vous qu’il s’affiche facilement sans avoir à faire défiler l’écran trop longuement (en haut de la page, si possible). Les recherches Adobe montrent que de nombreux formulaires ont une faible interaction, car ils sont masqués.
   - **Optimisez les ressources :** conservez la taille maximale de tout code JavaScript ou CSS personnalisé pour vos formulaires afin d’assurer des temps de chargement rapides. Edge Delivery Services facilite le chargement de la page de base, mais les scripts de formulaires volumineux peuvent ralentir le processus.

- **Gestion responsable des données utilisateur**
   - **Demandez uniquement ce dont vous avez besoin :** moins vous demandez d’informations d’identification personnelles (PII), mieux c’est. Chaque champ est une raison potentielle pour laquelle un utilisateur ou une utilisatrice abandonne le formulaire.
   - **Faites preuve de transparence :** expliquez clairement *pourquoi* vous avez besoin de certaines informations et *comment elles seront utilisées*. Lien vers votre politique de confidentialité. Cela crée de la confiance.

- **Amélioration de l’expérience utilisateur : solutions de remplacement au Captcha**

   - **Repenser les captchas visibles :** ces tests de type « tapez les caractères visibles » ou « cliquez sur tous les feux de signalisation » peuvent être très frustrants, en particulier pour les personnes porteuses de handicap, entraînant ainsi un taux d’abandon élevé.

- **Envisagez des solutions de remplacement :**
   - **Champs honeypot (pot de miel) :** ajoutez un champ masqué que seuls les robots peuvent remplir. Si ce champ contient des données, l’envoi est probablement un spam.
   - **Contrôles basés sur l’heure :** permettent de mesurer la vitesse d’envoi d’un formulaire. Les envois trop rapides sont souvent des robots.
   - **reCAPTCHA invisible (v3) :** ce service Google analyse le comportement des personnes en arrière-plan et ne présente un problème que si la personne semble suspecte. C’est souvent une bien meilleure expérience d’utilisation.

## Conception de formulaires : à faire et à ne pas faire

| ✅ À faire - Pour de meilleurs formulaires | ❌ À ne pas faire – À éviter |
|----------------------------------------------------------------------|------------------------------------------------------------------|
| Utiliser des balises `<label>` visibles pour tous les champs | N’utiliser que du texte d’espace réservé au lieu de libellés appropriés |
| Privilégier les types d’entrée HTML standard (par exemple, `<input type="email">`) | Utiliser des widgets personnalisés trop complexes |
| Garantir une navigation complète avec le clavier | Fournir des messages d’erreur vagues ou manquants |
| Afficher des messages d’erreur clairs et exploitables | Demander des données personnelles excessives sans justification |
| Demander uniquement les informations nécessaires | Utiliser des CAPTCHA visibles difficiles à résoudre |
| Expliquer comment les données sont utilisées (informations de confidentialité ou liens) | Masquer le formulaire profondément dans la page |
| Utiliser des techniques de CAPTCHA invisibles ou comportementales |                                                                  |
| Rendre le formulaire facile à trouver sur la page (placement proéminent) |                                                                  |


## Étapes suivantes

Ce guide présente une vue d’ensemble de l’utilisation des formulaires avec AEM Edge Delivery Services. Pour obtenir des instructions détaillées sur les configurations spécifiques, reportez-vous à la documentation officielle d’Adobe Experience Manager :

- [Création basée sur des documents avec les formulaires Edge Delivery Services](/help/edge/docs/forms/tutorial.md)
- [Éditeur universel avec formulaires Edge Delivery Services](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [Création de documents (DA) et incorporation de contenu](https://www.aem.live/developer/da-tutorial?lang=fr)
- [Service d’envoi de formulaires AEM](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)

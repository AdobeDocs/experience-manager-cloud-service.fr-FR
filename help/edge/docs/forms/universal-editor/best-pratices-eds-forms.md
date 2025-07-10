---
title: Bonnes pratiques relatives à la conception de Forms hautes performances
description: Découvrez les bonnes pratiques essentielles pour créer des formulaires conviviaux, accessibles et hautement performants à l’aide d’AEM Forms. Améliorez la qualité des données, l’expérience utilisateur et les taux de réussite des envois.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 67b6873b-bb93-4d38-963c-2ca65a1a644b
source-git-commit: 75d8ea4f0913e690e3374d62c6e7dcc44ea74205
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Bonnes pratiques relatives à la création de Forms

La création de grandes formes va au-delà de la technologie. Voici comment vous assurer que vos formulaires sont conviviaux et atteignent leurs objectifs :

## Concevoir un Forms convivial et accessible

* **Utiliser des libellés clairs et visibles :** chaque champ de formulaire nécessite un `<label>`. Ne vous fiez pas uniquement au texte d’espace réservé (texte dans le champ de saisie), car il disparaît lorsque les utilisateurs et utilisatrices saisissent du texte, et est mauvais pour l’accessibilité.
   * *Bon :* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
   * *Bad:* `<input type="email" placeholder="Email Address">`
* **Restez simple :** utilisez des types d’entrée HTML standard (`<input type="date">`, `<input type="tel">`) si possible. Ils offrent souvent une meilleure prise en charge et accessibilité mobiles que les widgets personnalisés complexes.
* **Ordre logique et regroupement :** organisez les champs de manière logique pour l’utilisateur. Regroupez les champs associés à l’aide des `<fieldset>` et des `<legend>`.
* **Fournissez des instructions claires :** pour les champs qui peuvent prêter à confusion, proposez un texte d’aide concis ou des info-bulles.
* **Navigation au clavier :** assurez-vous que les utilisateurs peuvent parcourir l’ensemble de votre formulaire à l’aide du clavier uniquement (Tabulation, Maj+Tabulation, Entrée, Barre d’espace).
* **Gestion des erreurs :** permet de rendre les erreurs évidentes et faciles à corriger. Affichez des messages d’erreur en regard du champ approprié et expliquez les problèmes à résoudre.

* **Chargement rapide et visibilité de votre Forms**

   * **Placer le Forms en évidence :** si un formulaire est important, assurez-vous que les utilisateurs puissent le voir facilement sans avoir à faire défiler l’écran trop longuement (en haut de la page, si possible). La recherche Adobe montre que de nombreux formulaires ont une faible interaction, car ils sont masqués.
   * **Optimisation d’Assets :** conservez la taille maximale de tout code JavaScript ou CSS personnalisé pour vos formulaires afin d’assurer des temps de chargement rapides. Edge Delivery Services facilite le chargement de la page de base, mais les scripts de formulaires volumineux peuvent ralentir le processus.

* **Gestion responsable des données utilisateur**
   * **Demandez uniquement ce dont vous avez besoin :** moins vous demandez d’informations d’identification personnelles (PII), mieux c’est. Chaque champ est une raison potentielle pour laquelle un utilisateur ou une utilisatrice abandonne le formulaire.
   * **Soyez transparent :** expliquez clairement *pourquoi* vous avez besoin de certaines informations et *comment elles seront utilisées*. Lien vers votre politique de confidentialité. Cela crée de la confiance.

* **Amélioration de l’expérience utilisateur : Captcha Alternatives**

   * **Repenser les captchas visibles :** ces tests de type « tapez le texte ondulé » ou « cliquez sur tous les feux de signalisation » peuvent être très frustrants pour les utilisateurs, en particulier ceux présentant un handicap, et entraînent souvent un taux de chute élevé.

* **Envisagez Des Alternatives :**
   * **Champs de pot de miel :** ajoutez un champ masqué que seuls les robots peuvent remplir. Si elle contient des données, l’envoi est probablement du spam.
   * **Contrôles basés sur l’heure :** permettent de mesurer la vitesse d’envoi d’un formulaire. Les envois trop rapides sont souvent des robots.
   * **reCAPTCHA invisible (v3) :** ce service Google analyse le comportement des utilisateurs en arrière-plan et ne présente un problème que si l’utilisateur semble suspect. C’est souvent une bien meilleure expérience utilisateur.

## Tâches et tâches de conception de formulaire

| ✅ - Pour un meilleur Forms | ❌ à éviter |
|----------------------------------------------------------------------|------------------------------------------------------------------|
| Utiliser des balises `<label>` visibles pour tous les champs | N’utilisez que du texte d’espace réservé au lieu des libellés appropriés. |
| Privilégiez les types d’entrée HTML standard (par exemple, `<input type="email">`). | Utilisation de widgets personnalisés trop complexes |
| Garantir une navigation complète avec le clavier | Fournir des messages d’erreur vagues ou manquants |
| Afficher des messages d’erreur clairs et exploitables | Demander des données personnelles excessives sans justification |
| Demander uniquement les informations nécessaires | Utiliser des CAPTCHA visibles difficiles à résoudre |
| Expliquez comment les données sont utilisées (informations de confidentialité ou liens). | Masquez le formulaire profondément dans la page |
| Utilisation des techniques de CAPTCHA invisibles ou comportementales |                                                                  |
| Rendre le formulaire facile à trouver sur la page (emplacement proéminent) |                                                                  |


## Étapes suivantes

Ce guide présente un aperçu de l’utilisation de forms avec AEM Edge Delivery Services. Pour obtenir des instructions détaillées sur les configurations spécifiques, reportez-vous à la documentation Adobe Experience Manager officielle :

* [Création basée sur des documents avec Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Éditeur universel avec Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Création de documents (DA) et incorporation de contenu](https://www.aem.live/developer/da-tutorial)
* [Service d’envoi AEM Forms](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)

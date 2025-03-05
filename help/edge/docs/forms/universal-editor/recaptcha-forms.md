---
title: Protégez votre Forms avec reCAPTCHA - Un guide visuel
description: Découvrez comment ajouter facilement du reCAPTCHA Google à vos formulaires Edge Delivery Services pour empêcher les spams et les envois de robots
feature: Edge Delivery Services
keywords: reCAPTCHA dans les formulaires, Utilisation de reCAPTCHA dans l’éditeur universel, Ajout de reCAPTCHA dans les formulaires, sécurité des formulaires, protection contre le spam
role: Developer
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 2%

---


# Protection de votre Forms contre le spam grâce à Google reCAPTCHA

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> avec le nom de votre organisation GitHub et le nom du référentiel.</span>



## Pourquoi utiliser reCAPTCHA dans vos formulaires ?

| ![Sécurité](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![Protection des robots](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![Expérience utilisateur](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **Sécurité renforcée** | **Prévention des robots et des spams** | **Expérience utilisateur transparente** |
| Protégez vos formulaires contre les activités frauduleuses et les attaques malveillantes | Empêchez les robots automatisés d’inonder vos formulaires de contenu non pertinent ou nuisible | Le reCAPTCHA invisible fonctionne en coulisses sans perturber les utilisateurs légitimes |

Par exemple, un formulaire de calcul des impôts contenant des informations financières sensibles doit être protégé contre toute utilisation abusive. reCAPTCHA vérifie que les envois proviennent d’utilisateurs authentiques et non de systèmes automatisés.

## Choisissez votre solution reCAPTCHA

Edge Delivery Services Forms prend en charge deux options reCAPTCHA Google :

| ![reCAPTCHA Enterprise](/help/edge/docs/forms/universal-editor/assets/enterprise.svg) | ![reCAPTCHA Standard](/help/edge/docs/forms/universal-editor/assets/standard.svg) |
|:-------------:|:-------------:|
| [**reCAPTCHA Enterprise**](#set-up-recaptcha-enterprise) | [**reCAPTCHA Standard**](#set-up-recaptcha-standard) |
| Détection des fraudes haut de gamme et de qualité professionnelle avec fonctionnalités et personnalisation supplémentaires | Service gratuit avec détection basée sur les scores qui fonctionne de manière invisible en arrière-plan |
| Idéal pour : grandes entreprises ayant des besoins complexes en matière de sécurité | Idéal pour : projets de petite et moyenne envergure ayant des besoins de protection de base |

Les deux options utilisent la détection basée sur les scores (0,0 à 1,0) pour identifier les interactions humaines ou entre robots sans perturber l’expérience utilisateur.

## Configuration de reCAPTCHA Enterprise

### Étape 1 : Obtention De Vos Informations D’Identification Google Cloud

Avant de configurer reCAPTCHA Enterprise, vous aurez besoin des éléments suivants :

- Un projet Google Cloud [](https://cloud.google.com/recaptcha/docs/prepare-environment?hl=fr#before-you-begin) avec votre [ID de projet](https://support.google.com/googleapi/answer/7014113)
- [API reCAPTCHA Enterprise activée](https://cloud.google.com/recaptcha/docs/prepare-environment?hl=fr#enable-api) pour votre projet
- Une [clé API](https://console.cloud.google.com/apis/credentials) pour l’authentification
- Une [clé de site](https://console.cloud.google.com/security/recaptcha) pour votre domaine

### Étape 2 : créer un conteneur de configuration cloud

![Configuration du cloud étape par étape](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Connectez-vous à votre instance d’auteur AEM
2. Accédez à **Outils** > **Général** > **Explorateur de configurations**
3. Recherchez votre formulaire et sélectionnez **Propriétés**
4. Activez **Configurations cloud** dans la boîte de dialogue
5. Enregistrez et publiez votre configuration

### Étape 3 : Configurer reCAPTCHA Enterprise Service

![écran de configuration reCAPTCHA Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Accédez à **Outils** > **Services cloud** > **reCAPTCHA**
2. Accédez à votre formulaire et cliquez sur **Créer**
3. Dans la boîte de dialogue :
   - Sélectionnez la version **ReCAPTCHA Enterprise**
   - Saisir un titre et un nom
   - Ajouter votre ID de projet, votre clé de site et votre clé API
   - Sélectionnez **Clé de site basée sur les scores** comme Type de clé.
   - Définissez un score de seuil (0-1) pour distinguer les humains des robots
4. Cliquez sur **Créer** et publiez votre configuration

## Configuration de reCAPTCHA Standard

### Étape 1 : obtenir vos clés API

Avant de commencer, [obtenez une paire de clés d’API reCAPTCHA](https://www.google.com/recaptcha/admin) (clé de site et clé secrète) à partir de la console reCAPTCHA de Google.

>[!IMPORTANT]
>
>Edge Delivery Services pour AEM Forms ne prend en charge que la version **reCAPTCHA basée sur les scores**.

### Étape 2 : créer un conteneur de configuration cloud

Suivez les mêmes étapes que dans la version Enterprise pour créer et publier un conteneur de configuration cloud.

### Étape 3 : Configurer le service standard reCAPTCHA

Écran de configuration ![reCAPTCHA Standard](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Accédez à **Outils** > **Services cloud** > **reCAPTCHA**
2. Accédez à votre formulaire et cliquez sur **Créer**
3. Dans la boîte de dialogue :
   - Sélectionnez la version **ReCAPTCHA v2**
   - Saisir un titre et un nom
   - Ajouter la clé de site et la clé secrète
4. Cliquez sur **Créer** et publiez votre configuration

## Ajouter reCAPTCHA à votre formulaire

Maintenant que vous avez configuré reCAPTCHA, il est temps de l’ajouter à votre formulaire :

![Ajout du composant reCAPTCHA à un formulaire](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

1. Ouvrez votre formulaire dans l’éditeur universel
2. Accédez à la section Formulaire adaptatif dans l’arborescence de contenu
3. Cliquez sur l’icône **Ajouter** et sélectionnez **Captcha (invisible)** dans la liste Composants de formulaire adaptatif .
   - *Vous pouvez également faire glisser et déposer le composant dans votre formulaire*
4. Cliquez sur **Publier** pour mettre à jour votre formulaire avec la protection reCAPTCHA

Votre formulaire est maintenant protégé ! Consultez-le à l’adresse :
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name>`

![Formulaire avec protection reCAPTCHA activée](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Validation de votre intégration reCAPTCHA

Après avoir ajouté reCAPTCHA à votre formulaire, il est essentiel de vérifier qu’il fonctionne correctement. Pour valider votre implémentation, procédez comme suit :

### Vérification visuelle

Alors que reCAPTCHA v2 (basé sur les scores) fonctionne de manière invisible, vous pouvez confirmer sa présence en procédant comme suit :

1. **Inspecter la source de la page** : faites un clic droit sur la page du formulaire et sélectionnez « Afficher le Source de la page »
   - Recherchez l’inclusion de script reCAPTCHA avec la clé de votre site
   - Exemple : `<script src="https://www.google.com/recaptcha/api.js?render=YOUR_SITE_KEY"></script>`

2. **Vérifier les requêtes réseau** : à l’aide des outils de développement du navigateur (F12)
   - Envoyez votre formulaire et recherchez les requêtes réseau à `google.com/recaptcha`
   - Ces requêtes indiquent que reCAPTCHA est actif sur votre formulaire

### Test fonctionnel

Pour vérifier que reCAPTCHA protège réellement votre formulaire :

1. **Test d’envoi normal** :
   - Remplissez votre formulaire avec des données valides
   - Envoyer le formulaire à un rythme humain normal
   - Vérifier les envois de formulaire

2. **Test de comportement de type robot** :
   - Ouvrez votre formulaire dans une fenêtre de navigation privée ou en mode privé
   - Remplissez le formulaire extrêmement rapidement (comportement de type automatisé)
   - Envoyer plusieurs fois de suite rapide
   - Si reCAPTCHA fonctionne, ces envois peuvent être bloqués ou marqués

3. **Vérifier les enregistrements d’envoi de formulaire** :
   - Vérifier les données d’envoi du formulaire
   - Chaque soumission doit inclure un score reCAPTCHA
   - Des scores plus proches de 1,0 indiquent des utilisateurs humains probables
   - Des scores plus proches de 0,0 indiquent une activité de robot potentielle

### Utilisation de la console d’administration Google reCAPTCHA

Pour les utilisateurs Grands comptes, la console cloud Google fournit des analyses détaillées :

1. Accédez à la [console cloud Google](https://console.cloud.google.com/)
2. Accédez à **Sécurité** > **reCAPTCHA**
3. Sélectionner la clé de votre site
4. Examiner les graphiques et les statistiques d&#39;évaluation
5. Recherchez :
   - Modèles de trafic
   - Répartitions de score
   - Activités potentiellement frauduleuses

Pour les utilisateurs reCAPTCHA standard, les statistiques de base sont disponibles dans l’[Admin Console reCAPTCHA](https://www.google.com/recaptcha/admin/).

### Ajustement de votre implémentation

En fonction des résultats de la validation :

- Si des utilisateurs légitimes sont bloqués, envisagez de réduire votre score de seuil
- Si vous recevez toujours du spam, envisagez d&#39;augmenter votre score seuil
- Pour les problèmes persistants, vérifiez votre configuration reCAPTCHA et assurez-vous que toutes les clés sont correctement saisies

N’oubliez pas que reCAPTCHA utilise le machine learning pour améliorer son efficacité au fil du temps et peut donc augmenter à mesure qu’il apprend les modèles de trafic de votre site.

## Résolution des problèmes et FAQ

| ![Question](/help/edge/docs/forms/universal-editor/assets/question.svg) | ![Réponse](/help/edge/docs/forms/universal-editor/assets/answer.svg) |
|:-------------:|:-------------:|
| **Que se passe-t-il si je ne crée pas de configuration reCAPTCHA ?** | Le système recherche une configuration dans le conteneur global. S’il n’en existe aucune, une erreur s’affiche. |
| **Que faire si je crée plusieurs configurations ?** | Le système utilise automatiquement la première configuration créée. |
| **Pourquoi mes modifications ne sont-elles pas visibles sur l’URL publiée ?** | Veillez à republier votre formulaire après avoir apporté des modifications. |
| **Quels services reCAPTCHA sont pris en charge ?** | Edge Delivery Services Forms ne prend en charge que les services reCAPTCHA basés sur les scores. |

## Étapes suivantes

Maintenant que vous avez protégé votre formulaire avec reCAPTCHA :

- **Valider votre implémentation** : suivez les [étapes de validation](#-validating-your-recaptcha-integration) pour vous assurer que reCAPTCHA fonctionne correctement
- **Surveiller les performances** : recherchez régulièrement les activités suspectes et les distributions de scores dans le tableau de bord reCAPTCHA de Google
- **Ajuster les paramètres** : ajustez votre score seuil en fonction de vos besoins en matière de sécurité et des commentaires sur l’expérience utilisateur.
- **Restez à jour** : Maintenez votre implémentation reCAPTCHA à jour avec les dernières recommandations de sécurité de Google
- **Formez votre équipe** : partagez vos connaissances sur le fonctionnement de reCAPTCHA et sur la manière d’interpréter les analyses
- **Collecter des commentaires** : surveillez l’expérience des utilisateurs pour vous assurer que les utilisateurs légitimes ne sont pas bloqués.

N’oubliez pas qu’une protection efficace des formulaires est un processus continu qui nécessite une surveillance et des ajustements réguliers.



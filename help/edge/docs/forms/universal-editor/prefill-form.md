---
title: Préremplissage des champs d’un formulaire adaptatif
description: Utilisez les données existantes pour préremplir les champs d’un formulaire adaptatif. Les utilisateurs et utilisatrices peuvent préremplir les informations de base dans un formulaire en se connectant avec leur profil de réseau social.
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
time: 45-60 minutes
keywords: Préremplir un formulaire adaptatif, formulaires adaptatifs Edge Delivery Services, remplissage automatique de formulaire adaptatif
exl-id: 7b6224e2-a19c-4146-8545-0ce9d1da9b29
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '1787'
ht-degree: 100%

---

# Configuration du service de préremplissage dans les formulaires adaptatifs à l’aide d’Edge Delivery Services

Le préremplissage de formulaire est le processus de remplissage automatique des champs de formulaire avec des données pertinentes provenant de sources externes dès qu’un utilisateur ou une utilisatrice ouvre le formulaire. En utilisant les informations des profils utilisateur et utilisatrices, des bases de données, des brouillons enregistrés ou d’autres systèmes back-end, le préremplissage simplifie l’expérience de remplissage de formulaire, en réduisant les saisies manuelles, en minimisant les erreurs et en accélérant l’opération. Cela améliore non seulement la satisfaction des utilisateurs et utilisatrices, mais augmente également les chances de réussite des envois de formulaires.

## Avantages du préremplissage de formulaire

| Avantage | Description |
|---------|-------------|
| **Opération plus rapide** | Réduit la saisie manuelle des données, aidant ainsi les utilisateurs et utilisatrices à remplir rapidement les formulaires. |
| **Amélioration de l’expérience d’utilisation** | Les formulaires sont plus personnalisés et plus pratiques, en particulier pour les utilisateurs et utilisatrices réguliers. |
| **Taux de conversion plus élevés** | Réduit l’abandon de formulaire en réduisant les efforts des utilisatrices et utilisatrices nécessaires. |
| **Réduction des erreurs de saisie** | Les données provenant de sources approuvées permettent de réduire les fautes de frappe et les saisies incorrectes. |
| **Meilleure qualité des données** | Garantit des données structurées, précises et cohérentes pour les systèmes back-end. |

## Fonctionnement du préremplissage

Le diagramme suivant illustre le processus de préremplissage automatique qui se produit lorsqu’un utilisateur ou une utilisatrice ouvre un formulaire adaptatif :

![Flux du processus de préremplissage de formulaire](/help/edge/docs/forms/universal-editor/assets/prefill-process-flow.svg)

Le processus de préremplissage comprend quatre étapes clés :

1. **L’utilisateur ou l’utilisatrice ouvre un formulaire** : l’utilisateur ou l’utilisatrice accède à un formulaire adaptatif via une URL ou par navigation.
1. **Identifier la source de données** : le service de préremplissage détermine la source de données configurée (modèle de données de formulaire ou service de brouillon).
1. **Récupérer les données** : le système récupère les données utilisateur ou utilisatrice pertinentes en fonction du contexte, des paramètres ou de l’identification de l’utilisateur ou de l’utilisatrice.
1. **Mapper et afficher** : les données sont mappées aux champs du formulaire à l’aide des propriétés `bindRef` et le formulaire renseigné est présenté à l’utilisateur ou l’utilisatrice.

Ce processus automatisé garantit que les utilisateurs et utilisatrices voient un formulaire prérempli avec leurs informations pertinentes, ce qui améliore considérablement l’expérience d’utilisation et les taux de remplissage de formulaire.

## Structure des données pour le préremplissage

Les formulaires adaptatifs prennent en charge deux types de champs :

- **Champs liés** : champs connectés à une source de données avec une propriété `bindRef` non vide.
- **Champs non liés** : champs autonomes avec des valeurs `bindRef` vides.

La structure des données de préremplissage comprend :

- **afBoundData** : contient des données pour les champs liés et les panneaux.
- **afUnBoundData** : contient des données pour les champs non liés.

Le format des données doit correspondre à votre modèle de formulaire :

- **Formulaires XFA** : XML conforme au schéma de modèle XFA.
- **Formulaires de schéma XML** : XML correspondant à la structure du schéma.
- **Formulaires de schéma JSON** : JSON compatible avec le schéma.
- **Formulaires de modèle de données de formulaire (FDM)** : JSON correspondant à la structure du FDM.
- **Formulaires sans schéma** : tous les champs sont non liés et utilisent du XML non lié.

## Prérequis

Avant de configurer les services de préremplissage, vérifiez les points suivants :

### Configuration requise

- [Référentiel GitHub configuré pour Edge Delivery Services](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)
- [Bloc de formulaires adaptatifs ajouté à votre projet](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- [Source de données configurée](/help/forms/configure-data-sources.md)
- [Modèle de données de formulaire créé](/help/forms/create-form-data-models.md)

### Conditions d’accès

- Accéder à l’instance AEM Forms as a Cloud Service
- Autorisations pour créer et modifier des formulaires
- Accès à l’éditeur universel avec activation des extensions requises

>[!TIP]
>
> Vous pouvez également modifier des formulaires pour intégrer le modèle de données de formulaire (FDM) dans l’éditeur universel afin de récupérer des données de diverses sources principales. Pour plus d’informations, reportez-vous à l’article [Intégration de formulaires à un modèle de données de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

## Options du service de préremplissage

L’éditeur universel fournit deux options de service de préremplissage :

| Type de service | Objectif | Source de données | Idéale pour |
|--------------|---------|-------------|----------|
| **Service de préremplissage de version préliminaire du portail Formulaires** | Reprend les formulaires partiellement remplis | Brouillons enregistrés sur le portail Formulaires | Demandes incomplètes en cours |
| **Service de préremplissage de modèle de données de formulaire** | Remplit les champs de systèmes externes | Bases de données principales via FDM | Le stockage des données du profil utilisateur |

### Comparaison détaillée

| Fonctionnalité | Service de préremplissage de brouillon | Sélectionner le service de préremplissage FDM |
|---------|----------------------|---------------------|
| **Authentication** | Nécessite une connexion utilisateur pour l’accès au brouillon | Paramétrable en fonction de la source de données |
| **Complexité de la configuration** | Configuration minimale | Nécessite une configuration et un mappage FDM |
| **Type de données** | Données statiques enregistrées | Données dynamiques en temps réel |
| **Cas d’utilisation** | Reprise des applications enregistrées | Préremplissage à partir de profils utilisateur ou de bases de données |


## Configurer un service de préremplissage pour un formulaire

+++Phase 1 : configuration du modèle de données de formulaire

### Étape 1 : créer un modèle de données de formulaire

1. Connectez-vous à votre instance AEM Forms as a Cloud Service.
1. Accédez à **Adobe Experience Manager** > **Formulaires** > **Intégration de données**
1. Sélectionnez **Créer** > **Modèle de données de formulaire**
1. Choisissez votre **Configuration de Source de données** et sélectionnez la **Source de données** configurée

   ![Modèle de données de formulaire créé](/help/edge/docs/forms/universal-editor/assets/create-fdm.png)

   >[!TIP]
   >
   >Pour obtenir des instructions détaillées sur la création de modèles de données de formulaire, consultez la section [Créer un modèle de données de formulaire](/help/forms/create-form-data-models.md).

### Étape 2 : configuration des services FDM

1. Accédez à **Adobe Experience Manager** > **Formulaires** > **Intégrations de données**
1. Ouvrez le modèle de données de formulaire en mode d’édition
1. Sélectionnez un objet de modèle de données et cliquez sur **Modifier les propriétés**
1. Configurer les services **Lire** et **Écrire** pour les objets du modèle de données sélectionnés

   ![Configuration du service de lecture/écriture](/help/edge/docs/forms/universal-editor/assets/configure-reda-write-service.png)

1. Configuration des arguments du service

   - Cliquez sur l’icône de modification de l’argument de service de lecture.
   - Liez l’argument à un **attribut du profil utilisateur**, un **attribut de requête** ou une **valeur littérale**.
   - Spécifiez la valeur de liaison (par exemple, `petid` pour un formulaire d’enregistrement d’un animal de compagnie).

   ![Configurer l’argument d’identifiant de l’animal de compagnie](/help/edge/docs/forms/universal-editor/assets/pet-id-arguments.png)

1. Cliquez sur **Terminé** pour enregistrer l’argument et sur **Enregistrer** pour enregistrer le FDM.

   >[!NOTE]
   >
   > En savoir plus sur la configuration des services FDM dans [Utilisation d’un modèle de données de formulaire (FDM)](/help/forms/work-with-form-data-model.md).

+++

+++Phase 2 : création et configuration du formulaire adaptatif

### Étape 3 : création d’un formulaire adaptatif

1. Accédez à **Adobe Experience Manager** > **Formulaires** > **Formulaires et documents**.
1. Sélectionnez **Créer** > **Formulaires adaptatifs**.
1. Dans l’onglet **Source**, sélectionnez un modèle basé sur Edge Delivery Services :

   ![Modèle Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

1. Cliquez sur **Créer** pour ouvrir l’assistant **Créer un formulaire**.
1. Spécifiez les détails du formulaire :

   - **Nom** : saisissez un nom explicite pour votre formulaire
   - **Titre** : fournissez un titre convivial
   - **URL GitHub** : saisissez l’URL de votre référentiel (par exemple, `https://github.com/wkndforms/edsforms`).

1. Cliquer sur **Créer**

   ![Créer un formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form1.png)

Le formulaire s’ouvre dans l’éditeur universel pour la création.

### Étape 4 : configurer le modèle de données de formulaire

1. Sélectionnez un formulaire, puis cliquez sur **Propriétés**.

   ![Sélectionner les propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-properties1.png)

2. Ouvrez l’onglet **Modèle de formulaire**.
3. Dans la liste déroulante **Sélectionner à partir de**, choisissez **Modèle de données de formulaire (FDM)**.
4. Sélectionnez dans la liste déroulante le modèle de données de formulaire (par exemple, PetFDM) que vous avez créé.

   ![Sélection de l’onglet Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-model1.png)

5. Cliquer sur **Enregistrer et fermer**
6. Ouvrez le formulaire pour le modifier dans l’éditeur universel.

Les éléments de formulaire de votre FDM apparaissent dans l’onglet **Source de données** de l’**Explorateur de contenu**.

### Étape 5 : ajouter une liaison de données aux champs de formulaire

1. Sélectionnez des éléments de données dans l’onglet **Source de données**.
2. Cliquez sur **Ajouter** ou faites glisser et déposez des éléments pour créer votre formulaire.

   ![Copie d’écran de l’éditeur universel affichant le formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/ue-form.png)

3. Ajoutez la liaison de données aux champs de formulaire :

   - Sélectionnez un champ de formulaire.
   - Dans le panneau **Propriétés**, recherchez la propriété **Référence de liaison**.
   - Sélectionnez la référence de liaison de données appropriée.

     ![Liaison de données](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding1.png)

+++

+++Phase 3 : configuration du service de préremplissage

### Étape 6 : activer les extensions requises

Assurez-vous que ces extensions sont activées dans l’éditeur universel :

1. **Extension des propriétés de formulaire AEM**

   - Ouvrez **Extension Manager** dans l’éditeur universel.
   - Activez l’extension **Propriétés de formulaire AEM**

   ![Icône Propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/form-edit-properties.png)

1. **Extension de source de données**

   - Activez l’extension **Source de données** si vous ne voyez pas l’icône **Sources de données**.

   ![Capture d’écran d’Extension Manager de l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

   >[!TIP]
   >
   > Pour obtenir des instructions détaillées sur la gestion des extensions, consultez [Principales fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

### Étape 7 : configurer le service de préremplissage

1. Ouvrez votre formulaire adaptatif dans l’éditeur universel.
2. Cliquez sur l’icône d’extension **Propriétés du formulaire AEM**.

   ![Sélection de l’icône Propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/select-fdm-properties-icon.png)

3. Cliquez sur l’onglet **Préremplissage**.
4. Sélectionnez **Service de préremplissage de modèle de données de formulaire**.

   ![Sélection du service de préremplissage](/help/edge/docs/forms/universal-editor/assets/select-fdm-prefill.png)

5. Cliquez sur **Enregistrer et fermer**.

+++

+++Phase 4 : test de votre configuration de préremplissage

### Étape 8 : prévisualisation et test

1. Accédez à **Formulaires** > **Formulaires et documents**.
2. Sélectionnez votre formulaire adaptatif.
3. Choisissez **Prévisualiser au format HTML**.
4. Testez le préremplissage en ajoutant des paramètres à l’URL :

   https://your-preview-url.com?`<bindreferencefield>`=`<value>`

   **Exemple :**

   https://your-preview-url.com?petid=12345

   ![Préremplissage d’un formulaire](/help/edge/docs/forms/universal-editor/assets/prefill-form.png)

Le formulaire doit être automatiquement renseigné avec des données en fonction du paramètre fourni.

+++

## Exemples

### Exemples de structures de données de préremplissage

**Exemple JSON pour un formulaire basé sur FDM :**

```
  {
    "afBoundData": {
      "user": {
        "firstName": "John",
        "lastName": "Doe",
        "email": "john.doe@example.com",
        "phone": "+1-555-0123"
      }
    },
    "afUnBoundData": {
      "additionalInfo": "User preferences loaded"
    }
  }
```

**Exemple XML pour un formulaire basé sur XFA :**

```
  <?xml version="1.0" encoding="UTF-8"?>
  <afData>
    <afBoundData>
      <user>
        <firstName>John</firstName>
        <lastName>Doe</lastName>
        <email>john.doe@example.com</email>
      </user>
    </afBoundData>
  </afData>
```

### Exemples d’URL de préremplissage

Les URL ci-dessous sont fournies à titre d’illustration uniquement et ne fonctionneront pas en l’état. Remplacez l’hôte et les paramètres par ceux relatifs à votre propre environnement lors du test de la fonctionnalité de préremplissage.

**Test de préremplissage de base :**

`https://preview.example.com/form.html?userId=12345`

**Test de paramètres multiples :**

`https://preview.example.com/form.html?userId=12345&category=premium`


## Résolution des problèmes

+++Problèmes courants et solutions

| Problème | Cause possible | Solution |
|-------|----------------|----------|
| **Les champs de formulaire ne sont pas préremplis** | Valeurs `bindRef` incorrectes | Vérifier que `bindRef` correspond exactement aux noms de champs FDM |
| **Erreurs de format des données** | Structure des données incohérente | Vérifier que les données de préremplissage correspondent au schéma du modèle de formulaire |
| **Service introuvable** | Problèmes de configuration de FDM | Vérifier que les services FDM sont correctement configurés et enregistrés |
| **Erreurs d’authentification** | Connectivité de la source de données | Vérifier les informations d’identification et la connectivité de la source de données |
| **Chargement partiel des données** | Mappages de champs manquants | Assurez-vous que tous les champs obligatoires possèdent les liaisons de données appropriées. |

+++

+++Étapes de débogage

1. **Vérifier la configuration FDM :**

   - Vérifier si les services sont correctement configurés.
   - Tester les services FDM indépendamment
   - Valider la connectivité de la source de données

2. **Vérifier la configuration du formulaire :**

   - S’assurer que le formulaire est associé au FDM correct.
   - Vérifiez les valeurs `bindRef` des champs.
   - Testez le formulaire sans préremplissage dans un premier temps.

3. **Testez le flux de données :**

   - Utilisez les outils de développement du navigateur pour examiner les requêtes du réseau.
   - Recherchez les erreurs JavaScript dans la console.
   - Validez le format des données de réponse.

4. **Messages d’erreur courants :**

   - « Service de préremplissage introuvable » : vérifiez la configuration du service.
   - « Échec de la liaison de données » : vérifiez l’exactitude des valeurs `bindRef`.
   - « Format de données non valide » : assurez-vous que les données correspondent au schéma.

+++

## Bonnes pratiques

+++Bonnes pratiques de configuration

- **Utiliser des noms descriptifs** : nommez clairement vos FDM et services.
- **Valider les schémas de données** : assurez-vous que la structure des données correspond aux exigences du formulaire.
- **Test incrémentiel** : configurez et testez un champ à la fois.
- **Mappages de documents** : suivez les mappages champ-données.

+++

+++Optimisation des performances

- **Réduire le volume des données** : préremplissez uniquement les champs nécessaires.
- **Utiliser la mise en cache** : configurez une mise en cache appropriée pour les données fréquemment consultées.
- **Optimiser les requêtes** : assurez-vous que les requêtes de base de données sont efficaces.
- **Surveiller les performances** : suivez les temps de chargement des formulaires avec le préremplissage activé.

+++

+++Considérations relatives à la sécurité

- **Valider les paramètres d’entrée** : validez toujours les paramètres d’URL.
- **Assainir les données** : nettoyez les données avant de préremplir les formulaires.
- **Implémenter des contrôles d’accès** : assurez-vous que les utilisateurs et utilisatrices peuvent uniquement accéder à leurs propres données.
- **Utiliser HTTPS** : utilisez toujours des connexions sécurisées pour la transmission de données.

+++

+++Conseils pour l’expérience d’utilisation

- **Envoyer des commentaires** : affichez les indicateurs de chargement lors de la récupération des données.
- **Gérer les erreurs avec élégance** : affichez des messages d’erreur utiles.
- **Autoriser les remplacements** : permettez aux utilisateurs et utilisatrices de modifier les données préremplies.
- **Maintenir la cohérence** : adoptez un comportement de préremplissage cohérent dans les formulaires.

+++

## Questions fréquentes

+++Comment vérifier si le préremplissage fonctionne correctement ?

Prévisualisez votre formulaire et ajoutez des paramètres de préremplissage à l’URL à l’aide du format suivant : `?<bindreferencefield>=<value>`. Assurez-vous que le champ comporte une valeur `bindRef` valide correspondant à votre structure de données. Utilisez les outils de développement du navigateur pour inspecter les requêtes réseau et vérifier que les données sont récupérées correctement.

+++

+++Quels formats de données sont pris en charge pour le préremplissage des formulaires adaptatifs ?

Les formulaires adaptatifs prennent en charge plusieurs formats en fonction de votre modèle de formulaire :

- **Formulaires XFA** : XML correspondant au schéma XFA.
- **Formulaires de schéma JSON** : données JSON conformes au schéma.
- **Formulaires FDM** : JSON qui mappe la structure du modèle de données.
- **Formulaires de schéma XML** : XML correspondant à la structure du schéma.

+++

+++Puis-je préremplir des champs liés et non liés ?

Oui, vous pouvez préremplir les deux types de champs. Les champs liés utilisent la section `afBoundData` et doivent correspondre à votre schéma de modèle de formulaire. Les champs non liés utilisent la section `afUnBoundData` et peuvent contenir toutes les données supplémentaires.

+++

+++Que dois-je faire si seuls certains champs sont préremplis ?

Vérifiez que tous les champs ont des valeurs `bindRef` correctes qui correspondent exactement à votre FDM. Vérifiez que votre source de données contient tous les champs obligatoires et que la structure des données correspond à votre schéma de modèle de formulaire.

+++

+++Puis-je utiliser plusieurs services de préremplissage dans un seul formulaire ?

Vous pouvez configurer un service de préremplissage principal par formulaire. Cependant, vous pouvez combiner différentes sources de données dans un seul modèle de données de formulaire pour obtenir des fonctionnalités similaires.

+++

+++Comment gérer l’authentification pour les services de préremplissage ?

L’authentification dépend de la configuration de votre source de données. Pour le préremplissage basé sur FDM, configurez l’authentification dans les paramètres de votre source de données. Pour le préremplissage des brouillons, les utilisateurs et utilisatrices doivent généralement se connecter pour accéder aux brouillons enregistrés.

+++



## Rubriques connexes

- [Intégrer des formulaires à un modèle de données de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)
- [Créer des modèles de données de formulaire](/help/forms/create-form-data-models.md)
- [Utiliser le modèle de données de formulaire (FDM)](/help/forms/work-with-form-data-model.md)
- [Configurer des sources de données](/help/forms/configure-data-sources.md)
- [Prise en main d’Edge Delivery Services pour AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)

---
title: Comment préremplir des champs de formulaire adaptatif ?
description: Utilisez des données existantes pour préremplir les champs d’un formulaire adaptatif. Les utilisateurs peuvent préremplir les informations de base dans un formulaire en se connectant avec leurs profils sociaux.
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
time: 45-60 minutes
keywords: préremplissage du formulaire adaptatif, services de diffusion edge des formulaires adaptatifs, remplissage automatique des formulaires adaptatifs
source-git-commit: 87650caea6eb907093f0f327f1dbc19641098e4a
workflow-type: tm+mt
source-wordcount: '1874'
ht-degree: 3%

---


# Configuration du service de préremplissage dans le Forms adaptatif à l’aide de Edge Delivery Services

Le préremplissage du formulaire est le processus de remplissage automatique des champs de formulaire avec des données pertinentes provenant de sources externes dès qu’un utilisateur ouvre le formulaire. En exploitant les informations des profils utilisateur, des bases de données, des brouillons enregistrés ou d’autres systèmes principaux, le préremplissage simplifie le remplissage des formulaires, en réduisant les saisies manuelles, en réduisant les erreurs et en accélérant la saisie. Cela améliore non seulement la satisfaction des utilisateurs et utilisatrices, mais augmente également les chances de réussite des envois de formulaire.

## Avantages du préremplissage de formulaire

| Bénéfice | Description |
|---------|-------------|
| **Accomplissement plus rapide** | Réduit la saisie manuelle des données, aidant ainsi les utilisateurs à remplir rapidement les formulaires |
| **Expérience utilisateur améliorée** | Forms est plus personnalisé et plus pratique, en particulier pour les utilisateurs réguliers |
| **Taux de conversion plus élevés** | Réduit l’abandon de formulaire en réduisant l’effort utilisateur requis |
| **Réduction des erreurs d’entrée** | Les données provenant de sources approuvées réduisent les fautes de frappe et les entrées incorrectes |
| **Meilleure qualité des données** | Garantit des données structurées, précises et cohérentes pour les systèmes principaux |

## Fonctionnement du préremplissage

Le diagramme suivant illustre le processus de préremplissage automatique qui se produit lorsqu’un utilisateur ouvre un formulaire adaptatif :

![Flux de processus de préremplissage de formulaire](/help/edge/docs/forms/universal-editor/assets/prefill-process-flow.svg)

Le processus de préremplissage comprend quatre étapes clés :

1. **L’utilisateur ouvre un formulaire** : l’utilisateur accède à un formulaire adaptatif par une URL ou une navigation
2. **Identifier le Source de données** : le service de préremplissage détermine la source de données configurée (modèle de données de formulaire ou service de brouillon)
3. **Récupérer les données** : le système récupère les données utilisateur pertinentes en fonction du contexte, des paramètres ou de l’identification de l’utilisateur
4. **Mapper et afficher** : les données sont mappées aux champs du formulaire à l’aide des propriétés `bindRef` et le formulaire renseigné est affiché pour l’utilisateur ou l’utilisatrice

Ce processus automatisé garantit que les utilisateurs voient un formulaire prérempli avec leurs informations pertinentes, ce qui améliore considérablement l’expérience utilisateur et les taux de remplissage du formulaire.

## Structure des données pour le préremplissage

Le Forms adaptatif prend en charge deux types de champs :

- **Champs liés** : champs connectés à une source de données avec une propriété `bindRef` non vide
- **Champs non liés** : champs autonomes avec des valeurs de `bindRef` vides

La structure de données de préremplissage comprend :

- **afBoundData** : contient des données pour les champs liés et les panneaux
- **afUnBoundData** : contient des données pour les champs non liés

Le format des données doit correspondre à votre modèle de formulaire :

- **Formulaires XFA** : XML conforme au schéma de modèle XFA
- **Formulaires de schéma XML** : XML correspondant à la structure du schéma
- **Formulaires de schéma JSON** : compatible JSON avec le schéma
- **Formulaires de modèle de données de formulaire (FDM)** : JSON correspondant à la structure FDM
- **Formulaires sans schéma** : tous les champs sont non liés et utilisent du code XML non lié


## Prérequis

Avant de configurer les services de préremplissage, vérifiez que vous disposez des éléments suivants :

### Configuration requise

- [Référentiel GitHub configuré pour Edge Delivery Services](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)
- [Bloc de Forms adaptatif ajouté à votre projet](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- [Source de données configurée](/help/forms/configure-data-sources.md)
- [Modèle de données de formulaire (FDM) créé](/help/forms/create-form-data-models.md)

### Conditions d’accès

- Accès à AEM Forms as a Cloud Service
- Autorisations pour créer et modifier des formulaires
- Accès à l’éditeur universel avec activation des extensions requises

>[!TIP]
>
> Vous pouvez également modifier des formulaires pour intégrer le modèle de données de formulaire (FDM) dans l’éditeur universel afin de récupérer des données de diverses sources principales. Pour plus d’informations, reportez-vous à l’article [Intégration de formulaires à un modèle de données de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

## Options du service de préremplissage

L’éditeur universel fournit deux options de service de préremplissage :

| Type de service | Objectif | Source de données | Idéal pour |
|--------------|---------|-------------|----------|
| **Préremplissage du brouillon du portail Formulaires** | Reprend les formulaires partiellement remplis | Brouillons enregistrés sur le portail Forms | Demandes incomplètes en cours |
| **Préremplissage Du Modèle De Données De Formulaire** | Remplit les champs de systèmes externes | Bases de données principales via FDM | Remplissage automatique des données de profil utilisateur |

### Comparaison détaillée

| Fonctionnalité | Service de préremplissage de brouillon | Service de préremplissage FDM |
|---------|----------------------|---------------------|
| **Authentification** | Nécessite une connexion utilisateur pour l’accès au brouillon | Paramétrable en fonction de la source de données |
| **Complexité de la configuration** | Configuration minimale | Nécessite une configuration et un mappage FDM |
| **Type de données** | Données statiques enregistrées | Données dynamiques en temps réel |
| **Cas d’utilisation** | Reprise des applications enregistrées | Préremplissage à partir de profils utilisateur ou de bases de données |


## Configuration du service de préremplissage d’un formulaire


+++Phase 1 : Configuration Du Modèle De Données De Formulaire

### Étape 1 : création d’un modèle de données de formulaire

1. Connectez-vous à votre instance AEM Forms as a Cloud Service
2. Accédez à **Adobe Experience Manager** > **Forms** > **Intégrations de données**
3. Sélectionnez **Créer** > **Modèle de données de formulaire**
4. Choisissez votre **Configuration de Source de données** et sélectionnez la **Source de données** configurée

   ![Modèle de données de formulaire créé](/help/edge/docs/forms/universal-editor/assets/create-fdm.png)

   >[!TIP]
   >
   > Pour obtenir des instructions détaillées sur la création de modèles de données de formulaire, voir [Créer un modèle de données de formulaire](/help/forms/create-form-data-models.md).

### Étape 2 : configuration des services FDM

1. Accédez à **Adobe Experience Manager** > **Forms** > **Intégrations de données**
2. Ouvrez votre modèle de données de formulaire en mode d’édition
3. Sélectionnez un objet de modèle de données et cliquez sur **Modifier les propriétés**
4. Configurez les services **Lecture** et **Écriture** pour les objets de modèle de données sélectionnés

   ![Configuration du service de lecture/écriture](/help/edge/docs/forms/universal-editor/assets/configure-reda-write-service.png)

5. Configurez les arguments de service :
   - Cliquez sur l’icône de modification de l’argument de service de lecture
   - Liez l’argument à une **Attribut du profil utilisateur**, **Attribut de requête** ou **Valeur littérale**
   - Spécifiez la valeur de liaison (par exemple, `petid` pour un formulaire d&#39;enregistrement d&#39;animal de compagnie)

   ![Configurer l’argument d’identifiant animal de compagnie](/help/edge/docs/forms/universal-editor/assets/pet-id-arguments.png)

6. Cliquez sur **Terminé** pour enregistrer l’argument et sur **Enregistrer** pour enregistrer le FDM

       >[!REMARQUE]
       >
   > En savoir plus sur la configuration des services FDM dans [Utilisation d’un modèle de données de formulaire (FDM)](/help/forms/work-with-form-data-model.md).

+++

+++Phase 2 : création et configuration du formulaire adaptatif

### Étape 3 : créer un formulaire adaptatif

1. Accédez à **Adobe Experience Manager** > **Forms** > **Forms et documents**
2. Sélectionnez **Créer** > **Forms adaptatif**
3. Dans l&#39;onglet **Source**, sélectionnez un modèle Edge Delivery Services :

       .[modèle Edge Delivery Services](/help/edge/assets/create-eds-forms.png)
   
4. Cliquez sur **Créer** pour ouvrir l’assistant **Créer un formulaire**
5. Spécifiez les détails du formulaire :
   - **Nom** : saisissez un nom explicite pour votre formulaire
   - **Titre** : fournissez un titre convivial.
   - **URL GitHub** : saisissez l’URL de votre référentiel (par exemple, `https://github.com/wkndforms/edsforms`).

6. Cliquez sur **Créer**.

       .[Créer un formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form1.png)
   
Le formulaire s’ouvre dans l’éditeur universel pour la création.

### Étape 4 : Configurer le Source de données de formulaire

1. Sélectionnez votre formulaire et cliquez sur **Propriétés**

       .[Sélectionner les propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-properties1.png)
   
2. Ouvrez l’onglet **Modèle de formulaire**
3. Dans la liste déroulante **Sélectionner à partir de**, choisissez **Modèle de données de formulaire (FDM)**
4. Sélectionnez le modèle de données de formulaire (par exemple, PetFDM) créé dans la liste déroulante

       .[Sélectionnez l’onglet Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-model1.png)
   
5. Cliquez sur **Enregistrer et fermer**.
6. Ouvrez le formulaire pour le modifier dans l’éditeur universel.

Les éléments de formulaire de votre FDM apparaissent dans l’onglet **Source de données** de l’**Explorateur de contenu**.

### Étape 5 : ajouter une liaison de données aux champs de formulaire

1. Sélectionnez des éléments de données dans l’onglet **Source de données**
2. Cliquez sur **Ajouter** ou faites glisser et déposez des éléments pour créer votre formulaire

   ![Capture d’écran de l’éditeur universel affichant le formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/ue-form.png)

3. Ajoutez la liaison de données aux champs de formulaire :
   - Sélectionner un champ de formulaire
   - Dans le panneau **Propriétés**, recherchez la propriété **Référence de liaison**
   - Sélectionner la référence de liaison de données appropriée

     ![Liaison de données](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding1.png)

+++

+++Phase 3 : configuration du service de préremplissage

### Étape 6 : Activer les extensions requises

Assurez-vous que ces extensions sont activées dans l’éditeur universel :

1. **Extension Des Propriétés D’AEM Form**
   - Ouvrez **Extension Manager** dans l’éditeur universel
   - Activez l’extension **Propriétés de formulaire AEM**

   ![Icône Propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/form-edit-properties.png)

2. **Extension Data Source**
   - Activez l’extension **Data source** si vous ne voyez pas l’icône **Data Sources**

   ![Capture d’écran de l’éditeur universel Extension Manager](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

   >[!TIP]
   >
   > Pour obtenir des instructions détaillées sur la gestion des extensions, consultez [Caractéristiques des fonctionnalités Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

### Étape 7 : Configuration du service de préremplissage

1. Ouvrez votre formulaire adaptatif dans l’éditeur universel
2. Cliquez sur l’icône d’extension **Propriétés d’AEM Form**

   ![Icône Sélectionner les propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/select-fdm-properties-icon.png)

3. Cliquez sur l’onglet **Préremplissage**
4. Sélectionnez **Service de préremplissage du modèle de données de formulaire**

       .[Sélectionnez le service de préremplissage](/help/edge/docs/forms/universal-editor/assets/select-fdm-prefill.png)
   
5. Cliquez sur **Enregistrer et fermer**.

+++

+++Phase 4 : Test De La Configuration De Préremplissage

### Étape 8 : prévisualisation et test

1. Accédez à **Forms** > **Forms et documents**
2. Sélection d’un formulaire adaptatif
3. Choisissez **Aperçu sous HTML**
4. Testez le préremplissage en ajoutant des paramètres à l’URL :

       https://your-preview-url.com?&lt;bindreferencefield>=&lt;value>
   
   **Exemple :**

       https://your-preview-url.com?petid=12345
       
        ![Formulaire de préremplissage](/help/edge/docs/forms/universal-editor/assets/prefill-form.png)
   
Le formulaire doit être automatiquement rempli avec des données en fonction du paramètre fourni.

+++

## Exemples

### Exemples de structures de données de préremplissage

**Exemple JSON pour un formulaire basé sur FDM :**

     »
    
    {
    « afBoundData »: {
    « user »: {
    « firstName »: « John »,
    « lastName »: « Doe »,
    « email »: « john.doe@example.com »,
    « phone »: « +1-555-0123 »
    }
    },
    « afUnBoundData »: {
    « additionalInfo »: « Préférences utilisateur chargées »
    }
    }
    
     »

**Exemple XML pour un formulaire XFA :**

     »
    
    &lt;?xml version=« 1.0 » encoding=« UTF-8 »?>
    &lt;afData>
    &lt;afBoundData>
    &lt;user>
    &lt;firstName>John&lt;/firstName>
    &lt;lastName>Doe&lt;/lastName>
    &lt;email>john.doe@example.com&lt;/email>
    &lt;/user>
    &lt;/afBoundData>
    &lt;/afData>
    
     »

### Exemples d’URL de préremplissage

Les URL ci-dessous sont fournies à titre d’illustration uniquement et ne fonctionneront pas en l’état. Remplacez l’hôte et les paramètres par ceux relatifs à votre propre environnement lors du test de la fonctionnalité de préremplissage.

**Test de préremplissage de base :**

    https://preview.example.com/form.html?userId=12345

**Test de paramètres multiples:**

    https://preview.example.com/form.html?userId=12345&amp;category=premium


## Résolution des problèmes

+++Problèmes courants et solutions

| Problème | Cause possible | Solution |
|-------|----------------|----------|
| **Les champs de formulaire ne sont pas préremplis** | Valeurs de `bindRef` incorrectes | Vérifier `bindRef` correspond exactement aux noms des champs FDM |
| **Erreurs de format des données** | Structure de données incohérente | Vérifier que les données de préremplissage correspondent au schéma du modèle de formulaire |
| **Service introuvable** | Problèmes de configuration FDM | Vérifiez que les services FDM sont correctement configurés et enregistrés. |
| **Erreurs d’authentification** | Connectivité des sources de données | Vérification des informations d’identification et de la connectivité de la source de données |
| **Chargement partiel** | Mappages de champs manquants | Assurez-vous que tous les champs obligatoires possèdent les liaisons de données appropriées |

+++

+++Étapes de débogage

1. **Vérifier la configuration FDM :**
   - Vérifier si les services sont correctement configurés
   - Tester les services FDM indépendamment
   - Valider la connectivité de la source de données

2. **Vérifier la configuration du formulaire :**
   - Confirmer que le formulaire est associé au FDM correct
   - Vérifier les valeurs de `bindRef` des champs
   - Tester le formulaire sans préremplissage

3. **Tester le flux de données :**
   - Utilisation des outils de développement du navigateur pour inspecter les requêtes réseau
   - Rechercher les erreurs JavaScript dans la console
   - Valider le format des données de réponse

4. **Messages d’erreur courants :**
   - « Service de préremplissage introuvable » : vérifiez la configuration du service.
   - « Échec de la liaison de données » : vérifiez `bindRef` précision
   - « Format de données non valide » : assurez-vous que les données correspondent au schéma

+++

## Bonnes pratiques

+++Bonnes pratiques de configuration

- **Utiliser des noms descriptifs** : nommez clairement vos FDM et services
- **Validation des schémas de données** : assurez-vous que la structure des données correspond aux exigences du formulaire
- **Test incrémentiel** : configuration et test d’un champ à la fois
- **Mappages de documents** : suivez les mappages champ-données

+++

+++Optimisation des performances

- **Réduire le volume des données** : préremplissez uniquement les champs nécessaires
- **Utiliser la mise en cache** : configurez une mise en cache appropriée pour les données fréquemment consultées
- **Optimiser les requêtes** : assurez-vous que les requêtes de base de données sont efficaces
- **Surveillance des performances** : suivez les temps de chargement des formulaires avec le préremplissage activé

+++

+++Considérations de sécurité

- **Valider les paramètres d’entrée** : toujours valider les paramètres d’URL
- **Assainir les données** : nettoyer les données avant de préremplir les formulaires
- **Implémenter des contrôles d’accès** : assurez-vous que les utilisateurs peuvent uniquement accéder à leurs propres données
- **Utiliser HTTPS** : utilisez toujours des connexions sécurisées pour la transmission de données

+++

+++Consignes relatives à l’expérience utilisateur

- **Provide feedback** : afficher les indicateurs de chargement lors de la récupération des données
- **Gérer les erreurs de manière élégante** : afficher des messages d’erreur utiles
- **Autoriser les remplacements** : permet aux utilisateurs de modifier les données préremplies.
- **Maintenir la cohérence** : utilisez un comportement de préremplissage cohérent dans les formulaires

+++

## Questions fréquentes

+++Comment vérifier si le préremplissage fonctionne correctement ?

Prévisualisez votre formulaire et ajoutez des paramètres de préremplissage à l’URL à l’aide du format suivant : `?<bindreferencefield>=<value>`. Assurez-vous que le champ comporte un `bindRef` valide correspondant à votre structure de données. Utilisez les outils de développement du navigateur pour inspecter les requêtes réseau et vérifier que les données sont récupérées correctement.

+++

+++Quels formats de données sont pris en charge pour le préremplissage du Forms adaptatif ?

Le Forms adaptatif prend en charge plusieurs formats en fonction de votre modèle de formulaire :

- **Formulaires XFA** : XML correspondant au schéma XFA
- **Formulaires de schéma JSON** : données JSON conformes au schéma
- **Formulaires FDM** : JSON qui mappe la structure du modèle de données
- **Formulaires de schéma XML** : XML correspondant à la structure du schéma

+++

+++Puis-je préremplir des champs liés et non liés ?

Oui, vous pouvez préremplir les deux types de champs. Les champs liés utilisent la section `afBoundData` et doivent correspondre à votre schéma de modèle de formulaire. Les champs non liés utilisent la section `afUnBoundData` et peuvent contenir toutes les données supplémentaires.

+++

+++Que dois-je faire si seuls certains champs sont préremplis ?

Vérifiez que tous les champs ont des valeurs de `bindRef` correctes qui correspondent exactement à votre FDM. Vérifiez que votre source de données contient tous les champs obligatoires et que la structure des données correspond à votre schéma de modèle de formulaire.

+++

+++Comment gérer l’authentification pour les services de préremplissage ?

L’authentification dépend de la configuration de votre source de données. Pour le préremplissage basé sur FDM, configurez l’authentification dans les paramètres de votre source de données. Pour le préremplissage des brouillons, les utilisateurs doivent généralement être connectés pour accéder aux brouillons enregistrés.

+++

+++Puis-je utiliser plusieurs services de préremplissage dans un seul formulaire ?

Vous pouvez configurer un service de préremplissage principal par formulaire. Cependant, vous pouvez combiner différentes sources de données dans un seul modèle de données de formulaire pour obtenir des fonctionnalités similaires.

+++

=
## Rubriques connexes

- [Intégrer des formulaires à un modèle de données de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)
- [Créer des modèles de données de formulaire](/help/forms/create-form-data-models.md)
- [Utiliser le modèle de données de formulaire (FDM)](/help/forms/work-with-form-data-model.md)
- [Configurer les sources de données](/help/forms/configure-data-sources.md)
- [Prise en main de Edge Delivery Services pour AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)

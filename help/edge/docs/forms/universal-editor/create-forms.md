---
title: Création et publication de Forms adaptatif avec Edge Delivery Services
description: Cette section contient des instructions détaillées sur la création et la publication de Forms adaptatif à l’aide des modèles de composant principal ou de Edge Delivery Services dans AEM, avec un accent mis sur la précision et la clarté techniques.
keywords: formulaires adaptatifs, services de diffusion edge, composants principaux, éditeur universel, création de formulaires, AEM forms, sélection de modèles, publication de formulaires
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '1774'
ht-degree: 5%

---


# Création et publication de Forms adaptatif avec Edge Delivery Services

Ce document fournit des instructions pour la création, la configuration et la publication d’un Forms adaptatif dans AEM à l’aide de Edge Delivery Services. Il couvre les modèles Composant principal et Edge Delivery Services.

À la fin de ce guide, vous apprendrez à :

- Sélectionnez le type de modèle approprié à votre cas d’utilisation
- Création de formulaires à l’aide de composants principaux ou de modèles Edge Delivery Services
- Créer des formulaires à l’aide de l’éditeur approprié
- Configuration et publication de formulaires dans Edge Delivery Services
- Accéder aux formulaires publiés et vérifier le déploiement

## Sélection du modèle

Avant de commencer, déterminez quel type de modèle correspond à vos besoins :

| Critères | Modèle de composants principaux | Modèle Edge Delivery Services |
|-------------------------|-----------------------------------------|-------------------------------------|
| Idéal pour | Workflows d’entreprise, intégrations complexes | Formulaires publics hautes performances |
| Éditeur | Éditeur de formulaires adaptatifs | Éditeur universel |
| Publication | Publication AEM + Edge Delivery Services | Edge Delivery Services uniquement |
| Complexité | Fonctionnalités de formulaire avancées | Formulaires rationalisés et rapides |
| Intégration | Écosystème AEM complet | Développement basé sur Git |
| Courbe d&#39;apprentissage | Familier avec les utilisateurs d’AEM | Approche moderne et simplifiée |

**Guide de décision :**

![Décision de sélection de modèle](/help/edge/docs/forms/universal-editor/assets/template-selection-decision.svg)

- Utilisez les **composants principaux** pour les workflows complexes, l’intégration approfondie d’AEM ou l’utilisation de ressources AEM existantes.
- Utilisez **Edge Delivery Services** pour les performances, la simplicité et les pratiques de développement modernes.


*Organigramme de décision permettant de choisir le type de modèle approprié*

## Prérequis

Assurez-vous que les conditions préalables suivantes sont remplies avant de continuer :

### Exigences techniques

- **AEM Forms as a Cloud Service** : instance de création active disposant d’une licence Forms.
- **Compte GitHub** : compte personnel ou organisationnel pour la gestion du référentiel.
- **Configuration du référentiel** : sélectionnez l’une des options suivantes :
   - **Nouveau projet** : [créez un projet AEM avec le bloc de Forms adaptatif](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). Le référentiel est préconfiguré pour Edge Delivery Services.
   - **Projet existant** : [Ajoutez un bloc Forms adaptatif à un référentiel existant](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) et mettez à jour la configuration.

### Configuration de l’environnement

- **Connexion AEM-GitHub** : [établissez une connexion](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) entre votre instance AEM et le référentiel GitHub.
- **Edge Delivery Services** : assurez-vous que le référentiel est configuré pour un déploiement automatique.
- **Autorisations** : vérifiez que vous disposez des droits d’accès nécessaires pour la création et la publication de formulaires.

### Validation de la configuration


1. Vérifiez que le référentiel GitHub contient le bloc de Forms adaptatif.
2. Tester la connexion entre AEM et votre référentiel GitHub
3. Vérifiez que vous pouvez publier du contenu dans Edge Delivery Services.



## Processus de création et de publication de formulaire

Le processus se compose de trois grandes phases :

- **Phase 1:** [Sélection de modèles et création de formulaires](#step-1-template-selection-and-form-creation)
- **Phase 2 :** [Création et conception de formulaire](#step-2-form-authoring-and-design)
- **Phase 3 :** [Configuration et publication](#step-3-configuration-and-publishing)

Chaque phase comprend des étapes de validation pour confirmer une configuration correcte.

![Workflow en trois phases](/help/edge/docs/forms/universal-editor/assets/three-phase-workflow.svg)
*Présentation des trois phases principales de la création et de la publication de formulaires*

### Étape 1 : sélection du modèle et création de formulaire

Sélectionnez le workflow en fonction de votre choix de modèle :

>[!BEGINTABS]

>[!TAB Modèle Edge Delivery Services]

**Cas d’utilisation :** formulaires hautes performances et workflows de développement modernes.

**Fonctionnalités :** création dans l’éditeur universel et publication Edge Delivery Services.

#### Procédure

1. **Accéder à la création de formulaire**
   - Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
   - Accédez à **Adobe Experience Manager** > **Formulaires** > **Formulaires et documents**.
   - Cliquez sur **Créer** > **Formulaires adaptatifs**.

1. **Sélectionner modèle**
   - Dans l’onglet **Source**, sélectionnez un modèle basé sur **Edge Delivery Services**.
   - Le bouton **Créer** devient activé.

     ![Créer des formulaires EDS](/help/edge/assets/create-eds-forms.png)

1. **Configurer les options (facultatif)**
   - **Onglet Source de données** : sélectionnez l’intégration de données si nécessaire.
   - **Onglet Envoi** : sélectionnez une action d’envoi (configurable ultérieurement).
   - **Onglet Diffusion** : définissez le planning de publication/dépublication.

1. **Terminer la configuration du formulaire**
   - Cliquez sur **Créer** pour ouvrir l’assistant de création de formulaire.
   - Entrez la commande suivante :
      - **Name** : identifiant interne (pas d&#39;espace, utilisez des tirets).
      - **Titre** : nom d’affichage de votre formulaire.
      - **URL GitHub** : URL du référentiel (par exemple, `https://github.com/your-org/your-repo`).

   ![Assistant Créer un formulaire](/help/edge/assets/create-form-wizard.png)

1. **Validation**
   - Après avoir cliqué sur **Créer**, vérifiez les éléments suivants :
      - Le formulaire s’ouvre dans l’éditeur universel.
      - L’URL GitHub est correctement liée.
      - La palette de composants est disponible.
      - La zone de travail du formulaire est visible.

   ![Interface de l’éditeur universel](/help/edge/assets/author-form.png)

**Résultat :** le formulaire est prêt pour la création dans l’éditeur universel.

>[!TAB  Modèle de composant principal ]

**Cas d’utilisation :** workflows d’entreprise et intégrations complexes.

**Fonctionnalités :** création de l’éditeur de Forms adaptatif, double publication (AEM + Edge Delivery Services), fonctionnalités de formulaire avancées.

#### Procédure

1. **Accéder à la création de formulaire**
   - Connectez-vous à votre instance d’auteur AEM Forms as a Cloud Service.
   - Accédez à **Adobe Experience Manager** > **Formulaires** > **Formulaires et documents**.
   - Cliquez sur **Créer** > **Formulaires adaptatifs**.

1. **Sélectionner le modèle et le thème**
   - Dans l’onglet **Source**, sélectionnez un modèle **basé sur les composants principaux**.
   - Choisissez un **thème** pour le style.
   - Le bouton **Créer** devient activé.

   ![Sélection du modèle de composant principal](/help/forms/assets/core-component-based-template.png)

1. **Configurer les options (facultatif)**
   - **Onglet Source de données** : sélectionnez l’intégration de données si nécessaire.
   - **Onglet Envoi** : sélectionnez une action d’envoi (configurable ultérieurement).
   - **Onglet Diffusion** : définissez le planning de publication/dépublication.

1. **Terminer la configuration du formulaire**
   - Cliquez sur **Créer** pour ouvrir l’assistant de création de formulaire.
   - Entrez la commande suivante :
      - **Name** : identifiant interne (pas d&#39;espace, utilisez des tirets).
      - **Titre** : nom d’affichage de votre formulaire.
      - **Chemin** : emplacement de stockage dans le référentiel AEM.

     ![Assistant Créer un formulaire](/help/forms/assets/create-cc-form.png)

1. **Validation**
   - Après avoir cliqué sur **Créer**, vérifiez les éléments suivants :
      - Le formulaire s’ouvre dans l’éditeur de Forms adaptatif.
      - La barre d’outils du composant est disponible.
      - Le panneau des propriétés est accessible.
      - Le style du thème est appliqué.

     ![Éditeur de formulaires adaptatifs](/help/forms/assets/af-editor-form.png)

**Résultat :** le formulaire est prêt pour la création dans l’éditeur de Forms adaptatif.

>[!ENDTABS]

### Étape 2 : création et conception de formulaire

L’expérience de création varie selon le modèle :

- **Modèle Edge Delivery Services** : Éditeur universel
- **Modèle de composant principal** : éditeur de Forms adaptatif

![Comparaison des éditeurs](/help/edge/docs/forms/universal-editor/assets/editor-comparison.svg)
*Comparaison des fonctionnalités de l’éditeur universel et de l’éditeur de Forms adaptatif*

>[!BEGINTABS]

>[!TAB Éditeur universel (Edge Delivery Services)]

**Interface :** modification moderne et rationalisée, optimisée pour les performances.

#### Ajouter des composants de formulaire

1. **Accéder à la bibliothèque de composants**
   - Ouvrez l’explorateur de contenu dans l’éditeur universel.
   - Accédez au composant **Formulaire adaptatif** dans l’arborescence de contenu.

   ![ Navigation dans l’arborescence de contenu ](/help/edge/assets/content-tree.png)

1. **Ajouter des champs de formulaire**
   - Cliquez sur l’icône **Ajouter** pour ouvrir la bibliothèque de composants.
   - Sélectionnez des composants dans la liste **Composants de formulaire adaptatif**.
   - Faites glisser et déposez des composants sur la zone de travail du formulaire.

   ![Ajouter des composants](/help/edge/assets/add-component.png)

1. **Créer le formulaire**
   - Configurez les propriétés du champ dans le panneau des propriétés.
   - Définissez des règles et des comportements de validation.
*s Ajustez le style et la disposition selon vos besoins.

   ![Formulaire d&#39;inscription complété](/help/edge/assets/contact-us.png)

#### Validation

- Tous les champs obligatoires sont présents.
- Les propriétés des champs sont correctement configurées.
- La mise en page est réactive et accessible.
- Les règles de validation fonctionnent comme prévu.

#### Étapes suivantes

- [Configurer les actions d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour la gestion des données.
- [Guide de l’éditeur universel](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) pour les fonctionnalités avancées.

>[!TAB Éditeur de Forms adaptatif (composants principaux)]

**Interface :** modification complète avec des fonctionnalités de formulaire avancées.

#### Ajouter des composants de formulaire

1. **Accéder à la bibliothèque de composants**
   - Cliquez sur **Insérer le composant** dans la section **Faire glisser les composants ici**.

   ![Zone d’insertion des composants](/help/forms/assets/drag-components-af-editor.png)

2. **Ajouter des champs de formulaire**
   - Parcourez la liste **Composants de formulaire adaptatif**.
   - Faites glisser les composants de votre choix vers le formulaire.
   - Utilisez des composants avancés tels que des panneaux, des assistants et des intégrations de données.

   ![Ajouter une bibliothèque de composants](/help/forms/assets/add-component-af.png)

3. **Créer le formulaire**
   - Configurez les propriétés du champ dans le panneau des propriétés.
   - Définissez des règles de validation et une logique métier complexes.
   - Appliquez des thèmes et un style avancé.

   ![Formulaire d’inscription complété](/help/forms/assets/af-editor-form.png)

#### Validation

- Tous les champs obligatoires sont présents.
- Des règles de validation complexes sont configurées.
- Le style du thème est appliqué.
- L’intégration de données fonctionne comme prévu (le cas échéant).

#### Étapes suivantes

- [Configurer des actions d’envoi](/help/forms/configure-submit-actions-core-components.md) pour les workflows avancés.
- [ Guide des composants principaux ](/help/forms/creating-adaptive-form-core-components.md) pour les fonctionnalités d’entreprise.

>[!ENDTABS]

### Étape 3 : configuration et publication

Configurez Edge Delivery Services et publiez votre formulaire. Le processus diffère en fonction du type de modèle.

#### Configuration de Edge Delivery Services

>[!BEGINTABS]
>[!TAB Modèle Edge Delivery Services (Automatique)]

**Configuration :** automatique (aucune configuration manuelle requise).

- La connexion au référentiel GitHub et la configuration Edge Delivery Services sont créées lors de la création du formulaire.
- Les points d’entrée de publication sont configurés automatiquement.

**Vérification:**

- Confirmez que la configuration s’affiche dans les paramètres du formulaire.
- Assurez-vous que l’URL GitHub est correctement liée.

![Configuration EDS automatique](/help/edge/assets/aem-instance-eds-configuration.png)

>[!TAB Modèle de composant principal (manuel)]

**Configuration :** configuration manuelle requise.

#### Étapes de configuration manuelles

1. **Accéder aux outils de configuration**
   - Accédez à **Outils** > **Services cloud** > **Configuration Edge Delivery Services**.

   ![ Accès à la configuration EDS ](/help/edge/assets/select-eds-conf.png)

1. **Création d’une configuration**
   - Sélectionnez le dossier correspondant au nom de votre formulaire (par exemple, `forms/enrollment-form`).
   - Cliquez sur **Créer** > **Configuration**.

   ![Créer une configuration EDS](/help/forms/assets/create-eds-conf.png)

1. **Configurer les propriétés**
   - Cliquez sur **Configuration de Edge Delivery Services**.
   - Sélectionnez **Propriétés** pour ouvrir la boîte de dialogue de configuration.

   ![Propriétés de configuration.](/help/forms/assets/eds-conf.png)

1. **Définir les paramètres**
   - **Obligatoire :**
      - **Organization** : nom de l’organisation GitHub.
      - **Nom du site** : nom du référentiel GitHub.
      - **Branche** : nom de la branche (laisser vide pour la branche principale).
   - **Facultatif:**
      - **Hôte Edge** : par défaut (publie à la fois .page et .live).
      - **Jeton d’authentification du site** : pour une authentification sécurisée (si nécessaire).

1. **Enregistrer la configuration**
   - Cliquez sur **Enregistrer et fermer**.

#### Validation

- La configuration a été créée.
- L’organisation et le référentiel GitHub sont correctement spécifiés.
- Les paramètres des branches correspondent à la structure du référentiel.
- Le formulaire s’affiche dans le dossier de configuration.

>[!ENDTABS]

#### Publication du formulaire

>[!BEGINTABS]
>[!TAB Publication dans l’éditeur universel]

**Pour les modèles Edge Delivery Services**

1. Dans l’éditeur universel, cliquez sur le bouton **Publier** (coin supérieur droit).
2. Confirmez que la publication a réussi dans la boîte de dialogue.
3. Notez les URL générées pour les versions intermédiaires et actives.

   ![ Publication dans l’éditeur universel ](/help/edge/assets/publish-form.png)

- [Guide de publication](/help/edge/docs/forms/universal-editor/publish-forms.md)

>[!TAB Publication dans l’éditeur de Forms adaptatif]

1. Dans la console Experience Manager Forms, sélectionnez le formulaire à publier.
2. Cliquez sur **[!UICONTROL Publier]** dans la barre d’outils. Consultez les ressources de référence à publier.

![Publication d’un formulaire dans l’éditeur de formulaires adaptatifs](/help/forms/assets/publish-af-editor.png)

>[!NOTE]
>
> Voir [Gérer la publication dans Experience Manager Forms](/help/forms/manage-publication.md) pour plus d’informations.

>[!ENDTABS]

## URL du formulaire

Les formulaires publiés sont accessibles via les URL de Edge Delivery Services.

### Structure de l’URL

- **Évaluation (prévisualisation/test) :**

  ```
  https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
  ```

- **En direct (production) :**

  ```
  https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
  ```

#### Paramètres d’URL

- `<branch>` : nom de la branche GitHub (par exemple, `main`, `develop`).
- `<repo>` : nom du référentiel GitHub (par exemple, `my-forms-project`).
- `<owner>` : nom d’organisation ou d’utilisateur GitHub (par exemple, `company-name`).
- `<form_name>` : identifiant du formulaire tel que défini dans AEM (par exemple, `contact-us`)

#### Exemple

Exemple de `contact-us` de formulaire dans le référentiel `forms-project` sous l’`acme-corp` d’organisation :

- **Intermédiaire :** `https://main--forms-project--acme-corp.aem.page/content/forms/af/contact-us`
- **Live:** `https://main--forms-project--acme-corp.aem.live/content/forms/af/contact-us`

#### Différences d’environnement

- **En cours d’évaluation (.page) :** dernières modifications pour le test.
- **En direct (.live) :** du contenu publié pour la production.

![Structure de l’URL](/help/edge/docs/forms/universal-editor/assets/url-structure.svg)
*Répartition de la structure de l’URL du formulaire Edge Delivery Services*

#### Exemples visuels

**Modèle Edge Delivery Services :**

- En cours : ![version intermédiaire du formulaire d’enregistrement](/help/forms/assets/registration-form-staged-version.png)
- En direct : ![version en direct du formulaire d’enregistrement](/help/forms/assets/registration-form-live-version.png)

**Modèle de composant principal :**

- En cours : ![version intermédiaire du formulaire d’inscription](/help/forms/assets/enrollment-form-staged-version.png)
- En direct : ![version en direct du formulaire d’inscription](/help/forms/assets/enrollment-form-live-version.png)

## Résolution des problèmes

Vous trouverez ci-dessous les problèmes courants et les solutions pour AEM Forms avec Edge Delivery Services.

+++Formulaire non chargé

**Problème :** l’URL du formulaire renvoie une page 404 ou vide.

**Résolution :**

- Supprimez l’extension `.html` des URL.
- Vérifiez que le formulaire est publié.
- Vérifiez le référentiel GitHub pour le bloc de Forms adaptatif.
- Assurez-vous que le nom du formulaire correspond à l’URL (sensible à la casse).

+++

+++Problèmes de configuration

**Problème :** configuration de Edge Delivery Services ne fonctionne pas.

**Résolution :**

- Assurez-vous que l’URL GitHub est au format `https://github.com/owner/repository`.
- Utilisez le nom de branche correct dans la configuration.
- Vérifiez l’accès au référentiel (public ou authentifié).
- Vérifiez `fstab.yaml` les détails GitHub corrects.

+++

+++Problèmes de publication

**Problème :** modifications n’apparaissent pas sur le site actif.

**Résolution :**

- Patientez 2 à 3 minutes pour l’actualisation du cache du réseau CDN.
- Confirmez que le workflow de publication est terminé.
- Testez d’abord l’environnement d’évaluation (.page).
- Assurez-vous que le référentiel GitHub est mis à jour.

+++

+++Problèmes liés à l’éditeur universel

**Problème :** impossible de modifier le formulaire ou les composants ne se chargent pas.

**Résolution :**

- Utilisez un navigateur pris en charge (Chrome, Firefox, Safari).
- Effacez le cache et les cookies du navigateur.
- Vérifiez la connectivité réseau.
- Confirmez les autorisations de création.

+++

+++Erreurs d’envoi de formulaire

**Problème :** envois de formulaire ne fonctionnent pas.

**Résolution :**

- Configurez l’action d’envoi dans les propriétés du formulaire.
- Testez manuellement les points d’entrée d’envoi.
- Vérifiez les paramètres CORS en cas d’incorporation de formulaires.
- Vérifiez que les champs obligatoires sont configurés.

+++

+++Problèmes de performances

**Problème :** chargement de formulaire lent ou mauvaises performances.

**Résolution :**

- Optimisez les images.
- Supprimez les composants inutiles.
- Tirez parti du réseau CDN de Edge Delivery Services.
- Réduisez les JavaScript/CSS personnalisés.

+++

+++Obtention d’aide

Si les problèmes persistent :

1. Vérifiez l’état du service Adobe Experience Cloud.
2. Consultez la documentation de [Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=fr).
3. Visitez [Communauté Adobe Experience League](https://experienceleaguecommunities.adobe.com/?profile.language=fr).
4. Contactez l’assistance clientèle d’Adobe.

+++

## Étapes suivantes

Après avoir créé et publié le formulaire, tenez compte des points suivants :

### Actions immédiates

- Testez votre formulaire à l’aide de ce guide.
- Validez votre référentiel GitHub et votre connexion AEM.
- Examinez les exemples de formulaires.

### Rubriques avancées

- [Configurer les actions Envoyer](/help/edge/docs/forms/universal-editor/submit-action.md) : configurez la gestion des données et les intégrations.
- [Modèles de données de formulaire](/help/forms/create-form-data-models.md) : connectez les formulaires aux sources de données principales.

### Optimisation des performances

- [Bonnes pratiques relatives à Edge Delivery Services ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=fr) : optimisation des performances.
- [Form Analytics](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html) : suivez les performances des formulaires et le comportement des utilisateurs et utilisatrices.


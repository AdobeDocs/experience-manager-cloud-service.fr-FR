---
title: Comment configurer les API synchrones des communications interactives ?
description: Configuration de l’environnement de développement pour les API synchrones de communications interactives pour Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromToC: true
index: false
source-git-commit: 5e3175cc4d96c89df4154ae42c5042cf9c2ca739
workflow-type: tm+mt
source-wordcount: '2574'
ht-degree: 2%

---


# Traitement des API synchrones de communication d’AEM Forms as a Cloud Service

Ce guide fournit des instructions complètes sur la configuration et l’utilisation des API synchrones AEM Forms Communications.

Découvrez comment configurer votre environnement AEM as a Cloud Service, activer l’accès aux API et appeler les API de communication à l’aide de l’authentification de serveur à serveur OAuth.

## Conditions préalables

Pour configurer un environnement afin d’exécuter et de tester les API AEM Forms Communications, vérifiez que vous disposez des éléments suivants :

### Accès et autorisations

Assurez-vous de disposer des droits d’accès et des autorisations requis avant de commencer à configurer les API Communications.

**Autorisations des utilisateurs et des rôles**

- Adobe ID créé à l’adresse [https://account.adobe.com/](https://account.adobe.com/fr)
- Adobe ID associé à l’e-mail de votre organisation
- Attribution du contexte de produit Adobe Managed Services
- Rôle de développeur affecté dans Adobe Admin Console
- Autorisation de création de projets dans le Adobe Developer Console

>[!NOTE]
>
> Pour en savoir plus sur l’attribution de rôles et l’octroi de l’accès aux utilisateurs, consultez l’article [Ajouter des utilisateurs et des rôles](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/users-and-roles).

**Accès Cloud Manager**

- Identifiants de connexion pour [Cloud Manager](https://my.cloudmanager.adobe.com)
- Accès pour afficher et gérer les environnements de votre programme
- Autorisation de créer et d’exécuter des pipelines CI/CD
- Accès aux détails et à la configuration de l’environnement

**Accès au référentiel Git**

- Accès au référentiel Git de Cloud Manager
- Informations d’identification Git pour le clonage et l’envoi de modifications

### Outils de développement

- **Node.js** pour exécuter des exemples d’applications
- Dernière version de **Git**
- Accès à **Terminal/Ligne de commande**
- **Éditeur de texte ou IDE** pour modifier les fichiers de configuration (VS Code, IntelliJ, etc.)
- **Postman** ou outil similaire pour les tests d’API

>[!NOTE]
>
> Il s’agit d’un processus unique par environnement qui doit être terminé avant de poursuivre la configuration des API Communications d’AEM Forms.

Maintenant, comprenons chaque étape en détail.

### Étape 1 : mettre à jour l’instance AEM

Pour mettre à jour l’instance AEM :

1. **Connexion à Adobe Cloud Manager**
   1. Accédez à [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
   2. Connexion avec votre Adobe ID

2. **Accéder à la présentation du programme**
   1. Sélectionnez votre programme dans la liste. Vous êtes redirigé vers la page Aperçu du programme .

3. **Rechercher les détails de l’environnement**
   1. Sélectionnez l’icône `ellipsis`(...) en regard du nom de l’environnement, puis cliquez sur **Mettre à jour**
   2. Cliquez sur le bouton **Envoyer** et exécutez le pipeline full stack suggéré.

      ![Mettre à jour l’environnement](/help/forms/assets/update-env.png)

### Étape 2 : Cloner Le Référentiel Git

Clonez le référentiel Git de Cloud Manager pour gérer vos fichiers de configuration API.

1. **Recherchez la section Repository**
   1. Sur la page **Présentation du programme**, cliquez sur l’onglet **Référentiels**
   2. Recherchez le nom du référentiel et cliquez sur le menu représentant des points de suspension (...)
   3. Copiez l’URL du référentiel.

      >[!NOTE]
      >
      > Le format de l’URL est généralement `https://git.cloudmanager.adobe.com/<org>/<program>/`

2. **Cloner À L’Aide De La Commande Git**

   1. Ouvrez l’invite de commande ou le terminal
   2. Exécutez la commande `git clone` pour cloner le référentiel Git.

      ```bash
      git clone [repository-url]
      ```

      >[!NOTE]
      >
      > Pour cloner le référentiel Git, utilisez les informations d’identification fournies par Adobe Cloud Manager.

      Par exemple, pour cloner votre référentiel Git, exécutez la commande suivante :

      ```bash
      https://git.cloudmanager.adobe.com/formsinternal01/AEMFormsInternal-ReleaseSanity-p43162-uk59167/
      ```

      ![Clonage du référentiel Git](/help/forms/assets/repo-clone.png)


### Options d’intégration du référentiel Git

Adobe Cloud Manager prend en charge les deux options de référentiel :

- **Utilisation directe du référentiel Git Cloud Manager**
   - Utiliser le référentiel Git natif de Cloud Manager
   - Intégration intégrée aux pipelines

- **Intégration au référentiel Git géré par le client**
   - Connectez votre propre référentiel Git (GitHub, GitLab, Bitbucket, etc.).
   - Configuration de la synchronisation avec Adobe Cloud Manager

Pour en savoir plus sur l’intégration d’Adobe Cloud Manager à Adobe Cloud Manager, voir [Documentation sur l’intégration Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/git-integration.html).

### Étape 3 : accéder à l’environnement AEM Cloud Service et au point d’entrée AEM Forms

Accédez aux détails de votre environnement AEM Cloud Service pour obtenir les URL et les identifiants nécessaires à la configuration de l’API.

1. **Connexion à Adobe Cloud Manager**
   1. Accédez à [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
   2. Connexion avec votre Adobe ID

2. **Accéder à la présentation du programme**
Sélectionnez votre programme dans la liste. Vous êtes redirigé vers la page Aperçu du programme .

3. **Accès et affichage de l’environnement AEM Cloud Service**

   Vous pouvez afficher les détails de l’environnement AEM Cloud Service ou y accéder à l’aide de l’une des deux options suivantes :

   - **Option 1 : À Partir De La Page Aperçu**

      1. Sur la page **Aperçu du programme**
      2. Cliquez sur **« Environnements »** dans le menu de gauche.  Vous pouvez voir une liste de tous les environnements

         ![Afficher tous les environnements](/help/forms/assets/all-env.png)

      3. Cliquez sur le nom de l’environnement pour en afficher les détails

         ![Option1-Détails de l’environnement](/help/forms/assets/option1-env.png)

   - **Option 2 : À Partir De La Section Environnements**

      1. Sur la page Aperçu du programme
      2. Recherchez la section **Environnements**
      3. Cliquez sur **« Tout afficher »** pour afficher tous les environnements
      4. Cliquez sur le menu **points de suspension (...)** en regard de l’environnement
         ![Option1-Détails de l’environnement](/help/forms/assets/option2-env-details.png)
      5. Sélectionnez **« Afficher les détails »**

         ![Option1-Détails de l’environnement](/help/forms/assets/option1-env.png)

4. **Recherchez Votre Point D’Entrée AEM Forms**

   Sur la page de détails **Environnement**, notez les informations suivantes :

   **URL du service de création**

   - URL : `https://author-pXXXXX-eYYYYY.adobeaemcloud.com`
   - Compartiment : author-pXXXXX-eYYYY
Exemple : `https://author-p43162-e177398.adobeaemcloud.com`

   **URL du service de publication**

   - URL : `https://publish-pXXXXX-eYYYYY.adobeaemcloud.com`
   - Compartiment : publish-pXXXXX-eYYYY
Exemple : `https://publish-author-p43162-e177398.adobeaemcloud.com`

>[!NOTE]
>
> Pour savoir comment accéder à l’environnement AEM Cloud Service et au point d’entrée AEM Forms, consultez la section [Documentation sur la gestion des environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=fr).

### Étape 4 : configuration de l’accès à l’API

Pour configurer les API AEM Forms Communications, procédez comme suit :

#### 4.1 Configuration du projet Adobe Developer Console

1. **Accéder à Adobe Developer Console**
   1. Accéder à [Adobe Developer Console](https://developer.adobe.com/console)
   2. Connexion avec votre Adobe ID

2. **Créer un projet**
   1. Dans la section **Démarrage rapide**, cliquez sur **Créer un projet**
   2. Un nouveau projet est créé avec un nom par défaut

      ![Créer un projet ADC](/help/forms/assets/adc-home.png)

   3. Cliquez sur **Modifier le projet** dans le coin supérieur droit

      ![Modifier projet](/help/forms/assets/adc-edit-project.png)

   4. Fournissez un nom significatif (par exemple, « projet de formulaire »).
   5. Cliquer sur **Enregistrer**

      ![Modifier le nom du projet](/help/forms/assets/adc-edit-projectname.png)

#### 4.2 Ajout des API de communication Forms

Vous pouvez ajouter différentes API AEM Forms Communications en fonction de vos besoins.

**A. Pour les API Document Services**

1. Cliquez sur **Ajouter une API**

   ![Ajouter une api](/help/forms/assets/adc-add-api.png)

2. Sélectionnez **API de communication Forms**
   1. Dans la boîte de dialogue _Ajouter une API_, filtrez par **Experience Cloud**
   2. Sélectionnez **« API de communication Forms »**

   ![Ajouter l’API de communication Forms](/help/forms/assets/adc-add-forms-api.png)


3. Sélectionnez la méthode d’authentification **OAuth de serveur à serveur**

   ![Sélectionner la méthode d’authentification](/help/forms/assets/adc-add-authentication-method.png)

**B. Pour les API d’exécution Forms**

1. **Cliquez sur Ajouter une API**
   - Dans votre projet, cliquez sur le bouton **Ajouter une API**

   ![Ajouter une api](/help/forms/assets/adc-add-api.png)

2. **Sélectionnez l’API de diffusion et d’exécution AEM Forms**
   - Dans la boîte de dialogue _Ajouter une API_, filtrez par **Experience Cloud**
   - Sélectionnez **« API de diffusion et d’exécution AEM Forms »**
   - Cliquer sur **Suivant**

   ![Ajouter une API d’exécution](/help/forms/assets/add-runtime-api.png)


3. **Méthode d’authentification**
   - Sélectionnez la méthode d’authentification **OAuth de serveur à serveur**.


   ![Sélectionner la méthode d’authentification](/help/forms/assets/add-authentication-for-runtime-apis.png)

#### 4.3 Ajouter un profil de produit

Pour ajouter le profil de produit, procédez comme suit :

1. Sélectionnez le **profil de produit** approprié en fonction du niveau d’accès requis :

   | Type d’accès | Profil de produit |
   |------------------|----------------------|
   | Accès en lecture seule | `AEM Users - author - Program XXX - Environment XXX` |
   | Accès en lecture/écriture | `AEM Assets Collaborator Users - author - Program XXX - Environment XXX` |
   | Accès administratif complet | `AEM Administrators - author - Program XXX - Environment XXX` |

2. Sélectionnez le **profil de produit** qui correspond à votre URL de service de création (`https://author-pXXXXX-eYYYYY.adobeaemcloud.com`). Par exemple : sélectionnez `https://author-pXXXXX-eYYYYY.adobeaemcloud.com`.

3. Cliquez sur **Save configured API** (Enregistrer l’API configurée). L’API et le profil de produit sont ajoutés au projet

   ![Sélectionner la configuration du projet](/help/forms/assets/adc-add-product-profile.png)

#### 4.4 Générer et enregistrer des informations d’identification

1. **Accéder À Vos Informations D’Identification**

   1. Accédez à votre projet dans Adobe Developer Console
   2. Cliquez sur les informations d’identification **OAuth de serveur à serveur**
   3. Consultez la section **Informations d’identification**

   ![Afficher les informations d’identification](/help/forms/assets/adc-view-credential.png)

2. **Enregistrer les informations d’identification de l’API**

   ```text
   API Credentials:
   ================
   Client ID: <your_client_id>
   Client Secret: <your_client_secret>
   Technical Account ID: <tech_account_id>
   Organization ID: <org_id>
   Scopes: AdobeID,openid,read_organizations
   ```

#### 4.5 Génération de jetons d’accès

**A. Pour les tests**

Générez manuellement les jetons d’accès dans Adobe Developer Console :

1. **Accédez à votre projet**
   1. Dans Adobe Developer Console, ouvrez votre projet
   2. Cliquez sur **OAuth de serveur à serveur**

2. **Générer un jeton d’accès**
   1. Cliquez sur le bouton **Générer un jeton d’accès »** dans la section API de votre projet
   2. Copier le jeton d’accès généré

   ![ Générer un jeton d’accès ](/help/forms/assets/adc-access-token.png)

   >[!NOTE]
   >
   > Le jeton d’accès est valide pendant **24 heures**

**B. Pour la production**

Générez des jetons par programmation à l’aide de l’API Adobe IMS :

**Informations d’identification requises :**

- ID client
- Secret client
- Portées (généralement : `AdobeID,openid,read_organizations`)

**Point d’entrée du jeton :**

```
https://ims-na1.adobelogin.com/ims/token/v3
```

**Exemple de requête (curl) :**

```bash
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'grant_type=client_credentials' \
  -d 'client_id=<YOUR_CLIENT_ID>' \
  -d 'client_secret=<YOUR_CLIENT_SECRET>' \
  -d 'scope=AdobeID,openid,read_organizations'
```

**Réponse:**

```json
{
  "access_token": "eyJhbGciOiJSUz...",
  "token_type": "bearer",
  "expires_in": 86399
}
```

#### 4.6 Enregistrement de l’ID client dans l’environnement AEM

Pour permettre à l’ID client de votre projet ADC de communiquer avec l’instance AEM, vous devez l’enregistrer à l’aide d’un fichier de configuration YAML et le déployer via un pipeline de configuration.

1. **Rechercher ou créer un répertoire de configuration**

   1. Accédez au référentiel de projet AEM cloné, puis au dossier `config` .
   2. S’il n’existe pas, créez-le au niveau racine du projet :

   ```bash
   mkdir config
   ```

2. Créez un fichier nommé `api.yaml` dans le répertoire `config` :

   ```bash
   touch config/api.yaml
   ```

3. Ajoutez le code suivant dans le fichier `api.yaml` :

   ```yaml
   kind: "API"
   version: "1"
   metadata:
   envTypes: ["dev"]  # or ["prod", "stage"] for production environments
   data:
   allowedClientIDs:
       author:
       - "<your_client_id>"
       publish:
       - "<your_client_id>"
       preview:
       - "<your_client_id>"
   ```

   Les paramètres de configuration sont expliqués ci-dessous :

   - **kind** : toujours définie sur `"API"` (identifie cela comme une configuration d&#39;API)
   - **version** : version de l’API, généralement `"1"` ou `"1.0"`
   - **envTypes** : tableau des types d’environnements auxquels s’applique cette configuration.
      - `["dev"]` - Environnements de développement uniquement
      - `["stage"]` - Environnements d’évaluation uniquement
      - `["prod"]` - Environnements de production uniquement
   - **allowedClientIDs** : ID de client autorisés à accéder à votre instance AEM
      - **author** : ID de client pour le niveau de création
      - **publish** : ID de client pour le niveau de publication
      - **preview** : ID de client pour le niveau d’aperçu

   Par exemple, ajoutez le `allowedClientIDs` en tant que `6bc4589785e246eda29a545d3ca55980` et envTypes en tant que `dev` :

   ![Ajout d’un fichier de configuration](/help/forms/assets/create-api-yaml-file.png)

4. **Valider et envoyer les modifications**

   1. Accédez au dossier racine du référentiel cloné et exécutez les commandes ci-dessous :


   ```bash
       git add config/api.yaml
       git commit -m "Whitelist client id for api invocation"
       git push origin <your-branch>
   ```

   ![Pousser les modifications Git](/help/forms/assets/push-yaml-changes-in-git.png)


5. **Configurer le pipeline**

   1. **Connexion à Cloud Manager**
      1. Accédez à [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
      2. Connexion avec votre Adobe ID

   2. **Accédez à votre programme**
Sélectionnez votre programme dans la liste et vous êtes redirigé vers la page Aperçu du programme .

   3. **Recherchez la carte Pipelines**
      1. Recherchez la vignette **Pipelines** dans la page Aperçu du programme .
      1. Cliquez sur **bouton « Ajouter »**

   4. **Sélectionner le type de pipeline**

      - **Pour Les Environnements De Développement** : Sélectionnez **« Ajouter Un Pipeline Hors Production »**. Les pipelines hors production sont destinés aux environnements de développement et intermédiaires

      - **Pour Les Environnements De Production** : Sélectionnez **« Ajouter Un Pipeline De Production »**. Les pipelines de production nécessitent des approbations supplémentaires

        >[!NOTE]
        >
        > Dans ce cas, créez un pipeline hors production, car un environnement de développement est disponible.

   5. **Configurer le pipeline - Onglet Configuration**

      Dans l’onglet **Configuration** :

      a. **Type de pipeline**
      - Sélectionnez **Pipeline de déploiement**

      b. **Nom du pipeline**
      - Attribuez un nom explicite, par exemple, « `api-config-pipieline` » au pipeline.

      c. **Déclencheur de déploiement**
      - **Manuel** : le déploiement n’est effectué que lorsqu’il est déclenché manuellement (recommandé pour la configuration initiale)
      - **Lors des modifications Git** : déploiement automatique lorsque les modifications sont transmises à la branche

      d. **Comportement en cas d’échecs de mesures importants**
      - **Demander à chaque fois** : demande d’action en cas d’échec (par défaut)
      - **Échec immédiat** : échec automatique du pipeline en cas d’échec des mesures
      - **Continuer immédiatement** : continuer malgré les échecs

      e. Cliquez sur **« Continuer »** pour accéder à l’onglet **Code Source**

      ![Configurer le pipeline](/help/forms/assets/add-config-pipeline.png)

   6. **Configurer le pipeline - Onglet Code Source**

      Dans l&#39;onglet **Code Source** :

      a. **Type de déploiement**
      - Sélectionnez **« Déploiement ciblé »**

      b. **Options de déploiement**
      - Sélectionnez **« Config »** (déployer les fichiers de configuration uniquement). Il indique à Cloud Manager qu’il s’agit d’un déploiement de configuration.

      c. **Sélectionner un environnement de déploiement éligible**
      - Choisissez l’environnement dans lequel vous souhaitez déployer la configuration. Dans ce cas, il s’agit d’un environnement `dev`.

      d. **Définition des détails du code Source**

      - **Référentiel** : sélectionnez le référentiel contenant votre fichier `api.yaml`. Par exemple, sélectionnez le référentiel `AEMFormsInternal-ReleaseSanity-p43162-uk59167`.
      - **Branche Git** : sélectionnez votre branche. Par exemple, dans ce cas, notre code est déployé au niveau de la branche `main`.
      - **Emplacement du code** : saisissez le chemin d’accès au répertoire `config`. Comme le `api.yaml` se trouve dans `config` dossier racine, saisissez `/config`

      e. Cliquez sur **« Enregistrer »** pour créer le pipeline

      ![Configurer le pipeline](/help/forms/assets/confirm-pipeline-1.png)

6. **Déployer la configuration**

   Maintenant que le pipeline est créé, déployez votre configuration `api.yaml` :

   1. **Dans la présentation des pipelines**
      1. Sur la page Aperçu du programme , recherchez la vignette **Pipelines**
      2. Accédez au pipeline de configuration que vous venez de créer dans la liste. Par exemple, recherchez le nom du pipeline que vous avez créé (par exemple, « api-config-pipeline »). Vous pouvez afficher les détails du pipeline, notamment le statut et la dernière exécution.

   2. **Démarrer le déploiement**
      1. Cliquez sur le bouton **« Créer »** (ou sur l’icône de lecture ▶) à côté de votre pipeline
      2. Confirmez le déploiement si vous y êtes invité et l’exécution du pipeline commence

      ![exécuter le pipeline](/help/forms/assets/run-config-pipeline.png)

   3. **Vérification de la réussite du déploiement**
      - Attendez que le pipeline soit terminé.
         - S’il réussit, le statut passe à « Succès » (coche verte ✓).
         - En cas d’échec, le statut est remplacé par « Échec » (✗ croix rouge). Cliquez sur **Télécharger les journaux** pour afficher les détails de l’erreur.

           ![Succès du pipeline](/help/forms/assets/pipeline-suceess.png)

      Vous pouvez maintenant commencer à tester les API Forms Communications. À des fins de test, vous pouvez utiliser le client Postman, curl ou tout autre client REST pour appeler les API .

### Étape 5 : spécifications et tests de l’API

Maintenant que votre environnement est configuré, vous pouvez commencer à tester les API de communication AEM Forms à l’aide de l’interface utilisateur [Swagger](#a-using-swagger-ui-for-api-testing) ou par programmation en développant l’application NodeJS.

Dans cet exemple, nous allons générer un PDF à l’aide des API Document Services à l’aide du modèle et du fichier XDP.

#### A. Utilisation de l’interface utilisateur Swagger pour les tests d’API

L’interface utilisateur Swagger fournit une interface interactive pour tester les API sans écrire de code. Utilisez la fonctionnalité **Essayer** pour appeler et tester l’API [générer PDF](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) Document Service.

1. Accéder à la documentation de l’API
   - API Forms : [Référence de l’API Forms](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
   - Document Services : [Référence de l’API des services de document](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
Ouvrez la documentation des [API des services de document](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document) dans votre navigateur.
2. Développez la section **Génération de documents** et sélectionnez [ Génère un formulaire PDF à remplir à partir d’un modèle XDP ou PDF, éventuellement avec fusion des données](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm).
3. Dans le volet de droite, cliquez sur **Essayer**.

   ![Test Swagger pour l’API](/help/forms/assets/api-doc-generation.png)
4. Saisissez les valeurs suivantes :

   | **Section** | **Paramètre** | **Valeur**. |
   |--------------|---------------|------------|
   | compartiment | Instance AEM | Nom de l’instance AEM sans le nom de domaine Adobe (`.adobeaemcloud.com`) Par exemple, utilisez `p43162-e177398` comme compartiment. |
   | Sécurité | Jeton porteur | Utilisez le jeton d’accès à partir des informations d’identification de serveur à serveur OAuth du projet Adobe Developer Console |
   | Corps | template | Chargez un fichier XDP pour générer le formulaire PDF. Par exemple, vous pouvez utiliser [ce XDP](/help/forms/assets/ClosingForm.xdp) pour générer un PDF. |
   | Corps | data | Fichier XML facultatif contenant les données à fusionner avec le modèle pour générer un formulaire PDF prérempli. Par exemple, vous pouvez utiliser [ce XML](/help/forms/assets/ClosingForm.xml) pour générer un PDF. |
   | Paramètres | X-Adobe-Accept-Experimental | 1 |

5. Cliquez sur **Envoyer** pour appeler l’API

   ![API d’envoi](/help/forms/assets/api-send.png)

6. Vérifiez la réponse dans l’onglet **Réponse** :
   - Si le code de réponse est `200`, cela signifie que le PDF a été créé avec succès.
   - Si le code de réponse est `400`, cela signifie que les paramètres de requête sont non valides ou incorrects.
   - Si le code de réponse est `500`, cela signifie qu’il existe une erreur de serveur interne.

   Dans ce cas, le code de réponse est `200`, ce qui signifie que le PDF a bien été généré :

   ![Réponse de révision](/help/forms/assets/api-success.png)

   Vous pouvez désormais télécharger le [PDF créé](/help/forms/assets/create-pdf.pdf) à l’aide du bouton **Télécharger** et l’afficher dans la visionneuse PDF :

   ![Afficher PDF](/help/forms/assets/create-pdf.png)

>[!NOTE]
>
> À des fins de test, vous pouvez également utiliser [Postman](https://www.postman.com/), [curl](https://curl.se/) ou tout autre client REST pour appeler les API AEM.

#### B. Par programmation, en développant l’application NodeJS

Développez une application Node.js pour générer un formulaire PDF à remplir à partir d’un modèle **XDP** et d’un fichier de données **XML** à l’aide de l’API **Document Services**

##### Conditions préalables

- Node.js installé sur votre système
- Instance AEM as a Cloud Service active
- Jeton porteur pour l’authentification de l’API à partir de Adobe Developer Console
- Exemple de fichier XDP : [ClosingForm.xdp](/help/forms/assets/ClosingForm.xdp)
- Exemple de fichier XML : [ClosingForm.xml](/help/forms/assets/ClosingForm.xml)

Pour développer l’application Node.js, procédez comme suit :

##### Étape 1 : créer un projet Node.js

Ouvrez le cmd/terminal et exécutez les commandes ci-dessous :

```bash
# Create a new directory
mkdir demo-nodejs-generate-pdf
cd demo-nodejs-generate-pdf

##### Initialize Node.js project
npm init -y
```

![Créer un projet node js](/help/forms/assets/api-1.png)

##### Étape 2 : Installer les dépendances requises

Installez les bibliothèques **node-fetch**, **dotenv** et **form-data** pour effectuer des requêtes HTTP, lire des variables d’environnement et gérer les données de formulaire, respectivement.

```bash
npm install node-fetch
npm install dotenv
npm install form-data
```

![installer les dépendances npm](/help/forms/assets/api-2.png)

##### Étape 3 : mettre à jour package.json

1. Ouvrez le cmd/terminal et exécutez la commande :

   ```bash
   code .
   ```

   ![ouvrez un projet dans l’éditeur](/help/forms/assets/api-3.png)

   Le projet s’ouvre alors dans l’éditeur de code.

2. Mettez à jour le fichier `package.json` pour ajouter le `type` à `module`.

   ```bash
   {
   "name": "demo-nodejs-generate-pdf",
   "version": "1.0.0",
   "type": "module",
   "main": "index.js",
   }
   ```

   ![mettre à jour le fichier de package](/help/forms/assets/api-4.png)

##### Étape 4 : Créer un fichier .env

1. Créer un fichier .env au niveau racine d’un projet
2. Ajoutez la configuration suivante et remplacez les espaces réservés par les valeurs réelles des informations d’identification OAuth de serveur à serveur du projet ADC.

   ```bash
   CLIENT_ID=<ADC Project OAuth Server-to-Server credential ClientID>
   CLIENT_SECRET=<ADC Project OAuth Server-to-Server credential Client Secret>
   SCOPES=<ADC Project OAuth Server-to-Server credential Scopes>
   ```

   ![créer un fichier d’environnement](/help/forms/assets/api-5.png)

   >[!NOTE]
   >
   > Vous pouvez copier les `CLIENT_ID`, `CLIENT_SECRET` et `SCOPES` à partir du projet Adobe Developer Console.

##### Étape 5 : Créer src/index.js

1. Créer `index.js` fichier au niveau racine du projet
2. Ajoutez le code suivant et remplacez les espaces réservés par les valeurs réelles :

```javascript
// Import the dotenv configuration to load environment variables from the .env file
import "dotenv/config";

// Import fetch for making HTTP requests
import fetch from "node-fetch";
import fs from "fs";
import FormData from "form-data";

// REPLACE THE FOLLOWING VALUE WITH YOUR OWN
const bucket = <bucket-value>; // Your AEM Cloud Service Bucket name
const xdpFilePath = <xdp-file>;
const xmlFilePath = <xml-file>;

// Load environment variables
const clientId = process.env.CLIENT_ID;
const clientSecret = process.env.CLIENT_SECRET;
const scopes = process.env.SCOPES;

// Adobe IMS endpoint for obtaining an access token
const adobeIMSV3TokenEndpointURL = "https://ims-na1.adobelogin.com/ims/token/v3";

// Function to get an access token
const getAccessToken = async () => {
    console.log("Getting access token from IMS...");

    const options = {
        method: "POST",
        headers: {
            "Content-Type": "application/x-www-form-urlencoded",
        },
        body: `grant_type=client_credentials&client_id=${clientId}&client_secret=${clientSecret}&scope=${scopes}`,
    };

    const response = await fetch(adobeIMSV3TokenEndpointURL, options);
    const responseJSON = await response.json();

    console.log("Access token received.");
    return responseJSON.access_token;
};

// Function to generate PDF form from XDP and XML
const generatePDF = async () => {
    const accessToken = await getAccessToken();

    console.log("Generating PDF form from XDP and XML...");

    // Read XDP and XML files
    const xdpFile = fs.readFileSync(xdpFilePath);
    const xmlFile = fs.readFileSync(xmlFilePath);

    const url = `https://${bucket}.adobeaemcloud.com/adobe/document/generate/pdfform`;

    const formData = new FormData();
    formData.append("template", xdpFile, {
        filename: "form.xdp",
        contentType: "application/vnd.adobe.xdp+xml"
    });
    formData.append("data", xmlFile, {
        filename: "data.xml",
        contentType: "application/xml"
    });

    const response = await fetch(url, {
        method: "POST",
        headers: {
            Authorization: `Bearer ${accessToken}`,
            "X-Api-Key": clientId,
            "X-Adobe-Accept-Experimental": "1",
            ...formData.getHeaders()
        },
        body: formData,
    });

    if (response.ok) {
        const arrayBuffer = await response.arrayBuffer();
        fs.writeFileSync("generatedForm.pdf", Buffer.from(arrayBuffer));
        console.log("✅ PDF form generated successfully (saved as generatedForm.pdf)");
    } else {
        console.error("❌ Failed to generate PDF. Status:", response.status);
        console.error(await response.text());
    }
};

// Run the PDF generation function
generatePDF();
```

![créer index.js](/help/forms/assets/api-6.png)

##### Étape 6 : exécuter l’application

```bash
node src/index.js
```

![exécuter l’application](/help/forms/assets/api-7.png)

Le PDF est créé dans le dossier `demo-nodejs-generate-pdf` . Accédez au dossier pour trouver le fichier généré nommé `generatedForm.pdf`.

![afficher le pdf créé](/help/forms/assets/api-8.png)

Vous pouvez ouvrir le [PDF généré](/help/forms/assets/create-pdf.png) pour l’afficher.

## Résolution des problèmes

### Problèmes courants et causes possibles

#### Problème 1 : Erreur 403 Interdite

**Symptômes :**

- `403 Forbidden` de retour des requêtes API
- Message d’erreur : *Accès refusé* ou *Autorisations insuffisantes*
- Se produit même avec un jeton d’accès valide

**Causes possibles :**

- Autorisations insuffisantes dans le profil de produit lié aux informations d’identification de serveur à serveur OAuth.
- Le groupe d’utilisateurs du service dans l’auteur AEM ne dispose pas des autorisations nécessaires sur les chemins de contenu requis

#### Problème 2 : Erreur 401 Non Autorisée

**Symptômes :**

- `401 Unauthorized` de retour des requêtes API
- Message d’erreur : *jeton non valide ou expiré*

**Causes possibles :**

- Jeton d’accès expiré (valide pendant 24 heures uniquement)
- Identifiant client et secret client incorrects ou incompatibles
- En-têtes d’authentification manquants ou incorrects dans la requête API

#### Problème 3 : Erreur 404 Introuvable

**Symptômes :**

- `404 Not Found` de retour des requêtes API
- Message d’erreur : *Ressource introuvable* ou point d’entrée *API introuvable*

**Causes possibles :**

- Identifiant client non inscrit dans la configuration `api.yaml` de l’instance AEM
- Paramètre de compartiment incorrect (ne correspond pas à l’identifiant de l’instance AEM)
- ID de ressource non valide ou inexistant (formulaire ou ressource)

#### Problème 4 : Option d’authentification de serveur à serveur non disponible

**Symptômes :**

- Option OAuth de serveur à serveur manquante ou désactivée dans Adobe Developer Console

**Cause possible :**

- L’utilisateur qui crée l’intégration n’est pas ajouté en tant que **développeur** dans le profil de produit associé

#### Problème 5 : échec du déploiement du pipeline

**Symptômes :**

- Échec de l’exécution de la configuration du pipeline
- Les journaux de déploiement affichent les erreurs liées aux `api.yaml`

**Causes possibles :**

- Syntaxe YAML non valide (problèmes de mise en retrait, de guillemets ou de format de tableau)
- `api.yaml` placé dans un répertoire incorrect
- Identifiant client incorrect ou mal formé dans la configuration


## Articles connexes

Pour savoir comment configurer un environnement pour le traitement par lots (API asynchrones), consultez [Traitement par lots des communications AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-batch-processing.md).

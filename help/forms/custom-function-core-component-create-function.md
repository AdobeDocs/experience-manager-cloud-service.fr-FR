---
title: Création et ajout de fonctions personnalisées dans un formulaire adaptatif
description: AEM Forms prend en charge les fonctions personnalisées, qui permettent aux utilisateurs de créer et d’utiliser leurs propres fonctions dans l’éditeur de règles.
keywords: Ajoutez une fonction personnalisée, utilisez une fonction personnalisée, créez une fonction personnalisée, utilisez une fonction personnalisée dans l’éditeur de règles.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: e7ab4233-2e91-45c6-9377-0c9204d03ee9
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '1360'
ht-degree: 50%

---

# Créer une fonction personnalisée pour un formulaire adaptatif basé sur les composants principaux

Le Forms adaptatif basé sur les composants principaux offre des expériences utilisateur dynamiques en ajustant le contenu et le comportement en fonction des entrées utilisateur. Les fonctions personnalisées permettent aux développeurs et aux développeuses d’étendre les fonctionnalités, en veillant à ce que les formulaires puissent répondre à des exigences spécifiques. En intégrant des fonctions personnalisées, les développeurs et les développeuses peuvent mettre en œuvre une logique complexe, automatiser les processus et introduire des interactions uniques qui s’alignent sur les besoins spécifiques de l’entreprise ou les attentes des utilisateurs et utilisatrices. Cela permet de s’assurer que les formulaires s’adaptent à des conditions variables, mais aussi qu’ils fournissent une solution plus précise et plus efficace pour divers cas d’utilisation.
Cet article vous guide tout au long des étapes de création de fonctions personnalisées pour le Forms adaptatif à l’aide de composants principaux.

## Considérations

* Les `parameter type` et `return type` ne prennent pas en charge `None`.

* Les fonctions qui ne sont pas prises en charge dans la liste des fonctions personnalisées sont les suivantes :
   * Fonctions du générateur
   * Fonctions asynchrones/d’attente
   * Définitions des méthodes
   * Méthodes de classe
   * Paramètres par défaut
   * Paramètres REST

* Les dernières fonctionnalités ECMAScript sont disponibles en tant qu’accès anticipé (EA), tandis que jusqu’à ECMAScript 2019 est pris en charge en disponibilité générale.

## Conditions préalables pour créer une fonction personnalisée

Avant de commencer à ajouter une fonction personnalisée à votre Forms adaptatif, vérifiez que vous disposez des éléments suivants :

**Logiciel:**

* **Éditeur de texte brut (IDE)** : bien que tout éditeur de texte brut puisse fonctionner, un environnement de développement intégré (IDE) comme Microsoft Visual Studio Code offre des fonctionnalités avancées pour faciliter la modification.

* **Git :** ce système de gestion de versions est nécessaire pour gérer les modifications de code. Si vous ne l’avez pas installé, téléchargez-le à partir de https://git-scm.com.


## Création d’une fonction personnalisée

Créez une bibliothèque cliente pour appeler des fonctions personnalisées dans l’éditeur de règles. Pour plus d’informations, voir [Utilisation des bibliothèques côté client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=fr#developing).

Les étapes de création de fonctions personnalisées sont les suivantes :

1. [Créez une bibliothèque cliente.](#create-client-library)
1. [Ajout d’une bibliothèque cliente à un formulaire adaptatif](#use-custom-function)

### Créez une bibliothèque cliente. {#create-client-library}

Vous pouvez ajouter des fonctions personnalisées en ajoutant une bibliothèque cliente. Pour créer une bibliothèque cliente, procédez comme suit :

**Clonez le référentiel**

Clonez votre référentiel AEM Forms as a Cloud Service [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git) :

1. Ouvrez la ligne de commande ou la fenêtre du terminal.

1. Accédez à l’emplacement souhaité sur votre ordinateur, où vous souhaitez stocker le référentiel.

1. Exécutez la commande suivante pour cloner le référentiel :

   `git clone [Git Repository URL]`

Cette commande télécharge le référentiel et crée un dossier local du référentiel cloné sur votre ordinateur. Tout au long de ce guide, nous nous référons à ce dossier sous le nom de [répertoire de projet AEMaaCS].

**Ajouter un dossier de bibliothèque cliente**

Pour ajouter un nouveau dossier de bibliothèque cliente au [répertoire de projet AEMaaCS], procédez comme suit :

1. Ouvrez le [répertoire de projet AEMaaCS] dans un éditeur.

   ![Structure de dossier de fonction personnalisée](/help/forms/assets/custom-library-folder-structure.png)

1. Localisez `ui.apps`.
1. Ajoutez un nouveau dossier. Par exemple, créez un dossier nommé `experience-league`.
1. Accédez au dossier `/experience-league/` et ajoutez un `ClientLibraryFolder`. Par exemple, créez un dossier de bibliothèque cliente nommé `customclientlibs`.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Ajouter des fichiers et des dossiers au dossier de bibliothèque cliente**

Ajoutez ce qui suit au dossier de bibliothèque cliente ajouté :

* Fichier .content.xml
* fichier js.txt
* dossier js

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Dans `.content.xml`, ajoutez les lignes de code suivantes :

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > Vous pouvez choisir n’importe quel nom pour les propriétés `client library folder` et `categories`.

1. Dans `js.txt`, ajoutez les lignes de code suivantes :

   ```javascript
         #base=js
       function.js
   ```

1. Dans le dossier `js`, ajoutez le fichier javascript en tant que `function.js` qui comprend les fonctions personnalisées :

   ```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */
   
    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();
   
    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();
   
    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }
   
    return age;
    }
   ```

1. Enregistrez les fichiers.

![Structure de dossier de fonction personnalisée](/help/forms/assets/custom-function-added-files.png)

**Incluez le nouveau dossier dans filter.xml** :

1. Accédez au fichier `/ui.apps/src/main/content/META-INF/vault/filter.xml` dans votre [répertoire de projet AEMaaCS].

2. Ouvrez le fichier et ajoutez la ligne suivante à la fin :

   `<filter root="/apps/experience-league" />`
3. Enregistrez le fichier.

![Filtre de fonction personnalisée xml](/help/forms/assets/custom-function-filterxml.png)

**Déployez le dossier de bibliothèque cliente nouvellement créé dans votre environnement AEM**

Déployez l’AEM as a Cloud Service, [répertoire de projet AEMaaCS], dans votre environnement Cloud Service. Pour effectuer un déploiement dans votre environnement Cloud Service :

1. Validez les modifications

   1. Ajoutez, validez et envoyez les modifications dans le référentiel à l’aide des commandes ci-dessous :

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. Déployez le code mis à jour :

   1. Déclenchez un déploiement de votre code via le pipeline full stack existant. Cela crée et déploie automatiquement le code mis à jour.

Si vous n’avez pas encore configuré de pipeline, reportez-vous au guide sur [comment configurer un pipeline pour AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline).

Une fois le pipeline exécuté correctement, la fonction personnalisée ajoutée dans la bibliothèque cliente est disponible dans votre [éditeur de règles de formulaire adaptatif](/help/forms/rule-editor-core-components.md).

### Ajout d’une bibliothèque cliente à un formulaire adaptatif{#use-custom-function}

Une fois que vous avez déployé votre bibliothèque cliente dans votre environnement Forms CS, utilisez ses fonctionnalités dans votre formulaire adaptatif. Pour ajouter la bibliothèque cliente dans votre formulaire adaptatif

1. Ouvrez votre formulaire en mode d’édition. Pour ouvrir un formulaire en mode d’édition, sélectionnez-le et cliquez sur **[!UICONTROL Ouvrir]**.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La boîte de dialogue du conteneur de formulaires adaptatifs s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL De base]** et sélectionnez le nom de la **[!UICONTROL catégorie de bibliothèque cliente]** dans la liste déroulante (dans ce cas, sélectionnez `customfunctionscategory`).

   ![Ajout de la bibliothèque cliente de fonction personnalisée](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > Vous pouvez ajouter plusieurs catégories en spécifiant une liste séparée par des virgules dans le champ **[!UICONTROL Catégorie de bibliothèque cliente]**.

1. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez utiliser la fonction personnalisée dans l’[éditeur de règles d’un formulaire adaptatif](/help/forms/rule-editor-core-components.md) à l’aide des [annotations JavaScript](##js-annotations).

## Utilisation d’une fonction personnalisée dans un formulaire adaptatif

Dans un formulaire adaptatif, vous pouvez utiliser des [fonctions personnalisées dans l’éditeur de règles](/help/forms/rule-editor-core-components.md). Ajoutons le code ci-après au fichier JavaScript (fichier `Function.js`) pour calculer l’âge en fonction de la date de naissance (AAAA-MM-JJ). Créez une fonction personnalisée `calculateAge()` qui prend la date de naissance comme entrée et renvoie l’âge :

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

Dans l’exemple ci-dessus, lorsque la personne saisit la date de naissance au format (AAAA-MM-JJ), la fonction personnalisée `calculateAge` est appelée et renvoie l’âge.

![Fonction personnalisée Calculalte Agae dans l’éditeur de règles](/help/forms/assets/custom-function-calculate-age.png)

Prévisualisons le formulaire pour observer comment les fonctions personnalisées sont implémentées par le biais de l’éditeur de règles :

![Fonction personnalisée Calculate Agae dans l’aperçu du formulaire de l’éditeur de règles](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Vous pouvez vous référer au dossier [fonction personnalisée](/help/forms/assets//customfunctions.zip) suivant. Téléchargez et installez ce dossier dans votre instance AEM à l’aide du [Gestionnaire de modules](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

## Fonctionnalités des fonctions personnalisées

Les fonctions personnalisées d’AEM forms offrent une solution robuste pour étendre et personnaliser les fonctionnalités de vos formulaires. Vous pouvez utiliser les fonctions personnalisées pour répondre aux besoins spécifiques de votre entreprise.

Ces fonctions prennent en charge diverses fonctionnalités, notamment l’utilisation de champs spécifiques, l’utilisation de champs globaux et les opérations asynchrones, ainsi que l’intégration de mécanismes de mise en cache. Cette flexibilité garantit que les formulaires peuvent s’adapter à des exigences complexes et offrir une expérience utilisateur efficace et personnalisée. Grâce à ces fonctionnalités avancées, vous pouvez améliorer les interactions entre les formulaires et optimiser les performances, ce qui rend vos formulaires AEM plus fonctionnels et plus réactifs.

Explorons les fonctionnalités des fonctions personnalisées.

### Prise en charge asynchrone des fonctions personnalisées {#support-of-async-functions}

Vous pouvez implémenter des fonctions asynchrones dans l’éditeur de règles à l’aide de fonctions personnalisées. Pour plus d’informations sur la procédure à suivre, consultez l’article [Utilisation de fonctions asynchrones dans un formulaire adaptatif](/help/forms/using-async-funct-in-rule-editor.md).

### Prise en charge des objets de champ et d’étendue globale dans les fonctions personnalisées {#support-field-and-global-objects}

Les objets de champ font référence aux composants ou éléments individuels d’un formulaire, tels que les champs de texte et les cases à cocher. L’objet Globals contient des variables en lecture seule, telles que l’instance de formulaire, l’instance de champ cible et des méthodes permettant de modifier le formulaire dans des fonctions personnalisées.

>[!NOTE]
>
> Le paramètre `param {scope} globals` doit être le dernier paramètre et il ne s’affiche pas dans l’éditeur de règles d’un formulaire adaptatif.

Pour plus d&#39;informations sur les objets Scope, voir l&#39;article [Objets Scope dans les fonctions personnalisées](/help/forms/custom-function-core-component-scope-function.md).

### Prise en charge de la mise en cache dans une fonction personnalisée

Les formulaires adaptatifs implémentent la mise en cache pour les fonctions personnalisées afin d’améliorer le temps de réponse lors de la récupération de la liste des fonctions personnalisées dans l’éditeur de règles. Un message `Fetched following custom functions list from cache` apparaît dans le fichier `error.log`.

![Fonction personnalisée avec prise en charge du cache](/help/forms/assets/custom-function-cache-error.png)

Si les fonctions personnalisées sont modifiées, la mise en cache est invalidée et elle est analysée.

## Résolution des problèmes

* Si le fichier JavaScript contenant du code pour les fonctions personnalisées comporte une erreur, les fonctions personnalisées ne sont pas répertoriées dans l’éditeur de règles d’un formulaire adaptatif. Pour vérifier la liste des fonctions personnalisées, vous pouvez accéder au fichier `error.log` correspondant à l’erreur. En cas d’erreur, la liste des fonctions personnalisées apparaît vide :

  ![Fichier journal d’erreur](/help/forms/assets/custom-function-list-error-file.png)

  En l’absence d’erreur, la fonction personnalisée est récupérée et apparaît dans le fichier `error.log`. Un message `Fetched following custom functions list` apparaît dans le fichier `error.log` :

  ![Fichier journal d’erreur avec fonction personnalisée appropriée](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Étape suivante

Examinons maintenant divers [exemples de fonctions personnalisées pour un formulaire adaptatif basé sur les composants principaux](/help/forms/custom-function-core-components-use-cases.md).

## Voir également

{{see-also-rule-editor}}

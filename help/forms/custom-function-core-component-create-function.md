---
title: Création et ajout de fonctions personnalisées dans un formulaire adaptatif
description: AEM Forms prend en charge les fonctions personnalisées qui permettent aux utilisateurs de créer et d’utiliser leurs propres fonctions dans l’éditeur de règles.
keywords: Ajoutez une fonction personnalisée, utilisez une fonction personnalisée, créez une fonction personnalisée, utilisez une fonction personnalisée dans l’éditeur de règles.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: e7ab4233-2e91-45c6-9377-0c9204d03ee9
source-git-commit: 747203ccd3c7e428e2afe27c56e47c3ec18699f6
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 7%

---

# Créer une fonction personnalisée pour un formulaire adaptatif basé sur les composants principaux

Les Forms adaptatives basées sur les composants principaux offrent des expériences utilisateur dynamiques en ajustant le contenu et le comportement en fonction des entrées de l’utilisateur. Les fonctions personnalisées permettent aux développeurs d’étendre les fonctionnalités, en s’assurant que les formulaires répondent à des exigences spécifiques. En intégrant des fonctions personnalisées, les développeurs peuvent implémenter une logique complexe, automatiser les processus et introduire des interactions uniques qui correspondent aux besoins spécifiques de l’entreprise ou aux attentes de l’utilisateur. Il permet de s’assurer que les formulaires s’adaptent non seulement à des conditions variées, mais qu’ils offrent également une solution plus précise et plus efficace pour divers cas d’utilisation.
Cet article vous guide tout au long des étapes de création de fonctions personnalisées pour le Forms adaptatif à l’aide des composants principaux.

## Considérations

* `parameter type` et `return type` ne prennent pas en charge `None`.

* Les fonctions qui ne sont pas prises en charge dans la liste des fonctions personnalisées sont les suivantes :
   * Fonctions du générateur
   * Fonctions asynchrones/attendues
   * Définitions des méthodes
   * Méthodes de classe
   * Paramètres par défaut
   * Paramètres REST

## Conditions préalables à la création d’une fonction personnalisée

Avant de commencer à ajouter une fonction personnalisée à votre Forms adaptatif, assurez-vous que vous disposez des éléments suivants :

**Logiciel :**

* **Éditeur de texte brut (IDE)** : bien que tout éditeur de texte brut puisse fonctionner, un environnement de développement intégré (IDE) comme Microsoft Visual Studio Code offre des fonctionnalités avancées pour faciliter la modification.

* **Git :** Ce système de contrôle de version est nécessaire pour gérer les modifications de code. Si vous ne l’avez pas installé, téléchargez-le à partir de https://git-scm.com.


## Créer une fonction personnalisée {#create-custom-function}

Créez une bibliothèque cliente pour appeler des fonctions personnalisées dans l’éditeur de règles. Pour plus d’informations, voir [Utilisation des bibliothèques côté client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=fr#developing).

Les étapes de création de fonctions personnalisées sont les suivantes :
1. [Créez une bibliothèque cliente.](#create-client-library)
1. [Ajout d’une bibliothèque cliente à un formulaire adaptatif](#use-custom-function)

### Créez une bibliothèque cliente. {#create-client-library}

Vous pouvez ajouter des fonctions personnalisées en ajoutant une bibliothèque cliente. Pour créer une bibliothèque cliente, procédez comme suit :

**Cloner le référentiel**

Cloner votre [référentiel as a Cloud Service AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git) :

1. Ouvrez la ligne de commande ou la fenêtre de terminal.

1. Accédez à l’emplacement souhaité sur votre ordinateur où stocker le référentiel.

1. Exécutez la commande suivante pour cloner le référentiel :

   `git clone [Git Repository URL]`

Cette commande télécharge le référentiel et crée un dossier local du référentiel cloné sur votre ordinateur. Dans ce guide, nous nous référons à ce dossier en tant que [répertoire de projet AEMaaCS].

**Ajouter un dossier de bibliothèque cliente**

Pour ajouter un nouveau dossier de bibliothèques clientes au [répertoire de projet AEMaaCS], procédez comme suit :

1. Ouvrez le [répertoire de projet AEMaaCS] dans un éditeur.

   ![Structure de dossier de fonctions personnalisées](/help/forms/assets/custom-library-folder-structure.png)

1. Recherchez `ui.apps`.
1. Ajoutez un nouveau dossier. Par exemple, ajoutez un dossier nommé `experience-league`.
1. Accédez au dossier `/experience-league/` et ajoutez un dossier `ClientLibraryFolder`. Par exemple, créez un dossier de bibliothèques clientes nommé `customclientlibs`.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Ajouter des fichiers et des dossiers au dossier de bibliothèque cliente**

Ajoutez ce qui suit au dossier de bibliothèque cliente ajouté :

* fichier .content.xml
* fichier js.txt
* dossier js

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Dans le `.content.xml`, ajoutez les lignes de code suivantes :

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > Vous pouvez choisir n’importe quel nom pour les propriétés `client library folder` et `categories`.

1. Dans le `js.txt`, ajoutez les lignes de code suivantes :

   ```javascript
         #base=js
       function.js
   ```
1. Dans le dossier `js`, ajoutez le fichier javascript `function.js` qui comprend les fonctions personnalisées :

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

![Structure de dossier de fonctions personnalisées](/help/forms/assets/custom-function-added-files.png)

**Inclure le nouveau dossier dans filter.xml** :

1. Accédez au fichier `/ui.apps/src/main/content/META-INF/vault/filter.xml` dans votre [ répertoire de projet AEMaaCS].

1. Ouvrez le fichier et ajoutez la ligne suivante à la fin :

   `<filter root="/apps/experience-league" />`
1. Enregistrez le fichier.

![filtre de fonction personnalisé xml](/help/forms/assets/custom-function-filterxml.png)

**Déployez le dossier de bibliothèque cliente nouvellement créé dans votre environnement AEM**

Déployez le [répertoire de projet AEMaaCS] d’AEM as a Cloud Service dans votre environnement de Cloud Service. Pour effectuer un déploiement sur votre environnement de Cloud Service :

1. Validez les modifications

   1. Ajoutez, validez et envoyez les modifications dans le référentiel à l’aide des commandes ci-dessous :

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. Déployez le code mis à jour :

   1. Déclenchez un déploiement de votre code par le biais du pipeline de pile complète existant. Cette opération génère et déploie automatiquement le code mis à jour.

Si vous n’avez pas encore configuré de pipeline, reportez-vous au guide sur la configuration d’un pipeline pour AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline).[

Une fois le pipeline exécuté avec succès, la fonction personnalisée ajoutée à la bibliothèque cliente devient disponible dans votre [éditeur de règles de formulaire adaptatif](/help/forms/rule-editor-core-components.md).

### Ajout d’une bibliothèque cliente à un formulaire adaptatif{#use-custom-function}

Une fois que vous avez déployé votre bibliothèque cliente dans votre environnement Forms CS, utilisez ses fonctionnalités dans votre formulaire adaptatif. Pour ajouter la bibliothèque cliente dans votre formulaire adaptatif

1. Ouvrez votre formulaire en mode d’édition. Pour ouvrir un formulaire en mode d’édition, sélectionnez un formulaire et choisissez **[!UICONTROL Modifier]**.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL Basic]** et sélectionnez le nom de la **[!UICONTROL catégorie de bibliothèque cliente]** dans la liste déroulante (dans ce cas, sélectionnez `customfunctionscategory`).

   ![Ajout de la bibliothèque cliente de fonction personnalisée](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > Plusieurs catégories peuvent être ajoutées en spécifiant une liste séparée par des virgules dans le champ **[!UICONTROL Catégorie de bibliothèque cliente]** .

1. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez utiliser la fonction personnalisée dans l’ [ éditeur de règles d’un formulaire adaptatif](/help/forms/rule-editor-core-components.md) à l’aide des [ annotations JavaScript](##js-annotations).

## Utilisation d’une fonction personnalisée dans un formulaire adaptatif

Dans un formulaire adaptatif, vous pouvez utiliser des [fonctions personnalisées dans l’éditeur de règles](/help/forms/rule-editor-core-components.md). Ajoutons le code suivant au fichier JavaScript (`Function.js`) pour calculer l’âge en fonction de la date de naissance (AAAA-MM-JJ). Créez une fonction personnalisée `calculateAge()` qui prend la date de naissance comme entrée et renvoie l’âge :

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

Dans l’exemple ci-dessus, lorsque l’utilisateur saisit la date de naissance au format (AAAA-MM-JJ), la fonction personnalisée `calculateAge` est appelée et renvoie l’âge.

![Fonction personnalisée Calcul de l’âge dans l’éditeur de règles](/help/forms/assets/custom-function-calculate-age.png)

Prévisualisons le formulaire pour observer comment les fonctions personnalisées sont implémentées par le biais de l’éditeur de règles :

![Fonction personnalisée Calcul de l’âge dans l’aperçu de formulaire de l’éditeur de règles](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Vous pouvez vous référer au dossier [custom function](/help/forms/assets//customfunctions.zip) suivant. Téléchargez et installez ce dossier dans votre instance AEM à l’aide du [Gestionnaire de modules](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

## Fonctions des fonctions personnalisées

Les fonctions personnalisées d’AEM forms offrent une solution robuste pour étendre et personnaliser les fonctionnalités de vos formulaires. Vous pouvez utiliser les fonctions personnalisées pour répondre aux besoins spécifiques de votre entreprise.

Ces fonctions prennent en charge diverses fonctionnalités, notamment l’utilisation de champs spécifiques, l’utilisation de champs globaux et d’opérations asynchrones, ainsi que l’incorporation de mécanismes de mise en cache. Cette flexibilité garantit que les formulaires peuvent s’adapter à des exigences complexes et offrir une expérience utilisateur efficace et personnalisée. En exploitant ces fonctionnalités avancées, vous pouvez améliorer les interactions des formulaires et optimiser les performances, rendant vos formulaires AEM plus fonctionnels et réactifs.

Explorons les fonctionnalités des fonctions personnalisées.

### Prise en charge asynchrone dans les fonctions personnalisées {#support-of-async-functions}

Vous pouvez implémenter des fonctions asynchrones dans l’éditeur de règles à l’aide de fonctions personnalisées. Pour plus d’informations sur la procédure à suivre, reportez-vous à l’article [Utilisation de fonctions asynchrones dans un formulaire adaptatif](/help/forms/using-async-funct-in-rule-editor.md).

### Prise en charge des objets de champ et de portée globale dans les fonctions personnalisées {#support-field-and-global-objects}

Les objets de champ font référence aux composants ou éléments individuels d’un formulaire, tels que les champs de texte et les cases à cocher. L’objet Globals contient des variables en lecture seule, telles que l’instance de formulaire, l’instance de champ cible et des méthodes permettant de modifier le formulaire dans des fonctions personnalisées.

>[!NOTE]
>
> `param {scope} globals` doit être le dernier paramètre et il ne s’affiche pas dans l’éditeur de règles d’un formulaire adaptatif.

Pour plus d’informations sur les objets de portée, consultez l’article [Objets de portée dans les fonctions personnalisées](/help/forms/custom-function-core-component-scope-function.md) .

### Prise en charge de la mise en cache dans une fonction personnalisée

Les Forms adaptatives implémentent la mise en cache pour les fonctions personnalisées afin d’améliorer le temps de réponse lors de la récupération de la liste des fonctions personnalisées dans l’éditeur de règles. Un message tel que `Fetched following custom functions list from cache` apparaît dans le fichier `error.log`.

![fonction personnalisée avec prise en charge du cache](/help/forms/assets/custom-function-cache-error.png)

Si les fonctions personnalisées sont modifiées, la mise en cache est invalidée et elle est analysée.

## Résolution des problèmes

* Si le fichier JavaScript contenant du code pour les fonctions personnalisées comporte une erreur, les fonctions personnalisées ne sont pas répertoriées dans l’éditeur de règles d’un formulaire adaptatif. Pour vérifier la liste des fonctions personnalisées, vous pouvez accéder au fichier `error.log` correspondant à l’erreur. En cas d’erreur, la liste des fonctions personnalisées apparaît vide :

  ![fichier journal d’erreur](/help/forms/assets/custom-function-list-error-file.png)

  En l’absence d’erreur, la fonction personnalisée est récupérée et apparaît dans le fichier `error.log`. Un message sous la forme `Fetched following custom functions list` apparaît dans le fichier `error.log` :

  ![ fichier journal d&#39;erreur avec fonction personnalisée appropriée](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Étape suivante

Nous allons maintenant voir divers [exemples de fonctions personnalisées pour un formulaire adaptatif basé sur les composants principaux](/help/forms/custom-function-core-components-use-cases.md).

## Voir également

{{see-also-rule-editor}}

---
title: Utilitaire de migration pour convertir les Forms adaptatives basées sur des composants de base en formulaires basés sur des composants principaux
description: Découvrez comment installer et utiliser l’utilitaire de migration pour convertir les Forms adaptatifs basés sur les composants Foundation en formulaires basés sur des composants principaux.
Keywords: Migration Utility tool, Convert Adaptive Forms based on foundation components to core component based forms, Convert Foundation forms to Core components forms, Using Modernizer tool to convert Foundation Components to Core components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 6%

---


# Présentation

Vous pouvez utiliser l’utilitaire de migration pour convertir les Forms adaptatives basées sur des composants de base en formulaires basés sur des composants principaux. Vous pouvez utiliser la variable [AEM l’outil de modernisation](https://opensource.adobe.com/aem-modernize-tools/) comme outil utilitaire de migration. La variable [AEM des outils de modernisation](https://opensource.adobe.com/aem-modernize-tools/) fournissent une suite d’utilitaires utilisés pour convertir les Forms adaptatives en fonction des composants de base en fonctionnalités modernes et prises en charge par les composants principaux.

## Qu’est-ce qu’AEM les outils de modernisation ?

[AEM des outils de modernisation](https://opensource.adobe.com/aem-modernize-tools/) fait référence à un ensemble d’utilitaires ou d’applications logicielles conçus pour faciliter le processus de modernisation ou de mise à jour des projets Adobe Experience Manager (AEM). Ces outils permettent généralement de convertir des composants ou des fonctionnalités plus anciens d’AEM en solutions plus récentes, plus efficaces et plus prises en charge.

AEM les outils de modernisation convertissent les Forms adaptatifs basés sur des composants de base plus anciens en formulaires basés sur des composants principaux plus récents. Ce processus de conversion permet de s’assurer que les formulaires s’alignent sur les normes et fonctionnalités modernes, améliorant ainsi les performances, la compatibilité et la facilité de maintenance de l’environnement AEM.

![AEM des outils de modernisation](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> Il est recommandé d’installer les outils de modernisation d’AEM sur votre configuration AEM locale. Migrez les formulaires basés sur les bases vers des formulaires basés sur des composants principaux. Téléchargez le formulaire avec ses ressources. Ensuite, chargez le formulaire et ses actifs dans l’environnement requis.

## Conditions préalables à l’utilisation des outils de modernisation d’AEM

* [Configuration de l’environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md)
* [Activez les composants principaux de Forms adaptatif pour votre environnement.](/help/forms/enable-adaptive-forms-core-components.md)

* Ajoutez vos utilisateurs au [!DNL forms-users] groupe. Les membres du groupe [!DNL forms-users] sont autorisés à créer un formulaire adaptatif.

* Les utilisateurs disposant des rôles suivants sont autorisés à installer les outils de modernisation d’AEM dans un environnement AEM :
   * Rôle de développeur
   * Rôle d’administrateur Pour obtenir une liste détaillée des groupes d’utilisateurs spécifiques aux formulaires, voir [Groupes et autorisations](forms-groups-privileges-tasks.md).

## Installation et configuration des outils de modernisation d’AEM

Étapes d’installation et de configuration des outils de modernisation d’AEM :

1. [Installer les outils de modernisation AEM dans votre environnement AEM Forms local](#install-aem-modernize-tools)
2. [Activation des outils de modernisation d’AEM pour votre environnement AEM Forms local](#enable-aem-modernize-tools)

### Installer les outils de modernisation AEM dans votre environnement AEM Forms local {#install-aem-modernize-tools}

Effectuez les étapes suivantes pour installer AEM Modernize Tools dans votre environnement AEM Forms local :

1. Démarrez le service de création AEM local en exécutant les éléments suivants à partir de la ligne de commande :

   `java -jar aem-author-p4502.jar`

   >[!NOTE]
   >
   > Indiquez le mot de passe d’administration `admin`. Tout mot de passe administrateur est acceptable, mais il est recommandé d’utiliser la valeur par défaut pour le développement local afin de réduire la nécessité de reconfigurer.

1. Cloner le [AEM des outils de modernisation](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) dans votre système local.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tools]
   ```
   Remplacez la variable [Chemin du référentiel Git des outils de modernisation d’AEM] avec l’URL réelle du référentiel Git correspondant des outils de modernisation AEM.
Une fois la commande exécutée correctement, vous disposez d’une copie locale du référentiel des outils de modernisation d’AEM disponible sur votre ordinateur.

1. Accédez au`[AEM Modernize Tools Repository]`  dans votre système local.
1. Exécutez la commande suivante :

   ```Shell
       mvn clean install 
   ```
![Image d’installation réussie](/help/forms/assets/aem-modernize-install-steps.png)

Une fois l’installation terminée, les outils de modernisation d’AEM deviennent disponibles pour votre environnement.

![Activation des outils de modernisation d’AEM](/help/forms/assets/enable-aem-modernizer-tools.png)


### Activation des outils de modernisation d’AEM pour votre environnement AEM Forms local{#enable-aem-modernize-tools}

Pour activer et utiliser les outils de modernisation AEM de votre environnement AEM, il est important de mettre en correspondance les règles de migration des composants de base vers les composants principaux :

1. Connectez-vous à votre instance d’auteur.
1. Accédez à `http://[host]:[port]/system/console/configMgr`.
1. Recherchez et modifiez les `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Ajoutez la variable `Component Rule Paths` as `/apps/forms-modernizer/rules`.
1. Cliquez sur **Enregistrer** pour enregistrer les modifications.

![AEM Actualiser la règle de composant](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Exécutez AEM des outils de modernisation pour convertir des formulaires basés sur des composants de base en formulaires basés sur des composants de base.

1. Accédez à **[!UICONTROL Outils > AEM Moderniser les outils > Conversion Forms]**.

   ![Sélection des outils de modernisation d’AEM](/help/forms/assets/aem-modernize-tools-select.png)

1. Sélectionnez la variable **[!UICONTROL Conversion Forms]** .

   ![Sélectionner l’option de conversion Forms](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Cliquez sur **Créer** pour créer une tâche.

   ![AEM des outils de modernisation Créer une tâche](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Spécifiez la variable **[!UICONTROL Job Name]**.
1. Dans le **[!UICONTROL Formulaire]** vous pouvez sélectionner l’une des options suivantes :
   * **Aucun** : sélectionnez cette option si la gestion des formulaires n’est pas requise.
   * **Restaurer** : sélectionnez cette option pour rétablir l’état du formulaire avant la dernière conversion.
   * **Copier vers Target**: sélectionnez cette option pour copier le formulaire avant d’effectuer la conversion.
Dans notre cas, la variable **Copier vers Target** est sélectionnée. Si la variable **Copier vers Target** est sélectionnée, la variable **[!UICONTROL Chemin source]** et **[!UICONTROL Chemin cible]** les options deviennent visibles.

1. Spécifiez la variable `source folder` dans le champ **[!UICONTROL Chemin source]**.
1. Spécifiez la variable `target folder` dans le champ **[!UICONTROL Chemin cible]**.
1. Sélectionnez **[!UICONTROL Suivant]**.
1. Cliquez sur **[!UICONTROL Ajouter Forms]**. Tous les formulaires du `source folder` s’affiche à l’écran.
1. Sélectionnez le formulaire en fonction des composants de base pour le convertir en formulaire en fonction des composants principaux. Vous pouvez également sélectionner plusieurs formulaires.

   ![AEM des outils de modernisation Sélection d’un formulaire](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Cliquez sur **[!UICONTROL Sélectionner]**.
1. Cliquez sur **[!UICONTROL Planification de la tâche]** pour lancer le processus de conversion.
1. Cliquez sur **[!UICONTROL Convertir]** de la **[!UICONTROL Convertir les pages]** de la boîte de dialogue

   ![AEM Moderniser les outils Convertir les pages](/help/forms/assets/aem-modernize-tools-convert-form.png)

   Lorsque l’état du processus est modifié en `success`. Accédez au `target folder` pour afficher le formulaire converti.

   ![AEM Moderniser la réussite des outils](/help/forms/assets/aem-modernize-tools-success.png)

1. Sélectionnez le formulaire adaptatif et choisissez > **[!UICONTROL Propriétés]**. La page Propriétés du formulaire s’ouvre.
   ![AEM Moderniser le dossier de destination des outils](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Sélectionner **[!UICONTROL Enregistrer et fermer]** pour enregistrer à nouveau les propriétés du formulaire converti.
   ![AEM Moderniser les outils Propriétés du formulaire adaptatif](/help/forms/assets/aem-modernize-tools-af-properties.png)

Vous pouvez maintenant constater que le formulaire adaptatif créé à partir de composants de base se transforme en formulaire adaptatif créé à partir de composants principaux.

## Remarques concernant l’utilisation de l’outil utilitaire de migration {#considerations}

* Si le formulaire créé à partir de composants de base contient des règles de fonction personnalisées, vous devez réécrire ces règles pour le formulaire converti en fonction des composants principaux.
* Le formulaire converti n’inclut aucune règle dans l’éditeur de règles, ce qui nécessite la réécriture des règles pour le formulaire converti.
* Vous devez recréer la tâche de traduction du formulaire converti.

## Bonnes pratiques {#best-practices}

* Le formulaire créé à partir des composants de base inclut uniquement les composants trouvés dans les composants de base.
* Assurez-vous que les règles sont formatées au format XML.



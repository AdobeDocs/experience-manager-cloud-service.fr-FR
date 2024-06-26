---
title: Outil de l’utilitaire de migration/AEM des outils de modernisation pour convertir des Forms adaptatifs basés sur des composants de base en formulaires basés sur des composants principaux
description: Découvrez comment installer et utiliser l’utilitaire de migration/AEM des outils de modernisation pour convertir les Forms adaptatifs basés sur les composants de base en formulaires basés sur les composants principaux.
Keywords: Migration Utility Tool, Convert Adaptive Forms based on Foundation Components to Core Component based forms, Convert Foundation forms to Core Components forms, Using Modernizer Tool to convert Foundation Components to Core Components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
exl-id: ee71a576-96a7-4c81-b3a3-1d678f010cba
feature: Adaptive Forms, Core Components
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 4%

---

# Présentation

L’utilitaire de conversion Forms, composant de [Outil de modernisation d’AEM](https://opensource.adobe.com/aem-modernize-Tools/) vous aide à convertir facilement les Forms adaptatives créées avec des composants de base hérités en formulaires qui tirent parti des fonctionnalités modernes et prises en charge des composants principaux.

## Qu’est-ce qu’AEM les outils de modernisation ?

[AEM des outils de modernisation](https://opensource.adobe.com/aem-modernize-Tools/) fait référence à un ensemble d’utilitaires ou d’applications logicielles conçus pour faciliter le processus de modernisation ou de mise à jour des projets Adobe Experience Manager (AEM). En règle générale, ces outils permettent de convertir des composants ou des fonctionnalités plus anciens d’AEM en solutions plus récentes, plus efficaces et plus prises en charge. L’utilitaire de conversion Forms est installé sous AEM Outils de modernisation afin de convertir les Forms adaptatifs basés sur des composants de base en formulaires basés sur des composants principaux.

L’utilitaire de conversion de Forms convertit les Forms adaptatifs basés sur des composants de base plus anciens en formulaires basés sur des composants principaux plus récents. Ce processus de conversion permet de s’assurer que les formulaires s’alignent sur les normes et fonctionnalités modernes, améliorant ainsi les performances, la compatibilité et la facilité de maintenance de l’environnement AEM.

![AEM des outils de modernisation](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
> Il est recommandé d’installer les outils de modernisation d’AEM sur votre configuration AEM locale. Migrez le Forms adaptatif basé sur les composants de base vers les formulaires basés sur les composants principaux. Téléchargez le formulaire avec ses ressources. Ensuite, chargez le formulaire et ses actifs dans l’environnement requis.

## Considérations relatives à l’utilisation des outils de modernisation d’AEM {#considerations}

* Lors de conversions réussies, toutes les règles appliquées au formulaire sont supprimées. Les règles ne sont pas migrées automatiquement. Vous devez recréer et appliquer manuellement ces règles au formulaire converti.
* Les paramètres de traduction utilisés dans le formulaire d’origine ne sont pas reportés. Reconfigurez la traduction du formulaire converti.
  <!-- * If the form built on Foundation Components contains custom function rules, you have to rewrite these rules for the converted form based on Core Components.-->

## Conditions préalables à l’utilisation des outils de modernisation d’AEM

* [Configuration de l’environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md)
* [Activez les composants principaux de Forms adaptatif pour votre environnement.](/help/forms/enable-adaptive-forms-core-components.md)

* Ajoutez vos utilisateurs au [!DNL forms-users] groupe. Les membres du groupe [!DNL forms-users] sont autorisés à créer un formulaire adaptatif.

* Les utilisateurs disposant des rôles suivants sont autorisés à installer les outils de modernisation d’AEM dans un environnement AEM :
   * Rôle de développeur
   * Rôle d’administrateur

Pour obtenir la liste détaillée des groupes d’utilisateurs spécifiques aux formulaires, voir [Groupes et autorisations](forms-groups-privileges-tasks.md).

## Installation et configuration des outils de modernisation d’AEM

Pour installer et configurer les outils de modernisation d’AEM :

1. [Installer les outils de modernisation AEM dans votre environnement AEM Forms local](#install-aem-modernize-Tools)
2. [Activation des outils de modernisation d’AEM pour votre environnement AEM Forms local](#enable-aem-modernize-Tools)

### Installer les outils de modernisation AEM dans votre environnement AEM Forms local {#install-aem-modernize-Tools}

Effectuez les étapes suivantes pour installer AEM Modernize Tools dans votre environnement AEM Forms local :

1. Ouvrez l’invite de commande ou le terminal.
1. Démarrez le service d’auteur d’AEM local. Par exemple, exécutez le code suivant à partir du pour démarrer l’instance d’auteur AEM locale :

   `java -jar aem-author-p4502.jar`

1. Cloner le [Outil de modernisation d’AEM](https://git.corp.adobe.com/livecycle/forms-modernizer/tree/convertForms) dans votre système local.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Une fois la commande exécutée correctement, vous disposez d’une copie locale du référentiel de l’outil de modernisation d’AEM disponible sur votre ordinateur.

1. Accédez au`[AEM Modernize Tool Repository]`  dans votre système local.
1. Exécutez la commande suivante :

   ```Shell
       mvn clean install 
   ```
![Image d’installation réussie](/help/forms/assets/aem-modernize-install-steps.png)

Une fois l’installation terminée, les outils de modernisation d’AEM sont disponibles pour votre environnement.

![Activer l’outil utilitaire de migration AEM](/help/forms/assets/enable-aem-modernizer-tools.png)


### Activation des outils de modernisation d’AEM pour votre environnement AEM Forms local{#enable-aem-modernize-Tools}

Pour activer et utiliser les outils de modernisation AEM de votre environnement AEM, il est important de mettre en correspondance les règles de migration des composants de base vers les composants principaux :

1. Connectez-vous à votre instance d’auteur.
1. Accédez à `http://[host]:[port]/system/console/configMgr`.
1. Recherchez et modifiez les `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Ajoutez la variable `Component Rule Paths` as `/apps/forms-modernizer/rules`.
1. Cliquez sur **Enregistrer** pour enregistrer les modifications.

![AEM Actualiser la règle de composant](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Exécutez l’utilitaire de conversion de formulaire pour convertir des formulaires basés sur des composants Foundation en formulaires basés sur des composants principaux.

1. Accédez à **[!UICONTROL Outils > AEM Moderniser les outils > Conversion Forms]**.

   ![Sélectionnez AEM des outils de modernisation](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Sélectionnez la variable **[!UICONTROL Conversion Forms]** .

   ![Sélectionner l’option de conversion Forms](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Cliquez sur **Créer** pour créer une tâche.

   ![AEM des outils de modernisation Créer une tâche](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Spécifiez la variable **[!UICONTROL Job Name]**.
1. Dans le **[!UICONTROL Formulaire]** vous pouvez sélectionner l’une des options suivantes :
   * **Aucun** : sélectionnez cette option si vous ne souhaitez pas créer de copie des formulaires basés sur les composants de base avant de commencer la conversion du formulaire.
   * **Restaurer** : sélectionnez l’option pour restaurer le formulaire à son état avant de commencer la conversion.
   * **Copier vers Target**: sélectionnez l’option permettant de créer une copie des formulaires basés sur le composant Foundation avant de commencer la conversion du formulaire.
Dans notre cas, la variable **Copier vers Target** est sélectionnée. Si la variable **Copier vers Target** est sélectionnée, la variable **[!UICONTROL Chemin Source]** et **[!UICONTROL Chemin cible]** les options deviennent visibles.

1. Spécifiez la variable `source folder` dans le champ **[!UICONTROL Chemin Source]**.
1. Spécifiez la variable `target folder` dans le champ **[!UICONTROL Chemin cible]**.
1. Sélectionnez **[!UICONTROL Suivant]**.
1. Cliquez sur **[!UICONTROL Ajouter Forms]**. Tous les formulaires du `source folder` s’affiche à l’écran.
1. Sélectionnez le Forms adaptatif basé sur les composants de base pour le convertir en formulaires basés sur les composants principaux. Vous pouvez également sélectionner plusieurs formulaires.

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

Vous pouvez maintenant constater que le formulaire adaptatif créé à partir des composants de base se transforme en formulaire adaptatif créé à partir des composants principaux.

## Bonnes pratiques {#best-practices}

* Assurez-vous que vos formulaires basés sur des composants de base utilisent uniquement les composants qui ont un équivalent [Composants principaux](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) disponible. Dans les cas où vous utilisez des composants de base qui n’ont pas de composant principal équivalent, le composant de base n’est pas converti. Il ne fonctionne donc pas correctement lors de la création d’un formulaire.
* Assurez-vous que les règles de couverture des composants de base vers les composants principaux sont formatées en XML.

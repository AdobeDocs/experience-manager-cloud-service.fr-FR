---
title: Utilitaire de migration Tool/AEM Modernize Tools pour convertir les formulaires Forms adaptatifs basés sur les composants de base en formulaires basés sur les composants principaux
description: Découvrez comment installer et utiliser les outils de modernisation de l’utilitaire de migration/AEM pour convertir les formulaires Forms adaptatifs basés sur les composants de base en formulaires basés sur les composants principaux.
Keywords: Migration Utility Tool, Convert Adaptive Forms based on Foundation Components to Core Component based forms, Convert Foundation forms to Core Components forms, Using Modernizer Tool to convert Foundation Components to Core Components in forms.
role: User, Developer, Admin
features: core components
hide: true
hidefromtoc: true
exl-id: ee71a576-96a7-4c81-b3a3-1d678f010cba
feature: Adaptive Forms, Core Components
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 8%

---

# Présentation

<span class="preview"> Cette fonctionnalité est disponible dans le cadre du programme des utilisateurs et utilisatrices précoces. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

L’utilitaire de conversion Forms, qui fait partie de la suite [Outil de modernisation AEM](https://opensource.adobe.com/aem-modernize-tools/), vous aide à convertir facilement des Forms adaptatifs créés avec des composants de base hérités en formulaires qui tirent parti des fonctionnalités modernes et prises en charge des composants principaux.

## En quoi consistent les outils de modernisation d’AEM ?

[Outils de modernisation AEM](https://opensource.adobe.com/aem-modernize-tools/) désigne un ensemble d&#39;utilitaires ou d&#39;applications logicielles conçus pour faciliter le processus de modernisation ou de mise à jour des projets Adobe Experience Manager (AEM). Ces outils aident généralement à convertir les anciens composants ou fonctionnalités d’AEM en solutions de remplacement plus récentes, plus efficaces et prises en charge. L’utilitaire de conversion Forms est installé sous AEM Modernize Tools pour convertir les formulaires adaptatifs Forms basés sur les composants de base en formulaires basés sur les composants principaux.

L’utilitaire de conversion Forms convertit les Forms adaptatifs basés sur d’anciens composants de base en formulaires plus récents basés sur les composants principaux. Ce processus de conversion garantit que les formulaires s’alignent sur les normes et fonctionnalités modernes, ce qui peut améliorer les performances, la compatibilité et la facilité de maintenance dans l’environnement AEM.

![Outils de modernisation AEM](/help/forms/assets/aem-modernize-tools.png)

>[!NOTE]
> 
>Il est recommandé d’installer les outils de modernisation AEM sur votre configuration AEM locale. Migrez le Forms adaptatif basé sur les composants de base vers les formulaires basés sur les composants principaux. Téléchargez le formulaire avec ses ressources. Ensuite, chargez le formulaire et ses ressources dans l’environnement requis.

## Remarques concernant l’utilisation des outils de modernisation d’AEM {#considerations}

* Une fois les conversions réussies, toutes les règles appliquées au formulaire sont supprimées. Les règles ne sont pas automatiquement migrées. Vous devez recréer et appliquer manuellement ces règles au formulaire converti.
* Les paramètres de traduction utilisés dans le formulaire d’origine ne sont pas transférés. Reconfigurez la traduction pour le formulaire converti.
* Si le formulaire créé sur les composants de base contient des scripts ou des règles de fonction personnalisées, vous devez les réécrire pour le formulaire converti basé sur les composants principaux.
* Les composants de base prêts à l’emploi suivants ne sont pas encore pris en charge dans les composants principaux et sont donc supprimés dans le formulaire converti :

   * Bloc Adobe Sign
   * Graphique
   * Liste des pièces jointes
   * Espace réservé de note de bas de page
   * Choix d’image
   * Bouton Suivant
   * Bouton Précédent
   * Signature tactile
   * Étape de résumé
   * Barre d’outils

## Conditions préalables à l’utilisation des outils de modernisation d’AEM

* [Configuration d’un environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md).
* [Activation des composants principaux des formulaires adaptatifs pour votre environnement](/help/forms/enable-adaptive-forms-core-components.md).
* Ajoutez vos utilisateurs au groupe [!DNL forms-users]. Les membres du groupe [!DNL forms-users] sont autorisés à créer un formulaire adaptatif.
* Les utilisateurs et utilisatrices disposant des rôles suivants sont autorisés à installer les outils de modernisation d’AEM dans un environnement AEM :

   * Rôle de développeur
   * Rôle d’administrateur

Pour obtenir une liste détaillée des groupes d’utilisateurs spécifiques aux formulaires, voir [Groupes et autorisations](forms-groups-privileges-tasks.md).

## Installation et configuration des outils de modernisation d’AEM

Pour installer et configurer les outils de modernisation d’AEM :

1. [Installation des outils de modernisation d’AEM dans votre environnement AEM Forms local](#install-aem-modernize-Tools)
1. [Activation des outils de modernisation AEM pour votre environnement AEM Forms local](#enable-aem-modernize-Tools)

### Installation des outils de modernisation d’AEM dans votre environnement AEM Forms local {#install-aem-modernize-Tools}

Pour installer les outils de modernisation d’AEM dans votre environnement AEM Forms local, procédez comme suit :

1. Ouvrez l’invite de commande ou le terminal.
1. Démarrez le service de création AEM local. Par exemple, exécutez le code suivant à partir de pour démarrer l’instance d’auteur AEM locale :

   `java -jar aem-author-p4502.jar`

1. Clonez le référentiel [Outil de modernisation AEM](https://github.com/adobe/forms-modernizer) dans votre système local.

   ```Shell
   git clone [Path of Git repository of AEM Modernize Tool]
   ```

   Une fois la commande exécutée, une copie locale du référentiel de l’outil de modernisation AEM est disponible sur votre ordinateur.

1. Accédez à l’`[AEM Modernize Tool Repository]` dans votre système local.
1. Exécutez la commande suivante :

   ```Shell
       mvn clean install 
   ```

![Image d’installation réussie](/help/forms/assets/aem-modernize-install-steps.png)

Une fois l’installation terminée, les outils de modernisation d’AEM sont disponibles pour votre environnement.

![Activer l’outil AEM Migration Utility](/help/forms/assets/enable-aem-modernizer-tools.png)


### Activation des outils de modernisation AEM pour votre environnement AEM Forms local{#enable-aem-modernize-Tools}

Pour activer et utiliser les outils de modernisation AEM pour votre environnement AEM, il est important de mapper les règles de migration des composants de base aux composants principaux :

1. Connectez-vous à votre instance de création.
1. Accédez à `http://[host]:[port]/system/console/configMgr`.
1. Recherchez et modifiez le `AEM Modernize Tools - Component Rewrite Rule Service`.
1. Ajoutez le `Component Rule Paths` en tant que `/apps/forms-modernizer/rules`.
1. Cliquez sur **Enregistrer** pour enregistrer les modifications.

![Règle De Composant Modernisation AEM](/help/forms/assets/aem-modernize-tools-component-rule.png)

## Exécutez l’utilitaire de conversion de formulaire pour convertir les formulaires basés sur les composants de base en formulaires basés sur les composants principaux

1. Accédez à **[!UICONTROL Outils > Outils de modernisation AEM > Conversion Forms]**.

   ![Sélectionnez Outils de modernisation AEM](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Sélectionnez l’option **[!UICONTROL Conversion Forms]**.

   ![Sélectionnez l’option Conversion Forms ](/help/forms/assets/aem-modernize-forms-conversion.png)

1. Cliquez sur **Créer** pour créer une tâche.

   ![Création d’un travail à l’aide des outils de modernisation d’AEM](/help/forms/assets/aem-modernize-tools-create-job.png)

1. Spécifiez le **[!UICONTROL Nom de la tâche]**.
1. Dans l’onglet **[!UICONTROL Formulaire]**, vous pouvez sélectionner l’une des options suivantes :

   * **Aucun** : sélectionnez cette option si vous ne souhaitez pas créer de copie des formulaires basés sur les composants de base avant de démarrer la conversion du formulaire.
   * **Restaurer** : sélectionnez cette option pour restaurer le formulaire à l’état dans lequel il se trouvait avant de démarrer la conversion du formulaire.
   * **Copier dans la cible** : sélectionnez cette option pour créer une copie des formulaires basés sur le composant de base avant de démarrer la conversion du formulaire.

   Dans notre cas, l’option **Copier dans Target** est sélectionnée. Si l’option **Copier dans la cible** est sélectionnée, les options **[!UICONTROL Chemin Source]** et **[!UICONTROL Chemin cible]** deviennent visibles.

1. Spécifiez le nom du `source folder` dans le chemin d’accès **[!UICONTROL Source]**.
1. Indiquez le nom de la `target folder` dans le **[!UICONTROL Chemin cible]**.
1. Sélectionnez **[!UICONTROL Suivant]**.
1. Cliquez sur **[!UICONTROL Ajouter Forms]**. Tous les formulaires du `source folder` s’affichent à l’écran.
1. Sélectionnez le Forms adaptatif basé sur les composants de base pour le convertir en formulaires basés sur les composants principaux. Vous pouvez également sélectionner plusieurs formulaires.

   ![Formulaire de sélection des outils de modernisation AEM](/help/forms/assets/aem-modernize-tools-select-form.png)

1. Cliquez sur **[!UICONTROL Sélectionner]**.
1. Cliquez sur **[!UICONTROL Planifier la tâche]** pour lancer le processus de conversion.
1. Cliquez sur **[!UICONTROL Convertir]** dans la boîte de dialogue **[!UICONTROL Convertir les pages]**.

   ![Outils de modernisation AEM Convertir les pages](/help/forms/assets/aem-modernize-tools-convert-form.png)

   Lorsque le statut du processus est modifié en `success`. Accédez à la `target folder` pour afficher le formulaire converti.

   ![Succès des outils de modernisation AEM](/help/forms/assets/aem-modernize-tools-success.png)

1. Sélectionnez le formulaire adaptatif, puis sélectionnez > **[!UICONTROL Propriétés]**. La page Propriétés du formulaire s’ouvre.

   ![Dossier de destination des outils de modernisation AEM](/help/forms/assets/aem-modernize-tools-destination-folder.png)

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer à nouveau les propriétés du formulaire converti.
   ![Propriétés des formulaires adaptatifs des outils de modernisation AEM](/help/forms/assets/aem-modernize-tools-af-properties.png)

Vous pouvez maintenant voir que le formulaire adaptatif créé sur les composants de base se transforme en formulaire adaptatif créé sur les composants principaux.

## Bonnes pratiques {#best-practices}

* Assurez-vous que vos formulaires basés sur les composants de base utilisent uniquement les composants disposant d’un [Composants principaux](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type) équivalent. Si vous utilisez des composants de base qui n’ont pas de composant principal équivalent, le composant de base n’est pas converti. Par conséquent, il ne fonctionne pas correctement lors de la création d’un formulaire
* Assurez-vous que les règles de conversion des composants de base en composants principaux sont au format XML.

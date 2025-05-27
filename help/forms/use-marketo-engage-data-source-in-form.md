---
Title: How to configure Marketo Engage data for Adaptive Forms?
Description: Learn how to use Marketo Engage schema in Adaptive Forms.
Keywords: Use Marketo Engage data source in Adaptive Forms, How to connect a Marketo instance data source with form? , Connect a form to Marketo.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 4656ec65-f1ad-4e97-8d93-25933cdc7f7b
source-git-commit: e46c5afac945620cc44e9064956848acecc786bf
workflow-type: ht
source-wordcount: '463'
ht-degree: 100%

---

# Configurer la source de données Marketo Engage pour les formulaires adaptatifs existants

<span class="preview"> Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

![Workflow](/help/forms/assets/workflow-marketo-2.png)

Après avoir créé la configuration du service cloud pour intégrer Marketo Engage à la configuration AEM Forms existante, vous pouvez configurer la source de données pour les formulaires.

La configuration de l’intégration de données permet aux utilisateurs et utilisatrices de se connecter à divers schémas ou sources de données. L’intégration à la source de données Marketo Engage et son utilisation dans différents formulaires facilite les opérations sur ces données. Pour explorer les sources de données prêtes à l’emploi prises en charge pour un formulaire adaptatif, reportez-vous à l’article [Configurer les sources de données](/help/forms/configure-data-sources.md).

## Remarque concernant la configuration de la source de données Marketo Engage pour les formulaires

Lors de la configuration de la source de données Marketo Engage pour les formulaires, tenez compte des points suivants :

* Il n’est pas possible de connecter des formulaires Edge Delivery Services à Marketo Engage.

## Condition préalable pour utiliser la source de données Marketo Engage pour les formulaires

Condition préalable pour utiliser la source de données Marketo Engage avec les formulaires :

* Créez la [configuration du service cloud pour intégrer Marketo Engage aux formulaires](/help/forms/integrate-form-to-marketo-engage.md).

## Comment configurer un formulaire adaptatif existant pour la source de données Marketo Engage ?

>[!VIDEO](https://video.tv.adobe.com/v/3442871/marketo-aem-forms-aem-marketo-engage)

Pour configurer un formulaire adaptatif avec la source de données Marketo Engage, procédez comme suit :
1. Connectez-vous à votre instance de création [!DNL Experience Manager Forms].

2. Ouvrez le formulaire adaptatif pour le modifier.
3. Ouvrez l’arborescence de contenu et sélectionnez le **[!UICONTROL conteneur de guide]**.
4. Cliquez sur l’icône des propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue Conteneur de formulaire adaptatif pour configurer les sources de données s’ouvre.
5. Ouvrez l’onglet **[!UICONTROL Modèle de données]** et sélectionnez un modèle de formulaire en tant que **Connecteur**.
6. Sélectionnez le **[!UICONTROL Connecteur]** dans la liste déroulante.

7. Après avoir sélectionné le **[!UICONTROL Connecteur]**, vous pouvez sélectionner la configuration cloud.

   ![Sélection du connecteur Marketo](/help/forms/assets/select-marketo-connector.png)

   Selon la configuration Marketo Engage sélectionnée, les éléments de formulaire sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL Explorateur de contenu]** dans la barre latérale. Vous pouvez faire glisser et déposer ces éléments pour créer votre formulaire adaptatif.

   ![Source de données Marketo](/help/forms/assets/marketo-engage-data-source.png)

8. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier sa configuration associée.

Le formulaire adaptatif est maintenant configuré avec la source de données de l’instance Marketo Engage connectée. Maintenant, configurez-le pour envoyer des données à Adobe Marketo Engage.

## Questions fréquentes

**Q : que se passe-t-il lors de la modification du connecteur du formulaire ?**\
**R :** si vous modifiez le connecteur du formulaire, les liaisons existantes ne sont plus valides.

**Q : quelles sont les trois opérations disponibles dans le service d’appel de l’éditeur de règles pour les formulaires intégrés à Marketo Engage ?**\
**R :** les trois opérations prêtes à l’emploi disponibles dans le **service d’appel** pour les formulaires intégrés à Marketo Engage sont les suivantes :
* Synchroniser le lead
* Obtenir le lead par ID
* Obtenir le lead par type de filtre

## Étape suivante

Vous avez maintenant configuré la source de données Marketo Engage pour les formulaires adaptatifs. Vous pouvez ensuite [configurer un formulaire adaptatif pour envoyer des données à Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md).

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}

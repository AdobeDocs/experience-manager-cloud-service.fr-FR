---
Title: How to configure Marketo Engage data for Adaptive Forms?
Description: Learn how to use Marketo Engage schema in Adaptive Forms.
Keywords: Use Marketo Engage data source in Adaptive Forms, How to connect a Marketo instance data source with form? , Connect a form to Marketo.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 12%

---


# Configuration de la source de données du Marketo Engage pour le Forms adaptatif existant

<span class="preview"> La fonctionnalité est disponible dans le cadre du programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

![Workflow](/help/forms/assets/workflow-marketo-2.png)

Après avoir créé la configuration du service cloud pour intégrer Marketo Engage à AEM Forms existant, vous pouvez configurer la source de données pour les formulaires.

La configuration de l’intégration des données permet aux utilisateurs de se connecter à différentes sources de données ou différents schémas. L’intégration à la source de données du Marketo Engage et son utilisation dans différents formulaires facilitent les opérations sur ces données. Pour explorer les sources de données prêtes à l’emploi prises en charge pour un formulaire adaptatif, reportez-vous à l’article [Configurer les sources de données](/help/forms/configure-data-sources.md) .

## Remarque concernant la configuration de la source de données Marketo Engage pour les formulaires

Lors de la configuration de la source de données Marketo Engage pour les formulaires, les points à prendre en compte sont les suivants :

* Il n’est pas possible de connecter Edge Delivery Services Forms à Marketo Engage.

## Condition préalable requise pour utiliser la source de données Marketo Engage pour les formulaires

Condition préalable requise pour utiliser la source de données Marketo Engage avec les formulaires :

* Créez la configuration de service cloud [ pour intégrer Marketo Engage à forms](/help/forms/integrate-form-to-marketo-engage.md).

## Comment configurer un formulaire adaptatif existant pour la source de données de Marketo Engage ?

Pour configurer un formulaire adaptatif avec la source de données du Marketo Engage, procédez comme suit :
1. Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms].

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Ouvrez l’arborescence de contenu et sélectionnez le **[!UICONTROL conteneur de guide]**.
1. Cliquez sur l’icône des propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue Conteneur de formulaires adaptatifs s’ouvre pour configurer la source de données.
1. Ouvrez l’onglet **[!UICONTROL Data Model]** et sélectionnez un modèle de formulaire **Connector**.
1. Sélectionnez **[!UICONTROL Connector]** dans la liste déroulante.

1. Après avoir sélectionné le **[!UICONTROL Connector]**, vous pouvez sélectionner la configuration cloud.

   ![Sélectionner le connecteur Marketo](/help/forms/assets/select-marketo-connector.png)

   En fonction de la configuration de Marketo Engage sélectionnée, les éléments de formulaire sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL explorateur de contenu]** dans la barre latérale. Vous pouvez faire glisser ces éléments pour créer votre formulaire adaptatif.

   ![Source de données Marketo](/help/forms/assets/marketo-engage-data-source.png)

1. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier la configuration qui lui est associée.

Le formulaire adaptatif est maintenant configuré avec la source de données de l’instance de Marketo Engage connectée. Maintenant, configurez-le pour envoyer des données à Adobe Marketo Engage.

## Questions fréquentes

**Q : Que se passe-t-il lorsque vous modifiez le connecteur du formulaire ?**\
**A :** Si vous modifiez le connecteur du formulaire, les liaisons existantes ne sont plus valides.

**Q : Quelles sont les trois opérations disponibles dans le service Invoke de l’éditeur de règles pour les formulaires intégrés à Marketo Engage ?**\
**A :** Les trois opérations d’usine disponibles dans le **service d’appel** pour les formulaires intégrés à Marketo Engage sont les suivantes :
* piste de synchronisation
* Obtention d’une piste avec ID
* Obtention d’une piste par type de filtre

## Étape suivante

Vous avez maintenant configuré la source de données du Marketo Engage pour Adaptive Forms. Ensuite, vous pouvez [configurer un formulaire adaptatif pour envoyer des données à Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md).

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}



---
title: Comment configurer les données Marketo Engage pour le Forms adaptatif ?
description: Découvrez comment utiliser le schéma Marketo Engage dans Adaptive Forms.
keywords: Utilisation de la source de données Marketo Engage dans le Forms adaptatif. Comment connecter une source de données d’instance Marketo à un formulaire ? , Connecter un formulaire à Marketo.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 4656ec65-f1ad-4e97-8d93-25933cdc7f7b
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 75%

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

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants UE/Foundation, reportez-vous à l’article </span>.

>[!BEGINTABS]

>[!TAB Composant de base]

Pour configurer un formulaire adaptatif en fonction des composants de base avec la source de données Marketo Engage, procédez comme suit :

1. Connectez-vous à votre instance de création [!DNL Experience Manager Forms].
1. Ouvrez le formulaire adaptatif pour le modifier et accédez à la section **[!UICONTROL Modèle de données]** des propriétés du conteneur de formulaires adaptatifs et sélectionnez un modèle de formulaire en tant que **Connecteur**.
1. Sélectionnez le **[!UICONTROL Connecteur]** dans la liste déroulante.
1. Après avoir sélectionné le **[!UICONTROL Connecteur]**, vous pouvez sélectionner la configuration cloud.

   ![Sélection du connecteur Marketo](/help/forms/assets/select-marketo-connector-af1.png){width=50%, height=50%}

   Selon la configuration Marketo Engage sélectionnée, les éléments de formulaire sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL Explorateur de contenu]** dans la barre latérale. Vous pouvez faire glisser et déposer ces éléments pour créer votre formulaire adaptatif.

   ![Source de données Marketo](/help/forms/assets/marketo-engage-data-source-af1.png){width=50%, height=50%}

1. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier sa configuration associée.

Le formulaire adaptatif est maintenant configuré avec la source de données de l’instance Marketo Engage connectée. Maintenant, configurez-le pour envoyer des données à Adobe Marketo Engage.

>[!TAB Composant principal]

Pour configurer un formulaire adaptatif basé sur les composants principaux avec la source de données Marketo Engage, procédez comme suit :

1. Connectez-vous à votre instance de création [!DNL Experience Manager Forms].

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Ouvrez l’arborescence de contenu et sélectionnez le **[!UICONTROL conteneur de guide]**.
1. Cliquez sur l’icône des propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue Conteneur de formulaire adaptatif pour configurer les sources de données s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL Modèle de données]** et sélectionnez un modèle de formulaire en tant que **Connecteur**.
1. Sélectionnez le **[!UICONTROL Connecteur]** dans la liste déroulante.

1. Après avoir sélectionné le **[!UICONTROL Connecteur]**, vous pouvez sélectionner la configuration cloud.

   ![Sélection du connecteur Marketo](/help/forms/assets/select-marketo-connector.png){width=50%, height=50%}

   Selon la configuration Marketo Engage sélectionnée, les éléments de formulaire sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL Explorateur de contenu]** dans la barre latérale. Vous pouvez faire glisser et déposer ces éléments pour créer votre formulaire adaptatif.

   ![Source de données Marketo](/help/forms/assets/marketo-engage-data-source.png){width=50%, height=50%}

1. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier sa configuration associée.

Le formulaire adaptatif est maintenant configuré avec la source de données de l’instance Marketo Engage connectée. Maintenant, configurez-le pour envoyer des données à Adobe Marketo Engage.

>[!TAB Éditeur universel]

Pour configurer un formulaire adaptatif créé dans l’éditeur universel avec la source de données Marketo Engage, procédez comme suit :

1. Ouvrez les propriétés du formulaire pour les modifier.
1. Sélectionnez le **[!UICONTROL modèle de formulaire]**.
1. Sélectionnez **Connecteur** dans le **[!UICONTROL Modèle de formulaire]**.
1. Après avoir sélectionné le **[!UICONTROL Connecteur]**, vous pouvez sélectionner la configuration cloud.

   ![Sélection du connecteur Marketo](/help/forms/assets/select-marketo-connector-ue.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

Selon la configuration Marketo Engage sélectionnée, les éléments de formulaire sont affichés dans l’onglet **[!UICONTROL Source de données]** de l’explorateur de contenu dans le panneau Propriétés. Vous pouvez faire glisser et déposer ces éléments pour créer votre formulaire adaptatif.

![Source de données Marketo](/help/forms/assets/marketo-engage-data-source-ue.png)

Le formulaire est maintenant configuré avec la source de données de l’instance Marketo Engage connectée. Maintenant, configurez-le pour envoyer des données à Adobe Marketo Engage.

>[!ENDTABS]

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

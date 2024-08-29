---
title: Comment ajouter des liens de formulaires sur la page AEM Sites à l’aide du composant Link Forms Portal ?
description: Découvrez comment ajouter des liens de formulaires à la page AEM Sites.
feature: Adaptive Forms, Core Components
role: User, Developer, Admin
source-git-commit: 58533d9a950fa4dc0e043ef8cb935d65fc68d233
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 14%

---


# Ajout de liens de formulaire à la page Sites

Dans le scénario du site Web bancaire, le composant **Lien** du portail Forms améliore la navigation en guidant les utilisateurs vers des formulaires spécifiques à travers différentes sections du site. Il fournit des références directes à des formulaires tels que des demandes de prêt, des formulaires d’ouverture de compte ou des enquêtes de retour, placés stratégiquement dans tout le site Web. Le composant **Lien** insère des liens qui orientent les utilisateurs vers des Forms adaptatives spécifiques dans la page Sites. Par exemple, sur le site web de la banque, les utilisateurs anonymes peuvent accéder à un formulaire d’enquête générale, tandis que les utilisateurs connectés peuvent accéder directement à des formulaires plus sécurisés, tels que des demandes de prêt ou des formulaires d’autorisation de transaction.

![Icône Lien](/help/forms/assets/link-forms.png){width="250" align="center"}

## Condition préalable

Avant d’explorer les différentes fonctionnalités d’un composant Forms Portal, assurez-vous que les composants principaux sont activés pour votre environnement. Pour obtenir des instructions détaillées sur l’activation des composants principaux pour votre environnement, [cliquez ici](/help/forms/enable-adaptive-forms-core-components.md).

Après avoir déployé les derniers composants principaux dans votre environnement, les composants du portail Forms deviennent accessibles dans votre environnement de création.

## Ajout du composant Lien à votre page Sites

Pour ajouter le composant de portail **Lien** à votre page Sites, procédez comme suit :

1. Ouvrez la page AEM Sites en mode **Modifier** .
1. Accédez à **[!UICONTROL Informations sur la page]** > **[!UICONTROL Modifier le modèle]**.
   ![Modifier la stratégie de modèle](/help/forms/assets/save-form-as-draft-edit-template.png){width="250" align="center"}

1. Cliquez sur la **[!UICONTROL Stratégie]** et cochez la case **[!UICONTROL Lien]** sous le **[Nom de projet d’AEM archétype] - Forms and Communications Portal**.

   ![Sélection de stratégie](/help/forms/assets/add-link.png){width="250" align="center"}

1. Cliquez sur **[!UICONTROL Terminé]**.
1. Maintenant, rouvrez la page AEM Sites en mode création.
1. Recherchez la section dans l’éditeur de page qui vous permet d’ajouter le composant Portail Forms .

1. Cliquez sur l&#39;icône **Ajouter** . L’icône est un signe plus (+) qui indique l’option d’ajout de nouveaux composants.

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche divers composants à insérer.

   >[!NOTE]
   >
   > Vous pouvez également faire glisser et déposer le composant.

1. Parcourez les composants disponibles dans la boîte de dialogue et sélectionnez un composant dans la liste. Par exemple, sélectionnez le composant **Lien** dans la liste pour ajouter le composant **Lien** Forms Portal.

   ![Composant Link](/help/forms/assets/add-link-in-sites.png){width="250" align="center"}

Maintenant, configurez les propriétés du composant **Lien**.

## Présentation des propriétés du composant Lien

Vous pouvez facilement personnaliser les propriétés du composant **Lien** à l’aide de la boîte de dialogue de configuration pour une expérience utilisateur transparente. Pour la configuration, sélectionnez le composant, puis sélectionnez l’icône ![Configurer](assets/configure_icon.png). La boîte de dialogue **[!UICONTROL Lien]** s’ouvre.

### Onglet Affichage

![Onglet Affichage](/help/forms/assets/link-asset-tab.png){width="250" align="center"}

Dans l’onglet **[!UICONTROL Affichage]**, fournissez la légende du lien et l’info-bulle pour faciliter l’identification des formulaires représentés par le lien.

### Onglet Asset Info

![Onglet Informations Assets](/help/forms/assets/link-asset-info.png){width="250" align="center"}

Dans l’onglet **[!UICONTROL Informations sur les ressources]**, spécifiez le chemin d’accès au référentiel où la ressource est stockée.

### Onglet Paramètres de requête

![Onglet Paramètres de requête](/help/forms/assets/link-query-tab.png){width="250" align="center"}

Dans l’onglet **[!UICONTROL Paramètres de requête]**, spécifiez les paramètres supplémentaires au format de paire clé-valeur. Lorsqu’un clic est effectué sur le lien, ces paramètres supplémentaires sont transmis avec le formulaire.

## Afficher les liens de formulaire sur la page Sites à l’aide du composant Lien

Prévisualisez la page Sites pour afficher le lien vers un formulaire adaptatif, qui est spécifié dans l’onglet des propriétés **Assets Info** du composant **Lien**. Cliquer sur le lien affiche le formulaire à l’écran pour les utilisateurs, qui peuvent y accéder en fonction des autorisations.

![Onglet Paramètres de requête](/help/forms/assets/link-forms.png){width="250" align="center"}

## Articles connexes

{{forms-portal-see-also}}

## Voir également {#see-also}

{{see-also}}

---
title: Comment ajouter des liens de formulaires sur la page AEM Sites à l’aide du composant Lien du portail Forms ?
description: Découvrez comment ajouter des liens de formulaires à la page AEM Sites.
feature: Adaptive Forms, Core Components
role: User, Developer, Admin
exl-id: a55d0776-8827-46cc-9625-5d6f5f6bda3b
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 14%

---

# Ajout de liens de formulaire à une page Sites

Dans le scénario d’un site web de banque, le composant **Link** du portail Forms améliore la navigation en guidant les utilisateurs et utilisatrices vers des formulaires spécifiques dans différentes sections du site. Il fournit des références directes à des formulaires tels que les demandes de prêt, les formulaires d’ouverture de compte ou les questionnaires de retour, stratégiquement placés sur l’ensemble du site web. Le composant **Link** insère des liens qui redirigent les utilisateurs vers des Forms adaptatifs spécifiques dans la page Sites. Par exemple, sur le site Web de la banque, les utilisateurs anonymes peuvent accéder à un formulaire de demande de renseignements généraux, tandis que les utilisateurs connectés peuvent accéder directement à des formulaires plus sécurisés, comme des demandes de prêt ou des formulaires d&#39;autorisation de transaction.

![Icône Lien](/help/forms/assets/link-forms.png)

## Condition préalable

Avant d’explorer les différentes fonctionnalités d’un composant du portail Forms, assurez-vous que les composants principaux sont activés pour votre environnement. Installez la dernière version de pour activer les composants principaux de Forms adaptatif pour votre environnement AEM Cloud Service.

Après le déploiement des derniers composants principaux dans votre environnement, les composants du portail Forms deviennent accessibles dans votre environnement de création.

## Ajoutez le composant Lien à votre page Sites

Pour ajouter le composant de portail **Link** à votre page Sites, procédez comme suit :

1. Ouvrez la page AEM Sites en mode **Modifier**.
1. Accédez à **[!UICONTROL Informations sur la page]** > **[!UICONTROL Modifier le modèle]**.
   ![Modifier la politique du modèle](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Cliquez sur le **[!UICONTROL Politique]** et cochez la case **[!UICONTROL Lien]** sous **[Nom du projet de l’archétype AEM] - Portail Forms et communications**.

   ![Sélection de politique](/help/forms/assets/add-link.png)

1. Cliquez sur **[!UICONTROL Terminé]**.
1. Rouvrez maintenant la page AEM Sites en mode création.
1. Recherchez la section dans l’éditeur de page qui vous permet d’ajouter le composant Forms Portal.

1. Cliquez sur l’icône **Ajouter**. L’icône est un signe plus (+) qui signifie que vous pouvez ajouter de nouveaux composants.

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche différents composants à insérer.

   >[!NOTE]
   >
   > Vous pouvez également effectuer un glisser-déposer du composant.

1. Parcourez les composants disponibles dans la boîte de dialogue et sélectionnez le composant de votre choix dans la liste. Par exemple, sélectionnez le composant **Link** dans la liste pour ajouter le composant **Link** Portail Forms.

   ![Composant Link](/help/forms/assets/add-link-in-sites.png)

Maintenant, configurez les propriétés du composant **Link**.

## Comprendre les propriétés du composant Lien

Vous pouvez facilement personnaliser les propriétés du composant **Link** à l’aide de la boîte de dialogue de configuration pour une expérience utilisateur fluide. Pour configurer, sélectionnez le composant, puis sélectionnez l’icône ![Configurer](assets/configure_icon.png). La boîte de dialogue **[!UICONTROL Lien]** s’ouvre.

### Onglet Affichage

![Onglet Affichage](/help/forms/assets/link-asset-tab.png)

Dans l’onglet **[!UICONTROL Affichage]**, fournissez la légende du lien et l’info-bulle pour faciliter l’identification des formulaires représentés par le lien.

### Onglet Informations sur les ressources

![Onglet Informations Assets](/help/forms/assets/link-asset-info.png)

Dans l’onglet **[!UICONTROL Informations sur les ressources]**, spécifiez le chemin d’accès au référentiel où la ressource est stockée.

### Onglet Paramètres de requête

![Onglet Paramètres de requête](/help/forms/assets/link-query-tab.png)

Dans l’onglet **[!UICONTROL Paramètres de requête]**, spécifiez les paramètres supplémentaires au format de paire clé-valeur. Lorsqu’un clic est effectué sur le lien, ces paramètres supplémentaires sont transmis avec le formulaire.

## Affichez les liens de formulaire sur la page Sites à l’aide du composant Lien

Prévisualisez la page Sites pour afficher le lien vers un formulaire adaptatif, qui est spécifié dans l’onglet des propriétés **Assets Info** du composant **Link**. Cliquer sur le lien affiche le formulaire à l’écran pour les utilisateurs et utilisatrices, qui peuvent ensuite y accéder en fonction des autorisations.

![Onglet Paramètres de requête](/help/forms/assets/link-forms.png)

## Articles connexes

{{forms-portal-see-also}}

## Voir également {#see-also}

{{see-also}}

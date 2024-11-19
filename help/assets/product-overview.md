---
title: Présentation de Content Hub
description: Découvrez Content Hub, ses principaux avantages, comment y accéder et comment fournir des commentaires sur les options disponibles dans Content Hub.
exl-id: c5908058-f1ad-4aaa-9e8e-c0157e107ed1
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 11%

---

# Présentation de Content Hub {#overview-content-hub}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |----|-----|

![Présentation de Content Hub](assets/content-hub-overview.png)

>[!AVAILABILITY]
>
>Le guide Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE PDF de guide Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Le hub de contenus est disponible dans le cadre d’Experience Manager Assets as a Cloud Service pour démocratiser l’accès au contenu de marque pour les organisations et leurs partenaires commerciaux. Il se concentre sur la distribution des ressources pour activation à grande échelle et la création de variantes de contenu sur marque afin d’améliorer l’agilité marketing.

## Pourquoi Content Hub ?

Content Hub offre les avantages clés suivants :

**Rechercher et partager toutes les ressources approuvées par la marque disponibles dans un portail intuitif**

AEM Assets sert de source unique de vérité et toutes les ressources approuvées sont automatiquement disponibles sur Content Hub dans une hiérarchie plate afin d’améliorer l’expérience de recherche.

**Interface utilisateur configurable**

Les propriétés les plus courantes de Content Hub, telles que les filtres de recherche, les champs disponibles lors de l’ajout ou de l’importation de ressources, les propriétés de ressource, le contenu de bannière pour la valorisation de marque, sont configurables et un administrateur peut facilement configurer l’interface utilisateur de Content Hub en fonction de ses besoins.

**Permettre aux non-créatifs de modifier et de remixer du contenu tout en restant sur la marque**

Content Hub vous permet de créer du contenu avec Adobe Express (si vous disposez de droits d’Adobe Express). Vous pouvez modifier du contenu existant à l’aide d’outils simples d’utilisation, produire des variations de marque avec des modèles et des éléments de marque et créer du contenu avec les dernières fonctionnalités GenAI d’Adobe Firefly.

**Obtenez des informations sur l’utilisation du contenu entre les équipes**

[!DNL Content Hub] fournit des informations précieuses sur les ressources, ce qui permet de répondre à un défi commun auquel les parties prenantes marketing sont souvent confrontées : les statistiques d’utilisation des ressources utilisées dans les campagnes marketing, les canaux et les différentes régions. En acquérant une compréhension claire des performances et de la popularité des ressources, elle fournit des informations exploitables essentielles à l’amélioration de l’expérience utilisateur.

## Conditions préalables {#prerequisites-content-hub}

Content Hub nécessite un environnement de création de production as a Cloud Service Experience Manager, version 2024.6 ou ultérieure (la version minimale est 2024.6.16799).

## Comment accéder à Content Hub ? {#access-content-hub}

[Après avoir configuré Content Hub](/help/assets/deploy-content-hub.md) et ajouté un utilisateur au [profil de produit Content Hub](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile), Content Hub est accessible à l’aide des méthodes suivantes :

* Accédez à Content Hub à l’aide du lien suivant :

  `https://experience.adobe.com/#/assets/contenthub`

* Connectez-vous à experience.adobe com et cliquez sur **[!UICONTROL Experience Manager Assets Content Hub]** disponible dans la section **[!UICONTROL Accès rapide]** :
  ![Accès à Content Hub](assets/access-content-hub.png)

* Connectez-vous à experience.adobe com et cliquez sur **[!UICONTROL Experience Manager Assets Content Hub]** disponible dans le sélecteur de produits :
  ![Méthode d’accès Content Hub 3](assets/access-content-hub-alternate.png)



## Fournir des commentaires Content Hub {#provide-content-hub-feedback}

Pour recommander des améliorations relatives aux produits, cliquez sur **[!UICONTROL Commentaires]** en regard du nom de votre organisation dans la partie supérieure de l’interface utilisateur de Content Hub.

Indiquez un objet, une description de la recommandation et joignez des fichiers, le cas échéant. Cliquez sur **[!UICONTROL Envoyer]** pour envoyer les commentaires à Adobe.

![Commentaires Content Hub](assets/content-hub-feedback.png)

## Configuration de Content Hub pour votre équipe {#setup-content-hub}

Procédez comme suit pour configurer Content Hub pour votre équipe :

1. [Activez Content Hub pour Experience Manager Assets à l’aide de Cloud Manager](deploy-content-hub.md#enable-content-hub).

1. [Administrateur Content Hub intégré](deploy-content-hub.md#onboard-content-hub-administrator).

1. [Ajouter des utilisateurs Content Hub clés](deploy-content-hub.md#onboard-content-hub-consumer-users).

1. [Les auteurs ou administrateurs DAM doivent approuver les ressources à l’aide de ressources Experience Manager](approve-assets.md).

1. [Les administrateurs peuvent configurer l’interface utilisateur de Content Hub pour d’autres utilisateurs](configure-content-hub-ui-options.md).

1. [Accordez l’accès à Content Hub à d’autres utilisateurs de l’équipe ](deploy-content-hub.md#onboard-content-hub-consumer-users).

1. [Accéder au portail Content Hub](#access-content-hub).

1. [Fournir des commentaires Content Hub](#provide-content-hub-feedback).


## En savoir plus sur les principales fonctionnalités {#key-capabilities-content-module}

<table>
<td>
   <a href="/help/assets/configure-content-hub-ui-options.md">
   <img alt="Déployer Content Hub" src="./assets/configure-assets.png" />
   </a>
   <div>
      <a href="/help/assets/configure-content-hub-ui-options.md">
      <strong> Configuration de l’interface utilisateur de Content Hub</strong>
      </a>
   </div>
   <p>
      <em>Découvrez comment les administrateurs peuvent configurer l’interface utilisateur de Content Hub. </em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-content-hub.md">
   <img alt="Recherche de ressources disponibles dans Content Hub" src="./assets/search.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-content-hub.md">
      <strong>Recherche de ressources disponibles dans Content Hub</strong>
      </a>
   </div>
   <p>
      <em>Découvrez comment utiliser différentes fonctionnalités pour affiner vos résultats de recherche.</em>
   </p>
</td>
<td>
   <a href="/help/assets/edit-images-content-hub.md">
   <img alt="Modifier des images à l’aide d’Adobe Express" src="./assets/edit-images-content-hub.png" />
   </a>
   <div>
      <a href="/help/assets/edit-images-content-hub.md">
      <strong>Modifier des images à l’aide d’Adobe Express</strong>
      </a>
   </div>
   <p>
      <em>Découvrez comment créer des variantes d’images dans Content Hub à l’aide d’Adobe Express</em>
   </p>
</td>
</table>
<table>
<td>
   <a href="/help/assets/share-assets-content-hub.md">
   <img alt="Partage de ressources disponibles dans Content Hub" src="./assets/share-assets-banner.png" />
   </a>
   <div>
      <a href="/help/assets/share-assets-content-hub.md">
      <strong> Partager des ressources disponibles dans Content Hub</strong>
      </a>
   </div>
   <p>
      <em>Découvrez comment partager une ou plusieurs ressources en tant que lien, puis y accéder.</em>
   </p>
</td>
<td>
   <a href="/help/assets/collections-content-hub.md">
   <img alt="Gérer des collections dans le hub de contenus" src="./assets/manage-collection.png" />
   </a>
   <div>
      <a href="/help/assets/collections-content-hub.md">
      <strong>Gestion des collections dans Content Hub</strong>
      </a>
   </div>
   <p>
      <em>Découvrez comment créer des collections à l’aide de ressources, puis les gérer.</em>
   </p>
</td>
<td>
   <a href="/help/assets/insights-content-hub.md">
   <img alt="Partage de ressources disponibles dans Content Hub" src="./assets/asset-insights-banner.jpg" />
   </a>
   <div>
      <a href="/help/assets/insights-content-hub.md">
      <strong>Affichage des informations sur les ressources dans Content Hub</strong>
      </a>
   </div>
   <p>
      <em> Le module de contenu fournit des insights précieux sur les ressources, en répondant à un défi commun auquel les parties prenantes marketing rencontrent souvent </em>
   </p>
</td>
</table>

---
title: Partagez Assets dans  [!DNL the Content Hub]
description: Partagez Assets dans  [!DNL the Content Hub]
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# Partager des ressources dans le hub de contenus {#search-assets-as-a-link}

Créez un lien vers les ressources sélectionnées pour les partager facilement avec d’autres personnes. En tant qu’utilisateur [!DNL Content Hub] autorisé, sélectionnez une ou plusieurs ressources disponibles dans votre environnement [!DNL Content Hub], générez un lien et envoyez-le à d’autres utilisateurs privés ou publics.

>[!VIDEO](https://video.tv.adobe.com/v/3474890/?learn=on&enablevpops=on){transcript=true}

## Conditions préalables {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent créer un lien vers les ressources sélectionnées et le partager avec d’autres utilisateurs.

## Partager des ressources {#share-assets}

Pour partager une ou plusieurs ressources avec des utilisateurs privés ou publics, procédez comme suit :

1. Accédez à la page d’accueil de votre [!DNL Content Hub], sélectionnez une ou plusieurs ressources, puis cliquez sur ![partager](/help/assets/assets/share.svg) **[!UICONTROL Partager]** pour afficher une seule ressource sélectionnée ou une liste de plusieurs ressources sélectionnées dans la boîte de dialogue **[!UICONTROL Partager les ressources]**.

   Vous pouvez également sélectionner et partager des ressources disponibles dans ![collections](/help/assets/assets/Smock_Collection_18_N.svg) **[!UICONTROL Collections]**.

1. Affichez une ressource ou consultez la liste des ressources disponibles dans la boîte de dialogue **[!UICONTROL Partage de ressources]**. Cliquez sur ![désélectionner](/help/assets/assets/Close.svg) en regard d’une ressource pour la supprimer de la liste.

1. Indiquez un titre et une description facultative qui définit l’ensemble des ressources sélectionnées.

1. Sélectionnez **[!UICONTROL Période d’expiration]**.

1. Dans la liste déroulante **[!UICONTROL Qui peut accéder]**, sélectionnez les options d’accès et cliquez sur **[!UICONTROL Obtenir le lien]** pour générer un lien à partager avec les utilisateurs sélectionnés. Les utilisateurs privés doivent se connecter à leur environnement [!DNL Content Hub] pour accéder à la page des ressources partagées. En revanche, les utilisateurs publics, en tant qu’invités, peuvent accéder à la page des ressources partagées sans se connecter à [!DNL Content Hub].

<!--1. Select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Get Link]** to generate a link to share with private users. Private users sign in to their [!DNL Content Hub] environment to access the shared assets page.-->

![lien privé et public](/help/assets/assets/shared-link-for-assets.png)

<!--Enable the **[!UICONTROL Public Link]** toggle, select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Generate Public Link]** to generate a link to share with public users. Public users, as guests, access the shared assets page without signing in to [!DNL Content Hub].-->

>[!NOTE]
> 
> [Activez le partage de liens public à partir de la page de configuration](/help/assets/configure-content-hub-ui-options.md#enable-public-link-sharing) pour afficher le bouton bascule **[!UICONTROL Lien public]** dans la boîte de dialogue **[!UICONTROL Partager les ressources]**.

## Partage d’une ressource à partir de sa page d’aperçu {#share-asset-from-preview-page}

Pour partager une ressource en cours de prévisualisation, procédez comme suit :

1. Accédez à la page d’accueil [!DNL Content Hub] et cliquez sur la miniature de la ressource pour la prévisualiser et afficher les options de menu dans le volet droit de la boîte de dialogue.
1. Sélectionnez ![partager](/help/assets/assets/share.svg) pour afficher le panneau **[!UICONTROL Partager]**.
   ![partager une ressource lors de sa prévisualisation](/help/assets/assets/share-link-asset-preview.png)
1. Suivez les étapes 3 à 5 de la section [Partage de ressources](#share-assets) pour générer et partager le lien de la ressource (privée ou publique) à partir de ce panneau **[!UICONTROL Partage]**.

## Accéder aux ressources partagées {#access-shared-assets}

Accédez à la page des ressources partagées via le lien et procédez comme suit :

* Sélectionnez une ou plusieurs ressources, puis cliquez sur ![Télécharger](/help/assets/assets/download-icon.svg) **[!UICONTROL Télécharger]** pour sélectionner les rendus **[!UICONTROL Original]**, **[!UICONTROL Statique]** ou les deux à partir des options de téléchargement disponibles.
  ![](/help/assets/assets/download-shared-assets.png)
* Cliquez sur la miniature de la ressource pour afficher ses métadonnées.
* Sur la page des ressources partagées ([accessible par le biais d’un lien privé](#share-assets)), cliquez sur la miniature d’une ressource et sélectionnez ![télécharger](/help/assets/assets/download-icon.svg) pour sélectionner et afficher les rendus dynamiques disponibles de la ressource dans le panneau **[!UICONTROL Télécharger]** avant de les sélectionner et de les télécharger.
  ![](/help/assets/assets/download-renditions-shared-assets-page.png)

## Questions fréquemment posées {#faqs-share-assets-content-hub}

### Que signifie le partage de ressources dans AEM Assets Content Hub ?

Le partage de ressources dans AEM Assets Content Hub permet aux utilisateurs autorisés de partager facilement une ou plusieurs ressources ou des collections entières avec d’autres utilisateurs en générant un lien. Ce lien peut être envoyé à des utilisateurs privés (qui doivent se connecter) ou publics (qui peuvent y accéder en tant qu’invités), ce qui permet aux destinataires d’accéder directement à l’affichage et au téléchargement des ressources sélectionnées.

### Comment partager des ressources ou des collections avec d’autres utilisateurs à l’aide d’AEM Assets Content Hub ?

Pour partager des ressources ou des collections dans AEM Assets Content Hub, accédez à la page d’accueil de Content Hub, sélectionnez une ou plusieurs ressources (ou accédez à l’onglet Collections pour les collections), puis cliquez sur l’icône Partager . Dans la boîte de dialogue Partager, vous pouvez prévisualiser les ressources, en supprimer si nécessaire, ajouter un titre et une description, sélectionner les personnes pouvant accéder au lien (privé ou public), définir un délai d’expiration, puis cliquer sur Obtenir le lien pour générer et copier l’URL partageable. Le lien peut ensuite être envoyé aux membres de l’équipe ou aux parties prenantes.

### Quelles sont les options d’accès disponibles lors du partage de ressources dans AEM Assets Content Hub et en quoi diffèrent-elles ?

Content Hub vous permet de choisir entre deux options d’accès pour les liens partagés : privé et public. Les liens privés exigent des destinataires qu’ils se connectent à leur environnement Content Hub pour afficher et télécharger des ressources, ce qui renforce la sécurité. Tout utilisateur disposant d’un lien peut accéder aux liens publics sans avoir à se connecter. Chaque type de lien est fourni avec ses propres paramètres d’expiration, par exemple entre 24 heures et une semaine pour les liens publics et des dates personnalisées pour les liens privés.

### Existe-t-il une configuration gérée par l’administrateur pour pouvoir générer des liens publics pour les ressources dans AEM Assets Content Hub ?

Oui, les administrateurs peuvent activer ou désactiver le bouton (bascule) **Activer le lien public** disponible dans l’onglet **Collections et partage** de l’interface utilisateur de configuration pour gérer la génération de liens publics pour les ressources dans AEM Assets Content Hub.

### Puis-je définir des dates d’expiration pour les liens de ressources partagées dans AEM Assets Content Hub et pourquoi est-ce important ?

Oui, vous pouvez définir des dates d’expiration pour les liens partagés privés et publics dans AEM Assets Content Hub. Pour les liens publics, vous pouvez choisir parmi des paramètres prédéfinis, par exemple 24 heures jusqu’à une semaine, tandis que les liens privés vous permettent de choisir parmi des paramètres prédéfinis ou de définir une date d’expiration personnalisée. Les dates d’expiration sont importantes, car une fois le lien expiré, il ne peut plus être utilisé pour accéder aux ressources ou les télécharger, ce qui contribue à maintenir la sécurité et le contrôle de votre contenu.

### Que peuvent faire les destinataires avec le lien de ressource partagé créé à l’aide d’AEM Assets Content Hub et existe-t-il des options pour télécharger différents rendus ?

Les destinataires qui reçoivent un lien de ressource partagé peuvent l’ouvrir dans leur navigateur pour prévisualiser, sélectionner et télécharger les ressources fournies. Si les rendus de ressources sont activés dans AEM Assets Content Hub, les destinataires peuvent choisir les rendus (tels que Original ou Statique) qu’ils souhaitent télécharger. Les ressources et les rendus sont téléchargés sous la forme d’un fichier zip et les métadonnées peuvent être affichées en cliquant sur la miniature de la ressource. Le lien reste fonctionnel jusqu’à sa date d’expiration définie.





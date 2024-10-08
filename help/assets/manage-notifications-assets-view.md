---
title: Gérer les notifications
description: Surveillez toute opération effectuée sur les ressources ou dossiers du répertoire à l’aide des notifications de la vue Assets.
exl-id: 1fe6a845-37d5-43c2-bb96-c5b149c238ab
feature: Assets Essentials
role: User, Leader
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 97%

---

# Surveiller des ressources, des dossiers et des collections {#watch-assets-folders}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Les notifications de la vue Assets vous permettent de surveiller les opérations effectuées sur les ressources, les dossiers ou les collections disponibles dans le référentiel. Pour recevoir les notifications, vous devez sélectionner le contenu et vous y abonner. Vous pouvez également configurer les catégories pour lesquelles les notifications vous sont envoyées.

## S’abonner aux catégories de notification {#subscribe-to-notification-categories}

Vous pouvez choisir de vous abonner à une liste de catégories et recevoir des notifications. La vue Assets vous envoie les notifications uniquement pour les catégories que vous sélectionnez dans les options disponibles :

<table>
    <tbody>
     <tr>
      <th><strong>Catégorie de notification</strong></th>
      <th><strong>Description</strong></th>
     </tr>
     <tr>
      <td>Demandes</td>
      <td>Lorsque vous affectez une tâche à un utilisateur, vous recevez des notifications pour toute action effectuée sur cette tâche par cet utilisateur.</td>
     </tr>
     <tr>
      <td>Affecté à moi</td>
      <td>Vous recevez une notification lorsqu’une tâche vous est assignée par un autre utilisateur.</td>
     </tr>
     <tr>
      <td>Commentaire sur le contenu auquel vous êtes abonné</td>
      <td>Vous recevez une notification lorsqu’un utilisateur apporte un commentaire sur la ressource à laquelle vous êtes abonné.</td>
     </tr>
     <tr>
      <td>Suppression du contenu auquel vous êtes abonné</td>
      <td>Vous recevez une notification lorsqu’un utilisateur supprime une ressource, un dossier ou une collection auquel vous êtes abonné.</td>
     </tr>
     <tr>
      <td>Partage externe de contenu auquel vous êtes abonné</td>
      <td>Vous recevez une notification lorsqu’un utilisateur génère un lien public pour la ressource, le dossier ou la collection auquel vous êtes abonné.</td>
     </tr>
     <tr>
      <td>Modification du contenu auquel vous êtes abonné</td>
      <td>Vous recevez une notification lorsqu’un utilisateur crée une nouvelle version de la ressource à laquelle vous êtes abonné.</td>
     </tr>
     <tr>
      <td>Déplacement/changement de nom du contenu auquel vous êtes abonné</td>
      <td>Vous recevez une notification lorsqu’un utilisateur déplace ou renomme la ressource ou le dossier auquel vous êtes abonné.</td>
     </tr>
     <tr>
      <td>Mise à jour des dossiers et collections auxquels vous êtes abonné</td>
      <td>Vous recevez une notification lorsqu’un utilisateur ajoute ou supprime une ressource d’une collection ou d’un dossier auquel vous êtes abonné.</td>
     </tr>    
    </tbody>
   </table>

Pour vous abonner aux catégories de notification, procédez comme suit :

1. Cliquez sur l’![icône en forme de cloche](assets/bell-icon.svg) à l’extrémité droite de la barre de menu de l’interface utilisateur de la vue Assets.

1. Cliquez sur ![icône des paramètres](assets/settings-icon.svg) pour consulter la page [!UICONTROL Préférences Experience Cloud].

1. Cliquez sur l’option **[!UICONTROL Notifications]** disponible dans le volet de gauche.

1. Dans la section **[!UICONTROL Notifications]**, accédez à la section [!UICONTROL vue Assets] et assurez-vous que le bouton (bascule) est bien activé.

   ![Notifications dans la vue Assets](assets/enable-notifications.png)

1. Cliquez sur **[!UICONTROL Personnaliser]** pour afficher les catégories de notification.
   ![Notifications dans la vue Assets](assets/enable-notification-categories.png)

1. Sélectionnez les catégories pour lesquelles vous souhaitez recevoir des notifications.

## Observer et ne pas observer de dossiers, ressources ou collections {#watch-unwatch-assets}

Une fois que vous êtes [abonné aux catégories de notification](#subscribe-to-notification-categories), vous devez vous abonner au contenu pour commencer à recevoir des notifications.

>[!NOTE]
>
>* Pour les catégories de notification **[!UICONTROL Demandes]** et **[!UICONTROL Attribué à moi]**, vous n’avez pas besoin de vous abonner au contenu après vous être abonné aux catégories de notification. Les notifications vous sont automatiquement envoyées dans les situations suivantes : lorsque vous créez une demande et lorsqu’une tâche vous est affectée.
>* La vue Assets envoie des notifications uniquement lorsque d’autres personnes utilisatrices effectuent des actions sur le contenu avec abonnement. Vous ne recevez pas de notifications pour les actions que vous effectuez sur le contenu avec abonnement.

Pour vous abonner au contenu, sélectionnez le dossier, la ressource ou la collection auquel vous souhaitez vous abonner, puis cliquez sur **[!UICONTROL Surveiller]**.

La vue Assets affiche un message de succès. Sur celui-ci, vous pouvez cliquer sur **[!UICONTROL Accéder aux préférences de notification]** pour modifier votre [abonnement aux catégories de notification](#subscribe-to-notification-categories).

![Notifications dans la vue Assets](assets/watch-assets.png)

La vue Assets envoie désormais des notifications pour les catégories pour lesquelles vous disposez d’un abonnement. Pour gagner du temps, vous pouvez également sélectionner plusieurs ressources, dossiers ou collections puis cliquer sur **[!UICONTROL Observer]**. Cependant, l’option **[!UICONTROL Observer]** ne s’affiche pas si des entités auxquelles vous êtes déjà abonné ont été sélectionnées.

De même, pour annuler votre abonnement, sélectionnez la ressource, le dossier ou la collection auquel vous vous êtes abonné, puis cliquez sur **[!UICONTROL Ne pas observer]**.

## Consulter les notifications {#view-notifications}

Les notifications s’affichent à l’extrémité droite de la barre de menu dans l’interface utilisateur de la vue Assets.

![Notifications dans la vue Assets](assets/notifications-assets-essentials.png)

Lorsque vous cliquez sur une notification, la vue Assets vous dirige vers la ressource à laquelle, ou le dossier auquel, cette notification fait référence.

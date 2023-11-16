---
title: Notifications
description: Découvrez comment recevoir des informations sur les déploiements de pipeline à l’aide du système de notifications d’Adobe Experience Cloud.
exl-id: c1c740b0-c873-45a8-9518-a856db2be75b
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 79%

---


# Notifications {#notifications}

Découvrez comment Cloud Manager vous informe des événements importants.

## Notifications dans Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] vous envoie des notifications lorsqu’un pipeline de production démarre et se termine (avec succès ou non) au début d’un déploiement en production.

Ces notifications sont envoyées via le système de notifications [!UICONTROL Experience Cloud] aux utilisateurs et utilisatrices disposant des rôles **Propriétaire de l’entreprise**, **Responsable de programme** et **Responsable de déploiement**.

Les notifications s’affichent dans une barre latérale dans [!UICONTROL Cloud Manager] et dans [!UICONTROL Experience Cloud] d’Adobe. Les nouvelles notifications sont signalées sur l’icone en forme de cloche dans l’en-tête.

![Icône de notifications](assets/notifications-bell-badged.png)

Cliquez sur l’icône en forme de cloche pour ouvrir la barre latérale et afficher les notifications. L’onglet **Notifications** dans la barre latérale répertorie les notifications les plus récentes, telles que les confirmations de déploiement. Les notifications concernent vos environnements.

![Barre latérale de notifications](assets/notifications-activities.png)

L’onglet **Annonces** comprend les annonces de produits Adobe. Les annonces concernent le produit.

![Barre latérale de notifications](assets/notificaitons-announcements.png)

Cliquez sur une notification ou une annonce pour en afficher les détails. Les notifications liées à des activités telles que les déploiements de pipeline vous permettent d’accéder aux informations de cette activité, telles que la fenêtre d’exécution du pipeline.

Cliquez sur le bouton **Afficher tout** au bas du panneau pour afficher toutes les annonces dans votre boîte de réception.

Cliquez sur le bouton **Tout marquer comme lu** au bas du panneau pour marquer toutes les notifications non lues comme lues et effacer le badge de l’icône représentant une cloche.

## Configuration des notifications {#configuration}

Vous pouvez personnaliser le mode de réception des notifications et les notifications que vous recevez.

Cliquez sur l’icône d’engrenage en haut de la barre latérale des notifications.

![Icône Paramètres de notification](assets/notifications-configuration.png)

Cela permet d’ouvre la fenêtre **Préférences Experience Cloud** où vous pouvez définir vos abonnements aux notifications et comment vous recevez les notifications.

### Abonnements {#subscriptions}

Les abonnements définissent les produits pour lesquels vous recevez des notifications et leur type.

![Abonnements aux notifications](assets/notifications-subscriptions.png)

Par défaut, vous recevrez toutes les notifications pour tous les produits de l’application et par email. Cliquez sur le chevron en regard d’un nom de produit pour afficher les options détaillées et définir les types de notifications que vous recevez pour ce produit. Ou cochez ou décochez les options au niveau du produit pour sélectionner/désélectionner toutes les options du produit.

![Personnalisation de l’abonnement aux notifications](assets/notifications-subscriptions-customize.png)

### Priorité {#priority}

Les alertes de priorité seront marquées d’une balise de priorité **ÉLEVÉE** et peuvent être configurées pour être reçues exclusivement en tant qu’alertes. Dans la section **Priorité**, vous pouvez définir les catégories qui remplissent les critères de notification de priorité.

![Priorité des notifications](assets/notifications-priority.png)

Utilisez le menu déroulant pour ajouter à la liste des catégories qui remplissent les critères de priorité. Cliquez sur le X à côté des noms de catégorie pour les supprimer.

### Alertes {#alerts}

Les alertes s’affichent dans le coin supérieur droit de la fenêtre pendant quelques secondes. Utilisez la section **Alertes** pour définir les notifications pour lesquelles vous recevez des alertes.

![Alertes de notification](assets/notifications-alerts.png)

Vous pouvez définir le comportement des alertes.

* **Afficher les alertes pour** - définit les types de notifications qui déclenchent des alertes
* **Les alertes doivent rester à l’écran jusqu’à ce que vous les supprimiez** : contrôle si les alertes doivent persister, sauf si vous les ignorez activement.
* **Durée** - définit la durée pendant laquelle l’alerte doit rester à l’écran si vous n’avez pas choisi de la conserver.

### E-mails {#emails}

Les notifications sont disponibles dans l’interface utilisateur web de toutes les solutions Adobe [!UICONTROL Experience Cloud]. Vous pouvez également choisir d’envoyer ces notifications par e-mail dans la section **E-mails**.

![E-mails de notification](assets/notifications-emails.png)

Par défaut, aucun e-mail n‘est envoyé. Vous pouvez choisir de recevoir des e-mails :

* Immédiatement
* Chaque jour
* Chaque semaine

Lorsque vous choisissez **Notifications instantanées**, les e-mails sont envoyés immédiatement pour chaque notification. Pour **Envoi quotidien** et **Envoi hebdomadaire**, vous pouvez choisir le moment où votre résumé quotidien est envoyé, et le jour et le moment où votre résumé hebdomadaire est envoyé.
---
title: Notifications
description: Découvrez comment recevoir des informations sur les déploiements de pipeline à l’aide du système de notification Adobe Experience Cloud.
exl-id: c1c740b0-c873-45a8-9518-a856db2be75b
source-git-commit: 451b5a089645004c58c2674fd1fb13afbe1201cf
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 12%

---


# Notifications {#notifications}

Découvrez comment Cloud Manager vous informe des événements importants.

## Notifications dans Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] vous envoie des notifications lorsqu’un pipeline de production démarre et se termine (avec succès ou non), au début d’un déploiement de production.

Ces notifications sont envoyées via le [!UICONTROL Experience Cloud] système de notification aux utilisateurs dans **Propriétaire de l’entreprise**, **Responsable de programme**, et **Responsable de déploiement** rôles.

Les notifications s’affichent dans une barre latérale dans [!UICONTROL Cloud Manager] et dans [!UICONTROL Experience Cloud] d’Adobe. Les nouvelles notifications sont signalées sur l’icone en forme de cloche dans l’en-tête.

![Icône de notifications](assets/notifications-bell-badged.png)

Cliquez sur l’icône en forme de cloche pour ouvrir la barre latérale et afficher les notifications. Le **Notifications** dans la barre latérale répertorie les notifications les plus récentes, telles que les confirmations de déploiement. Les notifications concernent vos environnements.

![Barre latérale de notifications](assets/notifications-activities.png)

Le **Annonces** comprend les annonces de produits Adobes. Les annonces concernent le produit.

![Barre latérale de notifications](assets/notificaitons-announcements.png)

Cliquez sur une notification ou une annonce pour en afficher les détails. Les notifications liées à des activités telles que les déploiements de pipeline vous permettent d’accéder au détail de cette activité, comme la fenêtre d’exécution du pipeline.

Cliquez sur le bouton **Afficher tout** au bas du panneau pour afficher toutes les annonces dans votre boîte de réception.

Cliquez sur le bouton **Tout marquer comme lu** au bas du panneau pour marquer toutes les notifications non lues comme lues et effacer le badge de l’icône représentant une cloche.

## Configuration des notifications {#configuration}

Vous pouvez personnaliser le mode de réception des notifications et les notifications que vous recevez.

Cliquez sur l’icône d’engrenage en haut de la barre latérale des notifications.

![Icône Paramètres de notification](assets/notifications-configuration.png)

Cela ouvre la fenêtre **Préférences Experience Cloud** où vous pouvez définir vos abonnements aux notifications et comment vous recevez les notifications.

### Abonnements {#subscriptions}

Les abonnements définissent les produits pour lesquels vous recevez des notifications et les notifications.

![Abonnements aux notifications](assets/notifications-subscriptions.png)

Par défaut, vous recevrez toutes les notifications pour tous les produits. Cliquez sur **Personnaliser** en regard d’un produit pour définir les types de notifications que vous recevez pour ce produit.

![Personnalisation de l’abonnement aux notifications](assets/notifications-subscriptions-customize.png)

### Priorité {#priority}

Les alertes de priorité seront marquées d’une **HIGH** et peut être configuré pour être reçu exclusivement en tant qu’alertes. Dans le **Priorité** , vous pouvez définir les catégories qui remplissent les critères de notification de priorité.

![Priorité des notifications](assets/notifications-priority.png)

Utilisez le menu déroulant pour ajouter à la liste des catégories qui remplissent les critères de priorité. Cliquez sur le X en regard des noms de catégorie pour les supprimer.

### Alertes {#alerts}

Les alertes s’affichent dans le coin supérieur droit de la fenêtre pendant quelques secondes. Utilisez la variable **Alertes** pour définir les notifications pour lesquelles vous recevez des alertes.

![Alertes de notification](assets/notifications-alerts.png)

Vous pouvez définir le comportement des alertes.

* **Afficher les alertes pour** - Définit les types de notifications qui déclenchent des alertes
* **Les alertes doivent rester à l’écran jusqu’à ce que je les rejette.** : contrôle si les alertes doivent persister, sauf si vous les ignorez activement.
* **Durée** - Définit la durée pendant laquelle l’alerte doit rester à l’écran si vous n’avez pas choisi de la conserver.

### Courriels {#emails}

Les notifications sont disponibles dans l’interface utilisateur web d’ dans tous les Adobes [!UICONTROL Experience Cloud] solutions. Vous pouvez également choisir d’envoyer ces notifications par courrier électronique dans la variable **Emails** .

![Emails de notification](assets/notifications-emails.png)

Par défaut, aucun email n&#39;est envoyé. Vous pouvez choisir de recevoir des emails comme suit :

* Instant
* Quotidienne
* Hebdomadaire

When **Notifications instantanées** est choisie, les emails sont envoyés immédiatement pour chaque notification. Pour **Résumé quotidien** et **Résumé hebdomadaire** vous pouvez choisir le moment où votre résumé quotidien est envoyé, le jour et le moment où votre résumé hebdomadaire est envoyé.
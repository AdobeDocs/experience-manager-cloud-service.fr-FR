---
title: Centre de notifications
description: Tirez parti du Centre de notification pour prendre des mesures appropriées concernant les incidents et d'autres informations importantes
hidefromtoc: true
source-git-commit: a5977c667d831c47d41cd86b68e9196fbe726899
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# Centre de notifications {#notification-center}

>[!NOTE]
>Cette fonctionnalité n’a pas été publiée.

Une fois configurée, AEM as Cloud Service envoie des notifications sur les informations importantes pour lesquelles les clients doivent agir. Parmi les exemples de notifications, citons une file d’attente bloquée ou un jeu d’informations d’identification arrivant à expiration. L’ensemble complet des types de notification peut être consulté dans la variable [tableau ci-dessous](#current-notification-types), et s’étendra au fil du temps. Les notifications sont reçues par e-mail et en tant que nouvelle entrée sous le widget de notification, accessible en cliquant sur l’icône représentant une cloche dans le coin supérieur droit de Adobe Experience Cloud. Les paramètres de notification peuvent être configurés.

Lorsqu’une notification est reçue, il est possible de cliquer dessus pour ouvrir AEM Centre de notification d’as a Cloud Service avec une fenêtre contextuelle présentant un contexte supplémentaire expliquant l’action recommandée pour un client.

Outre l’affichage d’informations sur la notification qui vient d’être cliquée, le Centre de notification sert de hub où vous pouvez afficher et gérer l’ensemble des notifications actuelles et antérieures. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

Il existe deux catégories de notifications de haut niveau :

1. Incidents : un événement s’est produit, qui nécessite généralement une résolution rapide. Par exemple, la résolution d’une file d’attente bloquée
1. Proactif : l’Adobe a une recommandation pour une action qu’un client doit entreprendre dans un avenir proche. Par exemple, pour arrêter de référencer une interface utilisateur obsolète.

Voir [tableau ci-dessous](#current-notification-types) pour les notifications actuellement prises en charge.

Dans l&#39;écran Centre de notifications, vous pouvez sélectionner un programme et un environnement spécifiques, ce qui a pour effet de filtrer cette portée.

## Configuration {#configuration}

Vous pouvez suivre les étapes ci-dessous pour configurer la réception de notifications :

1. Créez les profils de produit suivants, comme décrit [dans cet article](/help/journey-onboarding/user-groups.md), en attribuant les identifiants d’Adobe appropriés de votre organisation à ces profils.
1. Déterminez les paramètres de configuration des notifications. [Sur cette page](https://experience.adobe.com/preferences/notification-section), assurez-vous que l’option Abonnement du Experience Manager est activée et que la variable **Autres** est sélectionnée. En outre, il est recommandé de définir la section Emails sur **Notifications instantanées** ainsi, vous recevez des notifications immédiatement après un incident.

>[!NOTE]
>Les abonnements fonctionnent au niveau de l’organisation, de sorte que les abonnés reçoivent des notifications pour tous les programmes et environnements de ces programmes.

## Flux d’utilisateur détaillé {#detailed-user-flow}

Cliquer sur l’email vous permet d’accéder au Centre de notifications. Une fenêtre contextuelle indiquant le contexte de la notification sur laquelle vous avez cliqué et, dans certains cas, des liens vers des informations supplémentaires décrivant comment prendre des mesures correctives.

![Détails de l’incident](/help/operations/assets/incident-details.png)

Cliquez sur le bouton **En savoir plus** accède à cet article par le biais de ce lien, où la notification peut être référencée dans le tableau ci-dessous, qui fournit des conseils sur les actions à entreprendre.

Dans le Centre de notifications, vous pouvez voir une liste d’autres notifications récentes. Il est recommandé d’utiliser la liste Actions afin de signaler à l’Adobe que votre organisation est au courant de la tâche et de résoudre ultérieurement la notification lorsque des mesures correctives ont été prises.

![Liste de notifications](/help/operations/assets/notification-list.png)

Dans la plupart des cas, la notification doit fournir tout le contexte nécessaire pour résoudre le problème. Toutefois, si vous avez des questions à propos de l’assistance Adobe, vous pouvez cliquer sur le bouton **Contacter le support technique** lien dans la fenêtre contextuelle de notification. Vous obtiendrez alors un formulaire d’où vous pourrez décrire la question et l’envoyer pour créer le ticket d’assistance, qui inclura également une référence à la notification spécifique afin qu’un ingénieur d’assistance Adobe ait le contexte approprié.

![Contacter le support 1](/help/operations/assets/contact-support1.png)

![Contacter le support 2](/help/operations/assets/contact-support2.png)

Comme tous les tickets d’assistance, il apparaîtra dans la variable [Onglet Cas d’assistance Adobe Admin Console](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html), où vous pouvez effectuer le suivi et ajouter des commentaires supplémentaires.

![Prise en charge des Admin Console](/help/operations/assets/admin-console-support.png)

## Types de notification actuels {#current-notification-types}

Le tableau ci-dessous répertorie les types de notification actuellement pris en charge.

| Type de notification | Profil de produit associé | Correction |
|---|---|---|
| File d’attente de réplication bloquée | Incident | Débloquer la file d’attente en suivant les instructions de la section [Documentation de réplication](/help/operations/replication.md#troubleshooting) |
| Expiration du certificat S2S | Proactif | Découvrez comment actualiser des informations d’identification dans le [Documentation sur la génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) |

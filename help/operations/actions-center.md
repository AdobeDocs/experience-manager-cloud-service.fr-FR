---
title: Centre d’actions
description: Tirez parti du Centre d’actions pour agir facilement sur les incidents et d’autres informations importantes
hidefromtoc: true
hide: true
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 17%

---

# Centre d’actions {#actions-center}

>[!NOTE]
>Cette fonctionnalité n’a pas été publiée.

AEM as Cloud Service envoie des notifications par e-mail à Actions Center en cas d’incident critique nécessitant une action immédiate, ainsi que des recommandations proactives pour les optimisations. Par exemple, une file d’attente bloquée ou un jeu d’informations d’identification arrivant à expiration ; l’ensemble complet des types de notifications du Centre d’actions est visible dans la variable [tableau ci-dessous](#supported-notification-types), qui s’agrandira au fil du temps.

Lorsqu’une notification électronique du Centre d’actions est reçue, vous pouvez cliquer dessus pour ouvrir le Centre d’actions d’AEM as a Cloud Service, avec une fenêtre contextuelle présentant un contexte supplémentaire expliquant l’action à entreprendre par un client.

Outre l’affichage d’informations sur la notification qui vient d’être cliquée, le Centre d’actions sert de centre d’actions où vous pouvez afficher et gérer l’ensemble des notifications actuelles et antérieures. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

Il existe deux catégories de notifications de haut niveau qui apparaissent dans le centre d’actions :

1. Les incidents opérationnels : un événement s’est produit, ce qui nécessite généralement une résolution rapide. Par exemple, la résolution d’une file d’attente bloquée.
1. Recommandations proactives : l’Adobe a une recommandation pour une action qu’un client doit entreprendre prochainement. Par exemple, pour arrêter de référencer une interface utilisateur obsolète.

Voir [tableau ci-dessous](#supported-notification-types) pour les notifications actuellement prises en charge dans le centre d’actions.

Dans le Centre d’actions, vous pouvez sélectionner un programme et un environnement spécifiques, ce qui a pour effet de filtrer cette portée.

## Configuration {#configuration}

Pour configurer la réception de notifications par courrier électronique par le centre d’actions, créez les profils de produit décrits. [dans cet article](/help/journey-onboarding/notification-profiles.md), à savoir Notification d’incident - Cloud Service et Notification proactive - Cloud Service. Attribuez également les identifiants d’Adobe appropriés de votre organisation à ces profils. Cela permet à un administrateur de déterminer les utilisateurs qui peuvent recevoir ces notifications par courrier électronique.

>[!NOTE]
>Les notifications par courrier électronique du Centre d’actions fonctionnent au niveau de l’organisation, de sorte que les abonnés recevront des notifications pour tous les programmes et environnements de ces programmes.

## Flux d’utilisateur détaillé {#detailed-user-flow}

Cliquez sur l’e-mail pour accéder au Centre d’actions. Une fenêtre contextuelle s’affiche pour indiquer le contexte de la notification sur laquelle vous avez cliqué. Dans certains cas, des liens sont renvoyés vers des informations supplémentaires décrivant comment prendre des mesures correctives.

![Détails de l’incident](/help/operations/assets/incident-details.png)

Cliquez sur le bouton **En savoir plus** accède à cet article par le biais de ce lien, où le type de notification peut être référencé dans la variable [tableau des types de notification pris en charge](#supported-notification-types) ci-dessous, qui fournit des conseils sur les actions à entreprendre.

Le centre d’actions contient une liste d’autres notifications récentes. Il est recommandé d’utiliser la liste Actions afin de reconnaître à l’Adobe que votre organisation est au courant de la tâche et de résoudre la notification ultérieurement lorsque des mesures correctives ont été prises.

![Liste de notifications](/help/operations/assets/notification-list.png)

Dans la plupart des cas, la fenêtre contextuelle doit fournir tout le contexte nécessaire pour résoudre le problème. Toutefois, si vous souhaitez poser des questions à l’assistance Adobe, vous pouvez cliquer sur le lien **Contacter le support** dans la fenêtre contextuelle de la Vous obtiendrez alors un formulaire d’où vous pourrez décrire la question et l’envoyer pour créer un ticket d’assistance, qui inclura également une référence à la notification spécifique afin qu’un ingénieur d’assistance Adobe dispose du contexte approprié.

![Contacter l’assistance 1](/help/operations/assets/contact-support1.png)

![Contacter l’assistance 2](/help/operations/assets/contact-support2.png)

Comme tous les tickets d’assistance, il apparaîtra dans l’[onglet Cas d’assistance d’Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/support-for-enterprise.html) où vous pourrez effectuer le suivi et ajouter des commentaires supplémentaires.

![Assistance d’Admin Console](/help/operations/assets/admin-console-support.png)

## Quelles Notifications S’Affichent ? {#which-notification}

AEM as a Cloud Service comporte plusieurs types de notifications, mais seul un sous-ensemble apparaît dans le Centre d’actions, comme illustré dans le tableau ci-dessous.

| Type de notification | Description | Comment configurer | Apparaît dans le Centre d’actions |
|---|---|---|---|
| Incidents opérationnels | Des incidents critiques nécessitant une action immédiate | Utilisateur affecté au profil de produit &quot;Notification d’incident - Cloud Service&quot; | X |
| Recommandations proactives | Optimisations qui doivent être planifiées | Utilisateur affecté au profil de produit &quot;Notification proactive - Cloud Service&quot; | X |
| Statuts du pipeline de Cloud Manager | Informations sur l’état de vos pipelines | Utilisateur avec des rôles Propriétaire de l’entreprise, Responsable de programme ou Responsable de déploiement, case à cocher &quot;Autres&quot; sélectionnée dans [Préférences Experience Cloud](https://experience.adobe.com/preferences), comme [décrit ici](/help/implementing/cloud-manager/notifications.md). |   |

## Types de notification pris en charge {#supported-notification-types}

Le tableau suivant répertorie les types de notifications actuellement pris en charge dans le Centre d’actions.

| Type de notification | Profil de produit associé | Mesure corrective |
|---|---|---|
| File d’attente de réplication bloquée | Incident | Débloquer la file d’attente en suivant les instructions de la [documentation de réplication](/help/operations/replication.md#troubleshooting) |
| Expiration du certificat S2S | Proactif | Découvrez comment actualiser des informations d’identification dans la [documentation sur la génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials). |


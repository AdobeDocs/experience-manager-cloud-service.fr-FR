---
title: Centre de notifications
description: Tirez parti du Centre de notification pour prendre des mesures appropriées concernant les incidents et d'autres informations importantes
hidefromtoc: true
hide: true
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: 3aa753fb5cc5130ced7e9baafde63e8825394dce
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# Centre de notifications {#notification-center}

>[!NOTE]
>Cette fonctionnalité n’a pas été publiée.

AEM as Cloud Service envoie des notifications en cas d’incident critique nécessitant une action immédiate, ainsi que des recommandations proactives pour les optimisations. Par exemple, une file d’attente bloquée ou un jeu d’informations d’identification arrivant à expiration ; l’ensemble complet des types de notification peut être consulté dans la variable [tableau ci-dessous](#supported-notification-types), qui s’agrandira au fil du temps.

Ces notifications peuvent être configurées pour être reçues par email et sous le widget de notification, accessible en cliquant sur l’icône représentant une cloche dans le coin supérieur droit de Adobe Experience Cloud.

Lorsqu’une notification est reçue, il est possible de cliquer dessus pour ouvrir le centre de notification d’AEM as a Cloud Service avec une fenêtre contextuelle présentant un contexte supplémentaire expliquant l’action à entreprendre par un client.

Outre l’affichage d’informations sur la notification qui vient d’être cliquée, le Centre de notification sert de hub où vous pouvez afficher et gérer l’ensemble des notifications actuelles et antérieures. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

Il existe deux catégories de notifications de haut niveau qui apparaissent dans le Centre de notifications :

1. Les incidents opérationnels : un événement s’est produit, ce qui nécessite généralement une résolution rapide. Par exemple, la résolution d’une file d’attente bloquée.
1. Recommandations proactives : l’Adobe a une recommandation pour une action qu’un client doit entreprendre prochainement. Par exemple, pour arrêter de référencer une interface utilisateur obsolète.

Voir [tableau ci-dessous](#supported-notification-types) pour les notifications actuellement prises en charge.

Dans le Centre de notification, vous pouvez sélectionner un programme et un environnement spécifiques, ce qui a pour effet de filtrer cette portée.

## Configuration {#configuration}

Pour configurer la réception de notifications, procédez comme suit :

1. Créez les profils de produit suivants, comme décrit [dans cet article](/help/journey-onboarding/notification-profiles.md), attribuant également les identifiants d’Adobe appropriés de votre organisation à ces profils. Cela permet à un administrateur de déterminer quels utilisateurs peuvent recevoir ces notifications.
1. Chaque utilisateur affecté à l’étape précédente peut configurer la manière dont il souhaite recevoir ses notifications. Sur le [page Préférences de l’Experience Cloud](https://experience.adobe.com/preferences/notification-section), assurez-vous que l’abonnement du Experience Manager est activé et que la variable **Incidents opérationnels** et **Recommandations proactives** les cases à cocher sont sélectionnées pour les colonnes in-app et email (voir l’image ci-dessous). En outre, il est recommandé de définir la section Emails sur **Notifications instantanées** par conséquent, les notifications sont reçues immédiatement en cas d’incident.

![Configuration des abonnements](/help/operations/assets/configure-subscriptions.png)

>[!NOTE]
>Les notifications fonctionnent au niveau de l’organisation, de sorte que les abonnés reçoivent des notifications pour tous les programmes et environnements de ces programmes.

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

## Quelles Notifications S’Affichent ? {#which-notification}

AEM as a Cloud Service comporte plusieurs types de notifications, mais un seul sous-ensemble apparaît dans le Centre de notifications, comme illustré dans le tableau ci-dessous.

| Type de notification | Description | Comment configurer | Apparaît dans le Centre de notification |
|---|---|---|---|
| Incidents opérationnels | Des incidents critiques nécessitant une action immédiate | Utilisateur affecté au profil de produit &quot;Notification d’incident - Cloud Service&quot;, case à cocher &quot;Incidents opérationnels&quot; sélectionnée dans [Préférences Experience Cloud](https://experience.adobe.com/preferences) | X |
| Recommandations proactives | Optimisations qui doivent être planifiées | Utilisateur affecté au profil de produit &quot;Notification proactive - Cloud Service&quot;, case à cocher &quot;Recommandations proactives&quot; sélectionnée dans [Préférences Experience Cloud](https://experience.adobe.com/preferences) | X |
| Statuts du pipeline de Cloud Manager | Informations sur l’état de vos pipelines | Utilisateur avec des rôles Propriétaire de l’entreprise, Responsable de programme ou Responsable de déploiement, case à cocher &quot;Autres&quot; sélectionnée dans [Préférences Experience Cloud](https://experience.adobe.com/preferences) |  |

## Types de notification pris en charge {#supported-notification-types}

Le tableau suivant répertorie les types de notification actuellement pris en charge.

| Type de notification | Profil de produit associé | Correction |
|---|---|---|
| File d’attente de réplication bloquée | Incident | Débloquer la file d’attente en suivant les instructions de la section [Documentation de réplication](/help/operations/replication.md#troubleshooting) |
| Expiration du certificat S2S | Proactif | Découvrez comment actualiser des informations d’identification dans le [Documentation sur la génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) |


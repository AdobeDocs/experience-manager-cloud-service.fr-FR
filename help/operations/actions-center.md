---
title: Centre d’actions
description: Tirez parti du Centre d’actions pour agir facilement sur les incidents et d’autres informations importantes
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
feature: Operations
role: Admin
source-git-commit: 22d5975a0c4ee180bbcda906b035d306a352b752
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 53%

---

# Centre d’actions {#actions-center}

AEM as a Cloud Service envoie au Centre d’actions des notifications par e-mail en cas d’incident critique nécessitant une action immédiate, ainsi que des recommandations proactives pour les optimisations. Ces incidents peuvent être par exemple une file d’attente bloquée ou un jeu d’informations d’identification arrivant à expiration ; l’ensemble des types de notification du Centre d’actions peut être consulté dans le [tableau ci-dessous](#supported-notification-types), qui s’agrandira au fil du temps.

Lorsqu’une notification par e-mail du Centre d’actions est reçue, vous pouvez cliquer dessus pour ouvrir le Centre d’actions d’AEM as a Cloud Service avec une fenêtre contextuelle présentant un contexte supplémentaire expliquant l’action à entreprendre par un client.

Outre l’affichage d’informations sur la notification par e-mail ouverte, le Centre d’actions sert de hub où vous pouvez afficher et gérer l’ensemble des notifications actuelles et antérieures. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers do not find it) -->

Deux catégories de notifications de haut niveau apparaissent dans le Centre d’actions :

1. Incidents opérationnels : il s’agit d’événements qui nécessitent généralement une résolution rapide. Par exemple, la résolution d’une file d’attente bloquée.
1. Recommandations proactives : Adobe recommande au client ou à la cliente une action à effectuer dans un avenir proche. Par exemple, pour arrêter de référencer une interface utilisateur obsolète.

Consultez le [tableau ci-dessous](#supported-notification-types) pour voir les notifications actuellement prises en charge dans le Centre d’actions.

Depuis le Centre d’actions, vous pouvez sélectionner un programme et un environnement spécifiques et réaliser ainsi un filtrage pour cette portée.

## Configuration {#configuration}

Pour configurer la réception de notifications par e-mail par le Centre d’actions, créez les profils de produit décrits [dans cet article](/help/journey-onboarding/notification-profiles.md), à savoir Notification d’incident - Cloud Service et Notification proactive - Cloud Service. Attribuez également les identifiants Adobe appropriés de votre organisation à ces profils. Cela permet à un administrateur ou une administratrice de déterminer quels utilisateurs et utilisatrices peuvent recevoir ces notifications par e-mail.

>[!NOTE]
>Les notifications par e-mail du Centre d’actions fonctionnent au niveau de l’organisation, de sorte que les personnes abonnées reçoivent des notifications pour tous les programmes et environnements de ces programmes.

## Flux d’utilisateur détaillé {#detailed-user-flow}

Cliquez sur l’e-mail pour accéder au Centre d’actions. Une fenêtre contextuelle affiche le contexte de la notification sur laquelle vous avez cliqué et, dans certains cas, des liens vers des informations supplémentaires décrivant comment prendre des mesures correctives. Vous pouvez également accéder directement au Centre d’actions à l’adresse [https://experience.adobe.com/aem/actions-center](https://experience.adobe.com/aem/actions-center/), où vous pouvez sélectionner le programme et l’environnement appropriés.

![Détails de l’incident](/help/operations/assets/incident-details.png)

En cliquant sur le lien **En savoir plus**, la personne utilisatrice est dirigée vers cet article, où le type de notification peut être référencé dans le [tableau des types de notification pris en charge](#supported-notification-types) ci-dessous, qui fournit des conseils sur les actions à entreprendre.

Dans le Centre d’actions, vous pouvez voir une liste d’autres notifications récentes. Il est recommandé d’accuser réception d’une notification à l’aide de la liste des actions pour signaler à Adobe que votre organisation est au courant de la tâche, et de résoudre ultérieurement la notification lorsque des mesures correctives ont été prises.

![Liste de notifications](/help/operations/assets/notification-list.png)

Dans la plupart des cas, la fenêtre contextuelle doit fournir tout le contexte nécessaire pour résoudre le problème. Cependant, si vous avez des questions à propos de l’assistance Adobe, vous pouvez cliquer sur le lien **Contacter l’assistance** dans la fenêtre contextuelle. Vous obtiendrez alors un formulaire sur lequel vous pourrez poser votre question, puis vous pourrez l’envoyer pour créer un ticket d’assistance, qui inclura également une référence à la notification spécifique afin qu’un ingénieur ou une ingénieure de l’assistance Adobe dispose du contexte nécessaire.

![Contacter l’assistance 1](/help/operations/assets/contact-support1.png)

![Contacter l’assistance 2](/help/operations/assets/contact-support2.png)

Comme tous les tickets d’assistance, il apparaîtra dans l’[onglet Cas d’assistance d’Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/support-for-enterprise.html) où vous pourrez effectuer le suivi et ajouter des commentaires supplémentaires.

![Assistance d’Admin Console](/help/operations/assets/admin-console-support.png)

## Quelles notifications s’affichent ? {#which-notification}

AEM as a Cloud Service comporte plusieurs types de notifications, mais un seul sous-ensemble apparaît dans le Centre d’actions, tel qu’illustré dans le tableau ci-dessous.

| Type de notification | Description | Comment configurer | S’affiche dans le Centre d’actions |
|---------------------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| Incidents opérationnels | Des incidents critiques nécessitant une action immédiate. | Personne affectée au profil de produit « Notification d’incident - Cloud Service » | X |
| Recommandations proactives | Optimisations qui doivent être planifiées. | Personne affectée au profil de produit « Notification proactive - Cloud Service » | X |
| Statuts du pipeline de Cloud Manager | Informations sur l’état de vos pipelines | Utilisateur avec des rôles Propriétaire de l’entreprise, Responsable de programme ou Responsable de déploiement, case à cocher &quot;Autres&quot; sélectionnée dans [Préférences Experience Cloud](https://experience.adobe.com/fr/preferences), comme [décrit ici](/help/implementing/cloud-manager/notifications.md). |                           |

## Types de notifications pris en charge {#supported-notification-types}

Le tableau suivant répertorie les types de notifications actuellement pris en charge dans le Centre d’actions. Les notifications sont actuellement limitées aux environnements de production.

| Type de notification | Profil de produit associé | Mesure corrective |
|---------------------------------|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| File d’attente de réplication bloquée | Incident | Débloquer la file d’attente en suivant les instructions de la [documentation de réplication](/help/operations/replication.md#troubleshooting) |
| Requête GraphQL persistante non valide | Incident | Corrigez la requête GraphQL non valide en référençant la [documentation de dépannage des requêtes GraphQL persistantes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/persisted-queries-troubleshoot.html) |
| Pic de trafic à l’origine | Incident | Protect votre origine en configurant des règles de filtrage du trafic de limite de taux qui se déclenchent à des seuils inférieurs à ceux du pic de trafic par défaut à l’alerte d’origine.  Consultez la section [Blocking DoS and DDoS attaquant à l’aide de règles de trafic](/help/security/traffic-filter-rules-including-waf.md#blocking-dos-and-ddos-attacks-using-traffic-filter-rules) de la documentation sur les règles de filtrage du trafic, qui fait référence à un tutoriel. |
| Règles de filtrage du trafic CDN déclenchées | Incident | Si la règle de filtrage du trafic correspondante reflète une attaque et que votre site ne bloque pas ce trafic, protégez votre site en configurant une règle de filtrage du trafic en mode de blocage. Consultez la section [Protection des sites Web avec des règles de filtrage du trafic (y compris les règles WAF)](/help/security/traffic-filter-rules-including-waf.md#tutorial-protecting-websites) de la documentation sur les règles de filtrage du trafic, qui fait référence à un tutoriel. |
| Les pages contiennent un grand nombre de noeuds | Proactif | Réduire le nombre total de noeuds dans une page. Reportez-vous à la [documentation sur la complexité de la page](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/pcx) | |
| Grand nombre d’instances de workflow en cours d’exécution | Proactif | Arrêtez les workflows en cours d’exécution qui ne sont plus nécessaires. Découvrez comment [configurer une tâche de purge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance) |               |
| Expiration du certificat S2S | Proactif | Découvrez comment actualiser des informations d’identification dans la [documentation sur la génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials). | Nombre de connexions élevé | Proactif | En savoir plus sur le pool de connexions dans la [documentation sur le pool de connexions avec la mise en réseau avancée](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| Mappage des utilisateurs du service obsolète | Proactif | Découvrez comment utiliser le nouveau format de mappage des utilisateurs du service Sling, comme indiqué dans [Meilleures pratiques pour le mappage des utilisateurs du service Sling et la définition d’utilisateur du service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/best-practices-for-sling-service-user-mapping-and-service-user-definition) |
| Nombre de connexions élevé | Proactif | Pour en savoir plus sur le pool de connexions, consultez la [ documentation sur les réseaux avancés](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |  |
| Utilisateurs ajoutés directement au groupe personnalisé | Proactif | Les utilisateurs doivent être ajoutés aux groupes IMS appropriés et ces groupes IMS doivent être ajoutés en tant que membres des groupes AEM. Alignement avec [Bonnes pratiques IMS](/help/security/ims-support.md) | |
| Contenu JCR manquant | Proactif | Ajoutez le noeud de contenu JCR manquant. Reportez-vous à la [documentation Assets Content Validator](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv) | |
| Workflows terminés non purgés | Proactif | Réduisez le nombre d’instances de workflow et améliorez les performances en purgeant les instances de workflow qui ont plus de 90 jours. Découvrez comment [configurer les tâches de maintenance](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance) | |
| Type de ressource Sling manquant dans la page | Proactif | Ajoutez le noeud de type de ressource Sling manquant. Reportez-vous à la [documentation Assets Content Validator](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv) |

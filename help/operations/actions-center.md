---
title: Centre d’actions
description: Tirez parti du Centre d’actions pour agir de manière pratique sur les incidents et obtenir d’autres informations importantes.
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
feature: Operations
role: Admin
source-git-commit: 2e257634313d3097db770211fe635b348ffb36cf
workflow-type: tm+mt
source-wordcount: '1187'
ht-degree: 45%

---

# Centre d’actions {#actions-center}

AEM as a Cloud Service envoie au Centre d’actions des notifications par e-mail en cas d’incident critique nécessitant une action immédiate, ainsi que des recommandations proactives pour les optimisations. Ces incidents peuvent être par exemple une file d’attente bloquée ou un jeu d’informations d’identification arrivant à expiration ; l’ensemble des types de notification du Centre d’actions peut être consulté dans le [tableau ci-dessous](#supported-notification-types), qui s’agrandira au fil du temps.

Lorsqu’une notification par e-mail du Centre d’actions est reçue, il est possible de cliquer dessus pour ouvrir le Centre d’actions d’AEM as a Cloud Service avec un pop-up affichant un contexte supplémentaire expliquant l’action au client ou à la cliente.

Outre l’affichage d’informations sur la notification par e-mail ouverte, le Centre d’actions sert de hub où vous pouvez afficher et gérer l’ensemble des notifications actuelles et antérieures. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers do not find it) -->

Deux catégories de notifications de haut niveau apparaissent dans le Centre d’actions :

1. Incidents opérationnels : il s’agit d’événements qui nécessitent généralement une résolution rapide. Par exemple, la résolution d’une file d’attente bloquée.
1. Recommandations proactives : Adobe recommande au client ou à la cliente une action à effectuer dans un avenir proche. Par exemple, pour arrêter de référencer une interface utilisateur obsolète.

Consultez le [tableau ci-dessous](#supported-notification-types) pour voir les notifications actuellement prises en charge dans le Centre d’actions.

Depuis le Centre d’actions, vous pouvez sélectionner un programme et un environnement spécifiques et réaliser ainsi un filtrage pour cette portée.

## Configuration {#configuration}

Pour configurer la réception des notifications par e-mail du Centre des actions, créez les profils de produit comme décrit dans [Profils de notification](/help/journey-onboarding/notification-profiles.md), à savoir Notification d’incident - Cloud Service et Notification proactive - Cloud Service. Attribuez également les identifiants Adobe appropriés de votre organisation à ces profils. Cela permet à un administrateur ou une administratrice de déterminer quels utilisateurs et utilisatrices peuvent recevoir ces notifications par e-mail.

>[!NOTE]
>Les notifications par e-mail du Centre d’actions fonctionnent au niveau de l’organisation, de sorte que les personnes abonnées reçoivent des notifications pour tous les programmes et environnements de ces programmes.

## Flux d’utilisateur détaillé {#detailed-user-flow}

Cliquez sur l’e-mail pour accéder au Centre d’actions , avec un pop-up affichant le contexte de la notification sur laquelle vous avez cliqué et, dans certains cas, des liens vers des informations supplémentaires décrivant comment prendre des mesures correctives. Vous pouvez également accéder directement au Centre d’actions à l’adresse [https://experience.adobe.com/aem/actions-center](https://experience.adobe.com/aem/actions-center/), où vous pouvez sélectionner le programme et l’environnement appropriés.

![Détails de l’incident](/help/operations/assets/incident-details.png)

En cliquant sur le lien **En savoir plus**, la personne utilisatrice est dirigée vers cet article, où le type de notification peut être référencé dans le [tableau des types de notification pris en charge](#supported-notification-types) ci-dessous, qui fournit des conseils sur les actions à entreprendre.

Dans le Centre d’actions, vous pouvez voir une liste d’autres notifications récentes. Il est recommandé d’accuser réception d’une notification à l’aide de la liste des actions pour signaler à Adobe que votre organisation est au courant de la tâche, et de résoudre ultérieurement la notification lorsque des mesures correctives ont été prises.

![Liste de notifications](/help/operations/assets/notification-list.png)

Dans la plupart des cas, le pop-up doit fournir tout le contexte nécessaire à la résolution du problème. Toutefois, si vous avez des questions concernant l’assistance Adobe, vous pouvez cliquer sur le lien **Contacter l’assistance** dans la pop-up. Vous obtiendrez alors un formulaire sur lequel vous pourrez poser votre question, puis vous pourrez l’envoyer pour créer un ticket d’assistance, qui inclura également une référence à la notification spécifique afin qu’un ingénieur ou une ingénieure de l’assistance Adobe dispose du contexte nécessaire.

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
| Statuts du pipeline de Cloud Manager | Informations sur l’état de vos pipelines | Personne avec des rôles Propriétaire de l’entreprise, Responsable de programme ou Responsable de déploiement, case à cocher « Autres » sélectionnée dans [Préférences Experience Cloud](https://experience.adobe.com/fr/preferences), voir [Notifications](/help/implementing/cloud-manager/notifications.md). |                           |

## Types de notifications pris en charge {#supported-notification-types}

Le tableau suivant répertorie les types de notification actuellement pris en charge dans le Centre de maintenance. Les notifications sont actuellement limitées aux environnements de production.

| Type de notification | Profil de produit associé | Mesure corrective |
|---------------------------------|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| File d’attente de réplication bloquée | Incident | Débloquer la file d’attente en suivant les instructions de la [documentation de réplication](/help/operations/replication.md#troubleshooting) |
| Requête persistante GraphQL non valide | Incident | Corrigez la requête GraphQL non valide en vous référant à la [documentation de dépannage des requêtes GraphQL persistantes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/persisted-queries-troubleshoot.html?lang=fr) |
| Pic de trafic à l’origine | Incident | Protégez votre origine en configurant des règles de filtrage du trafic avec limite de débit qui se déclenchent à des seuils inférieurs au pic de trafic par défaut lors de l’alerte d’origine.  Consultez la section [&#x200B; Blocage des attaques DoS et DDoS à l’aide de règles de trafic &#x200B;](/help/security/traffic-filter-rules-including-waf.md#blocking-dos-and-ddos-attacks-using-traffic-filter-rules) de la documentation Règles de filtrage du trafic , qui fait référence à un tutoriel. |
| Règles de filtres de trafic CDN déclenchées | Incident | Si la règle de filtrage du trafic correspondante reflète une attaque et que votre site ne bloque pas ce trafic, protégez votre site en configurant une règle de filtrage du trafic en mode blocage. Consultez la section [&#x200B; Protection des sites web avec des règles de filtrage du trafic (y compris les règles WAF)](/help/security/traffic-filter-rules-including-waf.md#tutorial-protecting-websites) de la documentation Règles de filtrage du trafic , qui fait référence à un tutoriel. |
| Erreurs de transfert du journal Splunk | Incident | Vérifiez que le point d’entrée Splunk fonctionne et est accessible à partir de l’environnement AEM Cloud Service. Pour plus d’informations sur le transfert de journal, consultez la [documentation sur le transfert de journal Splunk](/help/implementing/developing/introduction/logging.md#splunk-logs). Si vous avez besoin d’aide pour résoudre les problèmes ou si vous devez apporter des modifications à votre configuration de journalisation, envoyez un ticket d’assistance à Adobe. |
| Les pages contiennent un grand nombre de nœuds | Proactif | Réduire le nombre total de nœuds dans une page Consultez la [documentation sur la complexité de la page](https://experienceleague.adobe.com/fr/docs/experience-manager-pattern-detection/table-of-contents/pcx) |
| Grand nombre d’instances de workflow en cours d’exécution | Proactif | Arrêtez les workflows en cours d’exécution qui ne sont plus nécessaires. Découvrez comment [configurer une tâche de purge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance) |
| Expiration du certificat S2S | Proactif | Découvrez comment actualiser des informations d’identification dans la [documentation sur la génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials). |
| Nombre élevé de connexions | Proactif | Découvrez le pool de connexions dans [Documentation sur le pool de connexions et la mise en réseau avancée](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| Mappage des utilisateurs de services obsolètes | Proactif | Découvrez comment utiliser le nouveau format de mappage des utilisateurs du service Sling, comme indiqué dans [Bonnes pratiques pour le mappage des utilisateurs du service Sling et la définition d’utilisateur du service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/best-practices-for-sling-service-user-mapping-and-service-user-definition) |
| Nombre élevé de connexions | Proactif | Découvrez le pool de connexions dans la [documentation de mise en réseau avancée](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| Utilisateurs ajoutés directement au groupe personnalisé | Proactif | Les utilisateurs doivent être ajoutés aux groupes IMS appropriés et ces groupes IMS doivent être ajoutés en tant que membres des groupes AEM. Alignement sur les bonnes pratiques [IMS](/help/security/ims-support.md) |
| Contenu JCR manquant | Proactif | Ajoutez le nœud de contenu JCR manquant. Consultez la [documentation du programme de validation de contenu Assets](https://experienceleague.adobe.com/fr/docs/experience-manager-pattern-detection/table-of-contents/acv) |
| Workflows terminés non purgés | Proactif | Réduisez le nombre d’instances de workflow et améliorez les performances en purgeant les instances de workflow qui ont plus de 90 jours. Découvrez comment [&#x200B; configurer des tâches de maintenance &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance) |
| Type de ressource Sling manquant dans la page | Proactif | Ajoutez le nœud de type de ressource Sling manquant. Consultez la [documentation du programme de validation de contenu Assets](https://experienceleague.adobe.com/fr/docs/experience-manager-pattern-detection/table-of-contents/acv) |
| Requête Lente | Proactif | Corrigez les requêtes lentes en définissant des définitions d’index correctes, comme suggéré par l’aide-mémoire sur les requêtes [&#x200B; JCQ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/JCR_query_cheatsheet-v1.1.pdf?lang=fr) |
| Requête Sans Index | Proactif | Évitez d’exécuter une requête qui n’utilise pas d’index - [lien vers la documentation sur l’indexation](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/indexing) |
| Alerte de bibliothèque obsolète | Proactif | Remplacez les packages obsolètes par leurs versions plus récentes recommandées, comme décrit dans l’article [&#x200B; Obsolescence &#x200B;](/help/release-notes/deprecated-removed-features.md), afin de garantir la sécurité et les performances de votre application |
| Alerte de configuration obsolète | Proactif | Remplacez les configurations obsolètes par leurs versions plus récentes recommandées, comme décrit dans l’article [&#x200B; Obsolescence &#x200B;](/help/release-notes/deprecated-removed-features.md), afin de garantir la sécurité et les performances de votre application |

---
title: Surveillance des infrastructures et des services dans AEM as a Cloud Service
description: Surveillance des infrastructures et des services dans AEM as a Cloud Service
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
source-git-commit: b1f6dfed5ac5a352750ea708324cd1a52997fc06
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Surveillance des infrastructures et des services dans AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service permet d’observer et de surveiller les aspects suivants : infrastructure, services et expérience utilisateur. Comme plusieurs solutions sont utilisées et qu’il existe plusieurs niveaux de surveillance, cette page est organisée en trois sections :

* [Disponibilité externe](#external-availability)
* [Surveillance des modules internes](#module-monitoring)
* [Observabilité des clients](#customer-observability)

AEM as a Cloud Service utilise des centaines de moniteurs natifs en mode cloud pour continuellement consigner l’état de chaque environnement (24/7) pendant 365 jours par an. Les définitions de moniteur ne sont pas statiques et sont continuellement examinées afin d’améliorer la capacité de détection précoce. Par ailleurs, des procédures d’appel sont mises en place pour répondre aux alertes par Adobe.

Si vous avez besoin d’informations sur d’autres types de surveillance, tels que la journalisation ou la surveillance via Cloud Manager, reportez-vous à la section [Ressources supplémentaires](#resources) .

## Disponibilité externe {#external-availability}

La disponibilité externe se compose de deux parties : Service Edge et surveillance personnalisée.

### Service Edge {#service-edge}

Tous vos environnements as a Cloud Service AEM sont surveillés pour assurer leur disponibilité. Toutefois, le service Edge Monitoring est configuré uniquement pour les environnements de production et les mesures sont utilisées pour calculer le contrat SLA du client. Il prend en compte l’exécution de l’environnement et le réseau de diffusion de contenu as a Cloud Service AEM. Le service Edge Monitoring utilise cinq emplacements distincts à proximité de la région de votre choix et vérifie régulièrement la disponibilité. L’indisponibilité d’un site déclenche une alerte et engage les équipes et les processus d’assistance sur appel de l’Adobe.

### Surveillance personnalisée {#custom-monitoring}

Grâce à la surveillance personnalisée, les clients ont la possibilité de fournir jusqu’à cinq URL de propriété web distinctes avant la variable [en direct](/help/journey-migration/go-live.md). Ces URL doivent être valides et renvoyer un code de réponse HTTP 200. Ces moniteurs prennent en charge les clients qui [apporter leur propre CDN](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) devant le réseau de diffusion de contenu de l’Adobe et tout routage de trafic externe utilisé devant AEM as a Cloud Service qui n’est pas sous le contrôle de l’Adobe. Les alertes résultant des contrôles de surveillance personnalisée impliquent les équipes et les processus d’assistance de l’Adobe.

## Surveillance des modules internes {#module-monitoring}

Bien que la disponibilité externe soit axée sur la surveillance des utilisateurs finaux, la surveillance des modules internes observe si les sous-systèmes architecturaux fonctionnent nominalement sans dégradation des fonctionnalités ou des performances. En cas de problème, des alertes sont déclenchées afin que les réparations puissent être effectuées automatiquement ou par l’intermédiaire de l’équipe d’exploitation, dans le but d’éviter une disponibilité compromise. Il existe différentes catégories d’moniteurs, présentées ci-dessous sont des exemples de contrôles :

* Le pourcentage d’attente du processeur ne dépasse pas un certain seuil.
* Les redéploiements d’instances ne dépassent pas une certaine fréquence.
* L’utilisation du disque est inférieure à un certain seuil.
* La taille du référentiel d’auteur se trouve dans certaines limites.
* Les opérations de sauvegarde sont terminées avec succès.
* L’intégrité et les performances de la base de données sont surveillées.
* Les services cloud AEM se comportent comme prévu, y compris aucune file d’attente de réplication bloquée, des données cohérentes et des requêtes performantes.

Des vérifications supplémentaires sont ajoutées aux environnements configurés pour Forms. Gardez à l’esprit que les définitions des contrôles ne sont pas statiques et sont sujettes à des modifications et des mises à jour.

## Observabilité des clients {#customer-observability}

Les clients peuvent utiliser la variable [Nouvelle surveillance des performances des applications relatives](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html) qui fournit des données de performances en temps réel collectées et tracées pour analyse et dépannage. En utilisant la suite de surveillance, les clients peuvent observer directement diverses mesures, telles que : Mesures de performances JVM, temps de transaction pour Java, appels externes en arrière-plan et appels de base de données.

## Ressources supplémentaires {#resources}

* [Nouvelle surveillance des performances des applications relatives](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html)
* [Journalisation pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html)
* [Surveiller les environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html)

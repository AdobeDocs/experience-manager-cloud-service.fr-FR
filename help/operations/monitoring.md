---
title: Surveillance des infrastructures et des services dans AEM as a Cloud Service
description: Surveillance des infrastructures et des services dans AEM as a Cloud Service
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 95%

---

# Surveillance des infrastructures et des services dans AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service permet d’observer et de surveiller l’infrastructure, les services et l’expérience utilisateur. Comme plusieurs solutions sont utilisées et qu’il existe plusieurs niveaux de surveillance, cette page est divisée en trois sections :

* [Disponibilité externe](#external-availability)
* [Surveillance des modules internes](#module-monitoring)
* [Observabilité des clients](#customer-observability)

AEM as a Cloud Service utilise des centaines de moniteurs natifs cloud pour évaluer en permanence l’état de chaque environnement, 24 h/24, 7 j/7 et 365 jours par an. Les définitions de moniteur ne sont pas statiques et sont continuellement examinées afin d’améliorer la capacité de détection précoce. Par ailleurs, Adobe a mis en place des procédures d’astreinte pour répondre aux alertes.

Si vous avez besoin d’informations sur d’autres types de surveillance, tels que la journalisation ou la surveillance via Cloud Manager, consultez les [ressources supplémentaires](#resources).

## Disponibilité externe {#external-availability}

La disponibilité externe se compose de deux volets : le service Edge et la surveillance personnalisée.

### Service Edge {#service-edge}

Tous vos environnements AEM as a Cloud Service sont surveillés pour assurer leur disponibilité. Toutefois, la surveillance Service Edge se destine uniquement aux environnements de production et les mesures sont utilisées pour calculer le contrat SLA du client. Elle prend en compte l’exécution de l’environnement et le réseau CDN d’AEM as a Cloud Service. La surveillance Service Edge utilise cinq sites distincts proches de la région que vous avez choisie et vérifie régulièrement leur disponibilité. L’indisponibilité d’un site déclenche une alerte et l’intervention des équipes d’astreinte et des processus d’assistance d’Adobe.

### Surveillance personnalisée {#custom-monitoring}

Avec la surveillance personnalisée, la clientèle peut éventuellement fournir jusqu’à cinq URL de propriété web distinctes avant la [mise en ligne](/help/journey-migration/go-live.md). Ces URL doivent être valides et renvoyer un code de réponse HTTP 200. Ces moniteurs prennent en charge la clientèle qui [place leur propre réseau CDN](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) en amont du réseau CDN Adobe et de tout routage de trafic externe utilisé en amont d’AEM as a Cloud Service qui n’est pas sous le contrôle d’Adobe. Les alertes résultant des contrôles de surveillance personnalisée impliquent les équipes et les processus d’assistance d’Adobe.

>[!NOTE]
>
> Cette fonctionnalité est uniquement proposée aux environnements de production et aux clients et clientes qui bénéficient de la [assistance cloud avancée](https://experienceleague.adobe.com/docs/support-resources/data-sheets/overview.html#support-add-ons?lang=fr). Pour toute question, contactez l’équipe chargée de votre compte d’Adobe.

## Surveillance des modules internes {#module-monitoring}

Bien que la disponibilité externe soit axée sur la surveillance des personnes utilisatrices finales, la surveillance des modules internes observe si les sous-systèmes architecturaux fonctionnent nominalement sans dégradation des fonctionnalités ou des performances. En cas de problème, des alertes sont déclenchées afin que les réparations puissent être effectuées automatiquement ou par l’intermédiaire de l’équipe en charge des opérations, dans le but d’éviter la compromission de la disponibilité. Il existe différentes catégories de moniteurs, en voici quelques exemples :

* Le pourcentage d’iowait du CPU ne dépasse pas un certain seuil.
* Les redéploiements d’instances ne dépassent pas une certaine fréquence.
* L’utilisation du disque est inférieure à un certain seuil.
* La taille du référentiel Auteur se situe dans certaines limites.
* Les opérations de sauvegarde sont terminées avec succès.
* L’intégrité et les performances de la base de données sont surveillées.
* Les services AEM Cloud se comportent comme prévu, notamment l’absence de files d’attente de réplication bloquées, des données cohérentes et des requêtes performantes.

Des vérifications supplémentaires sont ajoutées aux environnements configurés pour Forms. Vérifiez que les définitions de vérification ne sont pas statiques et qu’elles font l’objet de modifications et de mises à jour.

## Observabilité des clients et clientes {#customer-observability}

La clientèle peut utiliser la suite [Surveillance des performances des applications New Relic](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=fr) qui fournit des données de performances en temps réel collectées et tracées pour analyse et dépannage. En utilisant la suite de surveillance, la clientèle peut directement observer diverses métriques telles que : les mesures de performance JVM, la durée de transaction pour Java™, les appels externes en arrière-plan et les appels aux bases de données.

## Ressources supplémentaires {#resources}

* [Surveillance des performances des applications New Relic](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=fr)
* [Journalisation pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html?lang=fr)
* [Surveiller les environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html?lang=fr)

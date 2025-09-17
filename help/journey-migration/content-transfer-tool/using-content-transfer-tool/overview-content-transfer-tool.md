---
title: Présentation de l’outil de transfert de contenu
description: Découvrez comment utiliser l’outil de transfert de contenu pour transférer du contenu d’une instance AEM on-premise vers AEM as a Cloud Service
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
feature: Migration
role: Admin
source-git-commit: e73933acc3ff23d1456f03b288f2f842a6289ace
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 91%

---


# Présentation {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Présentation"
>abstract="Développé par Adobe, l’outil de transfert de contenu est utilisé pour délencher la migration de contenu existant entre une instance AEM source (on-premise ou AMS) et une instance AEM Cloud Service cible. Cet outil transfère également les groupes automatiquement."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr" text="Conseils et bonnes pratiques"

Développé par Adobe, l’outil de transfert de contenu est utilisé pour lancer la migration du contenu existant depuis une instance AEM source (on-premise ou AMS) vers une instance AEM Cloud Service cible.

Cet outil transfère également les groupes automatiquement.  Voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) pour plus d’informations.

L’outil de transfert de contenu intègre le processus de transfert de contenu à Cloud Acceleration Manager. Cela permet à la personne utilisatrice de bénéficier de tous les avantages suivants :

* Une méthode en libre-service pour extraire une seule fois un ensemble de migration et l’ingérer dans plusieurs environnements en parallèle
* Amélioration de l’expérience utilisateur grâce à une meilleure gestion des états de chargement, des mécanismes de sécurisation et des erreurs
* Conservation des journaux d’ingestion et leur constante disponibilité à des fins de dépannage
* Rapports de validation et de migration des entités principales disponibles pour validation

## Phases de l’outil de transfert de contenu {#phases-content-transfer-tool}

Le transfert de contenu comporte deux phases :

1. **Extraction** : l’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée *ensemble de migration*. Un *ensemble de migration* est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service.

   Pour plus d’informations, consultez la section [Processus d’extraction au cours du transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md).

1. **Ingestion** : l’ingestion désigne l’ingestion de contenu à partir de l’*ensemble de migration* dans l’instance Cloud Service cible.

   Pour plus d’informations, consultez [Processus d’ingestion au cours du transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

## Attributs d’un ensemble de migration {#attributes-migration-set}

Un ensemble de migration possède les attributs suivants :

* Avec la nouvelle version, vous pouvez créer un maximum de dix jeux de migration au sein d’un projet créé dans Cloud Acceleration Manager.
* Chaque ensemble de migration doit avoir un nom unique.

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Au cours de la phase d’extraction, pour ***compléter*** un ensemble de migration existant, l’option de *remplacement* doit être désactivée. Pour en savoir plus, voir [Extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process).

Lors de la phase d’ingestion, pour appliquer le contenu différentiel en plus du contenu actuel, l’option *Effacer* doit être désactivée. Pour en savoir plus, voir [Ingestion de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process).

## Expiration de l’ensemble de migration {#migration-set-expiry}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_migrationset_expiry"
>title="Expiration d’un ensemble de migration"
>abstract="Découvrez à quoi correspond l’expiration d’un ensemble de migration."

Tous les ensembles de migration expirent après une longue période d’inactivité d’environ 45 jours. Les indicateurs s’affichent sur la carte du projet et les lignes du tableau des tâches de migration pendant un certain temps, puis l’ensemble de migration expire et ses données deviennent indisponibles. Le délai d’expiration de l’ensemble de migration peut facilement être prolongé en :

* modifiant sa description
* obtenant sa clé d’extraction
* exécutant une extraction vers le jeu
* exécutant une ingestion à partir du jeu

Vous pouvez surveiller l’expiration d’un ensemble de migration sur la ligne Ensemble de migration. Un indicateur visuel utile indiquant que la date d’expiration d’un ensemble de migration approche a été ajouté à la carte du projet.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam29.png)

## Prochaines étapes {#whats-next}

Une fois que vous avez pris connaissance de l’outil de transfert de contenu et suivi la présentation de cet outil, vous pouvez l’utiliser pour déplacer du contenu existant d’une instance source AEM (on-premise ou AMS) vers l’instance cible AEM Cloud Service, vous devez consulter les [Conditions préalables pour l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md).

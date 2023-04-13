---
title: Présentation de l’outil de transfert de contenu
description: Présentation de l’outil de transfert de contenu
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: ac35bbe5ad78e07cc5292e089f3d71c6a8ed6ccc
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 79%

---

# Présentation {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Présentation"
>abstract="Développé par Adobe, l’outil de transfert de contenu est utilisé pour déplacer du contenu existant entre une instance AEM source (on-premise ou AMS) et une instance AEM Cloud Service cible. Cet outil transfère également automatiquement les entités principales (utilisateurs ou groupes)."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr" text="Conseils et bonnes pratiques"

Développé par Adobe, l’outil de transfert de contenu est utilisé pour déplacer du contenu existant entre une instance AEM source (on-premise ou AMS) et une instance AEM Cloud Service cible.

Cet outil transfère également automatiquement les entités principales (utilisateurs ou groupes).

Une nouvelle version de l’outil de transfert de contenu est disponible, qui intègre le processus de transfert de contenu à Cloud Acceleration Manager. Il est vivement recommandé de passer à cette nouvelle version afin d’exploiter tous les avantages qu’elle offre :

* Une méthode en libre-service pour extraire une seule fois un jeu de migration et l’ingérer dans plusieurs environnements en parallèle
* L’amélioration de l’expérience utilisateur grâce à une meilleure gestion des statuts de chargement, des barrières de sécurité et des erreurs
* La conservation des journaux d’ingestion et leur constante disponibilité à des fins de dépannage

Pour commencer à utiliser la nouvelle version, vous devrez désinstaller les anciennes versions de l’outil de transfert de contenu, car l’outil a subi un changement majeur d’architecture.

>[!NOTE]
>
> Dans les cas où une migration est déjà en cours, vous pouvez continuer à utiliser la version antérieure du CTT jusqu’à ce que la migration soit terminée. Pour consulter la documentation relative à la version précédente du CTT, reportez-vous à la [documentation héritée](/help/journey-migration/content-transfer-tool/ctt-legacy/overview-content-transfer-tool-legacy.md).

## Phases de l’outil de transfert de contenu {#phases-content-transfer-tool}

Le transfert de contenu comporte deux phases :

1. **Extraction** : l’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée *jeu de migration*. Un *jeu de migration* est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service.

   Pour plus d’informations, voir [Processus d’extraction au cours du transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md).

   >[!NOTE]
   >Le mappage utilisateur est désormais exécuté automatiquement dans le cadre de la phase d’extraction sur l’auteur (mais peut éventuellement être désactivé sur l’auteur ou activé sur la publication). Voir [Mappage des utilisateurs et migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) pour plus d’informations.

1. **Ingestion** : l’ingestion désigne l’ingestion de contenu à partir du *jeu de migration* dans l’instance Cloud Service cible.

   Pour plus d’informations, consultez [Processus d’ingestion au cours du transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

## Attributs d’un jeu de migration {#attributes-migration-set}

Un jeu de migration possède les attributs suivants :

* Avec la nouvelle version, vous pouvez créer un maximum de cinq jeux de migration au sein d’un projet créé dans Cloud Acceleration Manager.
* Chaque jeu de migration doit avoir un nom unique.

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Au cours de la phase d’extraction, pour ***compléter*** un jeu de migration existant, l’option de *remplacement* doit être désactivée. Pour en savoir plus, voir [Extraction de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process).

Lors de la phase d’ingestion, pour appliquer le contenu différentiel en plus du contenu actuel, l’option *Effacer* doit être désactivée. Pour en savoir plus, voir [Ingestion de complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process).

## Expiration du jeu de migration {#migration-set-expiry}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_migrationset_expiry"
>title="Expiration d&#39;un jeu de migration"
>abstract="Découvrez à quoi correspond l&#39;expiration d&#39;un jeu de migration."

Tous les jeux de migration finiront par expirer après une longue période d’inactivité d’environ 90 jours. Une fois les indicateurs affichés sur la carte du projet et les lignes du tableau des tâches de migration pendant une période donnée, le jeu de migration expire et ses données ne sont plus disponibles. Le délai d’expiration peut facilement être prolongé en agissant sur le jeu de migration en :

* modification de sa description
* obtention de sa clé d’extraction
* exécution d’une extraction sur celle-ci
* exécution d’une ingestion à partir de celle-ci

L’expiration d’un jeu de migration peut être surveillée sur la ligne Jeu de migration . Un indicateur visuel utile indiquant qu’un jeu de migration approche sa date d’expiration a également ajouté la carte du projet.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam29.png)


## Prochaines étapes {#whats-next}

Une fois que vous avez pris connaissance de l’outil de transfert de contenu et suivi la présentation de cet outil, vous pouvez l’utiliser pour déplacer du contenu existant d’une instance source AEM (on-premise ou AMS) vers l’instance cible AEM Cloud Service, vous devez consulter les [Conditions préalables pour l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md).

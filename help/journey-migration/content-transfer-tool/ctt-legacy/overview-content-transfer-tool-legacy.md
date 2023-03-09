---
title: Présentation de l’outil de transfert de contenu (hérité)
description: Présentation de l’outil de transfert de contenu
hide: true
hidefromtoc: true
exl-id: dd031580-e9d7-461e-8689-9bc3dbb2121b
source-git-commit: 3c8035e4db5729f58bae29136a32a0b9944d6a2f
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 72%

---

# Présentation de l’outil de transfert de contenu (hérité) {#overview-content-transfer-tool}

Développé par Adobe, l’outil de transfert de contenu est utilisé pour déplacer du contenu existant entre une instance AEM source (on-premise ou AMS) et une instance AEM Cloud Service cible.

Cet outil transfère également automatiquement les entités principales (utilisateurs ou groupes).

## Phases de l’outil de transfert de contenu {#phases-content-transfer-tool}

Le transfert de contenu comporte deux phases :

1. **Extraction** : l’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée *jeu de migration*. Un *jeu de migration* est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service.

   Pour plus d’informations, voir [Processus d’extraction au cours du transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=fr).

   >[!NOTE]
   >Exécutez l’outil de mappage des utilisateurs dans le cadre de la phase d’extraction. Pour plus d’informations, consultez [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=en).

1. **Ingestion** : l’ingestion désigne l’ingestion de contenu à partir du *jeu de migration* dans l’instance Cloud Service cible.

   Pour plus d’informations, consultez [Processus d’ingestion au cours du transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=fr).

## Attributs d’un jeu de migration {#attributes-migration-set}

Un jeu de migration possède les attributs suivants :

* Au maximum, il est possible de créer et de maintenir dix jeux de migration à la fois pendant l’activité de transfert de contenu.
* Chaque jeu de migration doit avoir un nom unique.
* Si un jeu de migration est inactif pendant plus de 30 jours, il est automatiquement supprimé.
* Chaque fois que vous créez un jeu de migration, il est associé à un environnement spécifique. Vous ne pouvez effectuer une ingestion que dans une instance d’auteur ou de publication d’un même environnement.


L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Dans la phase d&#39;extraction, à ***complément*** un jeu de migration existant, *overwrite* doit être désactivée. Pour en savoir plus, voir [Extraction de complément](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=en#top-up-extraction-process).

Lors de la phase d’ingestion, pour appliquer le contenu différentiel en plus du contenu actuel, l’option *Effacer* doit être désactivée. Pour en savoir plus, voir [Ingestion de complément](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en#top-up-ingestion-process).

## Prochaines étapes {#whats-next}

Une fois que vous avez pris connaissance de l’outil de transfert de contenu et de sa présentation, cet outil peut être utilisé pour déplacer le contenu existant d’une instance d’AEM source (on-premise ou AMS) vers l’instance AEM Cloud Service cible. Réviser [Conditions préalables pour l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en).

---
title: Présentation de l’outil de transfert de contenu
description: Présentation de l’outil de transfert de contenu
translation-type: tm+mt
source-git-commit: 60e236eadea8983fcf087b94ce908e55421214ae
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 94%

---


# Présentation {#overview-content-transfer-tool}

Développé par Adobe, l’outil de transfert de contenu est utilisé pour déplacer du contenu existant entre une instance AEM source (on-premise ou AMS) et une instance AEM Cloud Service cible.

Cet outil transfère également automatiquement les entités principales (utilisateurs ou groupes).

Le transfert de contenu comporte deux phases :

1. **Extraction** : l’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée *jeu de migration*. Un *jeu de migration* est un espace de stockage cloud fourni par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service.

   Pour plus d’informations, voir [Processus d’extraction au cours du transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process).

>[!NOTE]
>
> Il est recommandé d’exécuter l’outil de mappage des utilisateurs dans le cadre de la phase d’Extraction. Pour plus d&#39;informations, consultez [Utilisation de l&#39;outil de mappage utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration).

1. **Ingestion** : l’ingestion désigne l’ingestion de contenu à partir du *jeu de migration* dans l’instance Cloud Service cible.

   Pour plus d’informations, voir [Processus d’ingestion au cours du transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process).

Un *jeu de migration* possède les attributs suivants :

* Au maximum, il est possible de créer et maintenir quatre jeux de migration à la fois pendant l’activité de transfert de contenu.
* Chaque jeu de migration doit avoir un nom unique.
* Si un jeu de migration est inactif depuis plus de 30 jours, il est automatiquement supprimé.
* Chaque fois que vous créez un jeu de migration, il est associé à un environnement spécifique. Vous ne pouvez effectuer une ingestion que dans une instance d’auteur ou de publication d’un même environnement.

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
>
>Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Au cours de la phase d’extraction, pour ***compléter*** un jeu de migration existant, l’option de *remplacement* doit être désactivée. Pour en savoir plus, voir [Extraction de complément](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process).

Lors de la phase d’ingestion, pour appliquer le contenu différentiel en plus du contenu actuel, l’option *Effacer* doit être désactivée. Pour en savoir plus, voir [Ingestion de complément](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process).


## Conseils et bonnes pratiques {#best-practices}

Consultez la section ci-dessous pour accéder aux conseils et connaître les bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu :

* Il est conseillé de procéder à un [nettoyage de révision](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/deploying/deploying/revision-cleanup.html) et à des [contrôles de cohérence de l’entrepôt de données](https://helpx.adobe.com/fr/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) sur le référentiel **source** pour identifier les problèmes potentiels et réduire la taille du référentiel.

* Si le réseau de diffusion de contenu (CDN) de l’instance d’auteur AEM Cloud est configuré pour disposer d’une liste blanche d’adresses IP, il faut s’assurer que les adresses IP de l’environnement source sont aussi ajoutées à la liste autorisée pour que l’environnement source et l’environnement AEM Cloud puissent communiquer entre eux.

* Lors de la phase d’ingestion, il est recommandé d’exécuter l’ingestion en activant le mode d’*effacement*. Dans ce cas, le référentiel existant (auteur ou publication) de l’environnement AEM Cloud Service cible sera complètement supprimé, puis mis à jour à l’aide des données du jeu de migration. Ce mode est beaucoup plus rapide que le mode sans effacement, où le jeu de migration est appliqué par-dessus le contenu existant.

* Une fois l’activité de transfert de contenu terminée, une structure de projet appropriée est nécessaire dans l’environnement Cloud Service pour s’assurer que le contenu s’affiche correctement.

* Avant d’exécuter l’outil de transfert de contenu, vous devez vous assurer que l’espace disque disponible dans le sous-répertoire `crx-quickstart` de l’instance AEM source est suffisant. En effet, l’outil de transfert de contenu crée une copie locale du référentiel, ultérieurement chargée dans le jeu de migration.
La formule générale pour calculer l’espace disque disponible requis est la suivante :
   `data store size + node store size * 1.5`

   * *volume de stockage des données* : l’outil de transfert de contenu utilise 64 Go, même si l’entrepôt de données en question est plus volumineux.
   * *volume de stockage des nœuds* : taille du répertoire de stockage des segments ou taille de la base de données MongoDB.
Ainsi, pour un volume de stockage de segments de 20 Go, l’espace disque disponible requis est de 94 Go.

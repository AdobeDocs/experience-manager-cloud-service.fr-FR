---
title: Présentation de l’outil de transfert de contenu
description: Présentation de l’outil de transfert de contenu
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 100%

---


# Présentation {#overview-content-transfer-tool}

Développé par Adobe, l’outil de transfert de contenu est utilisé pour déplacer du contenu existant entre une instance AEM source (on-premise ou AMS) et une instance AEM Cloud Service cible.

Cet outil transfère également automatiquement les entités principales (utilisateurs ou groupes).

Le transfert de contenu comporte deux phases :

1. **Extraction** : L’extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée *jeu de migration*. Un *jeu de migration* est une zone d’enregistrement cloud fournie par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM Cloud Service.

   Pour plus d’informations, voir la section [Processus d’extraction au cours du transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process).

2. **Assimilation** : l’assimilation désigne l’assimilation de contenu à partir du *jeu de migration* dans l’instance Cloud Service cible.

   Pour plus d’informations, voir la section [Processus d’assimilation au cours du transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process).

Un *jeu de migration* possède les attributs suivants :

* Au maximum, il est possible de créer et maintenir quatre jeux de migration à la fois pendant l’activité de transfert de contenu.
* Chaque jeu de migration doit avoir un nom unique.
* Si un jeu de migration est inactif depuis plus de 30 jours, il est automatiquement supprimé.
* Chaque fois que vous créez un jeu de migration, il est associé à un environnement spécifique. Vous ne pouvez effectuer une assimilation que dans un auteur ou une instance de publication d’un même environnement.

L’outil de transfert de contenu comporte une fonctionnalité pour traiter un complément de contenu différentiel. Dans ce cas, seules les modifications effectuées depuis l’activité de transfert de contenu précédente sont transférées.

>[!NOTE]
> Suite au transfert initial d’un contenu, il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur le service cloud.

Au cours de la phase d’extraction, pour ***compléter*** un jeu de migration existant, l’option de *remplacement* doit être désactivée. Pour en savoir plus, voir la section [Extraction de complément](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process).

Lors de la phase d’assimilation, pour appliquer le contenu différentiel en plus du contenu actuel, l’option *Effacer* doit être désactivée. Pour en savoir plus, voir la section [Assimilation de complément](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process).


## Conseils et bonnes pratiques {#best-practices}

Consultez la section ci-dessous pour accéder aux conseils et connaître les bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu :

* Il est conseillé au préalable d’effectuer un compactage et de vérifier la cohérence des données stockées dans les référentiels pour détecter des problèmes potentiels, mais aussi réduire les informations inexploitables qu’ils contiennent.

* Si le réseau de diffusion de contenu (CDN) d’AEM Cloud Author est configuré pour disposer d’une liste blanche d’adresses IP, il faut s’assurer que les adresses IP de l’environnement source sont aussi ajoutées à la liste blanche pour que l’environnement source et l’environnement AEM Cloud puissent communiquer entre eux.

* Lors de la phase d’assimilation, il est recommandé d’exécuter l’assimilation en activant le mode d’*effacement*. Dans ce cas, le référentiel existant (auteur ou publication) de l’environnement de service AEM Cloud Service sera complètement supprimé, puis mis à jour à l’aide des données du jeu de migration. Ce mode est beaucoup plus rapide que le mode sans effacement, où le jeu de migration est appliqué par-dessus le contenu existant.

* Une fois l’activité de transfert de contenu terminée, une structure de projet appropriée est nécessaire dans l’environnement Cloud Service pour s’assurer que le contenu s’affiche correctement.
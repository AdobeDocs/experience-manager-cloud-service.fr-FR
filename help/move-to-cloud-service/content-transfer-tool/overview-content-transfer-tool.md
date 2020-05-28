---
title: Présentation de l’outil de transfert de contenu
description: Présentation de l’outil de transfert de contenu
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Présentation {#overview-content-transfer-tool}

L’outil de transfert de contenu est un outil développé par Adobe qui peut être utilisé pour déplacer du contenu existant d’une instance AEM source (sur site ou AMS) vers l’instance de service AEM Cloud cible.

Cet outil transfère également automatiquement les entités principales (utilisateurs ou groupes).

Le transfert de contenu comporte deux phases :

1. **Extraction**:  L’Extraction fait référence à l’extraction de contenu de l’instance AEM source dans une zone temporaire appelée jeu *de* migration. Un jeu *de* migration est une zone d’enregistrement de cloud fournie par Adobe pour stocker temporairement le contenu transféré entre l’instance AEM source et l’instance AEM du service Cloud.

   Pour plus d’informations, reportez-vous à la section Processus d’ [Extraction dans le transfert](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process) de contenu.

2. **Ingestion**: L’importation désigne l’assimilation de contenu à partir de la *migration définie* dans l’instance de service cible Cloud.

   Pour plus d&#39;informations, reportez-vous à la section Processus [d&#39;importation dans le transfert](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process) de contenu.

Un jeu *de* migration possède les attributs suivants :

* Au maximum quatre jeux de migration peuvent être créés et maintenus à la fois pendant l’activité de transfert de contenu.
* Chaque jeu de migration doit avoir un nom unique.
* Si un jeu de migration est inactif depuis plus de 30 jours, il est automatiquement supprimé.
* Chaque fois que vous créez un jeu de migration, il est associé à un environnement spécifique. Vous pouvez uniquement importer dans un auteur ou une instance de publication du même environnement.

L’outil de transfert de contenu comporte une fonctionnalité qui prend en charge le supplément de contenu différentiel où il est possible de transférer uniquement les modifications effectuées depuis l’activité précédente de transfert de contenu.

>[!NOTE]
> Après le transfert initial de contenu, il est recommandé d’effectuer de fréquents ajouts différentiels de contenu afin de raccourcir la période de gel de contenu pour le transfert différentiel final de contenu avant de passer en ligne sur le service Cloud.

Dans la phase d’extraction, pour ***compléter*** un jeu de migration existant, l’option de *remplacement* doit être désactivée. Pour plus d&#39;informations, consultez l&#39;Extraction [](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-extraction-process) Haut de page.

Lors de la phase d’assimilation, pour appliquer le contenu delta au-dessus du contenu actuel, l’option *essuyer* doit être désactivée. Pour plus d&#39;informations, reportez-vous à la section Ingestion [](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#top-up-ingestion-process) vers le haut.


## Lignes directrices et bonnes pratiques {#best-practices}

Suivez la section ci-dessous pour comprendre les directives et les meilleures pratiques relatives à l’utilisation de l’outil de transfert de contenu :

* Il est conseillé d&#39;exécuter la compaction, de vérifier la cohérence du stockage des données sur les référentiels avant de les faire main dans la main pour détecter les problèmes potentiels et de réduire les déchets présents dans le référentiel.

* Si la configuration du réseau CDN (AEM Cloud Author Content Diffusion Network) est configurée pour disposer d’une liste blanche des adresses IP, il faut s’assurer que les adresses IP de l’environnement source sont également ajoutées à la liste blanche afin que l’environnement source et l’environnement AEM Cloud puissent communiquer entre eux.

* Lors de la phase d’assimilation, il est recommandé d’exécuter l’assimilation en utilisant le mode de *balayage* activé où le référentiel existant (auteur ou publication) dans l’environnement de service AEM Cloud de cible sera complètement supprimé, puis mis à jour avec les données du jeu de migration. Ce mode est beaucoup plus rapide que le mode sans balayage, où l’ensemble de migration est appliqué au-dessus du contenu actuel.

* Une fois l’activité de transfert de contenu terminée, la structure de projet appropriée est requise dans l’environnement de service Cloud pour s’assurer que le contenu s’affiche correctement dans l’environnement de service Cloud.
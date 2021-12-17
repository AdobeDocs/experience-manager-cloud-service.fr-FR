---
title: Exécution de l’outil de transfert de contenu sur une instance de publication
description: Exécution de l’outil de transfert de contenu sur une instance de publication
source-git-commit: a1c57a9d8165c9e67ce270a3f0c2ad80c75b7196
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 29%

---


# Exécution de l’outil de transfert de contenu sur une instance de publication {#run-content-transfer-tool-publish-instance}

## Présentation {#introduction}

L’outil de transfert de contenu (CTT) n’effectue aucune analyse avant de transférer le contenu de l’instance source vers l’instance cible. Par exemple, le CTT ne fait pas de distinction entre le contenu publié et le contenu non publié lors de l’ingestion de contenu dans un environnement de publication. Quel que soit le contenu spécifié dans le jeu de migration, il sera ingéré dans l’instance cible choisie. L’utilisateur peut ingérer un jeu de migration dans une instance d’auteur ou de publication, ou les deux.

>[!NOTE]
>Il est recommandé que lors du déplacement du contenu vers une instance de production, l’outil de transfert de contenu soit installé sur l’instance d’auteur source pour déplacer le contenu vers l’instance d’auteur cible. De même, installez l’outil de transfert de contenu sur l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Voir [Approche recommandée](#recommended-approach) pour plus d’informations.

## Approche recommandée {#recommended-approach}

Suivez l’approche recommandée, comme décrit ci-dessous :

* Utilisez la même version de l’outil de transfert de contenu qui a été utilisée sur l’instance d’auteur.

* Un seul noeud de publication doit être migré. Il doit être supprimé de l’équilibreur de charge avant de commencer l’extraction.

* Lors de la création du jeu de migration, utilisez l’URL de l’environnement de création AEM as a Cloud Service.

* Lors de l’ingestion pour la publication, le niveau de publication ne sera pas réduit (contrairement à l’auteur).

   >[!IMPORTANT]
   >Par mesure de précaution, évitez les opérations d’écriture initiées par l’utilisateur, telles que :
   > * Distribution de contenu de AEM’auteur as a Cloud Service à la publication dans cet environnement
   > * Synchronisation des utilisateurs entre les instances de publication


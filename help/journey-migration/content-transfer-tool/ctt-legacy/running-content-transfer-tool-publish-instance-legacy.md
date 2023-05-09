---
title: Exécution de l’outil de transfert de contenu sur une instance de publication (hérité)
description: Exécution de l’outil de transfert de contenu sur une instance de publication
hide: true
hidefromtoc: true
exl-id: 0a699dc1-9977-4cf9-a1b0-7b503ea2fc69
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---

# Exécution de l’outil de transfert de contenu sur une instance de publication (hérité) {#run-content-transfer-tool-publish-instance}

## Présentation {#introduction}

L’outil de transfert de contenu (CTT) n’effectue aucune analyse avant de transférer le contenu de l’instance source vers l’instance cible. Par exemple, le CTT ne fait pas de distinction entre le contenu publié et le contenu dépublié lors de l’ingestion de contenu dans un environnement de publication. Quel que soit le contenu spécifié dans le jeu de migration, il sera ingéré dans l’instance cible choisie. L’utilisateur peut ingérer un jeu de migration dans une instance d’auteur ou de publication, ou les deux.

>[!NOTE]
>Il est recommandé, tout en déplaçant le contenu vers une instance de production, d’installer l’outil de transfert de contenu sur l’instance d’auteur source afin de déplacer le contenu vers l’instance d’auteur cible. De même, il est recommandé d’installer l’outil de transfert de contenu dans l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Consultez la section [Approche recommandée](#recommended-approach) pour plus d’informations.

## Approche recommandée {#recommended-approach}

Suivez l’approche recommandée, comme décrit ci-dessous :

* Utilisez la même version de l’outil de transfert de contenu qui a été utilisée sur l’instance d’auteur.

* Un seul nœud de publication doit être migré. Il doit être supprimé de l’équilibreur de charge avant de commencer l’extraction.

* Lors de la création du jeu de migration, utilisez l’URL de l’environnement de création AEM as a Cloud Service.

* Lors de l’ingestion pour la publication, le niveau de publication ne sera pas réduit (contrairement à l’auteur).

   >[!IMPORTANT]
   >Par mesure de précaution, évitez les opérations d’écriture initiées par l’utilisateur, telles que les suivantes :
   > * La distribution de contenu de la création dans AEM as a Cloud Service à la publication dans cet environnement
   > * La synchronisation des utilisateurs entre les instances de publication


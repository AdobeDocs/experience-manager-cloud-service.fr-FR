---
title: Exécution de l’outil de transfert de contenu sur une instance de publication
description: Exécution de l’outil de transfert de contenu sur une instance de publication
source-git-commit: 27e68cd282414da4cc23c3ba276b0fb3c330d49c
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 42%

---


# Exécution de l’outil de transfert de contenu sur une instance de publication {#run-content-transfer-tool-publish-instance}

## Présentation {#introduction}

L’outil de transfert de contenu (CTT) n’effectue aucune analyse avant de transférer le contenu de l’instance source vers l’instance cible. Par exemple, le CTT ne fait pas de distinction entre le contenu publié et le contenu non publié lors de l’ingestion de contenu dans un environnement de publication. Quel que soit le contenu spécifié dans le jeu de migration, il sera ingéré dans l’instance cible choisie. L’utilisateur peut ingérer un jeu de migration dans une instance d’auteur ou de publication, ou les deux. Il est recommandé, tout en déplaçant le contenu vers une instance de production, d’installer le CTT sur l’instance d’auteur source afin de déplacer le contenu vers l’instance d’auteur cible. De même, il est recommandé d’installer le CTT dans l’instance de publication source pour déplacer le contenu vers l’instance de publication cible.

>[!NOTE]
>Il est recommandé que lors du déplacement du contenu vers une instance de publication, l’outil de transfert de contenu soit installé sur l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Pour plus d’informations, voir la section [Approche recommandée](#recommended-approach) ci-dessous.

## Approche recommandée {#recommended-approach}

Suivez l’approche recommandée, comme décrit ci-dessous :

* Utilisez la même version du CTT que celle utilisée sur l’instance d’auteur.

* Un seul noeud de publication doit être migré. Il doit être supprimé de l’équilibreur de charge avant de commencer l’extraction.

* Lors de la création du jeu de migration, utilisez l’URL de l’environnement AEMaaCS de création.

* Lors de l’ingestion pour la publication, le niveau de publication ne sera PAS réduit (contrairement à l’auteur). Par mesure de précaution, évitez les opérations d’écriture initiées par l’utilisateur, telles que :

   * Distribution de contenu de AEM’auteur as a Cloud Service à la publication dans cet environnement
   * Synchronisation des utilisateurs entre les instances de publication

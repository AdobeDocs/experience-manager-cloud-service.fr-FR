---
title: Présentation des programmes de production
description: Découvrez les programmes de production et des suggestions pour configurer les vôtres.
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 83%

---


# Présentation des programmes de production {#production-programs}

Un programme de production est destiné à une équipe prête à commencer à écrire, créer et tester du code dans le but de le déployer pour héberger le trafic en direct.

Après la [création de votre programme de production](creating-production-programs.md), un [assistant de création de programme](using-the-wizard.md) guide l’utilisateur à travers les sélections en fonction de l’objectif de l’utilisateur lors de la création du programme.

## Options de création de programme {#program-creation-options}

Votre accord contractuel avec Adobe définit le nombre et les types de solutions disponibles pour votre organisation en particulier lors de la création de programmes de production. Vous avez le contrôle sur la manière de mapper les solutions disponibles aux programmes Cloud Manager.

Le tableau suivant décrit les scénarios courants des solutions disponibles et les programmes de production typiques créés à partir de ces solutions.

| Solutions disponibles | Options du programme | Éléments inclus | Quand l’utiliser | Exemples |
|---------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 Solution Sites | Créer 1 programme Sites uniquement | 1 Production + 1 Évaluation, 1 Développement, 1 Développement Rapide | S/O | S/O |
| 1 Solution Assets | Créer 1 programme Assets uniquement | 1 Production + 1 Évaluation, 1 Développement, 1 Développement Rapide | S/O | S/O |
| 1 Sites +1 Assets | Créer un programme : <br>1 programme Sites et Assets | 1 Production + 1 Évaluation, 2 Développement, 2 Développement Rapide | Lorsque la majorité des ressources numériques sont utilisées pour prendre en charge la mise en œuvre des sites.<br>Dans ce cas, la plupart des ressources numériques se trouvent dans un état terminé, prêt à être utilisé pour les expériences entre canaux via Sites.<br>Généralement, une seule équipe est chargée de gérer le contenu pour Sites et Assets. | Les images principalement utilisées pour un site web.<br>Un portail interne créé dans AEM Sites distribue les PDF. |
| 1 Sites +1 Assets | Créer des programmes distincts :<br>1 programme Sites uniquement et 1 programme Assets uniquement | 1 production + 1 évaluation, 1 développement, 1 développement rapide<br>1 production + 1 évaluation, 1 développement, 1 développement rapide | Lorsque de nombreuses ressources numériques ne prennent pas directement en charge la mise en œuvre des sites.<br> Dans ce cas, les ressources se trouvent dans différents états, y compris les types de fichiers bruts et sont en cours de mise au point.<br>Une équipe de création dédiée au contenu gère les ressources numériques tout au long de son propre cycle de vie et dispose de workflows et de cycles de publication distincts de ceux de l’équipe de gestion de contenu Sites. | Les images brutes d’une prise de vue sont stockées dans le programme Assets et seules quelques-unes sont utilisées dans l’implémentation de Sites.<br>Un grand nombre de types de fichiers Creative Cloud, tels que Photoshop et Illustrator, sont gérés dans AEM Assets et passent par leur propre workflow d’approbation avant qu’une ressource finalisée ne soit générée.<br>Envisagez d’utiliser des [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md#overview-of-connected-assets) dans ce cas. |
| 1 Sites + 1 Sites | Créer des programmes distincts :<br>1 programme Sites uniquement et 1 programme Sites uniquement | 1 production + 1 évaluation, 1 développement, 1 développement rapide<br>1 production + 1 évaluation, 1 développement, 1 développement rapide | Pour les implémentations de sites à plusieurs clients.<br>Dans ce cas, plusieurs sites avec leur propre planning de publication et des équipes de développement et de contenu dédiées doivent être gérés. | Deux marques de vente au détail avec des sites web dédiés et des équipes de développement distinctes |


>[!NOTE]
>
>Programmes de production [modifiables, mais non supprimés](editing-programs.md).

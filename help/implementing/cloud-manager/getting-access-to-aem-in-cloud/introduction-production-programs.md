---
title: 'Présentation des programmes de production '
description: Découvrez les programmes de production et les suggestions pour configurer le vôtre.
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
source-git-commit: a6152a1529b5c70bcf056857204e7ff97fc614e4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 21%

---


# Présentation des programmes de production {#production-programs}

Un programme de production est destiné à une équipe prête à commencer à écrire, créer et tester du code dans le but de le déployer pour héberger le trafic en direct.

Après vous [créer votre programme de production,](creating-production-programs.md) a [assistant de création de programme](using-the-wizard.md) guide l’utilisateur à travers les sélections en fonction de l’objectif de l’utilisateur lors de la création du programme.

## Options de création de programme {#program-creation-options}

Votre accord contractuel avec Adobe définit le nombre et les types de solutions disponibles pour votre organisation spécifique lors de la création de programmes de production. Vous avez le contrôle sur la manière de mapper les solutions disponibles aux programmes Cloud Manager.

Le tableau suivant décrit les scénarios courants des solutions disponibles et les programmes de production typiques créés à partir de ces solutions.

| Solutions disponibles | Options de programme | Éléments inclus | Quand utiliser | Exemples |
|--- |--- |--- |--- |---|
| 1 solution Sites | Créer 1 programme Sites uniquement | 1 Production + 1 Évaluation, 1 Développement | N/A | N/A |
| 1 solution Assets | Créer 1 programme Ressources uniquement | 1 Production + 1 Évaluation, 1 Développement | N/A | N/A |
| 1 Sites +1 Assets | Créez un programme : <br>1 programme Sites et ressources | 1 Production + 1 Évaluation, 2 Développement | Lorsqu’une majorité des ressources numériques sont utilisées pour prendre en charge la mise en oeuvre des sites.<br>Dans ce cas, la plupart des ressources numériques se trouvent dans un état terminé, prêt à être utilisé pour les expériences cross-canal via Sites.<br>En règle générale, une seule équipe est chargée de gérer le contenu pour Sites et Assets. | Images principalement utilisées pour un site web.<br>Les fichiers PDF qui seront distribués via un portail interne créé dans AEM Sites. |
| 1 Sites +1 ressources | Créer des programmes distincts :<br>1 programme Sites uniquement et 1 programme Ressources uniquement | 1 Production + 1 Évaluation, 1 Développement<br> 1 Production + 1 Évaluation, 1 Développement | Lorsque de nombreuses ressources numériques ne prennent pas directement en charge l’implémentation des sites.<br> Dans ce cas, les ressources se trouvent dans différents états, y compris les types de fichiers bruts et les travaux en cours.<br>Une équipe créative dédiée gère les ressources numériques tout au long de son propre cycle de vie et dispose de workflows et de cycles de publication distincts de l’équipe de gestion de contenu Sites. | Les images brutes d’une séance photo sont stockées dans le programme Ressources et seules quelques-unes d’entre elles seront utilisées dans la mise en oeuvre de Sites.<br>Un grand nombre de types de fichiers Creative Cloud, tels que Photoshop et Illustrator, sont gérés dans AEM Assets et passent par leur propre workflow d’approbation avant qu’une ressource finalisée ne soit générée.<br>Envisager d’utiliser [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md#overview-of-connected-assets) dans ce cas. |
| 1 Sites + 1 Sites | Créer des programmes distincts :<br>1 programme Sites uniquement et 1 programme Sites uniquement | 1 Production + 1 Évaluation, 1 Développement<br> 1 Production + 1 Évaluation, 1 Développement | Pour les implémentations de sites multi-clients.<br>Dans ce cas, plusieurs sites avec leur propre calendrier de publication et des équipes de développement et de contenu dédiées doivent être gérés. | Deux marques de vente au détail avec des sites web dédiés et des équipes de développement distinctes |

>[!NOTE]
>
>Programmes de production [ne peut pas être modifié et ne peut pas être supprimé.](editing-programs.md)

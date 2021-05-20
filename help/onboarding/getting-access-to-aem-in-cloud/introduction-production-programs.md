---
title: 'Présentation des programmes de production '
description: Présentation des programmes de production
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Présentation des programmes de production {#production-programs}

Un programme *Production* est destiné à un utilisateur familiarisé avec AEM et Cloud Manager et prêt à commencer à écrire, créer et tester du code dans le but de le déployer dans Production.

>[!NOTE]
>Vous ne pourrez pas supprimer un programme de production.

Un assistant de création de programme va guider l’utilisateur à effectuer des sélections, selon l’objectif de l’utilisateur lors de la création du programme. En fonction des droits de solution inutilisés disponibles pour le client ou l’organisation spécifique, l’utilisateur contrôle la manière de mapper les droits de solution disponibles (inutilisés) aux programmes Cloud Manager.

## Considérations sur la création de programme {#program-creation-considerations}

Le tableau ci-dessous décrit les scénarios courants à prendre en compte lors de la création de programmes dans Cloud Manager :

| Droits de solution inutilisés disponibles dans l’organisation | Créer des options de programme | Éléments inclus | Quand utiliser et d’autres considérations |
|--- |--- |--- |--- |
| 1 solution Sites | Créer 1 programme Sites uniquement | 1 production + 1 étape, 1 développement | NA |
| 1 solution Assets | Créer 1 programme Ressources uniquement | 1 production + 1 étape, 1 développement | NA |
| 1 Sites +1 ressources | Créer un programme : 1 programme Sites et ressources | 1 production + 1 étape, 2 développement | La majorité des ressources numériques sont utilisées pour prendre en charge la mise en oeuvre des sites. La plupart des ressources numériques se trouvent dans un état final, prêt à être utilisé pour les expériences cross-canal via Sites. En règle générale, une seule équipe est responsable de la gestion du contenu pour Sites et Assets. **Exemples courants** : Images principalement utilisées pour un site web. PDF qui seront distribués via un portail interne intégré à AEM Sites. |
| 1 Sites +1 ressources | Créer des programmes distincts : 1 programme Sites uniquement et 1 programme Ressources uniquement | 1 Production + 1 Étape, 1 Développement<br> 1 Production + 1 Étape, 1 Développement | De nombreuses ressources numériques ne prennent pas directement en charge l’implémentation des sites. Les ressources gérées se trouvent dans différents états, y compris les types de fichiers bruts et les travaux en cours. Une équipe créative dédiée gère les ressources numériques tout au long de son propre cycle de vie et dispose de workflows et de cycles de publication distincts de l’équipe de gestion de contenu Sites. *Exemples courants* : Les images brutes d’une séance photo sont stockées dans le programme Ressources et seules quelques-unes d’entre elles seront utilisées dans la mise en oeuvre de Sites. Un grand nombre de types de fichiers de Creative Cloud, tels que Photoshop et Illustrator, sont gérés dans AEM Assets et passent par leur propre processus d’approbation avant qu’une ressource terminée ne soit générée. Fonctionnalités à exploiter : [Ressources connectées](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html?lang=en#overview-of-connected-assets) |
| 1 Sites + 1 Sites | Créer des programmes distincts : 1 programme Sites uniquement et 1 programme Sites uniquement | 1 production + 1 étape, 1 développement<br>1 production + 1 étape, 1 développement | Implémentations de sites multi-clients. Plusieurs sites avec leur propre calendrier de publication et des équipes de développement et de contenu dédiées. *Exemples courants* : Deux marques de vente au détail avec des sites web dédiés et des équipes de développement distinctes |

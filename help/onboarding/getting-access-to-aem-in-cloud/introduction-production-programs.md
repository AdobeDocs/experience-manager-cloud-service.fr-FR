---
title: 'Présentation des programmes de production '
description: Présentation des programmes de production
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 100%

---

# Présentation des programmes de production {#production-programs}

Un programme de *production* est destiné à un utilisateur qui connaît AEM et Cloud Manager et qui est prêt à se lancer dans l’écriture, la compilation et le test de code puis à le déployer en production.

>[!NOTE]
>Vous ne pourrez pas supprimer un programme de production.

Un assistant de création de programmes permet à l’utilisateur d’effectuer des sélections en fonction de l’objectif de l’utilisateur lors de la création du programme. Selon les droits inutilisés concernant une solution, et disponibles pour un client ou une organisation spécifiques, l’utilisateur bénéficie d’un contrôle sur la mise en correspondance des droits de solution disponibles (inutilisés) avec les programmes de Cloud Manager.

## Considérations relatives à la création de programmes {#program-creation-considerations}

Le tableau ci-dessous décrit les scénarios courants à prendre en compte lors de la création de programmes dans Cloud Manager :

| Droits sur une solution inutilisés et disponibles dans l’organisation | Créer des options de programme | Éléments inclus | Conditions d’utilisation et autres considérations |
|--- |--- |--- |--- |
| 1 solution Sites | Créer 1 programme Sites uniquement | 1 Production + 1 Évaluation, 1 Développement | s.o. |
| 1 solution Assets | Créer un programme Assets uniquement | 1 Production + 1 Évaluation, 1 Développement | s.o. |
| 1 Sites +1 Assets | Créer un programme : 1 programme Sites et Assets | 1 Production + 1 Évaluation, 2 Développement | La majorité des ressources numériques sont utilisées pour prendre en charge la mise en œuvre des sites. La plupart des ressources numériques se trouvent dans un état achevé, prêtes à être utilisées pour des expériences cross-canal utilisant Sites. En règle générale, une seule équipe est chargée de gérer les contenus Sites et Assets. **Exemples courants** : images principalement utilisées pour un site web. Les fichiers PDF qui seront distribués via un portail interne créé dans AEM Sites. |
| 1 Sites +1 ressources | Créer des programmes distincts : 1 programme Sites uniquement et 1 programme Assets uniquement | 1 Production + 1 Évaluation, 1 Développement <br> 1 Production + 1 Évaluation, 1 Développement | De nombreuses ressources numériques ne prennent pas directement en charge la mise en œuvre des sites. Les ressources gérées se trouvent dans différents états, y compris les types de fichiers bruts et sont en cours de mise au point. Une équipe de création dédiée gère les ressources numériques tout au long de son propre cycle de vie et dispose de workflows et de cycles de publication distincts de ceux de l’équipe de gestion de contenu Sites. *Exemples courants* : les images brutes d’une prise de vue sont stockées dans le programme Assets et seules quelques-unes sélectionnées seront utilisées dans l’implémentation de Sites. Un grand nombre de types de fichiers Creative Cloud, tels que Photoshop et Illustrator, sont gérés dans AEM Assets et passent par leur propre workflow d’approbation avant qu’une ressource finalisée ne soit générée. Fonctionnalités à exploiter : [Ressources connectées](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html?lang=fr#overview-of-connected-assets) |
| 1 Sites + 1 Sites | Créer des programmes distincts : 1 programme Sites uniquement et 1 programme Sites uniquement | 1 Production + 1 Évaluation, 1 Développement <br> 1 Production + 1 Évaluation, 1 Développement | Implémentations de sites multi-locataires. Plusieurs sites avec leur propre calendrier de publication et des équipes dédiées de développement et de contenu. *Exemples courants* : deux marques de vente au détail avec des sites web dédiés et des équipes de développement distinctes |

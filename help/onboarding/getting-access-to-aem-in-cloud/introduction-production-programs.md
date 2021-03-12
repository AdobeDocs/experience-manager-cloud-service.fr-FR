---
title: 'Présentation des Programmes de production '
description: 'Présentation des Programmes de production '
translation-type: tm+mt
source-git-commit: 5773683a75254855687266929a3e1876c8f06e61
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---


# Introduction aux Programmes de production {#production-programs}

Un programme *Production* est destiné à un utilisateur qui connaît AEM et Cloud Manager et qui est prêt à début la rédaction, la création et le test de code dans le but de le déployer vers Production.

>[!NOTE]
>Vous ne pourrez pas supprimer un programme de production.

Un assistant de création de programme permet à l’utilisateur d’effectuer des sélections en fonction de l’objectif de l’utilisateur lors de la création du programme. En fonction des droits de solution inutilisés disponibles pour un client ou une organisation spécifique, l’utilisateur a le contrôle sur la mise en correspondance des droits de solution disponibles (inutilisés) avec les programmes de Cloud Manager.

## Considérations sur la création de programme {#program-creation-considerations}

Le tableau ci-dessous décrit les scénarios courants à prendre en compte lors de la création de programmes dans Cloud Manager :

| Droits de solution inutilisés disponibles dans l’organisation | Créer des options de Programme | Éléments inclus | Conditions d’utilisation et autres considérations |
|--- |--- |--- |--- |
| 1 Solution de sites | Créer 1 programme Sites uniquement | 1 Production + 1 Phase, 1 Développement | NA |
| 1 Solution de ressources | Créer un programme de ressources uniquement | 1 Production + 1 Phase, 1 Développement | NA |
| 1 Sites +1 Ressources | Créer un Programme : 1 programme Sites et ressources | 1 Production + 1 Phase, 2 Développement | La majorité des ressources numériques sont utilisées pour prendre en charge la mise en oeuvre des sites. La plupart des ressources numériques se trouvent dans un état achevé, prêt à être utilisé pour des expériences canaux par le biais de sites. En règle générale, une seule équipe est chargée de gérer le contenu des sites et des ressources. **Exemples** courants : Images principalement utilisées pour un site Web. Les fichiers PDF qui seront distribués via un portail interne créé en AEM Sites. |
| 1 Sites +1 Ressources | Créer des programmes distincts : 1 programme Sites uniquement et 1 programme Ressources uniquement | 1 Production + 1 Phase, 1 Développement <br> 1 Production + 1 Phase, 1 Développement | De nombreuses ressources numériques ne prennent pas directement en charge la mise en oeuvre des sites. Les ressources gérées se trouvent dans divers états, y compris les types de fichiers bruts et fonctionnent en cours. Une équipe de création dédiée gère les ressources numériques tout au long de son propre cycle de vie et dispose de workflows et de cycles de publication distincts de ceux de l&#39;équipe de gestion de contenu Sites. *Exemples* courants : Les images brutes d’une prise de vue sont stockées dans le programme Ressources et seules quelques-unes sélectionnées seront utilisées dans l’implémentation Sites. Un grand nombre de types de fichiers Creative Cloud, tels que Photoshop et Illustrator, sont gérés à AEM Assets et passent par leur propre processus d’approbation avant qu’une ressource terminée ne soit générée. Fonctionnalités à exploiter : [Ressources connectées](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html?lang=en#overview-of-connected-assets) |
| 1 Sites + 1 Sites | Créer des programmes distincts : 1 Sites uniquement programme et 1 Sites uniquement programme | 1 Production + 1 Phase, 1 Développement<br>1 Production + 1 Phase, 1 Développement | Implémentations de sites multi-locataires. Plusieurs sites avec leur propre calendrier de publication et des équipes dédiées de développement et de contenu. *Exemples* courants : Deux marques de vente au détail avec des sites Web dédiés et des équipes de développement distinctes |



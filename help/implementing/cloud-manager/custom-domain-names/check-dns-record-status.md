---
title: Vérification du statut de l’enregistrement DNS
description: Découvrez comment déterminer si vos paramètres DNS sont correctement résolus à l’aide de Cloud Manager.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8a10634e413ea5c66845dfffa7396a4554a5b3ca
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 25%

---


# Vérifiez le statut de l’enregistrement DNS {#check-dns-record-status}

Découvrez comment déterminer si vos paramètres DNS sont correctement résolus à l’aide de Cloud Manager.

## Statut des enregistrements DNS {#status}

Un nom de domaine personnalisé ne peut pas traiter le trafic en direct tant que le DNS n’a pas été résolu correctement. Dans Cloud Manager, vous pouvez déterminer si votre nom de domaine est correctement résolu sur votre site web AEM as a Cloud Service.

## Conditions requises {#requirements}

Renseignez ces exigences avant de vérifier l’état d’enregistrement DNS à l’aide de Cloud Manager.

Vous devez avoir déjà configuré les paramètres DNS pour votre nom de domaine personnalisé comme décrit dans [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

## Vérifiez le statut de l’enregistrement DNS {#how-to}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **Paramètres de domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **Statut** pour le nom de domaine.

Cloud Manager effectue une recherche DNS pour votre nom de domaine et l’affiche [état actuel](#statuses).

Cloud Manager déclenche automatiquement une recherche DNS lorsque votre nom de domaine personnalisé est vérifié et déployé pour la première fois. Pour les tentatives suivantes, vous devez sélectionner vous-même l’icône **Résoudre à nouveau** en face du statut.

## Statuts DNS dans Cloud Manager {#statuses}

Un domaine personnalisé peut avoir l’un des états suivants dans Cloud Manager.

| État | Description |
| --- | --- |
| Statut DNS non détecté | L’état DNS n’est pas détecté tant que votre nom de domaine personnalisé n’a pas été vérifié et déployé avec succès. Cet état est également observé lorsque votre nom de domaine personnalisé est en cours de suppression. |
| Résolution DNS incorrecte | Ce statut indique que la configuration des enregistrements DNS n&#39;a pas été résolue ou qu&#39;elle est erronée. Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour en savoir plus.<br>Une fois prêt, vous devez sélectionner l’icône **Résoudre** en regard de l’état. |
| Résolution DNS en cours | La résolution est en cours. Ce statut apparaît généralement après avoir sélectionné l’icône **Résoudre à nouveau** en face du statut. |
| Résolution DNS correcte | Vos paramètres DNS sont correctement configurés. Votre site accueille des visiteurs. |

## Étapes suivantes {#next-steps}

Vous avez correctement configuré votre domaine personnalisé pour l’utiliser avec Cloud Manager. Consultez le document [Gérer les noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour plus d’informations sur la gestion de vos noms de domaine personnalisés à l’aide de Cloud Manager.

---
title: Vérification du statut de l’enregistrement DNS
description: Découvrez comment déterminer si vos paramètres DNS sont correctement résolus à l’aide de Cloud Manager.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 60%

---


# Vérification du statut de l’enregistrement DNS {#check-dns-record-status}

Découvrez comment déterminer si vos paramètres DNS sont correctement résolus à l’aide de Cloud Manager.

## État des enregistrements DNS {#status}

Un nom de domaine personnalisé ne peut pas servir de trafic en direct tant que le DNS n’a pas été résolu correctement. Dans Cloud Manager, vous pouvez déterminer si votre nom de domaine se résout correctement sur votre site web AEM as a Cloud Service.

## Conditions requises {#requirements}

Vous devez répondre à ces exigences avant de vérifier l’état d’enregistrement DNS à l’aide de Cloud Manager.

* Vous devez avoir déjà configuré les paramètres DNS pour votre nom de domaine personnalisé, comme décrit dans le document [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).

## Comment vérifier l’état de l’enregistrement DNS {#how-to}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **Paramètres de domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **Statut** pour le nom de domaine.

Cloud Manager effectue une recherche DNS pour votre nom de domaine et l’affiche [état actuel](#statuses).

Cloud Manager déclenche automatiquement une recherche DNS lorsque votre nom de domaine personnalisé est vérifié et déployé correctement pour la première fois. Pour les tentatives suivantes, vous devez sélectionner vous-même l’icône **Résoudre à nouveau** en face du statut.

## Statuts DNS dans Cloud Manager {#statuses}

Un domaine personnalisé peut avoir l’un des états suivants dans Cloud Manager.

* **Statut de DNS non détecté** - Le statut du DNS n’est pas détecté tant que votre nom de domaine personnalisé n’a pas été vérifié et déployé avec succès.

   * Cet état est également observé lorsque votre nom de domaine personnalisé est en cours de suppression.

* **Résolution DNS incorrecte** - Cela indique que la configuration des enregistrements DNS n’a pas encore été résolue ou est erronée.

   * Voir [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour en savoir plus.
   * Une fois prêt, vous devez sélectionner l’icône **Résoudre à nouveau** en face du statut.

* **Résolution DNS en cours** - La résolution est en cours.

   * Ce statut apparaît généralement après avoir sélectionné l’icône **Résoudre à nouveau** en face du statut.

* **Résolution DNS correcte** - Vos paramètres DNS ont été configurés correctement.

   * Votre site accueille des visiteurs.

## Étapes suivantes {#next-steps}

Félicitations. Vous avez correctement configuré votre domaine personnalisé pour l’utiliser avec Cloud Manager. Consultez le document [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour plus d’informations sur la gestion de vos noms de domaine personnalisés à l’aide de Cloud Manager.

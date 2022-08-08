---
title: Vérification du statut de l’enregistrement DNS
description: Découvrez comment déterminer si vos paramètres DNS sont correctement résolus à l’aide de Cloud Manager.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 2278abcf0c34fd34a7730242ee27814d37b7d4d0
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%

---

# Vérification du statut de l’enregistrement DNS {#check-dns-record-status}

Dans Cloud Manager, vous pouvez déterminer si votre nom de domaine se résout correctement sur votre site web AEM as a Cloud Service.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **Paramètres du domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **Statut** pour le nom de domaine.

Cloud Manager effectue une recherche DNS pour votre nom de domaine et affiche l’un des messages de statut suivants.

* **Statut de DNS non détecté** - Le statut du DNS n’est pas détecté tant que votre nom de domaine personnalisé n’a pas été vérifié et déployé avec succès.

   * Ce statut est également observé lorsque votre nom de domaine personnalisé est en cours de suppression.

* **Résolution DNS incorrecte** - Cela indique que la configuration des enregistrements DNS n’a pas encore été résolue ou est erronée.

   * Consultez le document [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour en savoir plus.
   * Une fois prêt, vous devez sélectionner l’icône **Résoudre à nouveau** en face du statut.

* **Résolution DNS en cours** - La résolution est en cours.

   * Ce statut apparaît généralement après avoir sélectionné l’icône **Résoudre à nouveau** en face du statut.

* **Résolution DNS correcte** - Vos paramètres DNS ont été configurés correctement.

   * Votre site accueille des visiteurs.

Cloud Manager déclenche automatiquement une recherche DNS lorsque votre nom de domaine personnalisé est vérifié et déployé correctement pour la première fois. Pour les tentatives suivantes, vous devez sélectionner vous-même l’icône **Résoudre à nouveau** en face du statut.

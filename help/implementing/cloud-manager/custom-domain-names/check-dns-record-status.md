---
title: Vérification du statut de l’enregistrement DNS
description: Découvrez comment déterminer si vos paramètres DNS sont correctement résolus à l’aide de Cloud Manager.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 2278abcf0c34fd34a7730242ee27814d37b7d4d0
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 17%

---

# Vérification du statut de l’enregistrement DNS {#check-dns-record-status}

Dans Cloud Manager, vous pouvez déterminer si votre nom de domaine se résout correctement sur votre site web as a Cloud Service AEM.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Environnements** de l’écran **Présentation** page.

1. Cliquez sur **Paramètres de domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **État** pour le nom de domaine.

Cloud Manager effectue une recherche DNS pour votre nom de domaine et affiche l’un des messages d’état suivants.

* **Statut DNS non détecté** - L’état DNS ne sera pas détecté tant que votre nom de domaine personnalisé n’aura pas été vérifié et déployé avec succès.

   * Ce statut est également observé lorsque votre nom de domaine personnalisé est en cours de suppression.

* **Résolution DNS incorrecte** - Cela indique que la configuration des enregistrements DNS n’a pas été résolue ou qu’elle est erronée.

   * Reportez-vous au document [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour en savoir plus.
   * Une fois prêt, vous devez sélectionner la variable **Résoudre** en regard de l’état.

* **Résolution DNS en cours** - La résolution est en cours.

   * Cet état s’affiche généralement une fois que vous avez sélectionné la variable **Résoudre** en regard de l’état.

* **Le DNS se résout correctement** - Vos paramètres DNS sont correctement configurés.

   * Votre site accueille des visiteurs.

Cloud Manager déclenche automatiquement une recherche DNS lorsque votre nom de domaine personnalisé est vérifié et déployé pour la première fois. Pour les tentatives suivantes, vous devez sélectionner activement la variable **Résoudre** en regard de l’état.

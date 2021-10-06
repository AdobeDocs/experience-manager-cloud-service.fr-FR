---
title: Vérification du statut de l’enregistrement DNS
description: Vérification du statut de l’enregistrement DNS
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 17dffaae3beac678ce89b5fde7abea3b2dff86a8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 100%

---

# Vérification du statut de l’enregistrement DNS {#check-dns-record-status}

Vous pouvez déterminer si votre nom de domaine mène correctement vers votre site Web AEM as a Cloud Service en cliquant sur l’icône Statut de l’enregistrement DNS dans le tableau sur les Environnements depuis la page Paramètres de domaine.

Cloud Manager déclenche automatiquement une recherche DNS lorsque votre nom de domaine personnalisé est vérifié et déployé correctement pour la première fois. Pour les tentatives suivantes, vous devez sélectionner activement l’icône **Résoudre à nouveau** en regard du statut.

Cloud Manager effectue une recherche DNS pour votre nom de domaine et affiche l’un des messages d’état suivants :

* **Statut du DNS non détecté**
Le statut du DNS n’est pas détecté tant que votre nom de domaine personnalisé n’a pas été vérifié et déployé avec succès. Ce statut est également observé lorsque votre nom de domaine personnalisé est en cours de suppression.

* **Résolution DNS incorrecte**
Cela indique que la configuration des enregistrements DNS n’a pas encore été résolue/pointée ou est erronée.

   >[!NOTE]
   >Vous devez configurer un `CNAME` ou un `A-record` en suivant les instructions correspondantes. Voir Configuration des paramètres DNS pour en savoir plus. Une fois prêt, vous devez sélectionner l’icône **Résoudre à nouveau** en regard du statut.

* **Résolution DNS en cours**
La résolution est en cours. Cet état apparaît généralement après avoir sélectionné l’icône « Résoudre à nouveau » en regard du statut.

* **Résolution DNS correcte**
Vos paramètres DNS sont configurés correctement. Votre site accueille des visiteurs.

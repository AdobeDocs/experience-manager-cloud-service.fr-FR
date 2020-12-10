---
title: Vérification de l'état de l'enregistrement DNS
description: Vérification de l'état de l'enregistrement DNS
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Vérification du statut de l&#39;enregistrement DNS {#check-dns-record-status}

Vous pouvez déterminer si votre nom de domaine est correctement résolu sur votre AEM en tant que site Web Cloud Service en cliquant sur l’icône État de l’enregistrement DNS dans le tableau de la page Environnements de la page Paramètres de domaine.

Cloud Manager déclenche automatiquement une recherche DNS lorsque votre nom de domaine personnalisé est vérifié et déployé pour la première fois. Pour les tentatives suivantes, vous devez sélectionner activement l&#39;icône **résoudre de nouveau** en regard de l&#39;état.

Cloud Manager effectue une recherche DNS pour votre nom de domaine et affiche l’un des messages d’état suivants :

* **L&#39;état DNS non**
détectéL&#39;état DNS ne sera pas détecté tant que votre nom de domaine personnalisé n&#39;aura pas été vérifié et déployé avec succès. Cet état est également observé lorsque votre nom de domaine personnalisé est en cours de suppression.

* **Résolution DNS**
incorrectementCeci indique que la configuration des enregistrements DNS n&#39;a pas encore été résolue/pointée ou est erronée. Un représentant d&#39;Adobe sera automatiquement averti.

   >[!NOTE]
   >Vous devez configurer `CNAME` ou `A-record` en suivant les instructions correspondantes. Consultez Configuration des paramètres DNS pour en savoir plus. Une fois prêt, vous devez sélectionner l&#39;icône **résoudre à nouveau** en regard de l&#39;état.

* **Résolution DNS en cours de**
progressionRésolution est en cours. Cet état s’affiche généralement après avoir sélectionné l’icône &quot;Résoudre&quot; en regard de l’état.

* **Résolution DNS**
CorrectementVos paramètres DNS sont correctement configurés. Votre site sert des visiteurs.

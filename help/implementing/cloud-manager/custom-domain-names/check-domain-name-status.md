---
title: Vérification de l’état du nom de domaine
description: Découvrez comment déterminer si Cloud Manager a vérifié votre nom de domaine personnalisé avec succès.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 17%

---


# Vérification de l’état du nom de domaine {#check-status}

Vous pouvez déterminer l’état de votre nom de domaine personnalisé dans Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Environnements** de l’écran **Présentation** page.

1. Cliquez sur **Paramètres de domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **État** pour le nom de domaine.

Cloud Manager vérifie la propriété du domaine via la valeur TXT et affiche l’un des messages d’état suivants.

* **Échec de la vérification du domaine** - La valeur TXT est manquante ou est détectée avec des erreurs.

   * Suivez les instructions fournies pour résoudre le problème.
   * Une fois prêt, vous devez sélectionner la variable **Vérifier à nouveau** en regard de l’état.

* **Vérification de domaine en cours** - La vérification est en cours.

   * Cet état s’affiche généralement une fois que vous avez sélectionné la variable **Vérifier à nouveau** en regard de l’état.

* **Vérifié, Échec du déploiement** - La vérification TXT a réussi, mais le déploiement CDN a échoué.

   * Dans ce cas, veuillez contacter votre représentant Adobe.

* **Domaine vérifié et déployé** - Cet état indique que votre nom de domaine personnalisé est prêt à être utilisé.

   * À ce stade, votre nom de domaine personnalisé est prêt à être testé et pointé vers le nom de domaine Cloud Manager.
   * Reportez-vous au document [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour en savoir plus.

* **Suppression** - La suppression d’un nom de domaine personnalisé est en cours.

* **Échec de la suppression** - La suppression du nom de domaine personnalisé a échoué et doit être refaite.

   * Reportez-vous au document [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

Cloud Manager déclenche automatiquement une vérification TXT lorsque vous sélectionnez **Enregistrer** à l’étape de vérification de la **Ajouter un domaine personnalisé** assistant. Pour les vérifications suivantes, vous devez sélectionner activement l’icône Vérifier à nouveau en regard de l’état.

## Configurations CDN pré-existantes pour les noms de domaine personnalisés {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau de diffusion de contenu préexistante pour vos noms de domaine personnalisés, un message d’information s’affichera sur le **Noms de domaine personnalisés** et **Environnement** pages, vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Reportez-vous au document [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour plus d’informations.

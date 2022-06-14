---
title: Vérification de l’état du nom de domaine
description: Découvrez comment déterminer si Cloud Manager a vérifié votre nom de domaine personnalisé avec succès.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: ba0226b5ad3852dd5f72dd7e0ace650035f5ac6a
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 13%

---


# Vérification de l’état du nom de domaine {#check-status}

Vous pouvez déterminer l’état de votre nom de domaine personnalisé dans Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

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

## Erreurs de nom de domaine {#domain-error}

Cette section explique les erreurs que vous pouvez afficher et comment les résoudre.

**Domaine non installé** - Vous recevez cette erreur lors de la validation du domaine de l’enregistrement TXT même après avoir vérifié que l’enregistrement a été mis à jour de manière appropriée.

**Explication des erreurs** - verrouille rapidement un domaine sur le compte initial qui l’a enregistré et aucun autre compte ne peut enregistrer un sous-domaine sans demander l’autorisation. De plus, Fastly vous permet uniquement d’affecter un domaine apex et des sous-domaines associés à un seul service et compte Fastly. Si vous disposez d’un compte Fastly qui lie les mêmes apex et sous-domaines utilisés pour vos domaines AEM Cloud Service, cette erreur s’affichera.

**Résolution des erreurs** - L&#39;erreur est corrigée comme suit :

* Supprimez les apex et les sous-domaines du compte existant avant d’installer le domaine dans Cloud Manager. Utilisez cette option pour associer le domaine APX et tous les sous-domaines au compte as a Cloud Service Fastly AEM. Voir [Utilisation des domaines dans la documentation Fastly](https://docs.fastly.com/en/guides/working-with-domains) pour plus d’informations.

* Si votre domaine apex comporte plusieurs sous-domaines pour AEM sites as a Cloud Service as a Cloud Service et non-AEM que vous souhaitez lier à différents comptes Fastly, essayez d’installer le domaine dans Cloud Manager et si l’installation du domaine échoue, créez un ticket d’assistance clientèle avec Fastly afin que nous puissions suivre Fastly en votre nom.

>[!NOTE]
>
>REMARQUE : Ne routez pas le DNS de votre site vers les adresses IP as a Cloud Service si le domaine n’a pas été installé correctement.

## Configurations CDN pré-existantes pour les noms de domaine personnalisés {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau de diffusion de contenu préexistante pour vos noms de domaine personnalisés, un message d’information s’affichera sur le **Noms de domaine personnalisés** et **Environnement** pages, vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Reportez-vous au document [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour plus d’informations.

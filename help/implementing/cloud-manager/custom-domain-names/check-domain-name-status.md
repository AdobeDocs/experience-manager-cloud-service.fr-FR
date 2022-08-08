---
title: Vérification du statut du nom de domaine
description: Découvrez comment déterminer si Cloud Manager a vérifié votre nom de domaine personnalisé avec succès.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: ba0226b5ad3852dd5f72dd7e0ace650035f5ac6a
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 100%

---


# Vérification du statut du nom de domaine {#check-status}

Vous pouvez déterminer le statut de votre nom de domaine personnalisé dans Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **Paramètres du domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **Statut** pour le nom de domaine.

Cloud Manager vérifie la propriété du domaine via la valeur TXT et affiche l’un des messages de statut suivants.

* **Échec de la vérification du domaine** - La valeur TXT est manquante ou des erreurs ont été détectées.

   * Suivez les instructions fournies pour résoudre le problème.
   * Une fois prêt, vous devez sélectionner l’icône **Vérifier à nouveau** en face du statut.

* **Vérification du domaine en cours** - Vérification en cours.

   * Ce statut apparaît généralement après avoir sélectionné l’icône **Vérifier à nouveau** en face du statut.

* **Vérifié, échec du déploiement** - La vérification TXT a réussi mais le déploiement CDN a échoué.

   * Dans ce cas, contactez votre représentant Adobe.

* **Domaine vérifié et déployé** - Ce statut indique que votre nom de domaine personnalisé est prêt à être utilisé.

   * À ce stade, votre nom de domaine personnalisé est prêt à être testé et pointé vers le nom de domaine Cloud Manager.
   * Reportez-vous au document [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour en savoir plus.

* **Suppression** - La suppression d’un nom de domaine personnalisé est en cours.

* **Échec de la suppression** - La suppression du nom de domaine personnalisé a échoué et doit être réexécutée.

   * Consultez le document [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

Cloud Manager déclenche automatiquement une vérification TXT lorsque vous sélectionnez **Enregistrer** à l’étape de vérification de l’assistant **Ajout de domaine personnalisé**. Pour les vérifications suivantes, vous devez prendre l’initiative et sélectionner l’icône Vérifier à nouveau en face du statut.

## Erreurs de nom de domaine {#domain-error}

Cette section explique les erreurs que vous pouvez voir et comment les résoudre.

**Domaine non installé** - Vous recevez cette erreur lors de la validation du domaine de l’enregistrement TXT même après avoir vérifié que l’enregistrement a été mis à jour de manière appropriée.

**Explication des erreurs** - Fastly verrouille rapidement un domaine sur le compte initial qui l’a enregistré, aucun autre compte ne peut enregistrer un sous-domaine sans demander l’autorisation. De plus, Fastly ne vous permet d’affecter qu’un seul domaine apex et ses sous-domaines associés à un seul service et compte Fastly. Si vous disposez d’un compte Fastly qui lie les mêmes apex et sous-domaines utilisés pour vos domaines AEM Cloud Service, cette erreur s’affichera.

**Résolution des erreurs** - L’erreur est corrigée comme suit :

* Supprimez les apex et les sous-domaines du compte existant avant d’installer le domaine dans Cloud Manager. Utilisez cette option pour associer le domaine apex et tous les sous-domaines au compte Fastly AEM as a Cloud Service. Consultez [Utilisation des domaines dans la documentation Fastly](https://docs.fastly.com/en/guides/working-with-domains) pour plus d’informations.

* Si votre domaine apex comporte plusieurs sous-domaines pour les sites AEM as a Cloud Service et non-AEM as a Cloud Service que vous souhaitez lier à différents comptes Fastly, essayez d’installer le domaine dans Cloud Manager et, si l’installation du domaine échoue, créez un ticket d’assistance clientèle avec Fastly afin que nous puissions suivre Fastly en votre nom.

>[!NOTE]
>
>REMARQUE : Ne routez pas le DNS de votre site vers les adresses IP d’AEM as a Cloud Service si le domaine n’a pas été installé correctement.

## Configurations CDN pré-existantes pour les noms de domaine personnalisés {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau CDN préexistante pour vos noms de domaine personnalisés, un message d’information s’affichera dans les pages **Noms de domaine personnalisés** et **Environnement**, vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Consultez le document [Obtention d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour plus d’informations.

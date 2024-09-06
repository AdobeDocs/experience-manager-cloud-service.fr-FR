---
title: Vérification du statut du nom de domaine
description: Découvrez comment déterminer si Cloud Manager a vérifié votre nom de domaine personnalisé avec succès.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 64%

---


# Vérification du statut du nom de domaine {#check-status}

Découvrez comment déterminer si Cloud Manager a vérifié votre nom de domaine personnalisé avec succès.

## Conditions requises {#requirements}

Vous devez respecter ces exigences avant de vérifier l’état de votre nom de domaine dans Cloud Manager.

* Vous devez d’abord ajouter un enregistrement TXT pour votre domaine personnalisé, comme décrit dans le document [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md).

## Comment vérifier l’état de votre nom de domaine personnalisé {#how-to}

Vous pouvez déterminer le statut de votre nom de domaine personnalisé dans Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à l’écran **Environnements** à partir de la page **Vue d’ensemble**.

1. Cliquez sur **Paramètres de domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **Statut** pour le nom de domaine.

Le détail de l’état s’affiche. Votre domaine personnalisé est prêt à être utilisé lorsque l’état **Domaine vérifié et déployé** est affiché. Consultez la [section suivante](#statuses) pour plus d’informations sur les différents statuts et sur ce qu’ils signifient.

>[!NOTE]
>
>Cloud Manager déclenche automatiquement la vérification lorsque vous sélectionnez **Créer** à l’étape de vérification de l’assistant **Ajouter un domaine personnalisé** lors de l’ [ajout d’un nouveau nom de domaine personnalisé à Cloud Manager](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Pour les vérifications suivantes, vous devez prendre l’initiative et sélectionner l’icône Vérifier à nouveau en face du statut.

## Compréhension des états de vérification {#statuses}

Cloud Manager vérifie la propriété du domaine via la [valeur TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) et affiche l’un des messages d’état suivants.

* **Échec de la vérification du domaine** - La valeur TXT est manquante ou des erreurs ont été détectées.

   * Suivez les instructions fournies dans le message d’état pour résoudre le problème.
   * Une fois prêt, vous devez sélectionner l’icône **Vérifier à nouveau** en face du statut.

* **Vérification du domaine en cours** - Vérification en cours.

   * Ce statut apparaît généralement après avoir sélectionné l’icône **Vérifier à nouveau** en face du statut.
   * La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.

* **Vérifié, échec du déploiement** - La vérification TXT a réussi mais le déploiement CDN a échoué.

   * Dans ce cas, contactez votre personne représentante Adobe.

* **Domaine vérifié et déployé** - Ce statut indique que votre nom de domaine personnalisé est prêt à être utilisé.

   * À ce stade, votre nom de domaine personnalisé est prêt à être testé et pointé vers le nom de domaine Cloud Manager.
   * Voir [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour en savoir plus.

* **Suppression** - La suppression d’un nom de domaine personnalisé est en cours.

* **Échec de la suppression** - La suppression du nom de domaine personnalisé a échoué et doit être réexécutée.

   * Voir [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

## Erreurs de nom de domaine {#domain-error}

Vous trouverez ci-dessous quelques erreurs courantes de vérification des noms de domaine et leurs résolutions courantes.

### Erreur de domaine non installé {#domain-not-installed}

Cette erreur peut se produire lors de la validation du domaine de l’enregistrement TXT, même après avoir vérifié que l’enregistrement a été mis à jour de manière appropriée.

#### Cause de l’erreur {#cause}

Fastly verrouille un domaine sur le compte initial qui l’a enregistré et aucun autre compte ne peut enregistrer de sous-domaine sans demander l’autorisation. De plus, Fastly vous permet d&#39;affecter un domaine apex et des sous-domaines associés à un seul service et compte Fastly. Si un compte Fastly existant lie les mêmes apex et sous-domaines utilisés pour vos domaines AEM Cloud Service, cette erreur s’affiche.

#### Résolution d’erreurs {#resolution}

L’erreur est résolue comme suit :

* Supprimez les apex et les sous-domaines du compte existant avant d’installer le domaine dans Cloud Manager.

* Utilisez cette option pour associer le domaine apex et tous les sous-domaines au compte Fastly AEM as a Cloud Service. Consultez [Utilisation des domaines dans la documentation Fastly](https://docs.fastly.com/en/guides/working-with-domains) pour plus d’informations.

* Si votre domaine apex comporte plusieurs sous-domaines pour des sites AEM as a Cloud Service et hors AEM as a Cloud Service que vous souhaitez lier à différents comptes Fastly, essayez d’installer le domaine dans Cloud Manager. Si l’installation du domaine échoue, créez un ticket d’assistance clientèle avec Fastly afin qu’Adobe puisse faire un suivi auprès de Fastly en votre nom.

>[!TIP]
>
>La résolution des problèmes de délégation de domaine avec Fastly prend généralement 1 à 2 jours ouvrés. Pour cette raison, il est vivement recommandé d’installer les domaines bien avant leur date d’activation.

>[!NOTE]
>
>Ne routez pas le DNS de votre site vers les adresses IP d’AEM as a Cloud Service si le domaine n’a pas été correctement installé.

## Configurations de réseau CDN préexistantes pour les noms de domaine personnalisés {#pre-existing-cdn}

Si vous disposez d’une configuration CDN préexistante pour vos noms de domaine personnalisés, un message informatif s’affiche sur les pages **Noms de domaine personnalisés** et **Environnement**, vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Pour plus d’informations, consultez la section [Affichage et mise à jour du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

## Étapes suivantes {#next-steps}

Une fois que vous avez vérifié l’état de votre domaine dans Cloud Manager, vous devez configurer les paramètres DNS en ajoutant des enregistrements CNAME DNS ou APEX qui pointent vers AEM as a Cloud Service. Passez au document [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour continuer à configurer votre nom de domaine personnalisé.

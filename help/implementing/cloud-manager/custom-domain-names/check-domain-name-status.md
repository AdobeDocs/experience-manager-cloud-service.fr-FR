---
title: Vérifier l’état du nom de domaine
description: Découvrez comment vérifier que Cloud Manager a confirmé avec succès votre nom de domaine personnalisé.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ff8c7fb21b4d8bcf395d28c194a7351281eef45b
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 24%

---


# Vérification de l’état du nom de domaine {#check-status}

Découvrez comment vérifier que Cloud Manager a confirmé avec succès votre nom de domaine personnalisé.

## Conditions requises {#requirements}

Renseignez ces conditions préalables avant de vérifier l’état de votre nom de domaine dans Cloud Manager.

* Ajoutez d’abord un certificat EV/OV pour votre domaine personnalisé, comme décrit dans le document [Ajoutez un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

## Vérifiez l’état de votre nom de domaine personnalisé. {#how-to}

Vous pouvez déterminer l’état de votre nom de domaine personnalisé dans Cloud Manager.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à l’écran **Environnements** à partir de la page **Vue d’ensemble**.

1. Cliquez sur **Paramètres de domaine** dans le panneau de navigation de gauche.

1. Cliquez sur le bouton **Statut** pour le nom de domaine.

Le détail de l’état s’affiche. Votre domaine personnalisé est prêt à être utilisé lorsque l’état **Domaine vérifié et déployé** est affiché. Consultez la [section suivante](#statuses) pour plus d’informations sur les différents statuts et sur ce qu’ils signifient.

>[!NOTE]
>
>Cloud Manager déclenche automatiquement la vérification lorsque vous sélectionnez **Créer** à l’étape de vérification de l’assistant **Ajouter un domaine personnalisé** lors de l’ [ajout d’un nouveau nom de domaine personnalisé à Cloud Manager](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Pour les vérifications suivantes, vous devez prendre l’initiative et sélectionner l’icône Vérifier à nouveau en face du statut.

## Statuts de vérification {#statuses}

Cloud Manager vérifie la propriété du domaine par le biais du certificat géré par le client. Une fois cette opération terminée, l’un des messages d’état suivants s’affiche :

| État | Description |
| --- | --- |
| Échec de la vérification du domaine | Le certificat EV/OV géré par le client est manquant ou est détecté avec des erreurs.<br> Suivez les instructions du message d’état pour résoudre le problème. Une fois prêt, vous devez sélectionner l’icône **Vérifier à nouveau** en face du statut. |
| Vérification des domaines en cours | La vérification est en cours.<br>Cet état s’affiche généralement une fois que vous avez sélectionné l’icône **Vérifier de nouveau** en regard de l’état. La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS. |
| Vérifié - Échec du déploiement | La vérification du certificat EV/OV a réussi, mais le déploiement CDN a échoué.<br>Dans ce cas, contactez votre représentant Adobe. |
| Domaine vérifié et déployé | Ce statut indique que votre nom de domaine personnalisé est prêt à être utilisé.<br>À ce stade, votre nom de domaine personnalisé est prêt pour le test et doit pointer vers le nom de domaine Cloud Manager. Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour en savoir plus. |
| Suppression en cours | La suppression d’un nom de domaine personnalisé est en cours. |
| Échec de la suppression | La suppression d’un nom de domaine personnalisé a échoué et doit être refaite.<br>Voir [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus. |


## Erreurs de nom de domaine {#domain-error}

Vous trouverez ci-dessous quelques erreurs courantes de vérification des noms de domaine et leurs résolutions courantes.

### Domaine non installé {#domain-not-installed}

Cette erreur peut se produire lors de la validation du domaine du certificat EV/OV, même après avoir vérifié que le certificat a été mis à jour de manière appropriée.

#### Cause d’erreur {#cause}

Permet de verrouiller rapidement un domaine sur le compte qui l’enregistre pour la première fois, et les autres comptes doivent demander l’autorisation d’enregistrer un sous-domaine. De plus, Fastly vous permet d&#39;affecter un domaine apex et des sous-domaines associés à un seul service et compte Fastly. Si un compte Fastly existant lie les mêmes apex et sous-domaines utilisés pour vos domaines AEM Cloud Service, cette erreur s’affiche.

#### Résolution des erreurs {#resolution}

L’erreur est résolue comme suit :

* Supprimez les apex et les sous-domaines du compte existant avant d’installer le domaine dans Cloud Manager.

* Utilisez cette option pour associer le domaine apex et tous les sous-domaines au compte Fastly AEM as a Cloud Service. Consultez [Utilisation des domaines dans la documentation Fastly](https://docs.fastly.com/en/guides/working-with-domains) pour plus d’informations.

* Si votre domaine apex comporte plusieurs sous-domaines pour AEM as a Cloud Service et les sites non AEM qui doivent se lier à différents comptes Fastly, essayez d’installer le domaine dans Cloud Manager. Ce processus permet de gérer les connexions de sous-domaines entre différents comptes Fastly. Si l’installation du domaine échoue, créez un ticket d’assistance clientèle à l’aide de Fastly afin que l’Adobe puisse le suivre en votre nom.

>[!TIP]
>
>La résolution des problèmes de délégation de domaine avec Fastly prend généralement 1 à 2 jours ouvrés. Pour cette raison, il est vivement recommandé d’installer les domaines bien avant leur date d’activation.

>[!NOTE]
>
>Ne routez pas le DNS de votre site vers les adresses IP d’AEM as a Cloud Service si le domaine n’a pas été correctement installé.

## Configurations CDN préexistantes pour les noms de domaine personnalisés {#pre-existing-cdn}

Si vous disposez déjà d’une configuration CDN pour vos noms de domaine personnalisés, un message d’information s’affiche sur les pages **Noms de domaine personnalisés** et **Environnement** . Il vous encourage à ajouter ces configurations via l’interface utilisateur afin qu’elles puissent être gérées et visualisées dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes ont été migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Pour plus d’informations, voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) .

## Étapes suivantes {#next-steps}

Après avoir vérifié l’état de votre domaine dans Cloud Manager, configurez les paramètres DNS en ajoutant des enregistrements DNS, CNAME ou APEX qui pointent vers AEM as a Cloud Service. Passez au document [Ajoutez un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour continuer à configurer votre nom de domaine personnalisé.

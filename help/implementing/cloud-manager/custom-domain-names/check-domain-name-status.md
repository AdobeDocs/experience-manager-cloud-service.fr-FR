---
title: Vérifier le statut du nom de domaine
description: Découvrez comment vérifier que Cloud Manager a confirmé votre nom de domaine personnalisé.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 17%

---


# Vérification du statut du nom de domaine {#check-status}

Découvrez comment vérifier que Cloud Manager a confirmé votre nom de domaine personnalisé.

## Vérification de l’état d’un nom de domaine personnalisé {#how-to}

Avant de vérifier le statut de votre nom de domaine dans Cloud Manager, assurez-vous d’avoir déjà ajouté un certificat SSL géré par le client (OV/EV) pour votre domaine personnalisé, comme décrit dans la section [Ajouter un certificat SSL géré par le client](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md##add-customer-managed-ssl-cert).

**Pour vérifier l’état d’un nom de domaine personnalisé :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à l’écran **Environnements** à partir de la page **Vue d’ensemble**.

1. Cliquez sur **Paramètres du domaine** dans le menu de gauche.

1. Cliquez sur le bouton **Statut** pour le nom de domaine.

Les détails du statut s’affichent. Votre domaine personnalisé est prêt à être utilisé lorsque le statut **Domaine vérifié et déployé** s’affiche. Voir la [section suivante](#statuses) pour plus d’informations sur les différents statuts et leur signification.

>[!NOTE]
>
>Si vous utilisez un certificat SSL *géré par Adobe (DV)* avec le domaine, Cloud Manager déclenche automatiquement la vérification lorsque vous cliquez sur **Vérifier** dans la boîte de dialogue Vérifier le domaine lorsque [vous ajoutez un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
>
>Si vous envisagez d’utiliser un **certificat SSL géré par le client (OV/EV)**, votre domaine est vérifié *après* vous [ ajouter le certificat SSL OV/EV](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).


## Statuts de vérification {#statuses}

Cloud Manager vérifie la propriété du domaine via le certificat SSL géré par le client (OV/EV). Lorsque vous avez terminé, l’un des messages de statut suivants s’affiche :

| État | Description |
| --- | --- |
| Échec de la vérification du domaine | Le certificat EV/OV géré par le client est manquant ou des erreurs ont été détectées.<br> Suivez les instructions fournies dans le message de statut pour résoudre le problème. Une fois prêt, vous devez sélectionner l’icône **Vérifier à nouveau** en face du statut. |
| Vérification du domaine en cours | Vérification en cours.<br>Ce statut apparaît généralement après avoir sélectionné l’icône **Vérifier à nouveau** en regard du statut. La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS. |
| Vérifié - Échec du déploiement | La vérification du certificat EV/OV a réussi, mais le déploiement CDN a échoué.<br>Dans ce cas, contactez votre représentant Adobe. |
| Domaine vérifié et déployé | Ce statut indique que votre nom de domaine personnalisé est prêt à être utilisé.<br>À ce stade, votre nom de domaine personnalisé est prêt à être testé et à pointer vers le nom de domaine Cloud Manager. Voir [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour en savoir plus. |
| Suppression en cours | La suppression d&#39;un nom de domaine personnalisé est en cours. |
| Échec de la suppression | La suppression d’un nom de domaine personnalisé a échoué et doit être réexécutée.<br>Voir [Gérer les noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus. |


## Erreur de nom de domaine {#domain-error}

Voici une erreur courante de vérification des noms de domaine et sa résolution standard.

### Erreur de domaine non installé {#domain-not-installed}

<!-- This error may occur during domain validation of the EV/OV certificate even after you have checked that the certificate has been updated appropriately. -->

Lorsque vous tentez d’ajouter un mappage de domaine dans Cloud Manager, le message d’erreur suivant peut s’afficher :

*Le domaine est déjà installé dans un compte Fastly. Supprimez-le d’abord de cet emplacement avant de l’ajouter à Cloud Service.*

<!-- This message indicates that the domain is currently associated with a different Fastly account—typically outside of Adobe's control. To proceed, the domain must be disassociated from the other account before it can be added to the Adobe-managed Cloud Service. This issue usually occurs when the same domain is already mapped to a different origin in a non-Adobe Fastly configuration. -->

**Cause de l’erreur**
Fastly verrouille un domaine sur le compte qui l’enregistre en premier, tandis que les autres comptes doivent demander l’autorisation d’enregistrer un sous-domaine. En outre, Fastly ne vous permet d’affecter qu’un seul domaine apex et ses sous-domaines associés à un seul service et compte Fastly. Cette erreur s’affiche si vous disposez d’un compte Fastly qui lie les mêmes apex et sous-domaines utilisés pour vos domaines AEM Cloud Service.

**Résolution d’erreurs**
L’erreur est corrigée comme suit :

* Supprimez les apex et les sous-domaines du compte existant avant d’installer le domaine dans Cloud Manager.

* Utilisez cette option pour associer le domaine apex et tous les sous-domaines au compte Fastly AEM as a Cloud Service. Voir [Utilisation des domaines](https://www.fastly.com/documentation/guides/getting-started/domains/working-with-domains/working-with-domains/) dans la documentation Fastly pour plus d’informations.

* Si votre domaine apex comporte plusieurs sous-domaines pour des sites AEM as a Cloud Service et non AEM qui doivent être liés à différents comptes Fastly, essayez d’installer le domaine dans Cloud Manager. Ce processus permet de gérer les connexions de sous-domaines sur différents comptes Fastly. Si l’installation du domaine échoue, créez un ticket d’assistance clientèle avec Fastly afin qu’Adobe puisse assurer le suivi auprès de Fastly en votre nom.

>[!TIP]
>
>La résolution des problèmes de délégation de domaine avec Fastly prend généralement 1 à 2 jours ouvrés. Pour cette raison, il est recommandé d’installer les domaines bien avant leur date d’activation.

>[!NOTE]
>
>Ne routez pas le DNS de votre site vers les adresses IP d’AEM as a Cloud Service si le domaine n’a pas été correctement installé.

## Configurations CDN préexistantes pour les noms de domaine personnalisés {#pre-existing-cdn}

Si vous disposez déjà d’une configuration CDN (réseau de diffusion de contenu) pour vos noms de domaine personnalisés, un message d’information s’affiche sur les pages **Noms de domaine personnalisés** et **Environnement**. Cela vous incite à ajouter ces configurations par le biais de l’interface utilisateur afin qu’elles puissent être gérées et affichées dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes ont été migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Voir [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour plus d’informations.

## Étapes suivantes {#next-steps}

Après avoir vérifié le statut de votre domaine dans Cloud Manager, configurez les paramètres DNS en ajoutant des enregistrements DNS, CNAME ou APEX qui pointent vers AEM as a Cloud Service. Accédez au document [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) pour continuer à configurer votre nom de domaine personnalisé.

---
title: Gestion des certificats SSL
description: Découvrez comment utiliser Cloud Manager pour vérifier l’état de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
source-git-commit: 6cc1620d139db3804325c118d0874c5f94cb23a4
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 30%

---

# Gestion des certificats SSL {#managing-ssl-certificates}

Découvrez comment utiliser Cloud Manager pour vérifier l’état de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.

## Vérification de l’état des certificats SSL {#checking-status-an-ssl-certificate}

L’état de vos certificats SSL se comprend d’un seul coup d’oeil grâce à la page de certificat SSL.

* **Vert** - Cet état indique que votre certificat est valide pendant au moins 60 jours à compter de la date actuelle.

* **Orange** - Ce statut indique que votre certificat doit expirer dans moins de 60 jours.
   * Il est temps de vous assurer que vous disposez d’un plan de renouvellement de votre certificat afin de le remplacer via l’interface utilisateur de Cloud Manager et d’éviter d’éventuelles interruptions d’accès au site.
   * Cloud Manager envoie régulièrement des notifications dans l’interface utilisateur pour vous avertir d’une expiration imminente du certificat.

* **Rouge** - Ce statut indique que le certificat SSL a expiré.

## Configurations de réseau de diffusion de contenu préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau de diffusion de contenu préexistante pour votre certificat SSL, un message d’information s’affichera sur le **Certificats SSL** , vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Reportez-vous au document [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) pour plus d’informations.

Un message similaire est également fourni dans la variable **LISTE AUTORISÉE IP** et le **Environnements** pages pour les environnements qui possèdent des configurations CDN préexistantes pour les listes autorisées IP ou les noms de domaine personnalisés.

## Mise à jour d’un certificat SSL {#update-ssl-certificate}

Lorsqu’un certificat expire, tout domaine utilisé avec le certificat expiré ne fonctionne plus. La mise à jour de vos certificats par le biais des étapes suivantes garantit que votre domaine continue à fonctionner comme vous le souhaitez.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à **Environnements** de l’écran **Présentation** page.
1. Accédez au **Certificats SSL** de l’écran **Environnements** écran.
1. Un tableau contenant une ligne pour chaque certificat SSL qui a été installé correctement dans votre programme apparaît. Cliquez sur le bouton représentant des points de suspension tout à droite de la ligne du certificat que vous souhaitez mettre à jour et sélectionnez **Afficher et mettre à jour**.
1. Les détails du certificat s’affichent et peuvent être mis à jour.

>[!NOTE]
>
>Un utilisateur doit être membre de la fonction **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour mettre à jour un certificat SSL dans Cloud Manager.

## Remplacement d’un certificat SSL {#replace-ssl-certificate}

Un certificat SSL peut être remplacé en suivant les mêmes étapes que celles décrites dans la section . [Mise à jour d’un certificat SSL.](#update-ssl-certificate)

## Suppression d’un certificat SSL {#deleting-an-ssl-certificate}

La suppression de certificats de Cloud Manager est une action permanente qui ne peut pas être annulée. Adobe recommande, en règle générale, d’enregistrer les fichiers SSL localement avant de les supprimer dans Cloud Manager.

Cloud Manager ne vous permet pas de supprimer un certificat SSL associé à un ou plusieurs domaines. Tous les domaines associés doivent être supprimés avant de supprimer le certificat SSL. Reportez-vous au document [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

Pour supprimer un certificat SSL, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à **Environnements** de l’écran **Présentation** page.
1. Accédez au **Certificats SSL** de l’écran **Environnements** écran.
1. Un tableau contenant une ligne pour chaque certificat SSL qui a été installé correctement dans votre programme apparaît. Cliquez sur le bouton représentant des points de suspension tout à droite de la ligne du certificat que vous souhaitez supprimer, puis sélectionnez **Supprimer**.
1. Confirmez la suppression dans le **Suppression de certificat SSL** boîte de dialogue.

>[!NOTE]
>
>Un utilisateur doit être membre de la fonction **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour supprimer un certificat SSL dans Cloud Manager.

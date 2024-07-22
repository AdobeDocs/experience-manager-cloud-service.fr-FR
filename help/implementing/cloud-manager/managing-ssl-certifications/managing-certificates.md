---
title: Gestion des certificats SSL
description: Découvrez comment utiliser Cloud Manager pour vérifier le statut de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 35ac4cfb18e348281d2b126bdc3b292c84590f3a
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 78%

---


# Gestion des certificats SSL {#managing-ssl-certificates}

Découvrez comment utiliser Cloud Manager pour vérifier le statut de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.

## Vérification du statut des certificats SSL {#checking-status-an-ssl-certificate}

Le statut de vos certificats SSL se comprend d’un seul coup d’œil grâce à la page de certificat SSL.

* **Vert** - Ce statut indique que votre certificat est valide pendant au moins 14 jours à compter de la date actuelle.

* **Orange** - Ce statut indique que votre certificat va expirer dans moins de 14 jours.
   * Il est temps de vous assurer que vous disposez d’un plan de renouvellement de votre certificat afin de le remplacer via l’interface utilisateur de Cloud Manager et d’éviter d’éventuelles interruptions d’accès au site.
   * Cloud Manager envoie régulièrement des notifications dans l’interface utilisateur pour vous avertir d’une expiration imminente du certificat.

* **Rouge** - Ce statut indique que le certificat SSL a expiré.

## Mise à jour d’un certificat SSL {#update-ssl-certificate}

Lorsqu’un certificat expire, tout domaine utilisé avec le certificat expiré ne fonctionne plus. La mise à jour de vos certificats par le biais des étapes suivantes garantit que votre domaine continue à fonctionner comme vous le souhaitez.

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à l’écran **Certificats SSL** à partir de l’écran **Environnements**.
1. Vous pouvez voir un tableau avec une ligne pour chaque certificat SSL installé avec succès dans votre programme. Cliquez sur le bouton représentant des points de suspension tout à droite de la ligne du certificat que vous souhaitez mettre à jour, puis sélectionnez **Afficher et mettre à jour**.
1. Les détails du certificat s’affichent et peuvent être mis à jour.
1. Enregistrez vos modifications.

Une fois vos modifications enregistrées, elles sont appliquées automatiquement.

>[!NOTE]
>
>L’utilisateur ou l’utilisatrice doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour pouvoir mettre à jour un certificat SSL dans Cloud Manager.

## Remplacement d’un certificat SSL {#replace-ssl-certificate}

Vous pouvez remplacer un certificat SSL en suivant les mêmes étapes que celles décrites dans la section [Mise à jour d’un certificat SSL.](#update-ssl-certificate)

## Suppression d’un certificat SSL {#deleting-an-ssl-certificate}

La suppression de certificats de Cloud Manager est une action permanente qui ne peut pas être annulée. Adobe recommande, en règle générale, d’enregistrer les fichiers SSL localement avant de les supprimer dans Cloud Manager.

Cloud Manager ne vous permet pas de supprimer un certificat SSL associé à un ou plusieurs domaines. Tous les domaines associés doivent être supprimés avant de supprimer le certificat SSL. Voir [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

Procédez comme suit pour supprimer un certificat SSL.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à l’écran **Certificats SSL** à partir de l’écran **Environnements**.
1. Vous pouvez voir un tableau avec une ligne pour chaque certificat SSL installé avec succès dans votre programme. Cliquez sur les points de suspension tout à droite de la ligne du certificat que vous souhaitez supprimer, puis sélectionnez **Supprimer**.
1. Confirmez la suppression dans la boîte de dialogue **Supprimer le certificat SSL**.
1. Exécutez le pipeline pour annuler le déploiement du certificat supprimé.

>[!NOTE]
>
>Un utilisateur ou une utilisatrice doit disposer du rôle **Propriétaire d’entreprise** ou **Responsable de déploiement** pour pouvoir supprimer un certificat SSL dans Cloud Manager.

## Configurations de réseau CDN préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration CDN préexistante pour votre certificat SSL, un message informatif s’affiche sur la page **Certificats SSL**, vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) pour plus d’informations.

Un message similaire est également fourni dans la **Liste d’adresses IP autorisées** et les pages **Environnements** pour les environnements qui possèdent des configurations CDN préexistantes pour les liste d’adresses IP autorisées ou les noms de domaine personnalisés.

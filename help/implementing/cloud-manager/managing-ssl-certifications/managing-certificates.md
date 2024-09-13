---
title: Gestion des certificats SSL
description: Découvrez comment utiliser Cloud Manager pour vérifier le statut de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d2f05915c0bf0af073db7f070b83f13aeae55252
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 13%

---


# Gestion des certificats SSL {#managing-ssl-certificates}

Découvrez comment utiliser Cloud Manager pour vérifier l’état des certificats SSL gérés par votre Adobe et gérés par le client et comment les supprimer. Pour les certificats gérés par le client, vous pouvez également les modifier et les mettre à jour (les remplacer).

## Vérification de l’état des certificats SSL {#checking-status-an-ssl-certificate}

L’état de vos certificats SSL peut être compris en un coup d’oeil à partir de la page **SSL Certificates**.

| État du certificat SSL | Description |
| --- | --- |
| Vert | Le certificat est valide pendant au moins 14 jours à compter de la date actuelle. |
| Orange | Le certificat doit expirer dans moins de 14 jours.<br> ・ Assurez-vous que vous disposez d’un plan pour renouveler votre certificat et le remplacer au moyen de l’interface utilisateur de Cloud Manager afin d’éviter tout accès ou interruption au site.<br> ・ Cloud Manager envoie des notifications régulières dans l’interface utilisateur pour vous alerter d’une expiration de certificat imminente. |
| Rouge | Le certificat SSL a expiré.<br>Voir [Mise à jour d’un certificat SSL géré par un client expiré](#update-ssl-certificate) ou [Suppression d’un certificat SSL](#deleting-an-ssl-certificate). |

## Mise à jour d’un certificat SSL géré par un client arrivé à expiration {#update-ssl-certificate}

Lorsqu’un certificat géré par le client expire, les domaines qui sont utilisés avec le certificat expiré ne fonctionnent plus. La mise à jour de vos certificats garantit que votre domaine continue à fonctionner comme vous le souhaitez.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour mettre à jour un certificat SSL géré par un client expiré :**

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.
1. Dans l’écran **Environments** (Environnements), accédez à l’écran **Certificats SSL**.
1. Dans la ligne du certificat géré par le client arrivé à expiration que vous souhaitez mettre à jour, cliquez sur le bouton représentant des points de suspension à l’extrémité droite, puis sélectionnez **Afficher et mettre à jour**.

   ![Mettre à jour une certification SSL gérée par un client expirée](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. Dans la boîte de dialogue **Afficher et mettre à jour le certificat SSL**, procédez comme suit :

   * (Facultatif) Dans le champ **Certificate name** , saisissez un nouveau nom.
   * Dans le champ **Certificate** , collez la nouvelle clé de contenu du certificat.
   * Dans le champ **Clé privée** , mettez à jour ce champ uniquement si vous avez apporté des modifications au certificat.
   * Dans le champ **Certificate chain** (ou chaîne de confiance), collez la chaîne de certificat.

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications et les faire appliquer automatiquement.

## Remplacement d’un certificat SSL géré par un client arrivé à expiration {#replace-ssl-certificate}

Suivez les mêmes étapes que celles décrites dans la section [Mettre à jour un certificat SSL expiré](#update-ssl-certificate) pour remplacer un certificat SSL géré par le client arrivé à expiration.

## Suppression d’un certificat SSL {#deleting-an-ssl-certificate}

La suppression des certificats SSL gérés par Adobe ou gérés par le client de Cloud Manager est une action permanente qui ne peut pas être annulée. Adobe recommande, en règle générale, d’enregistrer les fichiers SSL localement avant de les supprimer dans Cloud Manager.

>[!NOTE]
>
>Vous ne pouvez pas supprimer un certificat SSL géré par un Adobe auquel un ou plusieurs domaines actifs sont associés. Tous les domaines actifs associés doivent être supprimés avant de supprimer le certificat SSL. Voir [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer un certificat SSL :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.
1. Dans l’écran **Environments** (Environnements), accédez à l’écran **Certificats SSL**.
1. Dans la ligne du certificat que vous souhaitez supprimer, cliquez sur le bouton représentant des points de suspension à l’extrémité droite, puis sélectionnez **Supprimer**.
Si le bouton Supprimer comporte une icône d’information comme illustré dans l’image suivante, reportez-vous à la remarque ci-dessus.

   ![Bouton Supprimer avec icône d’informations](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. Dans la boîte de dialogue **Supprimer le certificat SSL**, cliquez sur **Supprimer** pour confirmer la suppression.
1. Exécutez le pipeline pour annuler le déploiement du certificat supprimé.

## Configurations CDN préexistantes {#pre-existing-cdn}

Si vous disposez déjà d’une configuration CDN pour votre certificat SSL, la page **Certificats SSL** affiche un message informatif. Il vous encourage à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et gérables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes ont été migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Pour plus d’informations, voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) .

Un message similaire est également fourni sur les pages **Liste autorisée IP** et **Environnements** pour les environnements ayant des configurations CDN préexistantes pour les Listes autorisées IP ou les noms de domaine personnalisés.

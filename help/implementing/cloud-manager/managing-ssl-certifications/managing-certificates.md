---
title: Gérer des certificats SSL
description: Découvrez comment utiliser Cloud Manager pour vérifier le statut de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f12392075b71b219bf449f585f63561167ddada9
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 9%

---


# Gérer des certificats SSL {#managing-ssl-certificates}

Découvrez comment utiliser Cloud Manager pour vérifier le statut de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.

## Vérification de l’état des certificats SSL {#checking-status-an-ssl-certificate}

Cloud Manager donne un aperçu de l’état de tous les certificats de votre programme.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.
1. Sous l’en-tête **Services**, cliquez sur ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

La page **Certificats SSL** fournit l’état de vos certificats SSL.

| État du certificat SSL | Description |
| --- | --- |
| Vert | Le certificat est valide pendant au moins 14 jours à compter de la date actuelle. |
| Orange | Le certificat doit expirer dans moins de 14 jours.<br> ・ Assurez-vous que vous disposez d’un plan pour renouveler votre certificat et le remplacer au moyen de l’interface utilisateur de Cloud Manager afin d’éviter tout accès ou interruption au site.<br> ・ Cloud Manager envoie des notifications régulières dans l’interface utilisateur pour vous alerter d’une expiration de certificat imminente. |
| Rouge | Le certificat SSL a expiré.<br>Voir [Mise à jour d’un certificat SSL géré par un client expiré](#update-ssl-certificate) ou [Suppression d’un certificat SSL](#deleting-an-ssl-certificate). |

## Mise à jour d’un certificat SSL géré par un client arrivé à expiration {#update-ssl-certificate}

Lorsqu’un certificat géré par le client expire, les domaines qui sont utilisés avec le certificat expiré ne fonctionnent plus. La mise à jour de vos certificats garantit que votre domaine continue à fonctionner comme vous le souhaitez.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour mettre à jour un certificat SSL géré par un client expiré :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.
1. Sous l’en-tête **Services**, cliquez sur ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.
1. Dans la ligne du certificat géré par le client arrivé à expiration que vous souhaitez mettre à jour, cliquez sur le bouton représentant des points de suspension à l’extrémité droite, puis sélectionnez **Afficher et mettre à jour**.

   ![Mettre à jour une certification SSL gérée par un client expirée](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. Dans la boîte de dialogue **Afficher et mettre à jour le certificat SSL**, procédez comme suit :

   * (Facultatif) Dans le champ **Certificate name** , saisissez un nouveau nom.
   * Dans le champ **Certificate** , collez la nouvelle clé de contenu du certificat.
   * Dans le champ **Clé privée** , mettez à jour ce champ uniquement si vous avez apporté des modifications au certificat.
   * Dans le champ **Certificate chain** (ou chaîne de confiance), collez la chaîne de certificat.

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications et les faire appliquer automatiquement.


>[!NOTE]
>
>Si vous disposez de deux certificats SAN ou plus qui couvrent la même entrée de domaine SAN, si ce domaine est couvert par un certificat et que l’autre est mis à jour, ce dernier est installé pour le domaine.
>
>Pour plus d’informations, voir [Dépannage des problèmes de certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md#wrong-san-cert) .

## Remplacement d’un certificat SSL géré par un client arrivé à expiration {#replace-ssl-certificate}

Suivez les mêmes étapes que celles décrites dans la section [Mettre à jour un certificat SSL expiré](#update-ssl-certificate) pour remplacer un certificat SSL géré par le client arrivé à expiration.

## Renommer un certificat SSL géré par un Adobe (#rename-an-ssl-certificate)

Voici quelques raisons pour lesquelles vous pouvez renommer un certificat SSL :

* **Organisation améliorée** : le changement de nom du certificat peut contribuer à clarifier son objectif, par exemple en identifiant l’environnement (par exemple, l’évaluation, la production) ou le domaine dans lequel il se trouve.
* **Eviter toute confusion** : si vous gérez plusieurs certificats, un nom clair et descriptif peut vous aider à éviter les erreurs, comme appliquer le mauvais certificat au mauvais domaine.
* **Conformité et audit** : les certificats correctement nommés peuvent être plus faciles à suivre à des fins de sécurité et d’audit.

**Pour renommer un certificat SSL géré par un Adobe :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.

1. Sous l’en-tête **Services**, cliquez sur ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

1. Sur la page **Certificats SSL**, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont le certificat SSL **Adobe managed** que vous souhaitez renommer.

1. Dans le menu déroulant, cliquez sur **Renommer**.

1. Dans la boîte de dialogue **Renommer le certificat DV**, dans le champ de texte **Nom du certificat**, saisissez le nouveau nom du certificat.

1. Cliquez sur **Renommer**.


## Suppression d’un certificat SSL {#deleting-an-ssl-certificate}

La suppression des certificats SSL gérés par Adobe ou gérés par le client de Cloud Manager est une action permanente qui ne peut pas être annulée. Adobe recommande, en règle générale, d’enregistrer les fichiers SSL localement avant de les supprimer dans Cloud Manager.

>[!NOTE]
>
>Vous ne pouvez pas supprimer un certificat SSL géré par un Adobe auquel un ou plusieurs domaines actifs sont associés. Tous les domaines actifs associés doivent être supprimés avant de supprimer le certificat SSL. Voir [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer un certificat SSL :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.

1. Sous l’en-tête **Services**, cliquez sur ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

1. Sur la page Certificats SSL, dans la ligne de tableau du certificat que vous souhaitez supprimer, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrémité droite.

1. Dans le menu déroulant, cliquez sur **Supprimer**.

   Si **Supprimer** comporte une icône d&#39;information telle qu&#39;elle est vue dans l&#39;image suivante, consultez la remarque ci-dessus.

   ![Bouton Supprimer avec icône d’informations](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. Dans la boîte de dialogue **Supprimer le certificat SSL**, cliquez sur **Supprimer** pour confirmer la suppression.

1. Exécutez le pipeline pour annuler le déploiement du certificat supprimé.


## Configurations CDN préexistantes {#pre-existing-cdn}

Si vous disposez déjà d’une configuration CDN pour votre certificat SSL, la page **Certificats SSL** affiche un message informatif. Il vous encourage à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et gérables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes ont été migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre un et deux jours ouvrés avant que le message disparaisse.

Pour plus d’informations, voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) .

Un message similaire est également fourni sur les pages **Liste autorisée IP** et **Environnements** pour les environnements ayant des configurations CDN préexistantes pour les Listes autorisées IP ou les noms de domaine personnalisés.

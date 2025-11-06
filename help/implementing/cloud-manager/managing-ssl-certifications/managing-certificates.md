---
title: Gérer des certificats SSL
description: Découvrez comment utiliser Cloud Manager pour vérifier le statut de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 13%

---


# Gérer des certificats SSL {#managing-ssl-certificates}

Découvrez comment utiliser Cloud Manager pour vérifier le statut de vos certificats SSL et comment les modifier, les remplacer, les mettre à jour et les supprimer.

## Vérifier le statut des certificats SSL {#checking-status-an-ssl-certificate}

Cloud Manager donne un aperçu du statut de tous les certificats de votre programme.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Afficher l’icône de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.
1. Sous l’en-tête **Services**, cliquez sur ![Icône Verrouiller fermé](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

La page **Certificats SSL** fournit le statut de vos certificats SSL.

| Statut du certificat SSL | Description |
| --- | --- |
| Vert | Le certificat est valide pendant au moins 14 jours à compter de la date actuelle. |
| Orange | Le certificat va expirer dans moins de 14 jours.<br>· Assurez-vous d’avoir un plan de renouvellement de votre certificat et remplacez-le par le biais de l’interface utilisateur de Cloud Manager afin d’éviter d’éventuelles interruptions d’accès au site.<br>· Cloud Manager envoie régulièrement des notifications dans l’interface utilisateur pour vous avertir d’une expiration imminente du certificat. |
| Rouge | Le certificat SSL a expiré.<br>Voir [Mettre à jour un certificat SSL géré par le client expiré](#update-ssl-certificate) ou [Supprimer un certificat SSL](#deleting-an-ssl-certificate). |

## Mettre à jour un certificat SSL expiré géré par le client {#update-ssl-certificate}

Lorsqu’un certificat géré par le client expire, les domaines utilisés avec le certificat expiré ne fonctionnent plus. La mise à jour de vos certificats garantit que votre domaine continue à fonctionner comme vous le souhaitez.

Un utilisateur doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

>[!IMPORTANT]
>
>Lors de l’ajout ou de la mise à jour d’un certificat SSL, n’incluez pas le nouveau certificat dans la chaîne de certificats. Son inclusion empêche le chargement de s’effectuer correctement.

**Pour mettre à jour un certificat SSL expiré géré par le client :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Afficher l’icône de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.
1. Sous l’en-tête **Services**, cliquez sur ![Icône Verrouiller fermé](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.
1. Dans la ligne du certificat géré par le client expiré que vous souhaitez mettre à jour, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrême droite, puis cliquez sur **Afficher et mettre à jour**.

   ![Mettre à jour une certification SSL expirée gérée par le client](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. Dans la boîte de dialogue **Afficher et mettre à jour le certificat SSL**, procédez comme suit :

   * (Facultatif) Dans le champ **Nom du certificat**, saisissez un nouveau nom.
   * Dans le champ **Certificat**, collez la nouvelle clé de contenu du certificat.
   * Dans le champ **Clé privée**, mettez à jour ce champ uniquement si vous avez apporté des modifications au certificat.
   * Dans le champ **Chaîne de certificats** (ou chaîne de confiance), collez la chaîne de certificats.

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications et les appliquer automatiquement.


>[!NOTE]
>
>Si plusieurs certificats SAN couvrent la même entrée de domaine SAN et que l’un d’eux est mis à jour, le système installe le certificat mis à jour pour le domaine.
>
>Voir [Résolution des problèmes de certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md#wrong-san-cert) pour plus d’informations.

## Remplacer un certificat SSL expiré géré par le client {#replace-ssl-certificate}

Suivez les mêmes étapes que celles décrites dans [Mise à jour d’un certificat SSL expiré](#update-ssl-certificate) pour remplacer un certificat SSL expiré géré par le client.

## Renommer un certificat SSL géré par Adobe (#rename-an-ssl-certificate)

Voici quelques raisons de renommer un certificat SSL :

* **Amélioration de l’organisation** : la modification du nom du certificat peut aider à clarifier son objectif, comme l’identification de l’environnement (par exemple, d’évaluation, de production) ou du domaine auquel il correspond.
* **Pour éviter toute confusion** : si vous gérez plusieurs certificats, un nom clair et descriptif peut vous aider à éviter les erreurs, comme l’application du mauvais certificat au mauvais domaine.
* **Conformité et audit** : le suivi de certificats correctement nommés peut être plus facile à effectuer à des fins de sécurité et d’audit.

**Pour renommer un certificat SSL géré par Adobe, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Afficher l’icône de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.

1. Sous l’en-tête **Services**, cliquez sur ![Icône Verrouiller fermé](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

1. Sur la page **Certificats SSL**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez renommer le certificat SSL **géré par Adobe**.

1. Dans le menu déroulant, cliquez sur **Renommer**.

1. Dans la boîte de dialogue **Renommer le certificat DV**, dans le champ de texte **Nom du certificat**, saisissez le nouveau nom du certificat.

1. Cliquez sur **Renommer**.


## Suppression d’un certificat SSL {#deleting-an-ssl-certificate}

La suppression des certificats SSL gérés par Adobe ou gérés par le client depuis Cloud Manager est une action permanente qui ne peut pas être annulée. Adobe recommande, en règle générale, d’enregistrer les fichiers SSL localement avant de les supprimer dans Cloud Manager.

>[!NOTE]
>
>Vous ne pouvez pas supprimer un certificat SSL géré par Adobe associé à un ou plusieurs domaines actifs. Tous les domaines actifs associés doivent être supprimés avant de supprimer le certificat SSL. Voir [Gérer les noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) pour en savoir plus.

Un utilisateur doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer un certificat SSL, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Afficher l’icône de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.

1. Sous l’en-tête **Services**, cliquez sur ![Icône Verrouiller fermé](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

1. Sur la page Certificats SSL, dans la ligne de tableau du certificat à supprimer, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrémité droite, puis cliquez sur **Supprimer**.

   Si **Supprimer** comporte une icône d’information comme illustré dans l’image suivante, reportez-vous à la remarque ci-dessus.

   ![Bouton Supprimer avec icône Informations](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. Dans la boîte de dialogue **Supprimer le certificat SSL**, cliquez sur **Supprimer** pour confirmer la suppression.

1. Exécutez le pipeline pour annuler le déploiement du certificat supprimé.


## Configurations de réseau CDN préexistantes {#pre-existing-cdn}

Si vous disposez déjà d’une configuration de réseau CDN pour votre certificat SSL, la page **Certificats SSL** affiche un message d’information. Cela vous incite à ajouter ces configurations par le biais de l’interface utilisateur afin qu’elles soient visibles et gérables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes ont été migrées à l’aide de l’interface utilisateur. La disparition du message peut prendre un à deux jours ouvrables.

Voir [Ajouter un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) pour plus d’informations.

Un message similaire est également fourni dans les pages **Liste autorisée IP** et **Environnements** pour les environnements qui disposent de configurations CDN préexistantes pour les Listes autorisées IP ou les noms de domaine personnalisés.

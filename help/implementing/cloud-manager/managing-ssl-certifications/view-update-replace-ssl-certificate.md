---
title: 'Affichage de la mise à jour et du remplacement d’un certificat SSL - Gestion de SSL '
description: Affichage de la mise à jour et du remplacement d’un certificat SSL - Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Affichage et mise à jour et remplacement d’un certificat SSL {#view-update-replace-ssl-certificate}

## Affichage et mise à jour d’un certificat SSL {#view-update}

Quand utiliser ces options dans l’interface utilisateur de Cloud Manager :

* Un certificat existant est sur le point d&#39;expirer. L’utilisateur a renouvelé le certificat auprès du fournisseur du certificat et souhaite remplacer le certificat existant sur le point d’expirer. Remarque Seuls les utilisateurs disposant des autorisations appropriées peuvent effectuer des mises à jour.
* Utilisez le menu **Vue et mise à jour** pour simplement vue les détails du certificat SSL.
* Vous pouvez également modifier le nom utilisé pour référencer un certificat à partir de cet écran.
* Seul l’utilisateur disposant des autorisations appropriées peut effectuer des mises à jour.


## Mise à jour d’un certificat SSL sur le point d’expirer {#update-ssl-certificate}

Lorsqu’un certificat expire, les domaines utilisés avec le certificat expiré ne fonctionneront plus. Pour mettre à jour un certificat expiré, vous devez suivre les étapes ci-dessous. Ainsi, votre domaine continuera à fonctionner comme vous le souhaitez. Pour Ajouter un nouveau certificat, il est nécessaire de mettre à jour le nom de domaine personnalisé avec le nouveau certificat avant que les domaines ne fonctionnent comme vous le souhaitez. Pour plus d&#39;informations, consultez [Affichage et mise à jour et remplacement d&#39;un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md).

Pour mettre à jour un certificat SSL, procédez comme suit :

>[!NOTE]
>Un utilisateur doit se trouver dans le rôle Business Owner ou Deployment Manager pour pouvoir mettre à jour un certificat SSL dans Cloud Manager.

1. Accédez à l’écran Certificats SSL à partir de la page **Environnements**.
1. Un tableau contenant une ligne pour chaque certificat SSL qui a été correctement installé dans votre programme s’affiche.
1. Pour accéder aux options de menu de chaque ligne, sélectionnez les trois boutons situés à l’extrémité droite de la ligne concernée.
1. Sélectionnez **Vue et mise à jour**. Les détails du certificat peuvent être affichés ici.

## Remplacement d’un certificat SSL {#replace-ssl-certificate}

Pour remplacer un certificat SSL, procédez comme suit :

1. Accédez à l’écran Certificats SSL à partir de la page **Environnements**.
1. Un tableau contenant une ligne pour chaque certificat SSL qui a été correctement installé dans votre programme s’affiche.
1. Pour accéder aux options de menu de chaque ligne, sélectionnez les trois boutons situés à l’extrémité droite de la ligne concernée.
1. Sélectionnez **Vue et mise à jour**.
1. Pour remplacer le certificat, collez le nouveau contenu dans les champs d’entrée appropriés et cliquez sur **Enregistrer**. Vous devrez corriger toutes les erreurs qui peuvent survenir.

   Consultez [Erreurs de certificat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-error) pour résoudre les problèmes courants.
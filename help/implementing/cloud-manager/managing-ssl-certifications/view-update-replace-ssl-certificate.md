---
title: 'Affichage, mise à jour et remplacement d’un certificat SSL – Gestion de SSL '
description: Affichage, mise à jour et remplacement d’un certificat SSL – Gestion des certificats SSL
exl-id: 662494b1-a710-4822-97ef-057043ef89ba
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 100%

---

# Affichage et mise à jour et remplacement d’un certificat SSL  {#view-update-replace-ssl-certificate}

## Affichage et mise à jour d’un certificat SSL {#view-update}

Quand utiliser ces options dans l’interface utilisateur de Cloud Manager :

* Un certificat existant est sur le point d’expirer. L’utilisateur a renouvelé le certificat auprès du fournisseur du certificat et souhaite remplacer le certificat existant sur le point d’expirer. Remarque : Seuls les utilisateurs disposant des autorisations appropriées peuvent effectuer des mises à jour.
* Utilisez le menu **Afficher et mettre à jour** pour afficher simplement les détails du certificat SSL.
* Vous pouvez également modifier le nom utilisé pour faire référence à un certificat à partir de cet écran.
* Seuls les utilisateurs disposant des autorisations appropriées peuvent effectuer des mises à jour.


## Mise à jour d’un certificat SSL sur le point d’expirer {#update-ssl-certificate}

Lorsqu’un certificat expire, tout domaine utilisé avec le certificat expiré ne fonctionne plus. Pour mettre à jour un certificat expiré, vous devez suivre les étapes ci-dessous. Ainsi, votre domaine continuera à fonctionner comme vous le souhaitez. L’ajout d’un nouveau certificat nécessite la mise à jour du nom de domaine personnalisé avec le nouveau certificat avant que les domaines ne fonctionnent comme vous le souhaitez. Pour plus d’informations, consultez [Affichage, mise à jour et remplacement d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md).

Pour mettre à jour un certificat SSL, procédez comme suit :

>[!NOTE]
>Un utilisateur doit être un propriétaire d’entreprise ou un responsable du déploiement pour pouvoir mettre à jour un certificat SSL dans Cloud Manager.

1. Accédez à l’écran Certificats SSL à partir de la page **Environnements**.
1. Un tableau contenant une ligne pour chaque certificat SSL qui a été installé correctement dans votre programme apparaît.
1. Pour accéder aux options de menu de chaque ligne, sélectionnez les trois boutons situés à l’extrémité droite de la ligne concernée.
1. Sélectionnez **Afficher et mettre à jour**. Les informations concernant le certificat peuvent être affichées ici.

## Remplacement d’un certificat SSL {#replace-ssl-certificate}

Pour remplacer un certificat SSL, procédez comme suit :

1. Accédez à l’écran Certificats SSL à partir de la page **Environnements**.
1. Un tableau contenant une ligne pour chaque certificat SSL qui a été installé correctement dans votre programme apparaît.
1. Pour accéder aux options de menu de chaque ligne, sélectionnez les trois boutons situés à l’extrémité droite de la ligne concernée.
1. Sélectionnez **Afficher et mettre à jour**.
1. Pour remplacer le certificat, collez le nouveau contenu dans les champs de saisie appropriés et cliquez sur **Enregistrer**. Vous devez corriger toute erreur qui peut survenir.

   Reportez-vous à [Erreurs de certificat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-error) pour résoudre les problèmes les plus courants.

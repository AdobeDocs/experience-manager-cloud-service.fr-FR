---
title: Gestion des noms de domaine personnalisés
description: Découvrez comment utiliser Cloud Manager pour afficher, mettre à jour, remplacer et supprimer des noms de domaine personnalisés.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 31%

---

# Gestion des noms de domaine personnalisés {#managing-custom-domain-names}

Cloud Manager vous permet d’afficher, de mettre à jour, de remplacer et de supprimer des noms de domaine personnalisés.

## Afficher et mettre à jour {#view-and-update}

Utilisez la variable **Afficher et mettre à jour** pour afficher les détails de l’un de vos noms de domaine personnalisés.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Environnements** de l’écran **Présentation** page.

1. Identifiez la ligne du nom de domaine personnalisé que vous souhaitez afficher ou mettre à jour.

1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.

1. Sélectionnez l’option **Afficher et mettre à jour**.

## Mise à jour du certificat SSL du nom de domaine personnalisé {#update-cert}

Vous pouvez suivre [les mêmes étapes pour afficher et mettre à jour un nom de domaine personnalisé ;](#view-and-update) pour mettre à jour le certificat SSL d’un nom de domaine personnalisé.

>[!NOTE]
>
>Le certificat SSL doit être valide, [déjà configuré,](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) et contiennent le nom de domaine personnalisé que vous mettez à jour.

##  Suppression d’un nom de domaine personnalisé {#deleting}

Un utilisateur avec la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut utiliser Cloud Manager pour supprimer un nom de domaine personnalisé.

### Suppression d’un nom de domaine personnalisé de tous les environnements associés {#delete-cdn-all}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Environnements** de l’écran **Présentation** page.

1. Accédez à la page **Paramètres de domaine** à partir de l’écran **Environnements**.

1. Identifiez la ligne du nom de domaine personnalisé que vous souhaitez supprimer.

1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.

1. Sélectionnez **Supprimer**.

   ![Suppression de noms de domaine personnalisés](/help/implementing/cloud-manager/assets/cdn/cdn-delete.png)

1. Confirmez votre envoi.

### Suppression d’un nom de domaine personnalisé d’un environnement spécifique {#delete-cdn-specific}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez au **Environnements** de l’écran **Présentation** page.
1. Dans la **Environnements** , accédez à l’écran des détails de l’environnement ciblé.
1. Dans la table des noms de domaine, identifiez la ligne du nom de domaine personnalisé que vous souhaitez supprimer.
1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.
1. Sélectionnez **Supprimer**.
1. Confirmez votre envoi.

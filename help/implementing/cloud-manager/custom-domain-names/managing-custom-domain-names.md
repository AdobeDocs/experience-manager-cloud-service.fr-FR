---
title: Gestion des noms de domaine personnalisés
description: Découvrez comment utiliser Cloud Manager pour afficher, mettre à jour, remplacer et supprimer des noms de domaine personnalisés.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
source-git-commit: c8599d4a0c3093bf3cff630745ada95e64124fef
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 100%

---

# Gestion des noms de domaine personnalisés {#managing-custom-domain-names}

Cloud Manager vous permet d’afficher, de mettre à jour, de remplacer et de supprimer des noms de domaine personnalisés.

## Affichage et mise à jour {#view-and-update}

Utilisez le menu **Affichage et mise à jour** pour afficher simplement les détails d’un ou plusieurs de vos noms de domaine personnalisé.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Identifiez la ligne où figure le nom de domaine personnalisé que vous souhaitez afficher ou mettre à jour.

1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.

1. Sélectionnez l’option **Afficher et mettre à jour**.

## Mise à jour du certificat SSL du nom de domaine personnalisé {#update-cert}

Vous pouvez suivre [les mêmes étapes pour afficher et mettre à jour un nom de domaine personnalisé](#view-and-update) pour mettre à jour le certificat SSL d’un nom de domaine personnalisé.

>[!NOTE]
>
>Le certificat SSL doit être valide, [déjà configuré](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md), et contenir le nom de domaine personnalisé que vous mettez à jour.

## Suppression d’un nom de domaine personnalisé {#deleting}

Un utilisateur avec le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut utiliser Cloud Manager pour supprimer un nom de domaine personnalisé.

### Suppression d’un nom de domaine personnalisé de tous les environnements associés {#delete-cdn-all}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Paramètres de domaine** à partir de l’écran **Environnements**.

1. Identifiez la ligne où figure le nom de domaine personnalisé que vous souhaitez supprimer.

1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.

1. Sélectionnez **Supprimer**.

   ![Suppression de noms de domaine personnalisé](/help/implementing/cloud-manager/assets/cdn/cdn-delete.png)

1. Confirmez votre envoi.

### Suppression d’un nom de domaine personnalisé d’un environnement spécifique {#delete-cdn-specific}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Sur la page **Environnements**, accédez à l’écran des détails de l’environnement qui vous intéresse.
1. Dans le tableau des noms de domaines, identifiez la ligne où figure le nom de domaine personnalisé que vous souhaitez supprimer.
1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.
1. Sélectionnez **Supprimer**.
1. Confirmez votre envoi.

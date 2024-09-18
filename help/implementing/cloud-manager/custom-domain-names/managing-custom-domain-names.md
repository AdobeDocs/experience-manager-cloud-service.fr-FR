---
title: Gestion des noms de domaine personnalisés
description: Découvrez comment utiliser Cloud Manager pour afficher, mettre à jour, remplacer et supprimer des noms de domaine personnalisés.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8e2fc0d4ee82e79d1a822a528b1a46acce3c192a
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 35%

---


# Gestion des noms de domaine personnalisés {#managing-custom-domain-names}

Cloud Manager vous permet de modifier, mettre à jour, remplacer et supprimer des noms de domaine personnalisés.

## Modification d’une configuration de nom de domaine personnalisé {#view-and-update}

Dans Adobe Cloud Manager, vous pouvez modifier une configuration de nom de domaine personnalisée pour les raisons suivantes :

* **Changement d’environnement** : pour appliquer la configuration appropriée selon que vous diffusez du contenu aux utilisateurs finaux (Publish) ou aux utilisateurs internes (Auteur).
* **Mises à jour de sécurité** : mise à niveau vers un certificat SSL plus récent à des fins de sécurité ou de conformité améliorée.
* **Modification de la stratégie de déploiement** : pour s’assurer que le certificat SSL correct est appliqué à un environnement spécifique pour un chiffrement correct et un accès au site.

**Pour modifier une configuration de nom de domaine personnalisé :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le coin supérieur gauche de la page, cliquez sur l’icône représentant un hamburger pour afficher le menu de navigation de gauche.
1. Sous l’en-tête **Services**, cliquez sur **Configurations CDN**.
1. Sur la page **Configurations du réseau de diffusion de contenu**, cliquez sur les points de suspension en fin de ligne dont vous souhaitez modifier le réseau de diffusion de contenu.
1. Cliquez sur **Modifier**.
1. Dans la boîte de dialogue **Modifier la configuration CDN**, procédez comme suit :
   * Dans la liste déroulante **Niveau** , sélectionnez le niveau (Auteur ou Publish) à utiliser.
   * Dans la liste déroulante **SSL certificate**, sélectionnez le certificat SSL que vous souhaitez utiliser.
1. Cliquez sur **Mettre à jour**.


## Mise à jour du certificat SSL d’un nom de domaine personnalisé {#update-cert}

Vous pouvez suivre [les mêmes étapes pour afficher et mettre à jour un nom de domaine personnalisé](#view-and-update) pour mettre à jour le certificat SSL d’un nom de domaine personnalisé.

>[!NOTE]
>
>Le certificat SSL doit être valide, [déjà configuré](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) et contenir le nom de domaine personnalisé que vous mettez à jour.


## Suppression d’un nom de domaine personnalisé {#deleting}

Un utilisateur avec le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut utiliser Cloud Manager pour supprimer un nom de domaine personnalisé.

### Suppression d’un nom de domaine personnalisé de tous les environnements associés {#delete-cdn-all}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la page **Paramètres de domaine** à partir de l’écran **Aperçu**.

1. Identifiez la ligne du nom de domaine personnalisé que vous souhaitez supprimer.

1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.

1. Sélectionnez **Supprimer**.

1. Confirmez votre envoi.


### Suppression d’un nom de domaine personnalisé d’un environnement spécifique {#delete-cdn-specific}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Sur la page **Environnements** , accédez à un écran de détails de l’environnement intéressant.
1. Dans le tableau des noms de domaine, identifiez la ligne du nom de domaine personnalisé que vous souhaitez supprimer.
1. Cliquez sur le bouton représentant des points de suspension à l’extrémité droite de la ligne.
1. Sélectionnez **Supprimer**.
1. Confirmez votre envoi.

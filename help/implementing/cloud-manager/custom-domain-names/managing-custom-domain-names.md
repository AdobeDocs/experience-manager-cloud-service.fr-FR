---
title: Gérer les noms de domaine personnalisés
description: Découvrez comment utiliser Cloud Manager pour afficher, mettre à jour, remplacer et supprimer des noms de domaine personnalisés.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 27d9a48c6afa115d5c755fa54cf96cb6a561b2f5
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 20%

---


# Gestion des noms de domaine personnalisés {#managing-custom-domain-names}

Cloud Manager vous permet de modifier, mettre à jour, remplacer, vérifier et supprimer des noms de domaine personnalisés.

## Modification d’une configuration de nom de domaine personnalisé {#view-and-update}

Dans Adobe Cloud Manager, vous pouvez modifier une configuration de nom de domaine personnalisée pour les raisons suivantes :

* **Changement d’environnement** : pour appliquer la configuration appropriée selon que vous diffusez du contenu aux utilisateurs finaux (Publish) ou aux utilisateurs internes (Auteur).
* **Mises à jour de sécurité** : mise à niveau vers un certificat SSL plus récent à des fins de sécurité ou de conformité améliorée.
* **Modification de la stratégie de déploiement** : pour s’assurer que le certificat SSL correct est appliqué à un environnement spécifique pour un chiffrement correct et un accès au site.

**Pour modifier une configuration de nom de domaine personnalisé :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher - hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de navigation de gauche.

1. Sous l’en-tête **Services**, cliquez sur **Configurations CDN**.

1. Sur la page **Configurations du réseau de diffusion de contenu**, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez modifier le réseau de diffusion de contenu.

1. Cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier la configuration CDN**, procédez comme suit :

   * Dans la liste déroulante **Niveau** , sélectionnez le niveau (Publish ou Aperçu) à utiliser.
   * Dans la liste déroulante **Certificat SSL**, sélectionnez le certificat SSL que vous souhaitez utiliser.

1. Cliquez sur **Mettre à jour**.


## Mise à jour du certificat SSL d’un nom de domaine personnalisé {#update-cert}

Suivez les mêmes étapes ci-dessus pour mettre à jour le certificat SSL d’un nom de domaine personnalisé.

>[!NOTE]
>
>Le certificat SSL doit être valide, [déjà configuré](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) et contenir le nom de domaine personnalisé que vous mettez à jour.


## Vérification d’un nom de domaine personnalisé {#verify-custom-domain-name}

Voir aussi [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la page **Paramètres de domaine** à partir de l’écran **Aperçu**.

1. Identifiez la ligne du nom de domaine personnalisé que vous souhaitez vérifier.

1. Cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrémité droite de la ligne.

1. Dans le menu déroulant, cliquez sur **Vérifier**.

1. Dans la boîte de dialogue **Vérifier le domaine**, dans le **Quel type de certificat prévoyez-vous d’utiliser avec ce domaine ?Sélectionnez l’une des options suivantes dans la liste déroulante** :

   | Option de type de certificat | Description |
   | --- | --- |
   | Certificat SSL géré par Adobe (DV) | Sélectionnez ce type de certificat si vous souhaitez utiliser un certificat DV (Domain Validation). Cette option est idéale pour la plupart des cas, car elle fournit une validation de domaine de base. Adobe gère et renouvelle automatiquement le certificat. |
   | Certificat SSL géré par le client (OV/EV) | Sélectionnez ce type de certificat si vous envisagez d’utiliser un certificat SSL EV/OV pour sécuriser le domaine. Cette option offre une sécurité améliorée avec OV (validation de l’organisation) ou EV (validation étendue). Utilisez cette option si une vérification plus stricte, des niveaux de confiance plus élevés ou un contrôle personnalisé sur les certificats est requis. |

1. Dans la boîte de dialogue **Vérifier le domaine**, en fonction du type de certificat que vous avez sélectionné, effectuez l’une des opérations suivantes :

   | Si vous avez sélectionné le type de certificat | Description |
   | --- | ---  |
   | Certificat géré par Adobe | a. Exécutez les [étapes du certificat géré par Adobe](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-steps). Lorsque vous exécutez les étapes de la boîte de dialogue **Vérifier le domaine**, cliquez sur **Vérifier**.<ul><li>La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.</li><li>Cloud Manager vérifie finalement la propriété des noms de domaine et met à jour l’état dans la table **Paramètres de domaine**. Voir [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.</li>![Vérifier l’état du domaine](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. Vous êtes maintenant prêt à [ajouter un certificat SSL géré par Adobe (DV)](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert).</li></ul> |
   | Certificat géré par le client ou la cliente | a. Cliquez sur **OK**.<br>b. Vous êtes maintenant prêt à [ajouter un certificat SSL géré par le client (OV/EV)](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert).<br>Après avoir ajouté le certificat, votre nom de domaine est marqué comme vérifié dans la table **Paramètres de domaine**. Voir [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.</li></ul><br>![Vérification du domaine pour un certificat EV/OV géré par un client ou une cliente](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |


## Suppression d’un nom de domaine personnalisé de tous les environnements associés {#deleting}

Un utilisateur avec le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut utiliser Cloud Manager pour supprimer un nom de domaine personnalisé.

### Suppression d’un nom de domaine personnalisé de tous les environnements associés {#delete-cdn-all}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la page **Paramètres de domaine** à partir de l’écran **Aperçu**.

1. Identifiez la ligne du nom de domaine personnalisé que vous souhaitez supprimer.

1. Cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrémité droite de la ligne.

1. Sélectionnez **Supprimer**.

1. Confirmez votre envoi.


### Suppression d’un nom de domaine personnalisé d’un environnement spécifique {#delete-cdn-specific}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Sur la page **Environnements** , accédez à un écran de détails de l’environnement intéressant.

1. Dans le tableau des noms de domaine, identifiez la ligne du nom de domaine personnalisé que vous souhaitez supprimer.

1. Cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrémité droite de la ligne.

1. Sélectionnez **Supprimer**.

1. Confirmez votre envoi.

---
title: Rôles de Cloud Manager
description: Cette page décrit les rôles et autorisations des utilisateurs. Consultez cette page pour savoir comment ajouter des utilisateurs et les affecter à des rôles de Cloud Manager.
exl-id: d1689134-044a-4d96-97a2-cd09f735a680
source-git-commit: a0edbaf650fdfbc271a000ab4827a4c414321613
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 92%

---

# Rôles de Cloud Manager {#user-roles-permissions}

## Rôles utilisateur {#user-roles}

De nombreuses fonctionnalités de Cloud Manager nécessitent des autorisations spécifiques pour opérer et limiter les actions que vous effectuez dans l’interface utilisateur en fonction des rôles et des autorisations attribués. Dans certains cas, si vous n’êtes pas autorisé à effectuer une action, le contrôle d’interface est présent, mais désactivé.

Si vous souhaitez effectuer une action, mais que vous ne pouvez pas, consultez la section ci-dessous, [Rôles utilisateur et autorisations](#permissions). Selon votre objectif, vous pouvez contacter l’administrateur système et demander le rôle dont vous avez besoin.

Cloud Manager définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Responsable de programme
* Développeur

>[!NOTE]
>Dans Admin Console, le développeur n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

## Affichage de vos rôles {#view-roles}

Pour afficher vos rôles dans Cloud Manager, connectez-vous à l’interface utilisateur de Cloud Manager, sélectionnez l’icône de votre profil dans l’angle supérieur droit et sélectionnez **Rôles utilisateur**, comme illustré dans la figure ci-dessous.

>[!NOTE]
>Voir [Accéder à Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md) pour en savoir plus sur la connexion à Cloud Manager.

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### Profil de produit d’intégration {#integration-product-profile}

En plus de ce qui précède, Cloud Manager crée automatiquement un profil de produits nommé « Intégrations – Cloud Service ». Ce profil de produit est utilisé pour les intégrations entre Adobe Experience Manager et d’autres produits d’Adobe. Ce profil de produit **ne doit pas** être supprimé. Si vous supprimez accidentellement ce profil, il doit être recréé manuellement. Le nom d’affichage de ce profil **doit** être `CM_CS_DEFAULT`.


## Rôles utilisateur et autorisations {#permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le référentiel Git. Un propriétaire d’entreprise dispose également d’autorisations différentes lui permettant d’ajouter et de modifier des programmes, d’ajouter des environnements et d’approuver des déploiements.

Chacun des rôles est associé à des autorisations spécifiques. Par exemple, si vous êtes dans le rôle d’un :

* ***Propriétaire de l’entreprise***, vous êtes autorisé à ajouter un nouveau programme ou à modifier un programme, à ajouter ou mettre à jour un environnement et à exécuter n’importe quel pipeline.

* ***Deployment Manager*** vous permet d’ajouter ou de mettre à jour un environnement et d’exécuter n’importe quel pipeline.

* ***Développeur***, vous êtes autorisé à générer un jeton d’accès personnel pour accéder à Git.

   >[!NOTE]
   > Un utilisateur peut être affecté à plusieurs rôles. Par exemple, l’attribution des rôles Propriétaire de l’entreprise et Responsable de déploiement à un utilisateur leur donne la combinaison ou la somme de ces autorisations.


Le tableau suivant résume les rôles et les autorisations associées dans Cloud Manager.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajouter un programme<br>Modifier le programme | Ajout d’un nouveau programme.<br>Modification d’un programme – Ajout ou suppression de solutions ou de modules complémentaires | x |  |  |  |
| Créer un environnement | Créer des environnements Prod+Éval, Dév, etc. | x | x |  |  |
| Mettre à jour l’environnement | Mettre à jour Prod+Éval, Dév, Environnements. | x | x |  |  |
| Suppression de l’environnement de dév | Supprimer les environnements de développement. | x | x |  |  |
| Configuration du pipeline | Configurer ou modifier un pipeline. |  | x |  |  |
| Exécution du pipeline | Démarrer le pipeline. | x | x |  |  |
| Exécution du pipeline | Refuser/approuver des échecs importants de 3 niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Suppression de pipeline | Permet la suppression d’un pipeline. |  | x |  |  |
| Annuler l’exécution | Annuler l’exécution actuelle. |  | x |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git. |  | x |  | x |

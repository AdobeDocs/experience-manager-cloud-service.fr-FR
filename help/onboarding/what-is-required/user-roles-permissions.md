---
title: Rôles de Cloud Manager
description: Cette page décrit les rôles et autorisations des utilisateurs. Consultez cette page pour savoir comment ajouter des utilisateurs et les affecter à des rôles Cloud Manager.
exl-id: d1689134-044a-4d96-97a2-cd09f735a680
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 19%

---

# Rôles de Cloud Manager {#user-roles-permissions}

## Rôles utilisateur {#user-roles}

De nombreuses fonctionnalités de Cloud Manager nécessitent des autorisations spécifiques pour opérer et limiter les actions que vous effectuez dans l’interface utilisateur en fonction des rôles et des autorisations attribués. Dans certains cas, si vous n’êtes pas autorisé à effectuer une action, le contrôle d’interface est présent, mais désactivé.

Si vous souhaitez effectuer une action, mais ne pouvez pas, consultez la section ci-dessous, [Rôles utilisateur et autorisations](#permissions). Selon votre objectif, vous pouvez contacter l’administrateur système et demander le rôle dont vous avez besoin.

Cloud Manager définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Responsable de programme
* Développeur

>[!NOTE]
>Dans Admin Console, le développeur n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

## Affichage de vos rôles {#view-roles}

Pour afficher vos rôles dans Cloud Manager, connectez-vous à l’interface utilisateur de Cloud Manager, sélectionnez l’icône de votre profil dans le coin supérieur droit et sélectionnez **Rôles utilisateur**, comme illustré dans la figure ci-dessous.

>[!NOTE]
>Voir [Accédez à Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md) pour en savoir plus sur la connexion à Cloud Manager.

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### Profil de produit d’intégration {#integration-product-profile}

Outre ce qui précède, Cloud Manager crée automatiquement un profil de produit nommé &quot;Intégrations - Cloud Service&quot;. Ce profil de produit est utilisé pour les intégrations entre Adobe Experience Manager et d’autres produits Adobe. Ce profil de produit **ne doit pas** être supprimé. Si vous supprimez accidentellement ce profil, il devra être recréé manuellement. Le nom d’affichage de ce profil **doit** être `CM_CS_DEFAULT`.


## Rôles utilisateur et autorisations {#permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et dispose de l’autorisation de transférer le code vers le référentiel Git. Un propriétaire d’entreprise dispose également d’autorisations différentes lui permettant d’ajouter et de modifier des programmes, d’ajouter des environnements et d’approuver des déploiements.

Chacun des rôles est associé à des autorisations spécifiques. Par exemple, si vous êtes dans le rôle d’un :

* ***Propriétaire de l’entreprise***, vous êtes autorisé à ajouter un nouveau programme ou à modifier un programme, à ajouter ou mettre à jour un environnement, à ajouter/modifier/supprimer le pipeline et à exécuter n’importe quel pipeline, ainsi qu’à déployer le code pour AEM la qualité de l’environnement ou du code.

* ***Deployment Manager*** vous permet d’ajouter ou de mettre à jour un environnement, d’exécuter n’importe quel pipeline et de déployer du code dans AEM environnement ou qualité du code.

* ***Développeur***, vous êtes autorisé à générer un jeton d’accès personnel pour accéder à Git.

   >[!NOTE]
   > Un utilisateur peut être affecté à plusieurs rôles. Par exemple, l’attribution des rôles Propriétaire de l’entreprise et Responsable de déploiement à un utilisateur leur donne la combinaison ou la somme de ces autorisations.


Le tableau suivant résume les rôles et les autorisations associées dans Cloud Manager.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajouter le programme<br>Modifier le programme | Ajout d’un nouveau programme.<br>Modification d’un programme - Ajout ou suppression de solutions ou de modules complémentaires | x |  |  |  |
| Créer un environnement | Créez des environnements Prod+Stage, Dev, etc. | x | x |  |  |
| Mettre à jour l’environnement | Mettre à jour Prod+Stage, Dev, Environnements. | x | x |  |  |
| Suppression de l’environnement de développement | Suppression d’environnements de développement. | x | x |  |  |
| Configuration du pipeline | Configuration ou modification du pipeline. |  | x |  |  |
| Exécution du pipeline | Démarrez le pipeline. | x | x |  |  |
| Exécution du pipeline | Rejeter/Approuver des échecs importants de trois niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Suppression de pipeline | Permet la suppression d’un pipeline. |  | x |  |  |
| Annuler l’exécution | Annuler l’exécution en cours. |  | x |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git. |  | x |  | x |

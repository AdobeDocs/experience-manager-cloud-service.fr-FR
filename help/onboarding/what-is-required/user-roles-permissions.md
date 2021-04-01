---
title: Rôles de Cloud Manager
description: Cette page décrit les rôles utilisateur et les autorisations. Suivez cette page pour savoir comment ajouter des utilisateurs et les affecter à des rôles Cloud Manager.
translation-type: tm+mt
source-git-commit: 7b5973aef0d3296a54bcf1e57bda616cdd618346
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 19%

---


# Rôles de Cloud Manager {#user-roles-permissions}

## Rôles utilisateur {#user-roles}

De nombreuses fonctionnalités de Cloud Manager nécessitent des autorisations spécifiques pour fonctionner et limitent les actions que vous effectuez dans l’interface utilisateur en fonction des rôles et autorisations attribués. Dans certains cas, si vous n&#39;êtes pas autorisé à effectuer une action, le contrôle d&#39;interface est présent, mais désactivé.

Si vous souhaitez exécuter une action, mais que vous ne pouvez pas, cochez la section suivante, [Rôles utilisateur et autorisations](#permissions). Selon votre objectif, vous pouvez contacter l&#39;administrateur système et demander le rôle dont vous avez besoin.

Cloud Manager définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Responsable de programme
* Développeur

>[!NOTE]
>Dans Admin Console, le développeur n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

## Affichage de vos rôles {#view-roles}

Pour vue de vos rôles dans Cloud Manager, connectez-vous à l’interface utilisateur de Cloud Manager, sélectionnez l’icône de votre profil dans le coin supérieur droit et sélectionnez **Rôles utilisateur**, comme illustré dans la figure ci-dessous.

>[!NOTE]
>Voir [Accédez à Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md) pour en savoir plus sur la connexion à Cloud Manager.

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### Profil du produit d&#39;intégration {#integration-product-profile}

Outre ce qui précède, Cloud Manager crée automatiquement un profil de produits nommé &quot;Intégrations - Cloud Service&quot;. Ce profil de produits est utilisé pour les intégrations entre Adobe Experience Manager et d&#39;autres produits d&#39;Adobe. Ce profil de produit **ne doit pas** être supprimé. Si vous supprimez accidentellement ce profil, il doit être recréé manuellement. Le nom d&#39;affichage de ce profil **doit** être `CM_CS_DEFAULT`.


## Rôles utilisateur et autorisations {#permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et est autorisé à le transmettre au référentiel Git. Un propriétaire d’entreprise dispose également de différentes autorisations lui permettant d’ajouter et de modifier des programmes, d’ajouter des environnements et d’approuver des déploiements.

Chacun des rôles est associé à des autorisations spécifiques. Par exemple, si vous êtes dans le rôle d’un :

* ***Propriétaire*** d&#39;entreprise, vous avez l&#39;autorisation d&#39;Ajouter un nouveau programme ou de modifier un programme, d&#39;ajouter ou de mettre à jour un environnement, d&#39;ajouter/modifier/supprimer le pipeline et d&#39;exécuter un pipeline, et de déployer le code pour AEM qualité d&#39;environnement ou de code.

* ***Deployment Manager*** vous permet d’ajouter ou de mettre à jour un environnement, d’exécuter tout pipeline et de déployer le code dans AEM environnement ou qualité du code.

* ***Développeur***, vous avez l&#39;autorisation de générer un Jeton d&#39;accès personnel pour accéder à Git.

   >[!NOTE]
   > Un utilisateur peut être affecté à plusieurs rôles. Par exemple, l’attribution des rôles Business Owner et Deployment Manager à un utilisateur leur donne la combinaison ou la somme de ces autorisations.


Le tableau suivant récapitule les rôles et les autorisations associées dans Cloud Manager.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Programme d’Ajoute<br>Modifier le Programme | Ajoutez un nouveau Programme.<br>Modifier un programme : Ajouter ou supprimer des solutions ou des modules complémentaires | x |  |  |  |
| Créer un Environnement | Créer des Environnements Prod+Stage, Dev. | x | x |  |  |
| Mettre à jour l’environnement | Mettre à jour Prod+Stage, Dev, Environnements. | x | x |  |  |
| Supprimer l&#39;Environnement de développement | Supprimer les Environnements de développement. | x | x |  |  |
| Configuration du tuyau | Configuration ou modification du tuyau. |  | x |  |  |
| Exécution du pipeline | Début du pipeline. | x | x |  |  |
| Exécution du pipeline | Rejeter/Approuver les échecs importants à trois niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Suppression de pipeline | Permet de supprimer un tuyau. |  | x |  |  |
| Annuler l’exécution | Annuler l&#39;exécution en cours. |  | x |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git. |  | x |  | x |


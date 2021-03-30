---
title: 'Ajouter des utilisateurs et affecter des rôles Cloud Manager '
description: Suivez cette page pour savoir comment ajouter des utilisateurs et les affecter à des rôles Cloud Manager
translation-type: tm+mt
source-git-commit: 6e8cf08ec3f85437a8472a45895f3818e473e98c
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 33%

---


# Ajouter des utilisateurs et affecter des rôles à Cloud Manager {#add-users-assign}

L&#39;Adobe va créer un **identifiant d&#39;organisation** pour votre société dans le système IMS (Adobe Identity Management System), où tous vos utilisateurs et leurs autorisations peuvent être gérés. Chaque utilisateur, qui doit être membre de cette organisation et qui aura accès à l&#39;un des services [!UICONTROL Experience Cloud], devra disposer de son propre **Adobe ID**.

## Présentation des rôles utilisateur {#user-roles}

La plupart des fonctionnalités de Cloud Manager nécessitent des autorisations spécifiques.

Cloud Manager définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Responsable de programme
* Développeur

>[!NOTE]
>Dans Admin Console, le développeur n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

Le tableau suivant résume les rôles :

| Rôles de [!UICONTROL Cloud Manager] | Description |
|--- |--- |
| Propriétaire de l’entreprise | Est responsable de la définition des ICP, approuve les déploiements en production et contourne les échecs de trois niveaux. |
| Responsable de programme | Utilise [!UICONTROL Cloud Manager] pour configurer les équipes et passer en revue les statuts et les IPC. Peut approuver des échecs importants de 3 niveaux. |
| Responsable de déploiement | Gère les opérations de déploiement. Utilise [!UICONTROL Cloud Manager] pour exécuter les déploiements dans les environnements intermédiaires/de production. Peut modifier les pipelines CI/CD. Peut approuver des échecs importants de 3 niveaux. Peut accéder au référentiel Git. |
| Développeur | Développe et teste du code d’application personnalisé. Utilise principalement [!UICONTROL Cloud Manager] pour consulter les statuts. Peut accéder au référentiel Git pour la validation du code. |
| Auteur de contenu | N’interagit généralement pas avec [!UICONTROL Cloud Manager]. Peut utiliser le commutateur de programmes de [!UICONTROL Cloud Manager] (depuis [!UICONTROL Experience Cloud]) pour accéder à AEM. |

### Profil du produit d&#39;intégration {#integration-product-profile}

Outre ce qui précède, Cloud Manager crée automatiquement un profil de produits nommé &quot;Intégrations - Cloud Service&quot;. Ce profil de produits est utilisé pour les intégrations entre Adobe Experience Manager et d&#39;autres produits d&#39;Adobe. Ce profil de produit **ne doit pas** être supprimé. Si vous supprimez accidentellement ce profil, il doit être recréé manuellement. Le nom d&#39;affichage de ce profil **doit** être `CM_CS_DEFAULT`.


## Autorisations associées aux définitions de rôle {#permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le **référentiel Git**. Un propriétaire d’entreprise dispose d’autorisations différentes qui lui permettent de définir des indicateurs de performance clés et d’approuver les déploiements.

Chacun des rôles possède des autorisations spécifiques associées à chaque rôle. Le tableau suivant récapitule les rôles, liste les fonctions disponibles et les rôles qui peuvent exécuter la fonction.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajout d’un programme | Ajoutez un nouveau Programme. | x |  |  |  |
| Créer un Environnement | Créer des Environnements Prod+Stage, Dev. | x | x |  |  |
| Mettre à jour l’environnement | Mettre à jour Prod+Stage, Dev, Environnements. | x | x |  |  |
| Supprimer l’environnement | Supprimer les Environnements non-prod, Dev. | x | x |  |  |
| Configuration du tuyau | Configuration ou modification du tuyau. |  | x |  |  |
| Exécution du pipeline | Début du pipeline. | x | x |  |  |
| Exécution du pipeline | Rejeter/Approuver les échecs importants à trois niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Suppression de pipeline | Permet de supprimer un tuyau. |  | x |  |  |
| Annuler l’exécution | Annuler l&#39;exécution en cours. |  | x |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git. |  | x |  | x |

## Ajouter des utilisateurs {#add-users}

>[!NOTE]
>Pour ajouter un utilisateur, vous devez être administrateur système.

1. Si vous êtes administrateur système, accédez au [Admin Console](https://adminconsole.adobe.com). Vous pouvez également accéder à Cloud Manager où vous verrez le bouton **Gérer l’accès**, comme décrit ci-dessous.

1. Cliquez sur le bouton **Gérer l’accès**, situé en haut à droite du landing page Cloud Manager, pour ouvrir le Admin Console dans un nouvel onglet.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

   À partir du **Admin Console**, vous pouvez ajouter des utilisateurs à Cloud Manager et les affecter à des rôles, appelés Profils de produits dans le Admin Console.

1. Sélectionnez **Adobe Experience Manager en tant que Cloud Service** dans la carte **Produits et services**, comme indiqué ci-dessous.

   ![](/help/onboarding/what-is-required/assets/admin-console-1.png)

1. Sélectionnez l&#39;onglet **Utilisateurs** dans la barre d&#39;actions, puis sélectionnez **Ajouter l&#39;utilisateur**.

   ![](/help/onboarding/what-is-required/assets/admin-console-2.png)

1. Sélectionnez l’utilisateur et affectez à l’utilisateur les rôles ou Profils de produits Cloud Manager appropriés, comme indiqué ci-dessous.

   ![](/help/onboarding/what-is-required/assets/admin-console-3.png)

   >[!NOTE]
   >Reportez-vous aux sections précédentes, [Rôles utilisateur et autorisations](#user-roles) et [Permissions associées aux définitions de rôles](#permissions) pour vous assurer que les bons utilisateurs se voient attribuer le ou les rôles appropriés dans le **Admin Console**.

   Vous avez maintenant ajouté des utilisateurs à Adobe Experience Manager en tant que contexte de produit Cloud Service et vous avez configuré les rôles ou Profils de produits appropriés.

   Par exemple, si vous êtes dans le rôle d’un :

   * ***Propriétaire*** d&#39;entreprise, vous avez l&#39;autorisation d&#39;Ajouter un nouveau programme ou de modifier un programme, d&#39;ajouter ou de mettre à jour un environnement, d&#39;ajouter/modifier/supprimer le pipeline et d&#39;exécuter un pipeline, et de déployer le code pour AEM qualité d&#39;environnement ou de code.

   * ***Deployment Manager*** vous permet d’ajouter ou de mettre à jour un environnement, d’exécuter tout pipeline et de déployer le code dans AEM environnement ou qualité du code.

   * ***Développeur***, vous avez l&#39;autorisation de générer un Jeton d&#39;accès personnel pour accéder à Git.

      >[!NOTE]
      > Un utilisateur peut être affecté à plusieurs rôles. Par exemple, l’attribution des rôles Business Owner et Deployment Manager à un utilisateur leur donne la combinaison ou la somme de ces autorisations.

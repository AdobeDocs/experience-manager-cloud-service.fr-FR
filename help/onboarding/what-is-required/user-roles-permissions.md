---
title: Rôles utilisateur et autorisations
description: Cette page décrit les rôles utilisateur et les autorisations. Suivez cette page pour savoir comment ajouter des utilisateurs et les affecter à des rôles Cloud Manager.
translation-type: tm+mt
source-git-commit: 98c7105aed1b9092a72005cf2cfab4bcf227601f
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 44%

---


# Rôles utilisateur et autorisations {#user-roles-permissions}

L&#39;Adobe va créer un **identifiant d&#39;organisation** pour votre société dans le système IMS (Adobe Identity Management System), où tous vos utilisateurs et leurs autorisations peuvent être gérés. Chaque utilisateur, qui doit être membre de cette organisation et qui aura accès à l&#39;un des services [!UICONTROL Experience Cloud], devra disposer de son propre **Adobe ID**.

## Rôles utilisateur {#user-roles}

La plupart des fonctionnalités de Cloud Manager nécessitent des autorisations spécifiques.

De nombreuses fonctionnalités de Cloud Manager nécessitent des autorisations spécifiques pour fonctionner et limitent les actions que vous effectuez dans l’interface utilisateur en fonction des rôles et autorisations attribués. Dans certains cas, si vous n&#39;êtes pas autorisé à effectuer une action, le contrôle d&#39;interface est présent, mais désactivé.

Si vous souhaitez exécuter une action, mais ne pouvez pas l&#39;effectuer, vérifiez les [autorisations associées aux définitions de rôles](#permissions). Selon votre objectif, vous pouvez contacter l&#39;administrateur système et demander le rôle dont vous avez besoin.

Cloud Manager définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Responsable de programme
* Développeur

>[!NOTE]
>Dans Admin Console, le développeur n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

## Définitions de rôle {#role-definitions}

Le tableau suivant résume les rôles :

| Rôles de [!UICONTROL Cloud Manager] | Description |
|--- |--- |
| Propriétaire de l’entreprise | Est responsable de la définition des ICP, approuve les déploiements en production et contourne les échecs de trois niveaux. |
| Responsable de programme | Utilise [!UICONTROL Cloud Manager] pour configurer les équipes et passer en revue les statuts et les IPC. Peut approuver des échecs importants de 3 niveaux. |
| Responsable de déploiement | Gère les opérations de déploiement. Utilise [!UICONTROL Cloud Manager] pour exécuter les déploiements dans les environnements intermédiaires/de production. Peut modifier les pipelines CI/CD. Peut approuver des échecs importants de 3 niveaux. Peut accéder au référentiel Git. |
| Développeur | Développe et teste du code d’application personnalisé. Utilise principalement [!UICONTROL Cloud Manager] pour consulter les statuts. Peut accéder au référentiel Git pour la validation du code. |
| Auteur de contenu | N’interagit généralement pas avec [!UICONTROL Cloud Manager]. Peut utiliser le commutateur de programmes de [!UICONTROL Cloud Manager] (depuis [!UICONTROL Experience Cloud]) pour accéder à AEM. |

### Affichage de vos rôles {#view-roles}

Pour vue votre rôle dans Cloud Manager, connectez-vous à l’interface utilisateur de Cloud Manager, sélectionnez l’icône de votre profil dans le coin supérieur droit et sélectionnez **Rôles utilisateur**, comme illustré dans la figure ci-dessous.

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

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
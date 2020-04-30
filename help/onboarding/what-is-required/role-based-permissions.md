---
title: Autorisations basées sur les rôles
description: Autorisations basées sur les rôles
translation-type: tm+mt
source-git-commit: 3c56d94f9922cb65b91912dd96eb8aa60efc2b53

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le **référentiel Git**. Un propriétaire d’entreprise dispose d’autorisations différentes qui lui permettent de définir des indicateurs de performance clés et d’approuver les déploiements.

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles possède des autorisations, des tâches préconfigurées ou des autorisations spécifiques, associées à chaque rôle. Ce tableau récapitule les fonctions disponibles et les rôles associés à chaque fonction.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajout d’un programme | Ajouter un nouveau Programme. | x |  |  |  |
| Créer un Environnement | Créez des Environnements Prod+Stage, Dev, Playground. | x | x |  |  |
| Mettre à jour l’environnement | Mettre à jour les Environnements Prod+Stage, Dev, Playground. | x | x |  |  |
| Supprimer l’environnement | Supprimer les Environnements non-prod, Dev, Playground. | x | x |  |  |
| Supprimer l’environnement | Supprimer l&#39;Environnement Prod+Stage. |  |  |  |  |
| Configuration du Programme | Configurez le Programme (y compris les indicateurs clés de performance). | x |  |  |  |
| Configuration du Programme | Obtenez L’Accès De Validation. |  | x |  | x |
| Configuration du tuyau | Configuration ou modification du tuyau. |  | x |  |  |
| Exécution du pipeline | Début du pipeline. | x | x |  |  |
| Exécution du pipeline | Rejeter/Approuver les échecs importants à trois niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Exécution du pipeline | Reprendre le pipeline de production. |  |  |  |  |
| Suppression du tuyau | Permet de supprimer un tuyau. |  | x |  |  |
| Annuler l’exécution | Annuler l&#39;exécution en cours. |  | x |  |  |
| Gérer l’environnement | Ajouter segment Publier-Répartiteur de l’écran Gérer l’Environnement. | x | x |  |  |  |
| Mise à jour Push | Début Push Update Pipeline. |  |  |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git. |  | x |  | x |


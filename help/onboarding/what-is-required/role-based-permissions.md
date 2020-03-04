---
title: Autorisations basées sur les rôles
description: Autorisations basées sur les rôles
translation-type: tm+mt
source-git-commit: a1b4feced2dd8becc74383fe8a3b835bde7159d2

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le **référentiel Git**. Un propriétaire d’entreprise dispose d’autorisations différentes qui lui permettent de définir des indicateurs de performance clés et d’approuver les déploiements.

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles dispose d’autorisations spécifiques, de tâches préconfigurées, ou de permissions, inhérentes à chaque rôle. Ce tableau récapitule les fonctions disponibles et les rôles associés à chaque fonction.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajouter le programme | Ajouter un nouveau programme. | x |  |  |  |
| Créer un environnement | Créez Des Environnements Prod+Stage, Dev, Playground. | x | x |  |  |
| Mettre à jour l’environnement | Mettez à jour les environnements Prod+Stage, Dev, Playground. | x | x |  |  |
| Supprimer l’environnement | Supprimez Les Environnements Non-Prod, Dev, Playground. | x | x |  |  |
| Supprimer l’environnement | Supprimer l’environnement Prod+Stage. |  |  |  |  |
| Configuration du programme | Configuration du programme (y compris les IPC). | x |  |  |  |
| Configuration du programme | Obtenez L’Accès De Confirmation. |  | x |  | x |
| Configuration du pipeline | Configuration ou modification du pipeline. |  | x |  |  |
| Exécution du pipeline | Démarrez le pipeline. | x | x |  |  |
| Exécution du pipeline | Rejeter/Approuver les échecs importants à trois niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Exécution du pipeline | Reprendre le pipeline de production. |  |  |  |  |
| Gérer l’environnement | Ajoutez le segment Publier-Répartiteur à partir de l’écran Gérer l’environnement. | x | x |  |  |  |
| Mise à jour Push | Démarrez Push Update Pipeline. |  |  |  |  |
| Générer un jeton d’accès personnel | Accéder à Git. |  | x |  | x |


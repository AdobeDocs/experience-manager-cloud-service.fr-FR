---
title: Autorisations basées sur les rôles
description: Autorisations basées sur les rôles
translation-type: tm+mt
source-git-commit: 6cae9b2b719dab687f601a0596d37f99afded9ab

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le **référentiel Git**. Un propriétaire d’entreprise dispose d’autorisations différentes qui lui permettent de définir des indicateurs de performance clés et d’approuver les déploiements.

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles dispose d’autorisations spécifiques, de tâches préconfigurées, ou de permissions, inhérentes à chaque rôle. Ce tableau récapitule les fonctions disponibles et les rôles associés à chaque fonction.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Créer un client | Créer un client. |  |  |  |  |
| Mettre à jour le client | Mettre à jour le client. |  |  |  |  |
| Ajouter le programme | Ajouter un nouveau programme. | x |  |  |  |
| Créer un environnement | Créez Des Environnements Prod+Stage, Dev, Playground. | x | x |  |  |
| Configuration des variables d’environnement | Configuration des variables d’environnement et des secrets. |  | x |  | x |
| Ajouter ou supprimer un nom de domaine personnalisé, télécharger ou mettre à jour le certificat SSL | Ajouter/Supprimer un nom de domaine personnalisé, Télécharger/Mettre à jour le certificat SSL. | x | x |  |  |
| Mettre à jour l’environnement | Mettez à jour les environnements Prod+Stage, Dev, Playground. | x | x |  |  |
| Supprimer l’environnement | Supprimez Les Environnements Non-Prod, Dev, Playground. | x | x |  |  |
| Supprimer l’environnement | Supprimer l’environnement Prod+Stage. |  |  |  |  |
| Environnement d’hibernation | Hibernate Non-prod, Dev, Environnements Playground. | x | x |  |  |
| Configuration du programme | Configuration du programme (y compris les IPC). | x |  |  |  |
| Configuration du programme | Configuration des stratégies de mise à l’échelle (Général : configuration du nombre maximal de niveaux et de l’échelle horizontale à la demande : souscription). | x |  |  |  |
| Configuration du programme | Obtenez L’Accès De Validation. |  | x |  | x |
| Configuration du pipeline | Configuration ou modification du pipeline. |  | x |  |  |
| Exécution du pipeline | Démarrez le pipeline. | x | x |  |  |
| Exécution du pipeline | Rejeter/Approuver les échecs importants à trois niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Exécution du pipeline | Reprendre le pipeline de production. |  |  |  |  |
| Inscription (ou désinscription) à l&#39;approvisionnement | Ouverture à la demande Approvisionnement horizontal à partir de l’écran Configuration du programme. Configurez le nombre maximal de segments P-D &quot;autorisés&quot; pouvant être mis à l&#39;échelle horizontalement dans les environnements PROD et non PROD. | x |  |  |  |
| Gérer l’environnement | Ajoutez le segment Publier-Répartiteur à partir de l’écran Gérer l’environnement. | x | x |  |  |  |
| Mise à jour du produit | La carte de mise à jour AEM est visible et conduit l’utilisateur à l’Assistant de mise à jour. | x | x | x | x |
| Mise à jour du produit | L&#39;Assistant Mise à jour de produit peut être activé. | x | x |  |  |
| Mise à jour Push | Démarrez Push Update Pipeline. |  |  |  |  |
| Générer un jeton d’accès personnel | Générer un jeton d’accès personnel. |  | x |  | x |


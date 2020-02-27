---
title: Autorisations basées sur les rôles
description: Autorisations basées sur les rôles
translation-type: tm+mt
source-git-commit: e59fe55c255d5239a561a9fb878faa81d17b4b48

---


# Autorisations basées sur les rôles {#role-based-permissions}

[!UICONTROL Cloud Manager] dispose de rôles préconfigurés avec les autorisations appropriées. Par exemple, un développeur développe du code et a l’autorisation de placer le code dans le **référentiel Git**. Un propriétaire d’entreprise dispose d’autorisations différentes qui lui permettent de définir des indicateurs de performance clés et d’approuver les déploiements.

## Autorisations d’utilisateur {#user-permissions}

Chacun des rôles dispose d’autorisations spécifiques, de tâches préconfigurées, ou de permissions, inhérentes à chaque rôle. Ce tableau récapitule les fonctions disponibles et les rôles associés à chaque fonction.

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajouter le programme | Ajouter un nouveau programme. | x | x | x | x |
| Lecture de l’application | Lisez les IPC du programme. | x | x | x | x |
| Écriture de l’application | Configuration ou modification du programme. | x |  |  |  |  |
| Lecture de l’environnement | Voir les détails de l’environnement. | x | x | x | x |
| Création de l’exécution | Démarrage du pipeline. | x | x | x |  |
| Lecture de l’exécution | Voir le statut de l’exécution. | x | x | x | x |
| Relancer l’exécution | Relance l’exécution lorsqu’elle est en pause. | x | x | x |  | x |
| Approbation de l’exécution du déploiement en production | Fournit l’approbation de GoLive. | x | x | x |  |  |
| Planning d’exécution du déploiement en production | Planning du déploiement en production. | x | x | x |
| Annuler l’exécution | Annuler l’exécution actuelle. | x | x | x |  |
| Contourner les échecs du point de contrôle de qualité | Approuver des échecs importants du point de contrôle qualité. | x | x | x |  |
| Création d’un pipeline | Configurer/modifier un pipeline. |  | x |  |  |
| Lecture d’un pipeline | Voir les détails du pipeline. | x | x | x | x |
| Écriture d’un pipeline | Configurer/modifier un pipeline. |  | x |  |  |
| Approbation de la modification d’un pipeline | Permet la modification de l’option Propriétaire de l’entreprise. |  | x |  |  |
| Lecture de l’étape | Voir les résultats des mesures de qualité de l’étape. | x | x | x | x |

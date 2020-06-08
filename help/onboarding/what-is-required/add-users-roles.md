---
title: Ajouter les utilisateurs et les rôles - Ce qui est requis
description: Ajouter les utilisateurs et les rôles - Ce qui est requis
translation-type: tm+mt
source-git-commit: 936e42f273b75f0ea7776c51f57af44ec9e6d96f
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 93%

---


# Ajout d’utilisateurs et de rôles {#add-users-roles}


La plupart des fonctionnalités de [!UICONTROL Cloud Manager] nécessitent des autorisations spécifiques. Par exemple, seuls certains utilisateurs sont autorisés à définir les indicateurs de performance clés (IPC) d’un programme. Ces autorisations sont regroupées de manière logique en rôles.

[!UICONTROL Cloud Manager] définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

>[!CAUTION]
>
>Pour utiliser [!UICONTROL Cloud Manager], vous devez disposer d’un Adobe ID et du contexte du produit Adobe Managed Services.

## Définitions de rôle {#role-definitions}

>[!NOTE]
>
>Dans Admin Console, le développeur n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

Le tableau suivant résume les rôles :

| Rôles de [!UICONTROL Cloud Manager] | Description |
|--- |--- |
| Propriétaire de l’entreprise | Est responsable de la définition des ICP, approuve les déploiements en production et contourne les échecs de trois niveaux. |
| Responsable de programme | Utilise [!UICONTROL Cloud Manager] pour configurer les équipes et passer en revue les statuts et les IPC. Peut approuver des échecs importants de 3 niveaux. |
| Responsable de déploiement | Gère les opérations de déploiement. Utilise [!UICONTROL Cloud Manager] pour exécuter les déploiements dans les environnements intermédiaires/de production. Peut modifier les pipelines CI/CD. Peut approuver des échecs importants de 3 niveaux. Peut accéder au référentiel Git. |
| Développeur | Développe et teste du code d’application personnalisé. Utilise principalement [!UICONTROL Cloud Manager] pour consulter les statuts. Peut accéder au référentiel Git pour la validation du code. |
| Auteur de contenu | N’interagit généralement pas avec [!UICONTROL Cloud Manager]. Peut utiliser le commutateur de programmes de [!UICONTROL Cloud Manager] (depuis [!UICONTROL Experience Cloud]) pour accéder à AEM. |
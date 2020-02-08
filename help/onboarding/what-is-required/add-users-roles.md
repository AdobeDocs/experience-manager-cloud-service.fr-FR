---
title: 'Ajout d’utilisateurs et de rôles : éléments requis'
description: 'Ajout d’utilisateurs et de rôles : éléments requis'
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247

---


# Ajout d’utilisateurs et de rôles : éléments requis {#add-users-roles}


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

## Utilisation d’Admin Console pour créer un profil {#using-admin-console-to-create-a-profile}

Les rôles sont gérés pour [!UICONTROL Cloud Manager] à partir d’Adobe Admin Console. Des rôles spécifiques sont fournis en ajoutant un utilisateur à un profil de produit [!UICONTROL Cloud Manager] dans Admin Console.

Vous pouvez affecter des rôles spécifiques en ajoutant un utilisateur à un **Profil de produit** [!UICONTROL Cloud Manager] dans Adobe Admin Console, un emplacement central pour gérer les droits Adobe dans l’ensemble de l’organisation. Pour en savoir plus sur Adobe Admin Console, consultez la documentation d’[Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>Pour accéder à Admin Console et configurer votre équipe (utilisateurs et rôles), ouvrez un navigateur et rendez-vous sur [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Afin de fournir aux utilisateurs de [!UICONTROL Cloud Manager] les autorisations appropriées basées sur les rôles, un administrateur de l’**organisation** du client doit créer de nouveaux profils de produit sous le contexte du produit [!UICONTROL AEM Managed Services].

Pour accorder les autorisations appropriées basées sur les rôles aux utilisateurs de [!UICONTROL Cloud Manager], en tant qu’administrateur, vous devez créer quatre profils de produit sous le contexte du produit [!UICONTROL AEM Managed Services] correspondant à chacun des quatre rôles [!UICONTROL Cloud Manager] :

* Propriétaire de l’entreprise
* Responsable de déploiement
* Développeur
* Responsable de programme

Vous pouvez créer, ou ajouter, des utilisateurs/groupes à ces profils de produit avec [Admin Console](https://adminconsole.adobe.com/) pour [!UICONTROL Cloud Manager], comme illustré dans la figure ci-dessous :

1. Connectez-vous à Admin Console et cliquez sur **Nouveau profil** pour ajouter un nouveau profil.

1. Renseignez les champs afin de configurer un nouveau rôle pour [!UICONTROL Cloud Manager].

   Saisissez les **Nom de profil** et **Nom d’affichage** pour créer un profil. Vous pouvez en outre sélectionner un **groupe d’autorisations** pour le profil.

   Cliquez sur **Terminé** pour terminer l’étape de création du profil.

   >[!NOTE]
   >
   >Lors de la création de ces profils de produit, le **Nom d’affichage** doit correspondre à la valeur technique définie par [!UICONTROL Cloud Manager] (voir le tableau ci-dessous). Le **Nom de profil** peut être n’importe quel nom, bien que pour éviter toute confusion, il est recommandé d’utiliser les valeurs de la colonne *Nom de profil recommandé* ci-dessous. Pour ce faire, lors de la création du profil du produit, désélectionnez **Identique au nom de profil** et spécifiez la valeur correspondante comme **Nom d’affichage**.

   | **Rôle** | **Nom d’affichage (obligatoire)** | **Nom de profil recommandé** |
   |---|---|---|
   | Propriétaire de l’entreprise | CM_ BUSINESS_ OWNER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] : rôle du propriétaire de l’entreprise |
   | Responsable de déploiement | CM_ DEPLOYMENT_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] : rôle de responsable de déploiement |
   | Développeur | CM_ DEVELOPER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] : rôle de développeur |
   | Responsable de programme | CM_ PROGRAM_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] : rôle de responsable de programme |

1. Une fois le profil du produit créé, vous pouvez ajouter des utilisateurs (ou des groupes) aux profils de produit.



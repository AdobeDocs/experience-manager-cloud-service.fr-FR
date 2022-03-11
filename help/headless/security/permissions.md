---
title: Considérations relatives aux autorisations pour le contenu sans interface
description: Découvrez les différentes considérations relatives aux autorisations et aux listes de contrôle d’accès pour une mise en oeuvre sans interface avec Adobe Experience Manager. Découvrez les différentes personnes et les niveaux d’autorisation potentiels nécessaires pour les environnements de création et de publication.
feature: Content Fragments,GraphQL API
exl-id: 3fbee755-2fa4-471b-83fc-3f4bf056267a
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Considérations relatives aux autorisations pour le contenu sans interface

Avec une mise en oeuvre sans interface, il existe plusieurs domaines de sécurité et d’autorisations à résoudre. Les autorisations et les personnages peuvent être largement considérés en fonction de l’environnement AEM **Auteur** ou **Publier**. Chaque environnement contient des personnages différents et a des besoins différents.

## Considérations sur le service de création

Le service Auteur est l’emplacement où les utilisateurs internes créent, gèrent et publient du contenu. Les autorisations sont axées sur les différentes personnes qui gèrent le contenu.

### Gestion des autorisations au niveau du groupe

Il est recommandé de définir les autorisations sur les groupes dans AEM. Également appelés groupes locaux, ces groupes peuvent être gérés dans l’environnement de création AEM.

Le moyen le plus simple de gérer l’appartenance à un groupe consiste à utiliser les groupes Adobe Identity Management System (IMS) et à attribuer [Groupes IMS vers les groupes d’AEM locaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=en#managing-permissions-in-aem).

![Flux d’autorisation Admin Console](assets/admin-console-aem-group-permissions.png)

À un niveau général, le processus est le suivant :

1. Ajoutez des utilisateurs IMS à un groupe d’utilisateurs IMS nouveau ou existant à l’aide de la fonction [Admin Console](https://adminconsole.adobe.com/)
1. Les groupes IMS sont synchronisés avec AEM lorsque les utilisateurs se connectent.
1. Affectez des groupes IMS à des groupes AEM.
1. Définissez des autorisations sur les groupes AEM.
1. Lorsque les utilisateurs se connectent à AEM et sont authentifiés via IMS, ils héritent des autorisations du groupe AEM.

>[!TIP]
>
> Une présentation vidéo détaillée de la gestion des utilisateurs et groupes IMS et d’AEM est disponible [here](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html).

Pour gérer **groups** dans AEM, accédez à **Outils** > **Sécurité** > **Groupes**.

Pour gérer les autorisations des groupes dans AEM, accédez à **Outils** > **Sécurité** > **Autorisations**.

### Utilisateurs de DAM

&quot;DAM&quot;, dans ce contexte, signifie gestion des actifs numériques. Le **Utilisateurs de DAM** est un groupe prêt à l’emploi dans AEM qui peut être utilisé pour les utilisateurs &quot;quotidiens&quot; qui gèrent les ressources numériques et les fragments de contenu. Ce groupe fournit des autorisations pour **view**, **add**, **update**, **delete**, et **publier** Fragments de contenu et tous les autres fichiers dans AEM Assets.

Si vous utilisez IMS pour l’appartenance à un groupe, ajoutez les groupes IMS appropriés en tant que membres de **Utilisateurs de DAM** groupe. Les membres du groupe IMS héritent des autorisations du groupe Utilisateurs de la gestion des actifs numériques lors de leur connexion à l’environnement AEM.

#### Personnalisation du groupe d’utilisateurs DAM

Il est préférable de ne pas modifier directement les autorisations d’un groupe prêt à l’emploi. Vous pouvez également créer votre ou vos propres groupes, en suivant le modèle de l’événement **Utilisateurs de DAM** autorisations de groupe et restreindre davantage l’accès à différents **dossiers** dans AEM Assets.

Pour obtenir des autorisations plus granulaires, utilisez la variable **Autorisations** dans AEM et mettez à jour le chemin à partir de `/content/dam` à un chemin plus spécifique, c’est-à-dire `/content/dam/mycontentfragments`.

Il peut être souhaitable de donner à ce groupe d’utilisateurs les autorisations de créer et de modifier des fragments de contenu, mais pas de les supprimer. Pour vérifier et attribuer des autorisations à modifier, mais pas à supprimer, voir [Fragments de contenu - considérations sur la suppression](/help/assets/content-fragments/content-fragments-delete.md).

### Éditeurs de modèle

La possibilité de modifier **Modèles de fragment de contenu** doit être laissé aux administrateurs ou à un **petit groupe** Nombre d’utilisateurs disposant d’autorisations élevées. La modification du modèle de fragment de contenu a de nombreux effets en aval.

>[!CAUTION]
>
>Les modifications apportées aux modèles de fragment de contenu modifient l’API GraphQL sous-jacente sur laquelle les applications sans interface se fient.

Si vous souhaitez créer un groupe qui gère les modèles de fragment de contenu sans accès administrateur complet, vous pouvez créer un groupe avec les entrées de contrôle d’accès suivantes :

| Chemin  | Autorisation | Autorisations |
|-----| -------------| ---------|
| `/conf` | **autoriser** | `jcr:read` |
| `/conf/<config-name>/settings/dam/cfm` | **autoriser** | `rep:write`, `crx:replicate` |

## Autorisations du service de publication

Le service de publication est considéré comme l’environnement &quot;en ligne&quot; et est généralement ce avec quoi les clients de l’API GraphQL interagissent. Le contenu, après avoir été modifié et approuvé sur le service Auteur, est publié sur le service Publication. L’application sans interface utilise ensuite le contenu approuvé du service de publication via les API GraphQL.

Par défaut, le contenu exposé via les points d’entrée GraphQL du service de publication AEM est accessible à tous, y compris aux utilisateurs non authentifiés.

### Autorisations de contenu

Le contenu exposé via AEM API GraphQL peut être limité à l’aide de [Groupes d’utilisateurs fermés (CUG)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html) défini sur les dossiers de ressources, qui spécifient quels groupes d’utilisateurs AEM (et leurs membres) peuvent accéder au contenu des dossiers de ressources.

Les CUG de ressources fonctionnent comme suit :

* Tout d’abord, refuser l’accès au dossier et aux sous-dossiers
* Vous pouvez ensuite autoriser l’accès en lecture au dossier et aux sous-dossiers pour tous les groupes d’utilisateurs AEM répertoriés dans la liste des CUG.

Les groupes d’utilisateurs fermés peuvent être configurés sur des dossiers de ressources contenant du contenu exposé via les API GraphQL. L’accès aux dossiers de ressources sur AEM Publish doit être contrôlé par l’intermédiaire de groupes d’utilisateurs plutôt que directement par l’utilisateur. Créez (ou réutilisez) un groupe d’utilisateurs AEM qui accorde l’accès aux dossiers de ressources contenant du contenu exposé par les API GraphQL.

#### Sélection du schéma d’authentification{#publish-permissions-users}

Le [AEM SDK sans affichage](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) prend en charge deux types d’authentification :

* [Authentification basée sur les jetons](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) à l’aide des informations d’identification du service liées à un seul compte technique.
* Authentification de base à l’aide d’utilisateurs AEM.

### Accès à l’API GraphQL

requêtes HTTP fournissant le [informations d’authentification appropriées](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) aux points d’entrée de l’API GraphQL du service de publication AEM incluent du contenu que les informations d’identification sont autorisées à lire et du contenu accessible de manière anonyme. Les autres clients de l’API GraphQL ne peuvent pas lire le contenu dans les dossiers protégés par CUG.

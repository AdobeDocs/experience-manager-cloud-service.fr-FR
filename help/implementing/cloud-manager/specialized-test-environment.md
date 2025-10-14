---
title: Ajout d’un environnement de test spécialisé
description: Découvrez comment les environnements de test spécialisés dans Cloud Manager offrent un espace dédié pour valider les fonctionnalités dans des conditions de quasi-production, idéal pour les tests de contrainte et les contrôles avancés avant déploiement.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Private Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
exl-id: 815fb5c3-a171-4531-8727-b79183d85f06
source-git-commit: 498a58c89910f41e6b86c5429629ec9282028987
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 12%

---

# Ajout d’un environnement de test spécialisé{#add-special-test-enviro}

>[!NOTE]
>
>&#x200B;>La fonctionnalité décrite dans cet article n’est disponible que via le programme bêta privé. Pour vous inscrire à la version bêta privée, voir [Environnement de test spécialisé](/help/implementing/cloud-manager/release-notes/current.md#specialized-test-environment).

L’environnement de test spécialisé, ou DevXL, est un nouveau type d’environnement Cloud Manager que vous pouvez créer. Il est conçu pour prendre en charge des cas d’utilisation avancés tels que les tests d’acceptation utilisateur (UAT) et la validation des performances. Contrairement aux environnements de développement, de développement rapide ou d’évaluation traditionnels, les environnements DevXL fonctionnent en dehors du pipeline de déploiement de production. Ils vous offrent donc une plus grande flexibilité tout en maintenant une isolation stricte afin d’éviter toute interférence avec les workflows de production.

DevXL est conçu pour refléter la taille, l’évolutivité et les configurations d’un environnement d’évaluation standard. Cette approche garantit que les tests effectués dans DevXL peuvent fournir des informations réalistes sur la façon dont le code et le contenu se comportent dans des conditions de type production. L’environnement prend également en charge la copie directe de contenu depuis la production ou l’évaluation. Il conserve également la parité avec les environnements de développement en termes de workflows de déploiement, de contrôles d’accès et de configurations réseau.

## Fonctionnalités clés et configurations {#key-features}

| Catégorie | Comportement de DevXL |
| --- | --- |
| Objectif | Test d’expérience utilisateur et tests de performance. |
| Type de pipeline | Pas dans le pipeline de production. |
| Taille de l’environnement | Correspond à l’environnement d’évaluation. |
| Isolement | Complètement isolé des autres environnements. |
| Pipelines de code | Identique à l’environnement de développement (validation, création, déploiement). |
| Copier le contenu | Autorisé depuis un environnement de production, d’évaluation ou de test spécialisé. |
| Restauration du contenu | Identique à l’environnement de développement. |
| Journaux d’accès | Identique à l’environnement de développement. |
| Developer Console | Identique à l’environnement de développement. |
| `IP Allow List` | Identique à l’environnement de développement. |
| Mise en réseau | Identique à l’environnement de développement (services, nom de domaine, certificats SSL, réseau avancé). |

Voir aussi [Gérer les environnements](/help/implementing/cloud-manager/manage-environments.md)

## Ajout d’un environnement de test spécialisé {#add-specialized-testing-environment}

Pour ajouter ou modifier un environnement, un utilisateur doit disposer du rôle **Propriétaire de l’entreprise**.

**Pour ajouter un environnement de test spécialisé, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, cliquez sur le programme pour lequel vous souhaitez ajouter un environnement.

1. Utilisez l’une des méthodes suivantes :

   * Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sur la carte **Environnements**, cliquez sur **Ajouter un environnement**.
Si l’option **Ajouter un environnement** est grisée (désactivée), cela peut être dû à un manque d’autorisations ou à une dépendance aux ressources sous licence.

   ![Carte Environnements](assets/no-environments.png)

   * Sur le panneau de gauche, cliquez sur ![Icône de données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**, puis sur la page Environnements, près du coin supérieur droit, cliquez sur **Ajouter un environnement**.

     ![Onglet Environnements](assets/environments-tab.png)

1. Dans la boîte de dialogue **Ajouter un environnement**, procédez comme suit :

   * Cliquez sur **Environnement de test spécialisé**.
   * Fournissez un environnement **Nom**. Le nom de l’environnement ne peut pas être modifié une fois l’environnement créé.
   * (Facultatif) Fournissez une **Description** pour l’environnement.
   * Sélectionnez une région de Principal **&#x200B;**&#x200B;dans la liste déroulante. Une fois créée, la région principale de l’environnement DevXL (par exemple, *États-Unis (ouest des États-Unis)*) est verrouillée et ne peut pas être modifiée.

   ![Boîte de dialogue Ajouter un environnement avec le bouton radio Environnement de test spécialisé sélectionné](assets/specialized-test-environment.png)

1. Cliquez sur **Enregistrer**.

   La page **Aperçu** affiche désormais votre nouvel environnement dans la vignette **Environnements**. Vous pouvez désormais configurer des pipelines pour votre nouvel environnement.

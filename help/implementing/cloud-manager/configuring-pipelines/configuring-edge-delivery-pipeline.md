---
title: Ajout d’un pipeline Edge Delivery
description: Découvrez comment ajouter un pipeline Edge Delivery pour créer et déployer votre code dans les environnements de production.
index: true
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Utilisateur(Utilisatrice) Précoce" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: true
hidefromtoc: true
source-git-commit: 22289138be1fa63caa1beda83e98ffa75dfabc2a
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Ajout d’un pipeline Edge Delivery {#configure-edge-delivery-pipeline}

Découvrez comment configurer des pipelines de production pour créer et déployer votre code dans les environnements de production. Un pipeline de production déploie le code d’abord dans l’environnement intermédiaire. Lors de la validation, il déploie le même code dans l’environnement de production.

Un utilisateur doit disposer du rôle **[Responsable de déploiement](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer un pipeline Edge Delivery.

>[!NOTE]
>
>Les fonctionnalités décrites dans cet article ne sont disponibles que par le biais du programme des utilisateurs et utilisatrices précoces. Pour plus d’informations et pour vous inscrire en tant qu’utilisateur ou utilisatrice précoce, voir [Apporter votre propre Git](/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket).
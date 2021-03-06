---
title: Accès aux référentiels
description: Découvrez comment accéder à votre référentiel git et le gérer à l’aide de la gestion de compte git en libre-service à partir de Cloud Manager.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 4729574eb31e01077f0d2a35efcef6d134f6aa5c
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 8%

---

# Accès aux référentiels {#accessing-repos}

Découvrez comment accéder à votre référentiel git et le gérer à l’aide de la gestion de compte git en libre-service à partir de Cloud Manager.

## Utilisation de la gestion de compte du référentiel en libre-service {#self-service-repos}

Cloud Manager facilite la récupération des informations de votre référentiel à l’aide de la fonction **Accès aux informations sur le référentiel** est disponible en bonne place sur la carte pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à **Pipelines** de votre **Aperçu du programme** et recherchez les **Accès aux informations sur le référentiel** pour accéder à votre référentiel git et le gérer.

   ![Bouton Accéder aux informations de Repo sur la carte Environnements](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Cliquez sur le bouton **Afficher les informations sur le référentiel** pour ouvrir une boîte de dialogue afin d’afficher :

   * URL vers le référentiel git de Cloud Manager.
   * Nom d’utilisateur Git.
   * Le mot de passe Git, dont la valeur s’affiche lorsque la variable **Générer un mot de passe** est sélectionné.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

À l’aide de ces informations d’identification, l’utilisateur peut cloner une copie locale du référentiel et apporter des modifications à ce référentiel local. Une fois prêt, il peut valider toutes les modifications de code dans le référentiel de code distant dans Cloud Manager.

Le **Accès aux informations sur le référentiel** est également disponible sur la **Non-production** onglet de pipeline de **Pipelines** carte.

![Bouton Accéder aux informations de Repo dans l’onglet hors production](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>Le **Accès aux informations sur le référentiel** est visible par les utilisateurs disposant de **Développeur** ou **Responsable de déploiement** rôles.

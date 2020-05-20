---
title: Gestion des environnements - Cloud Service
description: Gestion des environnements - Cloud Service
translation-type: tm+mt
source-git-commit: 1f72e8c935dc6cfe1124afd9f1a0fe37a97ded34
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 68%

---


# Gestion des environnements {#manage-environments}

La section suivante décrit les types d’environnement qu’un utilisateur peut créer et comment cet utilisateur peut créer un environnement.

## Types d’environnement {#environment-types}

Un utilisateur disposant des autorisations requises peut créer les types d’environnement suivants (dans les limites de ce qui est disponible pour le client spécifique).

* **Environnement de production et de test** : les environnements de production et de test sont disponibles en duo et sont utilisés à des fins de test et de production.

* **Développement** : un environnement de développement peut être créé à des fins de développement et de test et sera associé uniquement aux pipelines qui ne sont pas en production.

   >[!NOTE]
   >Un environnement de développement créé automatiquement dans un programme Sandbox sera configuré pour inclure les solutions Sites et Assets.

   Le tableau suivant récapitule les types d’environnement et leurs attributs :

   | Nom | Niveau de création | Niveau de publication | L’utilisateur peut créer | L’utilisateur peut supprimer | Pipeline pouvant être associé à l’environnement |
   |--- |--- |--- |--- |---|---|
   | Production | Oui | Oui si Sites est inclus | Oui | Non | Pipeline de production |
   | Scène | Oui | Oui si Sites est inclus | Oui | Non | Pipeline de production |
   | Développement | Oui | Oui si Sites est inclus | Oui | Oui | Pipeline hors production |

   >[!NOTE]
   >La production et le test sont disponibles en duo et sont utilisés à des fins de test et de production. L’utilisateur ne pourra pas créer uniquement un environnement de production ou de test.

## Ajout d’un environnement {#adding-environments}


1. Cliquez sur **Ajouter Environnement** pour ajouter un environnement. Ce bouton sera accessible à partir de l&#39;écran **Environnements** .
   ![](assets/no-environment-2.png)


   L&#39;option Environnement **** Ajouter est également disponible sur la carte **Environnements** lorsqu&#39;il n&#39;y a aucun environnement dans le programme.

   ![](assets/no-environments.png)

   >[!NOTE]
   >L’option Environnement **** Ajoutersera désactivée en raison d’un manque d’autorisations ou de ce qui peut être contracté.

1. La boîte de dialogue **Ajouter un environnement** s’affiche. L’utilisateur doit ajouter des détails tels que le **type d’environnement**, **nom de l’environnement** et la **description de l’environnement** (selon l’objectif de l’utilisateur lors de la création de l’environnement dans les limites de ce qui est disponible pour le client spécifique).

   ![](assets/add-environment2.png)

   >[!NOTE]
   >Lors de la création d’un environnement, une ou plusieurs *intégrations* sont créées dans les E/S Adobe. Elles sont visibles par les utilisateurs clients qui ont accès à la console d’E/S Adobe et ne doivent pas être supprimées. Cette suppression est déconseillée dans la description de la console d’E/S Adobe.

   ![](assets/add-environment-image1.png)

1. Cliquez sur **Enregistrer** pour ajouter un environnement avec les critères renseignés. Désormais, l’écran *Aperçu* affiche la carte à partir de laquelle vous pouvez configurer votre pipeline.

   >[!NOTE]
   >Si vous n’avez pas encore configuré votre pipeline hors production, l’écran *Aperçu* affiche la carte d’où vous pouvez créer votre pipeline hors production.

## Mise à jour de l’environnement {#updating-dev-environment}

Les mises à jour des environnements Test et Production sont gérées automatiquement par Adobe.

Les mises à jour des environnements de développement sont gérées par les utilisateurs du programme. Lorsqu’un environnement n’exécute pas la dernière version d’AEM disponible pour le public, l’état de la carte Environnements sur l’écran d’accueil affiche **MISE À JOUR DISPONIBLE**.

![](assets/manage-environments2.png)


L’option **Mettre à jour** est disponible dans le menu déroulant de la carte **Environnements** .
Cette option est également disponible à partir du bouton **Gérer** si vous cliquez sur **Détails** dans la carte **Environnements** .

![](assets/update-environment2.png)

Si vous sélectionnez cette option dans le menu déroulant, un gestionnaire de déploiement pourra mettre à jour le pipeline associé à cet environnement vers la dernière version, puis exécuter le pipeline.

Si le pipeline a déjà été mis à jour, l’utilisateur est invité à exécuter le pipeline.

## Suppression d’un Environnement {#deleting-environment}

L’utilisateur disposant des autorisations requises peut supprimer un environnement de développement.

L’option **Supprimer** est disponible dans le menu déroulant de la carte **Environnements** .
Cette option est également disponible à partir du bouton **Gérer** si vous cliquez sur **Détails** dans la carte **Environnements** .

![](assets/deleting-environment1.png)

>[!NOTE]
Cette fonction n’est pas disponible pour l’environnement de production/étape défini dans un programme normal configuré à des fins de production. Cette fonction est toutefois disponible pour les environnements de production/d’étape dans un programme de sandbox.

## Accès à la Console développeur {#accessing-developer-console}

Sélectionnez Console **** développeur dans le menu déroulant de la carte **Environnements** .

![](assets/dev-console1.png)

Vous pouvez également sélectionner cette option à partir du bouton **Gérer** si vous cliquez sur **Détails** dans la carte **Environnements** .


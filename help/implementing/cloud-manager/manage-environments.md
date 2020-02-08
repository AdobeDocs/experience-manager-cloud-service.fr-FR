---
title: Gestion des environnements - Service Cloud
description: Gestion des environnements - Service Cloud
translation-type: tm+mt
source-git-commit: 81f993325b80c0de17d6032a45ebd61c22169d39

---


# Gestion des environnements {#manage-environments}

La section suivante décrit les types d’environnement qu’un utilisateur peut créer et comment il peut créer un environnement.

## Types d’environnement {#environment-types}

Un utilisateur disposant des autorisations requises peut créer les types d’environnement suivants (dans les limites de ce qui est disponible pour le client spécifique).

* **Environnement** de production et d’étape :La production et la scène sont disponibles en tant que duo et sont utilisées à des fins de test et de production.

* **Développement**: Un environnement de développement peut être créé à des fins de développement et de test et sera associé uniquement aux pipelines qui ne sont pas en production.

   >[!NOTE]
   >Un environnement de développement créé automatiquement dans un programme Sandbox sera configuré pour inclure les solutions Sites et Ressources.

   Le tableau suivant récapitule les types d’environnement et leurs attributs :

   | Nom | Niveau d’auteur | Publier le niveau | L’utilisateur peut créer | L’utilisateur peut supprimer | Pipeline pouvant être associé à l&#39;environnement |
   |--- |--- |--- |--- |---|---|
   | Production | Oui | Oui si Sites inclus | Oui | Non | Gazoduc de production |
   | Scène | Oui | Oui si Sites inclus | Oui | Non | Gazoduc de production |
   | Développement | Oui | Oui si Sites inclus | Oui | Oui | Pipeline hors production |

   >[!NOTE]
   >La production et la scène sont disponibles en tant que duo et sont utilisées à des fins de test et de production.  L’utilisateur ne pourra pas créer uniquement un environnement de production ou de phase.

## Ajout d’un environnement {#adding-environments}


1. L’utilisateur clique sur le bouton **Ajouter un environnement** pour ajouter un environnement.

   ![](assets/add-environment.png)

1. La boîte de dialogue **Ajouter un environnement** s’affiche. L’utilisateur doit envoyer des détails tels que le type **d’** environnement et le nom **de l’** **environnement et la description de l’environnement (selon l’objectif de l’utilisateur lors de la création de l’environnement dans les limites de ce qui est disponible pour le client spécifique).**

   ![](assets/add-environment2.png)

   >[!NOTE]
   >Lors de la création d’un environnement, une ou plusieurs *intégrations* sont créées dans les E/S Adobe. Elles sont visibles par les utilisateurs clients qui ont accès à la console d’E/S Adobe et ne doivent pas être supprimées. Ceci est déconseillé dans la description de la console d’E/S Adobe.

   ![](assets/add-environment-image1.png)

1. Cliquez sur **Enregistrer** pour ajouter un environnement avec les critères renseignés.  Désormais, l’écran *Aperçu* affiche la carte d’où vous pouvez configurer votre pipeline.

   >[!NOTE]
   >Si vous n’avez pas encore configuré votre pipeline hors production, l’écran *Aperçu* affiche la carte d’où vous pouvez créer votre pipeline hors production.


## Mise à jour de l’environnement {#updating-dev-environment}

Les mises à jour des environnements Stage et Production sont gérées automatiquement par Adobe.

Les mises à jour des environnements de développement sont gérées par les utilisateurs du programme. Lorsqu’un environnement n’exécute pas la dernière version d’AEM disponible pour le public, l’état de la carte Environments sur l’écran d’accueil affiche **UPDATE DISPONIBLE**.

![](assets/manage-environments2.png)
)

Lorsque cet état est affiché, l’option **Mettre à jour** est disponible dans le menu déroulant, à la fois dans la carte Environnements et dans le menu **Gérer** si vous cliquez sur **Détails** de la carte **ENVIRONNEMENTS.**

![](assets/add-environment4.png)

Si vous sélectionnez cette option dans le menu déroulant, un gestionnaire de déploiement pourra mettre à jour le pipeline associé à cet environnement vers la dernière version, puis exécuter le pipeline.

Si le pipeline a déjà été mis à jour, l’utilisateur est invité à exécuter le pipeline.

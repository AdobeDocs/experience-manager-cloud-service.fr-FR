---
title: Gestion des environnements - Cloud Service
description: Gestion des environnements - Cloud Service
translation-type: tm+mt
source-git-commit: 5d3100ce33aa294c30509f8b8c0e41ed4c42b880
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 62%

---


# Gestion des environnements {#manage-environments}

La section suivante décrit les types d’environnement qu’un utilisateur peut créer et comment cet utilisateur peut créer un environnement.

## Types d’environnement {#environment-types}

Un utilisateur disposant des autorisations requises peut créer les types d’environnement suivants (dans les limites de ce qui est disponible pour le client spécifique).

* **Environnement de production et d’évaluation** : les environnements de production et d’évaluation sont disponibles en duo et sont utilisés à des fins de test et de production.

* **Développement** : un environnement de développement peut être créé à des fins de développement et de test et sera associé uniquement aux pipelines qui ne sont pas en production.

   >[!NOTE]
   >Un environnement de développement créé automatiquement dans un programme Sandbox sera configuré pour inclure les solutions Sites et Assets.

   Le tableau suivant récapitule les types d’environnement et leurs attributs :

   | Nom | Niveau de création | Niveau de publication | L’utilisateur peut créer | L’utilisateur peut supprimer | Pipeline pouvant être associé à l’environnement |
   |--- |--- |--- |--- |---|---|
   | Production | Oui | Oui si Sites est inclus | Oui | Non | Pipeline de production |
   | Évaluation | Oui | Oui si Sites est inclus | Oui | Non | Pipeline de production |
   | Développement | Oui | Oui si Sites est inclus | Oui | Oui | Pipeline hors production |

   >[!NOTE]
   >La production et le test sont disponibles en duo et sont utilisés à des fins de test et de production. L’utilisateur ne pourra pas créer uniquement un environnement de production ou de test.

## Environnement Ajoutant {#adding-environments}

1. Cliquez sur **Ajouter un environnement** pour ajouter un environnement. Ce bouton sera accessible à l’aide de l’écran **Environnements**.
   ![](assets/environments-tab.png)

   L’option **Ajouter un environnement** est également disponible sur la carte **Environnements** lorsqu’il n’y a aucun environnement dans le programme.

   ![](assets/no-environments.png)

   >[!NOTE]
   >L’option **Ajouter un environnement** sera désactivée en raison de l’absence d’autorisations ou de conditions contractuelles.

1. La boîte de dialogue **Ajouter l’environnement** s’affiche. L’utilisateur doit ajouter des détails tels que le **Type d’environnement**, **Nom de l’environnement** et la **Description de l’environnement** (selon l’objectif de l’utilisateur lors de la création de l’environnement dans les limites de ce qui est disponible pour le client spécifique).

   ![](assets/add-environment2.png)

   >[!NOTE]
   >Lors de la création d’un environnement, une ou plusieurs *intégrations* sont créées dans Adobe I/O. Elles sont visibles par les utilisateurs clients qui ont accès à la console Adobe I/O et ne doivent pas être supprimées. Cette suppression est déconseillée dans la description de la console Adobe I/O.

   ![](assets/add-environment-image1.png)

1. Cliquez sur **Enregistrer** pour ajouter un environnement avec les critères renseignés. Désormais, l’écran *Aperçu* affiche la carte à partir de laquelle vous pouvez configurer votre pipeline.

   >[!NOTE]
   >Si vous n’avez pas encore configuré votre pipeline hors production, l’écran *Aperçu* affiche la carte d’où vous pouvez créer votre pipeline hors production.


## Affichage de l&#39;Environnement {#viewing-environment}

La carte **Environnements** de la page Aperçu liste jusqu’à trois environnements.

1. Sélectionnez le bouton **Afficher tout** pour accéder à la page de résumé **Environnement** afin de vue d’un tableau avec une liste complète d’environnements.

   ![](assets/environment-view-1.png)

1. La page **Environnements** affiche la liste de tous les environnements existants.

   ![](assets/environment-view-2.png)

1. Sélectionnez l&#39;un des environnements de la liste à la vue des détails de l&#39;environnement.

   ![](assets/environment-view-3.png)


## Mise à jour de l’environnement {#updating-dev-environment}

Les mises à jour des environnements Test et Production sont gérées automatiquement par Adobe.

Les mises à jour des environnements de développement sont gérées par les utilisateurs du programme. Lorsqu’un environnement n’exécute pas la dernière version d’AEM disponible pour le public, l’état de la carte Environnements sur l’écran d’accueil affiche **MISE À JOUR DISPONIBLE**.

![](assets/environ-update.png)


L’option **Mettre à jour** est disponible à partir de la carte **Environnements**.
Cette option est également disponible si vous cliquez sur **Détails** dans la carte **Environnements**. La page **Environnements** s’ouvre. Une fois que vous avez sélectionné l’environnement de développement, cliquez sur **...** et sélectionnez **Mettre à jour**, comme illustré dans la figure ci-dessous :

![](assets/environ-update2.png)

Si vous sélectionnez cette option, un gestionnaire de déploiement pourra mettre à jour le pipeline associé à cet environnement vers la dernière version, puis exécuter le pipeline.

Si le pipeline a déjà été mis à jour, l’utilisateur est invité à exécuter le pipeline.

## Suppression d’un environnement {#deleting-environment}

Un utilisateur disposant des autorisations requises peut supprimer un environnement de développement.

L’option **Supprimer** est disponible dans le menu déroulant de la carte **Environnements.** Cliquez sur **...** pour un environnement de développement que vous souhaitez supprimer.

![](assets/environ-delete.png)

L’option de suppression est également disponible si vous cliquez sur **Détails** dans la carte **Environnements**. La page **Environnements** s’ouvre. Une fois que vous avez sélectionné l’environnement de développement, cliquez sur **...** et sélectionnez **Supprimer**, comme illustré dans la figure ci-dessous :

![](assets/environ-delete2.png)


>[!NOTE]
>
>Cette fonction n’est pas disponible pour l’environnement de production/d’évaluation défini dans une configuration de programme normale à des fins de production. Cette fonction est toutefois disponible pour les environnements de production/d’évaluation dans un programme Sandbox.

## Gestion de l’accès {#managing-access}

Sélectionnez **Gérer l’accès** dans le menu déroulant de la carte **Environnements**. Vous pouvez accéder directement à l’instance d’auteur et gérer l’accès pour votre environnement.

Consultez [Gestion de l’accès à l’instance d’auteur](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md#manage-access-aem) pour en savoir plus.

![](assets/environ-access.png)


## Accès à Developer Console {#accessing-developer-console}

Sélectionnez **Developer Console** dans le menu déroulant de la carte **Environnements**. Un nouvel onglet s’ouvre alors dans votre navigateur, contenant la page de connexion à **Developer Console**.

Seul un utilisateur possédant le rôle de développeur aura accès à **Developer Console**. L’exception concerne les programmes Sandbox, où tout utilisateur ayant accès au programme Cloud Manager Sandbox aura accès à **Developer Console**.

Pour plus d’informations, voir [Mise en veille et réactivation d’environnements Sandbox](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/sandbox-programs.html#hibernating-introduction).


![](assets/environ-devconsole.png)

Cette option est également disponible si vous cliquez sur **Détails** dans la carte **Environnements**. La page **Environnements** s’ouvre. Une fois que vous avez sélectionné un environnement, cliquez sur **...** et sélectionnez **Console développeur**.

## Connexion locale {#login-locally}

Sélectionnez **Connexion locale** dans le menu déroulant de la carte **Environnements** pour vous connecter localement à Adobe Experience Manager.

![](assets/environ-login-locally.png)

De plus, vous pouvez vous connecter localement à partir de la **page de résumé Environnements**.

![](assets/environ-login-locally-2.png)

## Gestion des noms de domaine personnalisés {#manage-cdn}

Accédez à la page de détails **Environnements** à partir de la page Résumé des Environnements.

Vous pouvez exécuter les actions suivantes sur le service de publication pour votre environnement, comme décrit ci-dessous :

1. **Ajouter un**
nom de domaine personnaliséReportez-vous à la section  [Ajoute d&#39;un nom de domaine personnalisé.](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

1. **Affichage et mise à jour des**
certificats de domaine et des noms de domaine personnalisésReportez-vous à la section
   * [Affichage et mise à jour des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.md)
   * [Affichage et mise à jour des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/view-update-replace-ssl-certificate.md)

1. **Suppression de noms de domaine et de**
certificats personnalisésReportez-vous à la section
   * [Suppression d&#39;un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md)
   * [Certificats SSL](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md)

## Gestion des Listes autorisées IP {#manage-ip-allow-lists}

Accédez à la page Détails de l&#39;Environnement à partir de la page Récapitulatif des Environnements. Vous pouvez exécuter les actions suivantes sur le ou les services de publication et/ou d’auteur pour votre environnement ici.

### Application d&#39;une Liste autorisée IP {#apply-ip-allow-list}

L’application d’une Liste autorisée IP est le processus par lequel toutes les plages d’adresses IP incluses dans la définition de la Liste autorisée sont associées à un service Auteur ou Publication dans un environnement. Un utilisateur du rôle Propriétaire de l&#39;entreprise ou Deployment Manager doit être connecté pour pouvoir appliquer une Liste autorisée IP.

>[!NOTE]
>La Liste autorisée IP doit exister dans Cloud Manager pour pouvoir l’appliquer à un environnement-service. Pour en savoir plus sur les Listes autorisées IP dans Cloud Manager, accédez à [Introduction aux Listes autorisées IP dans le composant Can Manager](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

Suivez les étapes ci-dessous :

1. Accédez à la page Détails de l&#39;Environnement spécifique à partir de l&#39;écran Environnements et accédez au tableau Liste autorisée IP.
1. Utilisez les champs d’entrée en haut du tableau Liste autorisée IP pour sélectionner la Liste autorisée IP et le service Auteur ou Publication auquel vous souhaitez l’appliquer.
1. Sélectionnez ensuite Appliquer et confirmez votre envoi.

### Annulation de l&#39;application d&#39;une Liste autorisée IP {#unapply-ip-allow-list}

L’annulation de l’application d’une Liste autorisée IP est le processus par lequel toutes les plages d’adresses IP incluses dans la définition de la Liste autorisée sont dissociées d’un service Auteur/Editeur dans un environnement.  Un utilisateur du rôle Propriétaire de l&#39;entreprise ou Deployment Manager doit être connecté pour pouvoir annuler l&#39;application d&#39;une Liste autorisée IP.

Suivez les étapes ci-dessous :

1. Accédez à la page Détails de l&#39;Environnement spécifique à partir de l&#39;écran Environnements et accédez au tableau Liste autorisée IP.
1. Identifiez la ligne où est répertoriée la règle de Liste autorisée IP que vous souhaitez annuler.
1. Sélectionnez **...** à l&#39;extrémité droite de la ligne.
1. Sélectionnez l’option Annuler l’application et confirmez votre envoi.



---
title: Mise en veille et réactivation d’environnements Sandbox
description: Découvrez comment les environnements d’un programme Sandbox passent automatiquement en mode veille et comment les réactiver.
exl-id: c0771078-ea68-4d0d-8d41-2d9be86408a4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 88b4864da30fbf201dbd5bde1ac17d3be977648f
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 42%

---


# Mise en veille et réactivation d’environnements Sandbox {#hibernating-introduction}

Les environnements d’un programme Sandbox passent en mode veille si aucune activité n’est détectée pendant huit heures. La veille est propre aux environnements de programme Sandbox. Les environnements de programme de production ne peuvent pas être mis en veille.

## Mise en veille {#hibernation-introduction}

La mise en veille peut se produire automatiquement ou manuellement.

* **Automatique** - Les environnements de programme Sandbox sont automatiquement mis en veille après huit heures d’inactivité. L’inactivité est définie comme l’absence de requêtes aux services de création, de prévisualisation et de publication.
* **Manuelle** - En tant qu’utilisateur, vous pouvez mettre en veille manuellement un environnement de programme Sandbox. Il n’est pas nécessaire de le faire, car la veille se produit automatiquement comme décrit précédemment.

Les environnements de programme Sandbox peuvent prendre quelques minutes pour passer en mode veille. Les données sont conservées pendant la veille.

### Mise en veille manuelle d’un environnement de programme Sandbox {#using-manual-hibernation}

Vous pouvez mettre en veille manuellement votre programme Sandbox à partir de la Developer Console. Tout utilisateur de Cloud Manager peut accéder à Developer Console pour un programme d’environnement de test.

**Pour mettre manuellement en veille un environnement de programme Sandbox :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, cliquez sur un *programme sandbox* que vous souhaitez mettre en veille pour afficher ses détails.

1. Sur la carte **Environments**, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), puis sur **Developer Console**.

   * Consultez [Accès à Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) pour plus d’informations sur Developer Console.

   ![Option du menu Developer Console](/help/implementing/cloud-manager/assets/developer-console-menu-option.png)

1. Sur la page **Developer Console**, cliquez sur **Hibernate** (Mettre en veille).

<!-- UPDATE THESE SCREENSHOTS WHEN NEW AEM DEVELOPER CONSOLE UI IS RELEASED. AS OF OCTOBER 14, 2024, NEW UI IS STILL IN BETA -->

![Bouton Hibernate](assets/hibernate-1.png) (Mise en veille)

1. Cliquez sur **Hibernate** (Mise en veille) pour confirmer l’étape.

   ![Confirmation de la mise en veille](assets/hibernate-2.png)

Une fois la veille terminée, vous voyez la notification de fin du processus de veille pour votre environnement dans l’écran **Developer Console**.

![Confirmation de veille](assets/hibernate-4.png)

Dans Developer Console, cliquez sur le lien **Environments** dans le chemin de navigation situé au-dessus de la liste déroulante **Pod** pour afficher les environnements disponibles pour la veille.

![Liste des environnements à mettre en veille](assets/hibernate-1b.png)

## Réactivation manuelle d’un programme d’environnement de test à partir de Developer Console {#de-hibernation-introduction}

Vous pouvez mettre en veille manuellement votre programme d’environnement de test à partir de Developer Console.

>[!IMPORTANT]
>
>Un utilisateur disposant d’une de rôle de **développeur** peut réactiver un environnement de programme Sandbox.

**Pour réactiver manuellement un programme d’environnement de test à partir de Developer Console :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, cliquez sur le programme que vous souhaitez réactiver pour afficher ses détails.

1. Sur la carte **Environments** , cliquez sur https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg , puis sur **Developer Console**.

   * Consultez [Accès à Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) pour plus d’informations sur Developer Console.

1. Cliquez sur **De-hibernate** (Réactiver).

   ![Bouton De-hibernate](assets/de-hibernation-img1.png) (Réactiver)

1. Cliquez sur **De-Hibernate** (Réactiver) pour confirmer l’étape.

   ![Confirmation de la réactivation](assets/de-hibernation-img2.png)

1. Vous recevez une notification vous informant que le processus de réactivation a commencé et vous recevez des informations sur la progression.

   ![Notification de progression de la mise en veille](assets/de-hibernation-img3.png)

1. Une fois le processus terminé, l’environnement de programme Sandbox redevient actif.

   ![Fin de la réactivation](assets/de-hibernation-img4.png)

Dans Developer Console, cliquez sur le lien **Environments** dans le chemin de navigation situé au-dessus de la liste déroulante **Pod** pour accéder aux environnements disponibles pour la réactivation.

![Liste des capsules en veille](assets/de-hibernate-1b.png)

### Autorisations de réactiver {#permissions-de-hibernate}

Tout utilisateur disposant d’un profil de produit qui lui donne accès à AEM as a Cloud Service doit pouvoir accéder à la **Developer Console**, qui lui permet de réactiver l’environnement.

## Accès à un environnement mis en veille {#accessing-hibernated-environment}

Lorsqu’un utilisateur envoie une requête de navigateur au service de création, de prévisualisation ou de publication d’un environnement mis en veille, il rencontre une page d’entrée. Cette page décrit l’état de veille de l’environnement et fournit un lien vers Developer Console pour la réactivation.

![Page de destination du service mis en veille](assets/de-hibernation-img5.png)

## Déploiements et mises à jour AEM {#deployments-updates}

Les environnements mis en veille permettent toujours les déploiements et les mises à niveau manuelles d’AEM.

* Un utilisateur peut utiliser un pipeline pour déployer du code personnalisé sur des environnements mis en veille. L’environnement reste en veille et le nouveau code apparaît dans l’environnement une fois réactivé.

* Les mises à niveau d’AEM peuvent être appliquées aux environnements mis en veille et peuvent être déclenchées manuellement à partir de Cloud Manager. L’environnement reste en veille et la nouvelle version apparaît dans l’environnement une fois sa réactivation terminée.

## Mise en veille et suppression {#hibernation-deletion}

* Les environnements d’un programme Sandbox sont automatiquement mis en veille après huit heures d’inactivité.
   * L’inactivité est définie comme l’absence de requêtes aux services de création, de prévisualisation et de publication.
   * Une fois mis en veille, ils peuvent être [réactivés manuellement](#de-hibernation-introduction).
* Les programmes Sandbox sont supprimés après six mois de mise en veille continue, après quoi ils peuvent être recréés.

>[!NOTE]
>
>Seuls les environnements Sandbox sont automatiquement supprimés après six mois de mise en veille continue. Le programme Sandbox avec son référentiel et son code est conservé.

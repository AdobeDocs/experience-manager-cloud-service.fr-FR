---
title: Accès à Cloud Manager
description: Découvrez comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet.
role: Admin, User, Developer
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 41%

---


# Accès à Cloud Manager {#cloud-resources}

Dans cette partie du [parcours d&#39;intégration,](overview.md) vous apprendrez à accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet.

## Objectif {#objective}

Dans l&#39;article précédent du présent parcours d&#39;intégration, [Affectation de membres d’équipe à des profils de produit Cloud Manager,](assign-profiles-cloud-manager.md) vous avez attribué les rôles appropriés à votre équipe AEMaaCS. Découvrez maintenant comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet que votre équipe utilisera.

Puisque vous avez terminé l’étape précédente dans ce parcours, votre équipe peut accéder à Cloud Manager. Cloud Manager permet de créer et de gérer des ressources de projet telles que des programmes et des environnements.

Après avoir lu ce document, vous devez comprendre :

* qu’un administrateur système a affecté à la variable **Propriétaire de l’entreprise** doit être le premier de votre entreprise à se connecter et à accéder à Cloud Manager.
* Comment se connecter à Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et constitue le point d’entrée unique de votre équipe. Il prend en charge les clients disposant de configurations de développement d’entreprise avec ses pipelines CI/CD conçus spécifiquement, qui sont équipés pour garantir des tests approfondis et une qualité de code optimale afin de fournir des expériences exceptionnelles. Cloud Manager fournit tout ce dont vous avez besoin pour commencer en libre-service, notamment la possibilité de créer vos ressources et environnements cloud.

En règle générale, un membre de l’équipe affecté à la variable **Propriétaire de l’entreprise** product profile est chargé d’ajouter vos ressources cloud telles que les programmes et les environnements. Cette personne comprend les besoins de l’entreprise et qui effectue la configuration initiale de Cloud Manager.

Pour les besoins de ce parcours d’intégration, vous, en tant qu’administrateur système, vous êtes déjà affecté à la variable **Propriétaire de l’entreprise** profil de produit et configurera les ressources cloud. Selon les besoins réels du projet, les propriétaires d’entreprise peuvent être ou non les mêmes que l’administrateur système.

## Accédez à Cloud Manager en tant qu’administrateur système et propriétaire de l’entreprise {#access-sysadmin-bo}

Avant les membres de l’équipe que vous avez affectés à la **Propriétaire de l’entreprise** le rôle peut accéder à cloud manager et commencer à créer des ressources cloud. l’administrateur système doit se voir attribuer la variable **Propriétaire de l’entreprise** et connectez-vous à Cloud Manager comme vous l’avez fait à l’étape précédente de ce parcours d’intégration.

1. Assurez-vous, en tant qu’administrateur système, que vous disposez de la variable **Propriétaire de l’entreprise** rôle attribué.

   * Revenez à l&#39;étape précédente dans ce parcours, [Affecter des membres d’équipe à des profils de produit Cloud Manager,](assign-profiles-cloud-manager.md) pour plus d’informations sur l’attribution de la variable **Propriétaire de l’entreprise** du rôle de l’administrateur système si vous ne l’avez pas déjà fait.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et familiarisez-vous avec la page d’entrée normale.

En se connectant correctement en tant qu’administrateur système avec **Propriétaire de l’entreprise** , vous initialisez Cloud Manager pour l’utiliser par les autres utilisateurs avec le **Propriétaire de l’entreprise** rôle. Vous ne recevrez aucune confirmation ou message. Il vous suffit de vous connecter.

Jusqu’à ce que vous vous connectiez à Cloud Manager en tant qu’administrateur système avec le **Propriétaire de l’entreprise** rôle, autres utilisateurs avec le **Propriétaire de l’entreprise** ne sera pas en mesure de créer des programmes dans Cloud Manager même s’ils disposent des rôles appropriés.

## Accéder à Cloud Manager {#navigate-cloud-manager}

Utilisateurs avec la variable **Propriétaire de l’entreprise** Un rôle recevra un e-mail de bienvenue avec un lien pour commencer. Suivez les étapes ci-dessous pour accéder à Cloud Manager à l’aide de cet e-mail de bienvenue.

1. Dans l’e-mail de bienvenue, cliquez sur **Commencer**, comme illustré dans l’illustration ci-dessous.
   ![Exemple d’e-mail](/help/journey-onboarding/assets/get-started-email.png)

1. Vous accédez à la page **Programmes et produits** de Cloud Manager.

   >[!TIP]
   >
   >Vous pouvez également accéder directement à la page de connexion de Cloud Manager à partir de `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`. Veuillez mettre un signet sur cette page pour vous en servir ultérieurement.

1. Vous serez redirigé vers la page d’entrée de Cloud Manager.

Vous pouvez également accéder au **Programmes et produits** à partir de la page d’accueil Adobe Experience Cloud en procédant comme suit :

1. Accédez directement à [Adobe Experience Cloud](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

1. Sur la page d’accueil d’Adobe Experience Cloud, sélectionnez **Experience Manager**.

   ![Page d’accueil Experience Cloud](/help/journey-onboarding/assets/setup-resources2.png)

1. Vous accédez alors à la page d’accueil AEM. À partir de là, cliquez sur **Ouvrir** sur la mosaïque **Cloud Manager**.

   ![Page d’accueil AEM](/help/journey-onboarding/assets/setup-resources3.png)

1. Une fois votre connexion établie, vous êtes dirigé vers la page d’entrée de Cloud Manager, comme indiqué ci-dessous. Voir [Affichage des programmes de Cloud Manager](#viewing-programs) pour plus d’informations.

C’est à vous de décider comment accéder à vos programmes et produits via Cloud Manager et cela n’a aucun effet sur la manière dont vous utilisez Cloud Manager ou dont vous gérez vos programmes.

>[!NOTE]
>
>Selon les rôles affectés dans Cloud Manager et l’état de l’application, différents écrans s’affichent lors de l’utilisation de l’interface utilisateur de Cloud Manager.

## Affichage des programmes {#viewing-programs}

Une fois que vous avez accédé à Cloud Manager, ce que vous voyez dépend de l’état de vos programmes, comme indiqué dans les sections suivantes.

### Lorsqu’il n’existe aucun programme {#no-programs}

S’il n’existe aucun programme dans votre organisation, votre page d’entrée vous invite à créer votre premier programme.

![Aucun programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### Quand les programmes existent déjà {#programs-exist}

Si des programmes existent déjà dans votre organisation, votre page d’entrée affiche vos programmes existants et propose également un bouton pour ajouter des programmes supplémentaires.

![Il existe des programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### Lorsqu’un programme existe et que vous êtes administrateur système {#programs-exist-sysadmin}

Si des programmes existent déjà dans votre entreprise et que vous êtes administrateur système, votre page d’entrée s’affiche. **Gérer l’accès** avec **Ajout d’un programme** .

![Vue de l’administrateur système](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## Vérification des rôles utilisateur {#verify-user-roles}

Une fois que vous êtes connecté à Cloud Manager, vous pouvez vérifier que le profil de produit **Propriétaire de l’entreprise** vous a été attribué.

1. Sélectionnez votre profil en haut à droite de la fenêtre.

   ![Profil utilisateur](/help/journey-onboarding/assets/setup-resources5.png)

1. Sélectionnez **Rôles utilisateur** pour afficher les rôles affectés à votre utilisateur.

   ![Rôles utilisateur](/help/journey-onboarding/assets/setup-resources6.png)

1. La boîte de dialogue doit confirmer que votre utilisateur dispose de la variable **Propriétaire de l’entreprise** rôle.

   ![Liste des rôles utilisateur](/help/journey-onboarding/assets/setup-resources7.png)

Vous vous êtes connecté à Cloud Manager en tant que propriétaire d’entreprise. Si le rôle de **Propriétaire de l’entreprise** ne vous est pas affecté, contactez votre administrateur système.

## Prochaines étapes {#whats-next}

Maintenant que vous pouvez accéder à Cloud Manager en tant qu’administrateur système, vous êtes prêt à créer votre premier programme.

Continuez votre parcours d’intégration en consultant le document. [Création d’un programme](create-program.md) où vous apprendrez à le faire.

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur les aspects suivants :

* [Présentation de Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - En savoir plus sur Cloud Manager, les programmes Cloud Manager et les environnements.

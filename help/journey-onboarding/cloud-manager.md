---
title: Accéder à Cloud Manager
description: Découvrez comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
feature: Onboarding
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '1040'
ht-degree: 100%

---

# Accéder à Cloud Manager {#cloud-resources}

Dans cette partie du [parcours d’intégration](overview.md), vous apprendrez à accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet.

## Objectif {#objective}

Dans l’article précédent du présent parcours d’intégration, [Affectation de membres d’équipe à des profils de produit Cloud Manager](assign-profiles-cloud-manager.md), vous avez attribué les rôles appropriés à votre équipe AEMaaCS. Découvrez maintenant comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet que votre équipe utilise.

Puisque vous avez terminé l’étape précédente dans ce parcours, votre équipe peut accéder à Cloud Manager. Cloud Manager permet de créer et de gérer des ressources de projet telles que des programmes et des environnements.

Après avoir lu ce document, vous comprendrez les éléments suivants :

* Un administrateur ou une administratrice système affecté(e) au rôle **Propriétaire de l’entreprise** doit être le premier/la première dans votre organisation à se connecter et à accéder à Cloud Manager.
* Comment se connecter à Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et constitue le point d’entrée unique de votre équipe. Il prend en charge les clients disposant de configurations de développement d’entreprise avec ses pipelines CI/CD spécialement conçus, qui sont équipés pour garantir des tests approfondis et une qualité de code optimale afin de fournir des expériences exceptionnelles. Cloud Manager fournit tout ce dont vous avez besoin pour commencer en libre-service, notamment la possibilité de créer vos ressources et environnements cloud.

En règle générale, un membre de l’équipe affecté au profil de produit **Propriétaire de l’entreprise** est chargé d’ajouter vos ressources cloud telles que les programmes et les environnements. Cette personne comprend les besoins de l’entreprise et effectue la configuration initiale de Cloud Manager.

Pour les besoins de ce parcours d’intégration, vous (en tant qu’administrateur ou administratrice système) êtes déjà affecté(e) au profil de produit **Propriétaire de l’entreprise** et pouvez configurer les ressources cloud. Selon les exigences réelles du projet, les propriétaires d’entreprise peuvent être ou non les mêmes que l’administrateur ou l’administratrice système.

## Accédez à Cloud Manager en tant qu’administrateur ou administratrice système et propriétaire de l’entreprise {#access-sysadmin-bo}

Avant que les membres de l’équipe que vous avez affectés au rôle de **Propriétaire de l’entreprise** puissent accéder à Cloud Manager et commencer à créer des ressources cloud, l’administrateur ou l’administratrice système doit se voir affecter le rôle de **Propriétaire de l’entreprise**. Ils doivent également se connecter à Cloud Manager comme vous l’avez fait à l’étape précédente de ce parcours d’intégration.

1. Assurez-vous, en tant qu’administrateur ou administratrice système, que le rôle de **Propriétaire de l’entreprise** vous est affecté(e).

   * Revenez à l’étape précédente dans ce parcours, [Affecter des membres de l’équipe à des profils de produits Cloud Manager](assign-profiles-cloud-manager.md), pour plus d’informations sur l’attribution du rôle de **Propriétaire de l’entreprise** à l’administrateur ou l’administratrice système.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et familiarisez-vous avec la page de destination normale.

En vous connectant en tant qu’administrateur système avec le rôle de **Propriétaire de l’entreprise**, vous initialisez Cloud Manager pour une utilisation par les autres utilisateurs affectés au rôle de **Propriétaire de l’entreprise**. Vous ne recevez aucune confirmation ni aucun message. Il vous suffit de vous connecter.

Jusqu’à ce que vous vous connectiez à Cloud Manager en tant qu’administrateur ou administratrice système avec le rôle **Propriétaire de l’entreprise**, les autres personnes dont le rôle est **Propriétaire de l’entreprise** ne pourront pas créer de programmes dans Cloud Manager. Cette règle est vraie, même si les rôles appropriés leur sont attribués.

## Accéder à Cloud Manager {#navigate-cloud-manager}

L’utilisateur ou l’utilisatrice dont le rôle est **Propriétaire de l’entreprise** recevra un e-mail de bienvenue avec un lien pour commencer. Suivez les étapes ci-dessous pour accéder à Cloud Manager à l’aide de cet e-mail de bienvenue.

1. Dans l’e-mail de bienvenue, cliquez sur **Commencer**, comme illustré ci-dessous.
   ![Exemple d’e-mail](/help/journey-onboarding/assets/get-started-email.png)

1. Accédez à la page **Programmes et produits** de Cloud Manager.

   >[!TIP]
   >
   >Vous pouvez également accéder directement à la page de connexion de Cloud Manager à partir de `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`. Mettez un signet sur cette page pour vous en servir ultérieurement.

1. Vous accédez à la page de destination de Cloud Manager.

Vous pouvez également accéder à la page **Programmes et produits** de Cloud Manager à partir de la page d’accueil d’Adobe Experience Cloud en procédant comme suit :

1. Accédez directement à [Adobe Experience Cloud](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

1. Sur la page d’accueil d’Adobe Experience Cloud, sélectionnez **Experience Manager** pour ouvrir la page d’accueil d’AEM.

   ![Page d’accueil Experience Cloud](/help/journey-onboarding/assets/setup-resources2.png)

1. Sur la vignette **Cloud Manager**, cliquez sur **Lancer**.

   ![Page d’accueil AEM](/help/journey-onboarding/assets/setup-resources3.png)

1. Une fois la connexion établie, vous accédez à la page de destination de Cloud Manager. Voir [Affichage des programmes de Cloud Manager](#viewing-programs) pour plus d’informations.

C’est à vous de décider comment accéder à vos programmes et produits via Cloud Manager et cela n’a aucun effet sur la manière dont vous utilisez Cloud Manager ou dont vous gérez vos programmes.

>[!NOTE]
>
>Selon les rôles affectés dans Cloud Manager et l’état de l’application, plusieurs écrans s’affichent lors de l’utilisation de l’interface utilisateur de Cloud Manager.

## Affichage des programmes {#viewing-programs}

Une fois que vous avez accédé à Cloud Manager, ce que vous voyez dépend de l’état de vos programmes, comme indiqué dans les sections suivantes.

### Lorsqu’il n’existe aucun programme {#no-programs}

S’il n’existe aucun programme dans votre organisation, votre page de destination vous invite à créer votre premier programme.

![Aucun programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### Quand les programmes existent déjà {#programs-exist}

Si des programmes existent déjà dans votre organisation, votre page de destination affiche vos programmes existants et propose également un bouton pour ajouter des programmes supplémentaires.

![Il existe des programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### Lorsqu’un programme existe et que vous êtes administrateur système {#programs-exist-sysadmin}

Si des programmes existent déjà dans votre organisation et que vous êtes administrateur ou administratrice système, votre page de destination affiche alors le bouton **Gérer l’accès** avec l’option **Ajouter un programme**.

![Vue de l’administrateur système](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## Vérification des rôles utilisateur {#verify-user-roles}

Une fois que vous êtes connecté à Cloud Manager, vous pouvez vérifier que le profil de produit **Propriétaire de l’entreprise** vous a été attribué.

1. Sélectionnez votre profil en haut à droite de la fenêtre.

1. Pour afficher les rôles affectés à votre utilisateur ou utilisatrice, sélectionnez **Rôles utilisateur**.

   ![Rôles utilisateur](/help/journey-onboarding/assets/setup-resources6.png)

1. La boîte de dialogue doit confirmer que votre utilisateur dispose du rôle **Propriétaire de l’entreprise**.

   ![Liste des rôles utilisateur](/help/journey-onboarding/assets/setup-resources7.png)

Vous vous êtes connecté à Cloud Manager en tant que propriétaire d’entreprise. Si le rôle de **Propriétaire de l’entreprise** ne vous est pas affecté, contactez votre administrateur système.

## Prochaines étapes {#whats-next}

Maintenant que vous pouvez accéder à Cloud Manager en tant qu’administrateur ou administratrice système, vous êtes prêt(e) à créer votre premier programme.

Continuez votre parcours d’intégration en consultant le document [Créer un programme](create-program.md).

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous des ressources facultatives supplémentaires si vous souhaitez aller au delà du contenu du parcours d’intégration.

* [Présentation de Cloud Manager](/help/onboarding/cloud-manager-introduction.md) -
En savoir plus sur Cloud Manager, les programmes Cloud Manager et les environnements.
* [Équipe et profils de produits AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md) - Découvrez comment l’équipe et les profils de produits AEM as a Cloud Service peuvent accorder et limiter l’accès à vos solutions Adobe sous licence.
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->

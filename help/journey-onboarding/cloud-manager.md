---
title: Accéder à Cloud Manager
description: Découvrez comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
feature: Onboarding
source-git-commit: 0db48ef4c15b6ca530b2626f7078c7172c872fff
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 84%

---

# Accéder à Cloud Manager {#cloud-resources}

Dans cette partie du [parcours d’intégration](overview.md), vous apprendrez à accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet.

## Objectif {#objective}

Dans l’article précédent du présent parcours d’intégration, [Affectation de membres d’équipe à des profils de produit Cloud Manager](assign-profiles-cloud-manager.md), vous avez attribué les rôles appropriés à votre équipe AEMaaCS. Découvrez maintenant comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet que votre équipe prévoit d’utiliser.

Puisque vous avez terminé l’étape précédente dans ce parcours, votre équipe peut accéder à Cloud Manager. Cloud Manager permet de créer et de gérer des ressources de projet telles que des programmes et des environnements.

Après avoir lu ce document, vous comprendrez les éléments suivants :

* Un administrateur ou une administratrice système affecté(e) au rôle **Propriétaire de l’entreprise** doit être le premier/la première dans votre organisation à se connecter et à accéder à Cloud Manager.
* Comment se connecter à Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et constitue le point d’entrée unique de votre équipe. Il prend en charge les clients disposant de configurations de développement d’entreprise avec ses pipelines CI/CD spécialement conçus, qui sont équipés pour garantir des tests approfondis et une qualité de code optimale afin de fournir des expériences exceptionnelles. Cloud Manager fournit tout ce dont vous avez besoin pour commencer en libre-service, notamment la possibilité de créer vos ressources et environnements cloud.

En règle générale, une personne membre de l’équipe affectée au profil de produit **Propriétaire de l’entreprise** est chargée d’ajouter vos ressources cloud telles que les programmes et les environnements. Cette personne comprend les besoins de l’entreprise et effectue la configuration initiale de Cloud Manager.

Pour les besoins de ce parcours d’intégration, vous (en tant qu’administrateur ou administratrice système) êtes déjà affecté(e) au profil de produit **Propriétaire de l’entreprise** et pouvez configurer les ressources cloud. Selon les exigences réelles du projet, les propriétaires d’entreprise peuvent être ou non les mêmes que l’administrateur ou l’administratrice système.

## Accédez à Cloud Manager en tant qu’administrateur ou administratrice système et propriétaire de l’entreprise {#access-sysadmin-bo}

Avant que les personnes membres de l’équipe que vous avez affectées au rôle de **Propriétaire de l’entreprise** puissent accéder à Cloud Manager et commencer à créer des ressources cloud, l’administrateur ou l’administratrice système doit se voir affecter le rôle de **Propriétaire de l’entreprise**. Ils doivent également se connecter à Cloud Manager comme vous l’avez fait à l’étape précédente de ce parcours d’intégration.

1. Assurez-vous, en tant qu’administrateur ou administratrice système, que le rôle de **Propriétaire de l’entreprise** vous est affecté(e).

   Revenez à l’étape précédente, [Affecter des personnes membres de l’équipe à des profils de produits Cloud Manager](assign-profiles-cloud-manager.md), pour plus d’informations sur l’attribution du rôle de **Propriétaire de l’entreprise** à l’administrateur ou l’administratrice système.

1. Connectez-vous à Cloud Manager à l’adresse [experiency.adobe.com](https://experience.adobe.com).
1. Dans le groupe Accès rapide, cliquez sur **Experience Manager**.
1. Dans le panneau de gauche, cliquez sur **Cloud Manager**.

   ![Cloud Manager sur la console](/help/journey-onboarding/assets/consol-cloud-manager.png)

En vous connectant correctement en tant qu’administrateur système avec le rôle **Propriétaire de l’entreprise**, vous utilisez Cloud Manager pour une utilisation par les autres utilisateurs qui disposent du rôle **Propriétaire de l’entreprise**. Vous ne recevez aucune confirmation ni aucun message. Il vous suffit de vous connecter.

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

<!-- OLD
Alternatively, you can navigate to Cloud Manager's **Programs and Products** page from the Adobe Experience Cloud home page using these steps.

1. Navigate directly to [Adobe Experience Cloud](https://experience.adobe.com) and login using your Adobe ID.

1. From the Adobe Experience Cloud home page, select **Experience Manager** to open the AEM home page.

   ![Experience Cloud homepage](/help/journey-onboarding/assets/setup-resources2.png)

1. On the **Cloud Manager** tile, select **Launch**.

   ![AEM home page](/help/journey-onboarding/assets/setup-resources3.png)

1. After successfully logging on, you are directed to the Cloud Manager landing page. See [Viewing Cloud Manager's Programs](#viewing-programs) for more details.

How you access your programs and products via Cloud Manager is up to you and has no effect on how you use Cloud Manager or how you manage your programs.

>[!NOTE]
>
>Depending on the roles assigned in Cloud Manager and the state of the application, you see different screens while using the Cloud Manager user interface. -->

## Afficher les programmes {#viewing-programs}

Une fois que vous avez accédé à Cloud Manager, ce que vous voyez dépend de l’état de vos programmes, comme indiqué dans les sections suivantes.

### Lorsqu’aucun programme n’existe {#no-programs}

S’il n’existe aucun programme dans votre organisation, votre page de destination vous invite à créer votre premier programme.

![Aucun programme](/help/journey-onboarding/assets/cloud-manager-programs-do-not-exist.png)

### Lorsque des programmes existent déjà {#programs-exist}

Si des programmes existent déjà dans votre organisation, votre page de destination affiche vos programmes existants et propose également un bouton pour ajouter des programmes supplémentaires.

![Il existe des programmes](/help/journey-onboarding/assets/cloud-manager-programs-exist.png)

### Lorsqu’un programme existe et que vous êtes administrateur système {#programs-exist-sysadmin}

Si des programmes existent déjà dans votre organisation et que vous êtes administrateur ou administratrice système, votre page de destination affiche alors le bouton **Gérer l’accès** avec l’option **Ajouter un programme**.

![Vue de l’administrateur système](/help/journey-onboarding/assets/cloud-manager-programs-as-sysadmin.png)

## Vérification des rôles utilisateur {#verify-user-roles}

Une fois la connexion à Cloud Manager effectuée, vous pouvez vérifier que le profil de produit **Propriétaire de l’entreprise** vous a été attribué.

1. Dans le coin supérieur droit de la page, cliquez sur l’icône **Compte**.

1. Cliquez sur **Rôles utilisateur**.

   ![Rôles utilisateur](/help/journey-onboarding/assets/cloud-manager-user-roles.png)

1. Dans la boîte de dialogue **Rôles utilisateur**, vérifiez que votre utilisateur dispose du rôle **Propriétaire de l’entreprise**.

   ![Liste des rôles utilisateur](/help/journey-onboarding/assets/cloud-manager-user-roles-business-owner.png)

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

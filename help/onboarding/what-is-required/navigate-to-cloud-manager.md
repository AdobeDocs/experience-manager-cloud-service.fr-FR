---
title: Accès à Cloud Manager
description: Consultez cette page pour savoir comment accéder à la page d’entrée de Cloud Manager.
exl-id: 9cf25d1d-a351-4ea0-b2e9-1df6ca4915b7
source-git-commit: 149776bdd7acce3e00710e50600d9bd1d7cc6b9b
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 80%

---

# Accéder à Cloud Manager {#cloud-manager}

Cloud Manager est une partie importante d’AEM as a Cloud Service. Il permet aux entreprises de gérer elles-mêmes Experience Manager dans le cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité. À l’aide de l’interface utilisateur, vous pouvez configurer et lancer le pipeline CI/CD.

Une fois que votre administrateur système vous a accordé l’accès à Cloud Manager, vous recevez un courrier électronique qui vous conduit à la page d’accueil de [Cloud Manager](https://experience.adobe.com).

>[!NOTE]
>Votre administrateur système doit vous attribuer au moins un rôle Cloud Manager (profil Produit dans l’Admin Console).

1. Dans l’e-mail de bienvenue, cliquez sur **Commencer**, comme illustré dans l’illustration ci-dessous.
   ![](/help/onboarding/what-is-required/assets/get-started-email.png)


   >[!IMPORTANT]
   >Vous pouvez également accéder directement à la page de connexion de Cloud Manager à partir de [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). Mettez cette page en signet pour plus d’informations et pour accéder directement à la page d’entrée de Cloud Manager.

De plus, vous pouvez également accéder à la page **Programmes et produits** de Cloud Manager à partir de la page d’accueil de Adobe Experience Cloud. Suivez les étapes ci-dessous :

1. Accédez directement à [Adobe Experience Cloud](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

1. Sélectionnez **Experience Manager**.
   ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/landing-page1.png)

1. Cliquez sur **Launch** à l’aide de la carte Cloud Manager. Une fois que vous êtes connecté à [!UICONTROL Cloud Manager], vous êtes prêt à utiliser l’interface utilisateur.
   ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/landing-page2.png)

1. Une fois votre connexion établie, vous êtes dirigé vers la page d’entrée de Cloud Manager, comme indiqué ci-dessous.


## Page d’entrée de Cloud Manager {#cloud-manager-landing}

Une fois votre connexion établie, vous êtes dirigé vers la page d’entrée de Cloud Manager, comme indiqué ci-dessous.

>[!NOTE]
>Selon les rôles affectés dans [!UICONTROL Cloud Manager] et l’état de l’application, vous verrez plusieurs écrans lors de l’utilisation de l’interface utilisateur de [!UICONTROL Cloud Manager].

L’une des trois options suivantes s’affiche :

* **Lorsqu’aucun programme n’existe dans Cloud Manager**

   S’il n’existe aucun programme dans votre organisation, votre page d’entrée vous demande de créer votre premier programme, comme le montre la figure ci-dessous.
   ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

* **Lorsque des programmes existent déjà dans Cloud Manager**

   Si des programmes existent déjà dans votre organisation, votre page d’entrée vous demande d’ajouter un autre programme et d’afficher tous vos programmes existants, comme le montre la figure ci-dessous.

   ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

* **Lorsqu’un programme existe et qu’un utilisateur est administrateur système**

   Si des programmes existent déjà dans votre organisation et que vous êtes administrateur système, votre page d’entrée affiche le bouton **Gérer l’accès** avec l’option **Ajouter un programme**, comme dans l’illustration ci-dessous.

   ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

À partir de là, un utilisateur disposant des autorisations appropriées, tel qu’un rôle Propriétaire de l’entreprise dans Cloud Manager, peut sélectionner **Ajouter le programme** pour lancer l’[assistant Ajouter un programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/production-programs/creating-production-program.html?lang=fr#getting-access).

Pour savoir comment ajouter un programme dans Cloud Manager, reportez-vous à la section Création :

* [Programme de production](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/production-programs/creating-production-program.html?lang=en)
* [Programme Sandbox](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sandbox-programs/creating-sandbox-program.html?lang=en)
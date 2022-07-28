---
title: Création d’une newsletter Adobe Experience Manager
description: 'Création d’une newsletter Adobe Experience Manager '
feature: Administering
role: Admin
source-git-commit: f68f5a457bbbcd76681cccabe5a3f4c92b6f8770
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 2%

---


# Création d’une newsletter Adobe Experience Manager {#creating-newsletter}

Avant d’effectuer les étapes présentées ci-dessous, vous devez d’abord [intégrer](/help/sites-cloud/integrating/integrating-campaign-classic.md) Adobe Campaign Classic et AEM as a Cloud Service. Après avoir configuré Adobe Campaign Classic et AEM as a Cloud Service, vous allez maintenant apprendre à créer une newsletter Adobe Experience Manager.

1. Dans l’instance d’auteur AEM, cliquez sur le logo Adobe Experience Manager dans le coin supérieur gauche de la page, puis sélectionnez **Sites**.
1. Sélectionnez Campagne, cliquez sur **Create→Page**.
   ![création de marque](assets/create.png)
1. Sélectionnez Marque et cliquez sur **Suivant**.
1. Saisissez un titre et cliquez sur **Créer** et **Terminé**.
1. Pour créer une page de campagne, accédez à **Campagnes→AdobeDemo→Principal** et cliquez sur **Create→Page**.
   ![page de campagne](assets/campaignpage.png)
1. Sélectionnez le modèle d&#39;opération puis cliquez sur **Suivant** et **Terminé**.
1. Saisissez un titre , cliquez sur **Créer** et **Terminé**.
1. Accédez à **Campaign→AdobeDemo→Principal** et cochez la case CampaignPage . Cliquez sur **Propriétés** en haut à gauche.
   ![propriétés de campagne](assets/propertiesedit.png)
1. Accédez au **Cloud Service** tab :
   * Sélectionnez Adobe Campaign dans la liste déroulante Configurations du Cloud Service .
   * Sélectionnez le nom de votre choix pour la configuration Adobe Campaign.
   * **Enregistrer** et **Fermer**.
1. Pour créer une page de courrier électronique Adobe Campaign Classic, accédez à **Campaign→AdobeDemo→Principal→CampaignPage** et cliquez sur **Create→Page**.
1. Sélectionnez le modèle Adobe Campaign Email (par exemple, AC 6.1) et cliquez sur **Suivant**.
1. Sur la page Créer , saisissez le titre de la newsletter, puis cliquez sur **Créer** et **Terminé**.
1. Accédez à **Campaign→AdobeDemo→Principal→CampaignPage**, cochez la case Campaign Classic et cliquez sur **Modifier** en haut à gauche pour ouvrir la page de courrier électronique.
1. Modifiez la page de newsletter par e-mail de Adobe Campaign Classic selon vos besoins.
1. Cliquez sur le bouton **Informations sur la page** en haut à gauche et cliquez sur **Publier la page**.
1. Sélectionnez la configuration sur laquelle la page doit être publiée. Cliquez sur **Publier**. 
   ![page de publication](assets/publish.png)
1. La page de newsletter a été publiée sur l’instance de publication, ainsi que sur la configuration Adobe Campaign Classic AEM.
   * Désormais, la page de newsletter sera visible dans Adobe Campaign Classic
1. Cliquez sur le bouton Informations sur la page , puis sur **Démarrer le processus**.
1. Sélectionner **Approuver pour Adobe Campaign** comme modèle de workflow, puis cliquez sur l’icône **Démarrer le processus** bouton .
1. Une clause de non-responsabilité s’affiche en haut de la page. Cliquez sur **Terminer** pour confirmer la révision, puis cliquez de nouveau sur **OK**.
1. Cliquez sur **Terminer** et sélectionnez **Approbation de la newsletter** dans la liste déroulante Étape suivante , cliquez sur le bouton **OK** bouton .

## Création d’un destinataire {#creating-recipient}

1. Ouvrez le serveur Adobe Campaign Classic à l’aide de la console cliente Adobe Campaign Classic.
1. Accédez à la vue Explorateur.
1. Dans l’arborescence de gauche, accédez à Profils et cibles et sélectionnez **Destinataires**.
   ![destinataires](assets/recipients.png)
1. Renseignez les Détails du destinataire.
   * Saisissez le Prénom.
   * Saisissez le Nom.
   * Saisissez l’adresse électronique.
   * Cliquez sur **Enregistrer**.

## Création d’une diffusion email dans Adobe Campaign Classic {#create-delivery}

1. Ouvrez le serveur Adobe Campaign Classic à l’aide de la console cliente Adobe Campaign Classic.
1. Accédez à la vue Explorateur.
1. Dans l’arborescence de gauche, sélectionnez **Campaign Management** et sélectionnez **Diffusions**.
1. Dans le coin supérieur droit, cliquez sur **Nouveau**.
1. Sélectionner **Diffusion Email avec AEM contenu** dans la liste déroulante Modèle de diffusion , puis cliquez sur **Continuer**.
1. Cliquez sur le lien De sous Paramètres de l&#39;email.
   * Saisissez l&#39;adresse de l&#39;expéditeur.
   * Saisissez le champ De .
   * Cliquez sur **OK**.
1. Cliquez sur **À** lier puis cliquer sur **Ajouter** sur l’écran de sélection de la cible.
1. Sélectionner **Un destinataire** et cliquez sur **Suivant**.
   ![type de cible](assets/publish.png)
1. Sélectionner le destinataire créé [précédemment](#creating-recipient) et cliquez sur **Terminer**.
1. Le destinataire a été sélectionné. Cliquez sur **OK**.
1. Cliquez sur **Synchroniser**.
1. Sélectionnez la page d’email dans la liste, puis cliquez sur **OK**.
1. Le modèle de courrier électronique est synchronisé. Cliquez sur **Actualiser le contenu** s’il n’est pas chargé.
1. Cliquez sur **Envoyer** pour envoyer l’email.
1. Sur l’écran suivant, sélectionnez **Diffusion dès que possible** puis cliquez sur **Analyser**.
   ![cible de diffusion](assets/deliverytarget.png)
1. Maintenant que la diffusion a été créée, cliquez sur **Confirmer la diffusion** pour commencer à envoyer l’email. Cliquez sur **Oui** pour confirmer.
   ![confirmer la diffusion](assets/confirmdelivery.png)
1. La diffusion a commencé. Cliquez sur **Fermer**.
1. Cliquez sur **Enregistrer** pour enregistrer la diffusion.

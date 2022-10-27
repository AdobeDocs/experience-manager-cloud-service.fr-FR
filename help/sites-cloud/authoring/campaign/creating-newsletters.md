---
title: Créer des newsletters Campaign avec AEM
description: Découvrez comment utiliser AEM as a Cloud Service pour créer des newsletters pouvant être envoyées avec Adobe Campaign Classic.
feature: Authoring
role: User
exl-id: 60a6a9d0-f5e6-424f-b320-dd4943c55d45
source-git-commit: 6196f3fc67dbcfe03a71bb6a0796dd5d1d0f8546
workflow-type: ht
source-wordcount: '1341'
ht-degree: 100%

---


# Créer des newsletters Campaign avec AEM {#creating-newsletters}

Dans ce document, vous apprendrez à utiliser AEM as a Cloud Service pour créer des newsletters qui peuvent être envoyées avec Adobe Campaign Classic.

En tirant parti de l’intégration entre AEM as a Cloud Service et Adobe Campaign Classic, vous pouvez créer vos newsletters à l’aide des puissants outils de création d’AEM. Ensuite, lorsque vous êtes prêt à envoyer votre newsletter, vous pouvez utiliser les fonctionnalités de gestion des destinataires et de distribution de Campaign pour l’envoyer.

## Conditions préalables {#prerequisites}

Avant de pouvoir créer une newsletter avec AEM et l’envoyer avec Campaign, vous devez d’abord [intégrer Adobe Campaign Classic et AEM as a Cloud Service.](/help/sites-cloud/integrating/integrating-campaign-classic.md)

## Créer la structure d’une newsletter {#create-structure}

Le contenu de la newsletter est géré dans AEM comme vous le feriez avec le contenu de votre site. Vous commencez par créer un « site » pour votre contenu. Dans ce « site » vous pouvez regrouper vos newsletters par marque.

1. Connectez-vous à votre instance de création AEM.

1. Sur la page de navigation principale, ouvrez la console **Sites**.

1. Dans une installation standard d’AEM, il y aura un dossier **Campagne** existant. Sélectionnez-le et cliquez sur le bouton **Créer**, puis sur **Page**.

   ![Créer une page](assets/create-page.png)

1. Sélectionnez **Marque** comme modèle de site, puis cliquez sur **Suivant**.

   ![Créer une marque](assets/create-brand.png)

1. Saisissez un **titre** et cliquez sur **Créer** puis sur **Terminé**.

   ![Fournir des détails sur la marque](assets/create-brand-page.png)

Vous disposez désormais d’une structure de contenu de base pour créer vos campagnes.

![Structure du contenu](assets/content-structure.png)

## Créer une campagne {#create-campaign}

Maintenant que vous disposez d’une structure de contenu de base pour votre campagne, vous pouvez créer la campagne elle-même. La campagne sera utilisée pour éventuellement organiser plusieurs newsletters.

1. En utilisant le [mode colonne](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) dans la console sites, sélectionnez la marque que vous avez créée précédemment (dans ce cas, **WKND Escapes**), puis sélectionnez **Zone Principale**, qui a été automatiquement créée pour vous, puis cliquez sur le bouton **Créer** puis, sur **Page**.

   ![Créer une page de campagne](assets/create-campaign-page.png)

1. Sélectionnez **Campagne** comme modèle, puis cliquez sur **Suivant** et sur **Terminé**.

   ![Sélectionner un modèle de campagne](assets/select-campaign-template.png)

1. Saisissez un **Titre** pour la campagne, puis cliquez sur **Créer** et sur **Terminé**.

   ![Titre de la campagne](assets/campaign-title.png)

Vous disposez maintenant d’une campagne dans laquelle vous pouvez créer vos newsletters.

![Structure de la campagne](assets/campaign-structure.png)

## Sélectionner la configuration de la campagne {#campaign-configuration}

AEM peut prendre en charge plusieurs configurations d’intégration. Pour votre nouvelle campagne, vous devez définir les configurations à utiliser pour envoyer le contenu de votre newsletter.

1. En vous servant du [mode colonne](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) de la console Sites, recherchez la campagne que vous avez créée précédemment (dans ce cas, **Campagne d’évasion estivale WKND**), puis sélectionnez-la à l’aide de la case à cocher, ensuite cliquez sur le bouton **Propriétés** de la barre d’outils.

   ![Sélectionner une campagne](assets/select-campaign.png)

1. Dans la fenêtre **Propriétés**, sélectionnez l’onglet **Cloud Service** pour définir l’intégration à utiliser avec cette campagne.

   * Sélectionnez **Adobe Campaign** dans la liste déroulante **Configurations de Cloud Service**.
   * Sélectionnez la configuration de l’intégration Adobe Campaign souhaitée dans la liste déroulante **Adobe Campaign**.
   * Cliquez sur **Enregistrer et fermer**.

   ![Propriétés de configuration de la campagne](assets/campaign-configuration-properties.png)

Votre campagne est maintenant liée à votre intégration Adobe Campaign. Vous êtes prêt à créer une newsletter dans AEM et à l’envoyer avec Adobe Campaign.

## Créer une newsletter {#create-newsletter}

Vous créez et gérez vos newsletters sous la structure de contenu de campagne que vous avez déjà créée et configurée.

1. En vous servant du [mode colonne](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) de la console Sites, recherchez la campagne que vous avez précédemment configurée (dans ce cas, **Campagne d’évasion estivale WKND**), sélectionnez-la, puis cliquez sur le bouton **Créer** et ensuite sur **Page**.

   ![Créer une newsletter](assets/create-newsletter.png)

1. Dans l’assistant de création de page, sélectionnez le modèle **E-mail Adobe Campaign (AC 6.1)** et cliquez sur **Suivant**.

   ![Sélectionner le modèle d’e-mail de campagne](assets/adobe-campaign-email-template.png)

1. Pour l’étape **Propriétés** de l’assistant, saisissez un **Titre** pour la newsletter, cliquez sur **Créer** puis sur **Ouvrir**.

   ![Titre de la newsletter](assets/create-newsletter-wizard-properties.png)

1. Modifiez la page de la newsletter comme vous le feriez pour n’importe quelle autre page de contenu AEM afin de répondre à vos besoins.

Vous disposez désormais d’une newsletter prête à être envoyée avec Adobe Campaign.

## Publier votre newsletter {#publishing-newsletter}

Vous devez publier votre newsletter pour qu’Adobe Campaign puisse l’envoyer.

1. En vous servant du [mode colonne](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) dans la console Sites, recherchez la newsletter que vous avez précédemment créée (dans ce cas, **Première newsletter pour la campagne d’évasion estivale WKND**), sélectionnez-la, puis cliquez sur le bouton **Informations sur la page** en haut à gauche et cliquez sur **Publier la page**.

1. Sélectionnez la ou les configurations pour lesquelles la page doit être publiée, puis cliquez sur **Publier**.

   ![Publier la page](assets/publish.png)

La page de newsletter est maintenant publiée sur l’instance de publication AEM et est visible dans Adobe Campaign Classic. Pour pouvoir la sélectionner dans Adobe Campaign, elle doit être approuvée.

1. Une fois de plus, cliquez sur le bouton **Informations sur la page** pour la newsletter, puis sur **Démarrer le Workflow**.

1. Sélectionnez **Approuver pour Adobe Campaign** en tant que modèle de workflow (en fournissant éventuellement une description) et cliquez sur le bouton **Démarrer le workflow**.

   ![Démarrer le workflow](assets/start-workflow.png)

1. Une bannière s’affiche en haut de l’éditeur de page de la newsletter pour indiquer les étapes suivantes du processus d’approbation. Cliquez sur **Terminer**.

   ![Approuver le workflow](assets/approve-workflow.png)

1. Dans la boîte de dialogue **Terminer l’élément de travail**, sélectionnez **Révision de la newsletter (administrateur)** de la liste déroulante **Étape suivante** puis cliquez sur le bouton **OK**.

   ![Révision de la newsletter](assets/newsletter-review.png)

1. Dans la bannière qui s’affiche en haut de l’éditeur de page de la newsletter, cliquez de nouveau sur **Terminer**.

1. Dans la boîte de dialogue **Terminer l’élément de travail**, sélectionnez **Approbation de la newsletter** dans la liste déroulante **Étape suivante** puis cliquez sur le bouton **OK**.

   ![Approbation de la newsletter](assets/newsletter-approval.png)

1. Lorsque la boîte de dialogue se ferme, la bannière qui s’affichait en haut de l’éditeur de page de la newsletter disparaît, car le workflow d’approbation est terminé.

La newsletter est maintenant publiée dans AEM et approuvée pour une utilisation dans Adobe Campaign.

>[!TIP]
>
>Les étapes de workflow décrites ici sont simplifiées pour illustrer le processus. Dans un flux de travail normal, la création de la newsletter et son approbation fonctionnent normalement selon différents rôles.
>
>Voir le document [Utilisation des workflows](/help/sites-cloud/authoring/workflows/overview.md) pour plus d’informations sur l’utilisation des workflows.

## Créer un destinataire {#creating-recipient}

Pour pouvoir envoyer la newsletter que vous avez créée dans AEM, vous devez d&#39;abord définir vos destinataires dans Adobe Campaign Classic.

1. Connectez-vous à Adobe Campaign Classic à l’aide de la console cliente.

1. Sélectionnez **Outils** -> **Explorateur** dans la barre de menus.

1. Dans l’explorateur, accédez au nœud **Profils et cibles** -> **Destinataires**.

   ![Destinataires](assets/recipients.png)

1. Cliquez sur **Nouveau** dans la barre d&#39;outils et indiquez les détails du destinataire.

   * Prénom
   * Nom
   * Adresse e-mail

1. Cliquez sur **Enregistrer**.

Vous disposez désormais d’un destinataire auquel vous pouvez envoyer votre newsletter à l’aide de Adobe Campaign Classic.

## Créer une diffusion par e-mail {#create-delivery}

La dernière étape consiste à envoyer la newsletter que vous avez créée dans AEM au destinataire que vous avez ajouté dans Adobe Campaign Classic.

1. Connectez-vous à Adobe Campaign Classic à l’aide de la console cliente.

1. Sélectionnez **Outils** -> **Explorateur** dans la barre de menus.

1. Dans l’explorateur, accédez au nœud **Gestion de campagnes** -> **Diffusions** et cliquez sur **Nouveau**.

   ![Diffusion de contenu AEM](assets/delivery-aem-content.png)

1. Dans la boîte de dialogue **Diffusion**, sélectionnez **Diffusion E-mail avec contenu AEM** comme **Modèle de diffusion** dans la liste déroulante, puis cliquez sur **Continuer**.

   ![Diffusion de contenu AEM](assets/aem-content-delivery.png)

1. Dans la section **Paramètres de messagerie**, cliquez sur le lien **De**, saisissez les informations de l’expéditeur, puis cliquez sur **OK**.

   * Adresse de l’expéditeur
   * Champ De

   ![Définir le champ De](assets/delivery-from.png)

1. Dans la section **Paramètres de messagerie**, cliquez sur lien **À** pour ouvrir la boîte de dialogue **Sélectionner la cible** puis cliquez sur **Ajouter**.

   ![Sélectionner la cible](assets/select-target.png)

1. Dans la boîte de dialogue **Sélectionner un élément cible**, sélectionnez **un destinataire** et cliquez sur **Suivant**.

   ![Sélectionner un élément cible](assets/select-target-element.png)

1. À l’aide des filtres, sélectionnez le destinataire que vous avez [précédemment créé](#creating-recipient) et cliquez sur **Terminer**.

   ![Sélectionner un destinataire](assets/select-target-element-recipient.png)

1. De retour dans la boîte de dialogue **Sélectionner la cible**, cliquez sur **OK**.

1. Dans la fenêtre de diffusion, cliquez sur **Synchroniser**.

   ![Synchroniser](assets/synchronize.png)

1. Dans la boîte de dialogue **Synchroniser avec du contenu AEM**, sélectionnez dans la liste la newsletter que vous avez précédemment créée, puis cliquez sur **OK**.

1. Le contenu d’e-mail d’Adobe Campaign est synchronisé avec le contenu de la newsletter que vous avez créé dans AEM.

   * Cliquez sur **Actualiser le contenu** si le contenu n’est pas automatiquement chargé.

1. Cliquez sur **Envoyer** pour envoyer l’e-mail.

1. Dans la boîte de dialogue **Envoyer à la cible de diffusion principale**, sélectionnez **Diffuser dès que possible** et puis cliquez sur **Analyser**.

   ![Analyse des diffusions](assets/delivery-analysis.png)

1. L’étape d’analyse crée la diffusion, combinant le contenu avec les destinataires. Maintenant que la diffusion a été créée, cliquez sur **Confirmer la diffusion** pour envoyer l’e-mail. Cliquez sur **Oui** pour confirmer.

1. La diffusion a commencé. Cliquez sur **Fermer**.

   ![Diffusion](assets/delivering.png)

1. Cliquez sur **Enregistrer** pour enregistrer la diffusion.

Votre newsletter a été envoyée.

>[!TIP]
>
>Cet exemple illustre une diffusion simplifiée de l’envoi d’une newsletter à un seul destinataire. Bien sûr, une diffusion normale contiendrait de nombreux destinataires différents, ce qu’Adobe Campaign rend facile à gérer. Veuillez vous reporter à la section [Documentation Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr) pour plus de détails sur la gestion des diffusions et des destinataires.

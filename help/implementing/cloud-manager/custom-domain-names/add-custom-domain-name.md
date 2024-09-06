---
title: Ajout d’un nom de domaine personnalisé
description: Découvrez comment ajouter un nom de domaine personnalisé à l’aide de Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 27%

---


# Ajout d’un nom de domaine personnalisé {#adding-cdn}

Découvrez comment ajouter un nom de domaine personnalisé à l’aide de Cloud Manager.

## Conditions requises {#requirements}

Renseignez ces exigences avant d’ajouter un nom de domaine personnalisé dans Cloud Manager.

* Vous devez avoir ajouté un certificat SSL de domaine pour le domaine que vous souhaitez ajouter avant d’ajouter un nom de domaine personnalisé comme décrit dans le document [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
* Vous devez disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour ajouter un nom de domaine personnalisé dans Cloud Manager.
* Utilisez le CDN Fastly.

## Où ajouter des noms de domaine personnalisés {#where}

Vous pouvez ajouter un nom de domaine personnalisé à partir de deux emplacements dans Cloud Manager :

* [Dans la page Paramètres du domaine](#adding-cdn-settings)
* [Dans la page Environnements](#adding-cdn-environments)

Lors de l’ajout d’un nom de domaine personnalisé, le domaine est diffusé à l’aide du certificat valide le plus spécifique. Si plusieurs certificats ont le même domaine, la mise à jour la plus récente est choisie. Adobe recommande de gérer les certificats de sorte qu’il n’y ait pas de chevauchement de domaines.

Les étapes décrites dans ce document sont basées sur la méthode Fastly. Si vous avez utilisé un autre CDN, configurez votre domaine avec le CDN que vous avez choisi d’utiliser.

## Ajout d’un nom de domaine personnalisé à partir de la page Paramètres du domaine {#adding-cdn-settings}

Suivez la procédure suivante pour ajouter un nom de domaine personnalisé à partir de la page **Paramètres du domaine**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à l’onglet **Paramètres de domaine** dans le panneau de navigation de gauche.

   ![Fenêtre Paramètres du domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Cliquez sur le bouton **Ajouter un domaine** en haut à droite pour ouvrir la boîte de dialogue **Ajouter un nom de domaine** .

   ![Boîte de dialogue Ajouter un domaine](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Dans l’onglet **Nom de domaine**, saisissez le nom de domaine personnalisé dans le champ **Nom de domaine**.

   >[!NOTE]
   >
   >N’incluez pas `http://`, `https://` ni d’espace lors de la saisie dans votre domaine.

1. Sélectionnez l’**environnement** dont le service est associé au nom de domaine.

1. Sélectionnez le service **Publier** ou **Aperçu**.

1. Sélectionnez le **certificat de domaine SSL** associé au nom de domaine dans la liste déroulante et sélectionnez **Continuer**.

1. L’onglet **Verification** s’affiche.

   ![Vérification des noms de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   * L’onglet **Vérification** décrit les étapes suivantes pour configurer votre nom de domaine personnalisé, qui crée un enregistrement TXT nécessaire.
   * Vous pouvez effectuer cette étape immédiatement (avant de cliquer sur **Créer** dans la boîte de dialogue) ou après avoir cliqué sur **Créer** dans la boîte de dialogue.
   * Les options et les étapes suivantes sont décrites ci-dessous.

1. Cliquez sur **Créer** pour enregistrer le nom de domaine personnalisé dans Cloud Manager.

Lorsque vous sélectionnez **Créer** dans l’assistant **Ajouter un domaine personnalisé**, Cloud Manager déclenche une vérification TXT. Créez l’enregistrement TXT lorsque vous configurez le nom de domaine personnalisé dans Cloud Manager. Toutefois, cette étape n’est pas requise. Pour les vérifications suivantes, vous devez sélectionner activement l’icône **Vérifier à nouveau** en regard de l’état.

Le nom n’est pas actif tant que Cloud Manager n’a pas vérifié que l’entrée TXT est ajoutée. L’état de **Vérifié et déployé** indique une vérification TXT réussie.

* Voir [Ajouter un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus sur les enregistrements TXT.
* Voir [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations sur la manière dont Cloud Manager vérifie le nom de domaine personnalisé et son entrée TXT.

## Étapes suivantes {#next-steps}

Après avoir créé votre nom de domaine personnalisé dans Cloud Manager, ajoutez une entrée TXT pour vérifier la propriété du domaine. Passez au document [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour continuer à configurer votre nom de domaine personnalisé.

## Ajout d’un nom de domaine personnalisé à partir de la page Environnements {#adding-cdn-environments}

Les étapes pour ajouter un nom de domaine personnalisé à partir de la page **Environments** sont les mêmes que lorsque [l’ajout d’un nom de domaine personnalisé à partir de la page Paramètres du domaine](#adding-cdn-settings), mais le point d’entrée diffère. Procédez comme suit pour ajouter un nom de domaine personnalisé à partir de la page **Environnements**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la page **Détails des environnements** pour connaître l’environnement qui vous intéresse.

   ![Saisie d’un nom de domaine sur la page Détails de l’environnement](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Utilisez le tableau **Noms de domaine** pour envoyer le nom de domaine personnalisé.

   1. Entrez le nom de domaine personnalisé.
   1. Sélectionnez le certificat SSL associé à ce nom dans la liste déroulante.
   1. Cliquez sur **+Ajouter**.

   ![Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. La boîte de dialogue **Ajouter le nom de domaine** s’ouvre sur l’onglet **Nom de domaine**. Continuez comme vous le feriez pour [ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine](#adding-cdn-settings).

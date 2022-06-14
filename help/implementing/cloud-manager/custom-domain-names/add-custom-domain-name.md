---
title: Ajout d’un nom de domaine personnalisé
description: Découvrez comment ajouter un nom de domaine personnalisé à l’aide de Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 0febf4b4a59617e6cc4f8414963c4a91fcf8765e
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 29%

---

# Ajout d’un nom de domaine personnalisé {#adding-cdn}

Vous pouvez ajouter un nom de domaine personnalisé à partir de deux emplacements dans Cloud Manager :

* [Dans la page Paramètres du domaine](#adding-cdn-settings)
* [Sur la page Environnements](#adding-cdn-environments)

>[!NOTE]
>
>Un utilisateur doit disposer de la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** rôle pour ajouter un nom de domaine personnalisé dans Cloud Manager

## Ajout d’un nom de domaine personnalisé à partir de la page Paramètres du domaine {#adding-cdn-settings}

Procédez comme suit pour ajouter un nom de domaine personnalisé à partir du **Paramètres de domaine** page.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Environnements** de l’écran **Présentation** page.

1. Cliquez sur **Paramètres de domaine** dans le panneau de navigation de gauche.

   ![Fenêtre Paramètres de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Cliquez sur le bouton **Ajouter un domaine** en haut à droite pour ouvrir la **Ajouter un nom de domaine** boîte de dialogue.

   ![Boîte de dialogue Ajouter un domaine](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Saisissez le nom de domaine personnalisé dans la variable **Nom de domaine** champ .

   >[!NOTE]
   >
   >N’incluez pas `http://`, `https://` ni d’espace lors de la saisie dans votre domaine.

1. Sélectionnez la **Environnement** dont le service sera associé au nom de domaine.

1. Sélectionnez l’une des options suivantes : **Publier** ou **Aperçu** service.

1. Sélectionnez la **Domain SSL Certificate** associé au nom de domaine dans la liste déroulante et sélectionnez **Continuer**.

1. Le **Ajouter un nom de domaine** s’affiche et vous mène au processus de vérification des noms de domaine. Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement. Cliquez sur **Créer**.

   ![Vérification des noms de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Cela est indiqué par l’état **Vérifié et déployé**.

Reportez-vous au document [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur la manière de résoudre les problèmes potentiels.

>[!NOTE]
>
>Le traitement de la vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.
>
>Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau des paramètres de domaine. Reportez-vous au document [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

>[!TIP]
>
>Voir [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus sur les enregistrements TXT.

## Ajout d’un nom de domaine personnalisé à partir de la page Environnements {#adding-cdn-environments}

Procédez comme suit pour ajouter un nom de domaine personnalisé à partir du **Environnements** page.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à **Détails des environnements** pour l’environnement d’intérêt.

   ![Saisie d’un nom de domaine sur la page Détails de l’environnement](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Utilisez la variable **Noms de domaine** pour envoyer le nom de domaine personnalisé.

   1. Entrez le nom de domaine personnalisé.
   1. Sélectionnez le certificat SSL associé à ce nom dans la liste déroulante.
   1. Cliquez sur **+ Ajouter**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Vérifiez les valeurs sélectionnées dans la variable **Ajouter un nom de domaine** , puis cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >Ne pas inclure `http://`, `https://`ou des espaces lors de la saisie dans le nom de domaine.

1. Le **Ajouter un nom de domaine** s’affiche et vous mène au processus de vérification des noms de domaine. Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement. Cliquez sur **Créer**.

   ![Vérification des noms de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Cela est indiqué par l’état **Vérifié et déployé**.

Reportez-vous au document [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur la manière de résoudre les problèmes potentiels.

>[!NOTE]
>
>Le traitement de la vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.
>
>Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau des paramètres de domaine. Reportez-vous au document [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

>[!TIP]
>
>Voir [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus sur les enregistrements TXT.

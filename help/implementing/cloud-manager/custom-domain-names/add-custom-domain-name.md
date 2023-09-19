---
title: Ajout d’un nom de domaine personnalisé
description: Découvrez comment ajouter un nom de domaine personnalisé à l’aide de Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 600288a87e024fbe58ff605a8bcdc61535cc0759
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 74%

---

# Ajout d’un nom de domaine personnalisé {#adding-cdn}

Vous pouvez ajouter un nom de domaine personnalisé à partir de deux emplacements dans Cloud Manager :

* [Dans la page Paramètres du domaine](#adding-cdn-settings)
* [Dans la page Environnements](#adding-cdn-environments)

>[!NOTE]
>
>Un utilisateur doit disposer de la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour ajouter un nom de domaine personnalisé dans Cloud Manager. Vous devez utiliser le réseau de diffusion de contenu Fastly.

## Ajout d’un nom de domaine personnalisé à partir de la page Paramètres du domaine {#adding-cdn-settings}

Suivez la procédure suivante pour ajouter un nom de domaine personnalisé à partir de la page **Paramètres du domaine.** Si vous utilisez un autre réseau de diffusion de contenu que celui fourni le plus rapidement, ces étapes ne fonctionneront pas pour vous et vous devez configurer votre domaine avec le réseau de diffusion de contenu que vous avez configuré.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **Paramètres du domaine** dans le panneau de navigation de gauche.

   ![Fenêtre Paramètres du domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Cliquez sur le bouton **Ajouter un domaine** en haut à droite pour ouvrir la boîte de dialogue **Ajouter un nom de domaine**.

   ![Boîte de dialogue Ajouter un domaine](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Entrez le nom de domaine personnalisé dans le champ **Nom de domaine**.

   >[!NOTE]
   >
   >N’incluez pas `http://`, `https://` ni d’espace lors de la saisie dans votre domaine.

1. Sélectionnez la variable **Environnement** dont le service est associé au nom de domaine.

1. Sélectionnez le service **Publier** ou **Aperçu**.

1. Sélectionnez le **certificat de domaine SSL** associé au nom de domaine dans la liste déroulante et sélectionnez **Continuer**.

1. La boîte de dialogue **Ajouter un nom de domaine** s’affiche et vous mène au processus de vérification des noms de domaine. Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement. Cliquez sur **Créer**.

   ![Vérification des noms de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Cela est indiqué par le statut **Vérifié et déployé**.

Voir [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur la manière de résoudre les problèmes potentiels.

>[!NOTE]
>
>La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.
>
>Cloud Manager vérifie la propriété et met à jour le statut visible dans le tableau des paramètres du domaine. Voir [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

>[!TIP]
>
>Voir [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus sur les enregistrements TXT.

## Ajout d’un nom de domaine personnalisé à partir de la page Environnements {#adding-cdn-environments}

Procédez comme suit pour ajouter un nom de domaine personnalisé à partir de la page **Environnements**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la page **Détails de l’environnement** pour l’environnement qui vous intéresse.

   ![Saisie d’un nom de domaine sur la page Détails de l’environnement](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Utilisez le tableau **Noms de domaine** pour envoyer le nom de domaine personnalisé.

   1. Entrez le nom de domaine personnalisé.
   1. Sélectionnez le certificat SSL associé à ce nom dans la liste déroulante.
   1. Cliquez sur **+ Ajouter**.

   ![Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Vérifiez les valeurs sélectionnées dans la boîte de dialogue **Ajouter le nom de domaine** et cliquez sur **Continuer**.

   ![Fenêtre du nom de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >N’incluez pas de `http://`, de `https://` ni d’espace lors de la saisie du nom de domaine.

1. La boîte de dialogue **Ajouter un nom de domaine** s’affiche et vous mène au processus de vérification des noms de domaine. Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement. Cliquez sur **Créer**.

   ![Vérification des noms de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Cela est indiqué par le statut **Vérifié et déployé**.

Voir [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur la manière de résoudre les problèmes potentiels.

>[!NOTE]
>
>La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.
>
>Cloud Manager vérifie la propriété et met à jour le statut visible dans le tableau des paramètres du domaine. Voir [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

>[!TIP]
>
>Voir [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus sur les enregistrements TXT.

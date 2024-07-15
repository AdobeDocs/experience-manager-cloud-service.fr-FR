---
title: Certificats de domaine validés (DV)
description: Découvrez comment gérer les certificats DV (domaine validé) dans Cloud Manager.
exl-id: 7f2c71b6-15c3-4919-9f51-a3e26d0d48d4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 8%

---

# Certificats de domaine validés (DV) {#domain-validated-certificates}

Découvrez comment gérer les certificats DV (domaine validé) dans Cloud Manager.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le [programme d’adoption précoce.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)

## Présentation {#introduction}

Cloud Manager vous permet de générer et de gérer en libre-service un certificat SSL (DV) validé par domaine. Vous bénéficiez ainsi de la solution la plus rapide, la plus simple et la plus économique pour créer un site web sécurisé destiné à votre entreprise en ligne.

Les certificats validés par domaine sont disponibles pour les programmes [de production et sandbox.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## Ajout d’un domaine personnalisé {#adding-domain}

Pour ajouter un certificat de domaine validé (DV), vous devez d’abord configurer votre domaine personnalisé. Le processus est largement le même que décrit dans le document [Introduction aux noms de domaine personnalisés.](/help/implementing/cloud-manager/custom-domain-names/introduction.md) Cependant, cette fonctionnalité a été légèrement développée.

1. Lors de la vérification du domaine, vous pouvez choisir d’utiliser des certificats gérés par Adobe ou auto-gérés avec le domaine. Sélectionnez **Adobe du certificat géré** pour ajouter un certificat DV ultérieurement.

   ![Choisir Adobe-géré](assets/verify-domain-dialog.png)

1. Pour utiliser un certificat géré par Adobe, vous devez ajouter un enregistrement CNAME à votre DNS comme décrit dans la boîte de dialogue **Vérifier le domaine** .

   ![Ajouter une entrée CNAME](assets/verify-domain-dialog-adobe-managed.png)

1. Une fois le domaine créé, appuyez ou cliquez sur le bouton représentant des points de suspension dans la liste des domaines et sélectionnez **Vérifier** pour vérifier le domaine.

   ![Vérifier le domaine](assets/verify-domain.png)

## Ajout d’un certificat DV {#adding}

Une fois que votre domaine est correctement configuré, pour ajouter un certificat DV, appuyez ou cliquez sur le bouton **Ajouter un certificat SSL** dans la fenêtre Certificats SSL .

![Ajout d’un certificat DC](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. Sélectionnez l’option **Adobe géré (DV)**.
1. Indiquez le nom de domaine dans la liste déroulante **Sélectionner des domaines** .
1. Cliquez ou appuyez sur **Enregistrer**.

Une fois le certificat ajouté avec succès, un avertissement jaune s’affiche dans le nom du certificat, dans la fenêtre **Certificats SSL**.

![Cert DV en attente](assets/pending-dv-certificate.png)

Une fois le certificat émis avec succès, une coche verte s’affiche sur son nom dans la fenêtre **Certificats SSL**.

![Certificat DV émis](assets/issued-dv-certificate.png)

Pour plus d’informations sur l’ajout de certificats SSL et la fenêtre Certificats SSL, consultez le document [Ajout d’un certificat SSL.](add-ssl-certificate.md)

## Ajouter une configuration CDN {#add-cdn}

Cette étape doit être effectuée afin de configurer un domaine avec un protocole SSL à l’aide d’un CDN Fastly.

Pour ajouter une configuration CDN à l’aide de Cloud Manager, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sélectionnez l’onglet **Configurations CDN** et cliquez ou appuyez sur **Ajouter** dans la barre d’outils.

1. Dans la boîte de dialogue **Configurer CDN**, fournissez les informations nécessaires.

   * Sélectionnez l’ **origine**. Il peut s’agir des éléments suivants :
      * Un environnement Cloud Service
      * Un site Edge Delivery Services
   * Sélectionnez votre type CDN.
   * Sélectionnez le domaine.
   * Sélectionnez le certificat SSL.
      * Uniquement requis pour les réseaux de diffusion de contenu gérés par Adobe.

   ![Configuration de la boîte de dialogue CDN](assets/configure-cdn-dialog.png)

>
>
>Pour les réseaux de diffusion de contenu gérés par l’Adobe, lors de l’utilisation de certificats DV, seuls les sites avec validation ACME sont autorisés.

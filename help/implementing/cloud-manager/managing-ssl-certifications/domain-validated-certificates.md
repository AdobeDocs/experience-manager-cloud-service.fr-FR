---
title: Certificats de domaine validés (DV)
description: Découvrez comment gérer les certificats DV (Domain Validé) dans Cloud Manager.
exl-id: 7f2c71b6-15c3-4919-9f51-a3e26d0d48d4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 8%

---

# Certificats de domaine validés (DV) {#domain-validated-certificates}

Découvrez comment gérer les certificats DV (Domain Validé) dans Cloud Manager.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le [programme d’adoption précoce.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)

## Présentation {#introduction}

Cloud Manager vous permet de générer et de gérer en libre-service un certificat SSL (DV) validé par domaine. Vous bénéficiez ainsi de la solution la plus rapide, la plus simple et la plus économique pour créer un site web sécurisé destiné à votre entreprise en ligne.

Les certificats validés par domaine sont disponibles pour les deux [programmes de production et sandbox.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## Ajout d’un domaine personnalisé {#adding-domain}

Pour ajouter un certificat de domaine validé (DV), vous devez d’abord configurer votre domaine personnalisé. Le processus est largement le même que décrit dans le document. [Présentation des noms de domaine personnalisés.](/help/implementing/cloud-manager/custom-domain-names/introduction.md) Toutefois, cette fonctionnalité a été légèrement développée.

1. Lors de la vérification du domaine, vous pouvez choisir d’utiliser des certificats gérés par Adobe ou auto-gérés avec le domaine. Choisir **Adobe du certificat géré** afin d’ajouter un certificat DV ultérieurement.

   ![Choisissez Gestion des Adobes](assets/verify-domain-dialog.png)

1. Pour utiliser un certificat géré par Adobe, vous devez ajouter un enregistrement CNAME à votre DNS, comme décrit dans la section **Vérifier le domaine** boîte de dialogue.

   ![Ajout d’une entrée CNAME](assets/verify-domain-dialog-adobe-managed.png)

1. Une fois le domaine créé, appuyez ou cliquez sur le bouton représentant des points de suspension dans la liste des domaines et sélectionnez **Vérifier** pour vérifier le domaine.

   ![Vérifier le domaine](assets/verify-domain.png)

## Ajout d’un certificat DV {#adding}

Une fois que votre domaine est correctement configuré, pour ajouter un certificat DV, appuyez ou cliquez sur le bouton **Ajout d’un certificat SSL** dans la fenêtre Certificats SSL .

![Ajout d’un certificat DC](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. Sélectionner l’option **Adobe géré (DV)**.
1. Indiquez le nom de domaine dans la variable **Sélectionner des domaines** déroulant.
1. Cliquez ou appuyez sur **Enregistrer**.

Une fois le certificat ajouté avec succès, son nom est associé à un état en attente doté d’un signe d’avertissement jaune. **Certificats SSL** fenêtre.

![Certificat DV en attente](assets/pending-dv-certificate.png)

Une fois le certificat émis avec succès, une coche verte s’affiche dans la zone **Certificats SSL** fenêtre.

![CERT DV émis](assets/issued-dv-certificate.png)

Pour plus d’informations sur l’ajout de certificats SSL et la fenêtre Certificats SSL , consultez le document . [Ajout d’un certificat SSL.](add-ssl-certificate.md)

## Ajouter une configuration CDN {#add-cdn}

Cette étape doit être effectuée afin de configurer un domaine avec un protocole SSL à l’aide d’un CDN Fastly.

Pour ajouter une configuration CDN à l’aide de Cloud Manager, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sélectionnez la variable **Configurations CDN** et cliquez ou appuyez sur **Ajouter** dans la barre d’outils.

1. Dans le **Configuration du réseau de diffusion de contenu** , fournissez les informations nécessaires.

   * Sélectionnez la variable **Origin**. Il peut s’agir des éléments suivants :
      * Un environnement Cloud Service
      * Un site Edge Delivery Services
   * Sélectionnez votre type CDN.
   * Sélectionnez le domaine.
   * Sélectionnez le certificat SSL.
      * Uniquement requis pour les réseaux de diffusion de contenu gérés par Adobe.

   ![Boîte de dialogue Configurer le réseau de diffusion de contenu](assets/configure-cdn-dialog.png)

>
>
>Pour les réseaux de diffusion de contenu gérés par l’Adobe, lors de l’utilisation de certificats DV, seuls les sites avec validation ACME sont autorisés.

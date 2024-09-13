---
title: Ajout d’un certificat SSL
description: Découvrez comment ajouter votre propre certificat SSL ou certificat DV (Domain Validation) à l’aide des outils en libre-service Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 9%

---


# Ajout d’un certificat SSL {#add-ssl-cert}

Découvrez comment ajouter un certificat SSL géré par le client ou un certificat DV (Domain Validation) généré et géré par un Adobe à l’aide des outils en libre-service Cloud Manager.

Voir aussi [Dépannage des erreurs de certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).

## Ajout d’un certificat SSL {#adding-an-ssl-certificate}

La configuration d’un certificat peut prendre quelques jours. Par conséquent, Adobe recommande que le certificat soit configuré bien avant toute date limite ou d’activation.

Veillez à consulter les **exigences de certificat** dans [Introduction à la gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements) pour vous assurer qu’AEM as a Cloud Service prend en charge le certificat que vous souhaitez ajouter.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

>[!NOTE]
>
>Les clients ne sont pas autorisés à télécharger des certificats DV (Domain Validation).

**Pour ajouter un certificat SSL :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.

1. Dans le panneau de navigation de gauche, sous **Services**, cliquez sur **Certificats SSL**. Si le panneau de navigation de gauche ne s’affiche pas comme dans l’image suivante, vous devrez peut-être cliquer sur l’icône représentant un hamburger dans le coin supérieur gauche.

   ![Ajout d’un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Dans le coin supérieur droit de la page, cliquez sur **Ajouter un certificat SSL**.

1. Dans la boîte de dialogue **Ajouter un certificat SSL**, en fonction de [votre cas d’utilisation particulier](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), effectuez l’une des opérations suivantes :

   | | Cas d’utilisation | Étapes |
   | --- | --- | --- |
   | 1 | **Ajout d’un certificat géré par Adobe (DV)** | **Pour ajouter un certificat géré par Adobe (DV) :**<br> a. Sélectionnez le type de certificat **Adobe géré (DV)**.<br>![Ajoutez un certificat DV](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. Dans la liste déroulante **Sélectionner des domaines**, sélectionnez un ou plusieurs domaines à associer au certificat DV.<br> Aucun domaine à sélectionner ? Si tel est le cas, cela signifie que vous devez ajouter un domaine personnalisé. Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Lorsque vous avez terminé d’ajouter un nom de domaine personnalisé, revenez à cette rubrique et recommencez à l’étape 1.<br>d. Passez à l’étape 7. |
   | 2 | **Ajouter un certificat géré par le client (OV/EV)** | **Pour ajouter un certificat géré par le client (OV/EV) :**<br> a. Sélectionnez le type de certificat **Customer managed (OV/EV)**.<br>b. Dans le champ **Certificate name** , saisissez un nom pour votre certificat. Ce champ est fourni à titre d’information uniquement et peut être n’importe quel nom qui vous aide à référencer facilement votre certificat.<br>c. Dans les champs **Certificate**, **Private key** et **Certificate chain** , collez les valeurs requises dans leurs champs respectifs.<br>![Boîte de dialogue Ajouter un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Toutes les erreurs détectées dans les valeurs s’affichent. Avant de pouvoir enregistrer votre certificat, vous devez corriger toutes les erreurs. Pour en savoir plus sur la résolution des erreurs courantes, voir [erreurs de certificat](#certificate-errors) .<br>d. Passez à l’étape 7. |

<!--
    **Add an SSL certificate:**
    1. Select the certificate type **Customer managed (OV/EV)**.
    1. In **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your certificate easily.
    1. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.

        ![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)
  
    Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate errors](#certificate-errors) to learn more about troubleshooting common errors.

    **Add a DV certificate:**
    1. Select the certificate type **Adobe managed (DV)**.

        ![Adding a DC certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

    1. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV certificate.

        No domains to select? If so, it means that you must add a custom domain. See [Add a custom domain](#add-custom-domain). When you are finished, resume the steps from the beginning again. -->

1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Enregistrer**.

   Une fois le certificat émis, une coche verte s’affiche dans la table **SSL Certificates**.

Vous avez maintenant ajouté un certificat SSL fonctionnel pour votre projet. Cette étape est souvent la première à configurer un nom de domaine personnalisé.

* Pour configurer un nom de domaine personnalisé, voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
* Pour en savoir plus sur la mise à jour et la gestion de vos certificats SSL dans Cloud Manager, voir [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

<!--
### Add a custom domain {#add-custom-domain}

Before you can add an Adobe generated and managed Domain Validated (DV) certificate, you must first add a custom domain. The process for doing so is nearly the same as detailed in [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) and [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). However, that functionality is now slightly expanded, as described below.

1. When adding a custom domain name, in the **Verify domain** dialog box, select an **Adobe managed certificate**.

    ![Choose Adobe-managed](assets/verify-domain-dialog.png)

1. In the **Verify domain** dialog box, add a CNAME verification record to your DNS.

    ![Add CNAME entry](assets/verify-domain-dialog-adobe-managed.png)

1. After the domain is created, click the ellipsis button in the list of domains and select **Verify** to verify the domain.

    ![Verify domain](assets/verify-domain.png) 

1. Resume the task [Add a DV certificate](#adding-an-ssl-certificate). -->



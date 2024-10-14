---
title: Ajout d’un certificat SSL
description: Découvrez comment ajouter votre propre certificat SSL ou et Adobe un certificat DV (Domain Validation) géré par à l’aide des outils en libre-service Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f12392075b71b219bf449f585f63561167ddada9
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 4%

---


# Ajout d’un certificat SSL {#add-ssl-cert}

Découvrez comment ajouter votre propre certificat SSL ou un certificat DV (Domain Validation) géré par Adobe à l’aide de Cloud

>[!NOTE]
>
>Si vous utilisez un certificat SSL géré par le client (OV/EV) et un fournisseur CDN géré par le client, vous pouvez ignorer l’ajout d’un certificat SSL et accéder directement à [Ajouter une configuration CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) une fois prêt.

La mise en service d’un certificat peut prendre plusieurs jours. Par conséquent, Adobe vous conseille de configurer votre propre certificat bien avant toute échéance ou date d’activation afin d’éviter tout retard.

Pour en savoir plus sur la mise à jour et la gestion de vos certificats SSL dans Cloud Manager, voir [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

Si vous rencontrez des problèmes lors de l’ajout ou de la gestion de vos certificats, reportez-vous à la section [ Résolution des problèmes liés aux erreurs de certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md).


## Conditions préalables {#prerequisites}

* Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour ajouter un certificat SSL.
* Si vous installez votre propre certificat, reportez-vous à la section **Exigences de certificat** dans [Introduction à la gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements).

## Choix du certificat SSL à ajouter {#which-ssl-to-add}

Après [l&#39;ajout d&#39;un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) dans AEM Cloud Manager, l&#39;étape suivante varie selon que vous avez choisi d&#39;utiliser un certificat SSL géré par Adobe (DV) (recommandé) ou un certificat SSL géré par le client (OV/EV).

* **Pour un certificat SSL géré par Adobe (DV) :**
   * Le processus de validation de domaine est effectué une fois que le domaine personnalisé est ajouté et vérifié dans Cloud Manager.
   * Maintenant, vous devez [ajouter un certificat SSL géré par Adobe (DV)](#add-adobe-managed-ssl-cert).
Une fois ajouté à Cloud Manager, attendez que l’Adobe vous envoie et installe le certificat SSL DV en votre nom.
   * Lorsque le certificat est actif, votre domaine personnalisé est prêt à l’emploi.

* **Pour un certificat SSL géré par un client (OV/EV) :**

   * Obtenez votre certificat SSL OV/EV auprès d’une autorité de certification. Pour plus d’informations, consultez les [exigences relatives aux certificats SSL OV/EV gérés par le client](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements).
   * Après l’acquisition du certificat, [ajoutez les détails](#add-customer-manage-ssl-cert) du certificat SSL géré par le client (OV/EV) dans Cloud Manager.
   * Une fois ajouté, le nom de domaine personnalisé est marqué comme vérifié et le certificat SSL est appliqué.

Dans les deux cas, une fois le certificat vérifié et installé, le domaine personnalisé peut être utilisé en toute sécurité dans votre environnement. Veillez à [vérifier régulièrement l’état du domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) dans l’interface de Cloud Manager pour vérifier que tout fonctionne comme prévu.

Voir aussi [Présentation des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md).

## Ajout d’un certificat SSL géré par Adobe (DV) {#add-adobe-managed-ssl-cert}

Vous avez besoin d’aide pour choisir d’utiliser un certificat SSL géré par un Adobe (recommandé) ou un certificat SSL géré par le client avec votre domaine ? Voir [Choix du certificat SSL à ajouter](#which-ssl-to-add)

**Pour ajouter un certificat SSL géré par Adobe (DV) :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.

1. Sous l’en-tête **Services**, cliquez sur ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

   ![Ajout d’un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Dans le coin supérieur droit de la page Certificats SSL, cliquez sur **Ajouter un certificat SSL**.

1. Dans la boîte de dialogue **Ajouter un certificat SSL**, en fonction de [votre cas d’utilisation particulier](#which-ssl-to-add), sélectionnez **Adobe géré (DV)**.

   ![Ajout d’un certificat DV](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. Dans le champ **Certificate name** , saisissez un nom à associer au certificat SSL DV.

1. Dans la liste déroulante **Sélectionner des domaines**, sélectionnez un ou plusieurs domaines vérifiés à associer au certificat SSL DV.
   * Aucun domaine à sélectionner ? Si tel est le cas, vous devez d’abord ajouter un nom de domaine personnalisé et vous assurer qu’il est vérifié avant de pouvoir ajouter un certificat SSL.
   * Consultez [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
   * Lorsque vous avez terminé d’ajouter un nom de domaine personnalisé, revenez à cette rubrique et recommencez à l’étape 1.

1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Enregistrer**.

   Une fois le certificat SSL émis, il s’affiche avec une coche verte Valide dans la table **SSL Certificates**.

Vous avez maintenant ajouté un certificat SSL DV géré par Adobe pour votre projet. Cette étape est souvent la première à configurer un nom de domaine personnalisé.

Vous êtes maintenant prêt à ajouter une [configuration CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Ajout d’un certificat SSL géré par le client (OV/ED) {#add-customer-managed-ssl-cert}

<!-- IF THIS TOPIC GET UPDATED, REMEMBER TO UPDATE THE STEPS ALSO IN THE "MANAGE SSL CERTIFICATES TOPIC TOO -->

Vous avez besoin d’aide pour choisir d’utiliser un certificat SSL géré par un Adobe (recommandé) ou un certificat SSL géré par le client avec votre domaine ? Voir [Choix du certificat SSL à ajouter](#which-ssl-to-add)

**Pour ajouter un certificat SSL géré par le client (OV/EV) :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.

1. Sous l’en-tête **Services**, cliquez sur ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

   ![Ajout d’un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Dans le coin supérieur droit de la page Certificats SSL, cliquez sur **Ajouter un certificat SSL**.

1. Dans la boîte de dialogue **Ajouter un certificat SSL**, en fonction de [votre cas d’utilisation particulier](#which-ssl-to-add), sélectionnez **Customer managed (OV/EV)**.

1. Dans le champ **Certificate name** , saisissez un nom pour votre certificat.
Ce champ est fourni à titre d’information uniquement et peut être n’importe quel nom qui vous aide à référencer facilement votre certificat SSL.

1. Dans les champs **Certificate**, **Private key** et **Certificate chain**, copiez les valeurs requises de votre certificat SSL OV ou EV et collez-les dans leurs champs respectifs dans la boîte de dialogue.

   Toutes les erreurs détectées dans les valeurs s’affichent. Avant de pouvoir enregistrer votre certificat, vous devez corriger toutes les erreurs. Pour en savoir plus sur la résolution des erreurs courantes, voir [erreurs de certificat](#certificate-errors) .

   ![Boîte de dialogue Ajouter un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)|

1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Enregistrer**.

   >[!NOTE]
   >
   >* Si vous avez sélectionné **certificat géré par le client** tout en [ajoutant un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), le domaine est vérifié ***après*** l’ajout et l’enregistrement du certificat SSL géré par le client (OV/EV). Voir aussi [Vérification de l’état d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to).

   Une fois le certificat SSL émis, il s’affiche avec une coche verte vérifiée dans la table **SSL Certificates**.

Vous avez maintenant ajouté un certificat SSL fonctionnel pour votre projet. Cette étape est souvent la première à configurer un nom de domaine personnalisé.

Vous êtes maintenant prêt à ajouter une [configuration CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).























<!--
## Add an SSL certificate {#add-ssl-cert}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate program.
1. On the **[My Programs](/help/implementing/cloud-manager/navigation.md#my-programs)** console, select the program.
1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to reveal the side menu. 
1. Under the **Services** heading, click ![Lock closed icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificates**. 

   ![Adding an SSL certificate](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Near the upper-right corner of the SSL Certificates page, click **Add SSL Certificate**.

1. In the **Add SSL certificate** dialog box, based on [your particular use case](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), do one of the following:

    | | Use case | Steps |
    | --- | --- | --- |
    | 1 | **Add an Adobe managed (DV) certificate** | **To add an Adobe managed (DV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Adobe managed (DV)**.<br>![Add a DV certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. In the **Certificate name** field, enter a name you want associated with the certificate.<br>c. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV SSL certificate.<br>No domains to select? If so, it means that you must first add a custom domain name and ensure it is verified before you can add an SSL certificate. See [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). When you are finished adding a custom domain name, return to this topic and begin at step 1 again.<br>d. Continue to step 7. |
    | 2 | **Add a customer managed (OV/EV) certificate** | **To add a customer managed (OV/EV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Customer managed (OV/EV)**.<br>b. In the **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your SSL certificate easily.<br>c. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.<br>![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate Errors](#certificate-errors) to learn more about troubleshooting common errors.<br>d. Continue to step 7. | 

1. In the lower-right corner of the dialog box, click **Save**.

    >[!NOTE]
    >
    >* If you selected **Adobe managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified with the added certificate when the custom domain is added. 
    >
    >* If you selected **Customer managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified ***after*** the customer managed (OV/EV) SSL certificate is added and saved. See also [Check the status of a custom domain name](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to).

    After the SSL certificate is successfully issued, it is displayed with a green verified check mark in the **SSL Certificates** table. 

    You now have added a working SSL certificate for your project. This step is often the first to set up a custom domain name. 
    

* To learn about updating and managing your SSL certificates in Cloud Manager, see [Manage SSL certificates](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

* If you are having issues adding or managing your certificates, see [Troubleshoot SSL certificate errors](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md). -->

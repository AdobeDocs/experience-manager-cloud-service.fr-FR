---
title: Ajout d’un certificat SSL
description: Découvrez comment ajouter votre propre certificat SSL ou certificat DV (Domain Validation) à l’aide des outils en libre-service Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: fcde1f323392362d826f9b4a775e468de9550716
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 23%

---


# Ajout d’un certificat SSL

Découvrez comment ajouter un certificat SSL géré par le client ou un certificat DV (Domain Validation) généré et géré par un Adobe à l’aide des outils en libre-service Cloud Manager.


## Ajout d’un certificat SSL ou DV {#adding-an-ssl-certificate}

La configuration d’un certificat peut prendre quelques jours. Par conséquent, Adobe recommande que le certificat soit configuré bien avant toute date limite ou d’activation.

Veillez à consulter les **exigences de certificat** dans [Introduction à la gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) pour vous assurer qu’AEM as a Cloud Service prend en charge le certificat que vous souhaitez ajouter.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

>[!NOTE]
>
>Les clients ne sont pas autorisés à télécharger des certificats DV (Domain Validation).

**Pour ajouter un certificat SSL ou DV :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.

1. Dans le panneau de navigation de gauche, sous **Services**, cliquez sur **Certificats SSL**. Si le panneau de navigation de gauche ne s’affiche pas comme dans l’image suivante, vous devrez peut-être cliquer sur l’icône représentant un hamburger dans le coin supérieur gauche.

   ![Ajout d’un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Dans le coin supérieur droit de la page, cliquez sur **Ajouter un certificat SSL**.

1. Dans la boîte de dialogue **Ajouter un certificat SSL**, en fonction de votre cas d’utilisation spécifique, effectuez l’une des opérations suivantes :

   | Cas d’utilisation | Étapes |
   | --- | --- |
   | **Ajout d’un certificat géré par Adobe (DV)** | **Pour ajouter un certificat géré par Adobe (DV) :**<br> a. Sélectionnez le type de certificat **Adobe géré (DV)**.<br>![Ajoutez un certificat DV](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. Dans la liste déroulante **Sélectionner des domaines**, sélectionnez un ou plusieurs domaines à associer au certificat DV.<br> Aucun domaine à sélectionner ? Si tel est le cas, cela signifie que vous devez ajouter un domaine personnalisé. Voir [Ajout d’un domaine personnalisé](#add-custom-domain). Lorsque vous avez terminé d’ajouter un nom de domaine personnalisé, revenez à cette rubrique et recommencez à l’étape 1.<br>d. Passez à l’étape 7. |
   | **Ajouter un certificat géré par le client (OV/EV)** | **Pour ajouter un certificat géré par le client (OV/EV) :**<br> a. Sélectionnez le type de certificat **Customer managed (OV/EV)**.<br>b. Dans le champ **Certificate name** , saisissez un nom pour votre certificat. Ce champ est fourni à titre d’information uniquement et peut être n’importe quel nom qui vous aide à référencer facilement votre certificat.<br>c. Dans les champs **Certificate**, **Private key** et **Certificate chain** , collez les valeurs requises dans leurs champs respectifs.<br>![Boîte de dialogue Ajouter un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Toutes les erreurs détectées dans les valeurs s’affichent. Avant de pouvoir enregistrer votre certificat, vous devez corriger toutes les erreurs. Pour en savoir plus sur la résolution des erreurs courantes, voir [erreurs de certificat](#certificate-errors) .<br>d. Passez à l’étape 7. |

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

1. Dans le coin inférieur droit de la boîte de dialogue, cliquez sur **Enregistrer**.

   Une fois le certificat émis, une coche verte s’affiche, comme dans l’image ci-dessus.

   ![Certificat DV émis](assets/issued-dv-certificate.png)

### Ajout d’un domaine personnalisé {#add-custom-domain}

Avant d’ajouter un certificat DV (Domain Validated) généré et géré par un Adobe, vous devez d’abord ajouter un domaine personnalisé. Le processus pour ce faire est presque le même que décrit dans [Introduction aux noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md) et [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Toutefois, cette fonctionnalité est maintenant légèrement développée, comme décrit ci-dessous.

1. Lors de l’ajout d’un nom de domaine personnalisé, dans la boîte de dialogue **Vérifier le domaine**, sélectionnez un **Adobe du certificat géré**.

   ![Choisir Adobe-géré](assets/verify-domain-dialog.png)

1. Dans la boîte de dialogue **Vérifier le domaine**, ajoutez un enregistrement de vérification CNAME à votre DNS.

   ![Ajouter une entrée CNAME](assets/verify-domain-dialog-adobe-managed.png)

1. Une fois le domaine créé, cliquez sur le bouton représentant des points de suspension dans la liste des domaines et sélectionnez **Vérifier** pour vérifier le domaine.

   ![Vérifier le domaine](assets/verify-domain.png)

1. Reprenez la tâche [Ajouter un certificat DV](#adding-an-ssl-certificate).

### Dépannage des erreurs de certificat {#certificate-errors}

Certaines erreurs peuvent se produire si un certificat n’est pas installé correctement ou ne répond pas aux exigences de Cloud Manager.

+++

* **Ordre de certificat correct**

  La raison la plus courante de l’échec du déploiement d’un certificat est que les certificats intermédiaires ou de chaîne ne sont pas dans le bon ordre.

  Les fichiers de certificat intermédiaires doivent se terminer par le certificat racine ou le certificat le plus proche de la racine. Ils doivent être dans l’ordre descendant du certificat `main/server` à la racine.

  Vous pouvez déterminer l’ordre de vos fichiers intermédiaires à l’aide de la commande suivante.

  ```shell
  openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout
  ```

  Vous pouvez vérifier que la clé privée et le certificat `main/server` correspondent à l’aide des commandes suivantes.

  ```shell
  openssl x509 -noout -modulus -in certificate.pem | openssl md5
  ```

  ```shell
  openssl rsa -noout -modulus -in ssl.key | openssl md5
  ```

  >[!NOTE]
  >
  >La sortie de ces deux commandes doit être exactement la même. Si vous ne parvenez pas à trouver une clé privée correspondante pour votre certificat `main/server`, vous devez recréer le certificat en générant une nouvelle CSR et/ou en demandant un certificat mis à jour à votre fournisseur SSL.

+++

+++

* **Supprimer les certificats du client**

  Lors de l’ajout d’un certificat, si vous recevez une erreur similaire à celle-ci :

  ```text
  The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
  ```

  Vous avez probablement inclus le certificat client dans la chaîne de certificats. Assurez-vous que la chaîne ne contient pas le certificat client et réessayez.

+++

+++

* **Stratégie de certificat**

  Si l’erreur suivante s’affiche, veuillez vérifier la politique de votre certificat.

  ```text
  Certificate policy must conform with EV or OV, and not DV policy.
  ```

  Les valeurs OID intégrées identifient normalement les stratégies de certificat. La génération d’un certificat dans du texte et la recherche de l’OID révèlent la stratégie du certificat.

  Vous pouvez générer les détails de votre certificat sous forme de texte à l’aide de l’exemple suivant comme guide.

  ```text
  openssl x509 -in 9178c0f58cb8fccc.pem -text
  certificate:
      Data:
         Version: 3 (0x2)
         Serial Number:
             91:78:c0:f5:8c:b8:fc:cc
         Signature Algorithm: sha256WithRSAEncryption
         Issuer: C = US, ST = Arizona, L = Scottsdale, O = "GoDaddy.com, Inc.", OU = http://certs.godaddy.com/repository/, CN = Go Daddy Secure Certificate Authority - G2
          Validity
              Not Before: Nov 10 22:55:36 2021 GMT
              Not After : Dec  6 15:35:06 2022 GMT
          Subject: C = US, ST = Colorado, L = Denver, O = Alexandra Alwin, CN = adobedigitalimpact.com
          Subject Public Key Info:
  ...
  ```

  Le modèle OID dans le texte définit le type de politique du certificat.

  | Modèle | Politique | Possible dans Cloud Manager |
  |---|---|---|
  | `2.23.140.1.1` | EV | Oui |
  | `2.23.140.1.2.2` | OV | Oui |
  | `2.23.140.1.2.1` | DV | Non |

  À l’aide de `grep` ping pour les modèles OID dans le texte du certificat de sortie, vous pouvez confirmer votre politique de certificat.

  ```shell
  # "EV Policy"
  openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.1" -B5
  
  # "OV Policy"
  openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.2" -B5
  
  # "DV Policy - Not Accepted"
  openssl x509 -in certificate.pem -text grep "Policy: 2.23.140.1.2.1" -B5
  ```

+++

+++

* **Dates de validité du certificat**

  Cloud Manager s’attend à ce que le certificat SSL soit valide pendant au moins 90 jours à compter de la date actuelle. Vérifiez la validité de la chaîne de certificats.

+++

## Étapes suivantes {#next-steps}

Vous avez maintenant ajouté un certificat SSL fonctionnel pour votre projet. Cette étape est souvent la première à configurer un nom de domaine personnalisé.

* Pour configurer un nom de domaine personnalisé, voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
* Pour en savoir plus sur la mise à jour et la gestion de vos certificats SSL dans Cloud Manager, voir [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

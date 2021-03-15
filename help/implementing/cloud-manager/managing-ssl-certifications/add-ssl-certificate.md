---
title: Ajout d’un certificat SSL – Gestion des certificats SSL
description: Ajout d’un certificat SSL – Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 100%

---


# Ajout d’un certificat SSL {#adding-an-ssl-certificate}

>[!NOTE]
>AEM as a Cloud Service n’accepte que les certificats OV (validation d’organisation) ou EV (validation étendue). Les certificats DV (Domain Validation) ne sont pas acceptés. De plus, tout certificat doit être de type TLS X.509, délivré par une autorité de certification approuvée (CA) et doté d’une clé privée RSA 2 048 bits correspondante.

La mise en service d’un certificat prend quelques jours et il est recommandé que le certificat soit mis en service plusieurs mois à l’avance. Consultez [Obtention d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) pour plus d’informations.

## Format de certificat {#certificate-format}

Les fichiers SSL doivent être au format PEM pour être installés sur Cloud Manager. Les extensions de fichier courantes au format PEM incluent `.pem,`.`crt`, `.cer` et `.cert`.

Procédez comme suit pour convertir le format de vos fichiers SSL au format PEM :

* Convertir PFX en PEM

   `openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

* Convertir P7B en PEM

   `openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

* Convertir DER en PEM

   `openssl x509 -inform der -in certificate.cer -out certificate.pem`

## Points importants {#important-considerations}

* Un utilisateur doit avoir le rôle Propriétaire de l’entreprise ou Responsable du déploiement pour pouvoir installer un certificat SSL dans Cloud Manager.

* À tout moment, Cloud Manager autorise un maximum de 10 certificats SSL qui peuvent être associés à un ou plusieurs environnements sur l’ensemble de votre programme, même si un certificat a expiré. L’interface utilisateur de Cloud Manager permet toutefois d’installer jusqu’à 50 certificats SSL dans le programme avec cette contrainte.

## Ajout d’un certificat {#adding-a-cert}

Procédez comme suit pour ajouter un certificat :

1. Connectez-vous à Cloud Manager.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Cliquez sur **Certificats SSL** dans le menu de navigation de gauche. Un tableau contenant les détails de tout certificat SSL existant s’affiche sur cet écran.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Cliquez sur **Ajouter le certificat SSL** pour ouvrir la boîte de dialogue **Ajouter le certificat SSL**.

   * Entrez un nom pour votre certificat dans **Nom du certificat**. Cela peut être n’importe quel nom qui vous aide à référencer facilement votre certificat.
   * Collez le **certificat**, la **clé privée** et la **chaîne de certificat** dans leurs champs respectifs. Utilisez l’icône Coller située à droite de la zone de saisie.
Les trois champs ne sont pas facultatifs et doivent être renseignés.

      ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)


      >[!NOTE]
      >Toutes les erreurs détectées s’affichent. Vous devez corriger toutes les erreurs avant de pouvoir enregistrer votre certificat. Consultez [Erreurs de certificat](#certificate-errors) pour en savoir plus sur la résolution des erreurs courantes.

1. Cliquez sur **Enregistrer** pour envoyer votre certificat. Celui-ci s’affiche dans une nouvelle ligne du tableau.

   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

## Erreurs de certificat {#certificate-errors}

### Ordre de certificat correct {#correct-certificate-order}

La raison la plus courante de l’échec du déploiement d’un certificat est que les certificats intermédiaires ou de chaîne ne sont pas dans le bon ordre. Plus précisément, les fichiers de certificat intermédiaire doivent se terminer par le certificat racine ou le certificat le plus proche de la racine et se trouver dans l’ordre décroissant entre le certificat `main/server` et la racine.

Vous pouvez déterminer l’ordre de vos fichiers intermédiaires à l’aide de la commande suivante :

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

Vous pouvez vérifier que la clé privée et le certificat `main/server` correspondent à l’aide des commandes suivantes :

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>La sortie de ces deux commandes doit être exactement la même. Si vous ne parvenez pas à trouver une clé privée correspondant à votre certificat `main/server`, vous devrez entrer à nouveau la clé du certificat en générant un nouveau CSR et/ou en demandant un certificat mis à jour à votre fournisseur SSL.

### Dates de validité du certificat {#certificate-validity-dates}

Cloud Manager s’attend à ce que le certificat SSL soit valide pendant au moins 90 jours à l’avenir. : Vérifiez la validité de la chaîne de certificats.

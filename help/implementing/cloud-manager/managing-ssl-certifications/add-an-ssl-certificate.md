---
title: Ajouter un certificat SSL - Gestion des certificats SSL
description: Ajouter un certificat SSL - Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: 9026befea071777dd2b97c16cdc5c623c86c1c8d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---


# Ajouter un certificat SSL {#adding-an-ssl-certificate}

>[!NOTE]
>La mise en service d’un certificat prend quelques jours et il est recommandé que le certificat soit mis en service plusieurs mois à l’avance. Accédez à Comment obtenir un certificat SSL pour en savoir plus.INSERTION DE LIEN

## Format de certificat {#certificate-format}

Les fichiers SSL doivent être au format PEM pour être installés sur Cloud Manager. Les extensions de fichier courantes au format PEM sont .pem, .crt, .cer et .cert.

Pour convertir le format de vos fichiers SSL au format PEM, procédez comme suit :

1. Convertir PFX en PEM

`openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes`

1. Convertir P7B en PEM

`openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer`

1. Convertir DER en PEM

`openssl x509 -inform der -in certificate.cer -out certificate.pem`

## Ajouter votre certificat {#adding-certificate}

>[!NOTE]
>* Un utilisateur doit se trouver dans le rôle Business Owner ou Deployment Manager pour pouvoir installer un certificat SSL dans Cloud Manager.
>* À tout moment, Cloud Manager autorise un maximum de 5 certificats SSL qui peuvent être associés à un ou plusieurs environnements sur votre Programme, même si un certificat a expiré. L’interface utilisateur de Cloud Manager permet toutefois d’installer jusqu’à 50 certificats SSL dans le programme avec cette contrainte.


1. Connectez-vous à Cloud Manager.
1. Accédez à l’écran Environnements à partir de la page Aperçu.
1. Accédez à l’écran Certificats SSL à partir du menu de navigation de gauche. Un tableau contenant les détails de tout certificat SSL existant s&#39;affiche sur cet écran.INSERTION D&#39;IMAGE
1. Sélectionnez le bouton **Ajouter le certificat** pour lancer un assistant.
1. Entrez un nom pour votre certificat. Il peut s’agir de n’importe quel nom qui vous aide à référencer facilement votre certificat.
1. Collez le contenu du certificat, de la clé privée et de la chaîne dans leurs champs respectifs. Utilisez l’icône Coller située à droite de la zone de saisie.
1. Sélectionnez **Enregistrer**.

   >[!NOTE]
   >Toutes les erreurs détectées s&#39;affichent. Vous devez corriger toutes les erreurs avant de pouvoir enregistrer votre certificat. Consultez la section Certificat INSERT LINK Errors (Erreurs de lien INSERT de certificat) pour en savoir plus sur la résolution des erreurs courantes.

   Une fois que vous avez envoyé votre certificat, il s’affichera sous la forme d’une nouvelle ligne dans le tableau.

## Erreurs de certificat {#certificate-errors}

### Corriger l&#39;ordre de certificat {#correct-certificate-order}

La raison la plus courante de l’échec du déploiement d’un certificat est que les certificats intermédiaires ou de chaîne ne sont pas dans le bon ordre. Plus précisément, les fichiers de certificat intermédiaire doivent se terminer par le certificat racine ou le certificat le plus proche de la racine et se trouver dans un ordre décroissant entre le `main/server` certificat et la racine.

Vous pouvez déterminer l’ordre de vos fichiers intermédiaires à l’aide de la commande suivante :

`openssl crl2pkcs7 -nocrl -certfile $CERT_FILE | openssl pkcs7 -print_certs -noout`

Vous pouvez vérifier que la clé privée et le `main/server` certificat correspondent à l’aide des commandes suivantes :

`openssl x509 -noout -modulus -in certificate.pem | openssl md5`

`openssl rsa -noout -modulus -in ssl.key | openssl md5`

>[!NOTE]
>La sortie de ces deux commandes doit être exactement la même. Si vous ne parvenez pas à trouver une clé privée correspondante à votre `main/server` certificat, vous devrez la resynchroniser en générant un nouveau CSR et/ou en demandant un certificat mis à jour à votre fournisseur SSL.

### Dates de validité du certificat {#certificate-validity-dates}

Cloud Manager s’attend à ce que le certificat SSL soit valide pendant au moins 90 jours à l’avenir.

Vérifier la validité de la chaîne de certificats.

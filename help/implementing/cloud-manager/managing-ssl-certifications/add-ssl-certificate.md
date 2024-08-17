---
title: Ajout d’un certificat SSL
description: Découvrez comment ajouter votre propre certificat SSL à l’aide des outils en libre-service de Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 64aa010c3d840adad9e1ab6040a6d80c07cd8455
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 47%

---


# Ajout d’un certificat SSL {#adding-an-ssl-certificate}

Découvrez comment ajouter votre propre certificat SSL à l’aide des outils en libre-service de Cloud Manager.

>[!TIP]
>
>La configuration d’un certificat peut prendre quelques jours. Adobe recommande donc que le certificat soit configuré bien avant toute date limite ou d’activation.

## Exigences de certificat {#certificate-requirements}

Vérifiez les **conditions requises pour les certificats** dans [Introduction à la gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) pour vous assurer qu’AEM as a Cloud Service prend en charge le certificat que vous souhaitez ajouter.

## Ajout d’un certificat {#adding-a-cert}

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à l’écran **Environnements** à partir de la page **Vue d’ensemble**.

1. Dans le panneau de navigation de gauche, sous **Services**, cliquez sur **Certificats SSL**. (Si nécessaire, vous devrez peut-être cliquer sur l’icône en forme de hamburger dans le coin supérieur gauche pour accéder au panneau de navigation. Un tableau contenant les détails de tout certificat SSL existant s’affiche.

   ![Ajout d’un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Cliquez sur **Ajouter un certificat SSL** pour ouvrir la boîte de dialogue **Ajouter un certificat SSL** .

   * Entrez un nom pour votre certificat dans **Nom du certificat**. Ce champ est fourni à titre d’information uniquement et peut être n’importe quel nom qui vous aide à référencer facilement votre certificat.
   * Collez les valeurs du **certificat**, de la **clé privée** et de la **chaîne de certificat** dans leurs champs respectifs. Les trois champs sont obligatoires.

   ![Boîte de dialogue Ajouter un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * Toutes les erreurs détectées dans les valeurs s’affichent. Avant de pouvoir enregistrer votre certificat, vous devez corriger toutes les erreurs.
Voir [Certificate errors](#certificate-errors) pour en savoir plus sur la résolution des erreurs courantes.

1. Cliquez sur **Enregistrer**.

![Certificat SSL enregistré](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)Votre certificat s’affiche désormais sous la forme d’une nouvelle ligne dans le tableau, comme dans l’image ci-dessus.

>[!NOTE]
>
>L’utilisateur ou l’utilisatrice doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour pouvoir installer un certificat SSL dans Cloud Manager.

## Erreurs de certificat {#certificate-errors}

Certaines erreurs peuvent se produire si un certificat n’est pas installé correctement ou répond aux exigences de Cloud Manager.

### Correction de l’ordre du certificat {#correct-certificate-order}

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

### Suppression des certificats du client {#client-certificates}

Lors de l’ajout d’un certificat, si vous recevez une erreur similaire à celle-ci :

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Vous avez probablement inclus le certificat client dans la chaîne de certificats. Assurez-vous que la chaîne ne contient pas le certificat client et réessayez.

### Stratégie de certificat {#certificate-policy}

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

### Dates de validité du certificat {#certificate-validity-dates}

Cloud Manager s’attend à ce que le certificat SSL soit valide pendant au moins 90 jours à compter de la date actuelle. Vérifiez la validité de la chaîne de certificats.

## Étapes suivantes {#next-steps}

Félicitations. Vous disposez désormais d’un certificat SSL fonctionnel pour votre projet. Cette étape est souvent la première à configurer un nom de domaine personnalisé.

* Pour configurer un nom de domaine personnalisé, voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
* Pour en savoir plus sur la mise à jour et la gestion de vos certificats SSL dans Cloud Manager, voir [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

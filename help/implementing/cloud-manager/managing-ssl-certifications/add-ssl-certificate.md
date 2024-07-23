---
title: Ajout d’un certificat SSL
description: Découvrez comment ajouter votre propre certificat SSL à l’aide des outils en libre-service de Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 07696086644d52199bada102e9aee163d868c9c0
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 69%

---

# Ajout d’un certificat SSL {#adding-an-ssl-certificate}

Découvrez comment ajouter votre propre certificat SSL à l’aide des outils en libre-service de Cloud Manager.

>[!TIP]
>
>La configuration d’un certificat peut prendre quelques jours. Adobe recommande donc que le certificat soit configuré bien en avance.

## Conditions requises du certificat {#certificate-requirements}

Consultez la section **Exigences de certificat** du document [Introduction à la gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements) pour vous assurer que le certificat que vous souhaitez ajouter est pris en charge par AEM as a Cloud Service.

## Ajout d’un certificat {#adding-a-cert}

Pour ajouter un certificat à l’aide de Cloud Manager, procédez comme suit.

1. Se connecter à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionner l’organisation appropriée

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **SSL Certificates** dans le panneau de navigation de gauche. Un tableau contenant les détails de tout certificat SSL existant s’affiche sur l’écran principal.

   ![Ajout d’un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-1.png)

1. Cliquez sur **Ajouter un certificat SSL** pour ouvrir la boîte de dialogue **Ajouter un certificat SSL** .

   * Entrez un nom pour votre certificat dans **Nom du certificat**.
      * Il s’agit d’un nom uniquement à titre d’information, il peut s’agir de n’importe quel nom qui vous aide à référencer facilement votre certificat.
   * Collez les valeurs du **certificat**, de la **clé privée** et de la **chaîne de certificat** dans leurs champs respectifs. Les trois champs sont obligatoires.

   ![Boîte de dialogue Ajouter un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)

   * Toutes les erreurs détectées s’affichent.
      * Vous devez corriger toutes les erreurs avant de pouvoir enregistrer votre certificat.
      * Consultez la section [Erreurs de certificat](#certificate-errors) pour en savoir plus sur la résolution des erreurs courantes.

1. Cliquez sur **Enregistrer** pour enregistrer votre certificat.

Une fois enregistré, votre certificat s’affiche sous la forme d’une nouvelle ligne dans le tableau.

![Certificat SSL enregistré](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)

>[!NOTE]
>
>L’utilisateur ou l’utilisatrice doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour pouvoir installer un certificat SSL dans Cloud Manager.

## Erreurs de certificat {#certificate-errors}

Certaines erreurs peuvent se produire si un certificat n’est pas installé correctement ou répond aux exigences de Cloud Manager.

### S’assurer d’un formatage correct des lignes {#line-formatting}

Lors du collage de valeurs pour **Certificate**, **Private key** et **Certificate chain**, les nouvelles lignes ne doivent être qu’après BEGIN CERTIFICATE et avant END CERTIFICATE. En d’autres termes, les valeurs collées doivent être construites comme suit :

* `-----BEGIN CERTIFICATE-----` doit apparaître sur sa propre ligne.
* `-----END CERTIFICATE-----` doit apparaître sur sa propre ligne.
* Le contenu du certificat doit apparaître sur sa propre ligne sous la forme d&#39;une longue chaîne **sans nouvelles lignes** entre `-----BEGIN CERTIFICATE-----` et `-----END CERTIFICATE-----`.

### Suppression de certificats du client {#client-certificates}

Lors de l’ajout d’un certificat, si vous recevez une erreur similaire à celle-ci :

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Vous avez probablement inclus le certificat client dans la chaîne de certificats. Assurez-vous que la chaîne ne contient pas le certificat client et réessayez.

### Politique de certificat {#certificate-policy}

Si l’erreur suivante s’affiche, veuillez vérifier la politique de votre certificat.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

Normalement, les politiques de certificat sont identifiées par des valeurs OID incorporées. La génération d’un certificat dans du texte et la recherche de l’OID révèleront la politique du certificat.

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

### Ordre de certificat correct {#correct-certificate-order}

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

### Dates de validité du certificat {#certificate-validity-dates}

Cloud Manager s’attend à ce que le certificat SSL soit valide pendant au moins 90 jours à compter de la date actuelle. Vérifiez la validité de la chaîne de certificats.

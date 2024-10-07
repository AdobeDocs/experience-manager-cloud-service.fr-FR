---
title: Résolution des problèmes liés aux certificats SSL
description: Découvrez comment résoudre les problèmes liés aux certificats SSL en identifiant les causes courantes afin que vous puissiez maintenir des connexions sécurisées.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1017f84564cedcef502b017915d370119cd5a241
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 33%

---


# Résolution des problèmes liés aux certificats SSL {#certificate-problems}

Découvrez comment résoudre les problèmes liés aux certificats SSL en identifiant les causes courantes afin que vous puissiez maintenir des connexions sécurisées.

+++**Certificat non valide**

## Certificat non valide {#invalid-certificate}

Cette erreur se produit car le client a utilisé une clé privée chiffrée et a fourni la clé au format DER.

+++

+++**La clé privée doit être au format PKCS 8**

## La clé privée doit être au format PKCS 8. {#pkcs-8}

Cette erreur se produit car le client a utilisé une clé privée chiffrée et a fourni la clé au format DER.

+++

+++**Ordre de certificat correct**

## Correction de l’ordre du certificat {#certificate-order}

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

+++**Supprimer les certificats du client**

## Suppression des certificats du client {#client-certificates}

Lors de l’ajout d’un certificat, si vous recevez une erreur similaire à celle-ci :

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Vous avez probablement inclus le certificat client dans la chaîne de certificats. Assurez-vous que la chaîne ne contient pas le certificat client et réessayez.

+++

+++**Stratégie de certificat**

## Stratégie de certificat {#policy}

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

Validité des +++**certificats

## Validité des certificats {#validity}

Cloud Manager s’attend à ce que le certificat SSL soit valide pendant au moins 90 jours à compter de la date actuelle. Vérifiez la validité de la chaîne de certificats.

+++

+++**Un certificat SAN incorrect est appliqué à mon domaine

## Un certificat SAN incorrect est appliqué à mon domaine {#wrong-san-cert}

Supposons que vous souhaitiez lier `dev.yoursite.com` et `stage.yoursite.com` à votre environnement hors production et `prod.yoursite.com` à votre environnement de production.

Pour configurer le réseau de diffusion de contenu pour ces domaines, vous avez besoin d’un certificat installé pour chacun d’eux. Vous devez donc installer un certificat qui couvre `*.yoursite.com` pour vos domaines hors production et un autre qui couvre également `*.yoursite.com` pour vos domaines de production.

Cette configuration est valide. Cependant, lorsque vous mettez à jour l’un des certificats, car les deux certificats couvrent la même entrée SAN, le CDN installe le certificat le plus récent sur tous les domaines applicables, ce qui peut sembler inattendu.

Bien que cela puisse être inattendu, il ne s’agit pas d’une erreur et il s’agit du comportement standard du réseau de diffusion de contenu sous-jacent. Si vous disposez de deux certificats SAN ou plus qui couvrent la même entrée de domaine SAN, si ce domaine est couvert par un certificat et que l’autre est mis à jour, ce dernier sera installé pour le domaine.

+++

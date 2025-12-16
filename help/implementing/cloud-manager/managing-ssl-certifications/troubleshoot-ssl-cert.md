---
title: Résolution des problèmes liés aux certificats SSL
description: Découvrez comment résoudre les problèmes liés aux certificats SSL en identifiant les causes courantes afin de pouvoir maintenir des connexions sécurisées.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 8fb8f708-51a5-46d0-8317-6ce118a70fab
source-git-commit: 7d86ec9cd7cc283082da44111ad897a5aa548f58
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 33%

---

# Résolution des problèmes liés aux certificats SSL {#certificate-problems}

Découvrez comment résoudre les problèmes liés aux certificats SSL en identifiant les causes courantes afin de pouvoir maintenir des connexions sécurisées.

+++**Certificat non valide**

## Certificat non valide {#invalid-certificate}

Cette erreur se produit, car le client a utilisé une clé privée chiffrée et a fourni la clé au format DER.

+++

+++**La clé privée doit être au format PKCS 8**

## La clé privée doit être au format PKCS 8. {#pkcs-8}

Cette erreur se produit, car le client a utilisé une clé privée chiffrée et a fourni la clé au format DER.

+++

+++**Ordre de certificat correct**

## Ordre de certificat correct {#certificate-order}

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
>La sortie de ces deux commandes doit être exactement la même. Si vous ne parvenez pas à trouver une clé privée correspondant à votre certificat `main/server`, vous devez entrer à nouveau la clé du certificat en générant un nouveau CSR et/ou en demandant un certificat mis à jour à votre fournisseur SSL.

+++ 

+++**Supprimer les certificats clients**

## Supprimer les certificats clients {#client-certificates}

Lors de l’ajout d’un certificat, si vous recevez une erreur similaire à ce qui suit :

```text
The Subject of an intermediate certificate must match the issuer in the previous certificate. The SKI of an intermediate certificate must match the AKI of the previous certificate.
```

Vous avez probablement inclus le certificat client dans la chaîne de certificats. Assurez-vous que la chaîne n’inclut pas le certificat client, puis réessayez.

+++

+++**Politique de certificat**

## Politique de certificat {#policy}

Si l’erreur suivante s’affiche, veuillez vérifier la politique de votre certificat.

```text
Certificate policy must conform with EV or OV, and not DV policy.
```

Les valeurs OID intégrées identifient normalement les politiques de certificat. La génération d’un certificat dans du texte et la recherche de l’OID révèlent la politique du certificat.

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

+++Validité du certificat

## Validité du certificat {#validity}

Cloud Manager s’attend à ce que le certificat SSL soit valide pendant au moins 90 jours à compter de la date actuelle. Vérifiez la validité de la chaîne de certificats.

+++

+++Un certificat SAN incorrect est appliqué à mon domaine

## Un certificat SAN incorrect est appliqué à mon domaine {#wrong-san-cert}

Supposons que vous souhaitiez lier `dev.yoursite.com` et `stage.yoursite.com` à votre environnement hors production et `prod.yoursite.com` à votre environnement de production.

Pour configurer le réseau CDN pour ces domaines, vous avez besoin d’un certificat installé pour chacun. Vous installez donc un certificat qui couvre les `*.yoursite.com` pour vos domaines hors production et un autre qui couvre également les `*.yoursite.com` pour vos domaines de production.

Cette configuration est valide. Cependant, lorsque vous mettez à jour l’un des certificats, les deux certificats couvrent toujours la même entrée SAN. Par conséquent, le réseau CDN installe le certificat le plus récent sur tous les domaines applicables, ce qui peut sembler inattendu.

Bien que ce scénario puisse être inattendu, il ne s’agit pas d’une erreur et il s’agit du comportement standard du réseau CDN sous-jacent. Si plusieurs certificats SAN couvrent la même entrée de domaine SAN, le réseau de diffusion de contenu installe le certificat le plus récemment mis à jour pour ce domaine. Cette situation se produit même lorsqu’un autre certificat couvre déjà la même entrée de domaine.

+++

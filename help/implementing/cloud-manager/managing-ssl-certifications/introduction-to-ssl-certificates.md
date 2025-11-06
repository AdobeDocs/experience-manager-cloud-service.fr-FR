---
title: Introduction à la gestion des certificats SSL
description: Découvrez les outils en libre-service que Cloud Manager vous fournit pour installer et gérer des certificats SSL.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 17%

---


# Introduction à la gestion des certificats SSL{#introduction}

Découvrez les outils en libre-service fournis par Cloud Manager pour installer et gérer des certificats SSL (Secure Socket Layer).

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Gérer des certificats SSL"
>abstract="Découvrez comment Cloud Manager propose des outils en libre-service pour installer et gérer des certificats SSL afin de sécuriser votre site pour les utilisateurs et utilisatrices. Cloud Manager utilise un service de plateforme TLS pour gérer les certificats SSL et les clés privées détenus par la clientèle et obtenus auprès d’autorités de certification tierces."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Affichage, mise à jour et remplacement d’un certificat SSL"
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Vérification du statut d’un certificat SSL"

## Que sont les certificats SSL ? {#overview}

Les entreprises et les organisations utilisent des certificats SSL (Secure Socket Layer) pour sécuriser leurs sites web et permettre à leurs clients de leur faire confiance. Pour utiliser le protocole SSL, un serveur web requiert un certificat SSL.

Lorsqu’une entité, telle qu’une organisation ou une entreprise, demande un certificat à une autorité de certification (AC), celle-ci effectue un processus de vérification. Ce processus peut aller de la vérification du contrôle des noms de domaine à la collecte de documents d&#39;enregistrement des sociétés et de contrats d&#39;abonnés. Une fois les renseignements d&#39;une entité vérifiés, l&#39;AC signe sa clé publique à l&#39;aide de la clé privée de l&#39;AC. Comme toutes les principales autorités de certification possèdent des certificats racine dans les navigateurs web, le certificat de l’entité est lié par une *chaîne de confiance* et le navigateur web le reconnaît comme un certificat approuvé.

>[!IMPORTANT]
>
>Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ces pièces doivent être obtenues auprès d&#39;une autorité de certification, une organisation tierce de confiance. Certaines autorités de certification connues incluent *DigiCert*, *Let&#39;s Encrypt*, *GlobalSign*, *Entrust* et *Verisign*.

## Gestion des certificats avec Cloud Manager {#cloud-manager}

Cloud Manager propose des outils en libre-service pour installer et gérer les certificats SSL, en assurant la sécurité du site pour vos utilisateurs. Cloud Manager prend en charge deux modèles de gestion des certificats.

| | Modèle | Description |
| --- | --- | --- |
| A | **[Certificat SSL géré par Adobe (DV)](#adobe-managed)** | Cloud Manager permet aux utilisateurs de configurer des certificats DV (Validation de domaine) fournis par Adobe pour une configuration rapide de domaine. |
| B | **[Certificat SSL géré par le client (OV/EV)](#customer-managed)** | Cloud Manager propose un service Platform TLS (Transport Layer Security) pour vous permettre de gérer les certificats SSL OV et EV que vous possédez et les clés privées d’autorités de certification tierces, telles que *Let’s Encrypt*. |

Les deux modèles offrent les fonctionnalités générales suivantes pour gérer vos certificats :

* Chaque environnement Cloud Manager peut utiliser plusieurs certificats.
* Une clé privée peut émettre plusieurs certificats SSL.
* Le service Platform TLS achemine les requêtes vers le service CDN du client en fonction du certificat SSL utilisé pour s’arrêter et du service CDN qui héberge ce domaine.

>[!IMPORTANT]
>
>[Pour ajouter et associer un domaine personnalisé à un environnement](/help/implementing/cloud-manager/custom-domain-names/introduction.md) vous devez disposer d’un certificat SSL valide couvrant le domaine.

### Certificats SSL gérés par Adobe (DV) {#adobe-managed}

Les certificats DV constituent le niveau de certification SSL le plus élémentaire et sont souvent utilisés à des fins de test ou pour sécuriser des sites web avec un chiffrement de base. Les certificats DV sont disponibles dans les [ programmes de production et les programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

Une fois le certificat DV créé, Adobe le renouvelle automatiquement tous les trois mois, sauf s’il est supprimé.

>[!IMPORTANT]
>
>Si votre environnement utilise des certificats SSL (DV) avec une validation CNAME, sachez que la suppression de l’enregistrement CNAME avant le renouvellement automatique du certificat peut entraîner l’échec du renouvellement. La suppression peut entraîner l’expiration du certificat et l’interruption du service. Pour éviter ce problème, assurez-vous que l’enregistrement CNAME reste en place tout au long du processus de renouvellement complet. Le processus de renouvellement repose sur la présence de l’enregistrement CNAME pour la validation de la propriété du domaine.

### Certificats SSL gérés par le client (OV/EV) {#customer-managed}

Les certificats OV et EV offrent des informations validées par l’autorité de certification. Ces informations permettent aux utilisateurs d’évaluer si le propriétaire du site web, l’expéditeur de l’e-mail ou le signataire numérique du code ou des documents PDF est digne de confiance. Les certificats DV ne permettent pas cette vérification de propriété.

OV et EV offrent en outre ces fonctionnalités par rapport aux certificats DV dans Cloud Manager.

* Plusieurs environnements peuvent utiliser un certificat OV/EV. En d’autres termes, il peut être ajouté une fois, mais utilisé plusieurs fois.
* Chaque certificat OV/EV contient généralement plusieurs domaines.
* Cloud Manager accepte les certificats OV/EV génériques pour un domaine.

>[!TIP]
>
>Si vous disposez de plusieurs domaines personnalisés, il se peut que vous ne souhaitiez pas charger un certificat à chaque fois que vous ajoutez un nouveau domaine. Dans ce cas, il est préférable d’obtenir un seul certificat couvrant plusieurs domaines.

#### Conditions requises pour les certificats SSL OV/EV gérés par le client {#requirements}

Si vous choisissez d’ajouter votre propre certificat SSL géré par le client, il doit répondre aux exigences mises à jour suivantes :

* Les certificats DV (Domain Validation) et les certificats auto-signés ne sont pas pris en charge.
* Le certificat doit être conforme aux stratégies OV (validation d’organisation) ou EV (validation étendue).
* Le certificat doit être un certificat TLS X.509 émis par une autorité de certification approuvée (CA).
* Les types de clés cryptographiques pris en charge sont les suivants :

   * RSA 2048 bits, prise en charge standard.
Les clés RSA de plus de 2 048 bits (telles que les clés RSA de 3 072 bits ou de 4 096 bits) ne sont pas prises en charge pour le moment.
   * Clés de courbe elliptique (EC) `prime256v1` (`secp256r1`) et `secp384r1`
   * Certificats ECDSA (Elliptic Curve Digital Signature Algorithm). Ces certificats sont recommandés par Adobe plutôt que par RSA pour améliorer les performances, la sécurité et l’efficacité.

* Les certificats doivent être formatés correctement pour réussir la validation. Les clés privées doivent être au format `PKCS#8`.

>[!NOTE]
>Si votre entreprise a besoin de se conformer à la réglementation en utilisant des clés RSA 3 072 bits, l’alternative recommandée par Adobe consiste à utiliser des certificats ECDSA (`secp256r1` ou `secp384r1`).


#### Bonnes pratiques relatives à la gestion des certificats

* **Éviter les certificats qui se chevauchent :**

   * Pour garantir une gestion fluide des certificats, évitez de déployer des certificats qui se chevauchent et qui correspondent au même domaine. Par exemple, la présence d’un certificat avec caractère générique (*.example.com) à côté d’un certificat spécifique (dev.example.com) peut prêter à confusion.
   * La couche TLS donne la priorité au certificat le plus spécifique et récemment déployé.

  Exemples de scénarios :

   * Le « certificat de développement » couvre les `dev.example.com` et est déployé en tant que mappage de domaine pour les `dev.example.com`.
   * Le « certificat d’évaluation » couvre les `stage.example.com` et est déployé en tant que mappage de domaine pour les `stage.example.com`.
   * Si le « certificat d’évaluation » est déployé/mis à jour *après* « certificat de développement », il sert également les requêtes de `dev.example.com`.

     Pour éviter de tels conflits, assurez-vous que les certificats sont soigneusement délimités par rapport aux domaines prévus.

* **Certificats génériques :**

  Bien que les certificats génériques (par exemple, `*.example.com`) soient pris en charge, ils ne doivent être utilisés que lorsque cela est nécessaire. En cas de chevauchement, le certificat le plus spécifique est prioritaire. Par exemple, le certificat spécifique sert `dev.example.com` au lieu du caractère générique (`*.example.com`).

* **Validation et dépannage :**
Avant de tenter d’installer un certificat avec Cloud Manager, Adobe vous recommande de valider l’intégrité de votre certificat localement à l’aide d’outils tels que `openssl`. Par exemple :

  `openssl verify -untrusted intermediate.pem certificate.pem`


<!--
>[!NOTE]
>
>If two certificates cover the same domain are installed, the one that is more exact is applied.
>
>For example, if your domain is `dev.adobe.com` and you have one certificate for `*.adobe.com` and another for `dev.adobe.com`, the more specific one (`dev.adobe.com`) is used.
-->

#### Format des certificats gérés par le client {#certificate-format}

Les fichiers des certificats SSL doivent être au format PEM pour être installés avec Cloud Manager. Les extensions de fichier courantes du format PEM incluent `.pem,`. `crt`, `.cer` et `.cert`.

Les commandes suivantes `openssl` peuvent être utilisées pour convertir des certificats non-PEM.

* Convertir PFX en PEM

  ```shell
  openssl pkcs12 -in certificate.pfx -out certificate.cer -nodes
  ```

* Convertir P7B en PEM

  ```shell
  openssl pkcs7 -print_certs -in certificate.p7b -out certificate.cer
  ```

* Convertir DER en PEM

  ```shell
  openssl x509 -inform der -in certificate.cer -out certificate.pem
  ```

## Limitation du nombre de certificats SSL installés {#limitations}

À tout moment, Cloud Manager prend en charge jusqu’à 70 certificats installés. Ces certificats peuvent être associés à un ou plusieurs environnements dans votre programme et inclure également des certificats expirés.

Si vous avez atteint la limite, vérifiez vos certificats et envisagez de supprimer tous les certificats expirés. Vous pouvez également regrouper plusieurs domaines dans le même certificat, car un certificat peut couvrir plusieurs domaines (jusqu’à 100 SAN).

## En savoir plus {#learn-more}

Un utilisateur disposant des autorisations nécessaires peut utiliser Cloud Manager pour gérer les certificats SSL d’un programme. Pour plus d’informations sur l’utilisation de ces fonctionnalités, consultez les documents suivants.

* [Ajouter un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [Gestion des certificats SSL ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->


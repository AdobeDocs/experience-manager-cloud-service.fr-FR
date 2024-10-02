---
title: Introduction à la gestion des certificats SSL
description: Découvrez les outils en libre-service que Cloud Manager vous permet d’installer et de gérer des certificats SSL.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 484f7b0fd8917902d028434451964dd9df3e3445
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 23%

---


# Introduction à la gestion des certificats SSL{#introduction}

Découvrez les outils en libre-service que Cloud Manager vous permet d’installer et de gérer des certificats SSL.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Gérer des certificats SSL"
>abstract="Découvrez comment Cloud Manager vous fournit des outils en libre-service pour installer et gérer des certificats SSL afin de sécuriser votre site pour les utilisateurs et utilisatrices. Cloud Manager utilise un service de plateforme TLS pour gérer les certificats SSL et les clés privées détenus par la clientèle et obtenus auprès d’autorités de certification tierces."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Affichage, mise à jour et remplacement d’un certificat SSL"
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Vérification du statut d’un certificat SSL"

## Que sont les certificats SSL ? {#overview}

Les entreprises et les organisations utilisent des certificats SSL (Secure Socket Layer) pour sécuriser leurs sites web et permettre à leurs clients d’y faire confiance. Pour utiliser le protocole SSL, un serveur web nécessite un certificat SSL.

Lorsqu’une entité, telle qu’une organisation ou une entreprise, demande un certificat à une autorité de certification, l’autorité de certification termine un processus de vérification. Ce processus peut aller de la vérification du contrôle des noms de domaine à la collecte des documents d’enregistrement de la société et des contrats d’abonné. Une fois les informations d’une entité vérifiées, l’autorité de certification signe sa clé publique à l’aide de la clé privée de l’autorité de certification. Comme toutes les principales autorités de certification disposent de certificats racine dans les navigateurs Web, le certificat de l’entité est lié par une *chaîne de confiance* et le navigateur Web le reconnaît comme un certificat de confiance.

>[!IMPORTANT]
>
>Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Elles doivent être obtenues auprès d’une autorité de certification, une organisation tierce approuvée. Parmi les autorités de certification connues, citons *DigiCert*, *Let&#39;s Encrypt*, *GlobalSign*, *Entrust* et *Verisign*.

## Gestion des certificats avec Cloud Manager {#cloud-manager}

Cloud Manager propose des outils en libre-service pour installer et gérer les certificats SSL, assurant ainsi la sécurité du site de vos utilisateurs. Cloud Manager prend en charge deux modèles de gestion des certificats.

| | Modèle | Description |
| --- | --- | --- |
| 1 | **[Adobe du certificat géré (DV)](#adobe-managed)** | Cloud Manager permet aux utilisateurs de configurer les certificats DV (Domain Validation) fournis par Adobe pour une configuration rapide du domaine. |
| 2 | **[Certificat géré par le client (OV/EV)](#customer-managed)** | Cloud Manager propose une plateforme TLS (Transport Layer Security) pour vous permettre de gérer les certificats SSL OV et EV que vous possédez, ainsi que les clés privées des autorités de certification tierces, telles que *Let&#39;s Encrypt*. |

Les deux modèles offrent les fonctions générales suivantes.

* Chaque environnement Cloud Manager peut utiliser plusieurs certificats.
* Une clé privée peut émettre plusieurs certificats SSL.
* Le service Platform TLS achemine les requêtes vers le service CDN du client en fonction du certificat SSL utilisé pour s’arrêter et du service CDN qui héberge ce domaine.

>[!IMPORTANT]
>
>[Pour ajouter et associer un domaine personnalisé à un environnement, ](/help/implementing/cloud-manager/custom-domain-names/introduction.md) vous devez disposer d’un certificat SSL valide qui couvre le domaine.

### Certificats gérés d’Adobe {#adobe-managed}

Les certificats DV sont le niveau de certification SSL le plus élémentaire et sont souvent utilisés à des fins de test ou pour sécuriser des sites web avec un chiffrement de base. Les certificats DV sont disponibles dans les [programmes de production et les programmes sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

Une fois le certificat DV créé, Adobe le renouvelle automatiquement tous les trois mois, sauf s’il est supprimé.

### Certificats gérés par le client {#customer-managed}

Les certificats OV et EV offrent des informations validées par l’autorité de certification. Ces informations aident les utilisateurs à évaluer si le propriétaire du site web, l’expéditeur d’emails ou le signataire numérique de documents de code ou de PDF peuvent être approuvés. Les certificats DV ne permettent pas cette vérification de propriété.

OV et EV offrent en outre ces fonctionnalités par rapport aux certificats DV dans Cloud Manager.

* Plusieurs environnements peuvent utiliser un certificat OV/EV.
   * En d’autres termes, il peut être ajouté une seule fois, mais utilisé plusieurs fois.
* Chaque certificat OV/EV contient généralement plusieurs domaines.
* Cloud Manager accepte les certificats OV/EV génériques pour un domaine.

>[!TIP]
>
>Si vous disposez de plusieurs domaines personnalisés et que vous ne souhaitez pas télécharger de certificat chaque fois que vous ajoutez un domaine, vous pouvez bénéficier d’un seul certificat comportant plusieurs domaines.

>[!NOTE]
>
>Si deux certificats couvrent le même domaine sont installés, celui qui est le plus exact est appliqué.
>
>Par exemple, si votre domaine est `dev.adobe.com` et que vous disposez d’un certificat qui couvre `*.adobe.com` et d’un certificat qui couvre `dev.adobe.com`, ce dernier sera appliqué car il est plus exact.

#### Conditions requises pour les certificats gérés par le client {#requirements}

Si vous choisissez de télécharger votre propre certificat EV/OV, il doit répondre aux exigences suivantes.

* AEM as a Cloud Service accepte les certificats conformes à la politique OV (Validation de l’organisation) ou EV (Validation étendue).
   * Cloud Manager ne prend pas en charge le chargement de vos propres certificats DV (Domain Validation).
* Tout certificat doit être un certificat TLS X.509 d’une autorité de certification approuvée avec une clé privée RSA 2 048 bits correspondante.
* Les certificats auto-signés ne sont pas acceptés.

#### Format des certificats gérés par le client {#certificate-format}

Les fichiers des certificats SSL doivent être au format PEM pour être installés avec Cloud Manager. `.pem,` sont les extensions de fichier courantes du format PEM. `crt`, `.cer` et `.cert`.

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

À tout moment, Cloud Manager autorise un maximum de 50 certificats SSL installés. Ces certificats peuvent être associés à un ou plusieurs environnements dans votre programme et inclure également les certificats expirés.

Si vous avez atteint la limite, passez en revue vos certificats et envisagez de supprimer tout certificat expiré. Vous pouvez également regrouper plusieurs domaines dans le même certificat, car un certificat peut couvrir plusieurs domaines (jusqu’à 100 SAN).

## En savoir plus {#learn-more}

Un utilisateur disposant des autorisations nécessaires peut utiliser Cloud Manager pour gérer les certificats SSL d’un programme. Pour plus d’informations sur l’utilisation de ces fonctionnalités, consultez les documents suivants.

* [Ajouter un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) <!--CQDOC-21758, #4 -->
* [Gérer les certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md) <!--CQDOC-21758, #4 -->


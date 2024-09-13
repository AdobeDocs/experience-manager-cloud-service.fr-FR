---
title: Présentation des certificats SSL
description: Découvrez comment Cloud Manager vous fournit des outils en libre-service pour installer les certificats SSL.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 35%

---


# Présentation des certificats SSL{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Gestion des certificats SSL"
>abstract="Découvrez comment Cloud Manager vous fournit des outils en libre-service pour installer et gérer des certificats SSL afin de sécuriser votre site pour les utilisateurs et utilisatrices. Cloud Manager utilise un service de plateforme TLS pour gérer les certificats SSL et les clés privées détenus par la clientèle et obtenus auprès d’autorités de certification tierces."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Affichage, mise à jour et remplacement d’un certificat SSL"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates" text="Vérification du statut d’un certificat SSL"


Cloud Manager propose des outils en libre-service pour installer et gérer des certificats SSL (Secure Socket Layer), ce qui garantit la sécurité de site à vos utilisateurs. Les deux cas d’utilisation suivants sont pris en charge :

<!-- CQDOC-21758, #1 -->

| | Cas d’utilisation | Description |
| --- | --- | --- |
| 1 | **Adobe du certificat géré (DV)** | Cloud Manager permet aux utilisateurs de configurer un certificat DV (Domain Validation) provenant d’Adobe pour une configuration de domaine rapide. Les certificats DV sont le niveau de certification SSL le plus élémentaire et sont souvent utilisés à des fins de test ou pour sécuriser des sites web avec un chiffrement de base. Les certificats DV sont disponibles dans les [programmes de production et les programmes sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md). Une fois le certificat DV créé, Adobe le renouvelle automatiquement tous les trois mois, sauf s’il est supprimé. |
| 2 | **Certificat géré par le client (OV/EV)** | Cloud Manager utilise une plateforme TLS (Transport Layer Security) pour gérer les certificats SSL détenus par le client et les clés privées des autorités de certification tierces, telles que *Let&#39;s Encrypt*. |

>[!NOTE]
>
>Les clients ne sont pas autorisés à télécharger des certificats DV (Domain Validation).


## Présentation des certificats SSL {#certificates}

Les entreprises et les organisations utilisent des certificats SSL pour sécuriser leurs sites web et permettre à leurs clients d’y faire confiance. Pour utiliser le protocole SSL, un serveur web nécessite un certificat SSL.

Lorsqu’une entité, telle qu’une organisation ou une entreprise, demande un certificat à une autorité de certification, l’autorité de certification termine un processus de vérification. Ce processus peut aller de la vérification du contrôle des noms de domaine à la collecte des documents d’enregistrement de la société et des contrats d’abonné. Une fois les informations d’une entité vérifiées, l’autorité de certification signe sa clé publique à l’aide de la clé privée de l’autorité de certification. Comme toutes les principales autorités de certification disposent de certificats racine dans les navigateurs Web, le certificat de l’entité est lié par une *chaîne de confiance* et le navigateur Web le reconnaît comme un certificat de confiance.

>[!IMPORTANT]
>
>Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ces éléments doivent être obtenus auprès d’une autorité de certification, une organisation tierce de confiance. Parmi les autorités de certification connues, citons *DigiCert*, *Let&#39;s Encrypt*, *GlobalSign*, *Entrust* et *Verisign*.

Cloud Manager respecte les options d’utilisation suivantes en matière de certificat SSL client.

* Plusieurs environnements peuvent utiliser un certificat SSL. En d’autres termes, il peut être ajouté une seule fois, mais utilisé plusieurs fois.
* Chaque environnement Cloud Manager peut utiliser plusieurs certificats.
* Une clé privée peut émettre plusieurs certificats SSL.
* Chaque certificat contient généralement plusieurs domaines.
* Le service Platform TLS achemine les requêtes vers le service CDN du client en fonction du certificat SSL utilisé pour s’arrêter et du service CDN qui héberge ce domaine.
* AEM as a Cloud Service accepte les certificats SSL génériques pour un domaine.

AEM as a Cloud Service ne prend en charge que les sites sécurisés `https`. Les clients qui disposent de plusieurs domaines personnalisés ne souhaitent pas charger de certificat chaque fois qu’ils ajoutent un domaine. Ces clients et clientes obtiennent un certificat comportant plusieurs domaines.

## Exigences de certificat SSL {#requirements}

* AEM as a Cloud Service accepte les certificats conformes à la politique OV (Validation de l’organisation), EV (Validation étendue) ou DV (Validation de domaine). <!-- CQDOC-21758, #2 -->
* Tout certificat doit être un certificat TLS X.509 d’une autorité de certification approuvée avec une clé privée RSA 2 048 bits correspondante.
* Les certificats auto-signés ne sont pas acceptés.

Les certificats OV et EV offrent des informations validées par l’autorité de certification. Ces informations aident les utilisateurs à évaluer si le propriétaire du site web, l’expéditeur d’emails ou le signataire numérique de documents de code ou de PDF peuvent être approuvés. Les certificats DV ne permettent pas cette vérification de propriété.

### Format de certificat SSL géré par le client {#certificate-format}

<!-- CQDOC-21758, #3 -->

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


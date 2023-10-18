---
title: Introduction à la gestion des certificats SSL
description: Découvrez comment Cloud Manager vous fournit des outils en libre-service pour installer les certificats SSL.
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 100%

---


# Introduction à la gestion des certificats SSL{#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_sslcert"
>title="Gestion des certificats SSL"
>abstract="Découvrez comment Cloud Manager vous fournit des outils en libre-service pour installer et gérer des certificats SSL afin de sécuriser votre site pour les utilisateurs et utilisatrices. Cloud Manager utilise un service de plateforme TLS pour gérer les certificats SSL et les clés privées détenus par la clientèle et obtenus auprès d’autorités de certification tierces."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html?lang=fr" text="Affichage, mise à jour et remplacement d’un certificat SSL"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/managing-certificates.html?lang=fr" text="Vérification du statut d’un certificat SSL"

Cloud Manager vous fournit des outils en libre-service pour installer et gérer des certificats SSL afin de sécuriser votre site pour les utilisateurs et utilisatrices. Cloud Manager utilise un service de plateforme TLS pour gérer les certificats SSL et les clés privées détenus par les clients et clientes et généralement obtenus auprès d’autorités de certification tierces, telles que Let’s Encrypt.

## Présentation des certificats {#certificates}

Les entreprises utilisent des certificats SSL pour sécuriser leurs sites web et permettre à leurs clients de leur faire confiance. Pour utiliser le protocole SSL, un serveur web nécessite un certificat SSL.

Lorsqu’une entité demande un certificat à une autorité de certification, celle-ci effectue un processus de vérification. Ce processus peut aller de la vérification du contrôle des noms de domaine jusqu’à la collecte de documents d’immatriculation des sociétés et de contrats d’abonnés. Une fois les informations d’une entité vérifiées, l’autorité de certification signe la clé publique à l’aide de sa clé privée. Étant donné que la totalité des principales autorités de certification possèdent des certificats racine dans les navigateurs web, le certificat de l’entité est lié par une *chaîne de confiance* et le navigateur web le reconnaît comme un certificat approuvé.

>[!IMPORTANT]
>
>Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ces éléments doivent être obtenus auprès des autorités de certification (AC).

## Fonctionnalités de gestion SSL de Cloud Manager {#features}

Cloud Manager respecte les options d’utilisation suivantes en matière de certificat SSL client.

* Un certificat SSL peut être utilisé par plusieurs environnements. C’est à dire qu’il peut être ajouté une fois et utilisé plusieurs fois.
* Chaque environnement Cloud Manager peut utiliser plusieurs certificats.
* Une clé privée peut émettre plusieurs certificats SSL.
* Chaque certificat contient généralement plusieurs domaines.
* Le service Platform TLS achemine les requêtes vers le service CDN du client en fonction du certificat SSL utilisé pour s’arrêter et du service CDN qui héberge ce domaine.
* AEM as a Cloud Service accepte les certificats SSL génériques pour un domaine.

## Recommandations {#recommendations}

AEM as a Cloud Service ne prend en charge que les sites sécurisés `https`. 

* Les clients disposant de plusieurs domaines personnalisés ne souhaitent pas télécharger un certificat à chaque fois qu’ils ajoutent un domaine.
* Ces clients et clientes obtiennent un certificat comportant plusieurs domaines.

## Conditions requises {#requirements}

* AEM as a Cloud Service n’accepte que les certificats conformes à la politique OV (validation d’organisation) ou EV (validation étendue). 
* Tout certificat doit être de type TLS X.509, délivré par une autorité de certification approuvée (CA) et doté d’une clé privée RSA 2 048 bits correspondante.
* La politique DV (Validation de domaines) n’est pas acceptée.
* Les certificats auto-signés ne sont pas acceptés.

Les certificats OV et EV apportent aux utilisateurs des informations supplémentaires, validées par l’autorité de certification. Ils peuvent les utiliser pour déterminer si le propriétaire d’un site web, l’expéditeur d’un courrier électronique ou le signataire numérique d’un code exécutable ou de documents PDF est fiable. Les certificats DV ne permettent pas cette vérification de propriété.

## Limites {#limitations}

À tout moment, Cloud Manager autorise l’installation d’un maximum de 50 certificats SSL. Ils peuvent être associés à un ou plusieurs environnements dans votre programme et inclure également des certificats expirés.

Si vous avez atteint la limite, vérifiez vos certificats et tenez compte des points suivants :

* Suppression des certificats ayant expiré.
* Regroupement de plusieurs domaines dans le même certificat, puisqu’un certificat peut couvrir plusieurs domaines (jusqu’à 100 SAN).

## En savoir plus {#learn-more}

Un utilisateur disposant des autorisations nécessaires peut utiliser Cloud Manager pour gérer les certificats SSL d’un programme. Pour plus d’informations sur l’utilisation de ces fonctionnalités, consultez les documents suivants.

* [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Affichage, mise à jour ou remplacement d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
* [Suppression d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)

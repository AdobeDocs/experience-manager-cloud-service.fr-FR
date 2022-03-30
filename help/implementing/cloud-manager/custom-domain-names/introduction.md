---
title: Présentation des noms de domaine personnalisés
description: L’interface utilisateur de Cloud Manager vous permet d’ajouter un domaine personnalisé pour identifier votre site avec un nom de marque unique en libre-service.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
source-git-commit: cc1b0d653706150c616ceafd002dc7594b6c7072
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 37%

---


# Présentation des noms de domaine personnalisés {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Gestion des noms de domaine personnalisés"
>abstract="L’interface utilisateur de Cloud Manager vous permet d’ajouter un domaine personnalisé pour identifier votre site avec un nom de marque unique en libre-service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html?lang=fr" text="Ajout d’un nom de domaine personnalisé"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/view-update-replace-custom-domain-name.html?lang=fr" text="Afficher et mettre à jour le nom de domaine personnalisé"

L’interface utilisateur de Cloud Manager vous permet d’ajouter un domaine personnalisé pour identifier votre site avec un nom de marque unique en libre-service. Adobe Experience Manager as a Cloud Service est fourni avec un nom de domaine par défaut qui se termine par `*.adobeaemcloud.com`. Ce nom de domaine par défaut reste, même après avoir associé des noms de domaine personnalisés à votre site web.

## Que sont les noms de domaine personnalisés ? {#what-are-custom-domain-names}

Chaque site web est associé à une adresse numérique unique, lisible par ordinateur, telle que `184.33.123.64`. Le système de noms de domaine (DNS) permet d’associer des domaines personnalisés de marque à des sites web en traduisant des adresses numériques en adresses mémorables, telles que `wknd.com`.

Il est recommandé d’attribuer à votre site un nom de domaine qui soit mémorable pour vos clients et qui reflète votre marque.

Vous pouvez acheter un nom de domaine auprès d’un service d’enregistrement de noms de domaine, d’une société ou d’une organisation qui gère et vend des noms de domaine. Les serveurs d’enregistrement de noms de domaine gèrent les noms de domaine sur les serveurs DNS.

>[!IMPORTANT]
>
>Cloud Manager n’est pas un service d’enregistrement de noms de domaine et ne fournit pas de services DNS.

## Limites {#limitations}

L’utilisation de noms de domaine personnalisés avec AEMaaCS présente certaines limites.

* Les noms de domaine personnalisés sont pris en charge dans Cloud Manager pour les programmes de publication et de prévisualisation de services pour les sites. Les domaines personnalisés côté auteur ne sont pas pris en charge.
* Chaque environnement Cloud Manager peut héberger jusqu’à 500 domaines personnalisés.
* AEM as a Cloud Service ne prend pas en charge les domaines génériques.
* Avant d’ajouter un nom de domaine personnalisé, un certificat SSL valide contenant le nom de domaine personnalisé doit être installé pour votre programme. Consultez la section Ajout d’un certificat SSL pour en savoir plus.
* Les noms de domaine ne peuvent pas être ajoutés aux environnements tant qu’un pipeline en cours d’exécution est attaché à ces environnements.
* Il n’est possible d’ajouter qu’un seul nom de domaine à la fois.
* Le même nom de domaine ne peut pas être utilisé sur plusieurs environnements.

## Workflow {#workflow}

L’ajout d’un nom de domaine personnalisé nécessite une interaction entre le service DNS et Cloud Manager. Pour cette raison, plusieurs étapes sont nécessaires pour installer, configurer et vérifier les noms de domaine personnalisés. Le tableau suivant présente un aperçu des étapes requises, y compris les mesures à prendre en cas d’erreurs courantes.

| Étape | Description | Responsabilité | En savoir plus |
|--- |--- |--- |---|
| 1 | Ajout d’un certificat SLL à Cloud Manager | Client | [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | Ajout d’un enregistrement TXT pour vérifier le domaine | Client | [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 3 | Examinez le statut de vérification du domaine | Client | [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3a | Si la vérification du domaine échoue avec l’état `Domain Verification Failure` | Client | [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 3b | Si la vérification du domaine échoue avec l’état `Verified, Deployment Failed`, contactez l’Adobe | Assistance clientèle d’Adobe | [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 4 | Configurez les paramètres DNS en ajoutant des enregistrements CNAME ou APEX DNS qui pointent vers AEM as a Cloud Service | Client | [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 5 | Vérification de l’état des enregistrements DNS | Client | [Vérification du statut de l’enregistrement DNS](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5a | Si l’état de l’enregistrement DNS échoue avec `DNS status not detected` | Client | [Vérification du statut de l’enregistrement DNS](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |
| 5b | Si l’état de l’enregistrement DNS échoue avec `DNS resolves incorrectly` | Client | [Vérification du statut de l’enregistrement DNS](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

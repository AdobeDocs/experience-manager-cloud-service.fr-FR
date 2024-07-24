---
title: Introduction aux noms de domaine personnalisés
description: L’interface utilisateur Cloud Manager vous permet d’ajouter un domaine personnalisé pour identifier votre site par un nom de marque unique en libre-service.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1c9924b4477d53d86bb72eda8597a02304450195
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 59%

---


# Introduction aux noms de domaine personnalisés {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Gestion des noms de domaine personnalisés"
>abstract="L’interface utilisateur Cloud Manager vous permet d’ajouter un domaine personnalisé pour identifier votre site par un nom de marque unique en libre-service."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Ajout d’un nom de domaine personnalisé"
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Afficher et mettre à jour le nom de domaine personnalisé"

Adobe Experience Manager as a Cloud Service est configuré avec un nom de domaine par défaut, se terminant par `*.adobeaemcloud.com`. À l’aide de l’interface utilisateur de Cloud Manager, vous pouvez ajouter un domaine personnalisé pour identifier votre site avec un nom de marque unique en libre-service. Le nom de domaine par défaut `*.adobeaemcloud.com` reste, même après avoir associé des noms de domaine personnalisés à votre site web.

## Que sont les noms de domaine personnalisés ? {#what-are-custom-domain-names}

Chaque site web est associé à une adresse numérique unique, lisible par ordinateur, telle que `184.33.123.64`. Le système de noms de domaine (DNS) est ce qui vous permet d’associer des domaines personnalisés et de marque à des sites web en traduisant des adresses numériques en adresses mémorables telles que `wknd.com`.

Il est recommandé d’attribuer à votre site un nom de domaine qui soit mémorable pour vos clients et qui reflète votre marque.

Vous pouvez acheter un nom de domaine auprès d’un service d’enregistrement de noms de domaine, d’une société ou d’une organisation qui gère et vend des noms de domaine. Les services d’enregistrement des noms de domaine gèrent les noms de domaine sur les serveurs DNS.

>[!IMPORTANT]
>
>Cloud Manager n’est pas un service d’enregistrement de noms de domaine et ne fournit pas de services DNS.

## Noms de domaines personnalisés et réseaux CDN BYO {#byo-cdn}

AEM as a Cloud Service propose un service CDN (Content Delivery Network) intégré, mais vous permet également d’apporter votre propre CDN (BYO) à utiliser avec AEM. Les domaines personnalisés peuvent être installés dans le réseau CDN géré par AEM ou dans un réseau CDN géré par vous-même.

* Les noms de domaines (et certificats) personnalisés installés dans le réseau CDN géré par AEM sont gérés via Cloud Manager.
* Les noms de domaines personnalisés (et les certificats) installés dans votre propre réseau CDN sont gérés dans ce réseau CDN spécifique.

**Les domaines gérés dans votre propre réseau de diffusion de contenu n’ont pas besoin d’être installés par le biais de Cloud Manager.** Ils sont mis à la disposition d’AEM par le biais de X-Forwarded-Host et correspondent aux hôtes définis dans Dispatcher. Voir la [documentation sur le réseau de diffusion de contenu.](/help/implementing/dispatcher/cdn.md)

Dans un seul environnement, vous pouvez avoir les deux domaines installés dans le réseau CDN géré par AEM et dans votre propre réseau CDN.

## Workflow {#workflow}

L’ajout d’un nom de domaine personnalisé nécessite une interaction entre le service DNS et Cloud Manager. Pour cette raison, plusieurs étapes sont nécessaires pour installer, configurer et vérifier les noms de domaine personnalisés. Le tableau suivant présente une vue d’ensemble des étapes requises, y compris des liens vers les ressources de documentation pour terminer ces étapes.

| Étape | Description | Documentation |
|---|---|---|
| 1 | Ajouter un certificat SSL à Cloud Manager | [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | Ajout d’un domaine personnalisé à Cloud Manager | [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 3 | Ajout d’un enregistrement TXT pour vérifier le domaine | [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) |
| 4 | Vérification de l’état du domaine | [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) |
| 5 | Configurez les paramètres DNS en ajoutant des enregistrements CNAME ou APEX DNS qui pointent vers AEM as a Cloud Service | [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) |
| 6 | Vérifiez le statut de l’enregistrement DNS | [Vérification du statut de l’enregistrement DNS](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>Le processus de configuration de noms de domaine personnalisés avec AEM as a Cloud Service s’avère généralement simple. Cependant, il peut arriver que des problèmes de délégation de domaine se produisent, ce qui peut prendre entre 1 et 2 jours ouvrables. C’est pourquoi il est vivement recommandé d’installer les domaines bien avant leur date d’activation. Consultez le document [Vérification du statut du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

## Limites {#limitations}

L’utilisation de noms de domaine personnalisés avec AEMaaCS présente plusieurs limites.

* Les noms de domaine personnalisés ne sont pris en charge dans Cloud Manager que pour les services de publication et de prévisualisation des programmes Sites.
   * Les domaines personnalisés pour les services de création ne sont pas pris en charge.
* Chaque environnement Cloud Manager peut héberger jusqu’à 500 domaines personnalisés.
* Les noms de domaines ne peuvent pas être ajoutés aux environnements tant qu’un pipeline en cours d’exécution est attaché à ceux-ci.
* Un même nom de domaine ne peut pas être utilisé sur plusieurs environnements.
* Il n’est possible d’ajouter qu’un seul nom de domaine à la fois.
* AEM as a Cloud Service ne prend pas en charge les domaines génériques tels que `*.example.com`.
* Avant d’ajouter un nom de domaine personnalisé, un certificat SSL valide contenant le nom de domaine personnalisé (les certificats génériques sont valides) doit être installé pour votre programme.

## Commencez ! {#get-started}

* Commencez à configurer un nouveau nom de domaine personnalisé pour votre projet en [ajoutant un certificat SSL.](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* Gérez vos noms de domaine existants en consultant le document [Gestion des noms de domaine personnalisés.](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)

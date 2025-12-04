---
title: Introduction aux noms de domaine personnalisés
description: L’interface utilisateur Cloud Manager vous permet d’ajouter un domaine personnalisé pour identifier votre site par un nom de marque unique en libre-service.
exl-id: ed03bff9-dfcc-4dfe-a501-a7facd24aa7d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 15da86656733074afccef85910cc8ea0109933e6
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 35%

---


# Introduction aux noms de domaine personnalisés {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_domains"
>title="Gérer les noms de domaine personnalisés"
>abstract="L’interface utilisateur Cloud Manager vous permet d’ajouter un domaine personnalisé pour identifier votre site par un nom de marque unique en libre-service."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name" text="Ajout d’un nom de domaine personnalisé"
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/managing-custom-domain-names" text="Afficher et mettre à jour le nom de domaine personnalisé"

Adobe Experience Manager as a Cloud Service est configuré avec un nom de domaine par défaut, se terminant par `*.adobeaemcloud.com`. À l’aide de l’interface utilisateur de Cloud Manager, vous pouvez ajouter un domaine personnalisé pour identifier votre site par un nom de marque unique en libre-service. Le nom de domaine `*.adobeaemcloud.com` par défaut est conservé, même après l’association de noms de domaine personnalisés à votre site web.

## Que sont les noms de domaine personnalisés ? {#what-are-custom-domain-names}

Chaque site web est associé à une adresse numérique unique, lisible par ordinateur, telle que `184.33.123.64`. Le système de noms de domaine (DNS) permet d’associer des domaines personnalisés de marque à des sites web en traduisant des adresses numériques en adresses mémorisables, telles que `wknd.com`.

Il est recommandé d’attribuer à votre site un nom de domaine qui soit mémorisable pour vos clients et qui reflète votre marque.

>[!IMPORTANT]
>
> Les domaines par défaut sous adobeaemcloud.com **ne doivent pas être utilisés** pour diffuser du contenu important à des fins d’optimisation pour les moteurs de recherche. Les domaines et sous-domaines adobeaemcloud.com ne sont pas indexables par les moteurs de recherche, car ils servent un [robots.txt par défaut](https://cdn.adobeaemcloud.com/robots.txt) qui empêche l’analyse et l’indexation. Utilisez plutôt votre propre domaine personnalisé pour servir un fichier robots.txt personnalisé.

Vous pouvez acheter un nom de domaine auprès d’un service d’enregistrement de noms de domaine, d’une société ou d’une organisation qui gère et vend des noms de domaine. Les services d’enregistrement des noms de domaine gèrent les noms de domaine sur les serveurs DNS.

>[!IMPORTANT]
>
>Cloud Manager n’est pas un service d’enregistrement de noms de domaine et ne fournit pas de services DNS.

## Noms de domaine personnalisés et apporter vos propres réseaux CDN {#byo-cdn}

AEM as a Cloud Service offre un service CDN (réseau de diffusion de contenu) intégré, mais vous permet également d’utiliser votre propre réseau CDN BYO (Bring Your Own) avec AEM. Les domaines personnalisés peuvent être installés dans le réseau CDN géré par AEM ou dans un réseau CDN géré par vous-même.

* Cloud Manager gère les noms de domaine et certificats personnalisés installés dans le réseau CDN géré par AEM.
* Les noms de domaine personnalisés et les certificats installés dans un réseau CDN BYO sont gérés directement dans ce réseau CDN.

**Les domaines gérés dans votre propre réseau CDN ne nécessitent pas d’installation via Cloud Manager** - Ils sont mis à la disposition d’AEM par le biais de X-Forwarded-Host et correspondent aux hôtes virtuels définis dans le Dispatcher. Consultez la [documentation sur le réseau CDN](/help/implementing/dispatcher/cdn.md).

Dans un seul environnement, les deux domaines peuvent être installés dans le réseau CDN géré par AEM et dans un réseau CDN BYO.

## Workflow {#workflow}

L’ajout d’un nom de domaine personnalisé nécessite une interaction entre le service DNS et Cloud Manager. En raison de ce workflow, plusieurs étapes sont nécessaires pour installer, configurer et vérifier les noms de domaine personnalisés. Le tableau suivant décrit les étapes requises, avec des liens vers les ressources de documentation, pour réaliser ces étapes.

>[!WARNING]
>
>Exécutez l’étape 4 (Configurer le DNS) *uniquement après* l’étape 3 (Ajouter un mappage de domaine) s’est terminée avec succès. Cette commande permet d’enregistrer le domaine sur le réseau de diffusion de contenu d’Adobe et de configurer le routage correct, protégeant ainsi votre site contre les reprises de domaine.

| Étape | Description |
| --- | --- |
| 1 | [Ajouter un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) |
| 2 | [Ajouter un domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 3 | [Ajouter un mappage de domaine](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) |
| 4 | [Configurer DNS](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#config-dns) |
| 5 | [Vérification du statut DNS](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) |

>[!TIP]
>
>Le processus de configuration de noms de domaine personnalisés avec AEM as a Cloud Service s’avère généralement simple. Cependant, il peut arriver que des problèmes de délégation de domaine se produisent, ce qui peut prendre entre 1 et 2 jours ouvrables. Pour cette raison, il est recommandé d’installer les domaines bien avant leur date d’activation. Consultez le document [Vérification du statut du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

## Remarques sur l’utilisation {#usage-notes}

* Les noms de domaine personnalisés sont pris en charge dans Cloud Manager uniquement pour les services de publication et de prévisualisation pour les programmes Sites.
   * Les domaines personnalisés pour les services de création ne sont pas pris en charge.
* Chaque environnement Cloud Manager peut héberger jusqu’à 500 domaines personnalisés.
* Les noms de domaine ne peuvent pas être ajoutés aux environnements tant qu’un pipeline en cours d’exécution est attaché à ces environnements.
* Un même nom de domaine ne peut pas être utilisé dans plusieurs environnements.
* Il n’est possible d’ajouter qu’un seul nom de domaine à la fois.
* AEM as a Cloud Service ne prend pas en charge les domaines génériques tels que `*.example.com`.
* Avant d’ajouter un nom de domaine personnalisé, un certificat SSL valide contenant le nom de domaine personnalisé (les certificats génériques sont valides) doit être installé pour votre programme.
* Des étapes de configuration supplémentaires sont requises pour utiliser un nom de domaine personnalisé avec [la fonctionnalité Pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md#custom-domains).

## Commencer {#get-started}

* Commencez à configurer un nouveau nom de domaine personnalisé pour votre projet en [ajoutant un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
* Gérez vos noms de domaine existants en consultant le document [Gérer les noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md).

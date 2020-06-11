---
title: CDN dans AEM en tant que service Cloud
description: CDN dans AEM en tant que service Cloud
translation-type: tm+mt
source-git-commit: a9bf697f65febcd9ba99539d8baa46f7a8d165e3
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 42%

---


# CDN dans AEM en tant que service Cloud {#cdn}

AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM.

Le réseau de diffusion de contenu géré AEM satisfait à la plupart des exigences de performances et de sécurité du client. Les clients peuvent éventuellement pointer vers le réseau de diffusion de contenu depuis leur propre réseau de diffusion de contenu, qu’ils devront gérer. Cela sera autorisé au cas par cas, en fonction de certaines conditions préalables, notamment, mais sans s&#39;y limiter, le client ayant une intégration héritée avec son fournisseur de réseau de diffusion de contenu difficile à abandonner.

## Réseau de diffusion de contenu géré par AEM {#aem-managed-cdn}

Suivez ces instructions pour préparer la diffusion du contenu en utilisant le CDN prêt à l’emploi Adobe :

1. Fournissez le certificat SSL et la clé secrète signés à Adobe en partageant un lien vers un formulaire sécurisé contenant ces informations. Veuillez coordonner cette tâche avec le service clientèle.
   **Remarque :** AEM as a Cloud Service ne prend pas en charge les certificats DV (Domain Validated, domaines validés).
1. Informer le service clientèle :
   * Quel domaine personnalisé doit être associé à un environnement donné, tel que défini par l’ID de programme et l’ID d’environnement. Notez que les domaines personnalisés côté auteur ne sont pas pris en charge.
   * Si une liste blanche d’adresses IP est nécessaire pour limiter le trafic à destination d’un environnement donné.
1. Coordonner avec l’assistance clientèle les modifications nécessaires apportées aux enregistrements DNS. Les instructions sont différentes selon qu’un enregistrement apex est nécessaire ou non :
   * si aucun enregistrement apex n’est nécessaire, les clients doivent définir l’enregistrement DNS CNAME pour qu’il pointe leur nom de domaine complet sur `cdn.adobeaemcloud.com`.
   * si un enregistrement apex est nécessaire, créez un enregistrement A pointant vers les adresses IP suivantes : 151.101.3.10, 151.101.67.10, 151.101.131.10, 151.101.195.10. Les clients ont besoin d&#39;un enregistrement apex si le nom de domaine complet correspond à la zone DNS. Vous pouvez le tester en utilisant la commande dig Unix pour vérifier si la valeur SOA de la sortie correspond au domaine. Par exemple, la commande `dig anything.dev.adobeaemcloud.com` renvoie un SOA (Début d&#39;autorité, c&#39;est-à-dire la zone) de `dev.adobeaemcloud.com` sorte qu&#39;il ne s&#39;agisse pas d&#39;un enregistrement APEX, alors que `dig dev.adobeaemcloud.com` renvoie un SOA de `dev.adobeaemcloud.com` sorte qu&#39;il s&#39;agit d&#39;un enregistrement apex.
1. Vous serez averti lorsque les certificats SSL arriveront à expiration afin que vous puissiez soumettre à nouveau les nouveaux certificats SSL.

**Limitation du trafic**

Par défaut, dans le cas d’une configuration de réseau de diffusion de contenu géré par Adobe, tout le trafic public peut se diriger vers le service de publication, tant pour les environnements de production que de non-production (de développement et d’évaluation). Si vous souhaitez limiter le trafic à destination du service de publication pour un environnement donné (par exemple, limiter l’évaluation par une plage d’adresses IP), vous devez demander au service clientèle de configurer ces restrictions.

## Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM {#point-to-point-CDN}

Si un client doit utiliser son réseau de diffusion de contenu existant, il peut le gérer et le pointer vers le réseau de diffusion de contenu géré Adobe, à condition que les éléments suivants soient satisfaits :

* Le client doit disposer d’un CDN existant qui serait onéreux à remplacer.
* Le client doit le gérer.
* Le client doit être en mesure de configurer le CDN pour travailler avec AEM en tant que service Cloud - voir les instructions de configuration ci-dessous.
* Le client doit disposer d&#39;experts du réseau de diffusion de contenu d&#39;ingénierie qui sont à l&#39;écoute au cas où des problèmes se poseraient.
* Le client doit effectuer et réussir un test de charge avant de passer en production.

Instructions de configuration :

1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine.
1. Définissez l’en-tête de l’hôte avec le domaine d’origine, qui est l’entrée du réseau de diffusion de contenu d’Adobe. La valeur doit provenir d’Adobe.
1. Envoyez l’en-tête SNI à l’origine. Tout comme l’en-tête d’hôte, l’en-tête SNI doit être le domaine d’origine.
1. Définissez la valeur `X-Edge-Key`, qui est nécessaire pour acheminer correctement le trafic vers les serveurs AEM. La valeur doit provenir d’Adobe.

Avant d’accepter le trafic en direct, vous devez vérifier auprès du service clientèle d’Adobe que le trafic de bout en bout fonctionne correctement.

Notez que les performances peuvent être faibles en raison du saut supplémentaire, bien que les sauts du CDN du client vers le CDN géré Adobe soient susceptibles d’être efficaces.

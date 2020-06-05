---
title: CDN dans AEM en tant que service Cloud
description: CDN dans AEM en tant que service Cloud
translation-type: tm+mt
source-git-commit: 0080ace746f4a7212180d2404b356176d5f2d72c
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 95%

---


# CDN dans AEM en tant que service Cloud {#cdn}

AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM.

Au total, AEM offre deux options :

1. Réseau de diffusion de contenu géré par AEM, le réseau de diffusion de contenu prêt à l’emploi d’AEM. Il s’agit d’une option étroitement intégrée qui ne nécessite pas d’investissement client important dans la prise en charge de l’intégration du réseau de diffusion de contenu avec AEM.
1. Le réseau de diffusion de contenu géré par le client pointe vers le réseau de diffusion de contenu géré par AEM ; le client pointe son propre réseau de diffusion de contenu vers le réseau de diffusion de contenu prêt à l’emploi d’AEM. Le client devra toujours gérer son propre réseau de diffusion de contenu, mais l’investissement dans l’intégration avec AEM est modéré.

La première option devrait répondre à la plupart des exigences en matière de performances et de sécurité du client. De plus, elle demande un effort minimal au client.

La deuxième option sera autorisée au cas par cas. La décision est basée sur la satisfaction de certaines conditions préalables, y compris, mais sans s’y limiter, le fait que le client possède une intégration héritée avec son fournisseur de réseau de diffusion de contenu difficile à abandonner.

Vous trouverez ci-dessous une matrice de décision pour comparer les deux options. Vous trouverez des informations plus détaillées dans les sections qui suivent.

| Détails | Réseau de diffusion de contenu géré AEM | Le réseau de diffusion de contenu géré par le client pointe vers le réseau de diffusion de contenu AEM |
|---|---|---|
| **Effort du client** | Aucun, le réseau est complètement intégré. Il suffit de pointer CNAME vers le réseau de diffusion de contenu géré par AEM. | Investissement client modéré. Le client doit gérer son propre réseau de diffusion de contenu. |
| **Conditions préalables** | Aucune | Réseau de diffusion de contenu existant onéreux à remplacer. Doit démontrer un test de charge réussi avant sa mise en opération. |
| **Expertise dans le réseau de diffusion de contenu** | Aucune | Nécessite au moins un ingénieur à temps partiel ayant des connaissances approfondies du réseau de diffusion de contenu et capable de configurer le réseau de diffusion de contenu du client. |
| **Sécurité** | Géré par Adobe. | Géré par Adobe (et éventuellement par le client sur son propre réseau de diffusion de contenu). |
| **Performances** | Optimisé par Adobe. | Bénéficiera de certaines fonctionnalités du réseau de diffusion de contenu AEM, mais potentiellement un faible gain en performances en raison du saut supplémentaire. **Remarque**: Des houblons du CDN du client à l&#39;Adobe sortis de la boîte (CDN susceptible d&#39;être efficace). |
| **Mise en cache** | Prend en charge les en-têtes de cache appliqués au Dispatcher. | Prend en charge les en-têtes de cache appliqués au Dispatcher. |
| **Fonctionnalités de compression d’images et de vidéos** | Peut fonctionner avec Adobe Dynamic Media. | Peut fonctionner avec Adobe Dynamic Media ou avec la solution d’image/vidéo du réseau de diffusion de contenu géré par le client. |

## Réseau de diffusion de contenu géré par AEM {#aem-managed-cdn}

La préparation de la diffusion de contenu à l’aide du réseau de diffusion de contenu prêt à l’emploi d’Adobe est simple, comme décrit ci-dessous :

1. Vous fournirez le certificat SSL signé et la clé secrète à Adobe en partageant un lien vers un formulaire sécurisé contenant ces informations. Veuillez coordonner cette tâche avec le service clientèle.
   **Remarque :** AEM as a Cloud Service ne prend pas en charge les certificats DV (Domain Validated, domaines validés).
1. Vous devez indiquer au service clientèle les informations suivantes :
   * Quel domaine personnalisé doit être associé à un environnement donné, tel que défini par l’ID de programme et l’ID d’environnement.
   * Si une liste blanche d’adresses IP est nécessaire pour limiter le trafic à destination d’un environnement donné.
1. Le service clientèle coordonnera alors avec vous le timing d’un enregistrement DNS CNAME, en pointant son nom de domaine complet vers `cdn.adobeaemcloud.com`.
1. Vous serez averti lorsque les certificats SSL arriveront à expiration afin que vous puissiez soumettre à nouveau les nouveaux certificats SSL.

**Limitation du trafic**

Par défaut, dans le cas d’une configuration de réseau de diffusion de contenu géré par Adobe, tout le trafic public peut se diriger vers le service de publication, tant pour les environnements de production que de non-production (de développement et d’évaluation). Si vous souhaitez limiter le trafic à destination du service de publication pour un environnement donné (par exemple, limiter l’évaluation par une plage d’adresses IP), vous devez demander au service clientèle de configurer ces restrictions.

## Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM {#point-to-point-CDN}

Pris en charge si vous souhaitez utiliser votre réseau de diffusion de contenu existant, mais ne pouvez pas satisfaire aux exigences d’un réseau de diffusion de contenu géré par le client. Dans ce cas, vous gérez votre propre réseau de diffusion de contenu, mais pointez sur le réseau de diffusion de contenu géré par Adobe.

Notez que :

1. Vous devez disposer d’un réseau de diffusion de contenu existant.
1. Vous devez le gérer.
1. Vous devez être en mesure de configurer le réseau de diffusion de contenu pour utiliser AEM as a Cloud Service. Reportez-vous aux instructions de configuration ci-dessous.
1. Vous devez disposer d’ingénieurs maîtrisant les réseaux de diffusion de contenu et disponibles pour résoudre les problèmes associés éventuels.
1. Vous devez effectuer et réussir un test de charge avant de passer en production.

Instructions de configuration :

1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine.
1. Définissez l’en-tête de l’hôte avec le domaine d’origine, qui est l’entrée du réseau de diffusion de contenu d’Adobe. La valeur doit provenir d’Adobe.
1. Envoyez l’en-tête SNI à l’origine. Tout comme l’en-tête d’hôte, l’en-tête SNI doit être le domaine d’origine.
1. Définissez la valeur `X-Edge-Key`, qui est nécessaire pour acheminer correctement le trafic vers les serveurs AEM. La valeur doit provenir d’Adobe.

Avant d’accepter le trafic en direct, vous devez vérifier auprès du service clientèle d’Adobe que le trafic de bout en bout fonctionne correctement.

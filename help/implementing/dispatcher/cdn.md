---
title: Réseau de diffusion de contenu dans AEM as a Cloud Service
description: Réseau de diffusion de contenu dans AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: f6c700f82bc5a1a3edf05911a29a6e4d32dd3f72
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 87%

---

# Réseau de diffusion de contenu dans AEM as a Cloud Service {#cdn}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_cdn"
>title="Réseau de diffusion de contenu dans AEM as a Cloud Service"
>abstract="AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM."

AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM.


Le réseau de diffusion de contenu géré par AEM satisfait à la plupart des exigences de performances et de sécurité du client. Pour le niveau de publication, les clients peuvent éventuellement privilégier leur propre réseau de diffusion de contenu, mais il leur appartiendra de le gérer. Ce choix sera possible au cas par cas, en fonction de certaines conditions préalables, y compris, mais sans s’y limiter, le fait que le client possède une ancienne intégration avec son fournisseur de réseau de diffusion de contenu, et qu’il soit difficile de l’abandonner.

## Réseau de diffusion de contenu géré par AEM {#aem-managed-cdn}

Suivez les étapes des sections ci-dessous pour utiliser l’interface utilisateur en libre-service de Cloud Manager afin de préparer la diffusion de contenu à l’aide du réseau de diffusion de contenu prêt à l’emploi d’AEM :

1. [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Limitation du trafic**

Par défaut, dans le cas d’une configuration de réseau de diffusion de contenu géré par AEM, tout le trafic public peut se diriger vers le service de publication, tant pour les environnements de production que de non-production (de développement et d’évaluation). Si vous souhaitez limiter le trafic au service de publication pour un environnement donné (par exemple, en limitant l’évaluation sur une plage d’adresses IP), vous pouvez le faire en libre-service via l’interface utilisateur de Cloud Manager.

Consultez [Gestion des listes autorisées d’adresses IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) pour en savoir plus.

>[!CAUTION]
>
>Seules les requêtes provenant des adresses IP autorisées seront diffusées par le biais du réseau de diffusion de contenu géré par AEM. Si vous pointez votre propre réseau de diffusion de contenu sur le réseau géré par AEM, assurez-vous que les adresses IP de votre réseau de diffusion de contenu sont incluses dans la liste autorisée.

## Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM {#point-to-point-CDN}

Si un client doit utiliser son réseau de diffusion de contenu existant, il peut le gérer et le diriger vers le réseau de diffusion de contenu géré AEM, à condition que les conditions suivantes soient satisfaites :

* Le client doit disposer d’un réseau de diffusion de contenu existant potentiellement onéreux à remplacer.
* Le client doit en assurer la gestion.
* Le client doit être en mesure de configurer le réseau de diffusion de contenu pour utiliser AEM as a Cloud Service. Voir à ce sujet les instructions de configuration ci-dessous.
* Le client doit disposer d’ingénieurs maîtrisant les réseaux de diffusion de contenu, et disponibles pour résoudre les problèmes associés éventuels.
* Le client doit effectuer et réussir un test de charge avant de passer en production.

Instructions de configuration :

1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine. Par exemple : `X-Forwarded-Host:example.com`.
1. Définissez l’en-tête de l’hôte avec le domaine d’origine, qui est l’entrée du réseau de diffusion de contenu AEM. Par exemple : `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Envoyez l’en-tête SNI à l’origine. Tout comme l’en-tête d’hôte, l’en-tête SNI doit être le domaine d’origine.
1. Définissez `X-Edge-Key` ou `X-AEM-Edge-Key` (si votre réseau de diffusion de contenu supprime `X-Edge-*`). La valeur doit provenir d’Adobe.
   * Cela est nécessaire afin que le réseau de diffusion de contenu de l’Adobe puisse valider la source des requêtes et transmettre les en-têtes `X-Forwarded-*` à l’application AEM. Par exemple, `X-Forwarded-Host` est utilisé par AEM pour déterminer l’en-tête de l’hôte et `X-Forwarded-For` est utilisé pour déterminer l’adresse IP du client. Il incombe donc à l’appelant de confiance (c’est-à-dire au réseau de diffusion de contenu géré par le client) de s’assurer que les en-têtes `X-Forwarded-*` sont corrects (voir la note ci-dessous).
   * En option, l’accès à l’entrée du réseau de diffusion de contenu d’Adobe peut être bloqué lorsqu’une balise `X-Edge-Key` n’est pas présente. Veuillez indiquer à Adobe si vous avez besoin d’un accès direct à l’entrée du CDN d’Adobe (à bloquer).

Avant d’accepter le trafic en direct, vous devez vérifier auprès du service clientèle d’Adobe que le trafic de bout en bout fonctionne correctement.

>[!NOTE]
>
>Les clients qui gèrent leur propre réseau de diffusion de contenu doivent garantir l’intégrité des en-têtes envoyés au réseau de diffusion de contenu AEM. Par exemple, il est recommandé aux clients d’effacer tous les en-têtes `X-Forwarded-*` et de les définir sur des valeurs connues et contrôlées. Par exemple, `X-Forwarded-For` doit contenir l’adresse IP du client, tandis que `X-Forwarded-Host` doit contenir l’hôte du site.

Les performances peuvent diminuer en raison du saut supplémentaire, bien que les sauts entre le réseau de diffusion du client et celui géré par AEM puissent être efficaces.

Notez que cette configuration de réseau de diffusion de contenu client est prise en charge pour le niveau de publication, mais pas au niveau auteur.

## En-têtes de géolocalisation {#geo-headers}

Le réseau de diffusion de contenu géré par AEM ajoute des en-têtes à chaque requête avec les éléments suivants :

* Le code de pays : `x-aem-client-country`
* Le code continent : `x-aem-client-continent`

Les valeurs des codes de pays sont les codes Alpha-2 décrits [ici](https://fr.wikipedia.org/wiki/ISO_3166-1).

Les valeurs des codes du continent sont les suivantes :

* AF Afrique
* AN Antarctique
* AS Asie
* EU Europe
* NA Amérique du Nord
* OC Océanie
* SA Amérique du Sud

Ces informations peuvent s’avérer utiles dans certains cas d’utilisation, tels que la redirection vers une URL différente en fonction de l’origine (pays) de la requête. Utilisez l’en-tête Vary pour mettre en cache les réponses qui dépendent des informations géographiques. Par exemple, les redirections vers la page d’entrée d’un pays spécifique doivent toujours contenir `Vary: x-aem-client-country`. Si nécessaire, vous pouvez utiliser `Cache-Control: private` pour empêcher la mise en cache. Voir aussi [Mise en cache](/help/implementing/dispatcher/caching.md#html-text).

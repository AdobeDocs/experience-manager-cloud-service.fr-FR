---
title: Réseau de diffusion de contenu dans AEM as a Cloud Service
description: Réseau de diffusion de contenu dans AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
translation-type: tm+mt
source-git-commit: 16a0f4de0d7a32032abd4742cc06a086038d032b
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 64%

---

# Réseau de diffusion de contenu dans AEM as a Cloud Service {#cdn}

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
>Seules les requêtes provenant des adresses IP autorisées seront diffusées par le biais du réseau de diffusion de contenu géré par AEM. Si vous pointez votre propre CDN sur le CDN AEM géré, assurez-vous que les adresses IP de votre CDN sont incluses dans la liste autorisée.

## Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM {#point-to-point-CDN}

Si un client doit utiliser son réseau de diffusion de contenu existant, il peut le gérer et le diriger vers le réseau de diffusion de contenu géré AEM, à condition que les conditions suivantes soient satisfaites :

* Le client doit disposer d’un réseau de diffusion de contenu existant potentiellement onéreux à remplacer.
* Le client doit en assurer la gestion.
* Le client doit être en mesure de configurer le réseau de diffusion de contenu pour utiliser AEM as a Cloud Service. Voir à ce sujet les instructions de configuration ci-dessous.
* Le client doit disposer d’ingénieurs maîtrisant les réseaux de diffusion de contenu, et disponibles pour résoudre les problèmes associés éventuels.
* Le client doit effectuer et réussir un test de charge avant de passer en production.

Instructions de configuration :

1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine. Par exemple : `X-Forwarded-Host:example.com`.
1. Définissez l’en-tête de l’hôte avec le domaine d’origine, qui est l’entrée du réseau de diffusion de contenu AEM. Par exemple : `Host: publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Envoyez l’en-tête SNI à l’origine. Tout comme l’en-tête Host, l’en-tête SNI doit être le domaine d’origine.
1. Définissez `X-Edge-Key` ou `X-AEM-Edge-Key` (si votre réseau de diffusion de contenu se décompose `X-Edge-*`). La valeur doit provenir d’Adobe.
   * Cela est nécessaire pour que le CDN de l&#39;Adobe puisse valider la source des requêtes et transmettre les en-têtes `X-Forwarded-*` à l&#39;application AEM. Par exemple, `X-Forwarded-Host` est utilisé par AEM pour déterminer l’en-tête hôte et `X-Forwarded-For` est utilisé pour déterminer l’adresse IP du client. Il incombe donc à l&#39;appelant de confiance (c&#39;est-à-dire au CDN géré par le client) de s&#39;assurer de l&#39;exactitude des en-têtes `X-Forwarded-*` (voir la note ci-dessous).
   * Si vous le souhaitez, l&#39;accès à l&#39;entrée du CDN de l&#39;Adobe peut être bloqué lorsqu&#39;un `X-Edge-Key` n&#39;est pas présent. Veuillez informer l&#39;Adobe si vous avez besoin d&#39;un accès direct à l&#39;entrée du CDN de l&#39;Adobe (à bloquer).

Avant d’accepter le trafic en direct, vous devez vérifier auprès de l’assistance clientèle de l’Adobe que le routage de trafic de bout en bout fonctionne correctement.

>[!NOTE]
>
>Les clients qui gèrent leur propre CDN doivent garantir l’intégrité des en-têtes envoyés à AEM CDN. Par exemple, il est recommandé aux clients d’effacer tous les en-têtes `X-Forwarded-*` et de les définir sur des valeurs connues et contrôlées. Par exemple, `X-Forwarded-For` doit contenir l’adresse IP du client, tandis que `X-Forwarded-Host` doit contenir l’hôte du site.

Les performances peuvent diminuer en raison du saut supplémentaire, bien que les sauts entre le réseau de diffusion du client et celui géré par AEM puissent être efficaces.

Notez que cette configuration CDN client est prise en charge pour la couche Publication, mais pas devant la couche Auteur.

## En-têtes de géolocalisation {#geo-headers}

Le CDN géré AEM ajoute des en-têtes à chaque requête avec :

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

Ces informations peuvent s’avérer utiles dans certains cas d’utilisation, tels que la redirection vers une URL différente en fonction de l’origine (pays) de la requête. Utilisez l’en-tête Vary pour mettre en cache les réponses qui dépendent des informations géographiques. Par exemple, les redirections vers un landing page de pays spécifique doivent toujours contenir `Vary: x-aem-client-country`. Si nécessaire, vous pouvez utiliser `Cache-Control: private` pour empêcher la mise en cache. Voir aussi [Mise en cache](/help/implementing/dispatcher/caching.md#html-text).

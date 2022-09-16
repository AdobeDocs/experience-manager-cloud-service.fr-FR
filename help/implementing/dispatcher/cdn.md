---
title: Réseau de diffusion de contenu dans AEM as a Cloud Service
description: Réseau de diffusion de contenu dans AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: a5d26c5cf07f60c65405afb2a25c903e97dc59aa
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 90%

---

# Réseau de diffusion de contenu dans AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="Réseau de diffusion de contenu dans AEM as a Cloud Service"
>abstract="AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM."

AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM.

Le réseau de diffusion de contenu géré par AEM satisfait à la plupart des exigences de performances et de sécurité du client. Pour le niveau de publication, les clients peuvent éventuellement privilégier leur propre réseau de diffusion de contenu, mais il leur appartiendra de le gérer. Ce choix sera possible au cas par cas, en fonction de certaines conditions préalables, y compris, mais sans s’y limiter, le fait que le client possède une ancienne intégration avec son fournisseur de réseau de diffusion de contenu, et qu’il soit difficile de l’abandonner.

Consultez également les vidéos suivantes [Cloud 5 AEM CDN Partie 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html?lang=fr) et [Cloud 5 AEM CDN Partie 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html?lang=fr) pour obtenir plus d’informations sur le réseau de diffusion de contenu dans AEM as a Cloud Service.

## Réseau de diffusion de contenu géré AEM  {#aem-managed-cdn}

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

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM"
>abstract="AEM as a Cloud Service offre aux clients une option pour utiliser son réseau CDN. Pour le niveau de publication, les clients peuvent éventuellement privilégier leur propre réseau de diffusion de contenu, mais il leur appartiendra de le gérer. Ce choix sera possible au cas par cas, en fonction de certaines conditions préalables, y compris, mais sans s’y limiter, le fait que le client possède une ancienne intégration avec son fournisseur de réseau de diffusion de contenu, et qu’il soit difficile de l’abandonner."

Si un client doit utiliser son réseau de diffusion de contenu existant, il peut le gérer et le diriger vers le réseau de diffusion de contenu géré AEM, à condition que les conditions suivantes soient satisfaites :

* Le client doit disposer d’un réseau de diffusion de contenu existant potentiellement onéreux à remplacer.
* Le client doit en assurer la gestion.
* Le client doit être en mesure de configurer le réseau CDN pour utiliser AEM as a Cloud Service. Consultez les instructions de configuration présentées ci-dessous.
* Le client doit disposer d’ingénieurs maîtrisant les réseaux de diffusion de contenu, et disponibles pour résoudre les problèmes associés éventuels.
* Le client doit effectuer et réussir un test de charge avant de passer en production.

>[!NOTE]
>
>Le réseau CDN d’Adobe n’est pas facultatif. Les clients qui apportent leur propre réseau CDN doivent le diriger vers le réseau CDN géré par AEM.

Instructions de configuration :

1. Pointez votre réseau CDN sur l’entrée du réseau CDN Adobe en tant que domaine d’origine. Par exemple, `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Le SNI doit également être défini sur l’entrée du réseau CDN Adobe..
1. Définissez l’en-tête hôte sur le domaine d’origine. Par exemple : `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine afin qu’AEM puisse déterminer l’en-tête hôte. Par exemple : `X-Forwarded-Host:example.com`.
1. Définir `X-AEM-Edge-Key`. La valeur doit provenir d’Adobe.

   * Ce paramétrage est nécessaire afin que le réseau de diffusion de contenu d’Adobe puisse valider la source des requêtes et transmettre les en-têtes `X-Forwarded-*` à l’application AEM. Par exemple,`X-Forwarded-For` est utilisé pour déterminer l’adresse IP du client. Il incombe donc à l’appelant approuvé (c’est-à-dire au réseau de diffusion de contenu géré par le client) de s’assurer que les en-têtes `X-Forwarded-*` sont corrects (voir la note ci-dessous).
   * L’accès à l’entrée du réseau de diffusion de contenu d’Adobe peut être aussi bloqué lorsqu’une balise `X-AEM-Edge-Key` n’est pas présente. Informez Adobe si vous avez besoin d’un accès direct à l’entrée du CDN d’Adobe (à bloquer).

Voir [Exemples de configurations de fournisseur CDN](#sample-configurations) pour consulter des exemples de configuration provenant de principaux fournisseurs de réseau de diffusion de contenu.

Avant d’accepter le trafic en direct, vous devez vérifier auprès du service clientèle d’Adobe que le trafic de bout en bout fonctionne correctement.

Après avoir obtenu la variable `X-AEM-Edge-Key`, vous pouvez tester que la requête est correctement acheminée comme suit.

Sous Linux :

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

Sous Windows:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

Veuillez noter que lorsque vous utilisez votre propre réseau CDN, il n’est pas nécessaire d’installer les domaines et les certificats dans Cloud Manager. Le routage dans le réseau CDN Adobe sera effectué à l’aide du domaine par défaut `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.

>[!NOTE]
>
>Les clients qui gèrent leur propre réseau de diffusion de contenu doivent garantir l’intégrité des en-têtes envoyés au réseau de diffusion de contenu AEM. Par exemple, il est recommandé aux clients d’effacer tous les en-têtes `X-Forwarded-*` et de les définir sur des valeurs connues et contrôlées. Par exemple, `X-Forwarded-For` doit contenir l’adresse IP du client, tandis que `X-Forwarded-Host` doit contenir l’hôte du site.

>[!NOTE]
>
>Les environnements de programme Sandbox ne prennent pas en charge un réseau CDN fourni par le client.

Le saut supplémentaire entre le réseau de diffusion de contenu client et le réseau de diffusion de contenu AEM n’est nécessaire que dans le cas d’une interruption du cache. En utilisant les stratégies d’optimisation du cache décrites dans cet article, l’ajout d’un réseau de diffusion de contenu client ne doit qu’introduire une latence négligeable.

Notez que cette configuration de réseau de diffusion de contenu client est prise en charge pour le niveau de publication, mais pas au niveau auteur.

### Exemples de configurations de fournisseur CDN {#sample-configurations}

Vous trouverez ci-dessous plusieurs exemples de configuration de plusieurs principaux fournisseurs de réseau de diffusion de contenu.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

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

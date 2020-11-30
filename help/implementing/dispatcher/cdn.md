---
title: Réseau de diffusion de contenu dans AEM as a Cloud Service
description: Réseau de diffusion de contenu dans AEM as a Cloud Service
translation-type: tm+mt
source-git-commit: 14d08529eeee0f9881e668eed6273cfa57f1360f
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 93%

---


# Réseau de diffusion de contenu dans AEM as a Cloud Service {#cdn}

AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM.

Le réseau de diffusion de contenu géré par AEM satisfait à la plupart des exigences de performances et de sécurité du client. Pour le niveau de publication, les clients peuvent éventuellement privilégier leur propre réseau de diffusion de contenu, mais il leur appartiendra de le gérer. Ce choix sera possible au cas par cas, en fonction de certaines conditions préalables, y compris, mais sans s’y limiter, le fait que le client possède une ancienne intégration avec son fournisseur de réseau de diffusion de contenu, et qu’il soit difficile de l’abandonner.

## Réseau de diffusion de contenu géré par AEM {#aem-managed-cdn}

Procédez comme suit pour préparer la diffusion de contenu à l’aide du réseau de diffusion de contenu prêt à l’emploi d’Adobe :

1. Fournissez le certificat SSL signé et la clé secrète à Adobe en partageant un lien vers un formulaire sécurisé contenant ces informations. Il est recommandé de coordonner cette tâche avec le service clientèle. Adobe prend en charge jusqu’à 10 certificats SSL pour un programme.
   **Remarque :** AEM as a Cloud Service ne prend pas en charge les certificats DV (Domain Validated, domaines validés). En outre, il doit s’agir d’un certificat TLS X.509 d’une autorité de certification approuvée (CA) avec une clé privée RSA 2 048 bits correspondante.
1. Donnez les informations suivantes au service clientèle :
   * quel(s) domaine(s) personnalisé(s) doit être associé(s) à un environnement donné, tel que défini par l&#39;ID de programme et l&#39;ID d&#39;environnement. Jusqu’à 100 domaines sont pris en charge pour un environnement donné et les domaines ne peuvent pas contenir de caractères génériques. Notez que les domaines personnalisés côté auteur ne sont pas pris en charge.
   * Une liste d’adresses IP autorisées éventuellement nécessaire pour limiter le trafic à destination d’un environnement donné.
1. Coordination avec l’assistance clientèle concernant les délais des modifications nécessaires apportées aux enregistrements DNS. Les instructions sont différentes selon qu’un enregistrement apex est nécessaire ou non :
   * si aucun enregistrement apex n’est nécessaire, les clients doivent définir l’enregistrement CNAME DNS pour qu’il adresse leur nom de domaine complet (FQDN) sur `cdn.adobeaemcloud.com`.
   * si un enregistrement apex est nécessaire, créez un enregistrement A pointant vers les adresses IP suivantes : 151.101.3.10, 151.101.67.10, 151.101.131.10, 151.101.195.10. Les clients ont besoin d’un enregistrement apex si le FQDN correspond à la zone DNS. Vous pouvez le tester en utilisant la commande dig Unix pour vérifier si la valeur SOA de la sortie correspond au domaine. Par exemple, la commande `dig anything.dev.adobeaemcloud.com` renvoie un SOA (Start of Authority, c’est-à-dire la zone) `dev.adobeaemcloud.com`, et il ne s’agit donc pas d’un enregistrement APEX. Par contre, `dig dev.adobeaemcloud.com` renvoie un SOA `dev.adobeaemcloud.com` qui est un enregistrement APEX.
1. Vous serez averti lorsque les certificats SSL arriveront à expiration afin que vous puissiez soumettre à nouveau les nouveaux certificats SSL.

**Limitation du trafic**

Par défaut, dans le cas d’une configuration de réseau de diffusion de contenu géré par Adobe, tout le trafic public peut se diriger vers le service de publication, tant pour les environnements de production que de non-production (de développement et d’évaluation). Si vous souhaitez limiter le trafic à destination du service de publication pour un environnement donné (par exemple, limiter l’évaluation par une plage d’adresses IP), vous devez demander au service clientèle de configurer ces restrictions.

## Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM {#point-to-point-CDN}

Si un client doit utiliser son réseau de diffusion de contenu existant, il peut le gérer et le diriger vers le réseau de diffusion de contenu géré d’Adobe, à condition que les conditions suivantes soient satisfaites :

* Le client doit disposer d’un réseau de diffusion de contenu existant potentiellement onéreux à remplacer.
* Le client doit en assurer la gestion.
* Le client doit être en mesure de configurer le réseau de diffusion de contenu pour utiliser AEM as a Cloud Service. Voir à ce sujet les instructions de configuration ci-dessous.
* Le client doit disposer d’ingénieurs maîtrisant les réseaux de diffusion de contenu, et disponibles pour résoudre les problèmes associés éventuels.
* Le client doit effectuer et réussir un test de charge avant de passer en production.

Instructions de configuration :

1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine.
1. Définissez l’en-tête de l’hôte avec le domaine d’origine, qui est l’entrée du réseau de diffusion de contenu d’Adobe. La valeur doit provenir d’Adobe.
1. Envoyez l’en-tête SNI à l’origine. Tout comme l’en-tête d’hôte, l’en-tête SNI doit être le domaine d’origine.
1. Définissez la valeur `X-Edge-Key`, qui est nécessaire pour acheminer correctement le trafic vers les serveurs AEM. La valeur doit provenir d’Adobe.

Avant d’accepter le trafic en direct, vous devez vérifier auprès du service clientèle d’Adobe que le trafic de bout en bout fonctionne correctement.

Les performances peuvent diminuer en raison du saut supplémentaire, bien que les sauts entre le réseau de diffusion du client et celui géré par Adobe puissent être efficaces.

Notez que cette configuration CDN client est prise en charge pour le niveau de publication, mais pas devant le niveau de création.

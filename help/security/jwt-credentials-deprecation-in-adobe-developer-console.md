---
title: Obsolescence des informations d’identification JWT dans la console Adobe Developer
description: Découvrez l’impact de l’obsolescence des informations d’identification JWT dans la console Adobe Developer sur AEM
source-git-commit: e02e38a5267188111f0392a0a5c7b73e6a4f22b5
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# Obsolescence des informations d’identification JWT dans la console Adobe Developer {#jwt-credentials-deprecation-in-adobe-developer-console}

Les clients Adobe utilisent [Console Adobe Developer](https://developer.adobe.com/console) pour générer des informations d’identification qui permettent l’accès à diverses API. Les clients effectuent un choix parmi différents types d’informations d’identification, allant d’OAuth Server à Server en passant par l’application monopage. L’un de ces types d’informations d’identification, les informations d’identification du compte de service (JWT), a été abandonné au profit des informations d’identification OAuth serveur à serveur. Les informations d’identification du nouveau compte de service (JWT) ne peuvent pas être créées le ou après le 1er mai 2024 et les informations d’identification JWT existantes ne fonctionneront pas le ou après le 1er janvier 2025. Vous pouvez [en savoir plus sur l’obsolescence](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Cet article fournit un contexte supplémentaire sur la manière dont AEM clients as a Cloud Service et AEM 6.5 doivent gérer l’obsolescence.

À ce stade, la principale leçon à retenir est que AEM fonctionnalités ne prennent pas encore en charge les nouvelles informations d’identification OAuth serveur à serveur. La prise en charge sera assurée prochainement : d’ici la mi-avril 2024, par le biais d’une version AEM pour AEM as a Cloud Service, et d’un package de compatibilité spécial à installer pour la version 6.5 d’Adobe, si vous exécutez le dernier Service Pack 20 ou version antérieure (Service Pack 21 et version ultérieure l’inclura automatiquement). Vous avez peut-être reçu un courrier électronique contenant des instructions pour migrer vos informations d’identification JWT, mais assurez-vous que vous pouvez et devez attendre la migration des informations d’identification jusqu’à ce qu’AEM prenne en charge le nouveau type d’informations d’identification OAuth Server-to-Server.

Les sections ci-dessous répertorient les scénarios où les clients doivent (ou dans certains cas ne doivent pas) remplacer leurs informations d’identification de compte de service (JWT) par des informations d’identification OAuth Server-to-Server, une fois qu’AEM les prend en charge à la mi-avril. [Lire comment](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) pour remplacer les informations d’identification ultérieurement.

>[!NOTE]
>
>La variable [**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (notez que la variable **AEM** dans le nom, qui le distingue de la fonction **Adobe** Developer Console) fournit un utilitaire de génération [JWT Tokens](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) utilisé pour les API serveur à serveur. Ces informations d’identification ne sont pas obsolètes et peuvent continuer à être utilisées.


## Intégration d’AEM à d’autres solutions d’Adobe {#integrating-aem-with-other-adobe-solutions}

**Action**: patientez jusqu’à la mi-avril 2024, date à laquelle AEM le prend en charge.

**Versions d’AEM pertinentes**: AEM as a Cloud Service et Adobe Managed Services (Service Pack 20 et versions antérieures).


Les clients AEM utilisent l’interface utilisateur d’AEM auteur pour configurer des intégrations avec toutes les autres solutions d’Adobe. Par exemple, Adobe Target, Adobe Analytics, Adobe Launch, AFCS, etc.

![Intégration d’AEM à d’autres solutions](/help/security/assets/jwt-deprecation.png)

Par exemple, voici : [les instructions](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html?lang=en) pour configurer l’intégration avec Adobe Target. La clé API dans la variable [Réalisation de la configuration IMS dans AEM](https://docs.mktossl.com/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims.html#completing-the-ims-configuration-in-aem) doit être migrée vers le type d’informations d’identification OAuth Server-to-Server, une fois AEM prise en charge de ces informations d’identification mi-avril. Ces instructions seront mises à jour à la mi-avril afin de vous aider à appliquer les nouvelles informations d’identification OAuth serveur à serveur.

## API Cloud Manager {#cloud-manager-apis}

**Action**: patientez jusqu’à la mi-avril 2024, date à laquelle AEM le prend en charge.

**Versions d’AEM pertinentes**: AEM as a Cloud Service et Adobe Managed Services (Service Pack 20 et versions antérieures).

Les clients créent des projets de la console Adobe Developer pour pouvoir appeler [API de Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). Les informations d’identification du projet Adobe Developer doivent être migrées vers le type OAuth Server-to-Server, une fois qu’AEM et Cloud Manager le prennent en charge.

## Projets générés automatiquement {#autogen-projects}

**Action**: ne migrez pas, car Adobe migre en votre nom.

**Versions d’AEM pertinentes**: uniquement AEM as a Cloud Service.

Lorsque Cloud Manager fournit AEM environnements as a Cloud Service, il génère automatiquement un projet de console Adobe Developer avec des informations d’identification JWT. Ce projet est marqué comme en lecture seule, comme illustré dans la capture d’écran ci-dessous. Les clients ne peuvent pas et ne doivent pas tenter de migrer ces projets vers les informations d’identification OAuth serveur à serveur ; au lieu de cela, Adobe migre ces projets tout seul, avant que les informations d’identification ne ne soient plus utilisables.

![Projets générés automatiquement](/help/security/assets/jwt-deprecation-autogen-projects.png)


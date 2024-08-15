---
title: Obsolescence des informations d’identification JWT dans Adobe Developer Console
description: Découvrez l’impact de l’obsolescence des informations d’identification JWT dans Adobe Developer Console sur AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
feature: Security
role: Admin
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 97%

---

# Obsolescence des informations d’identification JWT dans Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>Les clients AEM 6.5 doivent référencer [la documentation comparable pour AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) pour plus d’informations.

Les clientes et clients Adobe utilisent [Adobe Developer Console](https://developer.adobe.com/console) pour générer des informations d’identification qui permettent l’accès à diverses API. Les clientes et clients effectuent un choix parmi différents types d’informations d’identification, allant d’OAuth serveur à serveur jusqu’à l’application monopage. L’un de ces types d’informations d’identification, celui des informations d’identification du compte de service (JWT), a été abandonné au profit des informations d’identification OAuth serveur à serveur. Les informations d’identification du nouveau compte de service (JWT) ne peuvent plus être créées à partir du 3 juin 2024, et les informations d’identification JWT existantes ne fonctionneront plus à partir du 27 janvier 2025. Vous pouvez [en savoir plus sur l’obsolescence](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Cet article fournit un contexte supplémentaire sur la manière dont AEM as a Cloud Service doit gérer l’obsolescence.

Le principal point à retenir est qu’AEM prend désormais en charge les nouvelles informations d’identification OAuth de serveur à serveur pour AEM as a Cloud Service. Vous avez peut-être reçu un e-mail contenant des instructions pour migrer vos informations d’identification JWT. Cette migration peut maintenant être effectuée.

Les sections ci-dessous répertorient les scénarios où les clientes et clients doivent (ou dans certains cas ne doivent pas) remplacer leurs informations d’identification de compte de service (JWT) par des informations d’identification OAuth serveur à serveur, maintenant qu’AEM les prend en charge. [Découvrez comment](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) migrer les informations d’identification.

>[!NOTE]
>
>[**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (notez la mention **AEM** dans le nom, qui permet une distinction avec **Adobe** Developer Console) fournit un utilitaire pour générer des [jetons JWT](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) utilisés pour les API serveur à serveur. Ces informations d’identification ne sont pas obsolètes et peuvent continuer à être utilisées.

## Intégrer AEM à d’autres solutions Adobe {#integrating-aem-with-other-adobe-solutions}

**Action** : migrez votre configuration, car AEM prend désormais en charge les informations d’identification OAuth.

**Versions d’AEM pertinentes** : AEM as a Cloud Service

Les clientes et clients AEM utilisent AEM pour configurer des intégrations à de nombreuses autres solutions Adobe. Par exemple, Adobe Target, Adobe Analytics et d’autres.

Voir [Configuration des intégrations IMS pour AEM as a Cloud Service](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) pour plus de détails sur la façon d’effectuer ce qui suit :

* créer des configurations avec des informations d’identification OAuth ;
* migrer les configurations créées avec les informations d’identification JWT pour utiliser les informations d’identification OAuth.

## API Cloud Manager {#cloud-manager-apis}

**Action** : migrez vos informations d’identification JWT vers les informations d’identification OAuth, désormais prises en charge par Cloud Manager.

**Versions d’AEM pertinentes** : AEM as a Cloud Service

Les clientes et clients créent des projets Adobe Developer Console pour pouvoir appeler les [API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). Les informations d’identification du projet Adobe Developer doivent être migrées vers le type OAuth serveur à serveur avant que les informations d’identification JWT obsolètes n’expirent en janvier 2025.

## Projets générés automatiquement {#autogen-projects}

**Action** : n’effectuez pas de migration, car Adobe va le faire en votre nom.

**Versions d’AEM pertinentes** : AEM as a Cloud Service

Lorsque Cloud Manager fournit des environnements AEM as a Cloud Service, un projet Adobe Developer Console est génèré automatiquement avec des informations d’identification JWT. Ce projet est marqué comme en lecture seule, comme illustré dans la copie d’écran ci-dessous. Les clientes et clients ne peuvent pas et ne doivent pas tenter de migrer ces projets vers des informations d’identification OAuth de serveur à serveur. Au lieu de cela, Adobe s’occupera de migrer ces projets, avant que les informations d’identification ne soient plus utilisables.

![Projets générés automatiquement](/help/security/assets/jwt-deprecation-autogen-projects.png)

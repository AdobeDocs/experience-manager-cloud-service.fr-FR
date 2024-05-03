---
title: Obsolescence des informations d’identification JWT dans Adobe Developer Console
description: Découvrez l’impact de l’obsolescence des informations d’identification JWT dans Adobe Developer Console sur AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
source-git-commit: 802e29017d3f1e59ee1676b4172292cb3453648a
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 74%

---

# Obsolescence des informations d’identification JWT dans Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>Les clientes et les clients d’AEM 6.5 peuvent consulter [cet article](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console) pour plus d’informations.

Les clientes et clients Adobe utilisent [Adobe Developer Console](https://developer.adobe.com/console) pour générer des informations d’identification qui permettent l’accès à diverses API. Les clientes et clients effectuent un choix parmi différents types d’informations d’identification, allant d’OAuth serveur à serveur jusqu’à l’application monopage. L’un de ces types d’informations d’identification, celui des informations d’identification du compte de service (JWT), a été abandonné au profit des informations d’identification OAuth serveur à serveur. Les informations d’identification du nouveau compte de service (JWT) ne peuvent plus être créées à partir du 3 juin 2024, et les informations d’identification JWT existantes ne fonctionneront plus à partir du 27 janvier 2025. Vous pouvez [en savoir plus sur l’obsolescence](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

Cet article fournit un contexte supplémentaire sur la manière dont AEM as a Cloud Service doit gérer l’obsolescence.

Actuellement, la principale leçon à retenir est que les fonctionnalités AEM ne prennent pas encore en charge les nouvelles informations d’identification OAuth serveur à serveur. La prise en charge sera bientôt assurée d’ici la mi-mai 2024 par le biais d’une version AEM pour AEM as a Cloud Service. Vous avez peut-être reçu un e-mail contenant des instructions pour migrer vos informations d’identification JWT, mais vous pouvez et devriez attendre avant de migrer des informations d’identification jusqu’à ce qu’AEM prenne en charge le nouveau type d’informations d’identification OAuth serveur à serveur.

Les sections ci-dessous répertorient les scénarios où les clients doivent (ou parfois ne doivent pas) remplacer leurs informations d’identification de compte de service (JWT) par des informations d’identification OAuth Server-to-Server, une fois qu’AEM les prend en charge à la mi-mai. [Lisez comment](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) remplacer les informations d’identification ultérieurement.

>[!NOTE]
>
>[**AEM** Developer Console](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) (notez la mention **AEM** dans le nom, qui permet une distinction avec **Adobe** Developer Console) fournit un utilitaire pour générer des [jetons JWT](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) utilisés pour les API serveur à serveur. Ces informations d’identification ne sont pas obsolètes et peuvent continuer à être utilisées.


## Intégrer AEM à d’autres solutions Adobe {#integrating-aem-with-other-adobe-solutions}

**Action**: patientez jusqu’à la mi-mai 2024, date à laquelle AEM le prend en charge (cet article sera mis à jour à ce moment-là).

**Versions d’AEM pertinentes** : AEM as a Cloud Service

Les clientes et clients AEM utilisent l’interface utilisateur de création AEM pour configurer des intégrations à toutes les autres solutions Adobe. Par exemple, Adobe Target, Adobe Analytics, Adobe Launch, AFCS, etc.

![Intégrer AEM à d’autres solutions](/help/security/assets/jwt-deprecation.png)

Par exemple, voici les [instructions](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims) pour configurer l’intégration à Adobe Target. La clé API dans la variable [Réalisation de la configuration IMS dans AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/integrations/integration-adobe-target-ims#completing-the-ims-configuration-in-aem) doit être migrée vers le type d’informations d’identification OAuth Server-to-Server, une fois qu’AEM prend en charge ces informations d’identification à la mi-mai. Ces instructions seront mises à jour à la mi-mai pour vous aider à appliquer les nouvelles informations d’identification OAuth serveur à serveur.

## API Cloud Manager {#cloud-manager-apis}

**Action**: migration vers les informations d’identification OAuth serveur à serveur.

**Versions d’AEM pertinentes** : AEM as a Cloud Service

Les clientes et clients créent des projets Adobe Developer Console pour pouvoir appeler les [API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/). Les informations d’identification du projet Adobe Developer doivent être migrées vers le type OAuth Server-to-Server avant que les informations d’identification JWT obsolètes n’expirent en janvier 2025.

## Projets générés automatiquement {#autogen-projects}

**Action** : n’effectuez pas de migration, car Adobe va le faire en votre nom.

**Versions d’AEM pertinentes** : AEM as a Cloud Service

Lorsque Cloud Manager fournit des environnements AEM as a Cloud Service, il génère automatiquement un projet Adobe Developer Console avec des informations d’identification JWT. Ce projet est marqué en lecture seule, comme illustré dans la copie d’écran ci-dessous. Les clientes et clients ne peuvent pas et ne devraient pas tenter de migrer ces projets vers les informations d’identification OAuth serveur à serveur. Au lieu de cela, Adobe va migrer ces projets avant que les informations d’identification ne soient plus utilisables.

![Projets générés automatiquement](/help/security/assets/jwt-deprecation-autogen-projects.png)

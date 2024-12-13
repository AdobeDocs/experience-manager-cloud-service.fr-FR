---
title: Obsolescence des informations d’identification JWT dans Adobe Developer Console
description: Découvrez l’impact de l’obsolescence des informations d’identification JWT dans Adobe Developer Console sur AEM.
exl-id: 7c811081-484c-41f7-a289-4e9a10a837b3
feature: Security
role: Admin
source-git-commit: d3c00c33925a23ad5b1080c1e864cfdb5a8d1c1b
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 63%

---

# Obsolescence des informations d’identification JWT dans Adobe Developer Console {#jwt-credentials-deprecation-in-adobe-developer-console}

>[!NOTE]
>
>Pour plus d’informations, les clientes et clients d’AEM 6.5 doivent se reporter à [la documentation comparable pour AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/security/jwt-credentials-deprecation-in-adobe-developer-console).

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

## FAQ sur les projets générés automatiquement {#autogen-projects-faqs}

Cette section répond aux questions les plus fréquentes sur l’obsolescence des informations d’identification JWT pour les projets générés automatiquement dans AEM as a Cloud Service.

**Comment puis-je identifier les projets générés automatiquement ?**
Accéder au Adobe Developer Console | Section Projets.  Les projets générés automatiquement par AEM as a Cloud Service comporteront une icône de cadenas avec un identifiant « généré automatiquement ».  Les projets générés automatiquement suivent le format AEM-p######-e##### et sont créés par l’utilisateur du compte technique.

<img width="439" alt="image" src="https://git.corp.adobe.com/storage/user/16149/files/6b20a8a3-3711-4741-8f2c-ec5e36fe97cc">


**Que faire si nous rencontrons des problèmes avec nos projets générés automatiquement ?**

Contactez L’Assistance Clientèle D’Adobe [](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

**Dois-je procéder à la migration de nos projets générés automatiquement ?**

Aucune action n’est requise, car Adobe migrera les données générées automatiquement en votre nom pour les environnements disposant de la version AEM 17258 (août 2024) et ultérieure.

**Quels sont les délais de migration des projets générés automatiquement ?**

L’Adobe lancera une approche de migration progressive au premier trimestre 2025, en commençant par les environnements de développement.

**Comment notre instance AEM as a Cloud Service sera-t-elle affectée si nous disposons d’une version d’AEM qui est plus ancienne que la 17258 de mise à jour d’AEM (août 2024) ?**

Les intégrations de projets générées automatiquement cesseront de fonctionner si elles ne sont pas migrées vers OAuth d’ici juin 2025.

Pour assurer une transition fluide, les clients doivent contacter rapidement l&#39;Assistance clientèle d&#39;Adobe [](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) et commencer le processus de mise à jour vers la [dernière version d&#39;AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest). Cela laissera suffisamment de temps pour les tests de régression et permettra à l’Adobe de gérer efficacement la migration des projets.

**Puis-je effectuer une mise à niveau vers une version OAuth prise en charge sans mettre à niveau ma version AEM as a Cloud Service AEM ?**

Non. Pour assurer une transition fluide, les clients doivent contacter rapidement l&#39;Assistance clientèle d&#39;Adobe [](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) et commencer le processus de mise à jour vers la [dernière version d&#39;AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/maintenance/latest). Cela laissera suffisamment de temps pour les tests de régression et permettra à l’Adobe de gérer efficacement la migration des projets.

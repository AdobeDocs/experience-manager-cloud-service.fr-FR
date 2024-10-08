---
title: Intégration [!DNL Experience Manager Assets] avec  [!DNL Adobe Workfront]
description: Présentation de l’intégration entre  [!DNL Assets]  et  [!DNL Workfront]
role: Admin, Leader, Architect
feature: Workfront Integrations and Apps
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 84%

---

# Intégration d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] à [!DNL Adobe Workfront] {#assets-integration-overview}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

[!DNL Adobe Workfront] est une application de gestion du travail qui vous permet de gérer l’ensemble du cycle de vie du travail en un seul endroit. L’intégration entre [!DNL Workfront] et [!DNL Adobe Experience Manager Assets] permet aux entreprises d’améliorer la vitesse du contenu et le délai de mise sur le marché en établissant des liens intrinsèques entre le travail et la gestion des ressources numériques. Dans le cadre de la gestion de leur travail dans Workfront, les utilisateurs ont accès aux documents et images requis.

Adobe propose [integrate [!DNL Workfront] et [!DNL Adobe Experience Manager Assets] nativement (prise en charge des Assets Essentials et des as a Cloud Service Assets)](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html?lang=fr).

Avec l’intégration d’Experience Manager native, vous pouvez :

* Configuration rapide de l’intégration dans Workfront.

* Création automatique de dossiers liés entre Workfront et Experience Manager.

* Synchronisation aisée des métadonnées pour les ressources liées existantes.

* Mettez automatiquement à jour les métadonnées des projets lorsqu’elles sont modifiées dans Workfront.

* Connectez facilement plusieurs référentiels Experience Manager Assets à un environnement Workfront ou plusieurs environnements Workfront à un référentiel Experience Manager Assets en utilisant plusieurs identifiants d’organisation.


## Adobe Workfront pour Experience Manager Enhanced Connector {#enhanced-connector-information}


Depuis juin 2022, Adobe a lancé une nouvelle intégration native pour connecter Workfront à Adobe Experience Manager Assets as a Cloud Service. Cette intégration est devenue la méthode requise pour connecter ces deux solutions. Toute nouvelle implémentation future du connecteur amélioré (version 1.9.8 et versions ultérieures) pour connecter Workfront à AEM Assets as a Cloud Service est bloquée. Pour plus d’informations sur la configuration de cette intégration, voir [Configurer l’intégration Experience Manager Assets as a Cloud Service](workfront-connector-configure.md).

>[!NOTE]
>
>Adobe ne prend pas en charge l’utilisation en parallèle du connecteur amélioré Workfront pour Experience Manager et de l’intégration d’Experience Manager.

Pour les installations antérieures à juin 2022, voici quelques points à noter pour le déploiement et la configuration de [!DNL Adobe Workfront for Experience Manager enhanced connector] :

* Adobe nécessite le déploiement et la configuration de [!DNL Adobe Workfront for Experience Manager enhanced connector] uniquement par le biais de partenaires certifiés ou [!DNL Adobe Professional Services]. S’il est déployé et configuré sans partenaire certifié ou sans [!DNL Adobe Professional Services], il n’est pas pris en charge par Adobe.
* Adobe peut publier des mises à jour d’[!DNL Adobe Workfront] et d’[!DNL Adobe Experience Manager] qui rendent ce connecteur redondant ; si cela se produit, les clients peuvent être amenés à cesser d’utiliser ce connecteur.
* Adobe prend en charge les versions 1.7.4 et supérieures du connecteur. Les versions précédentes et personnalisées ne sont pas prises en charge. Pour vérifier la version du connecteur amélioré, consultez l’étape 5(a) des [instructions d’installation du connecteur amélioré](workfront-connector-install.md).
* Consultez la section [Examen de certification des partenaires pour Workfront pour le connecteur amélioré Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Pour plus d’informations sur l’examen, consultez le [Guide d’examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).
---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.3.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.3.0
feature: Release Information
exl-id: ab43605d-d46e-43de-b71f-fab610609550
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 63%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.3.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.3.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.26 est le 16 mars 2022.

### Nouveautés {#what-is-new-bpa}

* Capacité à détecter les ressources non traitées. Si des ressources non traitées sont détectées, elles doivent être définies sur traitées ou supprimées du jeu de migration lors du transfert de contenu afin d’éviter des problèmes lors de l’ingestion du contenu.
* Capacité à détecter si le contenu comporte plus de 1 000 URL de redirection vers un microsite. L’utilisation d’un nombre élevé d’URL de redirection vers un microsite n’est pas conforme avec les bonnes pratiques, car elle surcharge les serveurs de Dispatcher et de publication.
* Capacité à identifier les problèmes liés aux définitions d’index Oak et de détecter les incompatibilités avec AEM as a Cloud Service.
* Capacité à détecter et à générer des rapports sur l’utilisation des configurations de l’externaliseur. Dans AEM Externalizer as a Cloud Service, les configurations sont définies par Cloud Manager. Par conséquent, les configurations Externalizer existantes doivent être reconfigurées pour maintenir la compatibilité.

### Correctifs {#bug-fixes-bpa}

* Dans certains scénarios, l’exécution de l’analyseur de bonnes pratiques échouaient en raison d’une erreur d’affirmation de FormsSelectiveFeaturesAnalysis.
* L’analyseur de bonnes pratiques signalait les résultats liés au modèle WRK comme MAJEURS plutôt que CRITIQUES.
* BPA signalait de manière erronée les résultats liés aux définitions d’index Oak dans ui.apps comme étant CRITIQUES.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.9.0 est le 28 février 2022.

### Nouveautés {#what-is-new-ctt}

* Garde-fous de vérification de la taille : la fonctionnalité Vérification de la taille de l’outil de transfert de contenu permet de réduire le nombre de transferts de contenu ayant échoué. Grâce à la fonction Vérifier la taille, les utilisateurs peuvent déterminer s’ils disposent d’un espace disque suffisant dans la variable `crx-quickstart` sous-répertoire avant extraction. Ils peuvent également estimer la taille du jeu de migration et vérifier si elle est prise en charge. Si l’une de ces vérifications est enfreinte, les utilisateurs voient des avertissements dans l’interface utilisateur du CTT. Grâce à ce garde-fous de sécurité, vous pouvez éviter les échecs de transfert de contenu et discuter de manière proactive des options de migration avec l’assistance clientèle d’Adobe. Voir [Détermination de la taille du jeu de migration et de l’espace disque](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr#migration-set-size) pour plus d’informations.

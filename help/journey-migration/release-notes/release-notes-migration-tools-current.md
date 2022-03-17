---
title: Notes de mise à jour des outils de migration dans AEM version as a Cloud Service 2022.3.0
description: Notes de mise à jour des outils de migration dans AEM version as a Cloud Service 2022.3.0
feature: Release Information
source-git-commit: c497424271ea960d22a30b4a6c66432935ec820d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 13%

---


# Notes de mise à jour des outils de migration dans AEM version as a Cloud Service 2022.3.0 {#release-notes}

Cette page présente les notes de mise à jour des outils de migration dans AEM as a Cloud Service 2022.3.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.26 est le 16 mars 2022.

### Nouveautés {#what-is-new-bpa}

* Capacité à détecter les ressources non traitées. Si des ressources non traitées sont détectées, ces ressources doivent être définies sur traitées ou doivent être supprimées du jeu de migration lors du transfert de contenu afin d’éviter des problèmes lors de l’ingestion de contenu.
* Possibilité de détecter si le contenu comporte plus de 1 000 URL de redirection vers un microsite. L’utilisation d’un nombre élevé d’URL de redirection vers un microsite n’est pas une bonne pratique, car elle charge les serveurs de Dispatcher et de publication.
* Possibilité d’identifier les problèmes liés aux définitions d’index Oak et de détecter les incompatibilités avec AEM as a Cloud Service.
* Possibilité de détecter et de générer des rapports sur l’utilisation des configurations de l’externaliseur. Dans AEM les configurations de l’externaliseur as a Cloud Service sont définies par Cloud Manager, les configurations de l’externaliseur existantes doivent donc être restructurées pour maintenir la compatibilité.

### Correctifs {#bug-fixes-bpa}

* Dans certains scénarios, l’exécution de BPA a échoué en raison d’une erreur d’affirmation de FormsSelectiveFeaturesAnalysis. Ce problème a été résolu.
* Le BPA a rapporté que les résultats liés au modèle de WRK étaient MAJEURS plutôt que CRITIQUES. Ce problème a été résolu.
* La BPA signalait de manière incorrecte les résultats liés aux définitions d’index OAK dans ui.apps comme étant CRITIQUES. Ce problème a été résolu.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.9.0 est le 28 février 2022.

### Nouveautés {#what-is-new-ctt}

* Vérifier les barrières de taille : la fonction Taille de contrôle de l’outil de transfert de contenu permet de réduire les transferts de contenu ayant échoué.  Grâce à la fonction Vérifier la taille , les utilisateurs peuvent 1) déterminer s’ils disposent d’un espace disque suffisant dans la variable `crx-quickstart` sous-répertoire avant extraction, et 2) estimer la taille du jeu de migration et vérifier s’il est pris en charge. Si l’une de ces vérifications est enfreinte, les utilisateurs verront des avertissements dans l’interface utilisateur de CTT. Grâce à cette barrière de sécurité, vous pouvez éviter les échecs de transfert de contenu et discuter de manière proactive des options de migration avec l’assistance clientèle d’Adobe. Voir [Détermination de la taille du jeu de migration et de l’espace disque](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#migration-set-size) pour plus d’informations.
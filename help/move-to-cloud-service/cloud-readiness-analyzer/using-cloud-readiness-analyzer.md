---
title: Utilisation de Cloud Readiness Analyzer
description: Utilisation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 317dd08600df9c7127cf8502341f93758ac8ce0b
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 7%

---


# Utilisation de Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Considérations importantes pour l’utilisation de Cloud Readiness Analyzer {#imp-considerations}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte lors de l&#39;exécution de l&#39;outil Cloud Readiness Analyzer (CRA) :

* L’ARC est prise en charge sur les instances AEM source avec les versions 6.1 et ultérieures.
* L&#39;ARC peut s&#39;exécuter sur n&#39;importe quel environnement. Toutefois, afin d’augmenter le taux de détection et d’éviter tout ralentissement sur les instances critiques de l’entreprise, il est recommandé de l’exécuter sur les environnements d’évaluation de l’auteur source qui sont le plus proches possible des  de production dans les domaines de la personnalisation, de la configuration, du contenu et des applications utilisateur. Il peut également être exécuté sur un clone de l’environnement de publication.

## Disponibilité {#availability}

L&#39;analyseur de l&#39;état de préparation du cloud (CRA) peut être téléchargé sous la forme d&#39;un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais de Package Manager sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Téléchargez l’outil Cloud Readiness Analyzer (CRA) depuis le site en attente.

## Exécution de Cloud Readiness Analyzer {#running-tool}

Suivez cette section pour savoir comment exécuter Cloud Readiness Analyzer :

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

### Affichage des résultats {#viewing-the-results}

Il existe deux façons de vue de la production de l&#39;ARC :

1. Utilisation du rapport organisé (disponible sur AEM version 6.3 et ultérieure) Consultez Planification et état des Documents de l&#39;ARC pour décrire les niveaux d&#39;importance dans le rapport.

Pour vue la sortie de l’ARC (peut être utilisée avec AEM version 6.1 et ultérieure) :

1. Accédez à la console Web AEM en accédant à.

1. Sélectionnez Etat - Cloud Readiness Analyzer comme illustré dans l’image ci-dessous.
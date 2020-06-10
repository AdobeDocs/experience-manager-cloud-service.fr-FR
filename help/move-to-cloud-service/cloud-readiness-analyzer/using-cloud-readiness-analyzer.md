---
title: Utilisation de Cloud Readiness Analyzer
description: Utilisation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 3d818278c53f3d3b4c5b53aa5b78d06d876bf05f
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 6%

---


# Utilisation de Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Considérations importantes pour l’utilisation de Cloud Readiness Analyzer {#imp-considerations}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte lors de l&#39;exécution de l&#39;outil Cloud Readiness Analyzer (CRA) :

* L’ARC est prise en charge sur les instances AEM source avec les versions 6.1 et ultérieures.
* L&#39;ARC peut s&#39;exécuter sur n&#39;importe quel environnement.

   >[!NOTE]
   >Afin d&#39;augmenter le taux de détection et d&#39;éviter tout ralentissement sur les instances critiques de l&#39;entreprise, il est recommandé d&#39;exécuter CRA sur les environnements d&#39;évaluation de l&#39;auteur source qui sont aussi proches que possible des  de production dans les domaines de la personnalisation, de la configuration, du contenu et des applications utilisateur. Il peut également être exécuté sur un clone de l’environnement de publication.

## Disponibilité {#availability}

L&#39;analyseur de l&#39;état de préparation du cloud (CRA) peut être téléchargé sous la forme d&#39;un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Téléchargez l’outil Cloud Readiness Analyzer (CRA) depuis le site *en attente*.

## Exécution de Cloud Readiness Analyzer {#running-tool}

Suivez cette section pour savoir comment exécuter Cloud Readiness Analyzer :

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

### Affichage des résultats {#viewing-the-results}

Il existe deux façons de vue de la production de l&#39;ARC :

1. Utilisation du rapport organisé

   >[!NOTE]
   >Le rapport organisé est disponible sur AEM version 6.3 et ultérieure.

Consultez la planification et le statut des Documents de l&#39;ARC pour décrire les niveaux d&#39;importance dans le rapport.

1. Affichage de la sortie de l’ARC (peut être utilisée avec AEM version 6.1 et ultérieure) :

   1. Accédez à la console Web AEM en accédant à.

   1. Sélectionnez Etat - Cloud Readiness Analyzer comme illustré dans l’image ci-dessous.

#### Comprendre les niveaux d&#39;importance dans le rapport {#importance-levels}

Le tableau suivant décrit la signification des différents niveaux d’importance du Détecteur de schémas et de l’Analyseur de l’état de préparation du cloud.

| Niveau d’importance | Description |
|--- |--- |
| INFO/0 | Cette conclusion est fournie à titre d&#39;information. |
| CONSEILLER/1 | Cette recherche peut poser un problème de mise à niveau. Il est recommandé d&#39;approfondir l&#39;enquête. |
| MAJOR/2 | Il est probable que cette découverte soit un problème de mise à niveau qui devrait être résolu. |
| CRITIQUE/3 | Il est très probable que cette découverte soit un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |
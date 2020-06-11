---
title: Utilisation de Cloud Readiness Analyzer
description: Utilisation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 47773a56f8bb24342281068a8c4d03d6edfb9277
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 5%

---


# Utilisation de Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Considérations importantes pour l’utilisation de Cloud Readiness Analyzer {#imp-considerations}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte lors de l&#39;exécution de l&#39;outil Cloud Readiness Analyzer (CRA) :

* CRA est pris en charge sur les instances AEM source avec les versions 6.1 et ultérieures
* L&#39;ARC peut s&#39;exécuter sur n&#39;importe quel environnement (de préférence *un environnement d&#39;étape* ).

   >[!NOTE]
   >Afin d&#39;augmenter le taux de détection et d&#39;éviter tout ralentissement sur les instances critiques de l&#39;entreprise, il est recommandé d&#39;exécuter CRA sur les environnements d&#39;évaluation de l&#39;auteur source qui sont aussi proches que possible des  de production dans les domaines de la personnalisation, de la configuration, du contenu et des applications utilisateur. Il peut également s’exécuter sur un clone de l’environnement de *publication* .

## Disponibilité {#availability}

L&#39;analyseur de l&#39;état de préparation de Cloud peut être téléchargé dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Téléchargez Cloud Readiness Analyzer depuis le portail de distribution de logiciels *en attente*.

## Exécution de Cloud Readiness Analyzer {#running-tool}

Suivez cette section pour savoir comment exécuter Cloud Readiness Analyzer :

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

### Affichage des résultats {#viewing-the-results}

>[!IMPORTANT]
>Les rapports générés à partir de Cloud Readiness Analyzer sont basés sur les détecteurs de schémas. Consultez Détecteurs [de](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) schémas pour plus d’informations.

Il existe deux façons de vue de la sortie à partir de Cloud Readiness Analyzer :

1. **Utilisation du rapport organisé**

   >[!NOTE]
   >Le rapport organisé est disponible sur AEM version 6.3 et ultérieure.

   Ou,

1. **Voir la sortie de l&#39;ARC**

   Suivez les étapes ci-dessous pour vue de la sortie de Cloud Readiness Analyzer :

   >[!NOTE]
   >Les étapes ci-dessous s’appliquent à AEM version 6.1 et ultérieure.

   1. Accédez à la console **Web** AEM à l’aide de `https://serveraddress:serverport/system/console/configMgr`.

   1. Select **Status - Pattern Detector** as shown in the figure below.

#### Affichage du rapport dans les instances AEM 6.1 {#aem-instances-report}

Vous pouvez télécharger le rapport csv pour AEM 6.1.Ce rapport est en attente.

#### Comprendre les niveaux d&#39;importance dans le rapport {#importance-levels}

Le tableau suivant décrit la signification des différents niveaux d’importance du Détecteur de schémas et de l’Analyseur de l’état de préparation du cloud.

| Niveau d’importance | Description |
|--- |--- |
| INFO/0 | Cette conclusion est fournie à titre d&#39;information. |
| CONSEILLER/1 | Cette recherche peut poser un problème de mise à niveau. Il est recommandé d&#39;approfondir l&#39;enquête. |
| MAJOR/2 | Il est probable que cette découverte soit un problème de mise à niveau qui devrait être résolu. |
| CRITIQUE/3 | Il est très probable que cette découverte soit un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |
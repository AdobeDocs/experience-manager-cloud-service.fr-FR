---
title: Utilisation de Cloud Readiness Analyzer
description: Utilisation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 1739f81d4894f3e04cc4119f344a3bea5bd042d8
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 3%

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

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Une fois que vous avez cliqué sur **Cloud Readiness Analyzer**, l’outil début la génération du rapport et, après quelques minutes, le rapport récapitulatif est disponible sur votre instance AEM.

   >[!NOTE]
   >Vous devrez faire défiler la page vers le bas pour vue au rapport complet.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-2.png)

### Affichage des résultats dans le rapport de synthèse {#viewing-the-results}

>[!IMPORTANT]
>Les rapports générés à partir de Cloud Readiness Analyzer sont basés sur les détecteurs de schémas. Consultez Détecteurs [de](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) schémas pour plus d’informations.

Une fois que vous avez fait défiler la page jusqu&#39;à la vue du rapport de synthèse complet, vous pouvez voir les informations suivantes pour chacune des catégories surlignées dans le rapport :

1. **Niveau d’importance**

   Le tableau suivant décrit la signification des différents niveaux d’importance du Détecteur de schémas et de l’Analyseur de l’état de préparation du cloud.

   | Niveau d’importance | Description |
   |--- |--- |
   | INFO/0 | Cette conclusion est fournie à titre d&#39;information. |
   | CONSEILLER/1 | Cette recherche peut poser un problème de mise à niveau. Il est recommandé d&#39;approfondir l&#39;enquête. |
   | MAJOR/2 | Il est probable que cette découverte soit un problème de mise à niveau qui devrait être résolu. |
   | CRITIQUE/3 | Il est très probable que cette découverte soit un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |

1. **Description** La description fournit des informations sur la catégorie rapportée.

1. **URL** de la documentation L’URL de la documentation vous permet de vue de la documentation technique pour le type associé.

1. **Message** Description de la recherche dans un seul message.

### Affichage des résultats au format CSV {#viewing-the-results-csv}

Le rapport récapitulatif est disponible dans l’interface utilisateur d’AEM. Vous pouvez télécharger le rapport complet au format CSV (valeurs séparées par des virgules), ce qui s’avère utile lors du processus de refactorisation.

Suivez les étapes ci-dessous pour générer un format CSV de votre rapport de synthèse :

1. 
   1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

1. Une fois le rapport disponible, cliquez sur **CSV** pour télécharger le rapport de synthèse complet au format CSV (valeurs séparées par des virgules), comme le montre la figure ci-dessous.

![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-3.png)


#### Affichage du rapport dans les instances AEM 6.1 {#aem-instances-report}

Suivez les étapes ci-dessous pour télécharger le rapport CSV pour Adobe Experience Manager (AEM) 6.1 :

1.Navigate to **Adobe Experience Manager Web Console
Configuration** using `https://serveraddress:serverport/system/console/configMgr`.

1. Sélectionnez l’onglet **Etat** et recherchez le Détecteur **de** schémas dans la liste déroulante, comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-4.png)

1. Vous pouvez télécharger le rapport de synthèse dans un dossier zip ou au format JSON.



---
title: Évaluation de la complexité du passage au service Cloud
description: Évaluation de la complexité du passage au service Cloud
translation-type: tm+mt
source-git-commit: 83f7a1d57fae92e6ce15e4d9d6e00682d4596d05

---


# Évaluation de la complexité du passage au service Cloud {#accesing-complexity}

## Présentation {#overview}

L’analyseur de l’état de préparation du cloud (CRA) vous permet de vérifier que les instances AEM existantes sont prêtes à passer au service Cloud en détectant les modèles qui :

* Utilisez une fonctionnalité AEM 6.x qui n’est actuellement pas prise en charge sur le service Cloud.

* Violer certaines règles qui seront affectées par le passage au service Cloud

>[!NOTE]
>La production de l&#39;ARC accélère l&#39;évaluation de l&#39;effort de développement qui sera nécessaire pour passer au service Cloud.

## Configuration de Cloud Readiness Analyzer {#setting-up-cra}

L’ARC est publiée sous forme de package qui fonctionne sur toutes les versions source d’AEM à partir de XX et plus, explorant un passage au service Cloud.

Il est disponible sur le portail de distribution de logiciels et peut être installé à l’aide de Package Manager.

### Utilisation de Cloud Readiness Analytics {#using-cra}

>[!NOTE]
> L&#39;ARC peut s&#39;exécuter sur n&#39;importe quel  , y compris les instances de développement local.

>[IMPORTANT]
>Toutefois, afin d’augmenter le taux de détection et d’éviter tout ralentissement sur les instances critiques de l’entreprise, il est recommandé de l’exécuter sur des  d’évaluation  aussi proches que possible des de production dans les domaines des applications, du contenu et des configurations utilisateur.

### Affichage de la sortie sur l’analyseur de l’état de préparation du cloud {#viewing-output-cra}


1. Accédez à la console Web AEM en accédant à la configuration **de la console Web** Adobe Experience Manager à l’aide de `https://serveraddress:serverport/system/console/configMgr`.

1. Sélectionnez État - Analyseur de l’état de préparation du cloud comme illustré dans l’image ci-dessous.

1. Vous pouvez également  la sortie via une interface JSON standard ou basée sur du texte réactif.

>[!NOTE]
> Voir Détecteur [de](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) schémas pour plus d’informations sur ces méthodes). Il faut ajouter cette section une fois que l&#39;ARC est prête à être utilisée.

## Étapes suivantes sur la préparation au cloud {#the-next-steps}

Pour plus d’informations sur votre état de préparation au service Cloud, Adobe doit évaluer la sortie de l’ARC.

Suivez les étapes ci-dessous pour renvoyer le fichier :

1. Accédez à la console Web AEM et téléchargez le fichier xx comme illustré dans l’image ci-dessous.

1. Ouvrez un ticket DayCare pour envoyer le fichier à Adobe en procédant comme suit :
   1. Enregistrement d’un ticket d’assistance dans la garderie intitulé **Cloud Readiness Analyzer Output**
   1. Ajout d’un fichier de sortie au ticket


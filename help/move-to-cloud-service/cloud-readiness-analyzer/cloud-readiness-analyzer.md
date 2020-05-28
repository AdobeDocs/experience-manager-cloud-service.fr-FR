---
title: Évaluer la complexité du passage au service Cloud
description: Évaluer la complexité du passage au service Cloud
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Analyse de l’état de préparation du cloud {#accesing-complexity}

## Présentation {#overview}

L’outil Cloud Readiness Analyzer (CRA) vous permet de vérifier si les instances AEM existantes sont prêtes à passer au service Cloud en détectant les modèles qui :

* Utiliser une fonctionnalité AEM 6.x qui n’est actuellement pas prise en charge sur le service Cloud

* Violer certaines règles qui seront affectées par le passage au service Cloud

>[!NOTE]
>La production de l&#39;ARC accélère l&#39;évaluation de l&#39;effort de développement qui sera nécessaire pour passer au service Cloud.

## Configuration de Cloud Readiness Analyzer {#setting-up-cra}

L’ARC est publiée sous la forme d’un package qui travaille sur toute version source d’AEM à partir de XX et ultérieure, et qui explore un passage au service Cloud.

Il est disponible sur le portail de distribution de logiciels et peut être installé à l’aide de Package Manager.

### Utilisation de Cloud Readiness Analyzer {#using-cra}

>[!NOTE]
> L&#39;ARC peut s&#39;exécuter sur n&#39;importe quel environnement, y compris les instances de développement local.

>[IMPORTANT]
>Toutefois, afin d’augmenter le taux de détection et d’éviter tout ralentissement sur les instances critiques de l’entreprise, il est recommandé de l’exécuter sur des environnements d’évaluation aussi proches que possible des  de production dans les domaines des applications utilisateur, du contenu et des configurations.

### Affichage de la sortie sur Cloud Readiness Analyzer {#viewing-output-cra}


1. Accédez à la console Web AEM en accédant à Configuration **de la console Web** Adobe Experience Manager à l’aide de `https://serveraddress:serverport/system/console/configMgr`.

1. Sélectionnez Etat - Cloud Readiness Analyzer comme illustré dans l’image ci-dessous.

1. Vous pouvez également vue la sortie au moyen d’une interface JSON standard ou basée sur du texte réactif.

>[!NOTE]
> Pour plus d’informations sur ces méthodes, reportez-vous à la section Détecteur [de](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) motif (pour plus d’informations). Il faut ajouter cette section une fois que l&#39;ARC est prête à être utilisée.

## Étapes suivantes sur la préparation au nuage {#the-next-steps}

Pour obtenir de plus amples renseignements sur votre état de préparation au service Cloud, Adobe doit évaluer la production de l&#39;ARC.

Pour renvoyer le fichier, procédez comme suit :

1. Accédez à la console Web AEM et téléchargez le fichier xx comme illustré dans l’image ci-dessous.

1. Ouvrez un ticket DayCare pour envoyer le fichier à Adobe en :
   1. Enregistrement d’un ticket d’assistance dans la garderie intitulé **Cloud Readiness Analyzer Output**
   1. Joindre un fichier de sortie au ticket


---
title: Validation des transferts de contenu (hérités)
description: Utiliser l’outil de transfert de contenu pour valider les transferts de contenu
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 2%

---

# Validation des transferts de contenu (hérités) {#validating-content-transfers}

## Prise en main {#getting-started}

Les utilisateurs peuvent déterminer de manière fiable si tout le contenu extrait par l’outil de transfert de contenu a bien été ingéré dans l’instance cible. Cette fonction de validation fonctionne en comparant un résumé des noeuds impliqués lors de l’extraction avec un résumé des noeuds impliqués lors de l’ingestion. Si des chemins de noeud inclus dans le résumé d’extraction sont absents du résumé d’ingestion, la validation est considérée comme ayant échoué et une validation manuelle supplémentaire peut être nécessaire.

>[!INFO]
>
>Cette fonctionnalité sera disponible à partir de la version 1.8.x de l’outil de transfert de contenu (CTT). L’environnement cible AEM Cloud Service doit être en cours d’exécution au moins version 6158 ou supérieure. Elle nécessite également la configuration de l’environnement source pour être exécutée. [pre-copy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step). La fonction de validation recherche le fichier azcopy.config sur la source. S’il ne trouve pas ce fichier, la validation ne s’exécute pas. Pour en savoir plus sur la configuration d’un fichier azcopy.config, voir [cette page](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

La validation d’un transfert de contenu est une fonctionnalité facultative. L’activation de cette fonctionnalité augmentera le temps nécessaire à l’exécution d’une extraction ainsi que d’une ingestion. Pour utiliser cette fonctionnalité, activez-la dans la console système de l’environnement d’AEM source en procédant comme suit :

1. Accédez à la console web Adobe Experience Manager sur votre instance source en accédant à **Outils - Opérations - Console web** ou directement à l’URL à l’adresse *https://serveraddress:serverport/system/console/configMgr*
1. Rechercher **Configuration du service d’extraction de l’outil de transfert de contenu**
1. Utilisez le bouton représentant un crayon pour modifier ses valeurs de configuration.
1. Activez la variable **Activation de la validation de la migration lors de l’extraction** , puis appuyez sur **Enregistrer**:

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Lorsque ce paramètre est activé et que l’environnement AEM Cloud Service cible exécute une version compatible, la validation de migration se produit lors de toutes les opérations d’extraction et d’ingestion qui suivent.

Pour plus d’informations sur l’installation de l’outil de transfert de contenu, voir [Prise en main de l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Validation d’un transfert de contenu {#how-to-validate-a-content-transfer}

Lorsque la validation de migration est activée dans l’environnement de l’AEM source, commencez une extraction.

If **Remplacer le conteneur d’évaluation lors de l’extraction** est activée, tous les noeuds impliqués dans l’extraction sont consignés dans le résumé du chemin d’extraction. Lorsque ce paramètre est utilisé, il est important d’activer la variable **Effacer le contenu existant sur l’instance cloud avant l’ingestion** lors de l’ingestion, sans quoi il se peut qu’il manque des noeuds dans le résumé d’ingestion. Il s’agit des noeuds qui sont déjà présents sur la cible à partir des ingérations précédentes.

Pour une illustration graphique de ce phénomène, reportez-vous aux exemples ci-dessous :

### Exemple 1 {#example-1}

* **Extraction (écrasement)**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTextractionoverwrite.png)

* **Ingestion (essuyer)**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTingestionwipe.png)

* **Remarques**

   Cette combinaison de &quot;Remplacer&quot; et de &quot;Effacer&quot; permet d’obtenir des résultats de validation cohérents, même pour les ingérations répétées.

### Exemple 2 {#example-2}

* **Extraction**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTextraction.png)

* **Ingestion**

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTingestion.png)

* **Remarques**

   Cette combinaison de &quot;Remplacer&quot; et de &quot;Effacer&quot; résultera en des résultats de validation cohérents pour l’ingestion initiale.

   Si l’ingestion est répétée, le résumé d’ingestion est vide et la validation semble avoir échoué. Le condensé d’ingestion sera vide, car tous les noeuds de cette extraction seront déjà présents sur la cible.

Une fois l’extraction terminée, commencez l’ingestion.

La partie supérieure du journal d’ingestion contiendra une entrée semblable à `aem-ethos/tools:1.2.438`. Assurez-vous que ce numéro de version est **1.2.438** ou version ultérieure, sinon la validation n’est pas prise en charge par la version d’AEM as a Cloud Service que vous utilisez.

Une fois l’ingestion terminée et la validation en cours, l’entrée de journal suivante est notée dans le journal d’ingestion :

```
Gathering artifacts for migration validation...  
```

Les détails de la validation suivront cette entrée. Voici un exemple d’une migration importante :

```
Beginning publish migration validation. Migration job id=[3aba1f96-84b6-4bd0-8642-c61c0d528387]
Extraction path digest is being processed...
Extraction path digest processing took 982 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 999 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 51674784
INGESTION: Number of nodes ingested: 51674784
----------------------------------------------------------
Validation succeeded! No entries were detected to be missing from the ingestion digest.
----------------------------------------------------------
Comparing the path digests took 29 seconds
Migration validation took 33 minutes
```

Il s’agit d’un exemple de validation qui a réussi, puisqu’il n’y avait aucune entrée manquante dans le condensé d’ingestion présent dans le condensé d’extraction.

Pour comparer, voici à quoi ressemblerait un rapport de validation si la validation avait échoué :

```
Beginning publish migration validation. Migration job id=[ac217e5a-a08d-4e81-cbd6-f39f88b174ce]
Extraction path digest is being processed...
Extraction path digest processing took 0 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 0 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 4635
INGESTION: Number of nodes ingested: 0
----------------------------------------------------------
Validation failed. However, the following nodes may already be present in the target environment.
Please refer to our Migration Validation FAQ (https://www.adobe.com/go/aem_cloud_ctt_validation_en) or open a ticket with Customer Care.
There are 4635 entries present in the extraction digest that are missing from the ingestion digest.
/content/dam/bruce
/content/dam/bruce-assets
... more paths listed (up to 10k) ...
----------------------------------------------------------
Comparing the path digests took 0 seconds
Migration validation took 0 minutes
```

L’exemple d’échec ci-dessus a été réalisé en exécutant une ingestion, puis en réexécutant la même ingestion avec l’option Effacer désactivée, de sorte qu’aucun noeud n’était impliqué pendant l’ingestion — tout était déjà présent sur la cible.

Outre l’inclusion dans le journal d’ingestion, le rapport de validation est également accessible à partir de l’interface utilisateur de l’outil de transfert de contenu. Pour ce faire, sélectionnez un jeu de migration, puis cliquez sur le bouton **Valider** à partir de la barre d’actions :


![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidatebutton.png)

La boîte de dialogue Journaux de validation s’ouvre :

![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidationlogs.png)

Utilisez la variable **Validation Publish/Author Report** pour afficher le rapport de validation de l’ingestion la plus récente au niveau donné de votre environnement cible. Voir ci-dessous un exemple tiré d’une petite ingestion de publication :

![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidationreport.png)

>[!NOTE]
>
>Le **Validation Publish/Author Report** s’affiche une fois l’ingestion terminée. En outre, les rapports de validation sont conservés, de sorte qu’ils n’expirent pas une fois l’ingestion terminée, comme le font les journaux d’ingestion.

## Résolution des problèmes {#troubleshooting}

### Échec de la validation. Et maintenant ?  {#validation-fail}

La première étape consiste à déterminer si l’ingestion a vraiment échoué ou si le contenu extrait est déjà présent dans l’environnement cible. Cela peut se produire si une ingestion est répétée avec la variable **Effacer le contenu existant sur l’instance cloud avant l’ingestion** Option désactivée.

Pour vérifier, choisissez un chemin dans le rapport de validation et vérifiez s’il est présent dans l’environnement cible. S’il s’agit d’un environnement de publication, vous pouvez vous limiter à vérifier directement les pages et les ressources. Si vous avez besoin d’aide pour cette étape, veuillez ouvrir un ticket auprès de l’assistance clientèle.

### Le nombre de noeuds est inférieur à ce que je m’attendais. Pourquoi ? {#node-count-lower-than-expected}

Certains chemins d’accès des digests d’extraction et d’ingestion sont délibérément exclus afin de conserver la taille de ces fichiers gérables, dans le but de pouvoir calculer le résultat de la validation de migration dans les deux heures suivant l’exécution de l’ingestion.

Les chemins que nous excluons actuellement des digestes sont les suivants : `cqdam.text.txt` rendus, noeuds dans `/home`, et les noeuds dans `/jcr:system`.

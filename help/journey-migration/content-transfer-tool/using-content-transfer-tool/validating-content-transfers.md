---
title: Validation des transferts de contenu
description: Utiliser l’outil de transfert de contenu pour valider les transferts de contenu
exl-id: a12059c3-c15a-4b6d-b2f4-df128ed0eea5
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 75%

---

# Validation des transferts de contenu {#validating-content-transfers}

## Prise en main {#getting-started}

Les utilisateurs peuvent déterminer de manière fiable si tout le contenu extrait par l’outil de transfert de contenu a bien été ingéré dans l’instance cible. Cette fonctionnalité de validation fonctionne en comparant un résumé des chemins d’accès de tous les nœuds impliqués lors de l’extraction avec un résumé des chemins d’accès de tous les nœuds impliqués lors de l’ingestion. Si des chemins de nœud inclus dans le résumé d’extraction sont absents du résumé d’ingestion, la validation est considérée comme ayant échoué et une validation manuelle supplémentaire peut être nécessaire.

>[!INFO]
>
>Cette fonctionnalité sera disponible à partir de la version 1.8.x de l’outil de transfert de contenu (CTT). L’environnement cible AEM Cloud Service doit au moins utiliser la version 6158 ou ultérieure. L’environnement source doit également être configuré pour fonctionner avec une [précopie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step). La fonctionnalité de validation recherche le fichier azcopy.config sur la source. S’il ne trouve pas ce fichier, la validation ne s’exécute pas. Pour en savoir plus sur la configuration d’un fichier azcopy.config, consultez [cette page](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

La validation d’un transfert de contenu est une fonctionnalité facultative. L’activation de cette fonctionnalité augmentera le temps nécessaire à l’exécution d’une extraction et d’une ingestion. Pour utiliser cette fonctionnalité, activez-la dans la console système de l’environnement d’AEM source en procédant comme suit :

1. Accédez à la console web Adobe Experience Manager sur votre instance source en accédant à **Outils - Opérations - Console web** ou directement à l’URL à l’adresse *https://serveraddress:serverport/system/console/configMgr*
1. Recherchez **Configuration du service d’extraction de l’outil de transfert de contenu**
1. Utilisez le bouton représentant un crayon pour modifier ses valeurs de configuration.
1. Activez le paramètre **Activation de la validation de la migration lors de l’extraction**, puis appuyez sur **Enregistrer** :

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Lorsque ce paramètre est activé et que l’environnement AEM Cloud Service cible exécute une version compatible, la validation de la migration se produit lors de toutes les opérations d’extraction et d’ingestion qui suivent.

Pour plus d’informations sur l’installation de l’outil de transfert de contenu, consultez [Prise en main de l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Validation d’un transfert de contenu {#how-to-validate-a-content-transfer}

Lorsque la validation de la migration est activée dans l’environnement de l’AEM source, démarrez une extraction.

If **Remplacer le conteneur d’évaluation lors de l’extraction** est activée, tous les noeuds impliqués dans l’extraction sont consignés dans le résumé du chemin d’extraction. Lorsque ce paramètre est utilisé, il est important d’activer **Effacer le contenu existant sur l’instance Cloud avant l’ingestion** lors de l’ingestion, sans quoi il se peut qu’il manque des noeuds dans le résumé d’ingestion. Il s’agit des noeuds qui sont déjà présents sur la cible à partir des ingestions précédentes.

Pour une illustration graphique, reportez-vous aux exemples ci-dessous :

### Exemple 1 {#example-1}

* **Extraction (remplacer)**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/validation-01.png)

* **Ingestion (effacer)**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/validation-02.png)

* **Remarques**

  Cette combinaison de « Remplacer » et « Effacer » permet d’obtenir des résultats de validation cohérents, même pour les ingestions répétées.

### Exemple 2 {#example-2}

* **Extraction**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/validation-03.png)

* **Ingestion**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/validation-04.png)

* **Remarques**

  Cette combinaison de « Remplacer » et « Effacer » permet d’obtenir des résultats de validation cohérents pour l’ingestion initiale.

  Si l’ingestion est répétée, le résumé d’ingestion est vide et la validation semble avoir échoué. Le condensé d’ingestion est vide, car tous les noeuds de cette extraction seront déjà présents sur la cible.

Une fois l’extraction terminée, commencez l’ingestion.

La partie supérieure du journal d’ingestion contiendra une entrée semblable à `aem-ethos/tools:1.2.438`. Assurez-vous que ce numéro de version est **1.2.438** ou ultérieur, sinon la validation n’est pas prise en charge par la version d’AEM as a Cloud Service que vous utilisez.

Une fois l’ingestion terminée et la validation en cours, l’entrée de journal suivante est indiquée dans le journal d’ingestion :

```
Gathering artifacts for migration validation...
```

Les détails de la validation suivront cette entrée. Voici un exemple d’une migration importante :

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

Il s’agit d’un exemple de validation qui a réussi, puisqu’il n’y avait aucune entrée manquante dans le résumé d’ingestion présent dans le résumé d’extraction.

En comparaison, voici un exemple de rapport de validation si la validation avait échoué :

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

L’exemple d’échec ci-dessus a été réalisé en exécutant une ingestion, puis en exécutant à nouveau la même ingestion avec l’option Effacer désactivée, de sorte qu’aucun nœud n’était impliqué pendant l’ingestion – les éléments étaient déjà présents sur la cible.

En plus d’être inclus dans le journal d’ingestion, le rapport de validation est également accessible à partir de l’interface utilisateur des **Tâches d’ingestion** de Cloud Acceleration Manager. Pour ce faire, cliquez sur les trois petits points (**...**), puis cliquez sur **Rapport de validation** dans la liste déroulante pour afficher le rapport de validation.


![image](/help/journey-migration/content-transfer-tool/assets-ctt/CTTvalidationreportnew.png)

## Validation de la migration de l’entité de sécurité {#how-to-validate-principal-migration}

Voir [Mappage des utilisateurs et migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) pour lire les détails des migrations principales et les raisons pour lesquelles cela est nécessaire.

Une fois l’extraction et l’ingestion terminées, un résumé et un rapport de la migration principale sont disponibles. Ces informations peuvent être utilisées pour valider les utilisateurs et les groupes qui ont été migrés avec succès et, peut-être, pour déterminer pourquoi certains n’ont pas été migrés.

Pour afficher ces informations, accédez à Cloud Acceleration Manager. Cliquez sur la carte de votre projet, puis sur la carte Transfert de contenu. Accédez à **Tâches d’ingestion** et localisez l’ingestion que vous souhaitez vérifier. Cliquez sur les trois points (**...**) pour cette ingestion, puis cliquez sur **Afficher le résumé principal** dans la liste déroulante.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-action.png)

Une boîte de dialogue s’affiche avec les informations de résumé. Utilisez les icônes d’aide pour lire une description plus complète. Cliquez sur le bouton **Télécharger le rapport** pour télécharger le rapport complet séparé par des virgules (CSV).

![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-dialog.png)

>[!NOTE]
>
>Si le mappage utilisateur est désactivé, une autre variante de cette boîte de dialogue s’affiche. Il indique que le mappage des utilisateurs a été désactivé et n’affichera pas les 3 champs donnant des valeurs de mappage des utilisateurs.

## Résolution des problèmes {#troubleshooting}

### Échec de la validation. Et maintenant ?  {#validation-fail}

La première étape consiste à déterminer si l’ingestion a vraiment échoué ou si le contenu extrait est déjà présent dans l’environnement cible. Cela peut se produire si une ingestion est répétée avec l’option **Effacer le contenu existant sur l’instance Cloud avant l’ingestion** désactivée.

Pour vérifier, choisissez un chemin dans le rapport de validation et vérifiez s’il est présent dans l’environnement cible. S’il s’agit d’un environnement de publication, vous pouvez vous limiter à vérifier directement les pages et les ressources. Si vous avez besoin d’aide pour cette étape, veuillez ouvrir un ticket auprès de l’assistance clientèle.

### Le nombre de noeuds est inférieur à ce que je m’attendais. Pourquoi ? {#node-count-lower-than-expected}

Certains chemins d’accès des résumés d’extraction et d’ingestion sont délibérément exclus afin de conserver une taille de fichiers gérable, dans le but de pouvoir calculer le résultat de la validation de la migration dans les deux heures suivant l’exécution de l’ingestion.

Les chemins que nous excluons actuellement des résumés sont les suivants : les rendus `cqdam.text.txt` et les noeuds dans `/home`, et les noeuds dans `/jcr:system`.

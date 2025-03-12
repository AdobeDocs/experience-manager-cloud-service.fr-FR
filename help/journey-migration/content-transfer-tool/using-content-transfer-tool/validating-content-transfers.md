---
title: Validation des transferts de contenu
description: Utiliser l’outil de transfert de contenu pour valider les transferts de contenu
exl-id: a12059c3-c15a-4b6d-b2f4-df128ed0eea5
feature: Migration
role: Admin
source-git-commit: 9b05ed38e8eb337b3a07ee2051c6a0d530088af2
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 71%

---


# Validation des transferts de contenu {#validating-content-transfers}

## Prise en main {#getting-started}

Les utilisateurs peuvent déterminer de manière fiable si tout le contenu extrait par l’outil de transfert de contenu a bien été ingéré dans l’instance cible. Cette fonctionnalité de validation fonctionne en comparant un résumé des chemins d’accès de tous les nœuds impliqués lors de l’extraction avec un résumé des chemins d’accès de tous les nœuds impliqués lors de l’ingestion. Si des chemins de nœud inclus dans le résumé d’extraction sont absents du résumé d’ingestion, la validation est considérée comme ayant échoué et une validation manuelle supplémentaire peut être nécessaire.

>[!INFO]
>
>Cette fonctionnalité sera disponible à partir de la version 1.8.x de l’outil de transfert de contenu (CTT). L’environnement cible AEM Cloud Service doit au moins utiliser la version 6158 ou ultérieure. L’environnement source doit également être configuré pour fonctionner avec une [précopie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step). La fonctionnalité de validation recherche le fichier azcopy.config sur la source. S’il ne trouve pas ce fichier, la validation ne s’exécute pas. Pour en savoir plus sur la configuration d’un fichier azcopy.config, voir [ Gestion des référentiels de contenu volumineux - Configurer un fichier azcopy.config ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

La validation d’un transfert de contenu est une fonctionnalité facultative. L’activation de cette fonctionnalité augmentera le temps nécessaire à l’exécution d’une extraction et d’une ingestion. Pour utiliser cette fonctionnalité, activez-la dans la console système de l’environnement d’AEM source en procédant comme suit :

1. Accédez à la console web Adobe Experience Manager sur votre instance source en accédant à **Outils - Opérations - Console web** ou directement à l’URL à l’adresse *https://serveraddress:serverport/system/console/configMgr*
1. Recherchez **Configuration du service d’extraction de l’outil de transfert de contenu**
1. Utilisez le bouton représentant un crayon pour modifier ses valeurs de configuration.
1. Activez le paramètre **Activation de la validation de la migration lors de l’extraction**, puis appuyez sur **Enregistrer** :

   ![image](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

Lorsque ce paramètre est activé et que l’environnement AEM Cloud Service cible exécute une version compatible, la validation de la migration se produit lors de toutes les opérations d’extraction et d’ingestion qui suivent.

Pour plus d’informations sur l’installation de l’outil de transfert de contenu, consultez [Prise en main de l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## Validation d’un transfert de contenu {#how-to-validate-a-content-transfer}

Lorsque la validation de la migration est activée dans l’environnement de l’AEM source, démarrez une extraction.

Si **Remplacer le conteneur d’évaluation lors de l’extraction** est activé, tous les nœuds impliqués dans l’extraction sont consignés dans le résumé du chemin d’extraction. Lorsque ce paramètre est utilisé, il est important d’activer **Effacer le contenu existant sur l’instance Cloud avant l’ingestion** lors de l’ingestion, sans quoi il se peut qu’il manque des noeuds dans le résumé d’ingestion. Il s’agit des noeuds qui sont déjà présents sur la cible à partir des ingestions précédentes.

Pour obtenir une illustration graphique de ce sujet, reportez-vous aux exemples suivants :

### Exemple 1 {#example-1}

* **Extraction (remplacer)**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/example1-extraction.png)

* **Ingestion (effacer)**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/validation-02.png)

* **Remarques**

  Cette combinaison de « Remplacer » et « Effacer » permet d’obtenir des résultats de validation cohérents, même pour les ingestions répétées.

### Exemple 2 {#example-2}

* **Extraction**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/example2-extraction.png)

* **Ingestion**

  ![image](/help/journey-migration/content-transfer-tool/assets-ctt/validation-04.png)

* **Remarques**

  Cette combinaison de « Remplacer » et « Effacer » permet d’obtenir des résultats de validation cohérents pour l’ingestion initiale.

  Lorsque l’ingestion est répétée, le résumé d’ingestion est vide et la validation échoue. Le résumé d’ingestion est vide, car tous les nœuds de cette extraction sont déjà présents sur la cible.

Une fois l’extraction terminée, commencez l’ingestion.

La partie supérieure du journal d’ingestion contiendra une entrée semblable à `aem-ethos/tools:1.2.438`. Assurez-vous que ce numéro de version est **1.2.438** ou ultérieur, sinon la validation n’est pas prise en charge par la version d’AEM as a Cloud Service que vous utilisez.

Une fois l’ingestion terminée et la validation lancée, l’entrée de journal suivante est notée dans le journal d’ingestion :

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

En comparaison, voici à quoi ressemblerait un rapport de validation si la validation avait échoué (ou si une migration complémentaire avait été effectuée) :

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
See our Migration Validation FAQ (https://www.adobe.com/go/aem_cloud_ctt_validation_en) or open a ticket with Customer Care.
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

## Comment valider la migration des entités principales {#how-to-validate-group-migration}

Consultez [ Migration de groupe ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) pour lire les détails de la migration principale et sa raison d’être.

Une fois l’extraction et l’ingestion terminées, un résumé et un rapport de la migration des entités principales sont disponibles. Ces informations peuvent être utilisées pour valider les groupes qui ont été migrés avec succès et, peut-être, pour déterminer pourquoi certains ne l’ont pas été.

Pour afficher ces informations, accédez à Cloud Acceleration Manager. Cliquez sur votre carte de projet puis sur la carte de transfert de contenu. Accédez à **Tâches d’ingestion** et localisez l’ingestion que vous souhaitez vérifier. Cliquez sur les trois points (**...**) de cette ingestion, puis cliquez sur **Afficher le résumé principal** dans la liste déroulante.

![Image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-action.png)

Une boîte de dialogue contenant les informations récapitulatives s’affiche. Utilisez les icônes d’aide pour lire une description plus complète. Pour télécharger le rapport complet de migration des entités principales séparées par des virgules (CSV), sélectionnez **Rapport de migration des entités principales** dans la liste déroulante sous **Télécharger un fichier...** et cliquez sur le bouton **Télécharger**. Notez également qu’à la fin de ce rapport se trouve le rapport d’utilisateur , qui peut être utilisé pour la gestion des utilisateurs après la migration.

![Image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-dialog.png)

Le rapport de migration principale indique :

* Chaque groupe a été migré, ainsi que le premier chemin d’accès au contenu qui a déclenché la migration de ce groupe. Le groupe peut également se trouver sur d’autres chemins, mais seul le premier trouvé pour un groupe donné est signalé. Il indique également s’il a été trouvé dans une liste de contrôle d’accès ou une politique de CUG.
* Le mot « local » est indiqué sur la ligne de chaque groupe migré en tant que groupe local.
* Chaque groupe n’a pas été migré et la raison pour laquelle il n’a pas été migré.  En règle générale, il s’agit de l’une des raisons suivantes :
   * C&#39;est un groupe intégré
   * Il est déjà sur le système cible
   * Il ne se trouve pas dans une politique ACL ou CUG sur le contenu en cours de migration
   * Il comporte un champ unique en double (l’un des champs rep:principalName, rep:authorizableId, jcr:uuid ou rep:externalId se trouve déjà sur la destination, mais tous doivent être uniques).

## Résolution des problèmes {#troubleshooting}

### Échec de la validation. Et maintenant ?  {#validation-fail}

La première étape consiste à déterminer si l’ingestion a vraiment échoué ou si le contenu extrait est déjà présent dans l’environnement cible. Cela peut se produire si une ingestion est répétée avec l’option **Effacer le contenu existant sur l’instance Cloud avant l’ingestion** désactivée.

Pour vérifier, choisissez un chemin dans le rapport de validation et vérifiez s’il est présent dans l’environnement cible. S’il s’agit d’un environnement de publication, vous pouvez vous limiter à vérifier directement les pages et les ressources. Si vous avez besoin d’aide pour cette étape, ouvriez un ticket auprès de l’assistance clientèle.

### Le nombre de noeuds est inférieur à ce que je m’attendais. Pourquoi ? {#node-count-lower-than-expected}

Certains chemins d’accès des résumés d’extraction et d’ingestion sont délibérément exclus afin de conserver une taille de fichiers gérable, dans le but de pouvoir calculer le résultat de la validation de la migration dans les deux heures suivant l’exécution de l’ingestion.

Les chemins que nous excluons actuellement des résumés sont les suivants : les rendus `cqdam.text.txt` et les noeuds dans `/home`, et les noeuds dans `/jcr:system`.

### Groupes d’utilisateurs et d’utilisatrices fermés {#validating-cugs}

Consultez [ Migration de groupes d’utilisateurs fermés ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) pour plus d’informations lors de l’utilisation d’une politique de groupe d’utilisateurs fermé (CUG).

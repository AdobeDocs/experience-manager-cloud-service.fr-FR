---
title: Importation et exportation des métadonnées de ressources par lot
description: Cet article explique comment importer et exporter des métadonnées par lot.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: fb70a068-3ba3-4459-952d-79155d286c42
source-git-commit: ce7ba090a97c2f265af8ed21f11a5a45880e010a
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 100%

---

# Importation et exportation des métadonnées de ressources par lot {#import-and-export-asset-metadata-in-bulk}

Adobe Experience Manager Assets permet d’importer des métadonnées de ressources par lot à l’aide d’un fichier CSV. Vous pouvez effectuer des mises à jour par lot pour les ressources récemment transférées ou les ressources existantes en important un fichier CSV. Vous pouvez également assimiler des métadonnées de ressources par lot à partir d’un système tiers au format CSV.

## Importation de métadonnées {#import-metadata}

L’importation de métadonnées est asynchrone et ne nuit pas aux performances du système. La mise à jour simultanée des métadonnées de plusieurs ressources peut nécessiter beaucoup de ressources en raison de l’activité générée par les microservices de ressources dédiés à l’écriture différée de métadonnées. Adobe vous recommande de planifier toute opération par lot pendant les périodes au cours desquelles vos serveurs sont le moins sollicités afin que les performances des autres utilisateurs ne soient pas affectées.

>[!NOTE]
>
>Pour importer des métadonnées sur des espaces de noms personnalisés, commencez par enregistrer les espaces de noms.

1. Accédez à lʼinterface utilisateur [!DNL Assets], sélectionnez **[!UICONTROL Créer]** dans la barre d’outils, puis sélectionnez **[!UICONTROL Métadonnées]** dans le menu.
1. Dans la page **[!UICONTROL Importation des métadonnées]**, cliquez sur **[!UICONTROL Sélectionner un fichier]**. Sélectionnez le fichier CSV contenant les métadonnées.
1. Indiquez les paramètres suivants :

   | Paramètre | Description |
   | ---------------------- | ------- |
   | Taille du lot | Nombre de ressources dans un lot pour lesquelles les métadonnées doivent être importées. La valeur par défaut est 50. La valeur maximale est 100. |
   | Séparateur de champs | La valeur par défaut est `,` (une virgule). Vous pouvez spécifier n’importe quel autre caractère. |
   | Délimiteur à plusieurs valeurs | Séparateur des valeurs de métadonnées. La valeur par défaut est `|`. |
   | Lancer les workflows | Faux par défaut. Lorsque la valeur est définie sur `true` et que les paramètres par défaut sont utilisés pour le workflow Écriture différée des métadonnées de gestion des ressources numériques (DAM) (qui écrit des métadonnées dans les données XMP binaires). L’activation des workflows ralentit le système. |
   | Nom de colonne du chemin d’accès à la ressource | Définit le nom de la colonne du fichier CSV avec des ressources. |

1. Sélectionnez **[!UICONTROL Importer]** dans la barre d’outils. Une fois les métadonnées importées, une notification est envoyée à votre boîte de réception de notifications. Accédez à la page de propriété des ressources et vérifiez que les valeurs des métadonnées sont correctement importées pour les ressources.

1. Pour ajouter une date et un horodatage au cours de l’importation de métadonnées, utilisez le format de date et d’heure `YYYY-MM-DDThh:mm:ss.fff-00:00`. La date et l’heure sont séparées par `T`, `hh` correspond aux heures au format 24 heures, `fff` aux nanosecondes et `-00:00` au décalage du fuseau horaire. Par exemple, `2020-03-26T11:26:00.000-07:00` correspond au 26 mars 2020 à 11:26:00.000, heure du Pacifique.

   * Le format de la date dépend de lʼen-tête de la colonne et du format quʼelle contient. Par exemple, si la date est conforme au format `yyyy-MM-dd'T'HH:mm:ssXXX`, lʼen-tête de colonne correspondant doit être `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX`.
   * Le format de date par défaut est `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`.

<!-- Hidden via cqdoc-17869>

>[!CAUTION]
>
>If the date format does not match `YYYY-MM-DDThh:mm:ss.fff-00:00`, the date values are not set. The date formats of exported metadata CSV file is in the format `YYYY-MM-DDThh:mm:ss-00:00`. If you want to import it, convert it to the acceptable format by adding the nanoseconds value denoted by `fff`.
-->

## Exportation des métadonnées {#export-metadata}

Vous pouvez exporter des métadonnées pour plusieurs ressources au format CSV. Les métadonnées sont exportées de manière asynchrone et n’ont aucun impact sur les performances du système. Pour exporter des métadonnées, Experience Manager parcourt les propriétés du nœud de ressource `jcr:content/metadata` et de ses nœuds enfants et exporte les propriétés de métadonnées dans un fichier CSV.

Voici quelques cas d’utilisation pour l’exportation de métadonnées par lot :

* Importation des métadonnées dans un système tiers lors de la migration des fichiers.
* Partage des métadonnées de ressources avec une équipe de projet plus large.
* Test ou contrôle des métadonnées pour la conformité.
* Externalisation des métadonnées pour une localisation distincte.

1. Sélectionnez le dossier de ressources pour lequel vous souhaitez exporter des métadonnées. Dans la barre d’outils, sélectionnez **[!UICONTROL Exporter les métadonnées]**.
1. Dans la boîte de dialogue Exportation des métadonnées, indiquez un nom pour le fichier CSV. Pour exporter des métadonnées des ressources dans les sous-dossiers, sélectionnez **[!UICONTROL Inclure les ressources dans les sous-dossiers]**.

   ![Interface et options d’exportation des métadonnées de toutes les ressources dans un dossier](assets/export_metadata_page.png "Interface et options d’exportation des métadonnées de toutes les ressources dans un dossier")

1. Sélectionnez les options souhaitées. Indiquez un nom de fichier et, si nécessaire, une date.

1. Dans le champ **[!UICONTROL Propriétés à exporter]**, indiquez si vous voulez exporter toutes les propriétés ou certaines propriétés. Si vous choisissez Propriétés sélectives à exporter, ajoutez les propriétés souhaitées.

1. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Exporter]**. Un message confirme que les métadonnées ont été exportées. Fermez le message.
1. Ouvrez la notification de la boîte de réception pour la tâche d’exportation. Sélectionnez la tâche et cliquez sur **[!UICONTROL Ouvrir]** dans la barre d’outils. Pour télécharger le fichier CSV avec les métadonnées, appuyez/cliquez sur **[!UICONTROL Téléchargement CSV]** dans la barre d’outils. Cliquez sur **[!UICONTROL Fermer]**.

   ![Boîte de dialogue de téléchargement du fichier CSV contenant les métadonnées exportées en bloc](assets/csv_download.png)

   *Image : boîte de dialogue de téléchargement du fichier CSV contenant les métadonnées exportées en bloc.*

>[!MORELIKETHIS]
>
>* [Importation de métadonnées lors de l’importation de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor)


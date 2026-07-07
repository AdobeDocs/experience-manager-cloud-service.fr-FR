---
title: Suppression des dépendances externes pour les installations existantes
description: Suppression des dépendances externes pour les installations existantes
feature: Workfront Integrations and Apps
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
role: Admin
source-git-commit: 80a32672ec018274b0410abfa14fdd761fdb5aba
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Suppression des dépendances externes pour les installations existantes {#remove-external-depedencies}

Adobe vous recommande d’exécuter des étapes de configuration pour les installations de connecteur amélioré existantes pour Workfront afin de supprimer les dépendances sur les points de distribution Hoodoo.

>[!NOTE]
>
>Exécutez les étapes de configuration uniquement si vous avez installé le connecteur amélioré pour Workfront avant mars 2022. À compter de mars 2022, il n’existe aucune dépendance sur les points de distribution Hoodoo pour les nouvelles installations de connecteur amélioré pour Workfront.

Pour supprimer les dépendances externes :

1. Supprimez la configuration suivante de référentiel Hoodoo du parent `pom.xml` :

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. Supprimez la configuration de serveur suivante du fichier `settings.xml`, disponible à l’adresse `./cloudmanager/maven/settings.xml` :

   ```XML
         <server>
            <id>hoodoo-maven</id>
            <configuration>
               <httpHeaders>
                     <property>
                        <name>Deploy-Token</name>
                        <value>xxxxxxxxxxxxxxxx</value>
                     </property>
               </httpHeaders>
            </configuration>
         </server>
   ```

1. Exécutez les [étapes de nouvelle installation](workfront-connector-install.md).


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)


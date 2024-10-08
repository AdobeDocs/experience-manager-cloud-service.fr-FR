---
title: Suppression des dépendances externes pour les installations existantes
description: Suppression des dépendances externes pour les installations existantes
feature: Workfront Integrations and Apps
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
role: Admin
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 87%

---

# Suppression des dépendances externes pour les installations existantes {#remove-external-depedencies}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

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

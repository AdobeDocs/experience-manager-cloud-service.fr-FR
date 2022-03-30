---
title: Suppression des dépendances externes pour les installations existantes
description: Suppression des dépendances externes pour les installations existantes
feature: Integrations
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
source-git-commit: b71a78696d4b347c97b077d84b455f53a1747a07
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Suppression des dépendances externes pour les installations existantes {#remove-external-depedencies}

Adobe vous recommande d’exécuter des étapes de configuration pour les installations de connecteur améliorées existantes pour Workfront afin de supprimer les dépendances sur les points de distribution Hoodoo.

>[!NOTE]
>
>Exécutez les étapes de configuration uniquement si vous avez installé le connecteur amélioré pour Workfront avant mars 2022. À compter de mars 2022, il n’existe aucune dépendance sur les points de distribution Hoodoo pour les nouvelles installations de connecteur améliorées pour Workfront.

Pour supprimer les dépendances externes :

1. Supprimez la configuration de référentiel Hoodoo suivante du parent. `pom.xml`:

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. Supprimez la configuration de serveur suivante du `settings.xml` , disponible à l’adresse `./cloudmanager/maven/settings.xml`:

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

1. Exécutez le [nouvelles étapes d’installation](workfront-connector-install.md).

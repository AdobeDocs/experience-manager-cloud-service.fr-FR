---
title: Mettre à jour [!DNL Workfront for Experience Manager enhanced connector]
description: Mettre à jour [!DNL Workfront for Experience Manager enhanced connector]
source-git-commit: 34f3cf925a3ea58de176521be459a61f4317eec3
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 5%

---

# Mettre à jour [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

[!UICONTROL Experience Manager Assets as a Cloud Service] permet de mettre à jour la variable [!DNL Workfront for Experience Manager enhanced connector] d’une version précédente à la dernière version.

>[!TIP]
>
>Recherchez-vous [!DNL Workfront for Experience Manager enhanced connector] mise à jour de la documentation pour AEM 6.5 ? Cliquez sur [here](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=en##update-enhanced-connector-for-workfront).


Pour mettre à jour la variable [!DNL Workfront for Experience Manager enhanced connector] vers la dernière version :

1. Téléchargez la dernière version du connecteur amélioré à partir de [Distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [Accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) et cloner votre référentiel as a Cloud Service AEM à partir de Cloud Manager.

1. Ouvrez le référentiel as a Cloud Service de l’Experience Manager cloné à l’aide d’un IDE de votre choix.

1. Placez le fichier zip du connecteur amélioré téléchargé à l’étape 1 à l’emplacement suivant :

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Si la variable `resources` n’existe pas, créez le dossier .

1. Mettre à jour la version améliorée du connecteur dans parent `pom.xml`.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version> updated enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

1. Mettez à jour la dépendance dans `all module pom.xml`.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <scope>system</scope>
         <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

   >[!NOTE]
   >
   >Assurez-vous d’ajouter `<scope>` et `<systemPath>` aux dépendances des étapes 5 et 6.

1. Mettre à jour `pom.xml` incorpore. Ajoutez les packages [!DNL Workfront for Experience Manager enhanced connector] à la section `embeddeds` du `pom.xml` de tous vos sous-projets. Incorporer les mises à jour dans tous les modules `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   La cible de la section incorporée est définie sur `/apps/<path-to-project-install-folder>/install`. Ce chemin d’accès JCR `/apps/<path-to-project-install-folder>` doit être inclus dans les règles de filtrage de la variable `all/src/main/content/META-INF/vault/filter.xml` fichier . Les règles de filtrage du référentiel sont généralement dérivées du nom du programme. Utilisez le nom du dossier comme cible dans les règles existantes.

1. [Suppression des dépendances sur les points de distribution Hoodoo](remove-external-dependencies.md), le cas échéant.

1. Envoyez les modifications au référentiel.

1. Exécutez le pipeline pour [déployer les modifications dans Cloud Manager ;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

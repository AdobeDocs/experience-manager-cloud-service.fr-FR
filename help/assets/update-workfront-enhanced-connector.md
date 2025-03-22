---
title: Mettre à jour [!DNL Workfront for Experience Manager enhanced connector]
description: Mettre à jour [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 09276b4d-a7c8-4927-8c0a-40eda48e55a7
feature: Workfront Integrations and Apps
role: Admin
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 89%

---

# Mettre à jour [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

[!UICONTROL Experience Manager Assets as a Cloud Service] permet de mettre à jour la variable [!DNL Workfront for Experience Manager enhanced connector] d’une version précédente à la dernière version.

>[!TIP]
>
>Recherchez-vous la documentation de mise à jour [!DNL Workfront for Experience Manager enhanced connector] pour AEM 6.5 ? Cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=fr##update-enhanced-connector-for-workfront).


Pour mettre à jour [!DNL Workfront for Experience Manager enhanced connector] vers la dernière version :

1. Téléchargez la dernière version du connecteur amélioré à partir de la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [Accédez](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=fr) à votre référentiel AEM as a Cloud Service et clonez-le à partir de Cloud Manager.

1. Ouvrez le référentiel Experience Manager as a Cloud Service cloné à l’aide d’un IDE de votre choix.

1. Placez le fichier zip du connecteur amélioré téléchargé à l’étape 1 à l’emplacement suivant :

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Si le dossier `resources` n’existe pas, créez-le.

1. Mettez à jour la version améliorée du connecteur dans le `pom.xml` parent.

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
   >Assurez-vous d’ajouter `<scope>` et `<systemPath>` aux dépendances des étapes 5 et 6.

1. Mettez à jour les incorporations `pom.xml`. Ajoutez les packages [!DNL Workfront for Experience Manager enhanced connector] à la section `embeddeds` du `pom.xml` de tous vos sous-projets. Incorporez les mises à jour dans tous les modules `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   La cible de la section incorporée est définie sur `/apps/<path-to-project-install-folder>/install`. Ce chemin d’accès JCR `/apps/<path-to-project-install-folder>` doit être inclus dans les règles de filtrage du fichier `all/src/main/content/META-INF/vault/filter.xml`. Les règles de filtrage du référentiel sont généralement dérivées du nom du programme. Utilisez le nom du dossier comme cible dans les règles existantes.

1. [Supprimez les dépendances sur les points de distribution Hoodoo](remove-external-dependencies.md), le cas échéant.

1. Envoyez les modifications au référentiel.

1. Exécutez le pipeline pour [déployer les modifications dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=fr).

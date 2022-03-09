---
title: Installation de la version [!DNL Workfront for Experience Manager enhanced connector]
description: Installation de la version [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: a5776453b261e6f4e6c891763934b236bade8f7f
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Installation de la version [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

Un utilisateur disposant d’un accès administrateur dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] installe le connecteur amélioré. Avant de procéder à l’installation, vérifiez la prise en charge de la plateforme et d’autres [conditions préalables pour le connecteur](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>L’Adobe nécessite le déploiement et la configuration de [!DNL Adobe Workfront for Experience Manager enhanced connector] uniquement par le biais de partenaires certifiés ; [!DNL Adobe Professional Services]. Si elles sont déployées et configurées sans partenaire certifié ou [!DNL Adobe Professional Services], il n’est pas pris en charge par Adobe.
>
>Adobe peut mettre à jour les [!DNL Adobe Workfront] et [!DNL Adobe Experience Manager] qui rendent ce connecteur redondant ; si cela se produit, les clients peuvent être tenus de passer de l’utilisation de ce connecteur.

Avant d’installer le connecteur, procédez comme suit :

1. [Configuration du pare-feu](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html). Pour connaître la grappe IP dans [!DNL Workfront], accédez à [!UICONTROL Configuration] > [!UICONTROL Système] > [!UICONTROL Informations sur le client].

1. Sur le dispatcher, autorisez les en-têtes HTTP nommés `authorization`, `username`, et `apikey`. Autoriser `GET`, `POST`, et `PUT` de `/bin/workfront-tools`.

1. Assurez-vous que les chemins suivants n’existent pas dans [!DNL Experience Manager] référentiel :

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Cette installation nécessite des connaissances pour définir un projet Maven dans [!DNL Experience Manager] as a [!DNL Cloud Service]. Utilisez les ressources suivantes pour comprendre comment inclure un module tiers dans votre projet Maven :

   * [Incluez le package tiers dans votre projet Maven.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [Déploiement avec [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr).

Pour installer le module complémentaire dans [!DNL Experience Manager] as a [!DNL Cloud Service], procédez comme suit :

1. Téléchargez le connecteur amélioré depuis [Distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. [Accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) et cloner votre référentiel as a Cloud Service AEM à partir de Cloud Manager.

1. Ouvrez le référentiel as a Cloud Service AEM cloné à l’aide d’un IDE de votre choix.

1. Placez le fichier zip du connecteur amélioré téléchargé à l’étape 1 à l’emplacement suivant :

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Si la variable `resources` n’existe pas, créez le dossier .


1. Ajouter `pom.xml` dependencies :

   1. Ajouter une dépendance dans le parent `pom.xml`.

      ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version>enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
      ```

      >[!NOTE]
      >
      >Veillez à mettre à jour le numéro de version du connecteur amélioré avant de copier la dépendance sur le parent. `pom.xml`.

   1. Ajouter une dépendance dans `all module pom.xml`.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
      ```


1. Ajouter `pom.xml` incorpore. Ajoutez la variable [!DNL Workfront for Experience Manager enhanced connector] modules vers `embeddeds` de la section `pom.xml` de tous vos sous-projets. L’incorpore dans le module all ; `pom.xml`.

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

1. Envoyez les modifications au référentiel.

1. Exécutez le pipeline pour [déployer les modifications dans Cloud Manager ;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

1. Pour créer une configuration utilisateur système, créez `wf-workfront-users` in [!DNL Experience Manager] Groupe d’utilisateurs et attribuer l’autorisation `jcr:all` to `/content/dam`. Un utilisateur système `workfront-tools` est créée automatiquement et les autorisations requises sont gérées automatiquement. Tous les utilisateurs de [!DNL Workfront] qui utilisent le connecteur amélioré sont automatiquement ajoutés dans le cadre de ce groupe.

## Configurer la connexion entre [!DNL Experience Manager] as a [!DNL Cloud Service] et [!DNL Workfront] {#configure-connection}

Pour créer une connexion avec [!DNL Workfront], procédez comme suit :

1. Dans [!DNL Experience Manager], sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Configuration des outils Workfront]**.

1. Sélectionner `workfront-tools` dans le panneau de gauche, puis sélectionnez **[!UICONTROL Créer]** dans la zone supérieure droite de la page.

1. Dans le **[!UICONTROL Connexion Workfront]** , fournissez les détails requis de votre [!DNL Workfront] déploiement, puis sélectionnez **[!UICONTROL Connexion à Workfront]** . Une fois la connexion établie, la variable [!DNL Workfront] l’intégration personnalisée du document est créée automatiquement dans la variable [!DNL Workfront] environnement.

   ![Connexion [!DNL Experience Manager] et [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Accédez au **[!UICONTROL Avancé]** et sélectionnez l’option **[!UICONTROL Le serveur est-il AEM as a Cloud Service ?]**.

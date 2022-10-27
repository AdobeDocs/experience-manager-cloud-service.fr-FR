---
title: Installation de la version [!DNL Workfront for Experience Manager enhanced connector]
description: Installation de la version [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: 6e1408abde71c5400adaeaea130e4b7f9287169a
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 100%

---

# Installation de la version [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

Un utilisateur disposant d’un accès administrateur dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] installe le connecteur amélioré. Avant de procéder à l’installation, vérifiez la prise en charge de la plateforme et d’autres [conditions préalables pour le connecteur](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe nécessite le déploiement et la configuration de [!DNL Adobe Workfront for Experience Manager enhanced connector] uniquement par le biais de partenaires certifiés ou [!DNL Adobe Professional Services]. S’il est déployé et configuré sans partenaire certifié ou sans [!DNL Adobe Professional Services], il n’est pas pris en charge par Adobe.
>
>* Adobe peut publier des mises à jour d’[!DNL Adobe Workfront] et d’[!DNL Adobe Experience Manager] qui rendent ce connecteur redondant ; si cela se produit, les clients peuvent être amenés à cesser d’utiliser ce connecteur.
>
>* Adobe prend en charge les versions 1.7.4 et supérieures du connecteur amélioré. Les versions précédentes et personnalisées ne sont pas prises en charge. Pour vérifier la version du connecteur amélioré, consultez l’étape 5(a) des [instructions d’installation du connecteur amélioré](workfront-connector-install.md).
>
>* Consultez la section [Examen de certification des partenaires pour Workfront pour le connecteur amélioré Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Pour plus d’informations sur l’examen, consultez le [Guide d’examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


Avant d’installer le connecteur, procédez comme suit :

1. [Configuration du pare-feu](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html?lang=fr). Pour connaître la grappe IP dans [!DNL Workfront], accédez à [!UICONTROL Configuration] > [!UICONTROL Système] > [!UICONTROL Informations sur le client].

1. Sur le répartiteur, autorisez les en-têtes HTTP nommés `authorization`, `username`, et `apikey`. Autorisez les requêtes `GET`, `POST`, et `PUT` à `/bin/workfront-tools`.

1. Assurez-vous que les chemins d’accès suivants n’existent pas dans le référentiel [!DNL Experience Manager] :

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`
   * `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`

1. Cette installation nécessite des connaissances pour définir un projet Maven dans [!DNL Experience Manager] as a [!DNL Cloud Service]. Utilisez les ressources suivantes pour comprendre comment inclure un package tiers dans votre projet Maven :

   * [Incluez un package tiers dans votre projet Maven](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=fr#including-third-party).
   * [Effectuez le déploiement avec [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr).

Pour installer le module complémentaire dans [!DNL Experience Manager] as a [!DNL Cloud Service], procédez comme suit :

1. Téléchargez le connecteur amélioré depuis la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [Accédez](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=fr) à votre référentiel AEM as a Cloud Service et clonez-le à partir de Cloud Manager.

1. Ouvrez le référentiel AEM as a Cloud Service cloné à l’aide d’un IDE de votre choix.

1. Placez le fichier zip du connecteur amélioré téléchargé à l’étape 1 à l’emplacement suivant :

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >Si le dossier `resources` n’existe pas, créez-le.


1. Ajoutez des dépendances `pom.xml` :

   1. Ajoutez une dépendance dans le fichier parent `pom.xml`.

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
      >Veillez à mettre à jour le numéro de version du connecteur amélioré avant de copier la dépendance sur le parent `pom.xml`.

   1. Ajoutez une dépendance dans le fichier `all module pom.xml`.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
      ```


1. Ajoutez des incorporations `pom.xml`. Ajoutez les packages [!DNL Workfront for Experience Manager enhanced connector] à la section `embeddeds` du `pom.xml` de tous vos sous-projets. Nécessite qu’il soit incorporé dans tous les modules `pom.xml`.

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

1. Envoyez les modifications au référentiel.

1. Exécutez le pipeline pour [déployer les modifications dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=fr).

1. Pour créer une configuration utilisateur système, créez `wf-workfront-users` dans le groupe d’utilisateurs [!DNL Experience Manager] et affectez l’autorisation `jcr:all` à `/content/dam`. Un utilisateur système `workfront-tools` est créée automatiquement et les autorisations requises sont gérées automatiquement. Tous les utilisateurs de [!DNL Workfront] qui utilisent le connecteur amélioré sont automatiquement ajoutés dans le cadre de ce groupe.

Pour plus d’informations sur la mise à jour du [!DNL Workfront for Experience Manager enhanced connector] d’une version précédente à la dernière version, cliquez [ici](update-workfront-enhanced-connector.md).

## Configurer la connexion entre [!DNL Experience Manager] as a [!DNL Cloud Service] et [!DNL Workfront] {#configure-connection}

Pour créer une connexion avec [!DNL Workfront], procédez comme suit :

1. Dans [!DNL Experience Manager], sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Configuration des outils Workfront]**.

1. Sélectionnez `workfront-tools` dans le panneau de gauche et sélectionnez l’option **[!UICONTROL Créer]** dans la zone supérieure droite de la page.

1. Dans la boîte de dialogue **[!UICONTROL Connexion Workfront]**, fournissez les détails requis de votre déploiement [!DNL Workfront], et sélectionnez l’option **[!UICONTROL Connexion à Workfront]**. Une fois la connexion établie, l’intégration personnalisée du document [!DNL Workfront] est créée automatiquement dans l’environnement [!DNL Workfront].

   ![Connexion [!DNL Experience Manager] et [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Accédez à l’onglet **[!UICONTROL Avancé]** et sélectionnez l’option **[!UICONTROL Le serveur est-il AEM as a Cloud Service ?]**

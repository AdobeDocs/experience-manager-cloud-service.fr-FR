---
title: Installation de la version [!DNL Workfront for Experience Manager enhanced connector]
description: Installation de la version [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Workfront Integrations and Apps
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 99%

---

# Installation de la version [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Un utilisateur disposant d’un accès administrateur dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] installe le connecteur amélioré. Avant de procéder à l’installation, vérifiez la prise en charge de la plateforme et d’autres [conditions préalables pour le connecteur](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Depuis juin 2022, Adobe a lancé une nouvelle intégration native pour connecter Workfront à Adobe Experience Manager Assets as a Cloud Service. Cette intégration est devenue la méthode requise pour connecter ces deux solutions. Toute nouvelle implémentation future du connecteur amélioré (version 1.9.8 et versions ultérieures) pour connecter Workfront à AEM Assets as a Cloud Service est bloquée. Pour plus d’informations sur la configuration de cette intégration, voir [Configurer l’intégration Experience Manager Assets as a Cloud Service](workfront-connector-configure.md).

>[!IMPORTANT]
>
>* Adobe nécessite le déploiement et la configuration de [!DNL Adobe Workfront for Experience Manager enhanced connector] uniquement par le biais de partenaires certifiés ou [!DNL Adobe Professional Services]. S’il est déployé et configuré sans partenaire certifié ou sans [!DNL Adobe Professional Services], il n’est pas pris en charge par Adobe.
>
>* Adobe peut publier des mises à jour d’[!DNL Adobe Workfront] et d’[!DNL Adobe Experience Manager] qui rendent ce connecteur redondant ; si cela se produit, les clients peuvent être amenés à cesser d’utiliser ce connecteur.
>
>* Adobe prend en charge les versions 1.7.4 et supérieures du connecteur. Les versions précédentes et personnalisées ne sont pas prises en charge. Pour vérifier la version du connecteur amélioré, consultez l’étape 5(a) des [instructions d’installation du connecteur amélioré](workfront-connector-install.md).
>
>* Consultez la section [Examen de certification des partenaires pour Workfront pour le connecteur amélioré Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Pour plus d’informations sur l’examen, consultez le [Guide d’examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

Avant d’installer le connecteur, procédez comme suit :

1. Si votre programme AEM as a Cloud Service a configuré la mise en réseau avancée et activé la liste autorisée d’IP, vous devez ajouter les adresses IP de Workfront à cette liste autorisée pour permettre aux abonnements aux événement et aux divers appels API de passer à AEM.

   * [IP de cluster Workfront](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/get-started-administration/configure-your-firewall.html?lang=fr#ip-addresses-to-allow-for-clusters-1-2-3-5-7-8-and-9). Pour connaître le cluster d’IP dans [!DNL Workfront], accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Système]** > **[!UICONTROL Informations sur le client]**.

   * [IP des API d’abonnement à un événement Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-api/event-subscriptions/event-subs-api.html?lang=fr)

   >[!IMPORTANT]
   >
   >* Si la mise en réseau avancée est configurée pour votre programme et que vous utilisez la liste autorisée d’IP, en raison d’une limitation de l’architecture du connecteur amélioré de Workfront, vous devez également ajouter l’adresse IP sortante du programme à la liste autorisée dans Cloud Manager.
   >
   >* p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >* Pour trouver l’adresse IP de votre programme, ouvrez une fenêtre de terminal et exécutez une commande, telle que :
   >
   >    ```
   >    dscacheutil -q host -a name p{PROGRAM_ID}.external.adobeaemcloud.com
   >    
   >    ```

1. Assurez-vous que les recouvrements suivants n’existent pas dans le référentiel [!DNL Experience Manager] : Si ces chemins contiennent des recouvrements préexistants, vous devez supprimer les recouvrements ou fusionner les différences de modifications entre les deux :

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

1. Téléchargez le connecteur amélioré depuis la [distribution logicielle Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

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

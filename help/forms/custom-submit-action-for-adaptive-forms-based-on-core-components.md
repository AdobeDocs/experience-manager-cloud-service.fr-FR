---
title: Comment créer une action Envoyer personnalisée pour un formulaire adaptatif basé sur les composants principaux ?
description: Découvrez comment créer une action d’envoi personnalisée pour un Forms adaptatif afin de traiter les données avant envoi à l’aide de l’action d’envoi personnalisée.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Intermediate
exl-id: a369b585-d148-4b5a-8afe-d5673ea865d0
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 10%

---

# Création d’une action Envoyer personnalisée pour le Forms adaptatif (composants principaux)

Une action d’envoi permet aux utilisateurs et utilisatrices de sélectionner la destination des données capturées à partir d’un formulaire et de définir des fonctionnalités supplémentaires à exécuter lors de l’envoi du formulaire. AEM Form prend en charge plusieurs actions d’envoi prêtes à l’emploi [OOTB)](/help/forms/configure-submit-actions-core-components.md) telles que l’envoi d’un e-mail ou l’enregistrement de données dans SharePoint ou OneDrive.

Vous pouvez également créer une action d’envoi personnalisée pour ajouter des fonctionnalités non incluses dans les [options prêtes à l’emploi](/help/forms/configure-submit-actions-core-components.md#select-and-configure-a-submit-action-for-an-adaptive-form-select-and-configure-submit-action). Par exemple, intégrez les données de formulaire à une application tierce ou déclenchez une notification SMS personnalisée en fonction des entrées de l’utilisateur.

<!-- ![Custom Submit Image](/help/forms/assets/custom-submit-action-hero-image.png)
-->

## Conditions préalables

Avant de commencer à créer votre première action d’envoi personnalisée pour le Forms adaptatif, vérifiez que vous disposez des éléments suivants :

* **Éditeur de texte brut (IDE)** : bien que tout éditeur de texte brut puisse fonctionner, un environnement de développement intégré (IDE) comme Microsoft Visual Studio Code offre des fonctionnalités avancées pour faciliter la modification.

* **Git** : ce système de contrôle de version est nécessaire pour gérer les modifications de code. Si vous ne l’avez pas installé, téléchargez-le à partir de https://git-scm.com.

## Créer votre première action d’envoi personnalisée pour le formulaire

Le diagramme ci-dessous décrit les étapes de création d’une action d’envoi personnalisée pour un formulaire adaptatif :

![Workflow d’action d’envoi personnalisé](/help/forms/assets/custom-submit-action-workflow.png){width=50%, height-50%}

### Clonez le référentiel Git d’AEM as a Cloud Service.

1. Ouvrez la ligne de commande et sélectionnez un répertoire pour stocker votre référentiel AEM as a Cloud Service, tel que `/cloud-service-repository/`.

1. Exécutez la commande ci-dessous pour cloner le référentiel :

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```

   **Où trouver ces informations ?**

   Pour obtenir des instructions détaillées sur la localisation de ces détails, reportez-vous à l’article Adobe Experience League « [Accès à Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) ».

   **Votre projet est prêt !**

   Une fois la commande terminée, un nouveau dossier est créé dans votre répertoire local. Ce dossier porte le nom de votre application (par exemple, app-id). Ce dossier contient tous les fichiers et le code téléchargés à partir de votre référentiel Git AEM as a Cloud Service. Le `<appid>` de votre projet AEM se trouve dans le fichier `archetype.properties`.

   ![Propriétés de l’archétype](/help/forms/assets/custom-submit-action-archetype-app-id.png)

   Tout au long de ce guide, nous nous référons à ce dossier sous le nom de `[AEMaaCS project directory]`.

## Ajouter une nouvelle action d’envoi

1. Ouvrez le dossier du référentiel dans un éditeur.

   ![Référentiel cloné](/help/forms/assets/custom-submit-action-clone-repo.png)

1. Accédez au répertoire suivant dans votre `[AEMaaCS project directory]` :

   ```
   /ui.apps/src/main/content/jcr_root/apps/<app-id>/
   ```

   **Important** : remplacez `<app-id>` par votre ID d’application réel.

1. Créez un dossier pour votre action d’envoi personnalisée et donnez-lui un nom de votre choix. Par exemple, nommez le dossier `customsubmitaction`.

   ![Créer un dossier d’action d’envoi personnalisé](/help/forms/assets/custom-submit-action-create-folder.png)

1. Accédez au répertoire de l’action d’envoi personnalisée ajoutée.

   Dans votre `[AEMaaCS project directory]`, accédez au chemin suivant :

   `/ui.apps/src/main/content/jcr_root/apps/<app-id>/customsubmitaction/`

   `Important` : remplacez `<app-id>` par votre ID d’application réel.

1. Créez un fichier de configuration.
Dans le dossier `customsubmitaction`, créez un fichier nommé `.content.xml`.

   ![ Créer un fichier de configuration ](/help/forms/assets/custom-submit-action-create-config-folder.png)

1. Ouvrez ce fichier et collez le contenu suivant, en remplaçant `[customsubmitaction]` par le nom de votre action d’envoi

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
   jcr:description="[customsubmitaction]"
   jcr:primaryType="sling:Folder"
   
   guideComponentType="fd/af/components/guidesubmittype"
   guideDataModel="basic,xfa,xsd"
   submitService="[customsubmitaction]"/>
   ```

   Par exemple, remplacez le `[customsubmitaction]` par le nom de votre action d’envoi personnalisée, comme `Custom Submit Action`.

   ![Créer un fichier de configuration d’action d’envoi personnalisée](/help/forms/assets/custom-submit-action-config-file.png)

   >[!NOTE]
   >
   > Mémorisez le nom de l’[customsubmitaction], car le même nom apparaît dans la liste déroulante `Submit action` lors de la création d’un formulaire.


**Inclure le nouveau dossier dans`filter.xml`**

1. Accédez au fichier `/ui.apps/src/main/content/META-INF/vault/filter.xml` dans votre [répertoire de projet AEMaaCS].

1. Ouvrez le fichier et ajoutez la ligne suivante à la fin :

   ```
   <filter root="/apps/<app-id>/[customsubmitaction-folder]"/>
   ```

   Par exemple, ajoutez la ligne de code suivante pour ajouter le dossier `customsubmitaction` dans le fichier `filter.xml` :

   ```
   <filter root="/apps/wknd/customsubmitaction"/>
   ```

   ![Ajoutez les dossiers créés dans le fichier filter.xml](/help/forms/assets/custom-submit-action-filter-xml.png)

1. Enregistrez les modifications.

### Mettez en œuvre le service pour l’action d’envoi ajoutée.

1. Accédez au répertoire suivant dans votre `[AEMaaCS project directory]` :
   `/core/src/main/java/com/<app-id>/core/service/`
   `Important` : remplacez `<app-id>` par votre ID d’application réel.
1. Créez un fichier Java pour implémenter le service pour l’action d’envoi ajoutée. Par exemple, ajoutez le nouveau fichier Java en tant que `CustomSubmitService.java`.

   ![Dossier d’action d’envoi personnalisé](/help/forms/assets/custom-submit-action-custom-submit-folder.png)

1. Ouvrez ce fichier et ajoutez le code pour l’implémentation de votre action d’envoi personnalisée.

   Par exemple, le code Java ci-dessous est un service OSGi qui gère l’envoi du formulaire en consignant les données envoyées et renvoie un `OK` de statut. Ajoutez le code suivant dans le fichier `CustomSubmitService.java` :

   ```
   package com.wknd.core.service;
   
   import com.adobe.aemds.guide.model.FormSubmitInfo;
   import com.adobe.aemds.guide.service.FormSubmitActionService;
   import java.util.HashMap;
   import java.util.Map;
   import org.osgi.service.component.annotations.Component;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
       @Component(
       service = FormSubmitActionService.class,
       immediate = true
           )
       public class CustomSubmitService implements FormSubmitActionService {
   
       private static final String serviceName = "Custom Submit Action";
   
       private static Logger log = LoggerFactory.getLogger(CustomSubmitService.class);
   
       @Override
       public String getServiceName() {
       return serviceName;
       }
   
       @Override
       public Map<String, Object> submit(FormSubmitInfo formSubmitInfo) {
       String data = formSubmitInfo.getData();
       log.info("Using custom submit action service, [data] --> " + data);
       Map<String, Object> result = new HashMap<>();
       result.put("status", "OK");
       return result;
        }
       }
   ```

   ![Service d’action d’envoi personnalisé](/help/forms/assets/custom-submit-action-service.png)

1. Enregistrez les modifications.

### Déployez le code.

**Déploiement du code pour l’environnement de développement local**

* Déployez AEM as a Cloud Service, `[AEMaaCS project directory]`, dans votre environnement de développement local pour essayer la nouvelle action d’envoi sur votre ordinateur local. Pour déployer sur votre environnement de développement local :

   1. Vérifiez que votre environnement de développement local est opérationnel. Si vous n’avez pas encore configuré d’environnement de développement local, reportez-vous au guide sur la [Configuration d’un environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Ouvrez la fenêtre du terminal ou l’invite de commande.

   1. Accédez à la `[AEMaaCS project directory]` .

   1. Exécutez la commande suivante :

      ```
      mvn -PautoInstallPackage clean install
      ```

      ![Déploiement local](/help/forms/assets/custom-submit-action-local-deployment.png)

**Déployer le code pour l’environnement Cloud Service**

* Déployez l’AEM as a Cloud Service, `[AEMaaCS project directory]`, dans votre environnement Cloud Service. Pour effectuer un déploiement dans votre environnement Cloud Service :

   1. Validez vos modifications :

      Après avoir ajouté la nouvelle configuration d’action d’envoi personnalisée, validez vos modifications avec un message Git clair. (Par exemple, « Ajout d’une nouvelle action d’envoi personnalisée »).

   1. Déployez le code mis à jour :

      Déclenchez un déploiement de votre code via le [pipeline full stack existant](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline). Il crée et déploie automatiquement le code mis à jour avec la nouvelle prise en charge d’action d’envoi personnalisée.

      Si vous n’avez pas encore configuré de pipeline, reportez-vous au guide sur [comment configurer un pipeline pour AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline).

      ![Déploiement dans le cloud](/help/forms/assets/custom-submit-action-cloud-deployment.png)

      **Comment confirmer l’installation ?**

      Une fois le projet créé, l’action d’envoi personnalisée s’affiche dans la liste déroulante `Submit action` lors de la création d’un formulaire.

      ![Liste déroulante Action d’envoi personnalisée](/help/forms/assets/custom-submit-action-drop-down-list.png)

  Votre environnement est maintenant prêt à utiliser l’action d’envoi personnalisée ajoutée lors de la création d’un formulaire.

### Prévisualiser un formulaire adaptatif avec une action d’envoi nouvellement ajoutée

1. Connectez-vous à votre instance AEM Forms as a Cloud Service.
1. Accédez à **Formulaires** > **Formulaires et documents**.

   ![Forms et documents](/help/forms/assets/custom-submit-action-fnd.png)

1. Sélectionnez un formulaire adaptatif et cliquez sur **Modifier**. Le formulaire s’ouvre en mode d’édition.

   ![Modifier le formulaire](/help/forms/assets/custom-submit-action-edit-af.png)

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action d’envoi]**, sélectionnez l’action d’envoi. Par exemple, sélectionnez l’action d’envoi comme `Custom Submit Action`.

   ![Formulaire d’envoi personnalisé](/help/forms/assets/custom-submit-action-select-submit-action.png)

1. Remplissez le formulaire et envoyez-le.

   ![Envoyer le formulaire](/help/forms/assets/custom-submit-action-submit-form.png)

   ![Message de remerciement](/help/forms/assets/custom-submit-action-thankyou-msg.png)

   Une fois le formulaire envoyé, vous pouvez vérifier la configuration de la console web de Adobe Experience Manager **&#x200B;**&#x200B;afin de vérifier l’action de l’action d’envoi personnalisée dans l’environnement de développement local.
1. Accédez à `http://<host>:<port>/system/console/configMgr`.

1. Accédez à la page Prise en charge du journal de la console web de Adobe Experience Manager **&#x200B;**&#x200B;à l’adresse `http://<host>:<port>/system/console/slinglog`.

   ![ConfigMgr ](/help/forms/assets/custom-submit-action-sling-log.png)

1. Cliquez sur l’option `logs/error.log` .
   ![Ouvrez le fichier error.log](/help/forms/assets/custom-submit-action-error-log.png)

1. Ouvrez le fichier `error.log` pour vérifier que les données y ont été ajoutées.

   ![fichier error.log](/help/forms/assets/custom-submit-action-form-data-display.png)

   >[!NOTE]
   >
   > * Pour afficher les journaux d’erreurs dans l’environnement AEM as a Cloud Service, vous pouvez utiliser Splunk.
   > * Si un service d’action d’envoi personnalisé rencontre une erreur non gérée, AEM as a Cloud Service renvoie une page d’erreur 502 d’HTML.


## Questions fréquentes

**Q : Pourquoi mon formulaire adaptatif affiche-t-il une page d’erreur 5.x.x après l’envoi ?**
Échec du service d’action d’envoi personnalisé avec une erreur non gérée. AEM Cloud Service renvoie ensuite sa page d’erreur par défaut.

<!--
## Best practices

 * It is recommended to use the OSGi service approach for creating a custom submit action, as it is faster than the AEM servlet approach. 

## Next steps
-->

## Articles connexes

{{af-submit-action}}

<!-- The [Adaptive Forms Core Components](https://github.com/adobe/aem-core-forms-components) repository includes a sample folder, `customsubmission/logsubmit`, to simplify the process of adding new custom submit actions. It also provides the Java service implementation for the `logsubmit` custom submit action, named `CustomAFSubmitService`.java. These resources are available on GitHub. -->

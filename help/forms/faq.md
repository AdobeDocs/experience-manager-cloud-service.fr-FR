---
title: Questions fréquentes sur AEM Forms as a Cloud Service
description: Questions fréquentes sur Forms as a Cloud Service
contentOwner: khsingh
role: User
feature: Adaptive Forms
index: false
exl-id: 0b14b680-7da5-4e0b-bd6a-c379d148f9d7
source-git-commit: 5ee37f59bb959e0549c0541c6568aa8c135c330e
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 98%

---

# Questions fréquemment posées {#frequently-asked-questions}

* **Puis-je utiliser l’éditeur de code pour créer des règles ?**
Vous pouvez utiliser l’éditeur visuel pour créer des règles. L’éditeur de code n’est pas disponible sur [!DNL Forms] as a Cloud Service. Si votre formulaire adaptatif utilise des scripts de règle développés à l’aide de l’éditeur de code, utilisez l’[Utilitaire de migration](migrate-to-forms-as-a-cloud-service.md) pour convertir vos scripts de code en fonctions personnalisées. Vous pouvez utiliser des fonctions personnalisées avec l’éditeur visuel pour continuer à obtenir les résultats obtenus avec l’éditeur de code.

* **Puis-je créer un formulaire adaptatif XFA sur des instances de Cloud Service ?**
Oui, vous pouvez créer un formulaire adaptatif XFA sur une instance de Cloud Service. La prise en charge des formulaires adaptatifs XFA n’est toutefois pas disponible pour le SDK AEM Forms as a Cloud Service (environnement de développement local). Si vous envisagez d’utiliser un formulaire adaptatif XFA dans le SDK AEM Forms as a Cloud Service contactez l’assistance Adobe pour obtenir des détails sur votre cas d’utilisation et les exigences spécifiques.

<!-- * **Can I use an XDP as a Document of Record (DoR) template? Is Forms Designer included in AEM Forms as a Cloud Service license?** 

  Yes, you can use an XDP as a Document of Record template on Cloud Service instances. However, support to use XDP as a Document of Record template is not available for AEM Forms as a Cloud Service SDK (Local development environment). -->

* **Puis-je migrer du contenu d’un environnement On-Premise ou [!DNL Adobe-Managed Services] vers un environnement [!DNL Forms] as a Cloud Service ?**
Oui, vous pouvez migrer votre code, votre contenu et vos ressources personnalisés depuis les environnements On-Premise ou [!DNL Adobe-Managed Services] vers un environnement [!DNL Forms] as a Cloud Service. Pour obtenir des instructions détaillées, voir [Migrer vers Forms as a Cloud Service](migrate-to-forms-as-a-cloud-service.md).

<!-- You can use package manager or Experience Manager UI to [export and import Forms and related assets](import-export-forms-templates.md), use the migration utility to make your existing assets compatible with [!DNL Forms] as a Cloud Service, use the [Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#best-practices-analyzer) tool to find the features and APIs that require changes and updated before migration, and use the [Content Transfer Tools](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/home.html) to move your custom code without refactoring it. -->

* **Où puis-je obtenir la documentation de référence des API [!DNL Java™] d’AEM [!DNL Forms] as a Cloud Service ?**
Vous pouvez télécharger la documentation de référence API Java™ depuis [!DNL Maven Central Repository]. Pour télécharger :
   1. Accédez à [[!DNL Maven Central Repository]](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. Recherchez et ouvrez la page contenant la dernière version de [!DNL Experience Manager Forms] SDK.
   1. Cliquez sur l’option Afficher tout pour vue tous les fichiers.
   1. Téléchargez et extrayez le fichier `aem-forms-sdk-api-<version>-javadocs`.jar.
   1. Ouvrez le fichier index.html pour visualiser la documentation de référence API.

* **Où puis-je obtenir une référence de l’API [!DNL JavaScript™] pour les formulaires adaptatifs ?**
Vous pouvez télécharger la documentation de référence de l’API [!DNL JavaScript™] depuis [!DNL  Maven Central Repository]. Pour télécharger :
   1. Ouvrez [[!DNL Maven Central Repository]](https://mvnrepository.com/artifact/com.adobe.aem/aem-forms-sdk-api).
   1. Recherchez et ouvrez la page contenant la dernière version de [!DNL Experience Manager Forms] SDK.
   1. Cliquez sur l’option Afficher tout pour vue tous les fichiers.
   1. Téléchargez et extrayez le `aem-forms-sdk-api-<version>-jsdoc.jar`.
   1. Ouvrez le fichier index.html pour visualiser la documentation de référence API.

* **Puis-je continuer à utiliser les thèmes et modèles existants ?**
Oui, vous pouvez continuer à utiliser les thèmes créés avec des formulaires AEM 6.4 et des formulaires AEM 6.5 après avoir utilisé l’[Utilitaire de migration](migrate-to-forms-as-a-cloud-service.md) pour les déplacer vers [!DNL AEM Forms] as a Cloud Service.

  Vous pouvez également créer un projet basé sur [Archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment) [!DNL AEM Forms] as a Cloud Service et utiliser les exemples de thèmes et de modèles inclus.

* **Puis-je produire des données conformes au schéma ?**
Oui, vous pouvez créer un formulaire adaptatif pour produire des données conformes au schéma.

<!-- * **Can I pass custom parameters to the prefill service?**
Custom parameters are planned for an upcoming release. -->

* **Puis-je mettre en cache du contenu sécurisé ?**
Par défaut, la mise en cache des fonctionnalités de contenu sécurisé est désactivée. Pour activer cette fonction, vous pouvez exécuter les instructions fournies dans [Mise en cache du contenu sécurisé](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=fr).

* **J’ai un formulaire adaptatif localisé ; il n’effectue pas de rendu de la version localisée ? Quelle pourrait en être la cause et comment la résoudre ?**

  La convention d’URL des formulaires adaptatifs localisés prend désormais en charge la spécification d’un paramètre régional dans l’URL. La nouvelle convention d’URL permet de mettre en cache les formulaires localisés sur un Dispatcher ou un CDN. Sur l’environnement Cloud Service, utilisez le format d’URL `http://host:port/content/forms/af/<afName>.<locale>.html` pour demander une version localisée d’un formulaire adaptatif au lieu de `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe recommande d’utiliser la mise en cache du Dispatcher ou du CDN. Cela permet d’améliorer la vitesse de rendu des formulaires préremplis.

* **J’ai mis à jour un formulaire ; la version mise à jour n’est pas disponible pour les clients ?**
Par défaut, le CDN actualise le cache toutes les 5 minutes, patiente pendant 5 minutes, puis recherche la version mise à jour.

* **Puis-je utiliser l’étape de signature d’un formulaire adaptatif pour créer une expérience de signature dans le navigateur ?**
Non, l’étape de signature n’est pas disponible pour [!DNL Forms] as a Cloud Service. Supprimez l’étape de vos formulaires adaptatifs. Au lieu de l’étape de signature, autorisez les utilisateurs à signer un formulaire adaptatif après envoi. Cela vous permet de continuer à fournir une expérience de signature intégrée au navigateur.

* **Puis-je utiliser l’étape de vérification dans un formulaire adaptatif ?**
Non, l’étape de vérification n’est pas disponible pour [!DNL Forms] as a Cloud Service. Supprimez l’étape de vérification de vos formulaires adaptatifs existants avant de déplacer ces formulaires vers un environnement Cloud Service.

* **Puis-je ajouter des graphiques à un formulaire adaptatif ?**
Oui, vous pouvez ajouter des graphiques aux formulaires adaptatifs. Les formulaires adaptatifs fournissent un composant de graphique. Vous pouvez l’utiliser pour ajouter des graphiques à un formulaire adaptatif.

* **Puis-je connecter un modèle de données de formulaire à un modèle de base de données relationnelle ?**
Vous pouvez connecter un modèle de données de formulaire à [!DNL RESTful web services], [!DNL SOAP-based web services], [!DNL OData services] et un profil utilisateur Experience Manager en tant que sources de données. <!--Support to connect a Form Data Model with a relational database is not available.-->

* **Puis-je utiliser des certificats personnalisés avec le modèle de données de formulaire (FDM) pour l’authentification ?**
Le modèle de données de formulaire (FDM) ne fournit pas de méthode permettant d’utiliser des certificats personnalisés pour l’authentification. Par conséquent, les certificats personnalisés tels que x509 et SSL bidirectionnel ne sont pas pris en charge.

* **Puis-je utiliser des formulaires adaptatifs à soumettre au portail Formulaires ?**

  Vous pouvez modifier vos formulaires adaptatifs existants afin d’utiliser les actions d’envoi [Envoyer au point d’entrée REST](configuring-submit-actions.md#submit-to-rest-endpoint), [Envoyer un e-mail](configuring-submit-actions.md#send-email), [Envoyer à l’aide d’un modèle de données de formulaire (FDM)](configuring-submit-actions.md#submit-using-form-data-model) et [Appeler un workflow AEM](configuring-submit-actions.md#invoke-an-aem-workflow). Le portail Formulaires et l’action d’envoi au portail Formulaires ne sont pas encore disponibles. Surveillez les notes de mise à jour mensuelles pour connaître la disponibilité des fonctionnalités.

* **Puis-je utiliser l’application [!DNL AEM Forms] avec [!DNL AEM Forms] as a Cloud Service ?**

  Les formulaires adaptatifs offrent un design réactif. Ces formulaires modifient l’aspect, la conception et l’interactivité en fonction de l’appareil sous-jacent. Vous pouvez continuer à utiliser des formulaires adaptatifs sur un appareil mobile tout en surveillant les notes de mise à jour mensuelles concernant la disponibilité des fonctionnalités.

* **Quelles fonctionnalités ne font pas partie de la version GA initiale ?**
Le portail Formulaires, l’application [!DNL AEM Forms], l’intégration à Adobe Analytics et l’intégration à Adobe Target ne font pas partie de la version GA initiale. Consultez les notes de mise à jour mensuelles pour en savoir plus sur les nouvelles fonctionnalités.

* **J’ai conçu un [schéma JSON pour créer un formulaire adaptatif](adaptive-form-json-schema-form-model.md). Le schéma JSON définit les événements pour certains composants des formulaires adaptatifs. AEM Forms as a Cloud Service prend-il en charge les événements ?**
Créez le formulaire adaptatif basé sur le schéma JSON de l’environnement Experience Manager 6.5 Forms et utilisez l’[utilitaire de migration](migrate-to-forms-as-a-cloud-service.md) pour migrer ce type de formulaire adaptatif vers AEM Forms as a Cloud Service. L’utilitaire convertit ces événements en bibliothèques clientes et vous pouvez continuer à utiliser les formulaires adaptatifs avec des événements dans un environnement Cloud Service.

<!-- 

* **Is there any AEM Forms as a Cloud Service connector for Microsoft Power Automate?**

  Yes, Adobe provides an Adobe Experience Manager connector to access [Adobe Experience Manager Forms - Communication capabilities](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html) through Microsoft Power Automate. You can create a PDF document that is based on a form design and XML form data or create PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) and other Printer Definition Language documents. 

  You can get started with Adobe Experience Manager easily with just a few steps:

  1. Generate the Service credentials: Use Adobe Experience Manager Developer Console to [generate](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?#generate-service-credentials) the service credentials.  
  
  1. Setup your connection: Add your service credentials to the Adobe Experience Manager Connector. You can get crdential from service credential JSON and copy these credential details to your one-time connection setup:

    * AEM Server
    * Organization ID 
    * Client ID
    * Client Secret
    * Technical Account ID
    * Meta Scopes
    * Private Key - base64 encoded keys are accepted
    * Adobe IMS Host URL

    <br> 
    
    ![Use your Service Credential JSON for credential details](assets/forms-aem-pa-connector-connection.png)

    A sample Service Credential JSON file fields mapped to Adobe Experience Manager connector for Microsoft Power Automate.

    -->

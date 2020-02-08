---
title: Intégration à Adobe Target
description: 'Intégration à Adobe Target '
translation-type: tm+mt
source-git-commit: 518c3156b2ee1f6431ea11333c57548a42133aa9

---


# Intégration à Adobe Target{#integrating-with-adobe-target}

As part of the Adobe Marketing Cloud, [Adobe Target](http://www.adobe.com/solutions/testing-targeting/testandtarget.html) lets you increase content relevance through targeting and measuring across all channels. Adobe Target est utilisé par les marketeurs pour concevoir et exécuter des tests en ligne, créer des segments de public à la volée (en fonction du comportement) et automatiser le ciblage du contenu et les expériences en ligne. AEM en tant que service Cloud a adopté le processus de ciblage utilisé dans Adobe Target Standard. Si vous utilisez Target, vous serez familiarisé avec l’environnement de modification du ciblage dans AEM en tant que service Cloud.

Intégrez vos sites AEM à Adobe Target pour personnaliser le contenu dans vos pages :

* Mettez en œuvre le ciblage du contenu.
* Utilisez les publics cibles pour créer des expériences personnalisées.
* Envoyez des données contextuelles à Target lorsque des visiteurs interagissent avec vos pages.
* Suivez les taux de conversion.

>[!NOTE]
>
>Les clients Adobe Experience Manager en tant que clients du service Cloud qui ne disposent pas d’un compte Target existant peuvent demander l’accès à Target Foundation Pack pour Experience Cloud.  Foundation Pack offre une utilisation limitée en volume de Target.


Pour assurer l’intégration à Target, effectuez les tâches suivantes :

* [Effectuez les tâches préalables nécessaires](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html) : inscrivez-vous auprès d’Adobe Target et configurez certains aspects de l’instance de création AEM. Your Adobe Target account must have **approver** level permissions at a minimum. En outre, vous devez sécuriser les paramètres d’activité sur le nœud de publication afin que celui-ci ne soit pas accessible pour les utilisateurs.

* Lancer par Adobe est l’outil par défaut permettant d’instrumenter un site AEM avec des fonctionnalités Target (bibliothèques JS). Par conséquent, l’intégration d’AEM en tant que service Cloud avec Launch et Adobe Target s’effectue main dans la main (voir les liens ci-dessous).

   * [Intégration à Adobe Target à l’aide des E/S Adobe](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html)
   * [Intégrer le lancement par Adobe](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
   * [Intégration d’AEM à Adobe Launch par le biais des E/S Adobe](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
   * [Présentation de l’intégration d’AEM au lancement par Adobe, Analytics et Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)

1. [Configurez les activités](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html) : Associez vos activités à la configuration cloud Target.

>[!NOTE]
>
>La configuration IMS (comptes techniques) pour le lancement par Adobe est préconfigurée dans AEM en tant que service Cloud. Les utilisateurs n’ont pas à créer cette configuration.

>[!NOTE]
>
>Si vous utilisez Target avec une configuration de proxy personnalisée, vous devez configurer les deux configurations de proxy client HTTP, car certaines fonctionnalités d’AEM utilisent les API 3.x et d’autres les API 4.x :
>
>* 3.x is configured with [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* Les API 4.x sont configurées avec [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



>[!CAUTION]
>
>Vous devez sécuriser le nœud de paramètres d’activité **c:ActivitySettings** sur l’instance de publication de sorte qu’il ne soit pas accessible pour les utilisateurs normaux. Le nœud de paramètres d’activité doit être accessible uniquement au service gérant la synchronisation de l’activité avec Adobe Target.
>
>Voir [Préalables à l’intégration à Adobe Target](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node) pour plus d’informations.

When the integration is complete, you can [author targeted content](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/content-targeting-touch.html) that sends visitor data to Adobe Target. Notez que les composants de page nécessitent un code spécifique pour activer le ciblage de contenu. (See [Developing for Targeted Content](https://docs.adobe.com/content/help/en/experience-manager-65/developing/personlization/target.html).

>[!NOTE]
>
>Lorsque vous ciblez un composant dans le mode Auteur AEM, il effectue une série d’appels côté serveur vers Adobe Target afin d’enregistrer la campagne, de configurer des offres et de récupérer des segments Adobe Target (si cela est configuré). Aucun appel côté serveur n’est effectué depuis la publication AEM vers Adobe Target.

## Sources d’informations en arrière-plan {#background-information-sources}

L’intégration d’AEM en tant que service Cloud avec Adobe Target nécessite une connaissance approfondie d’Adobe Target, de la gestion des activités AEM et de la gestion des audiences AEM. Vous devez connaître les informations suivantes :

* Adobe Target (See the [Adobe Target documentation](https://marketing.adobe.com/resources/help/en_US/target/)).
* AEM Activities console (See [Managing Activities](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html).
* Publics AEM (voir [Gestion des publics](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/managing-audiences.html).

>[!NOTE]
>
>Lorsque vous travaillez avec Adobe Target, le nombre maximal d’artefacts autorisés dans une campagne est le suivant :
>
>* 50 emplacements
>* 2 000 expériences
>* 50 mesures
>* 50 segments de création de rapports
>



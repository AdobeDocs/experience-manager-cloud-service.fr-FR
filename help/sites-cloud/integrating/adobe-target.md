---
title: Intégration à Adobe Target
description: Intégration à Adobe Target
exl-id: 2b4cf35e-2b75-4303-8d09-f6644ad99274
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 86%

---

# Intégration à Adobe Target{#integrating-with-adobe-target}

Dans le cadre d’Adobe Marketing Cloud, [Adobe Target](https://www.adobe.com/fr/solutions/testing-targeting/testandtarget.html) vous permet d’améliorer la pertinence du contenu en effectuant un ciblage et des mesures sur tous les canaux. Adobe Target est utilisé par les spécialistes marketing pour concevoir et exécuter des tests en ligne, créer des segments ciblés à la volée (en fonction du comportement) et automatiser le ciblage du contenu et les expériences en ligne. AEM as a Cloud Service a adopté le workflow de ciblage qui est utilisé dans Adobe Target Standard. Si vous utilisez Target, vous connaissez l’environnement d’édition de ciblage dans AEM as a Cloud Service.

Intégrez vos sites AEM à Adobe Target pour personnaliser le contenu dans vos pages :

* Mettez en oeuvre le ciblage du contenu.
* Utilisez les audiences Target pour créer des expériences personnalisées.
* Envoyez des données contextuelles à Target lorsque les visiteurs interagissent avec vos pages.
* Suivi des taux de conversion.

>[!NOTE]
>
>Les clients Adobe Experience Manager as a Cloud Service qui ne disposent pas d’un compte Target existant peuvent demander l’accès au Target Foundation Pack pour Experience Cloud. Le Foundation Pack offre une utilisation limitée en volume de Target.


Pour assurer l’intégration à Target, effectuez les tâches suivantes :

* [Effectuez les tâches préalables nécessaires](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html?lang=fr) : inscrivez-vous auprès d’Adobe Target et configurez certains aspects de l’instance de création AEM. Votre compte Adobe Target doit disposer au minimum des autorisations de niveau **approbateur**. En outre, vous devez sécuriser les paramètres d’activité sur le nœud de publication afin que celui-ci ne soit pas accessible par les utilisateurs.

* Experience Platform Launch est l’outil par défaut permettant d’instrumenter un site AEM avec des fonctionnalités Target (bibliothèques JS). Par conséquent, l’intégration d’AEM as a Cloud Service avec Launch et Adobe Target s’effectue de façon conjointe (voir les liens ci-dessous).

   * [Intégration à Adobe Target à l’aide d’Adobe I/O](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/integration-target-ims-adobe-io.html?lang=fr)
   * [Intégrer Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html?lang=fr)
   * [Intégration d’AEM à Adobe Launch par le biais d’Adobe I/O](https://docs.adobe.com/content/help/fr/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html)
   * [Présentation de l’intégration d’AEM à Experience Platform Launch, Analytics et Target](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html?lang=fr)

>[!NOTE]
>
>La configuration IMS (comptes techniques) pour Experience Platform Launch est préconfigurée dans AEM as a Cloud Service. Les utilisateurs n’ont pas à créer cette configuration.

1. [Configurez les activités](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html?lang=fr) : Associez vos activités à la configuration cloud Target.

>[!CAUTION]
>
>Dans AEM as a Cloud Service, l’agent de réplication qui synchronise les offres et les activités d’AEM vers Adobe Target est désactivé par défaut. Contactez l’équipe d’[assistance Adobe](https://experienceleague.adobe.com/?support-solution=General&amp;lang=fr#support) si vous devez le réactiver.

>[!NOTE]
>
>Si vous utilisez Target avec une configuration de proxy personnalisée, vous devez configurer les deux configurations de proxy client HTTP, car certaines fonctionnalités d’AEM utilisent les API 3.x et d’autres les API 4.x :
>
>* La version 3.x est configurée avec [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* Les API 4.x sont configurées avec [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>

>[!CAUTION]
>
>Vous devez sécuriser le nœud de paramètres d’activité **c:ActivitySettings** sur l’instance de publication de sorte qu’il ne soit pas accessible pour les utilisateurs normaux. Le nœud de paramètres d’activité doit être accessible uniquement au service gérant la synchronisation de l’activité avec Adobe Target.
>
>Voir [Conditions préalables à l’intégration à Adobe Target](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html?lang=fr#securing-the-activity-settings-node) pour plus d’informations.

Une fois l’intégration terminée, vous pouvez [créer du contenu ciblé](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/content-targeting-touch.html?lang=fr) qui envoie les données de visiteur à Adobe Target. Notez que les composants de page requièrent un code spécifique pour activer le ciblage du contenu. (consultez [Développement pour le contenu ciblé](https://experienceleague.adobe.com/docs/experience-manager-65/developing/personlization/target.html?lang=fr)).

>[!NOTE]
>
>Lorsque vous ciblez un composant dans AEM auteur, le composant effectue une série d’appels côté serveur vers Adobe Target pour enregistrer la campagne, configurer des offres et récupérer des segments Adobe Target (s’ils sont configurés). Aucun appel côté serveur n’est effectué depuis la publication AEM vers Adobe Target.

## Sources d’informations sur le contexte {#background-information-sources}

Intégrer AEM as a Cloud Service à Adobe Target nécessite des connaissances sur Adobe Target, la gestion des activités AEM et la gestion des audiences AEM. Vous devez connaître les éléments suivants :

* Adobe Target (consultez la [documentation sur Adobe Target](https://experienceleague.adobe.com/docs/target/using/target-home.html?lang=fr)).
* Console des activités AEM (consultez la section [Gestion des activités](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html?lang=fr)).
* Audiences AEM (consultez la section [Gestion des audiences](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/managing-audiences.html?lang=fr)).

>[!NOTE]
>
>Lorsque vous travaillez avec Adobe Target, le nombre maximal d’artefacts autorisés dans une campagne est le suivant :
>
>* 50 emplacements
>* 2 000 expériences
>* 50 mesures
>* 50 segments de création de rapports

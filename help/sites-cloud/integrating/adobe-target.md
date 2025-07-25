---
title: Intégration à Adobe Target
description: Intégration à Adobe Target
exl-id: 2b4cf35e-2b75-4303-8d09-f6644ad99274
source-git-commit: 0af1f7dcc330a2ee5300088f274150a3ea79efe8
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 94%

---

# Intégration à Adobe Target{#integrating-with-adobe-target}

Dans le cadre d’Adobe Experience Cloud, [Adobe Target](https://business.adobe.com/fr/products/target/adobe-target.html) vous permet d’améliorer la pertinence du contenu en effectuant un ciblage et des mesures sur tous les canaux. Adobe Target est utilisé par les spécialistes marketing pour concevoir et exécuter des tests en ligne, créer des segments ciblés à la volée (en fonction du comportement) et automatiser le ciblage du contenu et les expériences en ligne. AEM as a Cloud Service a adopté le workflow de ciblage qui est utilisé dans Adobe Target Standard. Si vous utilisez Target, vous connaissez l’environnement d’édition de ciblage d’AEM as a Cloud Service.

Intégrez vos sites AEM à Adobe Target pour personnaliser le contenu dans vos pages :

* Implémentez le ciblage du contenu.
* Utilisez les audiences Target pour créer des expériences personnalisées.
* Envoyez des données contextuelles à Target lorsque les visiteurs et les visiteuses interagissent avec vos pages.
* Suivre les taux de conversion.

>[!NOTE]
>
>Les clientes et les clients qui ne disposent pas d’un compte Target existant peuvent demander l’accès au package Target Foundation pour Experience Cloud. Le Foundation Pack offre une utilisation limitée en volume de Target.

Pour assurer l’intégration à Target, effectuez les tâches suivantes :

* [Effectuez les tâches préalables nécessaires](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html?lang=fr) : inscrivez-vous auprès d’Adobe Target et configurez certains aspects de l’instance de création AEM. Votre compte Adobe Target doit disposer au minimum des autorisations de niveau **approbateur**. En outre, vous devez sécuriser les paramètres d’activité sur le nœud de publication afin que celui-ci ne soit pas accessible par les utilisateurs.

* Experience Platform Launch est l’outil par défaut permettant d’instrumenter un site AEM avec des fonctionnalités Target (bibliothèques JS). Par conséquent, l’intégration d’AEM as a Cloud Service avec Launch et Adobe Target s’effectue de façon conjointe (voir les liens ci-dessous).

   * [Intégrer Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html?lang=fr)
   * [Intégration d’AEM à Adobe Launch via Adobe I/O](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html?lang=fr)
   * [Présentation de l’intégration d’AEM à Experience Platform Launch, Analytics et Target](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html?lang=fr)

>[!NOTE]
>
>La configuration IMS (comptes techniques) pour Experience Platform Launch est préconfigurée dans AEM as a Cloud Service. Les utilisateurs n’ont pas à créer cette configuration.

1. [Configurez les activités](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html?lang=fr) : Associez vos activités à la configuration cloud Target.

>[!CAUTION]
>
>Dans AEM as a Cloud Service, l’agent de réplication qui synchronise les offres et les activités d’AEM vers Adobe Target est désactivé par défaut. Contactez l’[assitance technique d’Adobe](https://experienceleague.adobe.com/fr?support-solution=General&lang=fr#support) si vous devez réactiver l’agent de réplication.

>[!NOTE]
>
>Si vous utilisez Target avec une configuration de proxy personnalisée, vous devez configurer les deux configurations de proxy client HTTP, car certaines fonctionnalités d’AEM utilisent les API 3.x et d’autres les API 4.x :
>
>* 3.x est configuré avec [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x est configuré avec [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>

>[!CAUTION]
>
>Sécurisez le nœud de paramètres d’activité **cq:ActivitySettings** sur l’instance de publication afin qu’il ne soit pas accessible aux utilisateurs normaux. Le nœud de paramètres d’activité doit être accessible uniquement au service gérant la synchronisation de l’activité avec Adobe Target.
>
>Voir [Conditions préalables à l’intégration à Adobe Target](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html?lang=fr#securing-the-activity-settings-node) pour plus d’informations.

Une fois l’intégration terminée, vous pouvez [créer du contenu ciblé](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/content-targeting-touch.html?lang=fr) qui envoie les données de visiteur à Adobe Target. Les composants de page requièrent un code spécifique pour activer le ciblage du contenu. (consultez [Développement pour le contenu ciblé](https://experienceleague.adobe.com/docs/experience-manager-65/developing/personlization/target.html?lang=fr)).

>[!NOTE]
>
>Lorsque vous ciblez un composant dans l’instance de création AEM, le composant effectue une série d’appels côté serveur à Adobe Target pour enregistrer la campagne, configurer des offres et récupérer des segments Adobe Target (s’ils sont configurés). Aucun appel côté serveur n’est effectué depuis la publication AEM vers Adobe Target.

## Sources d’informations sur le contexte {#background-information-sources}

Intégrer AEM as a Cloud Service à Adobe Target nécessite des connaissances sur Adobe Target, la gestion des activités AEM et la gestion des audiences AEM. Vous devez connaître les éléments suivants :

* Adobe Target (consultez la [documentation sur Adobe Target](https://experienceleague.adobe.com/docs/target/using/target-home.html?lang=fr)).
* Console des activités AEM (consultez la section [Gestion des activités](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html?lang=fr)).
* Audiences AEM (consultez la section [Gestion des audiences](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/managing-audiences.html?lang=fr)).

>[!NOTE]
>
>Lorsque vous travaillez avec Adobe Target, le nombre maximal d’artefacts autorisés dans une campagne est le suivant :
>
>* 50 emplacements
>* 2 000 expériences
>* 50 mesures
>* 50 segments de création de rapports

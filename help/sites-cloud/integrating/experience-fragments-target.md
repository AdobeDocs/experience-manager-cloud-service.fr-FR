---
title: Exportation de fragments d’expérience vers Adobe Target
description: Découvrez comment exporter vos fragments d’expérience vers Adobe Target pour tester et personnaliser des expériences.
exl-id: 752d91f9-13a6-40c2-9425-7d18dafe9205
solution: Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 96%

---

# Exportation de fragments d’expérience vers Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>* Les fragments d’expérience AEM sont exportés dans l’espace de travail par défaut d’Adobe Target.
>* AEM doit être intégré à Adobe Target conformément aux instructions de la section [Intégration à Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md).

Vous pouvez exporter les [Fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md), créés dans Adobe Experience Manager as a Cloud Service (AEM), dans Adobe Target (Target). Ceux-ci peuvent ensuite être utilisés comme offres dans les activités Target, pour tester et personnaliser les expériences en fonction des besoins.

Il existe trois options de pour exporter un fragment d’expérience vers Adobe Target :

* HTML (par défaut) : prise en charge de la diffusion de contenu web et hybride
* JSON : prise en charge de la diffusion de contenu découplé
* HTML et JSON

Pour préparer votre instance à l’exportation de fragments d’expérience AEM vers Adobe Target, vous devez :

* [Intégrez-la à Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Ajoutez la configuration du cloud](#add-the-cloud-configuration)
* [Ajoutez la configuration héritée](#add-the-legacy-configuration)

Ensuite, vous pouvez :

* [Exporter un fragment d’expérience vers Adobe Target](#exporting-an-experience-fragment-to-adobe-target)
* [Utiliser des fragments d’expérience dans Adobe Target](#using-your-experience-fragments-in-adobe-target)
* Et aussi [Supprimer un fragment d’expérience déjà exporté vers Adobe Target](#deleting-an-experience-fragment-already-exported-to-adobe-target)

Les fragments d’expérience peuvent être exportés vers l’espace de travail par défaut dans Adobe Target ou vers des espaces de travail définis par l’utilisateur pour Adobe Target.

>[!NOTE]
>
>Les espaces de travail Adobe Target n’existent pas dans Adobe Target lui-même. Ils sont définis et gérés dans Adobe IMS (Identity Management System), puis sélectionnés pour une utilisation dans toutes les solutions à l’aide de la console Adobe Developer.

>[!NOTE]
>
>Les espaces de travail Adobe Target peuvent être utilisés pour permettre aux membres d’une organisation (groupe) de créer et de gérer des offres et des activités pour cette organisation uniquement ; sans donner accès à d’autres utilisateurs. Par exemple, les organisations spécifiques à un pays avec une préoccupation mondiale.

>[!NOTE]
>
>Pour plus d’informations, consultez les sections suivantes :
>
>* [Développement d’Adobe Target](https://developers.adobetarget.com/)
>* [Composants principaux - Fragments d’expérience](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)
>* [Adobe Target - Comment utiliser les fragments d’expérience d’Adobe Experience Manager (AEM) ?](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html?lang=fr)
>* [AEM 6.5 - Configuration manuelle de l’intégration avec Adobe Target - Création d’une configuration de cloud Target](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-configuring.html?lang=fr#creating-a-target-cloud-configuration)

## Conditions préalables {#prerequisites}

Plusieurs actions sont requises :

1. Vous devez [intégrer AEM à Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md).

1. Les fragments d’expérience sont exportés à partir de l’instance d’auteur AEM. Vous devez donc [Configurer l’externaliseur de liens d’AEM](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer) sur l’instance d’auteur pour vous assurer que toutes les références contenues dans le fragment d’expérience sont externalisées pour la diffusion web.

   >[!NOTE]
   >
   >Pour la réécriture de liens, non couverte par le format par défaut, il existe un [fournisseur de réécriture de liens des fragments d’expérience](/help/implementing/developing/extending/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html). Vous pouvez ainsi développer des règles personnalisées pour votre instance.

## Ajoutez la configuration du cloud {#add-the-cloud-configuration}

Avant d’exporter un fragment, vous devez ajouter la **configuration cloud** pour **Adobe Target** au fragment ou au dossier. Vous pouvez ainsi :

* spécifier la ou les options de format à utiliser pour l’export ;
* sélectionner un espace de travail Target comme destination ;
* sélectionner un domaine d’externaliseur pour réécrire des références dans le fragment d’expérience (facultatif).

Vous pouvez sélectionner les options obligatoires dans les **propriétés de page** du dossier ou du fragment concerné, ou les deux. La spécification est héritée, le cas échéant.

1. Accédez à la console **Fragments d’expérience**.

1. Ouvrez les **propriétés de page** pour le dossier ou le fragment approprié.

   >[!NOTE]
   >
   >Si vous ajoutez la configuration cloud au dossier parent Fragment d’expérience, celle-ci est héritée par tous les enfants.
   >
   >Si vous ajoutez la configuration cloud au fragment d’expérience lui-même, celle-ci est héritée par toutes les variations.

1. Sélectionnez l’onglet **Services cloud**.

1. Sous **Configuration du service cloud**, sélectionnez **Adobe Target** dans la liste déroulante.

   >[!NOTE]
   >
   >Le format JSON d’une offre de fragment d’expérience peut être personnalisé. Pour ce faire, définissez un composant de fragment d’expérience client, puis annotez comment exporter ses propriétés dans le modèle Sling du composant.
   >
   >Affichez le composant principal : [Composants principaux - Fragments d’expérience](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/experience-fragment.html?lang=fr)

1. Sous **Adobe Target** sélectionnez :

   * la configuration appropriée ;
   * l’option de format requise ;
   * un espace de travail Adobe Target ;
   * si nécessaire - domaine de l’externaliseur

   >[!CAUTION]
   >
   >Le domaine de l’externaliseur est facultatif.
   >
   > Un externaliseur d’AEM est configuré lorsque vous souhaitez que le contenu exporté pointe vers un domaine de *publication* spécifique. Pour plus d’informations, consultez [Configuration de l’externaliseur de liens d’AEM](/help/implementing/developing/extending/experience-fragments.md#configuring-the-aem-link-externalizer).
   >
   > Notez également que les domaines de l’externaliseur sont pertinents uniquement pour le contenu du fragment d’expérience envoyé à Target, et non pour les métadonnées telles que Afficher le contenu de l’offre.

   Par exemple, pour un dossier :

   ![Dossier - Cloud Services](assets/xf-target-integration-01.png "Dossier - Cloud Services")

1. **Enregistrez et fermez**.

## Ajoutez la configuration héritée {#add-the-legacy-configuration}

<!-- This is effectively the Manually Integrating with Adobe Target {#manually-integrating-with-adobe-target} section from 6.5 -->

>[!IMPORTANT]
>
>L’ajout d’une nouvelle configuration héritée est un scénario particulier qui n’est pris en charge que pour l’exportation de fragments d’expérience.

Après avoir [ajouté la configuration cloud](#add-the-cloud-configuration) pour utiliser Experience Platform Launch, pour intégrer initialement AEM à Adobe Target, vous devez également effectuer l’intégration manuelle à Adobe Target à l’aide d’une configuration héritée.

### Création d’une configuration du cloud Target {#creating-a-target-cloud-configuration}

Pour permettre à AEM d’interagir avec Adobe Target, créez une configuration de cloud Target. Pour créer la configuration, vous fournissez le code client Adobe Target et les informations d’identification de l’utilisateur.

Vous créez la configuration de cloud Target une seule fois, car vous pouvez l’associer à plusieurs campagnes AEM. Si vous disposez de plusieurs codes client Adobe Target, créez une configuration pour chaque code client.

Vous pouvez configurer la configuration de cloud pour synchroniser les segments depuis Adobe Target. Si vous activez la synchronisation, les segments sont importés de Target en arrière-plan dès que la configuration du cloud est enregistrée.

Procédez comme suit pour créer une configuration du cloud Target dans AEM :

1. Accédez aux **Services cloud hérités** via le **logo AEM** > **Outils** > **Cloud Services** > **Services cloud hérités**.
Par exemple : ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   La page d’aperçu d’**Adobe Experience Cloud** s’ouvre.

1. Dans la section **Adobe Target**, cliquez sur **Configurer maintenant**.
1. Dans la boîte de dialogue **Créer une configuration** :

   1. Donnez un **titre** à la configuration.
   1. Sélectionnez le modèle **Configuration d’Adobe Target**.
   1. Cliquez sur **Créer**.

Vous pouvez maintenant sélectionner la nouvelle configuration à modifier.

1. La boîte de dialogue de modification s’ouvre.

   ![config-target-settings-dialog](assets/config-target-settings-dialog.png)

   <!-- Can this still occur?

   >[!NOTE]
   >
   >When configuring A4T with AEM, you may see a Configuration reference missing entry. To be able to select the analytics framework, do the following:
   >
   >1. Navigate to **Tools** &gt; **General** &gt; **CRXDE Lite**.
   >1. Navigate to **/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   >1. Set the property **disable** to **false**.
   >1. Select **Save All**.

   -->

1. Dans la boîte de dialogue **Paramètres Adobe Target**, indiquez les valeurs de ces propriétés.

   * **Authentification** : par défaut, il s’agit d’IMS (les informations d’identification de l’utilisateur sont obsolètes).

   * **Code client** : code client du compte Target.

   * **Identifiant du client** : l’identifiant du client

   * **Configuration IMS** : sélectionnez la configuration requise dans la liste déroulante

   * **Type d’API** : par défaut : REST (XML est obsolète)

   * **Configuration d’A4T Analytics Cloud** : sélectionnez la configuration d’Analytics Cloud utilisée pour les objectifs et les mesures des activités de Target. Vous avez besoin de cette option si vous utilisez Adobe Analytics en tant que source de création de rapports lors du ciblage de contenu.

     <!-- Is this needed?
     If you do not see your cloud configuration, see note in [Configuring A4T Analytics Cloud Configuration](#configuring-a-t-analytics-cloud-configuration).
     -->

   * **Utiliser le ciblage précis** : par défaut, cette case est cochée. Si cette option est sélectionnée, la configuration du service cloud attend le chargement du contexte avant de charger le contenu. Lisez la remarque suivante.

   * **Synchroniser les segments à partir d’Adobe Target** : sélectionnez cette option pour télécharger les segments définis dans Target pour les utiliser dans AEM. Sélectionnez cette option lorsque la propriété Type d’API est REST, car les segments incorporés ne sont pas pris en charge et vous devez toujours utiliser les segments de Target. (Le terme AEM « segment » est l’équivalent d’« audience » dans Target.)

   * **Bibliothèque cliente** : par défaut, cette valeur est définie sur AT.js (mbox.js est obsolète).

     >[!NOTE]
     >
     >Le fichier de bibliothèque cible, [AT.JS](https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works.html?lang=fr), est une nouvelle bibliothèque d’implémentation pour Adobe Target qui a été conçue pour les implémentations web classiques et les applications d’une seule page.
     >
     >mbox.js est obsolète et sera supprimé ultérieurement.
     >
     >Adobe vous recommande d’utiliser AT.js comme bibliothèque cliente au lieu de mbox.js.
     >
     >AT.js offre plusieurs améliorations par rapport à la bibliothèque mbox.js :
     >
     >* Amélioration des temps de chargement des pages pour les implémentations web
     >* Amélioration de la sécurité
     >* Meilleures options d’implémentation pour les applications d’une seule page
     >* AT.js contient les composants qui étaient inclus dans target.js. Il n’y a donc plus d’appel à target.js.
     >
     >Vous pouvez sélectionner AT.js ou mbox.js dans le menu déroulant **Bibliothèque cliente**.

   * **Utilisation du système de gestion des balises pour diffuser la bibliothèque cliente** : sélectionnez cette option pour utiliser la bibliothèque cliente depuis Adobe Launch ou un autre système de gestion des balises (ou DTM, qui est obsolète).

   * **Fichier AT.js personnalisé** : parcourez l’arborescence pour charger votre fichier AT.js personnalisé. Laissez vide pour utiliser la bibliothèque par défaut.

     >[!NOTE]
     >
     >Par défaut, lorsque vous souscrivez à l’assistant de configuration Adobe Target, le ciblage précis est activé.
     >
     >Le ciblage précis implique que cette configuration du service cloud attend le chargement du contexte avant de charger le contenu. Par conséquent, en termes de performances, un ciblage précis peut créer un délai de quelques millisecondes avant le chargement du contenu.
     >
     >Le ciblage précis est toujours activé sur l’instance de création. Toutefois, sur l’instance de publication, vous pouvez choisir de le désactiver en désactivant la coche en regard de Ciblage précis dans la configuration du service cloud (**http://localhost:4502/etc/cloudservices.html**). Vous pouvez également activer et désactiver le ciblage précis pour chaque composant, quel que soit votre paramètre dans la configuration du service cloud.
     >
     >Si vous avez ***déjà*** créé les composants ciblés et si vous modifiez ce paramètre, vos modifications n’affectent pas ces composants. Vous devez apporter des modifications directement à ces composants.

1. Cliquez sur **Se connecter à Adobe Target** pour lancer la connexion à Target. Si la connexion est réussie, le message **Connexion réussie** s’affiche. Cliquez sur **OK** dans le message et **OK** dans la boîte de dialogue.

### Ajout d’un framework Target {#adding-a-target-framework}

<!-- Is this section needed? -->

Une fois que vous avez configuré la configuration de cloud Target, ajoutez une structure Target. La structure identifie les paramètres par défaut qui sont envoyés à Adobe Target à partir des composants [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md) disponibles. Target utilise les paramètres pour déterminer les segments qui s’appliquent au contexte actuel.

Vous pouvez créer des structures multiples pour une même configuration Target. Les structures multiples s’avèrent utiles lorsque vous devez envoyer un jeu de paramètres différent à Target pour différentes sections de votre site web. Créez une structure pour chaque jeu de paramètres que vous avez besoin d’envoyer. Associez chaque section de votre site web à la structure appropriée. Notez qu’une page web peut utiliser uniquement une structure à la fois.

1. Sur la page de configuration Target, cliquez sur le signe **+** en regard des configurations disponibles.

1. Dans la boîte de dialogue Créer une structure, spécifiez un **titre**, sélectionnez la **structure Adobe Target** et cliquez sur **Créer**.

   <!-- ![config-target-framework-dialog](assets/config-target-framework-dialog.png) -->

   La page de structure s’ouvre. Le sidekick fournit des composants qui représentent les informations de [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md) que vous pouvez mettre en correspondance.

   <!-- ![Framework](assets/chlimage_1-162.png) -->

1. Faites glisser le composant ClientContext représentant les données que vous souhaitez utiliser pour mettre en correspondance avec la cible de dépôt. Vous pouvez également faire glisser le composant **Boutique ContextHub** vers la structure.

   >[!NOTE]
   >
   >Lors de la mise en correspondance, les paramètres sont transmis à un mbox via des chaînes simples. Vous ne pouvez pas mapper des tableaux à partir de ContextHub.

   Par exemple, pour utiliser les **données du profil** des visiteurs de votre site afin de contrôler votre campagne Target, faites glisser le composant **Données du profil** vers la page. Les variables de données de profil qui sont disponibles pour la mise en correspondance des paramètres Target s’affichent.

   <!-- ![Profile Data](assets/chlimage_1-163.png) -->

1. Sélectionnez les variables que vous souhaitez rendre visibles pour le système Adobe Target en cochant la case **Partager** dans les colonnes appropriées.

   <!-- ![Share](assets/chlimage_1-164.png) -->

   >[!NOTE]
   >
   >La synchronisation des paramètres ne fonctionne que dans un sens : d’AEM à Adobe Target.

La structure est créée. Pour répliquer le framework sur l’instance de publication, utilisez la méthode **Activation du framework** dans le sidekick.

<!--
### Associating Activities With the Target Cloud Configuration  {#associating-activities-with-the-target-cloud-configuration}

Associate your [AEM activities](/help/sites-cloud/authoring/personalization/activities.md) with your Target cloud configuration so that you can mirror the activities in [Adobe Target](https://experienceleague.adobe.com/docs/target/using/experiences/offers/manage-content.html?lang=fr).

>[!NOTE]
>
>What types of activities are available is determined by the following:
>
>* If the **xt_only** option is enabled on the Adobe Target tenant (clientcode) used on the AEM side to connect to Adobe Target, then you can create **only** XT activities in AEM.
>
>* If the **xt_only** options is **not** enabled on the Adobe Target tenant (clientcode), then you can create **both** XT and A/B activities in AEM.
>
>**Additional note:** **xt_only** options is a setting applied on a certain Target tenant (clientcode) and can only be modified directly in Adobe Target. You cannot enable or disable this option in AEM.
-->

<!--
### Associating the Target Framework With Your Site {#associating-the-target-framework-with-your-site}

After you create a Target framework in AEM, associate your web pages with the framework. The targeted components on the pages send the framework-defined data to Adobe Target for tracking. (See [Content Targeting](/help/sites-cloud/authoring/personalization/targeted-content.md).)

When you associate a page with the framework, the child pages inherit the association.

1. In the **Sites** console, navigate to the site that you want to configure.
1. Using either [quick actions](/help/sites-cloud/authoring/basic-handling.md#quick-actions) or [selection mode](/help/sites-cloud/authoring/basic-handling.md#selecting-resources), select **View Properties.**
1. Select the **Cloud Services** tab.
1. Select **Edit**.
1. Select **Add Configuration** under **Cloud Service Configurations** and select **Adobe Target**.

  ![Cloud Service Configuration](assets/chlimage_1-165.png)

1. Select the framework you want under **Configuration Reference**.

   >[!NOTE]
   >
   >Make sure that you select the specific **framework** that you created and not the Target cloud configuration under which it was created.

1. Select **Done**.
1. Activate the root page of the website to replicate it to the publish server. (See [How To Publish Pages](/help/sites-cloud/authoring/sites-console/publishing-pages.md).)

   >[!NOTE]
   >
   >If the framework you attached to the page was not activated yet, a wizard opens which lets you publish it as well.
-->

## Exportation d’un fragment d’expérience vers Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Pour les contenus multimédias, comme les images, une seule référence est exportée vers Target. La ressource elle-même reste stockée dans AEM Assets et est diffusée à partir de l’instance de publication AEM.
>
>En conséquence, le fragment d’expérience, avec toutes les ressources associées, doit être publié avant l’exportation vers Target.

Pour exporter un fragment d’expérience d’AEM vers Target (après avoir spécifié la configuration cloud) :

1. Accédez à la console Fragment d’expérience.
1. Sélectionnez le fragment d’expérience que vous souhaitez exporter vers Target.

   >[!NOTE]
   >
   >Il doit s’agir d’une variation web de fragment d’expérience.

1. Sélectionnez **Exporter vers Adobe Target**.

   >[!NOTE]
   >
   >Si le fragment d’expérience a déjà été exporté, sélectionnez **Mettre à jour dans Adobe Target**.

1. Sélectionnez **Exporter sans publier** ou **Publish** selon les besoins.

   >[!NOTE]
   >
   >L’option **Publier** permet la publication immédiate du fragment d’expérience et l’envoie vers Target.

1. Sélectionnez **OK** dans la boîte de dialogue de confirmation.

   Votre fragment d’expérience se trouve désormais dans Target.

   >[!NOTE]
   >
   >[Divers détails](/help/sites-cloud/authoring/fragments/content-fragments.md#details-of-your-experience-fragment) sur l’exportation sont visibles dans la vue **Liste** de la console et dans les **Propriétés**.

   >[!NOTE]
   >
   >Lors de l’affichage d’un fragment d’expérience dans Adobe Target, la date de *dernière modification* affichée correspond à la date de la dernière modification du fragment dans AEM, et non à celle de la dernière exportation du fragment vers Adobe Target.

>[!NOTE]
>
>Vous pouvez également effectuer l’exportation à partir de l’éditeur de page à l’aide de commandes comparables dans le menu [Informations sur la page](/help/sites-cloud/authoring/page-editor/introduction.md#page-information).

## Utilisation de vos fragments d’expérience dans Adobe Target {#using-your-experience-fragments-in-adobe-target}

Après avoir effectué les tâches précédentes, le fragment d’expérience s’affiche sur la page Offres de Target. Voir [documentation spécifique de Target](https://experiencecloud.adobe.com/resources/help/fr_FR/target/target/aem-experience-fragments.html) pour en savoir plus sur ce qu’il est possible de faire.

>[!NOTE]
>
>Lors de l’affichage d’un fragment d’expérience dans Adobe Target, la date de *dernière modification* affichée correspond à la date de la dernière modification du fragment dans AEM, et non à celle de la dernière exportation du fragment vers Adobe Target.

## Suppression d’un fragment d’expérience déjà exporté vers Adobe Target {#deleting-an-experience-fragment-already-exported-to-adobe-target}

La suppression d’un fragment d’expérience qui a déjà été exporté vers Target peut entraîner des problèmes si le fragment est déjà utilisé pour une offre dans Target. La suppression du fragment rendrait l’offre inutilisable, car le fragment de contenu est fourni par AEM.

Pour éviter de telles situations :

* Si le fragment d’expérience n’est pas actuellement utilisé dans une activité, AEM permet à l’utilisateur ou à l’utilisatrice de le supprimer sans message d’avertissement.
* Si le fragment d’expérience est actuellement utilisé par une activité dans Target, un message d’erreur avertit l’utilisateur ou l’utilisatrice AEM des conséquences possibles de la suppression du fragment sur l’activité.

  Le message d’erreur apparu dans AEM n’empêche pas à l’utilisateur de forcer la suppression du fragment d’expérience. Lorsque le fragment d’expérience est supprimé :

   * l’offre Target qui utilise le fragment d’expérience AEM peut souffrir d’un comportement indésirable ;

      * l’offre effectue toujours le rendu, car le code HTML du fragment d’expérience a été transmis à Target ;
      * les références du fragment d’expérience peuvent ne pas fonctionner correctement si les ressources référencées ont également été supprimées dans AEM.

   * Bien sûr, toute modification supplémentaire apportée au fragment d’expérience est impossible, car le fragment d’expérience n’existe plus dans AEM.

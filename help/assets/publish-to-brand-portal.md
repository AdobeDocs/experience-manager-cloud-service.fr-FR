---
title: Publication de ressources, de dossiers et de collections sur Brand Portal
description: Publiez des ressources, des dossiers et des collections sur Brand Portal.
contentOwner: Vishabh Gupta
translation-type: ht
source-git-commit: 4677a8771c5891b8c9846e0adb58025304a71bdd

---


# Publication de ressources sur Brand Portal {#publish-assets-to-brand-portal}

En tant qu’administrateur d’Adobe Experience Manager (AEM) Assets, vous pouvez publier des ressources, des dossiers et des collections sur l’instance AEM Assets Brand Portal. Vous pouvez également planifier le workflow de publication d’une ressource ou d’un dossier à une date ou une heure ultérieure. Une fois ces éléments publiés, les utilisateurs de Brand Portal peuvent accéder aux ressources, aux dossiers et aux collections et les distribuer à d’autres utilisateurs.

Cependant, vous devez d’abord configurer AEM Assets avec Brand Portal. Pour plus de détails, voir [Configuration d’AEM Assets avec Brand Portal](configure-aem-assets-with-brand-portal.md).

Si vous apportez des modifications ultérieures à la ressource, au dossier ou à la collection d’origine dans AEM Assets, les changements ne sont reflétés dans Brand Portal que lorsque vous republiez l’élément modifié depuis AEM Assets. Cette fonction assure que les modifications en cours ne sont pas disponibles dans Brand Portal. Seules les modifications approuvées publiées par un administrateur sont disponibles dans Brand Portal.

* [Publication de ressources sur Brand Portal](#publish-assets-to-bp)
* [Publication de dossiers sur Brand Portal](#publish-folders-to-brand-portal)
* [Publication de collections sur Brand Portal](#publish-collections-to-brand-portal)

>[!NOTE]
>
>Adobe recommande la publication décalée, de préférence en dehors des heures de pointe, de sorte que l’auteur AEM n’utilise pas une quantité excessive de ressources.


## Publication de ressources sur Brand Portal {#publish-assets-to-bp}

Vous trouverez ci-dessous les étapes de publication de ressources d’AEM Assets vers Brand Portal :

1. Dans la console Assets, ouvrez le dossier parent et sélectionnez toutes les ressources à publier, puis cliquez sur l’option **[!UICONTROL Publication rapide]** dans la barre d’outils.

   ![publish2bp-2](assets/publish2bp.png)

1. Vous trouverez ci-dessous les deux méthodes de publication de ressources :
   * [Publier maintenant](#publish-to-bp-now) (publier les ressources immédiatement)
   * [Publier ultérieurement](#publish-to-bp-later) (planifier la publication des ressources)

### Publication immédiate des ressources {#publish-to-bp-now}

Pour publier les ressources sélectionnées sur Brand Portal, effectuez l’une des opérations suivantes :

* Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Cliquez ensuite sur **[!UICONTROL Publier sur Brand Portal]** dans le menu.

* Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

   1. Dans **[!UICONTROL Action]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]**.

      Dans **[!UICONTROL Planification]**, sélectionnez **[!UICONTROL Maintenant]**.

      Cliquez sur **[!UICONTROL Suivant]**.

   2. Confirmez votre sélection dans **[!UICONTROL Portée]** et cliquez sur **[!UICONTROL Publier sur Brand Portal]**.

Un message indique que les ressources ont été placées en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir les ressources publiées.

### Publication ultérieure des ressources {#publish-to-bp-later}

Pour planifier la publication des ressources sur Brand Portal à une date ou une heure ultérieure :

1. Sélectionnez les ressources dont vous souhaitez planifier la publication, puis cliquez sur **[!UICONTROL Gérer la publication]** dans la barre d’outils située en haut.

1. Sur la page **[!UICONTROL Gérer la publication]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]** dans **[!UICONTROL Action]**.

   Sélectionnez **[!UICONTROL Plus tard]** dans **[!UICONTROL Planification]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

1. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Cliquez sur **[!UICONTROL Suivant]**.

1. Sélectionnez une **Date d’activation** et spécifiez l’heure. Cliquez sur **Suivant**.

1. Spécifiez un **[!UICONTROL Titre de workflow]** sous **[!UICONTROL Processus]**. Cliquez sur **[!UICONTROL Publier ultérieurement]**.

   ![publishworkflow](assets/publishworkflow.png)

Connectez-vous à l’interface Brand Portal pour afficher les ressources publiées (selon la date ou l’heure planifiée).

![bp_landing_page](assets/bp_landing_page.png)


## Publication de dossiers sur Brand Portal {#publish-folders-to-brand-portal}

Vous pouvez publier ou annuler la publication de dossiers de ressources immédiatement ou en planifier la publication à une date ou une heure ultérieure.

### Publication de dossiers sur Brand Portal {#publish-folders-to-bp}

1. Dans la console Assets, sélectionnez les dossiers à publier, puis cliquez sur **[!UICONTROL Publication rapide]** dans la barre d’outils.

   ![publish2bp](assets/publish2bp.png)

1. **Publication instantanée des dossiers**

   Pour publier les dossiers sélectionnés sur Brand Portal, effectuez l’une des opérations suivantes :

   * Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**.

      Dans le menu, sélectionnez **[!UICONTROL Publier sur Brand Portal]**.

   * Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

      1. Dans **[!UICONTROL Action]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]**.

         Dans **[!UICONTROL Planification]**, sélectionnez **[!UICONTROL Maintenant]**.

         Cliquez sur **Suivant.**

      1. Confirmez votre sélection dans **[!UICONTROL Portée]** et cliquez sur **[!UICONTROL Publier sur Brand Portal]**.
   Un message indique que le dossier a été placé en file d’attente pour publication sur Brand Portal. Connectez-vous à l’interface Brand Portal pour voir le dossier publié.

1. **Publication ultérieure de dossiers**

   Pour planifier la publication des dossiers de ressources à une date ou une heure ultérieure :

   1. Sélectionnez les dossiers dont vous souhaitez planifier la publication, puis cliquez sur **[!UICONTROL Gérer la publication]** dans la barre d’outils située en haut.
   1. Dans **[!UICONTROL Action]**, sélectionnez **[!UICONTROL Publier sur Brand Portal]**.

      Dans **[!UICONTROL Planification]**, sélectionnez **[!UICONTROL Plus tard]**.

   1. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Cliquez sur **[!UICONTROL Suivant]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   1. Confirmez votre sélection dans **[!UICONTROL Portée]**. Cliquez sur **[!UICONTROL Suivant]**.

   1. Spécifiez un titre de workflow sous **[!UICONTROL Processus]**. Cliquez sur **[!UICONTROL Publier ultérieurement]**.

      ![manageschedulepub](assets/manageschedulepub.png)

### Annulation de la publication de dossiers sur Brand Portal {#unpublish-folders-from-brand-portal}

Vous pouvez supprimer n’importe quel dossier de ressources publié sur Brand Portal en en annulant la publication à partir de l’instance d’AEM Assets. Une fois que vous avez annulé la publication du dossier original, sa copie n’est plus disponible pour les utilisateurs de Brand Portal.

Vous pouvez annuler immédiatement la publication de dossiers de ressources depuis Brand Portal ou en programmer la publication à une date et une heure ultérieures.

Pour annuler la publication de dossiers de ressources sur Brand Portal :

1. Dans la console Assets, sélectionnez les dossiers de ressources dont vous souhaitez annuler la publication, puis cliquez sur **[!UICONTROL Gérer la publication]** dans la barre d’outils.

   ![publish2bp-1](assets/publish2bp.png)

1. **Annulation immédiate de la publication des dossiers de ressources**

   Pour annuler immédiatement la publication du dossier de ressources sélectionné sur Brand Portal :

   1. Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

   1. Dans **[!UICONTROL Action]**, sélectionnez **[!UICONTROL Annuler la publication sur Brand Portal]**.

      Dans **[!UICONTROL Planification]**, sélectionnez **[!UICONTROL Maintenant]**.

      Cliquez sur **[!UICONTROL Suivant]**.

   1. Confirmez votre sélection dans **[!UICONTROL Portée]** et cliquez sur **[!UICONTROL Annuler la publication sur Brand Portal]**.

      ![confirm-unpublish](assets/confirm-unpublish.png)

1. **Annulation ultérieure de la publication des dossiers de ressources**

   Pour planifier l’annulation de la publication d’un dossier de ressources à une date et une heure ultérieures :

   1. Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**.

   1. Dans **[!UICONTROL Action]**, sélectionnez **[!UICONTROL Annuler la publication dans Brand Portal]**.

      Dans **[!UICONTROL Planification]**, sélectionnez **[!UICONTROL Plus tard]**.

   1. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez l’heure. Cliquez sur **[!UICONTROL Suivant]**.

   1. Confirmez votre sélection dans **[!UICONTROL Portée]** et cliquez sur **[!UICONTROL Suivant]**.

   1. Spécifiez un **[!UICONTROL Titre de workflow]** sous **[!UICONTROL Processus]**. Cliquez sur **[!UICONTROL Annuler la publication ultérieurement]**.

      ![unpublishworkflows](assets/unpublishworkflows.png)

## Publication de collections sur Brand Portal {#publish-collections-to-brand-portal}

Vous pouvez publier des collections ou en annuler la publication à partir de votre instance cloud AEM Assets.

>[!NOTE]
>
>Les fragments de contenu ne peuvent pas être publiés sur Brand Portal. Par conséquent, si vous sélectionnez un ou plusieurs fragments de contenu dans Assets AEM, l’action **[!UICONTROL Publier sur Brand Portal]** n’est pas disponible.
>
>Si des collections contenant des fragments de contenu sont publiées sur Brand Portal à partir d’AEM Assets, alors tout le contenu du dossier, à l’exception des fragments de contenu, est répliqué sur l’interface Brand Portal.


### Publication de collections {#publish-collections}

Vous trouverez ci-dessous les étapes de publication de collections d’AEM Assets vers Brand Portal :

1. Dans l’interface utilisateur AEM Assets, cliquez sur le logo AEM.

1. Dans la console **Navigation**, accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Collections]**.

1. Dans la console **Collections**, sélectionnez les collections que vous souhaitez publier dans Brand Portal.

   ![select_collection](assets/select_collection.png)

1. Dans la barre d’outils, cliquez sur **[!UICONTROL Publier sur Brand Portal]**.

1. Dans la boîte de dialogue de confirmation, cliquez sur **[!UICONTROL Publier]**.

1. Fermez le message de confirmation.

   Connectez-vous à Brand Portal en tant qu’administrateur. La collection publiée est disponible dans la console Collections.

   ![collection publiée](assets/published_collection.png)

### Annulation de la publication de collections {#unpublish-collections}

Vous pouvez supprimer n’importe quelle collection publiée sur Brand Portal en en annulant la publication à partir de l’instance d’AEM Assets. Une fois la publication de la collection d’origine annulée, sa copie n’est plus disponible pour les utilisateurs de Brand Portal.

Vous trouverez ci-dessous les étapes d’annulation de la publication d’une collection :

1. Dans la console **Collections** de votre instance AEM Assets, sélectionnez la collection dont vous souhaitez annuler la publication.

   ![select_collection](assets/select_collection-1.png)

1. Dans la barre d’outils, cliquez sur l’icône **[!UICONTROL Supprimer de Brand Portal]**.
1. Dans la boîte de dialogue, cliquez sur **[!UICONTROL Annuler la publication]**.
1. Fermez le message de confirmation. La collection est supprimée de l’interface de Brand Portal.

Outre ce qui précède, vous pouvez également publier des schémas de métadonnées, des paramètres d’image prédéfinis, des facettes de recherche et des balises d’AEM Assets sur Brand Portal.

* [Publication de paramètres prédéfinis, de schémas et de facettes sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publication de balises sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


Pour plus d’informations, voir [Publication de balises sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/home.html).


<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

---
title: Utilisation de la publication sélective dans Dynamic Media
description: Découvrez comment utiliser la publication sélective dans Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User
exl-id: a5a2df68-be13-45a6-ad80-09fbd2fea8f2
source-git-commit: a11529886d4b158c19a97ccbcb7d004cf814178d
workflow-type: tm+mt
source-wordcount: '2946'
ht-degree: 77%

---

# Configuration de la publication sélective au niveau du dossier dans Dynamic Media {#selective-publish-configure-folder}

Vous pouvez choisir de publier ou d’annuler la publication de ressources dans Adobe Experience Manager ou Dynamic Media. Pour ce faire, utilisez **[!UICONTROL Gérer la publication]** ou **[!UICONTROL Publication rapide]**. Cette méthode de publication est utile car elle ne dépend pas uniquement de la **[!UICONTROL configuration Dynamic Media]** dont les paramètres sont globaux pour tous les dossiers de votre instance Dynamic Media.

Par exemple, avec la publication sélective, vous pouvez travailler sur des ressources pour des produits qui ne sont pas encore en ligne. Dans ce cas, une équipe marketing peut accéder à des images de recadrage intelligent et à des rendus dynamiques synchronisés dans Dynamic Media afin de pouvoir créer du matériel promotionnel, le tout sans avoir à publier ces ressources dans Dynamic Media pour une diffusion globale.

<!-- 
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>La *copie* de ressources vers et depuis des dossiers efface l’état de publication de ces ressources. Cependant, lorsque vous *déplacez* des ressources vers et depuis des dossiers dont la propriété de dossier est définie sur **[!UICONTROL Publication sélective]**, l’état de publication de ces ressources est conservé.

Si vous décidez ultérieurement de modifier les paramètres **[!UICONTROL Publication sélective]** dans un dossier, ces modifications n’affectent que les nouvelles ressources que vous chargez vers ce dossier à partir de ce moment. L’état de publication des ressources existantes dans le dossier reste tel quel jusqu’à ce que vous modifiiez manuellement ces ressources à partir de la boîte de dialogue **[!UICONTROL Publication rapide]** ou **[!UICONTROL Gérer la publication]**.

L’option **[!UICONTROL Mode de publication Dynamic Media]** de niveau dossier utilise toujours par défaut la valeur du paramètre **[!UICONTROL Publier les ressources]** de votre **[!UICONTROL configuration de Dynamic Media]**. Les étapes suivantes de cette rubrique vous montrent toutefois comment modifier manuellement cette valeur par défaut au niveau du dossier (comme décrit dans les étapes suivantes) pour remplacer la valeur **[!UICONTROL Configuration de Dynamic Media]**.

Que vous utilisiez ou non :

* la valeur **[!UICONTROL Publier les ressources]** définie dans **[!UICONTROL Configuration Dynamic Media]** ;
* ou la valeur **[!UICONTROL Mode de publication Dynamic Media]** définie dans les propriétés de niveau dossier ;

vous pouvez toujours choisir **[!UICONTROL Immédiatement]**, **[!UICONTROL Lors de l’activation]** ou **[!UICONTROL Publication sélective]**. Par exemple, vous pouvez définir la valeur **[!UICONTROL Publier les ressources]** dans votre **[!UICONTROL Configuration Dynamic Media]** sur **[!UICONTROL Lors de l’activation]**. De plus, vous pouvez définir la valeur de mode de **[!UICONTROL Publication Dynamic Media]** au niveau du dossier sur **[!UICONTROL Publication sélective]**, à l’inverse, et ainsi de suite.

Après avoir configuré la publication sélective dans un dossier, vous pouvez effectuer l’une des opérations suivantes :

* [Publier sélectivement des ressources dans Dynamic Media ou Experience Manager à l’aide de la fonction Gérer la publication](#selective-publish-manage-publication).
* [Annuler sélectivement la publication de ressources dans Dynamic Media ou Experience Manager à l’aide de la fonction Gérer la publication](#selective-unpublish-manage-publication).
* [Publiez des ressources dans Dynamic Media ou Experience Manager à l’aide de la publication rapide](#quick-publish-aem-dm).
* [Publier des ressources ou en annuler la publication de manière sélective au moyen des résultats de recherche](#selective-publish-unpublish-search-results).

**Pour configurer la publication sélective au niveau du dossier dans Dynamic Media :**

1. Dans Experience Manager, sélectionnez le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche, sélectionnez l’icône Navigation (juste au-dessus de l’icône Outils), puis accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Utilisez l’une des méthodes suivantes :
   * Modifiez les propriétés d’un dossier existant. Dans **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, accédez à un dossier dont vous souhaitez modifier les propriétés. Sélectionnez le dossier puis, sur la barre d’outils, sélectionnez **[!UICONTROL Propriétés]**.
   * Modifiez les propriétés d’un nouveau dossier : en **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, près du coin supérieur droit de la page, accédez à **[!UICONTROL Créer]** > **[!UICONTROL Dossier]**. Dans la boîte de dialogue **[!UICONTROL Créer un dossier]**, saisissez un titre (obligatoire) pour le dossier, puis sélectionnez **[!UICONTROL Créer]**. Sélectionnez le dossier puis, sur la barre d’outils, sélectionnez **[!UICONTROL Propriétés]**.

1. Dans la liste déroulante **[!UICONTROL Mode de synchronisation]**, sélectionnez l’une des options suivantes :

   | Mode de synchronisation | Description |
   | --- | --- |
   | **[!UICONTROL Hérité]** | Aucune valeur de synchronisation explicite sur le dossier ; au lieu de cela, le dossier hérite de la valeur de synchronisation de l’un de ses dossiers ancêtres ou du mode par défaut défini dans votre **[!UICONTROL Configuration de Dynamic Media]**. Le statut détaillé de l’**[!UICONTROL héritage]** s’affiche par le biais d’une info-bulle. |
   | **[!UICONTROL Synchroniser avec Dynamic Media tous les éléments de cette sous-arborescence de dossier]** | Pour que la publication dans Dynamic Media réussisse, les ressources doivent être synchronisées dans Dynamic Media. La sélection de cette option inclue toutes les ressources de cette sous-arborescence pour la synchronisation dans Dynamic Media. Les paramètres propres au dossier remplacent le paramètre par défaut dans la **[!UICONTROL Configuration de Dynamic Media]**. |
   | **[!UICONTROL Exclure de la synchronisation Dynamic Media tout le contenu de cette sous-arborescence de dossier]** | Excluez de la synchronisation dans Dynamic Media toutes les ressources de cette sous-arborescence. |

   ![Publication sélective au niveau du dossier](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Dans la liste déroulante **[!UICONTROL Mode de publication Dynamic Media]**, sélectionnez une option. L’option **[!UICONTROL Mode de publication Dynamic Media]** utilise toujours par défaut la valeur définie dans la **[!UICONTROL Configuration de Dynamic Media]**. Vous pouvez toutefois remplacer manuellement cette valeur **[!UICONTROL Configuration de Dynamic Media]** par défaut à l’aide de l’une des options suivantes.

   >[!IMPORTANT]
   >
   >Quelle que soit l’option Mode de publication Dynamic Media sélectionnée, les mises à jour apportées ultérieurement à une ressource *déjà* publiée sont immédiatement publiées sans autre action de l’utilisateur.

   | Option Mode de publication de média dynamique | Description |
   | --- | --- |
   | **[!UICONTROL Immédiatement]** | Lorsque des ressources sont chargées dans ce dossier, le système les ingère dans Experience Manager et fournit instantanément le lien d’URL/d’incorporation. Cette option est uniquement liée à la publication Experience Manager et aucune intervention de l’utilisateur n’est nécessaire pour publier des ressources.<br>Cette option n’est *pas* disponible si vous avez sélectionné **[!UICONTROL Exclure de la synchronisation Dynamic Media tout le contenu de cette sous-arborescence de dossier]** dans **[!UICONTROL Mode de synchronisation]** à l’étape précédente. |
   | **[!UICONTROL Lors de l’activation]** | Lorsque des ressources sont chargées dans ce dossier, vous devez d’abord les publier explicitement avant de fournir un lien d’URL/d’incorporation. Cette option est uniquement liée à la publication Experience Manager.<br>Cette option n’est *pas* disponible si vous avez sélectionné **[!UICONTROL Exclure de la synchronisation Dynamic Media tout le contenu de cette sous-arborescence de dossier]** dans **[!UICONTROL Mode de synchronisation]** à l’étape précédente. |
   | **[!UICONTROL Publication sélective]** | Les ressources sont publiées, au choix, dans Experience Manager ou Dynamic Media, pour diffusion dans le domaine public. Les deux méthodes de publication s’excluent mutuellement. En d’autres termes, vous pouvez publier des ressources dans DMS7 afin d’utiliser des fonctionnalités telles que le recadrage intelligent ou les rendus dynamiques. Vous pouvez également publier des ressources exclusivement dans Experience Manager pour un aperçu sécurisé ; ces mêmes ressources ne sont *pas* publiées dans DMS7 pour diffusion dans le domaine public. Cette option n’est pas disponible si vous avez sélectionné **[!UICONTROL Exclure de la synchronisation Dynamic Media tout le contenu de cette sous-arborescence de dossier]** dans **[!UICONTROL Mode de synchronisation]** à l’étape précédente. |

1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer et fermer]**, puis sélectionnez **[!UICONTROL OK]** pour revenir aux ressources du Experience Manager.

## Publier sélectivement des ressources dans Dynamic Media ou Experience Manager as a Cloud Service à l’aide de la fonction Gérer la publication{#selective-publish-manage-publication}

Avant de pouvoir utiliser **[!UICONTROL Gérer la publication]** pour publier sélectivement des ressources dans Dynamic Media ou Experience Manager, assurez-vous d’avoir effectué l’une des opérations suivantes :

* Définissez l’option **[!UICONTROL Publier les ressources]** dans **[!UICONTROL Configuration Dynamic Media]** sur **[!UICONTROL Publication sélective]**.
* Vous pouvez également configurer la publication sélective au niveau des dossiers.

Voir [Création d’une configuration Dynamic Media](#configuring-dynamic-media-cloud-services) ou [Configuration de la publication sélective au niveau du dossier dans Dynamic Media](#selective-publish-configure-folder)

<!--
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>La *copie* de ressources vers et depuis des dossiers efface l’état de publication de ces ressources. Cependant, lorsque vous *déplacez* des ressources vers et depuis des dossiers dont la propriété de dossier est définie sur **[!UICONTROL Publication sélective]**, l’état de publication de ces ressources est conservé.

**Pour publier sélectivement des ressources dans Dynamic Media ou Experience Manager as a Cloud Service à l’aide de la fonction Gérer la publication :**

1. Dans Experience Manager, sélectionnez le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche, sélectionnez l’icône Navigation (juste au-dessus de l’icône Outils), puis accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, effectuez l’une des opérations suivantes :
   * Accédez à un dossier dont vous souhaitez publier les ressources. Sélectionnez le dossier puis, sur la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**. Utilisez le **[!UICONTROL Mode Liste]** pour vérifier plus facilement l’état de publication d’un dossier en particulier.
   * Accédez à un dossier dont vous souhaitez publier les ressources. Ouvrez le dossier, puis sélectionnez une ou plusieurs ressources. Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**. Utilisez le **[!UICONTROL Mode Liste]** pour vérifier plus facilement l’état de publication d’une ressource en particulier.

      >[!NOTE]
      >
      >Si **[!UICONTROL Gérer la publication]** n’est pas visible dans la barre d’outils, sélectionnez le bouton avec les points de suspension à la place, puis sélectionnez **[!UICONTROL Gérer la publication]** dans le menu de liste.

1. Sur la page **[!UICONTROL Gérer la publication – Options]**, sous **[!UICONTROL Action]**, sélectionnez le type d’activation souhaité.

   | Action | Description |
   | --- | --- |
   | **[!UICONTROL Publier]** (vers Experience Manager) | Pour publier des ressources dans Experience Manager pour un aperçu sécurisé, sélectionnez cette option. |
   | **[!UICONTROL Publier vers Dynamic Media]** | Pour publier des ressources dans Dynamic Media pour diffusion dans le domaine public ou pour pouvoir utiliser des fonctionnalités telles que le recadrage intelligent ou les rendus dynamiques, sélectionnez cette option.<br>Cette option n’est disponible que si l’option **[!UICONTROL Mode de publication Dynamic Media]** est définie sur **[!UICONTROL Publication sélective]** dans les propriétés du dossier. |

1. Sous **[!UICONTROL Planification]**, définissez le calendrier de publication.

   | Planification | Description |
   | --- | --- |
   | **[!UICONTROL Maintenant]** | Sélectionnez cette option pour publier immédiatement les ressources. |
   | **[!UICONTROL Plus tard]** | Sélectionnez cette option pour publier les ressources à une date et une heure spécifiques. |

1. Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication]** , sélectionnez **[!UICONTROL Suivant]**.
1. Sur la page **[!UICONTROL Gestion de la publication – Portée]**, effectuez l’une des opérations suivantes :
   * Si nécessaire, sélectionnez une ou plusieurs ressources à supprimer de la publication.
   * Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication - Portée]** , sélectionnez **[!UICONTROL Publier]** ou **[!UICONTROL Publier sur Dynamic Media]**.
1. **[!UICONTROL Cliquez sur OK]**.

### Annuler sélectivement la publication de ressources dans Dynamic Media ou Experience Manager à l’aide de la fonction Gérer la publication. {#selective-unpublish-manage-publication}

1. Dans Experience Manager, sélectionnez le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche, sélectionnez l’icône Navigation (juste au-dessus de l’icône Outils), puis accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, effectuez l’une des opérations suivantes :
   * Accédez à un dossier dont vous souhaitez annuler la publication des ressources. Sélectionnez le dossier puis, sur la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**. Utilisez le **[!UICONTROL Mode Liste]** pour vérifier plus facilement l’état de publication d’un dossier en particulier.
   * Accédez à un dossier dont vous souhaitez annuler la publication des ressources. Ouvrez le dossier, puis sélectionnez une ou plusieurs ressources. Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**. Utilisez le **[!UICONTROL Mode Liste]** pour vérifier plus facilement l’état de publication d’une ressource en particulier.

      >[!NOTE]
      >
      >Si **[!UICONTROL Gérer la publication]** n’est pas visible dans la barre d’outils, sélectionnez le bouton avec les points de suspension à la place, puis sélectionnez **[!UICONTROL Gérer la publication]** dans le menu de liste.

1. Sur la page **[!UICONTROL Gérer la publication – Options]**, sous **[!UICONTROL Action]**, sélectionnez le type de désactivation souhaité.

   | Action | Description |
   | --- | --- |
   | **[!UICONTROL Annuler la publication]** (à partir de Experience Manager) | Pour annuler la publication de ressources sur Experience Manager, sélectionnez cette option. |
   | **[!UICONTROL Annuler la publication à partir de Dynamic Media]** | Pour annuler la publication de ressources à partir de Dynamic Media, sélectionnez cette option.<br>Cette option n’est disponible que si l’option **[!UICONTROL Mode de publication Dynamic Media]** est définie sur **[!UICONTROL Publication sélective]** dans les propriétés du dossier. |

1. Sous **[!UICONTROL Planning]**, définissez le calendrier de la désactivation.

   | Planification | Description |
   | --- | --- |
   | **[!UICONTROL Maintenant]** | Sélectionnez cette option pour annuler immédiatement la publication des ressources. |
   | **[!UICONTROL Plus tard]** | Sélectionnez cette option pour annuler la publication des ressources à une date et une heure spécifiques. |

1. Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication]** , sélectionnez **[!UICONTROL Suivant]**.
1. Sur la page **[!UICONTROL Gestion de la publication – Portée]**, effectuez l’une des opérations suivantes :
   * Sélectionnez une ou plusieurs ressources à supprimer de l’annulation de publication.
   * Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication - Portée]** , sélectionnez **[!UICONTROL Annuler la publication]** ou **[!UICONTROL Annuler la publication à partir de Dynamic Media]**.
1. **[!UICONTROL Cliquez sur OK]**.

## Publication de ressources dans Dynamic Media ou Experience Manager à l’aide de la publication rapide {#quick-publish-aem-dm}

Vous pouvez utiliser la fonction **[!UICONTROL Publication rapide]** dans les cas d’activation de ressources simples. La fonction **[!UICONTROL Publication rapide]** publie immédiatement les ressources sélectionnées sans autre interaction de l’utilisateur. Toutes les références non publiées sont également publiées automatiquement.

>[!NOTE]
>
>Pour utiliser la **[!UICONTROL publication rapide]** afin de publier des ressources dans Dynamic Media ou Experience Manager, assurez-vous que la fonction **[!UICONTROL Publication sélective]** est activée dans votre **[!UICONTROL Configuration de Dynamic Media]** ou dans les propriétés de dossier du dossier sélectionné.

**Pour publier des ressources dans Dynamic Media ou Experience Manager à l’aide de la publication rapide:**

1. Dans Experience Manager, sélectionnez le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche de la page, sélectionnez l’icône Navigation (juste au-dessus de l’icône Outils), puis, sur le côté droit de la page, accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, effectuez l’une des opérations suivantes :
   * Accédez à un dossier dont vous souhaitez publier les ressources. Sélectionnez le dossier puis, sur la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Utilisez le **[!UICONTROL Mode Liste]** pour vérifier plus facilement l’état de publication d’un dossier en particulier.
   * Accédez à un dossier dont vous souhaitez publier les ressources. Ouvrez le dossier, puis sélectionnez une ou plusieurs ressources. Dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**. Utilisez le **[!UICONTROL Mode Liste]** pour vérifier plus facilement l’état de publication d’une ressource en particulier.

      >[!NOTE]
      >
      >Si **[!UICONTROL Publication rapide]** n’est pas visible dans la barre d’outils, sélectionnez le bouton avec les points de suspension à la place, puis sélectionnez **[!UICONTROL Publication rapide]** dans le menu de liste.

      ![Publication rapide au niveau du dossier dans Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Sélectionnez l’une des options suivantes dans la liste de menu **[!UICONTROL Publication rapide]**.

   | Option Publication rapide | Effets |
   | --- | --- | 
   | Publier dans Experience Manager | Publie immédiatement les ressources sélectionnées dans Experience Manager. |
   | Publier sur Brand Portal | Publie immédiatement les ressources sélectionnées dans **[!UICONTROL Brand Portal]**.<br>Cette option n’est disponible que si votre instance Experience Manager Assets dispose déjà de **[!UICONTROL Brand Portal]** configuré. |
   | Publier vers Dynamic Media | Publie immédiatement les ressources sélectionnées dans Dynamic Media.<br>Une ressource doit déjà être synchronisée dans Dynamic Media. Si nécessaire, assurez-vous que le **[!UICONTROL mode de synchronisation]** dans les propriétés d’un dossier est déjà défini sur **[!UICONTROL Synchroniser avec Dynamic Media tout le contenu de cette sous-arborescence de dossier]**. |

1. Sélectionnez **[!UICONTROL OK]**, puis **[!UICONTROL Fermer]**.

## Publier des ressources ou en annuler la publication de manière sélective au moyen des résultats de recherche {#selective-publish-unpublish-search-results}

Les résultats de recherche peuvent afficher des ressources provenant de dossiers de ressources dont les paramètres de publication de Dynamic Media diffèrent. Lorsque vous avez sélectionné une ou plusieurs ressources à partir des résultats de la recherche et que les ressources comportent des paramètres de mode de publication Dynamic Media différents, vous pouvez déclencher la fonction **[!UICONTROL Gérer la publication]** à partir de la barre d’outils afin de publier ou d’annuler la publication.

Consultez également [Recherche de ressources dans Experience Manager](/help/assets/search-assets.md).

**Pour publier des ressources ou en annuler la publication de manière sélective au moyen des résultats de recherche :**

1. Dans Experience Manager, dans le coin supérieur gauche de la page, sélectionnez le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche de la page, sélectionnez l’icône Navigation (juste au-dessus de l’icône Outils), puis accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Dans la barre d’outils, près du coin supérieur droit de la page, sélectionnez l’icône Rechercher (loupe).
1. Dans le champ **[!UICONTROL Texte à rechercher]**, entrez un mot-clé, puis appuyez sur **[!UICONTROL Entrée]**.
1. Dans le coin supérieur droit de la page, sélectionnez l’icône **[!UICONTROL Mode Liste]** .
1. Dans le coin supérieur gauche de la page, sélectionnez l’icône **[!UICONTROL Filtres]** .

   ![Mode Liste et Filtres dans les résultats de recherche](/help/assets/assets-dm/select-publish-search-result.png)

1. Dans le panneau de gauche, développez **[!UICONTROL Statut]**, puis développez le prédicat de recherche **[!UICONTROL Dynamic Media]**.
1. Utilisez les cases à cocher **[!UICONTROL Publiée]** et **[!UICONTROL Publication annulée]** pour affiner davantage les résultats de recherche en fonction de l’état de publication des ressources Dynamic Media.
Vous pouvez éventuellement utiliser ces cases à cocher avec le prédicat de recherche **[!UICONTROL Publier]** pour affiner les résultats de recherche des ressources Experience Manager dont le statut est **[!UICONTROL Publiée]** et **[!UICONTROL Publication annulée]**.
1. Utilisez l’une des méthodes suivantes :
   * Sélectionnez une ou plusieurs ressources que vous souhaitez publier ou dont vous souhaitez annuler la publication.
   * Près du coin supérieur droit de la page **[!UICONTROL Résultats de la recherche]**, sélectionnez **[!UICONTROL Tout sélectionner]**.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Gérer la publication]**. Si nécessaire, sélectionnez l’icône représentant des points de suspension dans la barre d’outils pour afficher **[!UICONTROL Gérer la publication]**.
1. Sur la page **[!UICONTROL Gérer la publication – Options]**, sélectionnez l’action de votre choix.

   | Action sélectionnée | Paramètre Publier les ressources dans la configuration de Dynamic Media | Les ressources sont |
   | --- | --- | --- |
   | Publier | Immédiatement ou Lors de l’activation | Publié dans Experience Manager et Dynamic Media. |
   | Publier | Publication sélective | Publié dans Experience Manager uniquement. |
   | Annuler la publication | Immédiatement ou Lors de l’activation | Publication annulée à partir d’Experience Manager et de Dynamic Media. |
   | Annuler la publication | Publication sélective | Publication annulée à partir d’Experience Manager uniquement. |
   | Publier vers Dynamic Media | Immédiatement ou Lors de l’activation | Non publiées dans Experience Manager, dans Dynamic Media ou dans les deux. |
   | Publier vers Dynamic Media | Publication sélective | Publiées sur Dynamic Media uniquement. |
   | Annuler la publication à partir de Dynamic Media | Immédiatement ou Lors de l’activation | Publication non annulée à partir d’Experience Manager, de Dynamic Media ou des deux. |
   | Annuler la publication à partir de Dynamic Media | Publication sélective | Publication annulée à partir de Dynamic Media uniquement. |

1. Sous **[!UICONTROL Planning]**, définissez le calendrier de la désactivation.

   | Planification sélectionnée | Ce qui se produit |
   | --- | --- |
   | Maintenant | L’action sélectionnée est exécutée immédiatement. |
   | Plus tard | L’action sélectionnée est exécutée à la date et à l’heure particulières sélectionnées. |

1. Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication - Options]** , sélectionnez **[!UICONTROL Suivant]**.
1. (Facultatif) Sur la page **[!UICONTROL Gestion de la publication – Portée]**, passez en revue la colonne **[!UICONTROL Cible de publication]** du tableau correspondant aux ressources sélectionnées.

   | Paramètre Publier les ressources dans la configuration de Dynamic Media | Action sélectionnée | Cible de publication |
   | --- | --- | --- |
   | Immédiatement ou <br>Lors de l’activation | Publier | Experience Manager et Dynamic Media |
   | Immédiatement ou <br>Lors de l’activation | Publier vers Dynamic Media | Aucune |
   | Publication sélective | Publier | Experience Manager |
   | Publication sélective | Publier vers Dynamic Media | Dynamic Media |
   | Immédiatement ou <br>Lors de l’activation | Annuler la publication | Experience Manager et Dynamic Media |
   | Immédiatement ou <br>Lors de l’activation | Annuler la publication à partir de Dynamic Media | Aucune |
   | Publication sélective | Annuler la publication | Experience Manager |
   | Publication sélective | Annuler la publication à partir de Dynamic Media | Dynamic Media |

1. Sur la page **[!UICONTROL Gestion de la publication – Portée]**, effectuez l’une des opérations suivantes :
   * Sélectionnez une ou plusieurs ressources à supprimer de la publication ou de l’annulation de la publication.
   * Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication - Portée]** , sélectionnez **[!UICONTROL Publier]** ou **[!UICONTROL Annuler la publication]** pour lancer l’action.
1. **[!UICONTROL Cliquez sur OK]**.

## Vérification de l’état de publication d’une ressource {#check-publish-status-of-asset}

Vous pouvez utiliser **[!UICONTROL Chronologie]** en **[!UICONTROL Mode Carte]**, en **[!UICONTROL Mode Colonnes]** ou en **[!UICONTROL Mode Liste]** dans Experience Manager afin de vérifier rapidement l’état de publication d’une ressource.

**Pour vérifier l’état de publication d’une ressource :**

1. Dans Experience Manager, dans le coin supérieur gauche de la page, sélectionnez le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche de la page, sélectionnez l’icône Navigation (juste au-dessus de l’icône Outils), puis accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]** (la capture d’écran ci-dessous présente le **[!UICONTROL Mode Liste]**), ouvrez un dossier contenant les ressources que vous avez publiées ou dont vous avez annulé la publication.
1. Sélectionnez une ressource pour qu’elle s’affiche avec une coche. Voir la capture d’écran ci-dessous, par exemple.
1. Dans le menu déroulant situé dans le coin supérieur gauche de la page, sélectionnez **[!UICONTROL Chronologie]**. La section **[!UICONTROL État]** du panneau de gauche affiche l’état de publication de la ressource sélectionnée.
Lorsque vous utilisez l’option **[!UICONTROL Mode Liste]**, une colonne supplémentaire pour l’état de publication de **[!UICONTROL Dynamic Media]** s’affiche.
   * Un dossier configuré pour la synchronisation avec Dynamic Media affiche la colonne **[!UICONTROL Dynamic Media]** par défaut.
   * Un dossier *non* configuré pour la synchronisation avec Dynamic Media n’affiche pas la colonne Dynamic Media.
      ![Mode Liste et Chronologie](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Résolution des problèmes de publication sélective {#selective-publish-troubleshoot}

Une ressource qui n’est pas synchronisée avec Dynamic Media mais au niveau de laquelle une action de publication de Dynamic Media est déclenchée se traduit par le message d’erreur suivant et sa solution :

![Erreur de publication sélective](/help/assets/assets-dm/selective-publish-error.png)

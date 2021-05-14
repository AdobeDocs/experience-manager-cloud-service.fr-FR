---
title: Utilisation de la publication sélective dans Dynamic Media
description: Découvrez comment utiliser la publication sélective dans Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: Business Practitioner
exl-id: a5a2df68-be13-45a6-ad80-09fbd2fea8f2
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '2939'
ht-degree: 54%

---

# Configuration de la publication sélective au niveau des dossiers dans Dynamic Media {#selective-publish-configure-folder}

Vous pouvez choisir de publier ou d’annuler la publication de fichiers vers Adobe Experience Manager ou Dynamic Media ou d’y accéder. Vous pouvez le faire au niveau du dossier, en utilisant **[!UICONTROL Gérer la publication]** ou **[!UICONTROL Publication rapide]**. Cette méthode de publication est utile car elle ne repose pas uniquement sur la **[!UICONTROL Configuration Dynamic Media]** dont les paramètres sont globaux pour tous les dossiers de votre instance Dynamic Media.

Par exemple, avec la publication sélective, vous pouvez travailler sur des ressources pour des produits qui ne sont pas encore en ligne. Dans ce cas, une équipe marketing peut accéder aux images de recadrage intelligent et aux rendus dynamiques synchronisés sur Dynamic Media. Ils peuvent créer des supports promotionnels, le tout sans avoir à publier ces ressources sur Dynamic Media pour une diffusion mondiale.

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

Que vous comptiez sur :

* La valeur **[!UICONTROL Publier les ressources]** définie dans **[!UICONTROL Configuration de Dynamic Media]**
* Ou, la valeur **[!UICONTROL Mode de publication Dynamic Media]** définie dans les propriétés au niveau du dossier

Vous pouvez toujours choisir **[!UICONTROL Immédiatement]**, **[!UICONTROL À l’Activation]** ou **[!UICONTROL Publication sélective]**. Par exemple, vous pouvez définir la valeur **[!UICONTROL Publier les ressources]** de votre **[!UICONTROL Configuration de Dynamic Media]** sur **[!UICONTROL À l’Activation]**. De plus, vous pouvez définir la valeur du mode **[!UICONTROL Publication Dynamic Media]** au niveau du dossier sur **[!UICONTROL Publication sélective]**, inversement, etc.

Après avoir configuré la publication sélective dans un dossier, vous pouvez effectuer l’une des opérations suivantes :

* [Publiez sélectivement des fichiers sur Dynamic Media ou Experience Manager à l’aide de la fonction Gérer la publication](#selective-publish-manage-publication).
* [Annulation sélective de la publication de fichiers provenant de Dynamic Media ou d’un Experience Manager à l’aide de la commande Gérer la publication](#selective-unpublish-manage-publication).
* [Publication de fichiers sur Dynamic Media ou Experience Manager à l’aide de la publication](#quick-publish-aem-dm) rapide.
* [Publier des ressources ou en annuler la publication de manière sélective au moyen des résultats de recherche](#selective-publish-unpublish-search-results).

**Configurer la publication sélective au niveau des dossiers dans Dynamic Media:**

1. En Experience Manager, appuyez sur le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche, appuyez sur l’icône Navigation (juste au-dessus de l’icône Outils), puis appuyez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Utilisez l’une des méthodes suivantes :
   * Modifiez les propriétés d’un dossier existant. Dans **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, accédez à un dossier dont vous souhaitez modifier les propriétés. Sélectionnez le dossier puis, sur la barre d’outils, appuyez sur **[!UICONTROL Propriétés]**.
   * Modifiez les propriétés d’un nouveau dossier : en **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, près du coin supérieur droit de la page, appuyez sur **[!UICONTROL Créer > Dossier]**. Dans la boîte de dialogue **[!UICONTROL Créer un dossier]**, saisissez un titre (obligatoire) pour le dossier, puis appuyez sur **[!UICONTROL Créer]**. Sélectionnez le dossier puis, sur la barre d’outils, appuyez sur **[!UICONTROL Propriétés]**.

1. Dans la liste déroulante **[!UICONTROL Mode de synchronisation]**, sélectionnez l’une des options suivantes :

   | Mode de synchronisation | Description |
   | --- | --- |
   | **[!UICONTROL Hérité]** | Aucune valeur de synchronisation explicite sur le dossier ; au lieu de cela, le dossier hérite de la valeur de synchronisation de l’un de ses dossiers ancêtres ou du mode par défaut défini dans votre **[!UICONTROL Configuration de Dynamic Media]**. L’état détaillé de **[!UICONTROL Hérité]** s’affiche au moyen d’une info-bulle. |
   | **[!UICONTROL Synchroniser tout ce qui se trouve dans cette sous-arborescence de dossiers avec Dynamic Media]** | Pour que la publication dans Dynamic Media réussisse, les ressources doivent être synchronisées dans Dynamic Media. La sélection de cette option inclut tous les actifs de cette sous-arborescence pour la synchronisation avec Dynamic Media. Les paramètres propres au dossier remplacent le paramètre par défaut dans la **[!UICONTROL Configuration de Dynamic Media]**. |
   | **[!UICONTROL Exclure tout ce qui se trouve dans cette sous-arborescence de dossiers de la synchronisation Dynamic Media]** | Exclure tous les actifs de cette sous-arborescence de la synchronisation vers Dynamic Media. |

   ![Publication sélective au niveau du dossier](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Dans la liste déroulante **[!UICONTROL Mode de publication Dynamic Media]**, sélectionnez une option. L’option **[!UICONTROL Mode de publication Dynamic Media]** prend toujours par défaut la valeur définie dans la **[!UICONTROL Configuration Dynamic Media]**. Vous pouvez toutefois remplacer manuellement cette valeur **[!UICONTROL Configuration de Dynamic Media]** par défaut à l’aide de l’une des options suivantes.

   >[!IMPORTANT]
   >
   >Quelle que soit l’option de mode de publication Dynamic Media que vous sélectionnez, toutes les mises à jour apportées ultérieurement à un fichier *déjà* publié, ces mises à jour sont immédiatement publiées sans aucune autre action de l’utilisateur.

   | Option Mode de publication de média dynamique | Description |
   | --- | --- |
   | **[!UICONTROL Immédiatement]** | Lorsque des fichiers sont téléchargés dans ce dossier, le système les ingère dans le Experience Manager et fournit instantanément l’URL/l’incorporation. Cette option est liée uniquement à la publication des Experience Manager et aucune intervention de l’utilisateur n’est nécessaire pour publier des fichiers.<br>Cette option  ** n’est pas disponible si vous avez sélectionné  **[!UICONTROL Exclure tout ce qui se trouve dans cette sous-arborescence de dossiers dans le mode de]**   **** synchronisation de Dynamic Media à l’étape précédente. |
   | **[!UICONTROL Lors de l’activation]** | Lorsque des fichiers sont téléchargés dans ce dossier, vous devez d’abord publier explicitement le fichier avant qu’un lien URL/incorporé ne soit fourni. Cette option est liée à la publication des Experience Manager uniquement.<br>Cette option  ** n’est pas disponible si vous avez sélectionné  **[!UICONTROL Exclure tout ce qui se trouve dans cette sous-arborescence de dossiers dans le mode de]**   **** synchronisation de Dynamic Media à l’étape précédente. |
   | **[!UICONTROL Publication sélective]** | Les fichiers sont publiés à votre choix, soit Experience Manager, soit à Dynamic Media pour diffusion dans le domaine public. Les deux méthodes de publication s’excluent mutuellement. En d’autres termes, vous pouvez publier des ressources dans DMS7 afin d’utiliser des fonctionnalités telles que le recadrage intelligent ou les rendus dynamiques. Vous pouvez également publier des fichiers exclusivement sur le Experience Manager pour un aperçu sécurisé ; ces mêmes ressources sont *non* publiées dans DMS7 pour diffusion dans le domaine public. Cette option n&#39;est pas disponible si vous avez sélectionné **[!UICONTROL Exclure tout ce qui se trouve dans cette sous-arborescence de dossiers de Dynamic Media sync]** dans **[!UICONTROL mode de synchronisation]** à l&#39;étape précédente. |

1. Dans l’angle supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer et fermer]**, puis sur **[!UICONTROL OK]** pour revenir aux ressources du Experience Manager.

## Publiez sélectivement des fichiers sur Dynamic Media ou Experience Manager en tant que Cloud Service à l’aide de la fonction Gérer les publications{#selective-publish-manage-publication}

Avant de pouvoir utiliser **[!UICONTROL Gérer la publication]** pour publier des fichiers de manière sélective vers Dynamic Media ou vers un Experience Manager, assurez-vous d’avoir effectué l’une des opérations suivantes :

* Définissez l’option **[!UICONTROL Publier les ressources]** dans **[!UICONTROL Configuration de Dynamic Media]** sur **[!UICONTROL Publication sélective]**.
* Ou, configuré pour la publication sélective au niveau des dossiers.

Reportez-vous à [Création d’une configuration de Dynamic Media](#configuring-dynamic-media-cloud-services) ou [Configuration de la publication sélective au niveau des dossiers dans Dynamic Media](#selective-publish-configure-folder).

<!--
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>La *copie* de ressources vers et depuis des dossiers efface l’état de publication de ces ressources. Cependant, lorsque vous *déplacez* des ressources vers et depuis des dossiers dont la propriété de dossier est définie sur **[!UICONTROL Publication sélective]**, l’état de publication de ces ressources est conservé.

**Pour publier des fichiers de manière sélective sur Dynamic Media ou Experience Manager en tant que Cloud Service à l’aide de la commande Gérer la publication :**

1. En Experience Manager, appuyez sur le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche, appuyez sur l’icône Navigation (juste au-dessus de l’icône Outils), puis appuyez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, effectuez l’une des opérations suivantes :
   * Accédez à un dossier dont vous souhaitez publier les ressources. Sélectionnez le dossier puis, sur la barre d’outils, appuyez sur **[!UICONTROL Gérer la publication]**. Utilisez **[!UICONTROL Liste Vue]** pour vérifier plus facilement l’état de publication d’un dossier particulier.
   * Accédez à un dossier dont vous souhaitez publier les ressources. Ouvrez le dossier, puis sélectionnez une ou plusieurs ressources. Dans la barre d’outils, appuyez sur **[!UICONTROL Gérer la publication]**. Utilisez la **[!UICONTROL Vue de Liste]** pour vérifier plus facilement l’état de publication d’un fichier particulier.

      >[!NOTE]
      >
      >Si l’option **[!UICONTROL Gérer la publication]** n’est pas visible sur la barre d’outils, appuyez sur le bouton avec les points de suspension à la place, puis sélectionnez **[!UICONTROL Gérer la publication]** dans le menu de liste.

1. Sur la page **[!UICONTROL Gérer la publication – Options]**, sous **[!UICONTROL Action]**, sélectionnez le type d’activation souhaité.

   | Action | Description |
   | --- | --- |
   | **[!UICONTROL Publier]**  (vers le Experience Manager) | Pour publier des fichiers vers le Experience Manager pour une prévisualisation sécurisée, sélectionnez cette option. |
   | **[!UICONTROL Publier vers Dynamic Media]** | Pour publier des fichiers vers Dynamic Media pour diffusion dans le domaine public ou pour utiliser des fonctionnalités telles que Recadrage dynamique ou Rendus dynamiques, sélectionnez cette option.<br>Cette option n’est disponible que si l’option **[!UICONTROL Mode de publication Dynamic Media]** est définie sur **[!UICONTROL Publication sélective]** dans les propriétés du dossier. |

1. Sous **[!UICONTROL Planification]**, définissez le calendrier de publication.

   | Planification | Description |
   | --- | --- |
   | **[!UICONTROL Maintenant]** | Sélectionnez cette option pour publier immédiatement les ressources. |
   | **[!UICONTROL Plus tard]** | Sélectionnez cette option pour publier les ressources à une date et une heure spécifiques. |

1. Dans le coin supérieur droit de la page **[!UICONTROL Gestion de la publication]**, appuyez sur **[!UICONTROL Suivant]**.
1. Sur la page **[!UICONTROL Gestion de la publication – Portée]**, effectuez l’une des opérations suivantes :
   * Si nécessaire, sélectionnez une ou plusieurs ressources à supprimer de la publication.
   * Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication – Portée]**, appuyez sur **[!UICONTROL Publier]** ou **[!UICONTROL Publier vers Dynamic Media]**.
1. Appuyez sur **[!UICONTROL OK]**.

### Annulation sélective de la publication de fichiers à partir de Dynamic Media ou d’un Experience Manager à l’aide de l’option Gérer la publication {#selective-unpublish-manage-publication}

1. En Experience Manager, appuyez sur le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche, appuyez sur l’icône Navigation (juste au-dessus de l’icône Outils), puis appuyez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, effectuez l’une des opérations suivantes :
   * Accédez à un dossier dont vous souhaitez annuler la publication des ressources. Sélectionnez le dossier puis, sur la barre d’outils, appuyez sur **[!UICONTROL Gérer la publication]**. Utilisez **[!UICONTROL Liste Vue]** pour vérifier plus facilement l’état de publication d’un dossier particulier.
   * Accédez à un dossier dont vous souhaitez annuler la publication des ressources. Ouvrez le dossier, puis sélectionnez une ou plusieurs ressources. Dans la barre d’outils, appuyez sur **[!UICONTROL Gérer la publication]**. Utilisez la **[!UICONTROL Vue de Liste]** pour vérifier plus facilement l’état de publication d’un fichier particulier.

      >[!NOTE]
      >
      >Si l’option **[!UICONTROL Gérer la publication]** n’est pas visible sur la barre d’outils, appuyez sur le bouton avec les points de suspension à la place, puis sélectionnez **[!UICONTROL Gérer la publication]** dans le menu de liste.

1. Sur la page **[!UICONTROL Gérer la publication – Options]**, sous **[!UICONTROL Action]**, sélectionnez le type de désactivation souhaité.

   | Action | Description |
   | --- | --- |
   | **[!UICONTROL Annuler la publication]**  (à partir du Experience Manager) | Pour annuler la publication de fichiers du Experience Manager, sélectionnez cette option. |
   | **[!UICONTROL Annuler la publication à partir de Dynamic Media]** | Pour annuler la publication de fichiers depuis Dynamic Media, sélectionnez cette option.<br>Cette option n’est disponible que si l’option **[!UICONTROL Mode de publication Dynamic Media]** est définie sur **[!UICONTROL Publication sélective]** dans les propriétés du dossier. |

1. Sous **[!UICONTROL Planning]**, définissez le calendrier de la désactivation.

   | Planification | Description |
   | --- | --- |
   | **[!UICONTROL Maintenant]** | Sélectionnez cette option pour annuler immédiatement la publication des ressources. |
   | **[!UICONTROL Plus tard]** | Sélectionnez cette option pour annuler la publication des ressources à une date et une heure spécifiques. |

1. Dans le coin supérieur droit de la page **[!UICONTROL Gestion de la publication]**, appuyez sur **[!UICONTROL Suivant]**.
1. Sur la page **[!UICONTROL Gestion de la publication – Portée]**, effectuez l’une des opérations suivantes :
   * Sélectionnez une ou plusieurs ressources à supprimer de l’annulation de publication.
   * Dans le coin supérieur droit de la page **[!UICONTROL Gérer la publication – Portée]**, appuyez sur **[!UICONTROL Annuler la publication]** ou **[!UICONTROL Annuler la publication à partir de Dynamic Media]**.
1. Appuyez sur **[!UICONTROL OK]**.

## Publication de fichiers sur Dynamic Media ou Experience Manager à l’aide de la fonction de publication rapide {#quick-publish-aem-dm}

Vous pouvez utiliser la fonction **[!UICONTROL Publication rapide]** dans les cas d’activation de ressources simples. La fonction **[!UICONTROL Publication rapide]** publie immédiatement les ressources sélectionnées sans autre interaction de l’utilisateur. Toutes les références non publiées sont également publiées automatiquement.

>[!NOTE]
>
>Pour utiliser **[!UICONTROL Publication rapide]** pour publier des fichiers vers Dynamic Media ou le Experience Manager, veillez à ce que **[!UICONTROL Publication sélective]** soit activée dans votre **[!UICONTROL Configuration Dynamic Media]** ou dans les propriétés de dossier du dossier sélectionné.

**Pour publier des fichiers sur Dynamic Media ou Experience Manager à l’aide de la fonction Publication rapide :**

1. En Experience Manager, appuyez sur le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche de la page, appuyez sur l’icône Navigation (juste au-dessus de l’icône Outils), puis sur le côté droit de la page, appuyez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]**, effectuez l’une des opérations suivantes :
   * Accédez à un dossier dont vous souhaitez publier les ressources. Sélectionnez le dossier puis, sur la barre d’outils, appuyez sur **[!UICONTROL Publication rapide]**. Utilisez **[!UICONTROL Liste Vue]** pour vérifier plus facilement l’état de publication d’un dossier particulier.
   * Accédez à un dossier dont vous souhaitez publier les ressources. Ouvrez le dossier, puis sélectionnez une ou plusieurs ressources. Dans la barre d’outils, appuyez sur **[!UICONTROL Publication rapide]**. Utilisez la **[!UICONTROL Vue de Liste]** pour vérifier plus facilement l’état de publication d’un fichier particulier.

      >[!NOTE]
      >
      >Si l’option **[!UICONTROL Publication rapide]** n’est pas visible sur la barre d’outils, appuyez sur le bouton avec les points de suspension à la place, puis sélectionnez **[!UICONTROL Publication rapide]** dans le menu de liste.

      ![Publication rapide au niveau du dossier dans Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Sélectionnez l’une des options suivantes dans la liste de menu **[!UICONTROL Publication rapide]**.

   | Option Publication rapide | Effets |
   | --- | --- | 
   | Publier sur le Experience Manager | Publie immédiatement les ressources sélectionnées sur le Experience Manager. |
   | Publier sur Brand Portal | Publie immédiatement les ressources sélectionnées dans **[!UICONTROL Brand Portal]**.<br>Cette option n’est disponible que si votre instance de ressources Experience Manager dispose déjà de  **[!UICONTROL Portalus]** de marque. |
   | Publier vers Dynamic Media | Publie immédiatement les ressources sélectionnées dans Dynamic Media.<br>Un fichier doit déjà être synchronisé avec Dynamic Media. Si nécessaire, assurez-vous que **[!UICONTROL Mode de synchronisation]** dans les propriétés d&#39;un dossier est déjà défini sur **[!UICONTROL Synchroniser tout ce qui se trouve dans cette sous-arborescence de dossier avec Dynamic Media]**. |

1. Appuyez sur **[!UICONTROL OK]**, puis sur **[!UICONTROL Fermer]**.

## Publier des ressources ou en annuler la publication de manière sélective au moyen des résultats de recherche {#selective-publish-unpublish-search-results}

Les résultats de recherche peuvent afficher des ressources provenant de dossiers de ressources dont les paramètres de publication de Dynamic Media diffèrent. Lorsque vous avez sélectionné un ou plusieurs fichiers à partir des résultats de la recherche et que les fichiers ont des paramètres de mode de publication Dynamic Media différents, vous pouvez déclencher la publication ou l’annulation de publication dans **[!UICONTROL Gérer la publication]** de la barre d’outils.

Voir aussi [Rechercher des ressources dans le Experience Manager](/help/assets/search-assets.md).

**Pour publier des ressources ou en annuler la publication de manière sélective au moyen des résultats de recherche:**

1. En Experience Manager, dans le coin supérieur gauche de la page, appuyez sur le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche de la page, appuyez sur l’icône Navigation (juste au-dessus de l’icône Outils), puis appuyez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Dans la barre d’outils, dans le coin supérieur droit de la page, appuyez sur l’icône Rechercher (loupe).
1. Dans le champ **[!UICONTROL Texte à rechercher]**, entrez un mot-clé, puis appuyez sur **[!UICONTROL Entrée]**.
1. Dans le coin supérieur droit de la page, appuyez sur l’icône **[!UICONTROL Mode Liste]**.
1. Dans le coin supérieur gauche de la page, appuyez sur l’icône **[!UICONTROL Filtres]**.

   ![Mode Liste et Filtres dans les résultats de recherche](/help/assets/assets-dm/select-publish-search-result.png)

1. Dans le panneau de gauche, développez **[!UICONTROL Statut]**, puis développez le prédicat de recherche **[!UICONTROL Dynamic Media]**.
1. Utilisez les cases à cocher **[!UICONTROL Publiée]** et **[!UICONTROL Publication annulée]** pour affiner davantage les résultats de recherche en fonction de l’état de publication des ressources Dynamic Media.
Vous pouvez éventuellement utiliser ces cases à cocher avec le prédicat de recherche **[!UICONTROL Publier]** pour affiner les résultats de la recherche des ressources de Experience Manager **[!UICONTROL Publié]** et **[!UICONTROL Non publié]**.
1. Utilisez l’une des méthodes suivantes :
   * Sélectionnez une ou plusieurs ressources que vous souhaitez publier ou dont vous souhaitez annuler la publication.
   * Dans le coin supérieur droit de la page **[!UICONTROL Résultats de la recherche]**, appuyez sur **[!UICONTROL Tout sélectionner]**.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Gérer la publication]**. Si nécessaire, appuyez sur l’icône représentant des points de suspension dans la barre d’outils pour afficher **[!UICONTROL Gérer la publication]**.
1. Sur la page **[!UICONTROL Gérer la publication – Options]**, sélectionnez l’action de votre choix.

   | Action sélectionnée | Paramètre Publier les ressources dans la configuration de Dynamic Media | Les ressources sont |
   | --- | --- | --- |
   | Publier | Immédiatement ou Lors de l’activation | Publié sur Experience Manager et Dynamic Media. |
   | Publier | Publication sélective | Publié sur le Experience Manager uniquement. |
   | Annuler la publication | Immédiatement ou Lors de l’activation | Non publié du Experience Manager et de Dynamic Media. |
   | Annuler la publication | Publication sélective | Non publié uniquement à partir du Experience Manager. |
   | Publier vers Dynamic Media | Immédiatement ou Lors de l’activation | Non publié sur le Experience Manager, Dynamic Media ou les deux. |
   | Publier vers Dynamic Media | Publication sélective | Publiées sur Dynamic Media uniquement. |
   | Annuler la publication à partir de Dynamic Media | Immédiatement ou Lors de l’activation | Non non publié à partir d’un Experience Manager, de Dynamic Media ou des deux. |
   | Annuler la publication à partir de Dynamic Media | Publication sélective | Publication annulée à partir de Dynamic Media uniquement. |

1. Sous **[!UICONTROL Planning]**, définissez le calendrier de la désactivation.

   | Planification sélectionnée | Ce qui se produit |
   | --- | --- |
   | Maintenant | L’action sélectionnée est exécutée immédiatement. |
   | Plus tard | L’action sélectionnée est exécutée à la date et à l’heure particulières sélectionnées. |

1. Dans le coin supérieur droit de la page **[!UICONTROL Gestion de la publication – Options]**, appuyez sur **[!UICONTROL Suivant]**.
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
   * Dans le coin supérieur droit de la page **[!UICONTROL Gestion de la publication – Portée]**, appuyez sur **[!UICONTROL Publier]** ou **[!UICONTROL Annuler la publication]** pour lancer l’action.
1. Appuyez sur **[!UICONTROL OK]**.

## Vérification du statut de publication d’une ressource {#check-publish-status-of-asset}

Vous pouvez utiliser **[!UICONTROL Chronologie]** avec **[!UICONTROL vue de carte]**, **[!UICONTROL Vue de colonnes]** ou **[!UICONTROL Vue de Liste]** dans le Experience Manager pour vérifier rapidement l’état de publication d’un fichier.

**Pour vérifier l’état de publication d’une ressource:**

1. En Experience Manager, dans le coin supérieur gauche de la page, appuyez sur le logo du Experience Manager pour accéder à la console de navigation globale. Sur le côté gauche de la page, appuyez sur l’icône Navigation (juste au-dessus de l’icône Outils), puis appuyez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. En **[!UICONTROL Mode Carte]**, **[!UICONTROL Mode Colonnes]** ou **[!UICONTROL Mode Liste]** (la capture d’écran ci-dessous présente le **[!UICONTROL Mode Liste]**), ouvrez un dossier contenant les ressources que vous avez publiées ou dont vous avez annulé la publication.
1. Sélectionnez une ressource pour qu’elle s’affiche avec une coche. Voir la capture d’écran ci-dessous, par exemple.
1. Dans le menu déroulant situé dans le coin supérieur gauche de la page, sélectionnez **[!UICONTROL Chronologie]**.  La section **[!UICONTROL État]** du panneau de gauche affiche l’état de publication de la ressource sélectionnée.
Lorsque vous utilisez **[!UICONTROL Liste Vue]**, une colonne supplémentaire pour **[!UICONTROL Dynamic Media]** état de publication s’affiche.
   * Un dossier configuré pour la synchronisation avec Dynamic Media affiche par défaut la colonne **[!UICONTROL Dynamic Media]**.
   * Un dossier *non* configuré pour la synchronisation avec Dynamic Media n&#39;affiche pas la colonne Dynamic Media.
      ![Mode Liste et Chronologie](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Résolution des problèmes de publication sélective {#selective-publish-troubleshoot}

Une ressource qui n’est pas synchronisée avec Dynamic Media mais au niveau de laquelle une action de publication de Dynamic Media est déclenchée se traduit par le message d’erreur suivant et sa solution :

![Erreur de publication sélective](/help/assets/assets-dm/selective-publish-error.png)

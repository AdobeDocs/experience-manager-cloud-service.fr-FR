---
title: Comment personnaliser un modèle de document d’enregistrement généré automatiquement pour le Forms adaptatif ?
description: Découvrez comment télécharger, personnaliser et charger à nouveau le modèle de document d’enregistrement (DE) généré automatiquement pour le Forms adaptatif à l’aide d’Adobe Forms Designer.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer
source-git-commit: 51ec9ef76a8f3f9b7bf2cdc25b03f72e286f586f
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 3%

---


# Personnaliser le modèle de document d’enregistrement généré automatiquement

<span class="preview"> Cet article s’applique à la fois aux **composants principaux** et aux **composants de base** basés sur le Forms adaptatif.</span>

Lorsque vous générez automatiquement un document d’enregistrement (DE) pour un formulaire adaptatif, AEM Forms crée un modèle par défaut basé sur la structure du formulaire. Vous pouvez personnaliser ce modèle généré automatiquement pour répondre aux exigences de marque et de disposition de votre entreprise.

Le workflow de personnalisation comprend trois étapes :

1. Téléchargez le modèle de document d’enregistrement généré automatiquement depuis Forms Manager.
1. Modifiez le modèle à l’aide d’Adobe Forms Designer.
1. Chargez à nouveau le modèle personnalisé vers AEM Forms et configurez-le en tant que modèle personnalisé.

## Prérequis {#prerequisites}

Avant de commencer, vérifiez que vous disposez des éléments suivants :

* Accès à AEM Forms Manager avec des autorisations de téléchargement et de chargement de modèles.
* Adobe Forms Designer installé sur votre ordinateur local.
* Un formulaire adaptatif avec l’option **[!UICONTROL Générer un document d’enregistrement]** activée.

## Étape 1 : télécharger le modèle de document d’enregistrement généré automatiquement {#download-auto-generated-dor-template}

Pour télécharger le modèle de document d’enregistrement généré automatiquement (fichier XDP) pour votre formulaire adaptatif :

1. Connectez-vous à votre instance de création AEM Forms.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et Documents]**.
1. Sélectionnez le formulaire adaptatif pour lequel vous souhaitez télécharger le modèle de document d’enregistrement.
1. Ouvrez les propriétés du formulaire adaptatif sélectionné.
1. Dans le panneau des propriétés, sélectionnez l’option **[!UICONTROL Télécharger le document d’enregistrement]** pour télécharger le modèle de document d’enregistrement généré automatiquement (fichier XDP).
1. Enregistrez le fichier XDP téléchargé sur votre ordinateur local.


## Étape 2 : personnalisation du modèle à l’aide d’Adobe Forms Designer {#customize-template-using-designer}

Ouvrez le modèle XDP téléchargé dans Adobe Forms Designer et modifiez-le en fonction des besoins de votre entreprise.

1. Ouvrez le fichier XDP téléchargé dans **Adobe Forms Designer**.
1. Personnalisez le modèle selon vos besoins. Voici quelques exemples de personnalisation :

   * **Plusieurs gabarits de page** : ajoutez des gabarits de page supplémentaires pour définir différentes dispositions pour des pages spécifiques du document d’enregistrement. Par exemple, utilisez une première page distincte avec un en-tête de lettre d’entreprise et des pages suivantes avec une disposition plus simple.
   * **Couleurs et familles de polices** : modifiez la couleur, la taille et la famille de la police pour les aligner sur les directives de votre marque.
   * **Éléments personnalisés** : ajoutez des éléments tels que des logos, des en-têtes, des pieds de page et du texte de clause de non-responsabilité de la société pour établir une identité de marque cohérente.
   * **Mise en page et style** : ajustez les marges, l’espacement et la structure globale de la page pour améliorer la lisibilité.
   * **Style et positionnement des champs** : modifiez l’aspect et la position des champs du formulaire pour qu’ils correspondent à la disposition souhaitée.

1. Enregistrez le modèle XDP personnalisé.

>[!NOTE]
>
> Ne supprimez ou ne modifiez aucun script présent dans le modèle. La modification des scripts peut affecter la génération de la liaison de données et du document d’enregistrement.

## Étape 3 : Charger à nouveau le modèle personnalisé dans AEM {#reupload-customized-template}

Après avoir personnalisé le modèle, chargez-le dans AEM Forms et configurez le formulaire adaptatif pour l’utiliser.

1. Chargez le modèle XDP personnalisé sur votre instance AEM Forms :
   * Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et Documents]**.
   * Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Charger un fichier]** et chargez le fichier XDP personnalisé.

Configurez ensuite le formulaire pour utiliser le modèle personnalisé. Les étapes varient selon que votre formulaire est basé sur des composants principaux ou des composants de base.

>[!BEGINTABS]

>[!TAB Composants principaux]

Pour le Forms adaptatif basé sur les composants principaux :

1. Ouvrez le formulaire adaptatif dans l’éditeur auquel vous souhaitez appliquer le modèle personnalisé.
1. Dans l’arborescence de contenu, sélectionnez le **[!UICONTROL Conteneur de guides]** (panneau racine).
1. Ouvrez **[!UICONTROL Propriétés]** puis cliquez sur l’icône **[!UICONTROL Document d’enregistrement]** (DE) pour ouvrir les propriétés du document d’enregistrement.
1. Dans l’onglet **[!UICONTROL De base]**, ouvrez le menu déroulant **[!UICONTROL Modèle]** et sélectionnez **[!UICONTROL Personnalisé]**.
1. Recherchez et sélectionnez le modèle XDP personnalisé chargé.
1. Sélectionnez la coche à enregistrer.

   ![Propriétés du document d’enregistrement - Modèle défini sur Personnalisé (composants principaux)](/help/forms/assets/submission-pdf-dor-custom-template.png)

>[!TAB Composants de base]

Pour le Forms adaptatif basé sur les composants de base :

1. Ouvrez le formulaire adaptatif dans l’éditeur auquel vous souhaitez appliquer le modèle personnalisé.
1. Sélectionnez le panneau racine (conteneur de formulaires).
1. Ouvrez **[!UICONTROL Propriétés du document d’enregistrement]** (dans le panneau Propriétés ou l’onglet De).
1. Dans l’onglet **[!UICONTROL De base]**, ouvrez le menu déroulant **[!UICONTROL Modèle]** et sélectionnez **[!UICONTROL Personnalisé]**.
1. Recherchez et sélectionnez le modèle XDP personnalisé chargé.
1. Sélectionnez **[!UICONTROL Terminé]** pour enregistrer.

   ![Propriétés du document d’enregistrement - Modèle défini sur Personnalisé (composants de base)](/help/forms/assets/dor-custom-template-foundation-components.png)

>[!ENDTABS]

Le formulaire adaptatif utilise désormais le modèle personnalisé lors de la génération du document d’enregistrement.

## Vérification du modèle personnalisé {#verify-customized-template}

Pour vérifier que le modèle personnalisé est correctement appliqué :

1. Envoyez une entrée de test pour le formulaire adaptatif.
1. Générez le document d’enregistrement.
1. Vérifiez que le PDF généré reflète vos personnalisations, y compris les logos, les polices, les modifications de disposition et d’autres éléments de marque.

## Résolution des problèmes {#troubleshooting}

| Problème | Résolution |
|---|---|
| Le modèle personnalisé ne se charge pas. | Assurez-vous que le fichier XDP est valide et n’est pas corrompu. Vérifiez que vous disposez des autorisations requises pour charger des fichiers vers AEM Forms. |
| Les personnalisations n’apparaissent pas dans le document d’enregistrement généré. | Vérifiez que vous avez sélectionné le modèle personnalisé correct dans la section **[!UICONTROL Configuration du modèle de document d’enregistrement]** des propriétés du formulaire. |
| Problèmes de mise en page ou de mise en forme dans le PDF généré. | Vérifiez que les personnalisations dans Adobe Forms Designer respectent les [ conventions relatives aux modèles de base ](/help/forms/generate-document-of-record-core-components.md#base-template-conventions). Assurez-vous que tous les éléments sont correctement positionnés dans la structure du modèle. |

## Voir également {#see-also}

* [Génération d’un document d’enregistrement pour le Forms adaptatif (composants principaux)](/help/forms/generate-document-of-record-core-components.md)
* [Générer un document d’enregistrement pour le Forms adaptatif (composants de base)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Modèle de base d’un document d’enregistrement](/help/forms/generate-document-of-record-core-components.md#base-template-of-a-document-of-record)
* [Personnaliser les informations d’identité graphique d’un document d’enregistrement](/help/forms/generate-document-of-record-core-components.md#customize-the-branding-information-in-document-of-record)


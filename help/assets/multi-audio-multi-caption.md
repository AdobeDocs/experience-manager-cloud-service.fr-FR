---
title: Vidéos sur les fonctionnalités Multi Audio et Multi Captions dans Dynamic Media avec OpenAPI
description: Découvrez comment ajouter et gérer plusieurs pistes audio et sous-titres pour les ressources vidéo dans Dynamic Media avec les fonctionnalités OpenAPI d’Adobe Experience Manager Assets.
role: User
badgeSaas: label="AEM Assets" type="Positive"
source-git-commit: 80a32672ec018274b0410abfa14fdd761fdb5aba
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 14%

---


# Vidéos sur les fonctionnalités Multi Audio et Multi Captions dans Dynamic Media avec OpenAPI {#multi-audio-captions-dynamic-media-with-openapi-capabilities}

[!DNL Adobe Experience Manager Assets] Dynamic Media avec les fonctionnalités OpenAPI vous permet d’ajouter plusieurs pistes audio et fichiers de sous-titres aux ressources vidéo. Cette fonctionnalité améliore l’accessibilité, prend en charge les expériences de lecture localisées et améliore la diffusion vidéo pour les audiences mondiales.

Ces fonctionnalités sont gérées directement à partir de l’onglet **Légendes et pistes audio** de la page des propriétés de la ressource vidéo.

>[!NOTE]
>
>La prise en charge multi-audio et multi-légendes dans Dynamic Media avec les fonctionnalités OpenAPI est une fonctionnalité à disponibilité limitée. Vous pouvez l’activer en créant un [&#x200B; ticket d’assistance &#x200B;](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

Tous les formats vidéo Dynamic Media avec fonctionnalités OpenAPI prises en charge prennent en charge plusieurs légendes et pistes audio.

## Avant de commencer {#before-you-begin}

Vérifiez les éléments suivants :

* La ressource vidéo est disponible dans [!DNL AEM Assets]
* Format audio pris en charge : `.mp3`
* Format de légende pris en charge : `.vtt`

>[!NOTE]
>
>Dynamic Media avec des fonctionnalités OpenAPI ne nécessite pas de profil vidéo. L’onglet **Légendes et pistes audio** est disponible par défaut pour toutes les ressources vidéo.

## Ajout de plusieurs pistes audio {#add-audio-tracks}

![Onglet Légendes et pistes audio](/help/assets/assets/caption-audio-tracks1.png)

Pour ajouter des pistes audio à une vidéo :

1. Accédez à la ressource vidéo chargée.
1. Sélectionnez la ressource et cliquez sur **Propriétés**.
1. Ouvrez l’onglet **Légendes et pistes audio**.
1. Cliquez sur **Charger des pistes audio**.
1. Sélectionnez un ou plusieurs fichiers `.mp3`.
1. Cliquez sur l’icône **Dessin** en regard du nom du fichier de piste audio.

Dans la boîte de dialogue **Modifier la piste audio** :

* **Filename** - Nom de fichier par défaut dérivé du fichier chargé.
* **Langue** - Sélectionnez la langue audio.
* **Type** - Original, Standard ou Audio-description.
* **Libellé** - Nom d’affichage affiché dans le sélecteur audio du lecteur.

![Boîte de dialogue Piste audio](/help/assets/assets/edit-audio1.png)

1. Cliquez sur **Enregistrer**.
1. Répétez l’opération pour obtenir d’autres pistes audio si nécessaire.
1. Cliquez sur **Enregistrer et fermer**.

>[!NOTE]
>
>Chaque libellé de piste audio doit être unique.

## Ajouter plusieurs légendes {#add-captions}

![Onglet Légendes et pistes audio](/help/assets/assets/caption-audio-tracks1.png)

Pour ajouter des légendes :

1. Ouvrez la page vidéo **Propriétés**.
1. Ouvrez l’onglet **Légendes et pistes audio**.
1. Cliquez sur **Créer une légende** > **Télécharger des fichiers**.
1. Sélectionnez un ou plusieurs fichiers `.vtt`.
1. Cliquez sur l’icône **Dessin** en regard du fichier de légendes.

![&#x200B; Boîte de dialogue Charger la légende &#x200B;](/help/assets/assets/upload-caption.png)

Dans la boîte de dialogue **Modifier la légende** :

* **Filename** - Nom de fichier téléchargé par défaut.
* **Langue** - Langue de la légende.
* **Type** - Sous-titre ou légende.
* **Libellé** - Nom d’affichage affiché dans le sélecteur de légendes du lecteur.

![&#x200B; Boîte de dialogue Modifier la légende &#x200B;](/help/assets/assets/edit-captions.png)

1. Cliquez sur **Enregistrer**.
2. Cliquez sur **Enregistrer et fermer**.

>[!NOTE]
>
>La modification du texte de sous-titre n’est pas prise en charge. Mettez à jour le fichier en externe et chargez-le à nouveau.

## Comportement de validation {#approval-behavior}

L’approbation dépend de la ressource vidéo parent :

* Si **Approuvé**, les nouveaux fichiers sont automatiquement approuvés après traitement.
* S’ils ne sont pas approuvés, ils suivent le cycle de vie du parent.

## Affichage du statut du cycle de vie des fichiers {#status}

* **Approuvé** - Prêt pour la lecture
* **Rejeté** - Fichier rejeté

## Définition de la piste audio par défaut {#set-default-audio}

Par défaut, l’audio original est utilisé.

1. Ouvrez **Légendes et pistes audio**.
1. Sélectionnez la piste audio.
1. Cliquez sur **Définir par défaut**.

   ![Définir comme action par défaut](/help/assets/assets/set-default.png)

1. Cliquez sur **OK**.
1. Cliquez sur **Enregistrer et fermer**.

## Prévisualiser l’audio et les sous-titres {#preview-audio-captions}

Après le traitement :

1. Ouvrez l’aperçu vidéo.

   ![Lecteur de prévisualisation vidéo](/help/assets/assets/preview-caption-audio.png)

1. Utilisez les commandes du lecteur :

   * Changement de pistes audio
   * Activer les légendes

## Télécharger des sous-titres ou des fichiers audio {#download-tracks}

1. Sélectionnez une légende ou un fichier audio.
1. Cliquez sur **Télécharger**.

   ![Action de suivi du téléchargement](/help/assets/assets/download-caption.png)

1. Cliquez sur **Télécharger**.

Le fichier sélectionné est téléchargé sur votre système local.

## Supprimer les sous-titres ou les fichiers audio {#delete-tracks}

1. Sélectionnez une légende ou un fichier audio.
1. Cliquez sur **Supprimer**.

   ![Supprimer l’action de suivi](/help/assets/assets/delete-caption.png)

1. Cliquez sur **OK**.

L’audio original extrait de la vidéo ne peut pas être supprimé.


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

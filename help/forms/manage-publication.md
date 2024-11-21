---
title: Comment publier ou annuler la publication de formulaires sur des instances de prévisualisation ou de publication ?
description: Découvrez comment publier ou annuler la publication de formulaires à partir de l’environnement de création d’AEM pour prévisualiser ou publier des instances. Que vous testiez vos formulaires dans un environnement d’évaluation ou que vous les déployiez en direct pour les utilisateurs finaux, AEM fournit des outils rationalisés pour gérer efficacement ce processus.
Keywords: 6.5 forms to cloud service, 6.5 forms to cs, manage publication, , AEM Forms 6.5 to Cloud Service, AEM form migration to cloud service, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
contentOwner: khsingh
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
source-git-commit: 242dcbc5bb541dfac601454fb75dec3bdff1ea64
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 7%

---


# &#x200B; Gestion de la publication dans Experience Manager Forms

En tant qu’administrateur Adobe Experience Manager Forms, vous pouvez publier des formulaires de votre instance d’auteur vers Experience Manager Forms. Vous pouvez planifier la publication d’un formulaire ou d’un dossier à une date ou une heure ultérieure. Une fois la publication effectuée, les utilisateurs peuvent accéder aux formulaires et les remplir.

Vous pouvez publier ou annuler la publication d’un formulaire à l’aide de l’option Publish ou Gérer la publication disponible dans l’interface de Experience Manager Forms. Si vous apportez des modifications ultérieures aux formulaires ou au dossier d’origine dans Experience Manager Forms, les modifications ne sont pas répercutées dans l’instance de publication tant que vous n’avez pas republié à partir de Experience Manager Forms. Cela permet de s’assurer que les modifications en cours ne sont pas disponibles dans l’instance de publication. Seules les modifications publiées par un administrateur sont disponibles dans l’instance de publication.

## Option Formulaires Publish à l’aide de Publish

L’option de publication permet de publier immédiatement un formulaire. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez un formulaire à publier. Cliquez sur l’option Publish de la barre d’outils, examinez toutes les ressources de référence qui seraient publiées avec le formulaire, puis cliquez sur Publish.

Capture d&#39;écran d&#39;un ordinateur

Description générée automatiquement

## Publish ou annulation de la publication de formulaires à l’aide de la fonction Gérer la publication


La fonction Gérer la publication vous permet de publier ou d’annuler la publication de contenu vers et depuis la destination sélectionnée, d’ajouter du contenu à la liste de publication à partir du dossier Formulaires et documents, de sélectionner des références à publier et de planifier la publication à une date ou une heure ultérieure.


Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez un formulaire à publier. Cliquez sur l’option Gérer la publication dans la barre d’outils.


Capture d&#39;écran d&#39;un ordinateur

Description générée automatiquement



Les options suivantes sont disponibles dans l’interface Gérer la publication :

* Actions

   * Publish : Publish forms vers la destination sélectionnée
   * Annuler la publication : annuler la publication de formulaires à partir de la destination

* Destination

   * Publish : Publish forms vers l’instance Publish Experience Manager Forms (AEM).
   * Aperçu : Publish forms vers l’instance d’aperçu Experience Manager Forms (AEM).

* Planification

   * Maintenant : les formulaires Publish immédiatement
   * Plus tard : Publish forms selon la date ou l’heure d’activation



Pour continuer, cliquez sur **Suivant**. Dans l’onglet Périmètre , utilisez les options Ajouter du contenu pour ajouter du contenu à publier. Par exemple, vous pouvez ajouter d’autres fichiers Forms ou Document d’enregistrement.

### Ajouter du contenu

La publication sur Experience Manager Forms vous permet d’ajouter davantage de contenu (formulaires, ressources et dossiers) à la liste de publication. Vous pouvez ajouter d’autres formulaires, ressources ou dossiers à la liste à partir du dossier formsanddocuments . Cependant, vous ne pouvez pas ajouter de ressources à partir de plusieurs dossiers à la fois.

Capture d&#39;écran d&#39;un ordinateur

Description générée automatiquement

Cliquez sur le bouton **Ajouter du contenu** pour ajouter du contenu supplémentaire. Vous pouvez ajouter plusieurs ressources à partir d’un dossier ou ajouter plusieurs dossiers à la fois. Cependant, vous ne pouvez pas ajouter de ressources à partir de plusieurs dossiers à la fois.

Pour configurer les références à publier ou non pour un formulaire ou d’autres actifs, sélectionnez le formulaire ou l’actif et cliquez sur Références publiées.

Capture d&#39;écran d&#39;un ordinateur

Description générée automatiquement

Dans la boîte de dialogue Références publiées , désélectionnez les ressources que vous prévoyez de ne pas publier et cliquez sur Terminé.


Capture d&#39;écran d&#39;un ordinateur

Description générée automatiquement


## Publish ou annulation de la publication d’un formulaire ultérieurement


En plus de vous permettre de publier ou d’annuler la publication de formulaires à des date et heure ultérieures, l’option Publier ou Annuler la publication ultérieurement permet également de configurer un workflow. Les formulaires sont publiés ou dépubliés une fois le processus terminé. Pour planifier un formulaire à publier ou annuler la publication :

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez le formulaire dont vous souhaitez planifier la publication.
1. Cliquez sur l’option Gérer la publication dans la barre d’outils.
1. Cliquez sur Publish ou Annuler la publication sur Action, puis sélectionnez la destination dans laquelle vous souhaitez publier ou annuler la publication du contenu.

   * Aperçu : utilisez l’option Aperçu pour publier ou annuler la publication dans un environnement de prévisualisation Experience Manager Forms. Les environnements d’aperçu Experience Manager Forms sont utilisés pour tester sous des formulaires de développement.
   * Publish : utilisez l’option Experience Manager Forms Publish pour envoyer le formulaire à l’environnement de publication Experience Manager Forms une fois que le formulaire est prêt à être utilisé dans un environnement de production.


1. Sélectionnez Plus tard dans Planification.

1. Sélectionnez une Date d’activation et indiquez la date et l’heure. Cliquez sur Suivant.

   Capture d&#39;écran d&#39;un ordinateur

   Description générée automatiquement

1. Dans l&#39;onglet Périmètre , ajoutez du contenu (si nécessaire). Cliquez sur Suivant.

   Capture d&#39;écran d&#39;un ordinateur

   Description générée automatiquement

1, (Facultatif) Dans l’onglet Workflows, spécifiez un titre de workflow. Cliquez sur Publish ultérieurement.

Capture d&#39;écran d&#39;un ordinateur

Description générée automatiquement

## Définition du statut de publication

Il existe plusieurs façons de déterminer l’état de publication :

* Connectez-vous à l’instance de destination pour vérifier les formulaires publiés et d’autres ressources (selon la date ou l’heure planifiée).

* Utilisez la vue de la chronologie pour déterminer l’état de publication.

* Utilisez le menu d’informations sur la page dans l’éditeur de Forms adaptatif.
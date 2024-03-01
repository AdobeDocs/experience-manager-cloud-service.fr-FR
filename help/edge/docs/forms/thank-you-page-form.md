---
title: Configuration de la page de remerciement pour EDS Forms
description: Découvrez comment configurer les pages de remerciement et la redirection pour EDS Forms afin d’optimiser l’expérience utilisateur et de rationaliser les parcours utilisateur.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e2970c7a141025222c6b119787142e7c39d453af
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Configuration des pages de remerciement et de la redirection dans les blocs Forms adaptatifs

Les pages de remerciement et la redirection sont des aspects essentiels de l’amélioration de l’expérience utilisateur, ce qui permet aux utilisateurs de confirmer, de communiquer clairement et de naviguer en douceur après l’envoi du formulaire.

## Configuration des pages de remerciement

Les pages de remerciement servent d’avertissement rassurant aux utilisateurs et permettent aux entreprises de communiquer des informations essentielles tout en renforçant l’identité de marque. Pour configurer une page de remerciement pour EDS Forms, procédez comme suit :

1. Accédez à votre dossier de projet de diffusion Edge AEM sur Microsoft SharePoint ou Google Workspace.
1. Créez un fichier Microsoft Word ou Google Docs nommé &quot;Merci&quot; dans le répertoire de votre projet.
1. Ajoutez votre message de remerciement au fichier &quot;Merci&quot;.
   ![Exemple de page de remerciement](/help/edge/assets/sample-thankyou-page.png)
1. Utilisez AEM Sidekick pour prévisualiser et publier le fichier &quot;Merci&quot;.

## Redirection des utilisateurs après envoi

La redirection facilite les parcours utilisateur fluides en orientant les utilisateurs vers les destinations appropriées, en optimisant l’engagement et en augmentant les taux de conversion.

Par défaut, le bloc Forms adaptatif redirige les utilisateurs vers la page de remerciement. Pour rediriger les utilisateurs vers une page autre que la page de remerciement par défaut, deux options s’offrent à vous :

* remplacez la page de remerciement existante par une autre page, ou
* redirigez la page &quot;thankyou&quot; vers une autre page de votre choix.

### Remplacez la page existante &quot;Merci&quot;

1. Ouvrez le[Projet EDS]/blocks/form/form.js&quot; pour modification.
1. Modifiez la variable `thankyou` dans la ligne suivante à la page de votre choix :

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Par exemple,

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'payment';
   ```

   >[!NOTE]
   >
   > Assurez-vous qu’il existe une page portant le même nom dans le dossier de projet du service de diffusion Edge sur Microsoft SharePoint ou Google Workspace. Si la page n’existe pas, créez-la et publiez-la.

1. Continuez pour archiver le dossier &quot;form.js&quot; mis à jour et ses fichiers sous-jacents dans votre projet de service de diffusion Edge sur GitHub. Cette mise à jour garantit que le formulaire redirige désormais vers la page mise à jour, comme indiqué.

1. Assurez-vous que la page existe dans votre dossier de projet EDS et publiez-la.


### Utilisation des redirections de site web

Configurez une redirection de site web pour rediriger la page &quot;Merci&quot; vers une autre page. Voir [Documentation sur les redirections](https://www.aem.live/docs/redirects) pour obtenir des instructions détaillées.



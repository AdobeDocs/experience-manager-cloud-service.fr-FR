---
title: Configuration de la page de remerciement pour EDS Forms
description: Configuration de la page de remerciement pour EDS Forms
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0604838311bb9ab195789fad755b0910e09519fd
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 5%

---


# Configuration des redirections de bloc de formulaire

Vous avez la possibilité de paramétrer le bloc de formulaire pour qu&#39;il redirige vers une autre page de votre site web au lieu de la page de remerciement par défaut. Pour configurer une autre page comme destination de redirection

1. Ouvrez le fichier `[EDS Project]/blocks/form/form.js` en mode d’édition.

   ![code pour le noeud de remerciement](/help/edge/assets/change-thankyou-node.png)

1. Modifiez la variable `thankyou` dans la ligne suivante vers le noeud de votre choix :

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Par exemple,

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'home';
   ```

   >[!NOTE]
   >
   > Assurez-vous qu’une page de document portant le même nom est créée dans le dossier de projet du service de diffusion Edge sur Microsoft SharePoint ou Google Sheets, si elle n’a pas déjà été créée.


1. Passez à l’archivage du dossier &quot;form.js&quot; mis à jour et de ses fichiers sous-jacents dans votre projet de service de diffusion Edge sur GitHub. Cette mise à jour garantit que le formulaire redirige désormais vers le noeud mis à jour, comme indiqué.

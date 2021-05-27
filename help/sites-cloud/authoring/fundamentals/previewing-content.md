---
title: Aperçu du contenu
description: Découvrez comment utiliser le service d’aperçu AEM pour prévisualiser le contenu avant sa mise en ligne.
source-git-commit: 9b4ac173c55380cbc06de64677470818aa801df4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---


# Aperçu du contenu {#previewing-content}

>[!NOTE]
>
>La fonctionnalité Aperçu fait partie de la version 2021.5.0 et sera déployée progressivement au cours des prochaines semaines.

AEM propose un service d’aperçu de site conçu pour permettre aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Il facilite la prévisualisation des expériences de page qui ne seraient pas visibles autrement à partir de l’environnement de création, comme les transitions de page et tout autre contenu côté publication uniquement.

## Publication de contenu en vue de la prévisualisation {#publishing-content-to-preview}

Vous pouvez publier du contenu dans le service d’aperçu à l’aide de l’interface utilisateur de publication gérée comme suit :

1. Sélectionnez la ou les pages à envoyer pour la prévisualisation dans la console Sites et cliquez ensuite sur le bouton **Gérer la publication**
1. Dans l’assistant suivant, sélectionnez **Aperçu** comme destination.

   ![publication gérée](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Cliquez sur **Suivant**, puis sur **Publier** pour confirmer.

Pour voir le contenu de la prévisualisation, ajoutez **preview** à l’URL de publication de votre instance de production. L’URL doit être construite comme suit :

```
https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
```

Voir [Gestion des environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en) pour plus d’informations sur la manière d’obtenir les URL de vos environnements.


---
title: Aperçu du contenu
description: Découvrez comment utiliser le service d’aperçu AEM pour prévisualiser le contenu avant sa mise en ligne.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: c30470b321a4fba8c8de9becb62c518faff05498
workflow-type: tm+mt
source-wordcount: '390'
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

1. Une boîte de dialogue affiche les URL d’accès au contenu dans l’environnement Aperçu.

   Ou pour afficher le contenu de la prévisualisation, vous pouvez également ajouter **preview** à l’URL de publication de votre instance de production.

   L’URL doit être construite comme suit :

   ```
   https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
   ```

Voir [Gestion des environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en) pour plus d’informations sur la manière d’obtenir les URL de vos environnements.

Le contenu peut également être publié pour la prévisualisation à l’aide d’un [processus Publier l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) avec le paramètre agentId défini pour la prévisualisation ou à l’aide de l’[API de réplication](/help/operations/replication.md#replication-api) avec un AgentFilter configuré pour la prévisualisation.

## Configuration des paramètres OSGi pour le niveau de prévisualisation {#configuring-osgi-settings-for-the-preview-tier}

Les valeurs de propriété OSGI de leur niveau d’aperçu sont héritées du niveau de publication, mais les valeurs du niveau d’aperçu peuvent être différenciées du niveau de publication à l’aide de valeurs spécifiques à l’environnement définissant le paramètre de service avec la valeur &quot;aperçu&quot;. Prenez l’exemple ci-dessous d’une propriété OSGI qui détermine l’URL d’un point de terminaison d’intégration :

```
[
{
"name":"INTEGRATION_URL",
"type":"string",
"value":"http://s2.integrationvendor.com",
"service": "preview"
}
]
```

Pour plus d’informations, voir [cette section](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) de la documentation de configuration OSGi.

## Débogage de l’aperçu à l’aide de Developer Console {#debugging-preview-using-the-developer-console}

Pour déboguer le niveau d’aperçu à l’aide de Developer Console, procédez comme suit :

* Dans [Developer Console](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools), sélectionnez **— All Preview —** ou un environnement de production qui inclut **prev** dans son nom.
* Générer les informations pertinentes pour l&#39;instance d&#39;aperçu
Voir [Gestion des environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en) pour plus d’informations sur la manière d’obtenir les URL de vos environnements.

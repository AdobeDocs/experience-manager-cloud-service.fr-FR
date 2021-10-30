---
title: Aperçu du contenu
description: Découvrez comment utiliser le service d’aperçu AEM pour prévisualiser le contenu avant sa mise en ligne.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 78c5649c6b9c04cb459f5730161affeb452c916c
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# Aperçu du contenu {#previewing-content}

>[!NOTE]
>
>Pour activer la fonction d’aperçu sur les environnements créés avant le 3 août 2021, vérifiez que l’environnement se trouve dans AEM version 2021.05.5368.20210529T101701Z ou ultérieure, puis exécutez un pipeline initié par le client.

AEM propose un service d’aperçu Sites conçu pour permettre aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Il facilite la prévisualisation des expériences de page qui ne seraient pas visibles autrement à partir de l’environnement de création, comme les transitions de page et tout autre contenu côté publication uniquement.

Lisez également [Accès au service Aperçu](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Publication de contenu en vue de la prévisualisation {#publishing-content-to-preview}

Vous pouvez publier du contenu dans le service d’aperçu à l’aide de l’interface utilisateur de publication gérée comme suit :

1. Sélectionnez la ou les pages à envoyer pour prévisualisation dans la console Sites et cliquez ensuite sur le bouton **Gérer la publication**.
1. Dans l’assistant suivant, sélectionnez **Aperçu** comme destination.

   ![publication gérée](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Cliquez sur **Suivant**, puis sur **Publier** pour confirmer.

1. Une boîte de dialogue affiche les URL d’accès au contenu dans l’environnement Aperçu.

   Ou pour afficher le contenu de la prévisualisation, vous pouvez également ajouter **preview** à l’URL de publication de votre instance de production.

   L’URL doit être construite comme suit :

   ```
   https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
   ```

Voir [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la manière d’obtenir les URL de vos environnements.

Le contenu peut également être publié pour la prévisualisation à l’aide d’un [workflow de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) avec le paramètre agentId défini pour la prévisualisation ou à l’aide de l’[API de réplication](/help/operations/replication.md#replication-api) avec un AgentFilter configuré pour la prévisualisation.

## Configuration des paramètres OSGi pour le niveau d’aperçu {#configuring-osgi-settings-for-the-preview-tier}

Les valeurs de propriété OSGI du niveau d’aperçu sont héritées du niveau de publication, mais les valeurs du niveau d’aperçu peuvent être différenciées du niveau de publication à l’aide de valeurs spécifiques à l’environnement définissant le paramètre de service avec la valeur « preview ». Prenez l’exemple ci-dessous d’une propriété OSGI qui détermine l’URL d’un point d’entrée d’intégration :

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

Pour plus d’informations, consultez [cette section](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) de la documentation de la configuration OSGi.

## Débogage de l’aperçu à l’aide de Developer Console {#debugging-preview-using-the-developer-console}

Pour déboguer le niveau d’aperçu à l’aide de Developer Console, procédez comme suit :

* Dans [Developer Console](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools), sélectionnez **-- Tous les aperçus --** ou un environnement de production qui inclut **prev** dans son nom.
* Générez les informations pertinentes pour l’instance d’aperçu
Voir [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la manière d’obtenir les URL de vos environnements.

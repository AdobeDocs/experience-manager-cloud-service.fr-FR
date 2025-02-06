---
title: Internationaliser des chaînes d’interface utilisateur
description: AEM propose une console de gestion des différentes traductions de textes utilisés dans l’interface utilisateur des composants.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 14a6516872f842d099b902b9f633b1d6f984266d
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 14%

---


# Utiliser le traducteur pour gérer les dictionnaires{#using-translator-to-manage-dictionaries}

AEM fournit une console pour gérer les différentes traductions des textes utilisés dans l&#39;interface utilisateur des composants. Cette console est disponible à l’adresse suivante :

`https://<hostname>:<port-number>/libs/cq/i18n/gui/translator.html`

Utilisez l’outil Traducteur pour gérer les chaînes de caractères anglaises, ainsi que leurs traductions. Les dictionnaires sont créés dans le référentiel, par exemple, `/apps/myproject/i18n`.

L&#39;outil Traducteur et les dictionnaires que vous gérez servent à présenter l&#39;interface utilisateur des composants dans différentes langues. Si vous souhaitez traduire des pages, reportez-vous à [Traduction de contenu pour des sites multilingues](/help/sites-cloud/administering/translation/overview.md).

## Création d’un dictionnaire {#creating-a-dictionary}

Les développeurs peuvent créer des dictionnaires i18n dans AEM pour gérer les chaînes de composant localisées. Les dictionnaires font généralement partie du code du composant dans `/apps`. Voici un exemple du code AEM WKND avec une paire clé/valeur utilisée dans tous les composants WKND.

```
{
  "&copy; {0} WKND Site Site. All rights reserved." : "&copy; {0} WKND Site Site. Tous droits réservés."
}
```

L’équipe de développement peut créer des dictionnaires supplémentaires en ajoutant un nœud racine (`sling:Folder`) pour qu’un nouveau dictionnaire contienne les définitions de langue pour les chaînes de composant.

```shell
/apps/myProject/i18n [sling:Folder]
    - de.json [nt:file] [mix:language]
        + jcr:language = de
    - fr.json [nt:file] [mix:language]
        + jcr:language = fr
```

>[!NOTE]
>
>Il s’agit de la structure du [module Sling i18n](https://sling.apache.org/site/internationalization-support.html).

Une fois créés dans un référentiel AEM GitHub, les dictionnaires peuvent être déployés via un pipeline AEM [CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

## Emplacements du dictionnaire {#dictionary-locations}

Les développeurs sont libres de créer un dictionnaire de langue source dans `/apps` ou `/content/cq:i18n`. En commençant par l’exemple de code de l’archétype AEM, les dictionnaires initiaux se trouvent généralement dans le chemin d’accès `/apps`. Si l’objectif est de stocker les copies de langue du dictionnaire correspondantes également dans `/apps`, ces copies de langue doivent être créées et conservées manuellement par les développeurs dans le code du composant.

Sinon, le nouveau processus de traduction AEM Runtime pour les dictionnaires i18n crée les dictionnaires traduits dans `/content/cq:i18n/<projectName>`, que le dictionnaire source soit stocké dans `/apps` ou `/content`.

Les décisions relatives à l&#39;emplacement des dictionnaires i18n, des copies de source et de langue doivent être prises selon les critères suivants :

* `/apps`
   * emplacement par défaut des dictionnaires avec des traductions de chaînes de composant, en suivant l’archétype AEM et l’exemple de code WKND
   * ordre de rendu le plus élevé, par Sling ([hiérarchies de recherche de bundle de ressources](https://sling.apache.org/documentation/bundles/internationalization-support-i18n.html#resourcebundle-hierarchies))
   * mais aucune modification ni traduction de dictionnaires au moment de l’exécution n’est possible, car `/apps` est immuable dans les environnements AEM as a Cloud Service

* `/content/cq:i18n`
   * autre emplacement pour les dictionnaires i18n si
      * la traduction des dictionnaires au moment de l’exécution est requise
      * la possibilité de modifier un dictionnaire au moment de l’exécution est requise
   * emplacement par défaut où la traduction du dictionnaire d’exécution crée des copies de langue.

Étant donné que `/apps` remplace toujours `/content` dans l’ordre de rendu Sling, il est important de garder à l’esprit que les dictionnaires avec des paires clé/valeur identiques ne doivent pas exister simultanément dans `/apps` et `/content/cq:i18n`, car le dictionnaire dans `/content/cq:i18n` ne sera jamais utilisé pour le rendu. Si une copie de langue du dictionnaire, c’est-à-dire la destination de traduction, existe déjà dans `/apps` et que l’objectif est de la rendre traduisible au moment de l’exécution dans AEM as a Cloud Service, la copie de langue du dictionnaire d’origine dans `/apps` doit soit être déplacée vers `/content/cq:i18n`, soit être supprimée dans `/apps` et recréée automatiquement dans `/content/cq:i18n` en traduisant le dictionnaire source. Ce processus de traduction crée automatiquement les copies de langue dans `/content/cq:i18n`.

## Création automatique de dictionnaire {#automatic-creation}

Pour les pages AEM et les fragments d’expérience contenant des composants principaux AEM, le nouveau processus de traduction du dictionnaire analyse également ces pages ou fragments d’expérience à la recherche des composants et des chaînes de composant à traduire. Le système crée alors automatiquement les nouvelles copies de langue de dictionnaire correspondantes dans `/content/cq:i18n`. Cela ne s’applique pas aux fragments de contenu, car il s’agit de contenu pur et structuré sans utiliser les composants principaux AEM.

## Exportation d’un dictionnaire {#exporting-a-dictionary}

Bien que la traduction au moment de l’exécution des dictionnaires i18n à l’emplacement `/apps` ou `/libs` ne soit pas possible dans AEM as a Cloud Service, car ces emplacements sont immuables, ces dictionnaires peuvent toujours être exportés au moment de l’exécution pour une traduction asynchrone en dehors d’AEM.

Pour exporter les chaînes de langue source d&#39;un dictionnaire vers un fichier XLIFF :

1. Ouvrez l’outil de traduction `http://<host>:<port>/libs/cq/i18n/gui/translator.html`.

   >[!NOTE]
   >
   >L’outil n’est disponible que via cette URL et n’est pas accessible à partir de l’interface utilisateur du produit AEM.

1. Utilisez le menu déroulant Dictionnaires pour sélectionner le dictionnaire à exporter.
1. Cliquez sur Exporter une traduction XLIFF , puis sur Exporter une `<locale>` XLIFF complète.

## Importer un dictionnaire {#importing-a-dictionary}

Pour importer un fichier XLIFF dans un dictionnaire afin d’en remplir le contenu, procédez comme suit :

1. Ouvrez l’outil de traduction `http://<host>:<port>/libs/cq/i18n/gui/translator.html`.
1. Cliquez sur Importer , puis sur Traductions XLIFF.
1. Sélectionnez le fichier à importer et cliquez sur OK.

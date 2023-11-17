---
title: Configuration de l’intégration de traduction pour le contenu sans affichage
description: Découvrez comment connecter AEM à un service de traduction.
exl-id: c91b2701-7ede-4d0b-93dd-3636c6638be2
source-git-commit: e2505c0fec1da8395930f131bfc55e1e2ce05881
workflow-type: tm+mt
source-wordcount: '1229'
ht-degree: 93%

---

# Configuration de l’intégration de traduction {#configure-integration}

Découvrez comment connecter AEM à un service de traduction.

## Un peu d’histoire… {#story-so-far}

Dans le document précédent du parcours de traduction AEM, [Prise en main de la traduction découplée AEM](learn-about.md) vous avez appris à organiser votre contenu découplé et la manière dont fonctionnent les outils de traduction AEM et vous devriez maintenant :

* comprendre l’importance de la structure de contenu pour la traduction ;
* savoir comment AEM stocke du contenu découplé ;
* être familiarisé avec les outils de traduction AEM.

Cet article s’appuie sur ces principes de base afin que vous puissiez effectuer la première étape de configuration et configurer un service de traduction, que vous utiliserez ultérieurement dans le parcours pour traduire votre contenu.

## Objectif {#objective}

Ce document vous aide à comprendre comment configurer une intégration AEM au service de traduction de votre choix. Après avoir lu ce document, vous devriez :

* comprendre les paramètres importants de la structure d’intégration de traduction dans AEM ;
* savoir configurer votre propre connexion à votre service de traduction.

## Framework d’intégration de la traduction {#tif}

Le framework d’intégration de la traduction dans AEM s’intègre à des services de traduction tiers pour orchestrer la traduction du contenu d’AEM. Elle implique trois étapes de base.

1. Connectez-vous à un fournisseur de services de traduction.
1. Créez une configuration de framework d’intégration de traduction.
1. Associez la configuration à votre contenu.

Les sections suivantes décrivent ces étapes de manière plus détaillée.

## Connexion à un fournisseur de services de traduction {#connect-translation-provider}

La première étape consiste à choisir le service de traduction que vous souhaitez utiliser. Il existe de nombreux choix pour les services de traduction humaine et automatique, disponibles pour AEM. La plupart des fournisseurs proposent un package de traducteur à installer. Consultez la section [Ressources supplémentaires](#additional-resources) pour découvrir une sélection d’options disponibles.

>[!NOTE]
>
>Le spécialiste de traduction est généralement chargé de choisir le service de traduction à utiliser, mais l’administrateur est généralement chargé d’installer le package de connecteur de traduction requis.

Pour les besoins de ce parcours, nous utilisons Microsoft Translator à qui AEM fournit une licence d’évaluation prête à l’emploi. Consultez la section [Ressources supplémentaires](#additional-resources) pour plus d’informations sur ce fournisseur.

Si vous choisissez un autre fournisseur, votre administrateur doit installer le package de connecteur conformément aux instructions fournies par le service de traduction.

>[!NOTE]
>
>L’utilisation de Microsoft Translator prêt à l’emploi dans AEM ne nécessite pas de configuration supplémentaire et fonctionne en l’état sans configuration de connecteur supplémentaire.
>
>Si vous choisissez d’utiliser le connecteur Microsoft Translator à des fins de test, il n’est pas nécessaire d’effectuer les étapes des deux sections suivantes : [Création d’une configuration d’intégration de traduction](#create-config) et [Association de la configuration à votre contenu.](#associate) Il est toutefois conseillé de lire ces sections afin de vous familiariser avec les étapes de configuration de votre connecteur préféré.
>
>La licence d’évaluation du connecteur Microsoft Translator n’est pas destinée à la production. Si vous décidez de vous procurer une licence, l’administrateur ou l’administratrice système doit suivre les étapes présentées dans la section [Ressources supplémentaires](#additional-resources) à la fin de ce document pour configurer la licence.

## Création d’une configuration d’intégration de traduction {#create-config}

Une fois installé le package de connecteur correspondant au service de traduction choisi, vous devez créer une configuration de structure d’intégration de traduction pour ce service. La configuration contient les informations suivantes :

* Le fournisseur de service de traduction à utiliser
* Si une traduction humaine ou automatique doit être réalisée
* Si le contenu supplémentaire associé aux fragments de contenu tels que les balises doit être traduit

Pour créer une configuration de traduction :

1. Dans le menu de navigation globale, cliquez ou appuyez sur **Outils** > **Cloud Service** > **Cloud Service de traduction**.
1. Accédez à l’emplacement où vous souhaitez créer la configuration dans votre structure de contenu. Cet emplacement est souvent basé sur un projet en particulier, mais peut également être global.
   * Par exemple, dans ce cas, une configuration peut être effectuée globalement pour s’appliquer à tout le contenu, ou uniquement au projet WKND.

   ![Emplacement de configuration de traduction](assets/translation-configuration-location.png)

1. Fournissez les informations suivantes dans les champs requis, puis cliquez ou appuyez sur **Créer**.
   1. Sélectionnez **Type de configuration** dans la liste déroulante. Sélectionnez **Intégration de traduction** dans la liste.
   1. Indiquez un **Titre** pour votre configuration. Le **Titre** identifie la configuration dans la console **Services cloud**, ainsi que dans les listes déroulantes de propriétés de la page.
   1. Éventuellement, saisissez un **Nom** à utiliser pour le nœud du référentiel qui stocke la configuration.

   ![Créer une configuration de traduction](assets/create-translation-configuration.png)

1. Appuyez ou cliquez sur **Créer** et la fenêtre **Modifier la configuration**, dans laquelle vous pouvez configurer les propriétés de configuration.

1. N’oubliez pas que les fragments de contenu sont stockés en tant que ressources dans AEM. Appuyez ou cliquez sur l’onglet **Ressources**.

![Propriétés de Configuration de traduction](assets/translation-configuration.png)

1. Fournissez les informations suivantes.

   1. **Méthode de traduction** : sélectionnez **Traduction automatique** ou **Traduction humaine** selon votre fournisseur de traduction. Pour les besoins de ce parcours, nous supposons la traduction sera automatique.
   1. **Fournisseurs de traduction** : sélectionnez dans la liste le connecteur que vous avez installé pour votre service de traduction.
   1. **Catégorie de contenu** : sélectionnez la catégorie la plus appropriée pour mieux cibler la traduction (uniquement pour la traduction automatique).
   1. **Traduire les ressources de fragments de contenu** : cochez cette case pour traduire les ressources associées aux fragments de contenu.
   1. **Traduire les ressources** : cochez cette case pour traduire les ressources.
   1. **Traduire les métadonnées** : cochez cette option pour traduire les métadonnées des ressources.
   1. **Traduire les balises** : cochez cette case pour traduire les balises associées à la ressource.
   1. **Exécuter automatiquement la traduction** : cochez cette propriété si vous souhaitez que les traductions soient automatiquement envoyées à votre service de traduction.
   1. **Désactiver Traduction uniquement des champs mis à jour** - Lorsque cette option est cochée, la mise à jour du projet de traduction envoie tous les champs traduisibles pour traduction, et pas seulement ceux qui ont été modifiés depuis la dernière traduction. La mise à jour de votre projet de traduction est traitée ultérieurement dans le parcours.
   1. **Activer les champs de modèle de contenu pour la traduction** - Cochez cette option pour que la configuration de traduction reconnaisse automatiquement les champs des modèles de contenu en fonction de l’indicateur **Traduisible**.

1. Appuyez et cliquez sur **Enregistrer et fermer**.

Vous avez maintenant configuré le connecteur pour votre service de traduction.

## Association de la configuration à votre contenu {#associate}

AEM est un outil flexible et puissant qui prend en charge plusieurs services de traduction simultanés via plusieurs connecteurs et plusieurs configurations. Le paramétrage d’une telle configuration dépasse le cadre de ce parcours. Toutefois, cette flexibilité signifie que vous devez spécifier les connecteurs et la configuration à utiliser pour traduire votre contenu en associant cette configuration à votre contenu.

Pour ce faire, accédez à la racine de langue de votre contenu. Dans notre exemple, elle correspond à

```text
/content/dam/<your-project>/en
```

1. Accédez à la navigation globale et accédez à **Navigation** -> **Ressources** -> **Fichiers**.
1. Dans la console Ressources, sélectionnez la racine de langue à configurer et cliquez ou appuyez sur **Propriétés**.
1. Appuyez ou cliquez sur l’onglet **Services cloud**.
1. Sous **Configurations des services cloud** dans la liste déroulante **Ajouter une configuration**, sélectionnez votre connecteur. Il doit s’afficher dans la liste déroulante lorsque vous avez installé son package comme [décrit précédemment.](#connect-translation-provider)
1. Sous **Configurations des services cloud** dans la liste déroulante **Ajouter une configuration**, sélectionnez également votre configuration.
1. Appuyez et cliquez sur **Enregistrer et fermer**.

![Sélection des configurations de services cloud](assets/select-cloud-service-configurations.png)

## Prochaines étapes {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de traduction découplée, vous devriez savoir :

* comprendre les paramètres importants de la structure d’intégration de traduction dans AEM ;
* savoir configurer votre propre connexion à votre service de traduction.

Tirez parti de ces connaissances et continuez votre parcours de traduction AEM sans interface utilisateur graphique en consultant le document. [Traduire le contenu,](translation-rules.md) où vous apprenez à utiliser votre configuration jusqu’à présent pour traduire réellement votre contenu.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de traduction découplée en examinant le document [Configuration des règles de traduction](translation-rules.md), vous trouverez ci-après quelques ressources facultatives supplémentaires pour approfondir un certain nombre de concepts mentionnés dans ce document, même s’ils ne sont pas nécessaires pour poursuivre le parcours en mode découplé.

* [Configuration de le framework d’intégration de traduction](/help/sites-cloud/administering/translation/integration-framework.md) : consultez la liste des connecteurs de traduction sélectionnés et apprenez à configurer le framework d’intégration de traduction pour l’intégration à des services de traduction tiers.
* [Connexion à Microsoft Translator](/help/sites-cloud/administering/translation/connect-ms-translator.md) : AEM fournit un compte d’évaluation de traduction Microsoft à des fins de test.

---
title: Connexion à Microsoft Translator
description: Découvrez comment connecter AEM à Microsoft Translator prêt à l'emploi pour automatiser votre processus de traduction.
feature: Language Copy
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 41%

---


# Connexion à Microsoft Translator {#connecting-to-microsoft-translator}

Créez une configuration pour le service cloud [Microsoft Translator](https://hub.microsofttranslator.com) afin d’utiliser votre compte Microsoft Translation pour traduire AEM contenu ou ressources de page.

>[!NOTE]
>
>AEM fournit un compte d&#39;essai Microsoft Translation qui permet un maximum de 2 000 000 caractères traduits gratuits par mois. Pour obtenir un abonnement de compte adapté aux systèmes de production, voir [Mise à niveau de la configuration de la licence d’évaluation de Microsoft Translator](#upgrading-the-microsoft-translator-trial-license-configuration).

| Propriété | Description |
|---|---|
| Libellé de traduction | Nom d’affichage du service de traduction |
| Attribution de traduction | (Facultatif) Pour le contenu généré par l’utilisateur, attribution qui s’affiche en regard du texte traduit, par exemple `Translations by Microsoft` |
| ID d’espace de travail | (Facultatif) ID de votre moteur Microsoft Translator personnalisé à utiliser |
| Clé d’abonnement | Votre clé d’abonnement Microsoft pour Microsoft Translator |

Après avoir créé la configuration, vous devez [l&#39;activer](#activating-the-translator-service-configurations).

La procédure suivante crée une configuration Microsoft Translator.

1. Dans le panneau de navigation [, ](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) cliquez ou appuyez sur **Outils** -> **Cloud Services** -> **Cloud Services de traduction**.
1. Accédez à l’emplacement où vous souhaitez créer la configuration. Normalement, il s&#39;agit de la racine de votre site ou il peut s&#39;agir d&#39;une configuration globale par défaut.
1. Appuyez ou cliquez sur le bouton **Créer**.
1. Définissez votre configuration.
   1. Sélectionnez **Microsoft Translator** dans la liste déroulante.
   1. Indiquez un titre pour votre configuration. Le titre identifie la configuration dans la console Services cloud, ainsi que dans les listes déroulantes de propriétés de la page.
   1. Éventuellement, saisissez un nom à utiliser pour le nœud du référentiel qui stocke la configuration.

   ![Créer une configuration de traduction](../assets/create-translation-config.png)

1. Cliquez sur **Créer**.
1. Dans la fenêtre **Modifier la configuration**, indiquez les valeurs du service de traduction décrit dans le tableau précédent.

   ![Modifier la configuration de traduction](../assets/edit-translation-config.png)

1. Appuyez ou cliquez sur **Se connecter** pour vérifier la connexion.
1. appuyer et cliquer sur **Enregistrer et fermer**.

## Mise à niveau de la configuration Licence d’évaluation de Microsoft Translator {#upgrading-the-microsoft-translator-trial-license-configuration}

Les pages de configuration Microsoft Traduction fournissent un lien pratique vers le site web Microsoft pour obtenir un abonnement de compte qui est adapté aux systèmes de production.

1. Dans le panneau de navigation [, ](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) appuyez ou cliquez sur **Outils** -> **Cloud Services** -> **Cloud Services de traduction**.
1. Appuyez ou cliquez sur votre configuration Microsoft Translator existante.
1. Appuyez ou cliquez sur **Modifier**.
1. Dans la fenêtre **Modifier la configuration**, appuyez ou cliquez sur **Abonnement de mise à niveau**. Une page Web Microsoft contenant des détails supplémentaires sur le service s’ouvre.

## Personnalisation de votre moteur Microsoft Translator {#customizing-your-microsoft-translator-engine}

Les pages de configuration de Microsoft Traduction fournissent un lien pratique vers le site web Microsoft pour personnaliser votre moteur Microsoft Translator.

1. Dans le panneau de navigation [, ](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) appuyez ou cliquez sur **Outils** -> **Cloud Services** -> **Cloud Services de traduction**.
1. Appuyez ou cliquez sur votre configuration Microsoft Translator existante.
1. Appuyez ou cliquez sur **Modifier**.
1. Dans la fenêtre **Modifier la configuration**, appuyez ou cliquez sur **Personnaliser le traducteur**. Utilisez la page web de Microsoft qui s’ouvre pour personnaliser votre service.

## Activation des configurations du service de traducteur {#activating-the-translator-service-configurations}

Vous devez activer les configurations de service cloud pour prendre en charge le contenu traduit qui est répliqué vers l’instance de publication. Utilisez la méthode de [publication d&#39;une arborescence](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-and-unpublishing-a-tree) pour activer les noeuds de référentiel qui stockent les configurations Microsoft Translator. Les nœuds se trouvent sous les nœuds parents suivants :

* `/libs/settings/cloudconfigs/translation/msft-translation`

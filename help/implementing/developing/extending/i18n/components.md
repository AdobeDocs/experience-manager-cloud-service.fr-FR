---
title: Internationalisation de composants
description: Internationalisez vos composants et boîtes de dialogue afin que leurs chaînes d’interface utilisateur puissent être présentées dans différentes langues.
topic-tags: components
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: b55f7260628f759de2718290624cdc82da7a2961
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 83%

---

# Internationalisation de composants{#internationalizing-components}

Internationalisez vos composants et boîtes de dialogue afin que leurs chaînes d’interface utilisateur puissent être présentées dans différentes langues. Les composants conçus pour l’internationalisation permettent d’externaliser, de traduire et d’importer les chaînes de l’interface utilisateur dans le référentiel. Au moment de l’exécution, les préférences linguistiques de l’utilisateur ou de l’utilisatrice ou les paramètres régionaux de la page déterminent la langue affichée dans l’interface utilisateur.

![i18n-components-1.png](/help/implementing/developing/extending/assets/i18n-comp1.png)

Procédez comme suit pour internationaliser vos composants et proposer l’interface utilisateur dans différentes langues :

1. [Mettez en œuvre vos composants à l’aide d’un code qui internationalise les chaînes.](/help/implementing/developing/extending/i18n/dev.md) Votre code identifie les chaînes à traduire et sélectionne la langue à présenter au moment de l’exécution.
1. Créez des dictionnaires et ajoutez les chaînes anglaises à traduire.
1. Exportez le dictionnaire au format XLIFF, traduisez les chaînes, puis réimportez les fichiers XLIFF dans AEM.
1. Insérez le dictionnaire dans le processus de gestion des versions de votre application.

>[!NOTE]
>
>Les méthodes décrites ici pour internationaliser des composants sont destinées à traduire des chaînes statiques. Si les chaînes d’un composant sont susceptibles de changer, vous devriez utiliser les workflows de traduction traditionnels. Par exemple, lorsque les auteurs et autrices peuvent modifier une chaîne de l’interface utilisateur à l’aide de propriétés dans la boîte de dialogue Modifier d’un composant, vous ne devez pas utiliser de dictionnaire de langue pour internationaliser la chaîne.

## Dictionnaires de langues {#language-dictionaries}

Le framework d’internationalisation d’AEM utilise des dictionnaires dans le référentiel pour stocker les chaînes en anglais et leurs traductions dans d’autres langues. Le framework utilise l’anglais comme langue par défaut. Les chaînes sont identifiées à l’aide de leur version anglaise. En règle générale, les structures d’internationalisation utilisent des ID alphanumériques pour les chaînes de l’IU. L’utilisation de la version anglaise de la chaîne comme identifiant présente plusieurs avantages :

* Le code est facile à lire.
* La langue par défaut est toujours disponible.

Les modifications de traduction doivent provenir de Git via le [pipeline CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) dans AEM as a cloud service.

![i18n-components-2](/help/implementing/developing/extending/assets/i18n-comp2.png)


### Remplacement de chaînes dans les dictionnaires système {#overlaying-strings-in-system-dictionaries}

Si vos composants utilisent des chaînes qui sont incluses dans les dictionnaires système AEM, dupliquez la chaîne dans votre propre dictionnaire. Tous les composants utiliseront les chaînes de votre dictionnaire.

Notez que vous ne pouvez pas prédire quelle traduction est utilisée lorsque des chaînes sont dupliquées dans les dictionnaires qui se trouvent tous sous le nœud `/apps`.

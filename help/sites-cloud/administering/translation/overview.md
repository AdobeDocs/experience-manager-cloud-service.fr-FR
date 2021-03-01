---
title: Traduction de contenu pour les sites multilingues
description: Bénéficiez d'un aperçu de la manière de traduire du contenu pour les sites multilingues.
translation-type: tm+mt
source-git-commit: 4fc4dbe2386d571fa39fd6d10e432bb2fc060da1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 61%

---


# Traduction de contenu pour les sites multilingues {#translating-content-for-multilingual-sites}

Automatisez la traduction du contenu et des ressources des pages pour créer et gérer des sites Web multilingues. Pour automatiser les processus de traduction, vous intégrez des fournisseurs de services de traduction à AEM et vous créez des projets pour traduire le contenu dans plusieurs langues. AEM prend en charge les workflows de traduction humaine et automatique.

* **Traduction humaine :** Le contenu est envoyé à votre fournisseur de traduction et traduit par des traducteurs professionnels. Une fois la traduction terminée, le contenu traduit est renvoyé et importé dans AEM. Lorsque votre fournisseur de traduction est intégré à AEM, le contenu est automatiquement transféré entre AEM et le fournisseur de traduction.
* **Traduction automatique :** Le service de traduction automatique traduit immédiatement votre contenu.

La traduction du contenu implique les étapes suivantes :

1. [Connectez AEM à votre fournisseur de service de traduction](integration-framework.md#connecting-to-a-translation-service-provider) et [créez des configurations de structure d’intégration de traduction](integration-framework.md).
1. [Associer les pages de votre gabarit de langue](integration-framework.md#configuring-pages-for-translation) au service de traduction et aux configurations de structure.
1. [Identifiez le type de ](rules.md) contenu à traduire.
1. [Préparez le contenu à traduire](preparation.md) en créant le gabarit de langue et les pages racine des copies de langue.
1. [Créez des ](managing-projects.md) projets de traduction pour rassembler le contenu à traduire et préparer le processus de traduction.
1. Utiliser les projets de translation pour [gérer le processus de traduction du contenu](managing-projects.md).

Si votre fournisseur de services de traduction ne fournit pas de connecteur pour l’intégration à AEM, AEM prend en charge l’extraction et la réinsertion manuelles du contenu de translation au format XML.

>[!NOTE]
>
>Votre utilisateur doit être membre du groupe `project-administrators` pour utiliser les fonctionnalités de copie de langue.

## Bonnes pratiques {#best-practices}

La page [Bonnes pratiques de traduction](best-practices.md) contient des informations importantes concernant votre implémentation.

---
title: Traduction de contenu pour les sites multilingues
description: Bénéficiez d’un aperçu de la traduction de contenu pour les sites multilingues.
feature: Language Copy
role: Admin
exl-id: c3e89719-4d08-401b-b9dd-19d1db03d72c
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 82%

---

# Traduction de contenu pour les sites multilingues {#translating-content-for-multilingual-sites}

Automatisez la traduction du contenu de pages et de ressources pour créer et tenir à jour des sites web multilingues. Pour automatiser les processus de traduction, vous intégrez des fournisseurs de services de traduction à AEM et vous créez des projets pour traduire le contenu dans plusieurs langues. AEM prend en charge les workflows de traduction humaine et automatique.

* **Traduction humaine :** le contenu est envoyé à votre fournisseur de traduction et traduit par des traducteurs professionnels. Une fois la traduction terminée, le contenu traduit est renvoyé et importé dans AEM. Lorsque votre fournisseur de traduction est intégré à AEM, le contenu est automatiquement transféré entre AEM et le fournisseur de traduction.
* **Traduction automatique :** le service de traduction automatique traduit immédiatement votre contenu.

>[!TIP]
>
>Si vous êtes un débutant dans la traduction de contenu, reportez-vous à la section [Parcours de traduction de sites](/help/journey-sites/translation/overview.md), qui vous guide sur le chemin de la traduction de votre contenu AEM Sites à l’aide d’AEM de puissants outils de traduction, idéaux pour ceux qui ne disposent pas d’une expérience concernant AEM ou la traduction.

La traduction du contenu implique les étapes suivantes :

1. [Connectez AEM à votre fournisseur de service de traduction](integration-framework.md#connecting-to-a-translation-service-provider) et [créez des configurations de structure d’intégration de traduction](integration-framework.md).
1. [Associer les pages de votre gabarit de langue](integration-framework.md#configuring-pages-for-translation) au service de traduction et aux configurations de structure.
1. [Identifier le type de contenu](rules.md) à traduire.
1. [Préparez le contenu à traduire](preparation.md) en créant le gabarit de langue et les pages racine des copies de langue.
1. [Créez des projets de traduction](managing-projects.md) pour collecter le contenu à traduire et préparer le processus de traduction.
1. Utilisez les projets de translation pour [gérer le processus de traduction du contenu](managing-projects.md).

Si votre fournisseur de services de traduction ne fournit pas de connecteur pour l’intégration avec AEM, AEM prend en charge l’extraction et la réinsertion manuelles du contenu de traduction au format XML.

>[!NOTE]
>
>Votre utilisateur doit être membre du groupe `project-administrators` pour utiliser les fonctionnalités de copie de la langue.

## Bonnes pratiques {#best-practices}

La page [Bonnes pratiques de traduction](best-practices.md) fournit des informations importantes concernant votre mise en œuvre.

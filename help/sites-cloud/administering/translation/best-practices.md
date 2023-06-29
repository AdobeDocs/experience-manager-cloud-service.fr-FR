---
title: Bonnes pratiques de traduction
description: Découvrez les bonnes pratiques compilées par les équipes d’ingénierie et de consulting d’Adobe qui vous aideront à mener à bien vos projets de traduction.
feature: Language Copy
role: Admin
exl-id: 51b98c24-5566-4088-9010-bd39841a1633
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 63%

---

# Bonnes pratiques de traduction {#translation-best-practices}

>[!TIP]
>
>Si vous commencez à traduire du contenu, reportez-vous à la section [Parcours de traduction de sites,](/help/journey-sites/translation/overview.md) qui est un chemin guidé à travers la traduction de votre contenu AEM Sites à l’aide AEM outils de traduction puissants, idéal pour ceux qui n’ont pas d’AEM ou d’expérience de traduction.

## Général {#general}

La création ou le développement d’une présence mondiale sur le web peut être un processus complexe. Toutefois, avec une bonne préparation et planification, AEM peut simplifier vos efforts et soutenir les objectifs internationaux de votre entreprise.

* **Planifiez votre expansion internationale** avant de mettre en œuvre votre premier site. L’adaptation d’un site existant pour une couverture globale lorsque le site a été mis en oeuvre à court terme est généralement plus difficile que la planification d’une expansion globale au début :
   * Évaluez l’état actuel de la maturité de localisation de votre entreprise. Déterminez si vous disposez des **outils**, **processus** et **ressources** nécessaires pour prendre en charge une expansion internationale.
   * Tenez compte des **réglementations internationales** et des **préférences linguistiques régionales**. Concevez des structures de contenu et des processus flexibles qui peuvent s’adapter à un environnement professionnel global en constante évolution.
* Déterminez un modèle de **gouvernance** soutenant votre activité globale et utilisez des mécanismes AEM comme MSM et les permissions d’utilisateur afin d’appliquer le modèle sélectionné. Par exemple, déterminez si le contenu est créé de manière centralisée et &quot;envoyé&quot; ou &quot;extrait&quot; vers les régions/pays. Déterminez le contenu qui peut être déverrouillé et modifié dans les zones géographiques. Déterminer qui est chargé de lancer et de gérer les traductions.
* Si les ressources le permettent, il est préférable de gérer l’activité de traduction à partir d’une équipe centrale qui peut développer l’expertise dans les outils, processus et relations avec les fournisseurs nécessaires.
* **Planifiez**, **prototypez** et **testez** votre structure et vos processus globaux en vous assurant qu’ils soutiennent votre activité et que vous bénéficiez de l’appui nécessaire de la part des parties prenantes des différentes zones géographiques.

## Structure du site {#site-structure}

* Lors de la conception de la structure de votre site, commencez par examiner votre contenu et déterminer où et dans quelle langue il est rédigé. Cet emplacement doit correspondre au niveau supérieur de votre site.
* Il est recommandé d’adopter une **structure basée sur les langues** ne comportant pas de plus de 3 niveaux entre le niveau supérieur auteur et les sites des pays.
* Utilisez une convention de dénomination des langues/sites des pays qui suit les **[normes W3C](/help/sites-cloud/authoring/fundamentals/accessible-content.md)**.
* Déterminez la manière dont le contenu est distribué par les pays et les régions. Pensez aux pays qui partagent des langues. Il est recommandé de créer des gabarits de langue, un calque de pages non activées, où le contenu traduit peut être révisé et modifié, puis envoyé ou extrait vers un site de pays partageant cette langue.
* Il existe deux méthodes pour créer des gabarits de langue : à l’aide de copies de langue et de MSM/Live Copies.
   * L’approche impliquant des copies de langue est celle utilisée par la structure d’intégration de traduction prête à l’emploi d’AEM. C’est par conséquent la façon la plus facile de démarrer. Ce framework fournit une interface utilisateur qui permet, dès le départ, de propager et de traduire facilement les modifications du contenu du gabarit de langue principal (par exemple, l’anglais) sur les gabarits de langue. Cependant, à mesure que le projet se développe, l’automatisation des workflows devient de plus en plus nécessaire pour gérer la traduction du nombre croissant de pages et/ou de langues.
   * L’utilisation de MSM/Live Copies peut être une alternative pour les cas d’utilisation avancés, où les sites sont plus grands et plus complexes. Une gouvernance solide et l’automatisation des workflows sont nécessaires dès le départ pour gérer les relations d’héritage complexes entre le gabarit de langue anglaise et les autres gabarits de langue, et pour réduire les risques de remplacement des traductions existantes. Cette gestion est possible grâce à des connecteurs de traduction. Consultez [MSM et sites multilingues](/help/sites-cloud/administering/msm/best-practices.md#msm-and-multilingual-websites) pour plus d’informations.
* Si votre langue principale possède des variations globales, vous pouvez utiliser MSM pour créer une Live Copy à partir du gabarit global à utiliser pour la traduction. Par exemple, si la création globale est effectuée dans un gabarit anglais américain, créez un gabarit anglais international en tant que Live Copy et créez une base de traduction dans d’autres langues.
* Utilisez MSM pour créer des sites de pays à partir des gabarits de langue traduits et déployer le contenu sur les sites partageant la même langue. Par exemple, le gabarit de langue française peut être déployé sur les sites de France, de Belgique et de Suisse.
* Planifiez, prototypez et testez d’abord, avant de commencer la mise en oeuvre.

## Processus et méthodes de traduction {#translation-processes-and-methods}

* Faites appel à un **prestataire de services de localisation (LSP en anglais)** habitué aux tâches de traduction et maîtrisant les activités de localisation associées. Les LSP peuvent vous aider à dimensionner votre entreprise globale en fournissant un large éventail de ressources et de technologies pour améliorer l’efficacité et réduire les coûts de traduction :
   * Certains LSP sont à la fois des fournisseurs de services et de technologie. Il existe également des fournisseurs de technologie autonomes qui permettent à de nombreux LSP de participer à leurs plateformes de traduction.
   * La **structure de traduction AEM** prend en charge l’intégration à différents fournisseurs de technologie de traduction pour la traduction humaine et automatique.
   * Découvrez comment [intégrer les connecteurs de LSP à votre système AEM](integration-framework.md) pour automatiser la traduction du contenu ou comment créer, exporter et importer manuellement des projets de traduction pour les tests ou dans le cas où il n’y a aucun fournisseur de technologie de traduction ou LSP.
* Sélectionnez la **méthode de traduction** qui convient le mieux au contenu.
   * La **traduction humaine** est idéale pour le contenu où les attentes en matière de message et de qualité sont élevées, ainsi que pour le contenu destiné à rester longtemps sur le site, tel que celui des pages marketing.
   * La **traduction automatique** peut être un bon choix pour les grands volumes de traduction lorsque les délais de publication sont critiques, que les attentes en matière de qualité sont moindres ou que les coûts de traduction humaine sont prohibitifs. La base de connaissances de prise en charge et le contenu généré par les utilisateurs sont généralement traduits par la machine.
* Faites appel à l’expertise des fournisseurs de services de localisation, des conseillers en Adobe et des intégrateurs de système pour planifier, prototyper et tester votre structure de site multilingue.

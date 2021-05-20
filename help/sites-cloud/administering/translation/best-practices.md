---
title: Meilleures pratiques de traduction
description: Découvrez les bonnes pratiques compilées par les équipes d’ingénierie et de conseil d’Adobe pour vous aider à démarrer et à exécuter des projets de traduction.
feature: Copie de la langue
role: Administrator
exl-id: 51b98c24-5566-4088-9010-bd39841a1633
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 72%

---

# Meilleures pratiques de traduction {#translation-best-practices}

## Général {#general}

La création ou le développement d’une présence mondiale sur le web peut être un processus complexe. Toutefois, avec une bonne préparation et planification, AEM peut simplifier vos efforts et soutenir les objectifs internationaux de votre entreprise.

* **Planifiez l’** extension globale avant de mettre en oeuvre votre premier site. L’adaptation d’un site existant pour une couverture globale lorsque le site a été mis en œuvre très rapidement est en général plus difficile que la planification de l’expansion globale dès le début :
   * Évaluez l’état de maturité actuel de votre organisation en termes de localisation. Déterminez si les **outils**, **processus** et **ressources** sont en place pour prendre en charge l’expansion globale.
   * Tenez compte des **réglementations mondiales** et des **préférences linguistiques régionales**. Concevez des structures de contenu et des processus flexibles qui peuvent s’adapter à un environnement professionnel global en constante évolution.
* Déterminez un modèle de **gouvernance** qui prend en charge votre activité globale et utilisez des mécanismes d’AEM tels que MSM et les autorisations utilisateur pour appliquer le modèle de votre choix. Par exemple, déterminez si le contenu sera créé de manière centralisée et &quot;envoyé&quot; ou &quot;transmis&quot; vers les régions/pays. Déterminez le contenu qui peut être déverrouillé et modifié dans les zones géographiques. Déterminez qui est responsable du lancement et de la gestion des traductions.
* Si les ressources le permettent, il est préférable de gérer l’activité de traduction avec une équipe centrale qui peut développer une expertise dans les outils, les processus et les relations avec les fournisseurs nécessaires.
* **Planifiez**,  **** prototypez et  **** testez votre structure et vos processus globaux pour vous assurer qu’ils prennent en charge l’entreprise et que vous avez l’assistance requise des parties prenantes dans les zones géographiques.

## Structure du site  {#site-structure}

* Lors de la conception de la structure de votre site, commencez par examiner votre contenu et déterminer où et dans quelle langue il est rédigé. Cet emplacement doit être le niveau supérieur de votre site.
* La meilleure pratique consiste à adopter une **structure basée sur les langues** ne comportant pas de plus de 3 niveaux entre le niveau supérieur de rédaction et les sites des pays.
* Utilisez une convention de dénomination des langues/sites des pays qui suit les **[standards W3C.](/help/sites-cloud/authoring/fundamentals/accessible-content.md)**
* Déterminez la manière dont le contenu est distribué par les pays et les régions. Pensez aux pays qui partagent des langues. Il est recommandé de créer des gabarits de langue, une couche de pages non activées, où le contenu traduit peut être révisé et modifié, puis transmis ou extrait vers un site de pays partageant cette langue.
* Il existe deux approches pour créer des gabarits de langue : l’utilisation de copies de langue ou de MSM/Live Copies.
   * L’approche impliquant des copies de langue est celle utilisée par la structure d’intégration de traduction prête à l’emploi d’AEM. C’est par conséquent la façon la plus facile de démarrer. La structure fournit une interface utilisateur qui permet, dès le départ, de propager et de traduire facilement les modifications du contenu du gabarit de langue principal (par exemple, l’anglais) et les propager sur les gabarits de langue. Toutefois, au fur et à mesure que le projet se développe, l’automatisation des workflows devient de plus en plus nécessaire pour gérer la traduction du nombre plus important de pages et/ou de langues.
   * L’utilisation de MSM/Live Copies peut être une alternative pour les cas d’utilisation avancés, où les sites sont plus grands et plus complexes. Une gouvernance solide et l’automatisation des workflows sont nécessaires dès le départ pour gérer les relations d’héritage complexes entre le gabarit de langue anglaise et les autres gabarits de langue, et pour réduire les risques de remplacement des traductions existantes. Cette gestion est possible grâce à des connecteurs de traduction. Voir [MSM et sites multilingues](/help/sites-cloud/administering/msm/best-practices.md#msm-and-multilingual-websites) pour plus d’informations.
* Si votre langue principale possède des variations globales, vous pouvez utiliser MSM pour créer une Live Copy à partir du gabarit global à utiliser pour la traduction. Si, par exemple, la rédaction globale est effectuée dans un gabarit en anglais américain, créez un gabarit en anglais international en tant que Live Copy qui servira de base pour la traduction dans d’autres langues.
* Utilisez MSM pour créer des sites de pays à partir des gabarits de langue traduits et déployer le contenu sur les sites partageant la même langue. Par exemple, le gabarit de langue française peut être déployé sur les sites de France, de Belgique et de Suisse.
* Planifiez, prototypez et testez avant de lancer la mise en œuvre.

## Processus et méthodes de traduction  {#translation-processes-and-methods}

* Faire appel à un **fournisseur de services de localisation (LSP)** ayant une expertise dans les activités de traduction et de localisation associées. Les LSP peuvent vous aider à ajuster l’échelle de votre activité internationale en fournissant un éventail de ressources et de technologies pour accroître l’efficacité et économiser sur les coûts de traduction :
   * Certains LSP sont à la fois des fournisseurs de services et de technologie. Il existe également des fournisseurs de technologie autonomes qui permettent à plusieurs LSP de participer à leur plateforme de traduction.
   * La **structure de traduction AEM** prend en charge l’intégration à divers fournisseurs de technologies de traduction pour la traduction automatique et humaine.
   * Découvrez comment [intégrer les connecteurs de LSP à votre système AEM](integration-framework.md) pour automatiser la traduction du contenu ou comment créer, exporter et importer manuellement des projets de traduction pour les tests ou dans le cas où il n’y a aucun fournisseur de technologie de traduction ou LSP.
* Choisissez une **méthode de traduction** qui convient le mieux au contenu.
   * **La** traduction humaine est la mieux adaptée aux contenus dont les attentes en termes de qualité et de messagerie sont élevées et dont le contenu restera quelque temps sur le site, comme les pages marketing.
   * **La** traduction automatique peut être un bon choix pour des volumes massifs de traduction lorsque le temps de publication est critique, que les attentes en matière de qualité sont détendues ou que les coûts de traduction humaine sont prohibitifs. La base de connaissances de support et le contenu généré par l’utilisateur sont généralement traduits par ordinateur.
* Appuyez-vous sur l’expérience des prestataires de services de localisation, ainsi que sur celle des consultants et des intégrateurs système d’Adobe pour planifier, prototyper et tester la structure de votre site multilingue.

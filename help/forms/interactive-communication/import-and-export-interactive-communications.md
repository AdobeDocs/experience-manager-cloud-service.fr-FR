---
title: Importer et exporter une communication interactive
description: La communication interactive d’import et d’export permet aux utilisateurs de migrer, de réutiliser et de gérer facilement les communications entre les environnements.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 371838c77beafa8c67259a865b25325632bea0b0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 14%

---


# Importer et exporter une communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

La fonctionnalité d’importation et d’exportation de la communication interactive permet aux utilisateurs de migrer, de réutiliser et de gérer facilement les communications entre les environnements. Il vous permet d’exporter une communication interactive (IC) ainsi que ses fragments et modèles de données associés d’un environnement et de l’importer dans un autre, ce qui garantit la cohérence et réduit la duplication des efforts pendant le déploiement.

## Principaux avantages

- Simplifie la migration des CI entre les environnements.
- Préserve les fragments, les modèles de données et les dépendances.
- Réduit les efforts de recréation des CI entre les projets.

## Importer et exporter une communication interactive

Créez une communication interactive (CI) dans un environnement et réutilisez-la dans un autre en l’exportant et en l’important en procédant comme suit :

+++&#x200B;1. Comment exporter une communication interactive

1.1. Sélectionnez une [communication interactive créée](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/interactive-communication/create-interactive-communication) (IC).
1.2. Cliquez sur l’option **Télécharger** pour l’exporter sous la forme d’un fichier ZIP.
1.3. Le fichier ZIP téléchargé comprend le CI avec son **modèle**, **fragments** et **modèle de données** sélectionné.

![Rechercher un document IC](/help/forms/interactive-communication/assets/downloadic.png)
+++

+++&#x200B;2. Importer une communication interactive

2.1. Accédez à l’environnement cible.
2.2. Accédez à **Forms > Forms et Documents > Créer > Chargement de fichier**.
2.3. Chargez le fichier ZIP pour **importer** l’ID.

![Rechercher un document IC](/help/forms/interactive-communication/assets/uploadfile.png)

2.4. Après le chargement, l’IC apparaît avec ses fragments et son modèle de données associés.

![Rechercher un document IC](/help/forms/interactive-communication/assets/importfragment.png)
+++

+++&#x200B;3. Importer et exporter un fragment

3.1. Pour exporter, sélectionnez le fragment requis dans **Forms > Forms et documents**, puis cliquez sur **Télécharger** pour l’exporter sous la forme d’un fichier ZIP.

3.2. Pour importer, accédez à l’environnement cible, puis à Forms > Forms et Documents > Créer > **Chargement de fichier** et chargez le fichier ZIP exporté.

Cela permet une réutilisation facile des fragments dans différents environnements, assurant ainsi la cohérence de la conception et réduisant la duplication des efforts.
+++

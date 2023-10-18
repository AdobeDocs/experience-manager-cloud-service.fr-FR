---
title: Utilisation du Transformateur de contenu
description: Découvrez comment transformer votre structure de contenu en vue de la migration vers AEM as a Cloud Service.
exl-id: 40516ff7-5686-42e6-bdd1-c9c6de432b09
source-git-commit: 0109cea1be85e647fb6c04dde4714b162bdc75a5
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 93%

---

# Utilisation du Transformateur de contenu {#using-ct}

## Points importants concernant l’utilisation du Transformateur de contenu {#imp-considerations-ct}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour l’exécution du Transformateur de contenu (CT) :

* Pour utiliser le Transformateur de contenu, vous devez d’abord exécuter Best Practices Analyzer (BPA) dans votre environnement Adobe Experience Manager (AEM).
* Bien que vous puissiez exécuter le Transformateur de contenu dans votre environnement de production, il est recommandé de l’exécuter sur un clone de celui-ci. Plus important encore, vous devez vous assurer que BPA et le CT sont exécutés sur le même environnement.
* Vous devez avoir les droits d’administration de l’environnement dans lequel vous souhaitez exécuter le Transformateur de contenu.
* Toute opération pouvant modifier le contenu source (déplacer/supprimer/renommer) crée par défaut un package de sauvegarde des chemins sources sous `/etc/packages/content-transformation` avant la transformation. Bien que chaque boîte de dialogue d’opération dispose d’une option pour désactiver/activer la création de package de sauvegarde, il est strictement recommandé de toujours activer la création de package.
* Chaque page du Transformateur de contenu est configurée pour répertorier un maximum de 50 résultats. Par conséquent, un maximum de 50 résultats peuvent être transformés à la fois. Cela permet de fournir une réponse en temps voulu sur l’interface utilisateur.

## Disponibilité {#availability-ct}

Le Transformateur de contenu est fourni avec l’[Outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) qui peut être téléchargé sous la forme d’un fichier zip à partir du portail de distribution logicielle. Vous pouvez installer le package par le biais du gestionnaire de modules sur votre instance AEM source.

>[!NOTE]
>Le Transformateur de contenu est disponible avec l’Outil de transfert de contenu version 2.0.20 ou ultérieure.

## Ouverture du Transformateur de contenu {#opening-ct}

1. Connectez-vous à l’instance AEM source en tant qu’administrateur ou administratrice et accédez à la page de démarrage https://host:port/aem/start.html.
1. Accédez à Outils > Opérations > Migration du contenu

   ![image](/help/journey-migration/content-transformer/assets/ct-1.png)

   >[!NOTE]
   > Vérifiez que vous avez déjà exécuté le rapport BPA à l’aide de l’URL http://host:port/apps/best-practices-analyzer/content/BestPracticesReport.html.

1. Cliquez sur la carte portant le titre **Transformateur de contenu pour le rapport BPA**

   ![image](/help/journey-migration/content-transformer/assets/ct-2.png)

   Vous trouverez ci-dessous une vue d’ensemble du Transformateur de contenu si la création du rapport BPA a réussi et si des problèmes liés au contenu ont été détectés.

   Le délai d’expiration du rapport BPA s’affiche sur le rail latéral. Il est recommandé d’exécuter le Transformateur de contenu avec le dernier rapport BPA afin d’éviter d’omettre des résultats liés au contenu.

   ![image](/help/journey-migration/content-transformer/assets/ct-3.png)

1. Vous pouvez filtrer les problèmes en fonction de `Pattern Code`, `Subtype`, `Importance` et `Source`.

   ![image](/help/journey-migration/content-transformer/assets/ct-4.png)

1. Vous pouvez sélectionner tous les problèmes ou des problèmes spécifiques, puis les déplacer, les supprimer et les renommer afin de les résoudre. Des chemins personnalisés peuvent également être ajoutés à l’aide du bouton **Ajouter des chemins** dans le coin supérieur droit.

   >[!NOTE]
   > Lors de l’utilisation de l’opération de déplacement, il est recommandé de déplacer tous les chemins vers un seul dossier (par exemple, sous `/etc/packages/content-transformation/paths`). Ainsi, lorsque les packages de sauvegarde sont installés pour ramener l’instance à son état d’origine, le dossier (`/etc/packages/content-transformation/paths`) peut être supprimé à l’aide de l’opération de suppression afin de réduire la taille du référentiel.

   ![image](/help/journey-migration/content-transformer/assets/ct-5.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-6.png)

   >[!NOTE]
   > Toute opération pouvant modifier le contenu source (`move`/`remove`/`rename`) crée par défaut un package de sauvegarde des chemins sources sous `/etc/packages/content-transformation` avant la transformation. Bien que chaque boîte de dialogue d’opération dispose d’une option pour désactiver/activer la création de package de sauvegarde, il est strictement recommandé de toujours activer la création de package.

1. Un exemple de package de sauvegarde créé pour l’opération de déplacement des chemins est présenté ci-dessous. Cliquez sur Installer pour rétablir les chemins sources. Notez que l’installation ramènera uniquement les chemins sources à leur emplacement d’origine. Elle ne supprimera pas les chemins où ils ont été déplacés pendant la transformation. Pour supprimer les chemins dans l’emplacement déplacé, cliquez sur **Ajouter des chemins** pour ajouter l’emplacement (par exemple, `/etc/packages/content-transformation/paths`), sélectionnez l’emplacement et cliquez sur **Supprimer**.

   >[!CAUTION]
   > Ne supprimez pas `/etc/packages/content-transformation`, car il s’agit de l’emplacement où se trouvent les packages de sauvegarde. Vous pourrez supprimer cet emplacement uniquement lorsque vous aurez la certitude de ne plus avoir besoin de ces packages. Cela vous permettra de réduire la taille du référentiel.

   ![image](/help/journey-migration/content-transformer/assets/ct-7.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-8.png)

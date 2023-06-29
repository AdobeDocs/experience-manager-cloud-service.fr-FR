---
title: Utilisation de Content Transformer
description: Utilisation de Content Transformer
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 2%

---

# Utilisation de Content Transformer {#using-ct}

## Points importants concernant l’utilisation du transformateur de contenu {#imp-considerations-ct}

Consultez la section ci-dessous pour comprendre les points importants à prendre en compte pour utiliser le transformateur de contenu :

* Pour utiliser le transformateur de contenu, vous devez d’abord exécuter l’analyseur des bonnes pratiques dans votre environnement Adobe Experience Manager (AEM).
* Bien que vous puissiez exécuter Content Transformer dans votre environnement de production, il est recommandé d’exécuter Content Transformer sur un clone de votre environnement de production. Plus important encore, vous devez vous assurer que le BPA et le CT sont exécutés sur le même environnement.
* Vous devez être un administrateur de l’environnement dans lequel vous souhaitez exécuter Content Transformer.
* Toute opération pouvant modifier le contenu source ( déplacer/supprimer/renommer ) crée par défaut un package de sauvegarde des chemins source sous `/etc/packages/content-transformation` avant la transformation. Bien que chaque boîte de dialogue d’opération dispose d’une option pour désactiver/activer la création de package de sauvegarde, il est strictement recommandé de toujours sélectionner la création de package d’activation .
* Chaque page du CT est configurée pour répertorier un maximum de 50 résultats, donc à la fois un maximum de 50 résultats peuvent être transformés. Cela permet de fournir une réponse en temps voulu sur l’interface utilisateur.

## Disponibilité {#availability-ct}

Le transformateur de contenu est fourni avec la fonction [Outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) qui peut être téléchargé sous la forme d’un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le package via Package Manager sur votre instance d’AEM source.

>[!NOTE]
>Le transformateur de contenu est disponible avec l’outil de transfert de contenu version 2.0.20 ou ultérieure.

## Ouverture du transformateur de contenu {#opening-ct}

1. Connectez-vous à l’instance d’AEM source en tant qu’administrateur et accédez à la page de début : https://host:port/aem/start.html.
1. Accédez à Outils > Opérations > Migration du contenu

   ![image](/help/journey-migration/content-transformer/assets/ct-1.png)

   >[!NOTE]
   > Vérifiez que vous avez déjà exécuté le rapport BPA et vérifiez-le à l’aide de l’URL http://host:port/apps/best-practices-analyzer/content/BestPracticesReport.html

1. Cliquez sur la carte avec le titre . **Transformateur de contenu pour le rapport BPA**

   ![image](/help/journey-migration/content-transformer/assets/ct-2.png)

   Vous trouverez ci-dessous un exemple de l’apparence de la page Présentation du transformateur de contenu si la création du rapport BPA a réussi et si elle a détecté des problèmes liés au contenu.

   Le délai d’expiration du rapport BPA s’affiche sur le rail latéral. Il est recommandé d’exécuter le transformateur de contenu avec le dernier rapport BPA afin d’éviter d’omettre les résultats liés au contenu.

   ![image](/help/journey-migration/content-transformer/assets/ct-3.png)

1. Vous pouvez filtrer les problèmes en fonction de `Pattern Code`, `Subtype`, `Importance`, et `Source`.

   ![image](/help/journey-migration/content-transformer/assets/ct-4.png)

1. Vous pouvez sélectionner tous les problèmes ou des problèmes spécifiques et agir par exemple pour les déplacer, les supprimer et les renommer afin de les résoudre. Les chemins personnalisés peuvent également être ajoutés à l’aide de **Ajouter des chemins** dans le coin supérieur droit.

   >[!NOTE]
   > Lors de l’utilisation de l’opération de déplacement, il est recommandé de déplacer tous les chemins vers un seul dossier (par exemple, sous `/etc/packages/content-transformation/paths`), donc, lorsque les packages de sauvegarde sont installés pour ramener l’instance à l’état d’origine, le dossier (`/etc/packages/content-transformation/paths`) peut être supprimé à l’aide de l’opération remove pour réduire la taille du référentiel.

   ![image](/help/journey-migration/content-transformer/assets/ct-5.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-6.png)

   >[!NOTE]
   > Toute opération pouvant modifier le contenu source (`move`/`remove`/`rename`) crée par défaut un package de sauvegarde des chemins sources sous `/etc/packages/content-transformation` avant la transformation. Bien que chaque boîte de dialogue d’opération dispose d’une option pour désactiver/activer la création de package de sauvegarde, il est strictement recommandé de toujours sélectionner la création de package d’activation .

1. Un exemple de package de sauvegarde créé pour l’opération de déplacement des chemins est présenté ci-dessous. Cliquez sur Installer pour rétablir les chemins sources. Notez que l’installation ramènera uniquement les chemins source à leur emplacement d’origine et non pas les chemins où ils ont été déplacés pendant la transformation. Pour supprimer les chemins d’accès à l’emplacement déplacé, cliquez sur **Ajouter des chemins** pour ajouter l’emplacement (par exemple `/etc/packages/content-transformation/paths`), sélectionnez l’emplacement et cliquez sur **Supprimer**.

   >[!CAUTION]
   > Ne pas supprimer `/etc/packages/content-transformation` car il s’agit de l’emplacement où se trouvent les modules de sauvegarde. Ce n’est que lorsque vous êtes certain que vous n’avez plus besoin de ces packages que vous pouvez supprimer cet emplacement afin de réduire la taille du référentiel.

   ![image](/help/journey-migration/content-transformer/assets/ct-7.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-8.png)

---
title: Gestion des ressources numériques
description: Découvrez comment détecter les ressources en double
contentOwner: KK
mini-toc-levels: 3
feature: Asset Management,Publishing,Collaboration,Asset Processing
role: User,Architect,Admin
source-git-commit: bd0981b262f645653723f1b35d871808506d47ba
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 96%

---


# Détection des ressources en double {#detect-duplicate-assets}

Si un utilisateur DAM charge une ou plusieurs ressources qui existent déjà dans le référentiel, [!DNL Experience Manager] détecte la duplication et en informe l’utilisateur. La fonctionnalité de détection des doublons est désactivée par défaut, car elle peut avoir un impact sur les performances en fonction de la taille du référentiel et du nombre de ressources chargées.

Pour activer cette fonction :

1. Accédez à **[!UICONTROL Outils > Ressources > Configurations des ressources]**.

1. Cliquez sur **[!UICONTROL Détecteur de doublons de ressources]**.

1. Dans la [!UICONTROL page Détecteur de doublons de ressources], cliquez sur **[!UICONTROL Activé]**.

   La valeur `dam:sha1` pour Détecter le champ de métadonnées garantit que les ressources en double sont détectées même si les noms de fichier sont différents.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![Détecteur de doublons de ressources](assets/asset-duplication-detector.png)

>[!NOTE]
>
>Si vous avez configuré le détecteur de doublons à l’aide du fichier de configuration `/apps/example/config.author/com.adobe.cq.assetcompute.impl.assetprocessor.AssetDuplicationDetector.cfg.json` (configuration OSGi), vous pouvez continuer à l’utiliser, mais Adobe recommande d’utiliser la nouvelle méthode.


Une fois activé, Experience Manager envoie des notifications de ressources en double vers la boîte de réception Experience Manager. Il s’agit d’un résultat global correspondant à plusieurs doublons. Les utilisateurs peuvent choisir de supprimer les ressources en fonction des résultats.

![Notification de boîte de réception pour les ressources en double](assets/duplicate-detect-inbox-notification.png)

>[!NOTE]
>
>Lorsque vous chargez des ressources vers le référentiel, Experience Manager détecte la duplication et vous informe des 100 premières ressources en double.


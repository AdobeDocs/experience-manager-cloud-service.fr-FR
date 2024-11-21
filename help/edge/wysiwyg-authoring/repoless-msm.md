---
title: Réplication de la gestion multisite
description: Découvrez les recommandations de bonnes pratiques sur la configuration d’un projet avec des sites multilingues qui utilisent une seule base de code de manière réactive.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 02957fb8671d953a683ebd6e168979b11ad391c4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Réplication de la gestion multisite {#repoless-msm}

Ce document suppose que vous avez déjà créé un site de base pour votre projet appelé `my-aem-site` et que vous souhaitez le localiser à l’aide de la fonctionnalité MSM AEM.

Si vous avez déjà configuré votre projet pour le cas d’utilisation des répolations, la configuration cloud est affectée au niveau de la page racine, `/content/my-aem-site`. Pour les sites multilingues, cette affectation de configuration doit être modifiée sur la racine de langue telle que `/content/my-aem-site/language-master/de`.


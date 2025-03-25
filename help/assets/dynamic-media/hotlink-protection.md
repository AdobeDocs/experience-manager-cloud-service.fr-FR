---
title: Activation de la protection de lien dynamique dans Dynamic Media
description: Découvrez comment activer la protection de lien dynamique dans Dynamic Media.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 0198b3a3-173e-46ca-a845-3f58f8eab769
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 100%

---

# Activation de la protection de lien dynamique dans Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

On parle de lien dynamique lorsqu’un site web tiers utilise du code HTML pour afficher une image de votre site web. Il utilise votre bande passante chaque fois que l’image est demandée, car le navigateur du visiteur y accède directement depuis votre serveur. La *protection* de lien dynamique est une méthode qui empêche d’autres sites web d’établir un lien direct vers des images ou du contenu CSS ou JavaScript figurant sur vos pages web. Ce type de protection contribue à réduire l’utilisation inutile de bande passante sous votre compte Dynamic Media.

Le [service clientèle Adobe](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=fr#home) peut configurer un filtre référent au niveau du CDN. Cela permet de s’assurer que le contenu Dynamic Media n’est diffusé que sur les sites web de votre liste des sites web autorisés pour le domaine.

>[!NOTE]
>
>Cette fonctionnalité nécessite l’utilisation du réseau CDN prêt à l’emploi fourni avec Adobe Experience Manager Dynamic Media. Aucun autre réseau CDN personnalisé n’est pris en charge avec cette fonctionnalité. Pour activer la protection de lien dynamique, un administrateur doit créer un ticket de support afin de demander le changement de configuration pour votre compte Dynamic Media. L’activation de la protection de lien dynamique n’implique aucun frais supplémentaires.

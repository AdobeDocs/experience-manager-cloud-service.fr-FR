---
title: En-têtes HTTP personnalisés
description: Découvrez comment configurer des en-têtes HTTP personnalisés qui seraient envoyés au moteur de commerce, ainsi que ceux déjà envoyés par CIF.
exl-id: 2cef5d4b-45f6-4d72-a24b-67ca53d9057d
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 84%

---

# En-têtes HTTP personnalisés {#custom-http-headers}

## Vue d’ensemble {#overview}

Pour mieux contrôler leur serveur principal, les auteurs peuvent configurer des en-têtes HTTP personnalisés qui seraient envoyés au moteur de commerce, ainsi que ceux déjà envoyés par CIF. Les cas d’utilisation courants incluent des configurations multi-magasin dans lesquelles vous pouvez utiliser des en-têtes HTTP pour contrôler la réponse du serveur principal de commerce.

>[!NOTE]
>
>Les développeurs peuvent toujours configurer des en-têtes HTTP personnalisés à l’aide de la configuration client GraphQL.
>

## Configuration {#configuration}

Pour configurer les en-têtes HTTP personnalisés, vous devez d’abord les définir. Les en-têtes HTTP personnalisés doivent d’abord être définis par le biais de leur ajout à la configuration de service `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` à l’aide d’une configuration OSGi.

Vous pouvez configurer les valeurs des en-têtes HTTP dans la page Configuration du service cloud pour votre projet :

1. Accédez à la page de configuration de Cloud Service dans Outils > Cloud Services > Configuration de CIF .
1. Ouvrir une configuration existante ou en créer une
1. Accédez à l’onglet « Avancé » et recherchez le champ multiple « En-têtes HTTP personnalisés ». Vous pouvez sélectionner les en-têtes que vous avez définis précédemment et leur attribuer des valeurs.

Les composants qui utilisent la configuration de service cloud ci-dessus enverront ces en-têtes HTTP avec chaque requête GraphQL.

## Restrictions {#restrictions}

Bien que le service permette de définir des noms d’en-tête, y compris les noms standard, ils ne sont pas disponibles pour configuration. En d’autres termes, vous ne pouvez pas remplacer les en-têtes HTTP standard à l’aide de cette fonctionnalité. Vous trouverez une liste de noms d’en-tête restreints sous [mdn web docs : en-têtes HTTP](https://developer.mozilla.org/fr-FR/docs/Web/HTTP/Headers). En outre, deux en-têtes supplémentaires ne peuvent pas être utilisés :

* « Store » : utilisé par CIF pour identifier la boutique Adobe Commerce.
* « Preview-Version » : utilisé par CIF pour récupérer les produits intermédiaires.

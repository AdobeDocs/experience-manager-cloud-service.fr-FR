---
title: Configuration du filtre Référent avec AEM découplé
description: Le filtre Référent Adobe Experience Manager permet d’accéder à partir d’hôtes tiers. Une configuration OSGi pour le filtre Référent est nécessaire pour activer l’accès au point d’entrée GraphQL pour les applications découplées.
feature: GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
source-git-commit: 076cafe3d096fd7f4c808f1b2553a9ba6b6c1833
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 69%

---

# Filtre Référent {#referrer-filter}

Le filtre Référent Adobe Experience Manager permet d’accéder à partir d’hôtes tiers.

Une configuration OSGi pour le filtre de référent est nécessaire pour permettre l’accès au point de terminaison GraphQL pour les applications sans interface utilisateur via le POST HTTP. Lors de l’utilisation de AEM de requêtes persistantes sans affichage qui accèdent à AEM via un GET HTTP, aucune configuration de filtre de référent n’est nécessaire.

>[!WARNING]
> AEM Referrer Filter n’est pas une usine de configuration OSGi, ce qui signifie qu’une seule configuration est principale sur un service AEM à la fois. Dans la mesure du possible, évitez d’ajouter des configurations de filtrage de référent personnalisées, car elles remplacent AEM configurations natives et peuvent interrompre la fonctionnalité du produit.

Pour ce faire, ajoutez une configuration OSGi appropriée pour le filtre Référent qui :

* spécifie un nom d’hôte de site web approuvé ; soit `allow.hosts`, soit `allow.hosts.regexp`,
* accorde l’accès pour ce nom d’hôte.

Le nom du fichier doit être `org.apache.sling.security.impl.ReferrerFilter.cfg.json`.

Par exemple, pour accorder l’accès aux requêtes avec le référent `my.domain`, vous pouvez :

```xml
{
    "allow.empty": false,
    "allow.hosts": [
      "my.domain"
    ],
    "allow.hosts.regexp": [
      ""
    ],
    "filter.methods": [
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp": [
      ""
    ]
}
```

>[!CAUTION]
>
>Il incombe au client de :
>
>* n’accorder l’accès qu’aux domaines approuvés ;
>* s’assurer qu’aucune information sensible n’est exposée
>* ne pas utiliser la syntaxe de caractère générique [*] ; cette méthode désactive à la fois l’accès authentifié au point d’entrée GraphQL et l’expose par ailleurs vis-à-vis du monde entier.


>[!CAUTION]
>
>Tous les [schémas](#schema-generation) GraphQL (dérivés de modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point d’entrée GraphQL.
>
>En d’autres termes, vous devez vous assurer qu’aucune donnée sensible n’est disponible, car elle peut être divulguée de cette façon ; par exemple, cela concerne des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

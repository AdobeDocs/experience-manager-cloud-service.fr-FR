---
title: Configuration du filtre référent avec AEM Headless
description: Le filtre de référent d’Adobe Experience Manager autorise l’accès à partir d’hôtes tiers. Une configuration OSGi pour le filtre Référent est nécessaire pour activer l’accès au point d’entrée GraphQL pour les applications découplées.
feature: Headless, GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
solution: Experience Manager
role: Admin, Developer
source-git-commit: 3096436f8057833419249d51cb6c15e6c28e9e13
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 56%

---

# Filtre Référent {#referrer-filter}

Le filtre de référent d’Adobe Experience Manager autorise l’accès à partir d’hôtes tiers.

Une configuration OSGi pour le filtre de référent est nécessaire pour autoriser l’accès au point d’entrée GraphQL pour les applications découplées via POST HTTP. Lors de l’utilisation de requêtes persistantes découplées AEM qui accèdent à AEM via GET HTTP, aucune configuration de filtre de référent n’est nécessaire.

>[!WARNING]
> Le filtre de référent AEM n’est pas une configuration d’usine OSGi, ce qui signifie qu’une seule configuration à la fois est active sur un service AEM. Dans la mesure du possible, évitez d’ajouter des configurations de filtre de référent personnalisées, car elles remplacent les configurations natives AEM et peuvent altérer la fonctionnalité du produit.

Pour ce faire, ajoutez une configuration OSGi appropriée pour le filtre Référent qui :

* spécifie un nom d’hôte de site web approuvé ; soit `allow.hosts`, soit `allow.hosts.regexp`,
* accorde l’accès pour ce nom d’hôte.

Le nom du fichier doit être `org.apache.sling.security.impl.ReferrerFilter.cfg.json`.

## Exemple de configuration {#example-configuration}

Par exemple, pour accorder l’accès aux requêtes avec le référent `my.domain`, vous pouvez :

>[!CAUTION]
>
>Il s’agit d’un exemple de base qui peut remplacer la configuration standard. Vous devez vous assurer que les mises à jour de produit sont toujours appliquées à toutes les personnalisations.

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

## Sécurité des données {#data-security}

>[!CAUTION]
>
>Il vous incombe toujours de vous pencher pleinement sur les points suivants.

Pour garantir la sécurité de vos données, vous devez vous assurer que :

* L’accès est **uniquement** accordé aux domaines approuvés

* caractère générique [`*`] dans **not** utilisé ; cela désactive l’accès authentifié au point de terminaison GraphQL et l’expose également au monde entier.

* les informations sensibles sont **never** exposées ; ni directement, ni indirectement :

   * Par exemple, tous les [schémas GraphQL](/help/headless/graphql-api/content-fragments.md#schema-generation) sont :

      * dérivés de modèles de fragment de contenu **Activé** ;

     **and**

      * sont lisibles via le point d’entrée GraphQL ;

     Cela signifie que les informations présentes en tant que noms de champ dans la définition de modèle peuvent devenir disponibles.

Vous devez vous assurer qu’aucune donnée sensible n’est disponible de quelque manière que ce soit. De tels détails doivent donc être soigneusement étudiés.

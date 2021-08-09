---
title: Utilisation de Sling Resource Merger dans Adobe Experience Manager as a Cloud Service
description: Sling Resource Merger propose des services pour accéder à des ressources et les fusionner.
exl-id: 5b6e5cb5-4c6c-4246-ba67-6b9f752867f5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: ht
source-wordcount: '1160'
ht-degree: 100%

---

# Utilisation de Sling Resource Merger dans AEM as a Cloud Service{#using-the-sling-resource-merger-in-aem}

## Objectif {#purpose}

Sling Resource Merger propose des services pour accéder à des ressources et les fusionner. Il fournit des mécanismes de différenciation (diff) pour les deux éléments suivants :

* **[Recouvrements](/help/implementing/developing/introduction/overlays.md)** de ressources à l’aide de [chemins de recherche](/help/implementing/developing/introduction/overlays.md#search-paths).

* **Remplacements** de boîtes de dialogue de composant pour l’interface utilisateur tactile (`cq:dialog`), à l’aide de la hiérarchie des types de ressource (par le biais de la propriété `sling:resourceSuperType`).

Avec Sling Resource Merger, les ressources et/ou propriétés de recouvrement/remplacement sont fusionnées avec les ressources/propriétés d’origine :

* Le contenu de la définition personnalisée a une priorité plus élevée que celle d’origine (en d’autres termes, elle la *recouvre* ou elle la *remplace*).

* Si nécessaire, les [propriétés](#properties) définies dans la personnalisation indiquent comment utiliser le contenu fusionné à partir de l’original.

<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>Sling Resource Merger et les méthodes associées ne peuvent être utilisés qu’avec l’interface utilisateur tactile (qui est la seule interface utilisateur disponible pour AEM as a Cloud Service).

### Objectifs pour AEM {#goals-for-aem}

Sling Resource Merger est utilisé dans AEM pour deux raisons principales :

* S’assurer que les changements de personnalisation ne sont pas effectués dans `/libs`.
* Réduire la structure qui est répliquée à partir de `/libs`.

   Lorsque vous utilisez Sling Resource Merger, il est déconseillé de copier toute la structure depuis `/libs`, car cela entraînerait le stockage d’une trop grande quantité d’informations dans la personnalisation (généralement `/apps`). Dupliquer les informations augmente inutilement le risque que des problèmes surviennent lorsque le système est mis à niveau.

>[!CAUTION]
>
>Vous ne devez ***rien*** modifier dans le chemin `/libs`.
>
>En effet, le contenu de `/libs` peut être remplacé chaque fois que des mises à niveau sont appliquées à votre instance.
>
>* Les recouvrements dépendent des [chemins de recherche](/help/implementing/developing/introduction/overlays.md#search-paths).
   >
   >
* Les remplacements ne dépendent pas des chemins de recherche. Ils utilisent la propriété `sling:resourceSuperType` pour établir la connexion.
>
>
Cependant, les remplacements sont souvent définis sous `/apps`, car une pratique recommandée dans AEM as a Cloud Service consiste à définir des personnalisations sous `/apps`, du fait que vous ne devez rien changer sous `/libs`.

### Propriétés {#properties}

Resource Merger fournit les propriétés suivantes :

* `sling:hideProperties` (`String` ou `String[]`)

   Indique la propriété, ou la liste des propriétés, à masquer.

   Le caractère générique `*` masque tout.

* `sling:hideResource` (`Boolean`)

   Indique si les ressources doivent être complètement masquées, y compris leurs enfants.

* `sling:hideChildren` (`String` ou `String[]`)

   Contient le nœud enfant, ou la liste des nœuds enfants, à masquer. Les propriétés du nœud seront conservées.

   Le caractère générique `*` masque tout.

* `sling:orderBefore` (`String`)

   Contient le nom du nœud frère devant lequel le nœud actuel doit être positionné.

Ces propriétés déterminent la façon dont les ressources/propriétés correspondantes/d’origine (issues de `/libs`) sont utilisées par le recouvrement/remplacement (souvent dans `/apps`).

### Création de la structure {#creating-the-structure}

Pour créer un recouvrement ou un remplacement, vous devez recréer le nœud d’origine, avec la structure équivalente, sous la destination (qui est généralement `/apps`). Par exemple :

* Recouvrement

   * La définition de l’entrée de navigation pour la console Sites, comme illustrée dans le rail, est définie à l’emplacement suivant :

      `/libs/cq/core/content/nav/sites/jcr:title`

   * Pour recouvrir cela, créez le nœud suivant :

      `/apps/cq/core/content/nav/sites`

      Mettez ensuite la propriété `jcr:title` à jour selon les besoins.

* Remplacement

   * La définition de la boîte de dialogue tactile pour la console Textes est définie à l’emplacement suivant :

      `/libs/foundation/components/text/cq:dialog`

   * Pour remplacer cela, créez le nœud suivant ; par exemple :

      `/apps/the-project/components/text/cq:dialog`

Pour créer l’un de ces éléments, vous devez simplement recréer l’ossature. Pour simplifier la reconstitution de la structure, tous les nœuds intermédiaires peuvent être de type `nt:unstructured` (ils ne doivent pas nécessairement refléter le type de nœud d’origine ; par exemple, dans `/libs`).

Ainsi, dans l’exemple de recouvrement ci-dessus, les nœuds suivants sont nécessaires :

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Lorsque vous utilisez Sling Resource Merger (c’est-à-dire lorsque vous employez l’interface utilisateur tactile standard), il est déconseillé de copier toute la structure depuis `/libs`, car cela entraînerait le stockage d’une trop grande quantité d’informations dans `/apps`. Cela peut entraîner des problèmes lorsque le système est mis à niveau.

### Cas d’utilisation {#use-cases}

Ces éléments, en liaison avec les fonctionnalités standard, vous permettent d’effectuer les opérations suivantes :

* **Ajouter une propriété**

   La propriété n’existe pas dans la définition `/libs`, mais elle est requise dans le recouvrement/remplacement `/apps`.

   1. Créez le nœud correspondant dans `/apps`.
   1. Créez la propriété sur ce nœud.

* **Redéfinir une propriété (pas les propriétés créées automatiquement)**

   La propriété est définie dans `/libs`, mais une nouvelle valeur est requise dans le recouvrement/remplacement `/apps`.

   1. Créez le nœud correspondant dans `/apps`.
   1. Créez la propriété correspondante sur ce nœud (sous /`apps`).

      * La priorité de la propriété sera basée sur la configuration de Sling Resource Resolver.
      * Le type de la propriété peut être modifié.

         Si vous utilisez un type de propriété différent de celui utilisé dans `/libs`, c’est le type que vous avez défini qui sera utilisé.
   >[!NOTE]
   >
   >Le type de la propriété peut être modifié.

* **Redéfinir une propriété créée automatiquement**

   Par défaut, les propriétés créées automatiquement (telles que `jcr:primaryType`) ne sont pas soumises à une opération de recouvrement/remplacement pour s’assurer que le type de nœud défini actuellement sous `/libs` est respecté. Pour imposer un recouvrement/remplacement, vous devez recréer le nœud dans `/apps`, masquer explicitement la propriété, puis la redéfinir :

   1. Créez le nœud correspondant sous `/apps` avec la propriété `jcr:primaryType` souhaitée.
   1. Créez la propriété `sling:hideProperties` sur ce nœud, avec la valeur définie sur celle de la propriété créée automatiquement ; par exemple, `jcr:primaryType`

      Cette propriété, définie sous `/apps`, est désormais prioritaire par rapport à celle définie sous `/libs`

* **Redéfinir un nœud et ses enfants**

   Le nœud et ses enfants sont définis dans `/libs`, mais une nouvelle configuration est requise dans le recouvrement/remplacement de `/apps`.

   1. Combinez les actions des opérations suivantes :

      1. Masquer les enfants d’un nœud (conserver les propriétés du nœud).
      1. Redéfinir la (les) propriétés.

* **Masquer une propriété**

   La propriété est définie dans `/libs`, mais elle n’est pas requise dans le recouvrement/remplacement de `/apps`.

   1. Créez le nœud correspondant dans `/apps`.
   1. Créez une propriété `sling:hideProperties` de type `String` ou `String[]`. Utilisez-la pour spécifier les propriétés à masquer/ignorer. Des caractères génériques peuvent également être utilisés. Par exemple :

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Masquer un nœud et ses enfants**

   Le nœud et ses enfants sont définis dans `/libs`, mais ils ne sont pas nécessaires dans le recouvrement/remplacement de `/apps`.

   1. Créez le nœud correspondant sous /apps.
   1. Créez une propriété `sling:hideResource`

      * type: `Boolean`
      * value: `true`

* **Masquer les enfants d’un nœud (tout en conservant les propriétés du nœud)**

   Le nœud, ses propriétés et ses enfants sont définis dans `/libs`. Le nœud et ses propriétés sont requis dans le recouvrement/remplacement de `/apps`, tandis que la totalité ou une partie des nœuds enfants ne sont pas requis dans le recouvrement/remplacement de `/apps`.

   1. Créez le nœud correspondant sous `/apps`
   1. Créez la propriété `sling:hideChildren` :

      * type: `String[]`
      * value : liste des nœuds enfants (tels que définis dans `/libs`) à masquer/ignorer

      Le caractère générique &amp;ast; peut être utilisé pour masquer/ignorer tous les nœuds enfants.


* **Réorganiser les nœuds**

   Le nœud et ses frères sont définis dans `/libs`. Une nouvelle position est requise pour que le nœud soit recréé dans le recouvrement/remplacement de `/apps`. Cette position y est définie en référence au nœud frère approprié dans `/libs`.

   * Utilisez la propriété `sling:orderBefore` :

      1. Créez le nœud correspondant sous `/apps`
      1. Créez la propriété `sling:orderBefore` :

         Cela spécifie le nœud (comme dans `/libs`) devant lequel le nœud actif doit être positionné :

         * type: `String`
         * value: `<before-SiblingName>`

### Appel de Sling Resource Merger à partir de votre code {#invoking-the-sling-resource-merger-from-your-code}

Sling Resource Merger comprend deux fournisseurs de ressources personnalisés : un pour les recouvrements et un autre pour les remplacements. Chacun d’eux peut être appelé dans votre code en utilisant un point de montage :

>[!NOTE]
>
>Lorsque vous accédez à votre ressource, il est conseillé d’utiliser le point de montage approprié.
>
>De cette manière, vous avez la garantie que Sling Resource Merger est appelé et que la ressource entièrement fusionnée est renvoyée (réduction de la structure qui doit être répliquée à partir de `/libs`).

* Recouvrement :

   * Objectif : fusionner les ressources en fonction de leur chemin de recherche
   * Point de montage :`/mnt/overlay`
   * Usage : `mount point + relative path`
   * Exemple :

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Remplacement :

   * Objectif : fusionner les ressources en fonction de leur super-type
   * Point de montage :`/mnt/overide`
   * Usage : `mount point + absolute path`
   * Exemple :

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

<!--
### Example of Usage {#example-of-usage}

Some examples are covered:

* Overlay:

    * [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
    * [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)

* Override:

    * [Configuring your Page Properties](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
-->

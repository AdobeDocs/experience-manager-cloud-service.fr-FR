---
title: Types de noeud AEM
description: aem est basé sur Sling et utilise un référentiel JCR avec des types de noeud proposés par les deux, mais AEM fournit également une gamme de ses propres types de noeud.
translation-type: tm+mt
source-git-commit: 020cebfa714c098f032df963b7105503c741e748
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 15%

---


# aem Types de noeud {#aem-node-types}

Comme AEM est basé sur Sling et utilise un référentiel JCR, les types de noeud proposés par ces deux normes peuvent être utilisés dans AEM :

* [Types de nœuds JCR](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Types de nœuds Sling](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

De plus, aem fournit une gamme de types de noeud personnalisés. Pour la liste la plus récente avec toutes les propriétés associées, [utilisez CRXDE](/help/implementing/developing/tools/crxde.md) pour parcourir le chemin d’accès suivant dans le référentiel AEM :

`/jcr:system/jcr:nodeTypes`

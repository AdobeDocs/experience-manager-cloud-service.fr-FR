---
title: Types de nœuds AEM
description: AEM est architecturé autour de Sling et utilise un référentiel JCR avec des types de nœuds proposés par les deux plateformes. Cependant, AEM fournit également un éventail de types de nœuds personnalisés.
exl-id: 82cc28ca-37e2-4ca3-b3e4-cc03bbc5bdf5
source-git-commit: 08559417c8047c592f2db54321afe68836b75bd1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 93%

---

# Types de nœuds AEM {#aem-node-types}

AEM est architecturé autour de Sling et utilise un référentiel JCR. Aussi, les types de nœuds proposés par ces deux plateformes sont-ils disponibles :

* [Types de nœuds JCR](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Types de noeuds Sling](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

En plus de ceux-ci. AEM propose un éventail de types de nœuds personnalisés. Pour la liste la plus récente avec toutes les propriétés associées, [utilisez CRXDE](/help/implementing/developing/tools/crxde.md) pour parcourir le chemin d’accès suivant dans le référentiel AEM :

`/jcr:system/jcr:nodeTypes`

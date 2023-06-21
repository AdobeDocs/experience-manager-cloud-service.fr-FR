---
title: Diagnostic ContextHub
description: ContextHub fournit une page de diagnostic où vous avez accès à une vue d’ensemble du framework ContextHub
exl-id: c8d4e160-ea02-49f3-9e31-119445ef5a68
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 64%

---

# Diagnostics ContextHub {#contexthub-diagnostics}

ContextHub fournit une page de diagnostics qui affiche un aperçu de sa structure. Pour ouvrir la page, accédez à la page `contexthub.diagnostics.html` de votre instance de création AEM par exemple :

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

La page Diagnostics ContextHub fournit des informations sur les magasins et les modules d’IU créés, les dossiers de bibliothèques clientes chargés et les liens vers des pages utiles.

>[!NOTE]
>
>Pour que les informations de diagnostic soient renvoyées, le mode de débogage doit être activé ; dans le cas contraire, la page de diagnostic est vide. Reportez-vous à ce [document](configuring-contexthub.md#debugging-contexthub) pour plus de détails sur l’activation du mode débogage.

## Magasins {#stores}

La section Magasins répertorie tous les magasins ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **Title :** [type de magasin](sample-stores.md) sur lequel le magasin est basé.
* **path:** Le chemin d’accès au noeud du référentiel qui contient la configuration.
* **resourceType:** Chemin d’accès du noeud du référentiel où le type de magasin est défini.
* **clientlibs :** Les catégories des bibliothèques clientes chargées qui implémentent le type de magasin.

## Modules {#modules}

La section Modules répertorie tous les modules d’IU ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **Title :** [type de module d’IU](sample-modules.md) sur lequel le module d’IU est basé.
* **path:** Le chemin d’accès au noeud du référentiel qui contient la configuration.
* **resourceType:** Chemin d’accès du noeud du référentiel où le type de module d’IU est défini.
* **clientlibs :** Les catégories des bibliothèques clientes chargées qui implémentent le type de module d’IU.

## Clientlibs {#clientlibs}

La section Clientlibs répertorie tous les [dossiers de bibliothèque cliente](/help/implementing/developing/introduction/clientlibs.md) chargés par ContextHub. Les bibliothèques clientes sont classées comme suit :

* **kernel.js :** bibliothèques clientes qui implémentent le framework ContextHub, le moteur de segment et les types de stockage.
* **ui.js :** bibliothèques clientes qui implémentent les types de modules d’IU et l’IU ContextHub.
* **style.css :** Fichiers CSS chargés à partir des bibliothèques clientes.

## URL {#urls}

La section URL contient des liens vers les fonctionnalités de ContextHub :

* **Éditeur de configuration :** ouvre la [page de configuration ContextHub](configuring-contexthub.md) où vous pouvez configurer les magasins, les modes IU et les modules d’IU.
* **Configuration des modules ContextHub :** ouvre le fichier `/etc/cloudsettings/default/contexthub.config.kernel.js`, qui contient la représentation de l’objet Javascript des configurations du magasin ContextHub.
* **Configuration de l’IU ContextHub :** ouvre le fichier `/etc/cloudsettings/default/contexthub.config.ui.js`, qui contient la représentation de l’objet Javascript des configurations du mode d’IU ContextHub.
* **kernel.js :** ouvre le fichier `/etc/cloudsettings/default/contexthub.kernel.js`, qui contient le code source des bibliothèques clientes qui implémentent le framework ContextHub, le moteur de segment et les types de magasin.
* **ui.js :** ouvre le fichier `/etc/cloudsettings/default/contexthub.ui.js`, qui contient le code source des bibliothèques clientes qui implémentent le l’IU et les types de module d’IU ContextHub.
* **style.css :** ouvre le fichier `/etc/cloudsettings/default/contexthub.styles.css`, qui contient les styles CSS des modules d’IU et l’IU ContextHub.

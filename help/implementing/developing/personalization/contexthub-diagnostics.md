---
title: Diagnostic ContextHub
description: ContextHub fournit une page de diagnostic où vous avez accès à une vue d’ensemble du framework ContextHub
translation-type: tm+mt
source-git-commit: e361f24b943eff68982a37ac0dc2597f92450026
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 65%

---


# Diagnostic ContextHub {#contexthub-diagnostics}

ContextHub fournit une page de diagnostic où vous avez accès à une vue d’ensemble du framework ContextHub. To open the page, go to the `contexthub.diagnostics.html` page of your AEM author instance, for example:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

La page de diagnostic de ContextHub présente des informations sur les magasins et les modules d’IU qui ont été créés, les dossiers de bibliothèque cliente chargés et les liens vers des pages utiles.

>[!NOTE]
>
>Pour que les informations de diagnostic soient renvoyées, le mode de débogage doit être activé, sinon la page de diagnostic est vide. Se reporter à ce [document](configuring-contexthub.md#debugging-contexthub) pour plus de détails sur l’activation du mode débogage.

## Magasins {#stores}

La section Magasins répertorie tous les magasins ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **title :** [type de magasin](sample-stores.md) sur lequel le magasin est basé.
* **path :** chemin d’accès au nœud du référentiel contenant la configuration.
* **resourceType :** chemin du nœud du référentiel où le type de magasin est défini.
* **clientlibs :** catégories des bibliothèques clientes chargées qui implémentent le type de magasin.

## Modules {#modules}

La section Modules répertorie tous les modules d’IU ContextHub qui ont été configurés. Chaque élément de la liste comprend les informations suivantes :

* **Titre :** Type [du module](sample-modules.md) d’interface utilisateur sur lequel repose le module d’interface utilisateur.
* **path :** chemin d’accès au nœud du référentiel contenant la configuration.
* **resourceType :** chemin du nœud du référentiel où le type de module d’IU est défini.
* **clientlibs :** catégories des bibliothèques clientes chargées qui implémentent le type de module d’IU.

## Clientlibs {#clientlibs}

La section Clientlibs répertorie tous les dossiers de bibliothèque cliente chargés par ContextHub. Les bibliothèques clientes sont classées comme suit :

* **kernel.js : ** bibliothèques clientes qui implémentent le framework ContextHub, le moteur de segment et les types de stockage.
* **ui.js :** bibliothèques clientes qui implémentent les types de modules d’IU et l’IU ContextHub.
* **style.css :** fichiers CSS chargés à partir des bibliothèques clientes.

## URL  {#urls}

La section URL contient des liens vers les fonctionnalités de ContextHub :

* **Éditeur de configuration :** Ouvre la page [Configuration de](configuring-contexthub.md) ContextHub dans laquelle vous pouvez configurer les magasins, les modes d’interface utilisateur et les modules d’interface utilisateur.
* **Configuration des modules ContextHub :** Ouvre le `/etc/cloudsettings/default/contexthub.config.kernel.js` fichier, qui contient la représentation de l’objet Javascript des configurations de stockage ContextHub.
* **Configuration de l’interface utilisateur ContextHub :** Ouvre le `/etc/cloudsettings/default/contexthub.config.ui.js` fichier, qui contient la représentation de l’objet JavaScript des configurations de mode d’interface utilisateur ContextHub.
* **kernel.js :** Ouvre le `/etc/cloudsettings/default/contexthub.kernel.js` fichier, qui contient le code source des bibliothèques clientes qui implémentent la structure ContextHub, le moteur de segments et les types de stockage.
* **ui.js :** Ouvre le `/etc/cloudsettings/default/contexthub.ui.js` fichier, qui contient le code source des bibliothèques clientes qui implémentent les types d’interface utilisateur et de module d’interface ContextHub.
* **style.css :** Ouvre le `/etc/cloudsettings/default/contexthub.styles.css` fichier, qui contient les styles CSS pour l’interface utilisateur et les modules d’interface utilisateur ContextHub.

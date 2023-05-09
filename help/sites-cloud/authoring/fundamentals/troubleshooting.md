---
title: Résolution des problèmes d’AEM lors de la création
description: Problèmes que vous pouvez rencontrer lors de l’utilisation d’AEM
exl-id: b9c0584d-255e-486d-b829-09e07499ecd2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 78%

---

# Résolution des problèmes d’AEM lors de la création {#troubleshooting-aem-when-authoring}

La section suivante traite de certains problèmes susceptibles d’être rencontrés lorsque vous utilisez AEM, ainsi que des suggestions pour résoudre ces problèmes.

## Ancienne version de la page toujours visible sur le site de publication {#old-page-version-still-on-published-site}

* **Problème** :
   * Vous avez modifié une page et l’avez publiée sur le site de publication, mais l’*ancienne* version de la page est toujours visible sur le site de publication.
* **Raison** :
   * Cela peut avoir plusieurs causes, le plus souvent le cache (votre navigateur local ou Dispatcher), bien que cela puisse parfois poser un problème avec la file d’attente de réplication.
* **Solutions** :
   * Il existe différentes possibilités :
   * Vérifiez que la page a bien été répliquée. Vérifiez le statut de la page et, si nécessaire, le statut de la file d’attente de réplication.
   * Effacez la mémoire cache du navigateur local et accédez de nouveau à votre page.
   * Ajoutez `?` à la fin de l’URL de la page. Par exemple :
      * `http://<host>:<port>/sites.html/content?`
      * Ceci demandera la page directement auprès d’AEM et contournera le dispatcher. Si vous recevez la page mise à jour, ceci indique que vous devez vider la mémoire cache du dispatcher.
   * Contactez l’administrateur du système en cas de problèmes avec les files d’attente de réplication.

## Actions de composant non visibles dans la barre d’outils {#component-actions-not-visible-on-toolbar}

* **Problème** :
   * La plage entière des actions de composants applicables n’est pas visible lors de la modification d’une page de contenu dans l’environnement de création.
* **Raison** :
   * Dans de rares cas, une action précédente peut avoir un impact sur la barre d’outils.
* **Solution** :
   * Actualisez la page.

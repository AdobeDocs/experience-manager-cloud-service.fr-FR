---
title: Résolution des problèmes d’AEM lors de la création
description: Problèmes pouvant survenir lors de l’utilisation d’AEM
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Résolution des problèmes d’AEM lors de la création {#troubleshooting-aem-when-authoring}

La section suivante traite de certains problèmes susceptibles d’être rencontrés lorsque vous utilisez AEM, ainsi que des suggestions pour résoudre ces problèmes.

## Ancienne version de la page toujours visible sur le site de publication {#old-page-version-still-on-published-site}

* **Problème** :
   * You have made changes to a page and published the page to the publish site, but the *old* version of the page is still being shown on the publish site.
* **Motif** :
   * Les raisons peuvent être multiples, mais sont généralement liées à la mémoire cache (de votre navigateur local ou du dispatcher), bien qu’il s’agisse parfois d’un problème de la file d’attente de réplication.
* **Solutions** :
   * Plusieurs solutions sont possibles :
   * Vérifiez que la page a bien été répliquée. Vérifiez l’état de la page et, si nécessaire, l’état de la file d’attente de réplication.
   * Effacez la mémoire cache du navigateur local et accédez de nouveau à votre page.
   * Ajoutez `?` à la fin de l’URL de la page.Par exemple :
      * `http://<host>:<port>/sites.html/content?`
      * Ceci demandera la page directement auprès d’AEM et contournera le dispatcher. Si vous recevez la page mise à jour, ceci indique que vous devez vider la mémoire cache du dispatcher.
   * Contactez l’administrateur du système en cas de problèmes avec les files d’attente de réplication.

## Actions de composant non visibles dans la barre d’outils {#component-actions-not-visible-on-toolbar}

* **Problème** :
   * La plage entière des actions de composants applicables n’est pas visible lors de la modification d’une page de contenu dans l’environnement de création.
* **Motif** :
   * Dans de rares cas, une action précédente peut avoir un impact sur la barre d’outils.
* **Solution** :
   * Actualisez la page.

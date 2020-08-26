---
title: Expérience unifiée pour les outils de refactorisation du code
description: Expérience unifiée pour les outils de refactorisation du code
translation-type: tm+mt
source-git-commit: c554506aea99518c94666f5d2e6151a3dce3b91e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# Expérience unifiée pour les outils de refactorisation du code {#unified-experience}

Les outils Expérience unifiée pour la refactorisation du code unifient l’expérience d’exécution de l’AEM en tant qu’outils de refactorisation du code Cloud Service qui fonctionnent sur les fichiers de répartiteur, le code et les référentiels.

Cet outil réduit la complexité de l&#39;utilisation des outils de refactorisation du code, chacun ayant des exigences d&#39;exécution différentes en termes d&#39;installation, de configuration et d&#39;exécution.

## Avantages {#benefits}

L’expérience unifiée pour les outils de refactorisation du code appelle et exécute tous les outils de refactorisation du code qui fonctionnent sur le code source au même endroit.

L’expérience unifiée des outils de refactorisation du code, ainsi que les référentiels connexes, permettent de :

* Unifiez tous les outils qui fonctionnent sur la migration du code source dans une `node.js` application exposée `aio-cli plugin` afin de fournir une expérience utilisateur cohérente à l’utilisateur.

* Permet d’effectuer la migration globale par le biais d’une seule commande, tout en offrant la possibilité d’exécuter un outil particulier selon les besoins.

* Simplifiez l&#39;ajout futur de nouveaux outils, tels que l&#39;ajout de nouveaux outils au module externe, en ajoutant simplement une nouvelle commande pour le développeur et une simple mise à jour du module externe pour l&#39;utilisateur, afin que l&#39;expérience reste cohérente avec une plus grande valeur ajoutée.

## Présentation du module externe {#understanding-plugin}

Le `aio-cli-plugin-aem-cloud-service-migration` reformate le code client, la structure de référentiel ou les configurations sur l’ordinateur local du client. Cette page présente les exigences détaillées et les décisions de conception de l’expérience unifiée.
Il est disponible en tant que source libre pour la communauté pour étendre les applications sur mesure.

Ces outils unifient tous les outils de refactorisation du code dans une application node.js exposée `aio-cli plugin` afin de fournir une expérience utilisateur cohérente à l’utilisateur. Le module externe analyse la base de code local du client et produit AEM sous la forme d&#39;un code, de configurations et de packages compatibles avec le Cloud Service, qui peuvent ensuite être déployés sur des environnements Cloud Service.

Le module externe se compose de deux parties principales :

* **Interface utilisateur**

   `aio-cli` pour exécuter un ou plusieurs outils de migration (en chaînant les outils à exécuter de manière séquentielle)`config.yaml` qui accepte les paramètres d’entrée requis

* **Suite d’outils de migration sous-jacente**

   Les outils de migration exécutent leurs fonctionnalités en :

   * Analyser la section correspondante du code du client et effectuer la migration (en fonction de l’implémentation du code pour connaître les meilleures pratiques) pour produire la sortie qui peut ensuite être validée et déployée.

   * Enregistrement des opérations effectuées lors de la migration, dans un ordre cohérent, afin de produire un rapport de synthèse.

## Disponibilité {#availability}

Vous pouvez installer et utiliser le `aio-cli-plugin-aem-cloud-service-migration` via `aio-cli`.

>[!NOTE]
>Actuellement, cet outil n&#39;est intégré qu&#39;au Convertisseur Répartiteur.

Reportez-vous à la ressource [Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) pour en savoir plus sur l’utilisation et comment vous pouvez contribuer à ce code de module externe ouvert dans GitHub.


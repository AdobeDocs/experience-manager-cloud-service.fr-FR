---
title: Intégration d’AEM et de Magento à l’aide de Commerce Integration Framework – FAQ
description: Intégration d’AEM et de Magento à l’aide de Commerce Integration Framework – FAQ
translation-type: tm+mt
source-git-commit: cafe8825fe34f158c74b94b95b7252394de26e4d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 100%

---


# Intégration d’AEM et de Magento à l’aide de Commerce Integration Framework – FAQ


## 1. GraphQL est-il utilisé uniquement pour Magento ou sera-t-il disponible pour interroger du contenu créé dans AEM JCR ?

Adobe a adopté les API GraphQL de Magento comme API commerciales officielles pour toutes les données liées au commerce. Par conséquent, AEM utilise GraphQL pour échanger des données commerciales avec Magento et tout moteur de commerce via I/O Runtime.

## 2. Comment Adobe I/O Runtime entre-t-il en jeu ? Est-ce qu’AEM parle directement à Magento ?

AEM peut se connecter directement à Magento sans couche I/O Runtime. S’il est nécessaire d’intégrer un serveur principal de commerce non Magento (solution tierce) à AEM, la plate-forme I/O Runtime peut être utilisée pour héberger la couche de mappage afin de connecter les API GraphQL Magento aux API de solutions tierces. Pour plus d’informations à ce sujet, reportez-vous à cette [mise en œuvre de référence](https://github.com/adobe/commerce-cif-graphql-integration-reference). Pour les solutions non Magento, AEM serait configuré pour pointer vers le point d’entrée I/O Runtime.

La plate-forme I/O Runtime peut également être utilisée pour étendre ou personnaliser les services de commerce. Pour ces cas d’utilisation, vous appelleriez le point d’entrée I/O Runtime qui hébergera ensuite une mise en œuvre personnalisée du service concerné. Les cas d’utilisation d’intégration et d’extension peuvent être combinés.

## 3. Les ressources de produit (images) peuvent-elles être stockées et référencées à partir d’AEM via l’administration de Magento ? Comment les ressources issues de Dynamic Media peuvent-elles être utilisées ?

Il n’existe actuellement pas d’intégration AEM Assets – Magento. Pour pallier ce problème, vous pouvez stocker les ressources de produit (images) dans AEM Assets, mais vous devrez stocker manuellement les URL de ressources dans Magento. Dynamic Media fait désormais partie d’AEM Assets et fonctionnera de la même manière.

## 4. L’emplacement de déploiement de Magento est-il important ? (Sur site ou dans le cloud)

Peu importe où Magento est déployé. L’intégration et la nouvelle interface du magasin AEM Venia fonctionneront indépendamment du modèle de déploiement. Cependant, si Magento est déployé en fonction de l’architecture de référence E2E approuvée, les tests E2E seront exécutés par rapport aux IPC de performances collectés qui représentent le profil d’un client d’entreprise. Vous obtiendrez ainsi des informations supplémentaires que vous pourrez utiliser comme référence.

## 5. Comment les pages de catalogues ou de produits sont-elles créées dans AEM ? Comment persistent-elles dans AEM ?

Les pages de catalogues et de produits sont créées et mises en cache dynamiquement dans AEM en fonction de modèles de pages de catalogues et de produits génériques. Aucune donnée de produit ni de catalogue n’est importée et stockée dans AEM.

## 6. Mettez-vous également en cache les données de tarification et autres données par l’intermédiaire du Dispatcher ? Cela provoque-t-il un problème fréquent d’invalidation du cache ?

Les données dynamiques telles que le prix ou l’inventaire ne sont pas mises en cache dans le Dispatcher. Les données dynamiques sont récupérées côté client avec des composants web directement via les API GraphQL. Seules les données statiques (telles que les données de produit ou de catégorie) sont mises en cache dans le Dispatcher. Si les données de produit sont modifiées, le cache doit être invalidé.

## 7. Comment l’invalidation du cache pour AEM Dispatcher fonctionne-t-elle avec AEM Magento ?

Nous vous recommandons de configurer l’invalidation de cache TTL pour les pages mises en cache dans le Dispatcher. Pour les informations dynamiques telles que le prix ou l’inventaire, il est recommandé d’effectuer le rendu de la date côté client. Pour plus d’informations sur l’invalidation de cache TTL, reportez-vous à [AEM Dispatcher](https://helpx.adobe.com/fr/experience-manager/kb/optimizing-the-dispatcher-cache.html)

## 8. Pourquoi n’utilisez-vous pas We.Retail ?

Le thème Venia (développé par Magento) est utilisé. Il est d’abord mobile et aligné sur le PWA de Magento. Le thème Venia représente la toute dernière évolution en termes de style CSS et de composants principaux AEM.

## 9. Lors de la mise à jour des données de produit dans Magento, s’agit-il d’un transfert Push en temps réel vers AEM ? Ou s’agit-il d’un traitement par lots ?

Le module complémentaire CIF utilisé avec AEM Cloud Service permet aux données de passer de Magento à AEM à la demande. Par conséquent, il ne s’agit pas d’un transfert Push en temps réel ni d’un traitement par lots en cas de mise à jour dans Magento.

## 10. Y a-t-il une recommandation sur la recherche unifiée dans le contenu AEM avec Commerce ?

Une mise en œuvre de référence de recherche de produit est fournie, mais aucune recherche unifiée avec du contenu. Cette fonctionnalité est généralement très spécifique au client et mieux résolue au niveau du projet.

## 11. Comment la recherche fonctionne-t-elle avec AEM-Magento en utilisant CIF ?

CIF fournit des composants de barre de recherche et de résultats de recherche. Le composant de barre de recherche envoie une requête GraphQL avec le terme recherché à Magento. Magento renvoie ensuite une liste de produits qui inclut le nom, le prix, le SLUG, etc., du produit. Le composant de résultats de recherche affiche ensuite les résultats de la recherche dans une vue de galerie sur une page de résultats de recherche créée dans AEM. La recherche prend en charge la recherche de texte intégral de base. Nous utilisons la clé SLUG/url pour établir une référence au PDP.

## 11. Comment les données de produit peuvent-elles être utilisées dans MSM ou les traductions ?

Les données produit sont généralement déjà traduites dans PIM ou Magento. L’intégration AEM – Magento prend en charge la connexion à plusieurs magasins et vues de magasin Magento. Dans une configuration MSM, généralement un site AEM est lié à une vue de magasin Magento.

## 13. Comment CIF fonctionne-t-il avec les autres plates-formes commerciales ?

L’intégration à des solutions tierces telles que d’autres solutions commerciales (non Magento) est effectuée via la plate-forme I/O Runtime.  Nous avons créé une [mise en œuvre de référence](https://github.com/adobe/commerce-cif-graphql-integration-reference) pour démontrer comment cela est effectué. Cela permet de réutiliser [AEM CIF Cloud Connector](https://github.com/adobe/commerce-cif-connector) et les [composants principaux CIFAEM](https://github.com/adobe/aem-core-cif-components) en exposant l’API GraphQL Magento au-dessus d’une plate-forme de commerce tierce. Pour offrir une flexibilité et une évolutivité optimales, cette couche d’intégration est déployée sur la [plate-forme Adobe I/O Runtime sans serveur](https://www.adobe.io/apis/experienceplatform/runtime.html).

## 14. Existe-t-il un moyen d’améliorer les données de produit avec le texte commercial ? Où effectuer cette opération ? Dans AEM ou dans Magento ?

Il existe de multiples façons d’y parvenir et cela dépendra du cas d’utilisation. Une solution consisterait à utiliser des attributs personnalisés. Autorisez les auteurs AEM à transformer ces champs dans l’éditeur de produits d’AEM et à resynchroniser les données dans le PIM. Une autre option consisterait à exploiter les fragments d’expérience AEM qui sont injectés dans les pages de produits.

## 15. L’intégration entre AEM et Magento change-t-elle lorsque la plate-forme Adobe I/O Runtime est utilisée ?

Les clients qui souhaitent étendre les services de commerce peuvent utiliser la même intégration et écrire des séquences d’actions hébergées sur la plateforme I/O Runtime pour injecter une logique métier et enrichir les services de commerce.

## 16. Comme AEM crée dynamiquement des pages de produits et de catalogues à partir d’un modèle générique dans AEM, que verrais-je si j’ouvrais CRXDE Lite et que je vérifiais le contenu ? Verrais-je une arborescence complète de produits basée sur les produits figurant dans Magento ? Dans le cas contraire, comment un auteur pourrait-il améliorer ces pages ?

Il n’existe plus de catalogue JCR ni de pages produit. Voir question 12.

## 17. L’interface du magasin SPA fonctionnera-t-elle avec l’éditeur de SPA AEM ?

AEM peut être utilisé comme outil de création pour n’importe quel type d’interface de magasin. Actuellement, le rendu hybride est utilisé pour la nouvelle interface de magasin. A l’avenir, AEM sera utilisé pour la création avec SPA et PWA.

## 18. Comment PIM opère-t-il dans ce framework ?

Les données PIM sont exposées à AEM et aux clients par le biais de requêtes GraphQL. Nous recommandons d’intégrer PIM au moteur de commerce (Magento ou autre) afin que les données PIM puissent être récupérées à partir de ce dernier.

## 19. Comment pouvons-nous garantir la conformité PCI lors de l’utilisation d’AEM pour toute la couche de présentation ?

Lors de l’utilisation d’AEM dans un déploiement cloud AMS et Magento, il est obligatoire d’utiliser des méthodes de paiement abstraites. Le client du navigateur est ainsi en communication directe avec le fournisseur de passerelle de paiement, de sorte que ni les clouds Adobe ni les clouds Magento ne contiennent ni ne transmettent les données du détenteur de carte. Cette approche offre une couverture de conformité PCI pour les piles de technologies et les centres de données. Cependant, il existe d’autres aspects à considérer pour assurer une conformité PCI entière, tels que la façon dont les employés interagissent avec le système et les données. Pour plus d’informations sur la conformité PCI Magento, consultez https://magento.com/pci-compliance

## 20. Comment puis-je demander une licence d’évaluation d’I/O Runtime ?

Vous pouvez demander une licence d’évaluation pour utiliser I/O Runtime [ici](https://github.com/AdobeDocs/adobeio-runtime/blob/master/overview/request_a_trial.md).




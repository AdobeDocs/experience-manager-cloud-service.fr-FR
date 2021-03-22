---
title: AEM - Intégration du commerce à l’aide du cadre d’intégration du commerce FAQ
description: AEM - Intégration du commerce à l’aide du cadre d’intégration du commerce FAQ
translation-type: tm+mt
source-git-commit: ad831b2cc3657666678662eeff0eaf371ce4da49
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 68%

---


# AEM - Intégration du commerce à l’aide du cadre d’intégration du commerce FAQ


## 1. Est-ce que CIF GraphQL est uniquement utilisé pour le commerce ou sera-t-il disponible pour interroger du contenu créé sur AEM JCR ?

Adobe a adopté les API GraphQL de Magento comme API commerciales officielles pour toutes les données liées au commerce. Par conséquent, AEM utilise GraphQL pour échanger des données commerciales avec Magento et tout moteur de commerce via I/O Runtime. Cette API GraphQL est indépendante de l’API GraphQL AEM pour accéder aux fragments de contenu.

## 2. Comment Adobe I/O Runtime entre-t-il en jeu ? Est-ce qu’AEM parle directement à Magento ?

AEM peut se connecter directement à Magento sans couche I/O Runtime. S’il est nécessaire d’intégrer un serveur principal de commerce non Magento (solution tierce) à AEM, la plate-forme I/O Runtime peut être utilisée pour héberger la couche de mappage afin de connecter les API GraphQL Magento aux API de solutions tierces. Pour plus d’informations à ce sujet, reportez-vous à cette [mise en œuvre de référence](https://github.com/adobe/commerce-cif-graphql-integration-reference). Pour les solutions non Magento, AEM serait configuré pour pointer vers le point d’entrée I/O Runtime.

La plate-forme I/O Runtime peut également être utilisée pour étendre ou personnaliser les services de commerce. Pour ces cas d’utilisation, vous appelleriez le point d’entrée I/O Runtime qui hébergera ensuite une mise en œuvre personnalisée du service concerné. Les cas d’utilisation d’intégration et d’extension peuvent être combinés.

## 3. Les ressources de produit (images) peuvent-elles être stockées et référencées à partir d’AEM via l’administration de Magento ? Comment les ressources issues de Dynamic Media peuvent-elles être utilisées ?

Il n’existe actuellement pas d’intégration AEM Assets – Magento. Pour pallier ce problème, vous pouvez stocker les ressources de produit (images) dans AEM Assets, mais vous devrez stocker manuellement les URL de ressources dans Magento. Dynamic Media fait désormais partie d’AEM Assets et fonctionnera de la même manière.

## 4. Est-ce important de savoir où la solution commerciale est déployée ? (Sur site ou dans le cloud)

Peu importe où votre solution commerciale est déployée. L’intégration et la nouvelle interface du magasin AEM Venia fonctionneront indépendamment du modèle de déploiement. Cependant, si Magento est déployé en fonction de l’architecture de référence E2E approuvée, les tests E2E seront exécutés par rapport aux IPC de performances collectés qui représentent le profil d’un client d’entreprise. Vous obtiendrez ainsi des informations supplémentaires que vous pourrez utiliser comme référence.

## 5. Comment les pages de catalogues ou de produits sont-elles créées dans AEM ? Comment persistent-elles dans AEM ?

Les pages de catalogues et de produits sont créées et mises en cache dynamiquement dans AEM en fonction de modèles de pages de catalogues et de produits génériques. Aucune donnée de produit ni de catalogue n’est importée et stockée dans AEM.

## 6. Lors de la mise à jour des données de produit dans votre solution commerciale, s&#39;agit-il d&#39;une transmission en temps réel vers l&#39;AEM ? Ou s’agit-il d’un traitement par lots ?

Le module complémentaire CIF utilisé avec AEM Cloud Service permet aux données de passer de la solution commerciale à AEM à la demande. Par conséquent, il ne s’agit pas d’un processus Push en temps réel ou d’un traitement par lot lorsqu’une mise à jour est disponible dans votre solution commerciale.

## 7. Quelle est la taille du catalogue AEM avec la prise en charge de CIF ?

Cela dépend de quelques aspects supplémentaires que vous devez prendre en compte. Quel est le taux de cache de vos données et pages de catalogue ? Combien de demandes simultanées attendez-vous pendant les heures de pointe ? Quelle est l&#39;évolutivité des API de vos solutions commerciales ?

## 8. Comment PIM opère-t-il dans ce framework ?

Les données PIM sont exposées à AEM et aux clients par le biais de requêtes GraphQL. Nous recommandons d&#39;intégrer PIM au moteur de commerce (Magento ou autres) afin que les données PIM puissent être récupérées à partir du moteur de commerce.

## 9. Mettez-vous également en cache les données de tarification et autres données par l’intermédiaire du Dispatcher ? Cela provoque-t-il un problème fréquent d’invalidation du cache ?

Les données dynamiques telles que le prix ou l’inventaire ne sont pas mises en cache dans le Dispatcher. Les données dynamiques sont récupérées côté client avec des composants web directement via les API GraphQL. Seules les données statiques (telles que les données de produit ou de catégorie) sont mises en cache dans le Dispatcher. Si les données de produit sont modifiées, le cache doit être invalidé.

## 10. Comment l&#39;invalidation du cache pour AEM Répartiteur fonctionne-t-elle avec AEM et le commerce ?

Nous vous recommandons de configurer l’invalidation de cache TTL pour les pages mises en cache dans le Dispatcher. Pour les informations dynamiques telles que le prix ou l’inventaire, il est recommandé d’effectuer le rendu de la date côté client. Pour plus d’informations sur l’invalidation de cache TTL, reportez-vous à [AEM Dispatcher](https://helpx.adobe.com/fr/experience-manager/kb/optimizing-the-dispatcher-cache.html)

## 11. Y a-t-il une recommandation sur la recherche unifiée dans le contenu AEM avec Commerce ?

Une mise en œuvre de référence de recherche de produit est fournie, mais aucune recherche unifiée avec du contenu. Cette fonctionnalité est généralement très spécifique au client et mieux résolue au niveau du projet.

## 12. Comment la recherche fonctionne-t-elle avec l&#39;AEM et le commerce à l&#39;aide du FIC ?

CIF fournit des composants de barre de recherche et de résultats de recherche. Le composant de la barre de recherche envoie une requête GraphQL avec le terme de recherche à la solution commerciale, qui renvoie ensuite une liste de produits qui inclut le nom du produit, le prix, le SLUG, etc. Le composant de résultats de recherche affiche ensuite les résultats de la recherche dans une vue de galerie sur une page de résultats de recherche créée dans AEM. La recherche prend en charge la recherche de texte intégral de base. Nous utilisons la clé SLUG/url pour établir une référence au PDP.

## 13. Comment les données de produit peuvent-elles être utilisées dans MSM ou les traductions ?

Les données produit sont généralement déjà traduites dans PIM ou Magento. L’intégration AEM – Magento prend en charge la connexion à plusieurs magasins et vues de magasin Magento. Dans une configuration MSM, généralement un site AEM est lié à une vue de magasin Magento.

## 14. Comment le FIC fonctionne-t-il avec les plates-formes de commerce non Magento ?

L’intégration à des solutions tierces telles que d’autres solutions commerciales (non Magento) est effectuée via la plate-forme I/O Runtime.  Nous avons créé une [mise en œuvre de référence](https://github.com/adobe/commerce-cif-graphql-integration-reference) pour démontrer comment cela est effectué. Cela permet de réutiliser [AEM CIF Cloud Connector](https://github.com/adobe/commerce-cif-connector) et les [composants principaux CIFAEM](https://github.com/adobe/aem-core-cif-components) en exposant l’API GraphQL Magento au-dessus d’une plate-forme de commerce tierce. Pour offrir une flexibilité et une évolutivité optimales, cette couche d’intégration est déployée sur la [plate-forme Adobe I/O Runtime sans serveur](https://www.adobe.io/apis/experienceplatform/runtime.html).

## 15. Existe-t-il un moyen d’améliorer les données de produit avec le texte commercial ? Où effectuer cette opération ? En AEM ou dans la solution commerciale ?

Nous vous recommandons de gérer les données et le contenu liés au marketing dans AEM. Décorez les données de produit issues de votre solution commerciale avec des attributs supplémentaires à l’aide de fragments de contenu ou créez et liez des fragments d’expérience pour un contenu sans structure avec vos produits.

## 16. L’intégration entre AEM et Magento change-t-elle lorsque la plate-forme Adobe I/O Runtime est utilisée ?

Les clients qui souhaitent étendre les services de commerce peuvent utiliser la même intégration et écrire des séquences d’actions hébergées sur la plateforme I/O Runtime pour injecter une logique métier et enrichir les services de commerce.

## 17. L’interface du magasin SPA fonctionnera-t-elle avec l’éditeur de SPA AEM ?

AEM peut être utilisé comme outil de création pour n’importe quel type d’interface de magasin. Actuellement, le rendu côté serveur et côté client (hybride) est utilisé dans AEM vitrine. Nous publierons plus tard en 2021 la prise en charge des PWA pour la création de contenu sans tête et sans tête.


## 18. Comment pouvons-nous garantir la conformité PCI lors de l’utilisation d’AEM pour toute la couche de présentation ?

Nous vous recommandons d&#39;utiliser des méthodes de paiement abstraites. Le client du navigateur est ainsi en communication directe avec le fournisseur de passerelle de paiement, de sorte que ni l&#39;Adobe ni les solutions commerciales ne contiennent ni ne transmettent les données du détenteur de la carte. Cette approche ne requiert qu&#39;une conformité PCI de niveau 3. Cependant, il existe d’autres aspects à considérer pour assurer une conformité PCI entière, tels que la façon dont les employés interagissent avec le système et les données. Pour plus d’informations sur la conformité PCI Magento, consultez https://magento.com/pci-compliance

## 19. Si j&#39;utilise des versions de cloud Magento et AEM, est-ce que cette solution conjointe est compatible PCI ?

Oui, le questionnaire d&#39;auto-évaluation D et l&#39;attestation de conformité sont disponibles sur demande.


## 20. Comment puis-je demander une licence d’évaluation d’I/O Runtime ?

Vous pouvez demander une licence d’évaluation pour utiliser I/O Runtime [ici](https://adobeio.typeform.com/to/obqgRm).

---
title: AEM - Intégration des Magento à l’aide de Commerce Integration Framework FAQ
description: AEM - Intégration des Magento à l’aide de Commerce Integration Framework FAQ
translation-type: tm+mt
source-git-commit: cafe8825fe34f158c74b94b95b7252394de26e4d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---


# AEM - Intégration des Magento à l’aide de Commerce Integration Framework FAQ


## 1. GraphQL est-il utilisé uniquement pour le Magento ou sera-t-il disponible pour interroger du contenu créé sur AEM JCR ?

Adobe a adopté les API GraphQL du Magento comme API commerciale officielle pour toutes les données liées au commerce. Par conséquent, AEM utilise GraphQL pour échanger des données commerciales avec un Magento et avec tout moteur de commerce via l&#39;exécution d&#39;E/S.

## 2. Comment les E/S d&#39;Adobe entrent-elles en jeu ? Est-ce que AEM parle directement au Magento ?

AEM peut se connecter directement au Magento sans couche d&#39;exécution d&#39;E/S. S’il est nécessaire d’intégrer un serveur principal de commerce non Magento (solution tierce) à AEM, la plate-forme d’exécution E/S peut être utilisée pour héberger la couche de mappage afin de connecter les API GraphQL Magento à toute API de solutions tierces. Pour plus d&#39;informations à ce sujet, reportez-vous à cette mise en oeuvre [de](https://github.com/adobe/commerce-cif-graphql-integration-reference)référence. Pour les solutions non Magento, AEM serait configuré pour pointer vers le point de terminaison E/S Runtime.

La plate-forme E/S Runtime peut également être utilisée pour étendre ou personnaliser les services de commerce. Pour ces cas d&#39;utilisation, vous appelleriez le point de terminaison E/S Runtime qui hébergera ensuite une implémentation personnalisée du service concerné. Les cas d&#39;utilisation d&#39;intégration et d&#39;extension peuvent être combinés.

## 3. Les ressources du produit (images) peuvent-elles être stockées et référencées à partir d’AEM via l’administration du Magento ? Comment les actifs de Dynamic Media peuvent-ils être consommés ?

Il n&#39;y a pas actuellement d&#39;intégration AEM Assets-Magento. Pour pallier ce problème, vous pouvez stocker des ressources de produit (images) en AEM Assets, mais vous devrez stocker manuellement les URL de ressources dans le Magento. Dynamic Media fait maintenant partie des AEM Assets et va fonctionner de la même manière.

## 4. Est-ce important de savoir où le Magento est déployé ? (En direct ou dans le cloud)

Peu importe où le Magento est déployé. L’intégration et la nouvelle interface du magasin AEM Venia fonctionneront indépendamment du modèle de déploiement. Cependant, s&#39;il est déployé en fonction de l&#39;architecture de référence E2E approuvée, les tests E2E seront exécutés par rapport aux IPC de performances rassemblés pour représenter le profil d&#39;un client d&#39;entreprise. Vous obtiendrez ainsi des informations supplémentaires que vous pourrez utiliser comme référence.

## 5. Comment les pages de catalogue ou les pages de produit sont-elles créées dans AEM ? Comment persistent-ils en AEM ?

Les pages de catalogue et les pages de produit sont créées et mises en cache dynamiquement dans AEM en fonction de modèles de catalogue et de page de produit génériques. Aucune donnée de produit ou de catalogue n’est importée et stockée dans AEM.

## 6. Mettez-vous également en cache les prix et d’autres données par l’intermédiaire du Dispatcher. Cela soulève-t-il un problème fréquent d&#39;invalidation du cache ?

Les données dynamiques telles que le prix ou le stock ne sont pas mises en cache sur le Dispatcher. Les données dynamiques sont récupérées côté client avec des composants Web directement via les API GraphQL. Seules les données statiques (telles que les données de produit ou de catégorie) sont mises en cache sur le Dispatcher. Si les données du produit sont modifiées, le cache doit être invalidé.

## 7. Comment l’invalidation du cache pour AEM Dispatcher fonctionne-t-elle avec AEM-Magento ?

Nous vous recommandons de configurer l’invalidation du cache TTL pour les pages mises en cache sur le Dispatcher. Pour les informations dynamiques telles que le prix ou l’action, il est recommandé de rendre la date côté client. Pour plus d’informations sur l’invalidation du cache basé sur TTL, reportez-vous à [AEM Dispatcher](https://helpx.adobe.com/experience-manager/kb/optimizing-the-dispatcher-cache.html)

## 8. Pourquoi n&#39;utilisez-vous pas We.Retail ?

Le thème de Venia (développé par le Magento) est utilisé qui est d’abord mobile et aligné avec le PWA du Magento. Le thème Venia représente les derniers composants de base et de style CSS en termes de style et d’AEM.

## 9. Lors de la mise à jour des données de produit en Magento, s’agit-il d’une transmission en temps réel vers l’AEM ? Ou est-ce un traitement par lots ?

Le module complémentaire CIF utilisé avec AEM Cloud Service permet aux données de passer de Magento à AEM à la demande. Par conséquent, il ne s’agit pas d’un processus Push en temps réel ou d’un traitement par lot en cas de mise à jour dans le Magento.

## 10. Existe-t-il une recommandation sur la recherche unifiée dans AEM contenu avec Commerce ?

Une implémentation de référence de recherche de produit est fournie mais aucune recherche unifiée avec du contenu. Cette fonctionnalité est généralement très spécifique au client et mieux résolue au niveau du projet.

## 11. Comment la recherche fonctionne-t-elle avec AEM-Magento qui utilise CIF ?

CIF fournit des composants de barre de recherche et de résultat de recherche. Le composant de la barre de recherche envoie une requête GraphQL avec le terme recherché au Magento. Le Magento renvoie ensuite une liste de produit qui inclut le nom, le prix, la BANDE, etc. Le composant Résultat de la recherche affiche ensuite les résultats de la recherche dans une vue de galerie sur une page de résultats de la recherche créée dans AEM. La recherche prend en charge la recherche de texte intégral de base. Nous utilisons la touche SLUG/url pour créer une référence au PDP.

## 11. Comment les données des produits peuvent-elles être utilisées dans les médias multimédias ou les traductions ?

Les données des produits sont généralement traduites en PIM ou en Magento. L’intégration AEM - Magento prend en charge la connexion à plusieurs magasins et vues de stockage Magento. Dans une configuration MSM, généralement, un site AEM est lié à une vue de stockage Magento.

## 13. Comment le FIF fonctionne-t-il avec d&#39;autres plates-formes commerciales ?

L&#39;intégration à des solutions tierces, telles que d&#39;autres solutions commerciales (non-Magento) est effectuée via la plate-forme d&#39;exécution E/S.  Nous avons créé une mise en oeuvre [de](https://github.com/adobe/commerce-cif-graphql-integration-reference) référence pour démontrer comment cela se fait. Cela permet la réutilisation de l’ [AEM interface CIF Cloud Connector](https://github.com/adobe/commerce-cif-connector) et des composants [principaux](https://github.com/adobe/aem-core-cif-components) CIFAEM en exposant l’API GraphQL Magento sur toute plate-forme commerciale tierce. Pour offre une flexibilité et une évolutivité optimales, cette couche d’intégration est déployée sur la plate-forme [](https://www.adobe.io/apis/experienceplatform/runtime.html)Adobe I/O Runtime sans serveur.

## 14. Existe-t-il un moyen d&#39;améliorer les données sur les produits avec le texte commercial ? Où fais-tu ça ? En AEM ou en Magento ?

Il existe de multiples façons d&#39;y parvenir et cela dépendra du cas d&#39;utilisation. Une solution consisterait à utiliser des attributs personnalisés. Permettre aux auteurs d’AEM de muter ces champs dans l’éditeur de produits AEM et de synchroniser à nouveau les données dans le PIM. Une autre option consisterait à exploiter les fragments d’expérience AEM qui sont injectés dans les pages de produits.

## 15. L&#39;intégration entre AEM et Magento change-t-elle lorsque la plate-forme Adobe I/O Runtime est utilisée ?

Les clients qui souhaitent étendre les services de commerce peuvent utiliser la même intégration et écrire des séquences d&#39;actions hébergées sur la plateforme d&#39;exécution E/S pour injecter une logique métier et enrichir les services de commerce.

## 16. Comme AEM crée dynamiquement des pages de produits et de catalogues à partir d&#39;un modèle générique en AEM, que verrais-je si j&#39;ouvrais le CRXDE Lite et que je vérifiais le contenu ? Est-ce que je verrais une arborescence complète de produits basée sur les produits en Magento ? Dans le cas contraire, comment un auteur pourrait-il améliorer ces pages ?

Il n’existe plus de catalogue JCR ou de pages de produits. Voir question 12.

## 17. L’application d’une seule page stockée fonctionnera-t-elle de manière frontale avec AEM éditeur d’une application d’une seule page ?

AEM peut être utilisé comme outil de création pour n&#39;importe quel type d&#39;interface de magasin. Actuellement, le rendu hybride est utilisé pour le nouveau magasin frontal. A l’avenir, l’AEM sera utilisé pour la création avec l’application d’une seule page et avec le PWA.

## 18. Comment la GIR joue-t-elle son rôle dans ce cadre ?

Les données PIM sont exposées aux AEM et aux clients par le biais de requêtes GraphQL. Nous recommandons d&#39;intégrer PIM au moteur de commerce (Magento ou autre) afin que les données PIM puissent être récupérées à partir du moteur de commerce.

## 19. Comment pouvons-nous garantir la conformité PCI lors de l&#39;utilisation d&#39;AEM pour toute la couche de présentation ?

Lors de l’utilisation de l’AEM sur AMS et du déploiement de cloud Magento, il est obligatoire d’utiliser des méthodes de paiement abstraites. Le client du navigateur est ainsi en communication directe avec le fournisseur de passerelle de paiement, de sorte que ni les clouds d&#39;Adobe ni les clouds de Magento ne contiennent ni ne transmettent de données de détenteur de carte. Cette approche offre une couverture de conformité PCI pour les piles de technologies et les datacenters. Cependant, il y a d&#39;autres éléments à considérer comme entièrement conformes à PCI, comme la façon dont les employés interagissent avec le système et les données. Pour plus d&#39;informations sur la conformité PCI Magento, consultez https://magento.com/pci-compliance

## 20. Comment puis-je demander une licence d&#39;évaluation d&#39;E/S Runtime ?

Vous pouvez demander une licence d&#39;évaluation pour utiliser l&#39;exécution d&#39;E/S [ici](https://github.com/AdobeDocs/adobeio-runtime/blob/master/overview/request_a_trial.md).




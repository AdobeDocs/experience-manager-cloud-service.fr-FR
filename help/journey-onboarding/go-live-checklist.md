---
title: Liste de contrôle de mise en production
description: Découvrir tous les éléments à appliquer pour réussir une mise en production avec AEM as a Cloud Service
exl-id: b424a9db-0f3b-4a8d-be84-365d68df46ca
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 100%

---

# Liste de contrôle de mise en production {#Go-Live-Checklist}

Passez en revue cette liste d’activités pour parvenir à une mise en production en douceur et réussie.

* Exécutez un pipeline de production de bout en bout avec des tests fonctionnels et d’interface utilisateur pour garantir une expérience du produit AEM **toujours actuelle**. Reportez-vous aux ressources suivantes.
   * [Mises à jour de la version d’AEM](/help/implementing/deploying/aem-version-updates.md)
   * [Tests fonctionnels personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [Tests de l’interface utilisateur](/help/implementing/cloud-manager/ui-testing.md)
* Si vous migrez depuis AEM 6.5, migrez le contenu vers la production et vérifiez qu’un sous-ensemble approprié est disponible lors de l’évaluation pour les tests.
   * Les bonnes pratiques des DevOps pour AEM impliquent que le code passe du développement à l’environnement de production pendant que le contenu passe aux environnements de production.
* Planifiez une période de gel du code et du contenu.
   * Consultez également [Chronologies de gel du code et du contenu pour la migration](#code-content-freeze).
* Effectuez la dernière mise à jour du contenu.
* Validez les configurations du Dispatcher.
   * Utilisez un programme de validation de Dispatcher local qui facilite la configuration, la validation et la simulation locale du Dispatcher.
      * [Configurez les outils du Dispatcher local.](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools#prerequisites)
   * Examinez attentivement la configuration de l’hôte virtuel.
      * La solution la plus simple (et celle par défaut) est d’inclure `ServerAlias *` dans votre fichier d’hôte virtuel dans le `/dispatcher/src/conf.d/available_vhostsfolder`.
         * Ainsi, les alias d’hôte utilisés par les tests fonctionnels du produit, l’invalidation du cache du Dispatcher et les clones pourront tous fonctionner.
      * Cependant, si le `ServerAlias *` n’est pas acceptable, vous devez autoriser au minimum les entrées `ServerAlias` suivantes en plus de vos domaines personnalisés :
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* Configurez le CDN, le SSL et le DNS.
   * Si vous utilisez votre propre réseau de diffusion de contenu, saisissez un ticket d’assistance pour configurer le routage approprié.
      * Consultez [Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) dans la documentation du réseau de diffusion de contenu pour plus d’informations.
      * Configurez le SSL et le DNS conformément à la documentation de votre fournisseur de réseau de diffusion de contenu.
   * Si vous n’utilisez pas de réseau de diffusion de contenu supplémentaire, configurez le SSL et le DNS conformément à la documentation suivante :
      * Gestion des certificats SSL
         * [Introduction à la gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [Gestion du certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Gestion des noms de domaine personnalisés (DNS)
         * Pour vous assurer que le changement de DNS n’entraînera pas de problèmes inattendus, il est recommandé de créer un sous-domaine de test pour connecter votre instance de production avant la mise en ligne, ainsi que d’effectuer une batterie de tests UAT. Ainsi, si votre domaine est exemple.com, vous pouvez créer un sous-domaine test.exemple.com et l’appliquer à l’instance de production. Lors du test UAT du domaine, les éléments tels que la redirection des liens, la mise en cache et les configurations de Dispatcher nécessitent toute votre attention.
         * [Introduction aux noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * N’oubliez pas de valider le jeu TTL pour votre enregistrement DNS.
      * Le TTL est la durée pendant laquelle un enregistrement DNS reste dans un cache avant de demander une mise à jour au serveur.
      * Avec un TTL très élevé, les mises à jour de votre enregistrement DNS prendront plus de temps à se propager.
* Exécutez des tests de performance et de sécurité qui répondent aux besoins et aux objectifs de votre entreprise.
   * Effectuez des tests dans un environnement d’évaluation.  Celui-ci a la même taille que l’environnement de production.
   * Les environnements de développement n’ont pas la même taille que ceux destinés à l’évaluation et à la production.
* Effectuez une coupure et assurez-vous que la mise en production réelle est effectuée sans aucun nouveau déploiement ni mise à jour du contenu.
* Créez des profils de notification pour les utilisateurs et les utilisatrices de l’Admin Console. Consultez [Profils de notification](/help/journey-onboarding/notification-profiles.md)
* Vous pouvez configurer les règles de filtrage du trafic de manière à interdire le trafic qui n’est pas destiné à votre site web.
   * Les règles de filtrage du trafic limitant le débit peuvent être un outil efficace contre les attaques DDoS. Une catégorie spéciale de règles de filtrage du trafic, appelée règles WAF, nécessite une licence séparée.
   * Voir la documentation pour obtenir des [suggestions de règles de démarrage](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules).

Vous pouvez toujours vous référer à cette liste pour recalibrer vos tâches lors de la mise en production.

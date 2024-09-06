---
title: Liste de contrôle de mise en production
description: Découvrez tous les éléments qui doivent être en place pour que l’activation avec AEM as a Cloud Service soit réussie.
exl-id: b424a9db-0f3b-4a8d-be84-365d68df46ca
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 56%

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
* Validation des configurations Dispatcher.
   * Utilisation d’un validateur Dispatcher local qui facilite la configuration, la validation et la simulation locale du Dispatcher
      * [Configurez les outils Dispatcher locaux](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools#prerequisites).
   * Examinez attentivement la configuration de l’hôte virtuel.
      * La solution la plus simple (et par défaut) est d’inclure `ServerAlias *` dans votre fichier d’hôte virtuel dans `/dispatcher/src/conf.d/available_vhostsfolder`. Cela permet aux alias d’hôte utilisés par les tests fonctionnels du produit, l’invalidation du cache Dispatcher et les clones de fonctionner.
      * Cependant, si `ServerAlias *` n’est pas acceptable, au minimum les entrées `ServerAlias` suivantes doivent être autorisées en plus de vos domaines personnalisés :
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
         * [Présentation de la gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Gestion des noms de domaine personnalisés (DNS)
         * Assurez-vous que la coupure DNS n’entraîne pas de problèmes inattendus. Créez un sous-domaine de test auquel connecter votre instance de production avant de démarrer et effectuez un cycle de tests UAT. Ainsi, si votre domaine est example.com, vous pouvez créer un sous-domaine test.example.com et l’appliquer à la production. Lors du test UAT du domaine, recherchez des éléments tels que la redirection des liens, la mise en cache et les configurations Dispatcher appropriées.
         * [Présentation des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Gestion d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * N’oubliez pas de valider le jeu TTL pour votre enregistrement DNS.
      * Le TTL est la durée pendant laquelle un enregistrement DNS reste dans un cache avant de demander une mise à jour au serveur.
      * Si vous avez un TTL très élevé, la propagation des mises à jour de votre enregistrement DNS prend plus de temps.
* Exécutez des tests de performance et de sécurité qui répondent aux besoins et aux objectifs de votre entreprise.
   * Effectuez des tests dans un environnement intermédiaire.  Celui-ci a la même taille que l’environnement de production.
   * Les environnements de développement n’ont pas la même taille que ceux destinés à l’évaluation et à la production.
* Effectuez une coupure et assurez-vous que la mise en production réelle est effectuée sans aucun nouveau déploiement ni mise à jour du contenu.
* Créez des profils de notification utilisateur Admin Console. Consultez [Profils de notification](/help/journey-onboarding/notification-profiles.md)
* Vous pouvez configurer les règles de filtrage du trafic de manière à interdire le trafic qui n’est pas destiné à votre site web.
   * Limite de taux Les règles de filtrage du trafic peuvent être un outil efficace contre les attaques DDoS. Une catégorie spéciale de règles de filtrage du trafic, appelée règles WAF (Web Application Firewall), nécessite une licence distincte.
   * Voir la documentation pour obtenir des [suggestions de règles de démarrage](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules).

Vous pouvez toujours vous référer à cette liste pour recalibrer vos tâches lors de la mise en production.

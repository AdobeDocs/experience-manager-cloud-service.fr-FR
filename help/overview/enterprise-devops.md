---
title: Opérations de développement d’entreprise (DevOps)
description: Découvrez les processus, les méthodes et la communication nécessaires pour faciliter le déploiement et simplifier la collaboration.
exl-id: c8da1fd7-fe3e-4c7b-8fe7-1f7faf02769c
source-git-commit: 1a4c5e618adaef99d82a00e1118d1a0f8536fc14
workflow-type: ht
source-wordcount: '1009'
ht-degree: 100%

---

# Opérations de développement d’entreprise (DevOps){#enterprise-devops}

Les opérations de développement (DevOps) couvrent les processus, les méthodes et les communications requis pour :

* faciliter le déploiement de votre logiciel dans les différents environnements ;
* simplifier la collaboration entre les équipes de développement, de test et de déploiement.

Les opérations de développement visent à éviter les problèmes tels que :

* les erreurs manuelles ;
* les éléments oubliés, comme les fichiers et les détails de configuration ;
* les incohérences, par exemple, entre l’environnement local d’un développeur et d’autres environnements.

## Environnements {#environments}

Adobe Experience Manager (AEM) as a Cloud Service implique généralement plusieurs environnements, utilisés à diverses fins et à différents niveaux :

* [Développement](#development)
* [Assurance qualité](#quality-assurance)
* [Évaluation](#staging)
* [Production](#production-author-and-publish)

>[!NOTE]
>
>L’environnement de production doit avoir au moins un environnement de création et un environnement de publication.
>
>Il est recommandé que tous les autres environnements se composent également d’un environnement de création et de publication afin de refléter l’environnement de production et de permettre des tests lors de phases précoces du projet.

### Développement {#development}

Les personnes en charge du développement doivent développer et personnaliser le projet proposé (qu’il s’agisse d’un site web, d’applications mobiles, de la mise en œuvre de la gestion des actifs numériques, etc.), avec toutes les fonctionnalités requises. Elles :

* développent et personnalisent les éléments nécessaires, comme les modèles, les composants, les workflows et les applications ;
* réalisent la conception ;
* développent les services et les scripts nécessaires pour mettre en œuvre les fonctionnalités requises

La configuration de l’environnement de [development](/help/implementing/developing/introduction/development-guidelines.md) peut dépendre de divers facteurs, bien qu’il soit généralement composé des éléments suivants :

* Un système de développement intégré avec contrôle de version pour fournir une base de code intégrée. Cette base de code intégrée est utilisée pour fusionner et consolider le code des différents environnements de développement utilisés par chaque développeur et développeuse.
* Un environnement personnel pour chaque développeur ou développeuse, résidant habituellement sur son ordinateur local. Le code est synchronisé avec le système de contrôle de version à des intervalles appropriés

Selon l’échelle de votre système, l’environnement de développement peut comprendre une instance de création et une instance de publication.

### Assurance qualité {#quality-assurance}

Cet environnement est utilisé par l’équipe d’assurance qualité afin de tester entièrement votre nouveau système, autant à propos de sa conception que de ses fonctions. Il doit comporter des environnements de création et de publication, avec du contenu approprié, et fournir tous les services nécessaires pour activer une suite complète de tests.

### Évaluation  {#staging}

L’environnement d’évaluation doit être un miroir de l’environnement de production : configuration, code et contenu :

* Il est utilisé pour tester les scripts servant à mettre en œuvre le déploiement réel.
* Il peut être utilisé pour les tests finaux (conception, fonctionnalités et interfaces) avant le déploiement dans les environnements de production.
* Bien qu’il ne soit pas toujours possible que l’environnement d’évaluation soit identique à l’environnement de production, il doit être aussi proche que possible pour activer les tests de performance et de charge.

### Production : création et publication  {#production-author-and-publish}

L’environnement de production est constitué des environnements requis pour [créer et publier](/help/sites-cloud/authoring/author-publish.md) votre mise en œuvre.

Un environnement de production comprend au moins une instance de création et une instance de publication :

* Une instance de [création](#author) pour la saisie du contenu.
* Une instance de [publication](#publish) pour le contenu mis à la disposition de vos visiteurs/utilisateurs.

Selon l’échelle du projet, il se compose souvent de plusieurs personnes chargées de la création, de la publication, ou des deux. À un niveau inférieur, le référentiel peut également être mis en cluster sur plusieurs instances.

#### Création {#author}

En règle générale, les instances de création se trouvent derrière le pare-feu interne. Ce pare-feu interne est l’environnement dans lequel vous et vos collègues effectuez des tâches de création, telles que :

* administrer l’ensemble du système ;
* saisir votre contenu ;
* configurer la mise en page et la conception de votre contenu ;
* activer votre contenu dans l’environnement de publication

Le contenu qui a été activé est mis en package et placé dans la file d’attente de réplication de l’environnement de création. Le processus de réplication transporte ensuite ce contenu dans l’environnement de publication.

Pour répliquer à l’inverse les données générées dans un environnement de publication vers l’environnement de création, un écouteur de réplication dans l’environnement de création interroge l’environnement de publication et récupère ce contenu dans la boîte d’envoi de réplication inversée de l’environnement de publication.

#### Publier {#publish}

En règle générale, un environnement de publication se trouve dans la « zone démilitarisée » (DMZ). Cet environnement est l’endroit où les personnes accèdent à votre contenu (par exemple, par le biais d’un site Web ou sous la forme d’une application mobile) et interagissent avec celui-ci, qu’il soit public ou dans votre intranet. Un environnement de publication :

* contient du contenu répliqué à partir de l’environnement de création ;
* met ce contenu à la disposition des visiteurs et visiteuses ;
* stocke les données d’utilisation générées par vos visiteurs et visiteuses, telles que les commentaires ou autres envois de formulaire ;
* peut être configuré pour ajouter de telles données d’utilisation à une boîte d’envoi, afin que la réplication inversée soit rétablie dans l’environnement de création

L’environnement de publication génère votre contenu dynamiquement en temps réel et le contenu peut être personnalisé pour chaque personne utilisatrice.

## Mouvement de code  {#code-movement}

Propagez toujours le code du bas vers le haut :

* le code est initialement développé sur les environnements de développement locaux puis intégrés
* ...avant d’être soumis de tests approfondis sur les environnements d’assurance qualité...
* ...puis d’être testé à nouveau sur les environnements d’évaluation
* À ce stade seulement, le code doit être déployé dans les environnements de production.

En général, le code (par exemple, les fonctionnalités d’applications web et les modèles de conception personnalisés) est transféré en exportant et en important des packages entre les différents référentiels de contenu. Lorsque c’est approprié, cette réplication peut être configurée en tant que processus automatique.

Les projets sur AEM as a Cloud Service déclenchent souvent un déploiement de code :

* Automatiquement : pour le transfert vers les environnements de développement et d’assurance qualité.
* Manuellement : les déploiements sur les environnements d’évaluation et de production sont effectués de manière plus contrôlée, souvent manuelle ; l’automatisation reste toutefois possible, si nécessaire.

![Mouvement de code](assets/code-movement.png)

## Déplacement de contenu {#content-movement}

Le contenu conçu pour la production doit **toujours** être créé sur l’instance de création de production.

Le contenu ne doit pas suivre le déplacement du code des environnements inférieurs vers les environnements supérieurs. En d’autres termes, il n’est pas recommandé que les auteurs et autrices créent du contenu sur des ordinateurs locaux ou des environnements inférieurs, puis le déplacent vers l’environnement de production. La raison en est que cela peut introduire des erreurs et des incohérences.

Le contenu de production doit être déplacé à partir de l’environnement de production vers l’environnement d’évaluation pour veiller à ce que ce dernier fournisse un environnement de test efficace et précis.

>[!NOTE]
>
>Cette méthodologie ne signifie pas que le contenu d’évaluation doit être continuellement synchronisé avec la production ; les mises à jour régulières sont suffisantes, mais il doit l’être surtout avant de tester une nouvelle itération du code. Le contenu des environnements d’assurance qualité et de développement n’a pas besoin d’être mis à jour aussi fréquemment. Il doit simplement être une bonne représentation du contenu de production.

Le contenu peut être transféré :

* entre les différents environnements, en exportant et en important des packages ;
* entre différentes instances, en répliquant directement (par réplication AEM as a Cloud Service) le contenu (à l’aide d’une connexion HTTP ou HTTPS).

![Déplacement de contenu](assets/content-movement.png)

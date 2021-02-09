---
title: 'Configuration des paramètres DNS '
description: Configuration des paramètres DNS
translation-type: tm+mt
source-git-commit: 1c51560886515e092680c23db3e128758dcd7d99
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 100%

---


# Configuration des paramètres DNS {#configure-dns}

Une fois votre nom de domaine personnalisé vérifié et déployé, vous êtes prêt à mettre à jour les enregistrements DNS pour votre nom de domaine personnalisé avec votre fournisseur DNS. Cela permet à votre site de répondre aux visiteurs. Cette activité est donc généralement effectuée avant le lancement.

>[!NOTE]
>Vous ou la personne appropriée de votre organisation devez être en mesure de vous connecter ou de contacter votre fournisseur DNS (la société auprès de laquelle vous avez acheté le domaine) et d’effectuer des mises à jour de vos paramètres DNS.

Pour ce faire, vous devez déterminer si vous devez configurer vos paramètres DNS sur un enregistrement `CNAME` ou Apex pointant votre nom de domaine personnalisé vers le nom de domaine Cloud Manager. Un enregistrement `CNAME` ou A, une fois configuré, achemine tout le trafic Internet du domaine vers l’endroit où il pointe. Si cet emplacement n’est pas configuré pour desservir le trafic, il y aura une panne. S’il n’a pas été testé, il se peut que le contenu présente des erreurs. Cette étape est donc toujours réalisée une fois les tests terminés et que le client est prêt pour l’activation.

## Enregistrement CNAME {#cname-record}

Les sections suivantes vous aideront à déterminer quel type d’enregistrement convient à votre configuration DNS.

Un enregistrement de nom canonique ou `CNAME` est un type d’enregistrement DNS qui mappe un nom d’alias à un nom de domaine réel ou canonique. Les enregistrements CNAME sont généralement utilisés pour mapper un sous-domaine tel que `www.example.com` au domaine hébergeant le contenu de ce sous-domaine.

Connectez-vous à votre serveur d’enregistrement de domaine et créez un enregistrement CNAME pour pointer votre nom de domaine personnalisé vers la cible, comme indiqué ci-dessous :

| CNAME | Nom de domaine personnalisé pointant vers la cible |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

## Enregistrement APEX {#apex-record}

Un domaine apex est un domaine personnalisé qui ne contient pas de sous-domaine, tel qu’example.com. Un domaine apex est configuré avec un enregistrement `A`, `ALIAS` ou `ANAME` via votre fournisseur DNS. Les domaines Apex doivent pointer vers des adresses IP spécifiques.

Ajoutez tous les enregistrements A suivants aux paramètres DNS de votre domaine via votre fournisseur de domaine :

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

---
title: Configuration des paramètres DNS
description: Configuration des paramètres DNS
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 87%

---

# Configuration des paramètres DNS {#configure-dns}

Une fois votre nom de domaine personnalisé vérifié et déployé, vous êtes prêt à mettre à jour les enregistrements DNS pour votre nom de domaine personnalisé avec votre fournisseur DNS. Cela permet à votre site de répondre aux visiteurs. Cette activité est donc généralement effectuée avant le lancement.

## Que sont les paramètres DNS ? {#dns-settings}

Un enregistrement `CNAME` ou A, une fois configuré, achemine tout le trafic Internet du domaine vers l’endroit où il pointe. Si cet emplacement n’est pas configuré pour servir le trafic, il y a une panne. S’il n’a pas été testé, il se peut que le contenu présente des erreurs. C’est pourquoi cette étape est toujours effectuée une fois le test terminé et que vous êtes prêt à passer en ligne.

Pour configurer ces paramètres, vous devez déterminer si un `CNAME` ou un enregistrement Apex doit être configuré pour pointer votre nom de domaine personnalisé vers le nom de domaine Cloud Manager. Les sections suivantes vous aideront à déterminer quel type d’enregistrement convient à votre configuration DNS.

>[!NOTE]
>
>Vous ou la personne appropriée de votre organisation devez être en mesure de vous connecter ou de contacter votre fournisseur DNS (la société auprès de laquelle vous avez acheté le domaine) et d’effectuer des mises à jour de vos paramètres DNS.

## Enregistrement CNAME {#cname-record}

Un enregistrement de nom canonique ou CNAME est un type d’enregistrement DNS qui mappe un nom d’alias à un nom de domaine réel ou canonique. Les enregistrements CNAME sont généralement utilisés pour mapper un sous-domaine tel que `www.example.com` au domaine hébergeant le contenu de ce sous-domaine.

Connectez-vous au serveur d’enregistrement de votre domaine et créez un enregistrement `CNAME` qui pointera vers votre nom de domaine personnalisé vers la cible, comme dans le tableau suivant.

| CNAME | Nom de domaine personnalisé pointant vers la cible |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## Enregistrement APEX {#apex-record}

Un domaine apex est un domaine personnalisé qui ne contient pas de sous-domaine, tel que `example.com`. Un domaine apex est configuré avec un enregistrement `A`, `ALIAS` ou `ANAME` via votre fournisseur DNS. Des domaines apex doivent pointer vers des adresses IP spécifiques.

Ajoutez tous les enregistrements `A` suivants aux paramètres DNS de votre domaine via votre fournisseur de domaine. 

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

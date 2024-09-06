---
title: Configuration des paramètres DNS
description: Découvrez comment configurer les paramètres DNS pour vos noms de domaine personnalisés permet à votre site de servir les visiteurs.
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 49%

---


# Configuration des paramètres DNS {#configure-dns}

Une fois le nom de domaine personnalisé [vérifié et déployé avec succès, ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) vous êtes prêt à mettre à jour les enregistrements DNS de votre nom de domaine personnalisé avec votre fournisseur DNS. Cela permet à votre site de répondre aux visiteurs. Cette activité est donc généralement effectuée avant le lancement.

## Que sont les paramètres DNS ? {#dns-settings}

Un enregistrement `CNAME` ou A, une fois configuré, achemine tout le trafic Internet du domaine vers l’emplacement où il pointe. Si cet emplacement n’est pas configuré pour desservir le trafic, il y a une panne. S’il n’a pas été testé, il se peut que le contenu présente des erreurs. C’est pourquoi cette étape est toujours effectuée une fois le test terminé et que vous êtes prêt à passer en ligne.

Pour configurer ces paramètres, vous devez déterminer si un enregistrement `CNAME` ou apex doit être configuré pour pointer votre nom de domaine personnalisé vers le nom de domaine Cloud Manager. Les sections suivantes de ce document vous aideront à déterminer le type d’enregistrement approprié à votre configuration DNS.

## Conditions requises {#requirements}

Vous devez répondre à ces exigences avant de configurer vos enregistrements DNS.

* Vous devez identifier l’hôte ou le serveur d’enregistrement de votre domaine si vous ne le connaissez pas déjà.
* Vous devez être en mesure de modifier les enregistrements DNS pour le domaine de votre entreprise ou contacter la personne appropriée qui peut le faire.
* Vous devez avoir déjà vérifié le nom de domaine personnalisé que vous avez configuré comme décrit dans le document [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

## Enregistrement CNAME {#cname-record}

Un enregistrement de nom canonique ou CNAME est un type d’enregistrement DNS qui mappe un nom d’alias à un nom de domaine réel ou canonique. Les enregistrements CNAME sont généralement utilisés pour mapper un sous-domaine tel que `www.example.com` au domaine hébergeant le contenu de ce sous-domaine.

Connectez-vous au serveur d’enregistrement de votre domaine et créez un enregistrement `CNAME` qui pointera vers votre nom de domaine personnalisé vers la cible, comme dans le tableau suivant.

| CNAME | Nom de domaine personnalisé pointant vers la cible |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## Enregistrement APEX {#apex-record}

Un domaine apex est un domaine personnalisé qui ne contient pas de sous-domaine, tel que `example.com`. Un domaine apex est configuré avec un enregistrement `A`, `ALIAS` ou `ANAME` via votre fournisseur DNS. Des domaines apex doivent pointer vers des adresses IP spécifiques.

Ajoutez les enregistrements `A` suivants aux paramètres DNS de votre domaine par l’intermédiaire de votre fournisseur de domaine.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

## Étapes suivantes {#next-steps}

Une fois que vous avez configuré vos enregistrements DNS pour votre nom de domaine personnalisé, vous devez vérifier ces paramètres dans Cloud Manager. Passez au document [Vérification de l’état des enregistrements DNS](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) pour finaliser votre nom de domaine personnalisé.

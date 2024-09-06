---
title: Ajout d’un enregistrement TXT
description: Découvrez comment ajouter un enregistrement TXT pour vérifier que vous êtes propriétaire d’un domaine personnalisé à utiliser avec Cloud Manager.
exl-id: d441de29-af41-4d3e-9155-531af9702841
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 28%

---


# Ajout d’un enregistrement TXT {#adding-txt}

Découvrez comment ajouter un enregistrement TXT pour vérifier que vous êtes propriétaire d’un domaine personnalisé à utiliser avec Cloud Manager.

## Qu’est-ce qu’un enregistrement TXT ? {#what-is}

Un enregistrement texte (également appelé enregistrement TXT) est un type d’enregistrement de ressource dans le système de noms de domaine (DNS). Il permet d’associer du texte arbitraire à un nom d’hôte, tel que des informations lisibles par l’utilisateur sur un nom d’hôte, telles que des informations sur le serveur ou le réseau.

Cloud Manager utilise un enregistrement TXT spécifique pour autoriser l’hébergement d’un domaine dans un service CDN. Vous devez créer un enregistrement TXT DNS dans la zone qui autorise Cloud Manager à déployer le service CDN avec le domaine personnalisé et l’associer au service principal. Cette association reste entièrement sous votre contrôle et permet à Cloud Manager de diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée. L’enregistrement TXT est spécifique au domaine et à l’environnement Cloud Manager.

## Conditions requises {#requirements}

Vous devez remplir ces conditions avant d’ajouter un enregistrement TXT.

* Vous devez identifier l’hôte ou le serveur d’enregistrement de votre domaine si vous ne le connaissez pas déjà.
* Vous devez être en mesure de modifier les enregistrements DNS pour le domaine de votre entreprise ou contacter la personne appropriée qui peut le faire.
* Vous devez d’abord ajouter un nom de domaine personnalisé comme décrit dans le document [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

## Ajout d’un enregistrement TXT à des fins de vérification {#verification}

Un enregistrement TXT est ajouté dans le cadre de la vérification d’un nom de domaine personnalisé à utiliser avec Cloud Manager.

1. Vous devez d’abord ajouter un nom de domaine personnalisé comme décrit dans le document [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Dans l’onglet **Verification** de la boîte de dialogue **Add Domain Name** , Cloud Manager affiche le nom et la valeur TXT à utiliser pour la vérification. Copiez cette valeur.

   ![Vérification des noms de domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

1. Connectez-vous à l’hôte de domaine et recherchez la section enregistrements DNS .

1. Ajoutez `_aemverification.[yourdomainname]` comme **Nom** de la valeur et ajoutez la valeur TXT exactement comme elle apparaît dans la boîte de dialogue **Ajouter un nom de domaine**.

   * Voir les [exemples dans la section suivante](#examples).

1. Enregistrez l’enregistrement TXT sur l’hôte de votre domaine.

## Exemples d’enregistrement TXT {#examples}

| Domaine | Nom | Valeur TXT |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple :<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple :<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

## Vérification de l’enregistrement TXT {#verify}

Une fois que vous avez terminé, vous pouvez vérifier le résultat en exécutant la commande suivante.

```shell
dig _aemverification.[yourdomainname] -t txt
```

Le résultat attendu doit afficher la valeur TXT fournie dans l’onglet **Verification** de la boîte de dialogue **Add Domain Name** de l’interface utilisateur de Cloud Manager.

Par exemple, si votre domaine est `example.com`, exécutez :

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Plusieurs [outils de recherche DNS](https://www.ultratools.com/tools/dnsLookup) sont disponibles. Le DoH Google peut être utilisé pour rechercher des entrées d’enregistrement TXT et déterminer si l’enregistrement TXT est manquant ou erroné.

>[!NOTE]
>
>La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.
>
>Cloud Manager vérifie la propriété et met à jour le statut visible dans le tableau des paramètres du domaine. Consultez [Vérification du statut du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

## Étapes suivantes {#next-steps}

Maintenant que vous avez créé votre entrée TXT, vous pouvez vérifier votre état de nom de domaine. Passez au document [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour continuer à configurer votre nom de domaine personnalisé.

>[!TIP]
>
>L’entrée TXT et le CNAME ou un enregistrement A peuvent être définis simultanément sur le serveur DNS qui gouverne, ce qui permet de gagner du temps.
>
>Pour ce faire, passez d’abord en revue l’ensemble du processus de configuration d’un nom de domaine personnalisé, comme décrit dans le document [Introduction aux noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md) , en prenant particulièrement note du document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) et en mettant à jour correctement vos paramètres DNS.
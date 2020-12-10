---
title: Ajouter un enregistrement TXT
description: Ajouter un nom de domaine personnalisé
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Ajouter un enregistrement TXT {#adding-txt}

Un enregistrement DNS TXT autorise l’hébergement d’un domaine dans un service CDN. Le client doit créer un enregistrement DNS TXT dans la zone qui autorise Cloud Manager à déployer le service CDN avec le domaine personnalisé et à l’associer au service principal. Cette association est entièrement sous le contrôle du client et autorise fortement Cloud Manager à diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée.

Vous devez suivre les étapes ci-dessous avant de créer un enregistrement TXT :

* Vous pouvez modifier les enregistrements DNS du domaine de votre entreprise ou contacter la personne appropriée qui peut le faire.
* Identifiez l’hôte ou le serveur d’inscriptions de votre domaine si vous ne le connaissez pas déjà.

Lorsque vous lancez la vérification de domaine, Cloud Manager vous donne le nom et la valeur TXT à utiliser pour la vérification. Ajoutez un enregistrement TXT au serveur DNS de votre domaine à l’aide du nom et de la valeur spécifiés.

1. Connectez-vous à votre hôte de domaine et consultez la section des enregistrements DNS.
1. Ajoutez `_aemverification.[yourdomainname]` comme nom et ajoutez la valeur TXT telle qu’elle apparaît.
Reportez-vous aux exemples du tableau ci-dessous.

| Domaine | Nom | Valeur TXT |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Affiché dans l’interface utilisateur de Cloud Manager et spécifique au domaine et à l’environnement de Cloud Manager |
| `test.example.com` | `_aemverification.test.example.com` | Affiché dans l’interface utilisateur de Cloud Manager et spécifique au domaine et à l’environnement de Cloud Manager |

Lorsque vous avez terminé, vous pouvez vérifier le résultat en exécutant : `dig _aemverification.[yourdomainname] -t txt`.
Le résultat attendu doit afficher la valeur TXT fournie dans l’interface utilisateur de Cloud Manager.

Par exemple, si votre domaine est `example.com`, exécutez : `dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>Il existe également divers [outils de recherche DNS](https://www.ultratools.com/tools/dnsLookup), Google DoH peut être utilisé pour rechercher les entrées d&#39;enregistrement TXT et déterminer si l&#39;enregistrement TXT est manquant ou erroné.


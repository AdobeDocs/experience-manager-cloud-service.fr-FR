---
title: Ajout d’un enregistrement TXT
description: Ajout d’un nom de domaine personnalisé
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: f7688559a791281d0e157dd1d48a5f63568914f5
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 100%

---

# Ajout d’un enregistrement TXT {#adding-txt}

Un enregistrement TXT de DNS permet l’hébergement d’un domaine dans un service CDN. Le client doit créer un enregistrement TXT de DNS dans la zone qui permet à Cloud Manager de déployer le service CDN avec le domaine personnalisé et de l’associer au service d’arrière-plan. Cette association est entièrement contrôlée par le client et permet à Cloud Manager de diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée.

Vous devez respecter les étapes ci-dessous avant de créer un enregistrement TXT :

* Vous devez pouvoir modifier les enregistrements DNS du domaine de votre entreprise ou contacter la personne qui peut le faire.
* Identifiez l’hôte ou le serveur d’enregistrement de votre domaine si vous ne le connaissez pas déjà.

Lorsque vous lancez la vérification de domaine, Cloud Manager vous donne le nom et la valeur TXT à utiliser pour la vérification. Ajoutez un enregistrement TXT au serveur DNS de votre domaine à l’aide du nom et de la valeur spécifiés.

1. Connectez-vous à votre hôte de domaine et consultez la section des enregistrements DNS.
1. Ajoutez `_aemverification.[yourdomainname]` comme nom et ajoutez la valeur TXT telle qu’elle apparaît.
Reportez-vous aux exemples du tableau ci-dessous.

| Domaine | Nom | Valeur TXT |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple :<br>*adobe-aem-verification=<br>example.com/[program]/[env]/..* |
| `www.example.com` | `_aemverification.www.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple :<br>*adobe-aem-verification=<br>www.example.com/[program]/[env]/..* |

Lorsque vous avez terminé, vous pouvez vérifier le résultat en exécutant : `dig _aemverification.[yourdomainname] -t txt`.
Le résultat attendu doit afficher la valeur TXT fournie dans l’interface utilisateur de Cloud Manager.

Par exemple, si votre domaine est `example.com`, exécutez : `dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>Il existe également divers [outils de recherche DNS](https://www.ultratools.com/tools/dnsLookup), Google DoH peut être utilisé pour rechercher des entrées d’enregistrement TXT et déterminer si l’enregistrement TXT est manquant ou erroné.

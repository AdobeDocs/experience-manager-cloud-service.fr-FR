---
title: Ajout d’un enregistrement TXT
description: Découvrez comment ajouter un enregistrement TXT pour ajouter un nom de domaine personnalisé à l’aide de Cloud Manager.
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: ht
source-wordcount: '329'
ht-degree: 100%

---

# Ajout d’un enregistrement TXT {#adding-txt}

Un enregistrement TXT de DNS permet l’hébergement d’un domaine dans un service CDN. Vous devez créer un enregistrement TXT de DNS dans la zone qui permet à Cloud Manager de déployer le service CDN avec le domaine personnalisé et de l’associer au service d’arrière-plan. Cette association reste entièrement sous votre contrôle et permet à Cloud Manager de diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée. L’enregistrement TXT est spécifique au domaine et à l’environnement Cloud Manager.

Vous devez remplir ces conditions avant d’ajouter un enregistrement TXT.

* Vous devez pouvoir modifier les enregistrements DNS du domaine de votre entreprise ou contacter la personne qui peut le faire.
* Vous devez identifier l’hôte ou le serveur d’enregistrement de votre domaine si vous ne le connaissez pas déjà.

Lorsque vous lancez la vérification de domaine, Cloud Manager vous donne le nom et la valeur TXT à utiliser pour la vérification. Ajoutez un enregistrement TXT au serveur DNS de votre domaine à l’aide du nom et de la valeur spécifiés.

1. Connectez-vous à votre hôte de domaine et consultez la section des enregistrements DNS.
1. Ajoutez `_aemverification.[yourdomainname]` en tant que valeur **Nom** et ajoutez la valeur TXT telle qu’elle apparaît.

Consultez les exemples dans ce tableau.

| Domaine | Nom | Valeur TXT |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple :<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple :<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

Lorsque vous avez terminé, vous pouvez vérifier le résultat en exécutant la commande suivante.

```shell
dig _aemverification.[yourdomainname] -t txt
```

Le résultat attendu doit afficher la valeur TXT fournie dans l’interface utilisateur de Cloud Manager.

Par exemple, si votre domaine est `example.com`, exécutez :

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Il existe plusieurs [Outils de recherche DNS](https://www.ultratools.com/tools/dnsLookup) disponibles. Le DoH Google peut être utilisé pour rechercher des entrées d’enregistrement TXT et déterminer si l’enregistrement TXT est manquant ou erroné.

---
title: Ajout d’un enregistrement TXT
description: Découvrez comment ajouter un enregistrement TXT pour ajouter un nom de domaine personnalisé dans Cloud Manager.
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 491e710223c5878bfa81c4b0a57d18ec0ec29479
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 30%

---

# Ajout d’un enregistrement TXT {#adding-txt}

Un enregistrement TXT DNS autorise l’hébergement d’un domaine dans un service CDN. Vous devez créer un enregistrement TXT DNS dans la zone qui autorise Cloud Manager à déployer le service CDN avec le domaine personnalisé et à l’associer au service principal. Cette association est entièrement sous votre contrôle et autorise Cloud Manager à diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée. L’enregistrement TXT est spécifique au domaine et à l’environnement Cloud Manager.

Vous devez répondre à ces exigences avant d’ajouter un enregistrement TXT.

* Vous devez avoir la possibilité de modifier les enregistrements DNS pour le domaine de votre entreprise, ou contacter la personne appropriée qui peut le faire.
* Si vous ne le savez pas déjà, vous devez identifier l’hôte de domaine ou le serveur d’inscriptions.

Lorsque vous lancez la vérification de domaine, Cloud Manager vous donne le nom et la valeur TXT à utiliser pour la vérification. Ajoutez un enregistrement TXT au serveur DNS de votre domaine à l’aide du nom et de la valeur spécifiés.

1. Connectez-vous à l’hôte de votre domaine et recherchez la section enregistrements DNS .
1. Ajouter `_aemverification.[yourdomainname]` comme la propriété **Nom** et ajoutez la valeur TXT telle qu’elle apparaît.

Reportez-vous aux exemples de ce tableau.

| Domaine | Nom | Valeur TXT |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple : <br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cela est spécifique au domaine et à l’environnement. Par exemple : <br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

Une fois que vous avez terminé, vous pouvez vérifier le résultat en exécutant la commande suivante :

```shell
dig _aemverification.[yourdomainname] -t txt
```

Le résultat attendu doit afficher la valeur TXT fournie dans l’interface utilisateur de Cloud Manager.

Par exemple, si votre domaine est `example.com`, puis exécutez :

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Il existe plusieurs [Outils de recherche DNS](https://www.ultratools.com/tools/dnsLookup) disponible. Google DoH peut être utilisé pour rechercher des entrées d’enregistrement TXT et déterminer si l’enregistrement TXT est manquant ou erroné.

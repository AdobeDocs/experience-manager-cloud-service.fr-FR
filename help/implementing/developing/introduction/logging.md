---
title: Journalisation
description: Découvrez comment configurer des paramètres globaux pour le service de journalisation centrale, des paramètres spécifiques pour les services individuels ou apprenez à demander la journalisation des données.
translation-type: tm+mt
source-git-commit: 436b4d05c88ba227144052fdd63ea78cbf1f03ba
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 17%

---


# Journalisation {#logging}

La plate-forme AEM as a Cloud Service permet aux clients d’inclure du code personnalisé destiné à créer des expériences incomparables pour leurs propres bases de clients. Dans cette optique, la journalisation est une fonction essentielle pour déboguer et comprendre l&#39;exécution du code sur le développement local, et les environnements de cloud, en particulier l&#39;AEM en tant qu&#39;environnements de développement Cloud Service.

Les niveaux de journalisation et de journalisation AEM sont gérés dans des fichiers de configuration stockés dans le cadre du projet AEM dans Git, et déployés dans le cadre du projet AEM via Cloud Manager. La connexion à AEM en tant que Cloud Service peut être divisée en deux jeux logiques :

* Journalisation des AEM, qui effectue la journalisation au niveau de l&#39;AEM application
* Journalisation du serveur Web/Dispatcher Apache HTTPD, qui effectue la journalisation du serveur Web et du Dispatcher sur le niveau Publier.

## Journalisation des AEM {#aem-loggin}

La journalisation au niveau de l’application AEM est gérée par trois journaux :

1. Journaux Java AEM, qui affichent les instructions de journalisation Java pour l’application AEM.
1. Journaux de requêtes HTTP, qui consignent les informations sur les requêtes HTTP et leurs réponses fournies par AEM
1. Journaux d’accès HTTP, qui consignent les informations résumées et les requêtes HTTP diffusées par AEM

Notez que les requêtes HTTP diffusées à partir du cache du Dispatcher du niveau Publication ou du réseau de diffusion de contenu en amont ne sont pas reflétées dans ces journaux.

### Journalisation Java AEM {#aem-java-logging}

AEM en tant que Cloud Service donne accès aux instructions de journal Java. Les développeurs d&#39;applications pour AEM doivent suivre les meilleures pratiques de consignation Java générales, consigner les instructions pertinentes concernant l&#39;exécution du code personnalisé, aux niveaux de journal suivants :

<table>
<tr>
<td>
<b>Environnement AEM</b></td>
<td>
<b>Niveau de journal</b></td>
<td>
<b>Description</b></td>
<td>
<b>Disponibilité des instructions de journal</b></td>
</tr>
<tr>
<td>
Développement</td>
<td>
DEBUG</td>
<td>
Décrit ce qui se passe dans l’application.<br>

Lorsque la journalisation DEBUG est active, les instructions fournissant une image claire des activités survenues ainsi que les paramètres clés qui affectent le traitement sont consignées.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
</ul></td>
</tr>
<tr>
<td>
Scène</td>
<td>
WARN</td>
<td>
Décrit les conditions susceptibles de devenir des erreurs.<br>

Lorsque la journalisation WARN est active, seules les instructions indiquant les conditions qui approchent du sous-optimisme sont consignées.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
<li>Scène</li>
</ul></td>
</tr>
<tr>
<td>
Production</td>
<td>
ERREUR</td>
<td>
Décrit les conditions qui indiquent un échec et doivent être résolues.<br>

Lorsque la journalisation ERROR est active, seules les instructions indiquant des échecs sont consignées. Les relevés de journal d&#39;ERREUR indiquent un problème grave qui devrait être résolu le plus tôt possible.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
<li>Scène</li>
<li>Production</li>
</ul></td>
</tr>
</table>
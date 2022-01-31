---
title: 'Problèmes connus '
description: Bonnes pratiques en matière de communications, problèmes connus et limites
source-git-commit: 06da7d2a5063e163aa1534bedbc79ae50ef27515
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 79%

---


# Questions fréquentes, bonnes pratiques, problèmes connus et limites {#best-practices-known-issues-and-limitations}

Avant de commencer à utiliser les API de communication, posez les questions fréquentes et passez en revue les problèmes et limitations connus suivants :

## Problèmes connus

- Vous ne pouvez utiliser un type de rendu spécifique (PDF, IMPRESSION) qu’une seule fois dans la liste des options d’impression. Par exemple, vous ne pouvez pas avoir deux options d’IMPRESSION spécifiant chacune un type de rendu PCL.

- Pour une configuration de lot, une seule instance de combinaison de valeurs OutputType(PDF, PRINT) et RenderType(PostScript, PCL, IPL, ZPL, etc.) est autorisée.

## Bonnes pratiques

- Adobe recommande l’hébergement du magasin de conteneurs blob de fichiers de données dans la région cloud utilisée par AEM Cloud Service.

## Questions fréquemment posées  {#faq}

**Puis-je utiliser un dossier de contrôle ou d’autres mécanismes de stockage pour stocker les entrées et les sorties ?**

Actuellement, vous pouvez utiliser le stockage Azure Microsoft pour enregistrer les données d’entrée et les documents générés. Le stockage Microsoft Azure offre diverses options pour [automatiser les opérations de déplacement des données](https://docs.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10).

**Un compte de stockage Azure Microsoft est-il inclus avec la licence Experience Manager Forms Cloud Service ?**

Le compte de stockage Microsoft Azure est indépendant de la licence Experience Manager Forms Cloud Service.

**Les API Communications stockent-elles des données sur les serveurs de Service Experience Manager Forms Cloud Service ?**

Les données d’entrée et de sortie sont enregistrées uniquement sur le stockage Microsoft Azure.

**Les API Communications sont-elles disponibles uniquement pour Experience Manager Forms Cloud Service ? Puis-je obtenir des fonctionnalités similaires dans un environnement On-Premise ?**

Vous pouvez utiliser le service AEM Forms Output pour combiner un modèle (XFA ou PDF) avec des données client afin de générer des documents aux formats PDF, PS, PCL et ZPL.

Par rapport à l’environnement On-Premise, le service cloud offre des avantages supplémentaires liés à la mise à l’échelle automatique et à la rentabilité.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**Puis-je exécuter plusieurs opérations par lots simultanément ?**
Oui, vous pouvez exécuter plusieurs opérations par lots de manière simultanée. Pour éviter tout conflit, utilisez toujours des dossiers source et de destination différents pour chaque opération.

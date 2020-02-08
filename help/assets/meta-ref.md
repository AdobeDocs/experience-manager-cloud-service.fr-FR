---
title: Référence des schémas de métadonnées
description: 'Découvrez les conventions standard permettant de décrire les métadonnées des ressources, y compris Dublin Core, IPTC et d’autres schémas de métadonnées. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Référence des schémas de métadonnées {#metadata-schemata-reference}

La référence ci-après contient des informations sur un schéma de métadonnées spécifique (dans l’ordre alphabétique) ainsi qu’une liste de propriétés et de leur définition.

## Dublin Core {#dublin-core}

La métadonnée Dublin Core fournit un ensemble de conventions normalisé pour décrire les ressources afin de faciliter leur recherche. Dans AEM Assets, Dublin Core décrit les ressources numériques, y compris les vidéos, le son, les images et les documents.

Le DCMES (Dublin Core Metadata Element Set) contient 15 éléments de métadonnées qui sont répertoriés dans le tableau ci-après. Chaque élément Dublin Core est facultatif et peut être utilisé plusieurs fois. Vous pouvez ajouter ou supprimer des informations de métadonnées Dublin Core comme vous le feriez pour les métadonnées spécifiques au type de média.

Outre le DCMES, il existe d’autres éléments de métadonnées créés par le Dublin Core Initiative. Pour plus d’informations, voir [Dublin Core Initiative](https://dublincore.org/).

<table>
 <tbody>
  <tr>
   <td><strong>Propriétés</strong></td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td>contributor</td> 
   <td>Personne ou entreprise chargée d'apporter des contributions au contenu.</td> 
  </tr>
  <tr>
   <td>coverage (couverture)</td> 
   <td>Emplacement géographique ou période que couvre la ressource.<br /> </td> 
  </tr>
  <tr>
   <td>creator (créateur)</td> 
   <td>Personne ou entreprise chargée de la création du contenu.</td> 
  </tr>
  <tr>
   <td>date</td> 
   <td>Date ou période associée à la ressource.<br /> </td> 
  </tr>
  <tr>
   <td>description</td> 
   <td>Informations supplémentaires sur la ressource.</td> 
  </tr>
  <tr>
   <td>format</td> 
   <td>Format de fichier, support physique ou dimensions de la ressource. AEM uses <code>dc:format</code> to denote the mime-type of the asset.<br /> </td> 
  </tr>
  <tr>
   <td>formulaire</td> 
   <td>Référence unique à la ressource.</td> 
  </tr>
  <tr>
   <td>language</td> 
   <td>Langue de la ressource ("en" pour l'anglais, par exemple).</td> 
  </tr>
  <tr>
   <td>publisher (éditeur)</td> 
   <td>Personne ou entreprise chargée de rendre la ressource disponible.</td> 
  </tr>
  <tr>
   <td>relation</td> 
   <td>Ressource connexe.</td> 
  </tr>
  <tr>
   <td>rights (droits)</td> 
   <td>Informations sur la personne qui dispose des droits sur cette ressource.</td> 
  </tr>
  <tr>
   <td>source</td> 
   <td>Ressource connexe à partir de laquelle la ressource est dérivée.</td> 
  </tr>
  <tr>
   <td>subject (objet)</td> 
   <td>Objet de la ressource.<br /> </td> 
  </tr>
  <tr>
   <td>titre</td> 
   <td>Nom de la ressource.</td> 
  </tr>
  <tr>
   <td>Type</td> 
   <td>Nature ou genre de la ressource.</td> 
  </tr>
 </tbody>
</table>

## IPTC {#iptc}

L’ITPC (International Press Telecommunications Council) est un consortium réunissant les principales agences de presse à travers le monde. L’un de ses principaux objectifs est de développer et maintenir des normes techniques. L’IPTC a défini un ensemble de normes de métadonnées photographiques qui est presque universellement accepté par les photographes. Ces normes de métadonnées faisaient partie de la norme plus générale appelée IPTC Information Interchange Model (IIM) créée dans les années 1990.

Bien que les informations d’en-tête IPTC ont été essentiellement remplacées par XMP, un schéma de base IPTC et un schéma d’extension sont disponibles pour XMP. Dans les programmes de traitement d’images, les propriétés XMP et IPTC sont synchronisées.

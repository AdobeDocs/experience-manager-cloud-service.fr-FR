---
title: 'Utilisation de polices personnalisées '
description: 'Utilisation de polices personnalisées '
source-git-commit: 7dd3785206b6d79caa500a155d3a6f3597303e65
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Utilisation de polices personnalisées

**La documentation sur les communications des Cloud Service est en version bêta.**

Vous pouvez utiliser Forms as a Cloud Service Communications pour combiner des modèles XDP, des documents PDF basés sur XDP ou Acrobat Forms (AcroForm) avec des données XML afin de générer des documents PDF. Vous pouvez utiliser des polices système (polices incluses dans Cloud Service) ou des polices personnalisées (polices approuvées par l’organisation) pour générer les documents du PDF.

Les polices système sont déjà disponibles dans le Cloud Service. Vous pouvez utiliser le projet de développement Cloud Service pour ajouter des polices personnalisées à votre environnement de Cloud Service.

## Comportement des documents PDF

Vous pouvez [incorporer une police](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) dans un document PDF ou indiquez simplement le nom d’une police. Lorsqu’une police est incorporée, le document du PDF apparaît (Looks) identique sur toutes les plateformes. Il utilisait la police incorporée pour garantir une apparence cohérente. Lorsqu’une police n’est pas incorporée, le client de rendu du PDF recherche la police sur l’ordinateur client. Si la police est disponible sur l’ordinateur client, le PDF utilise la police spécifiée, sinon le PDF est rendu avec une police de secours.

## Ajout de polices personnalisées à votre environnement Forms as a Cloud Service

Pour ajouter des polices personnalisées à votre environnement de Cloud Service :

1. Configurez et ouvrez le projet de développement local. Vous pouvez utiliser n’importe quel IDE de votre choix.
1. Dans la structure de dossiers de niveau supérieur du projet, créez un dossier pour enregistrer les polices personnalisées et ajouter des polices personnalisées au dossier. Par exemple, fonts/src/main/resources
   ![Dossier Polices](assets/fonts.png)

1. Ouvrez le fichier pom.xml de niveau supérieur du projet de développement.
1. Ajouter `<Font-Archive-Version>` l’entrée manifest dans le fichier .pom et définissez la valeur de version sur 1 :

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   </addDefaultEntries>
                   </addDefaultImplementationEntries>
               </manifest>
               <manifestEntries>
                   <Font-Archive-Version>1</Font-Archive-Version>
                   <Font-Archive-Contents>/</Font-Archive-Contents>
               </manifestEntries> 
           </archive>
       </configuration>
   </plugin>
   ```

1. Ajoutez votre dossier de polices à `<modules>` répertorié dans le fichier pom. Par exemple :

   ```xml
   <modules>
       <module>all</module>
       <module>core</module>
       <module>ui.frontend</module>
       <module>ui.apps</module>
       <module>ui.apps.structure</module>
       <module>ui.config</module>
       <module>ui.content</module>
       <module>it.tests</module>
       <module>dispatcher</module>
       <module>dispatcher.ams</module>
       <module>dispatcher.cloud</module>
       <module>ui.tests</module>
       <module>fonts</module>
   </modules>
   ```

1. Archivez le code mis à jour et [exécution du pipeline](/help/implementing/cloud-manager/deploy-code.md) pour déployer les polices dans votre environnement de Cloud Service.

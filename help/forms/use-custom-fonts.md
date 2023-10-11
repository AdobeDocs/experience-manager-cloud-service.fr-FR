---
title: Comment utiliser des polices personnalisées dans AEM Forms ?
description: Découvrez comment ajouter des polices personnalisées à un environnement Forms as a Cloud Service.
exl-id: 88214d36-fb97-4d46-a9fe-71dbc7826eb1
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 95%

---

# Utiliser des polices personnalisées

**La documentation de Cloud Service Communications est en version Beta.**

Vous pouvez utiliser Forms as a Cloud Service Communications pour combiner un modèle XDP, un document PDF basé sur XDP ou un formulaire Acrobat (AcroForm) avec des données XML afin de générer des documents PDF. Vous pouvez également utiliser Communications pour combiner, réorganiser et étendre vos documents aux formats PDF et XDP et obtenir des informations sur les documents PDF.

En plus des opérations mentionnées précédemment, vous pouvez utiliser les polices incluses dans Cloud Service ou des polices personnalisées (approuvées par l’organisation) pour effectuer le rendu des documents PDF générés. Vous pouvez utiliser le projet de développement Cloud Service pour ajouter des polices personnalisées à votre environnement Cloud Service.

## Comportement des documents PDF

Vous pouvez [incorporer une police](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutputOptions) à un document PDF. Lorsqu’une police est incorporée, le document PDF s’affiche (semble) identique sur toutes les plateformes. Il utilise des polices intégrées pour garantir une apparence cohérente. Lorsqu’une police n’est pas intégrée, son rendu dépend des paramètres de rendu des clients de visionneuse PDF tels qu’Acrobat ou Acrobat Reader. Si la police est disponible sur l’ordinateur client, le PDF utilise la police spécifiée, sinon le PDF est rendu avec une police de secours par défaut.

## Ajouter des polices personnalisées à votre environnement Forms as a Cloud Service {#custom-fonts-cloud-service}

Pour ajouter des polices personnalisées à votre environnement Cloud Service :

1. Configurez et ouvrez le [projet de développement local](setup-local-development-environment.md). Vous pouvez utiliser n’importe quel IDE de votre choix.
1. Dans la structure de dossiers de niveau supérieur du projet, créez un dossier (module) pour enregistrer les polices personnalisées et ajouter des polices personnalisées au dossier. Par exemple, fonts/src/main/resources.
   ![Dossier Polices](assets/fonts.png)

1. Ouvrez le fichier pom.xml du module des polices du projet de développement.
1. Ajoutez le module externe jar au fichier pom :

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
           </archive>
       </configuration>
   </plugin>
   ```

1. Ajoutez l’entrée de manifeste `<Font-Archive-Version>` au fichier .pom et définissez la valeur de la version sur 1 :

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
               <manifestEntries>
                   <Font-Archive-Version>1</Font-Archive-Version>
                   <Font-Archive-Contents>/</Font-Archive-Contents>
               </manifestEntries> 
           </archive>
       </configuration>
   </plugin>
   ```

1. Ajoutez votre dossier de polices aux `<modules>` répertoriés dans le fichier pom. Par exemple :

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

   Le dossier des polices contient toutes les polices personnalisées.

1. Enregistrez le code mis à jour et [exécutez le pipeline](/help/implementing/cloud-manager/deploy-code.md) pour déployer les polices dans votre environnement Cloud Service.

1. (Facultatif) Ouvrez l’invite de commande, accédez au dossier du projet local, puis exécutez la commande ci-dessous. La commande regroupe les polices dans un fichier .jar avec les informations pertinentes. Vous pouvez utiliser le fichier .jar pour ajouter des polices personnalisées à un environnement de développement local du Cloud Service Forms.

   ```shell
   mvn clean install
   ```

## Ajout de polices personnalisées à votre environnement de développement Cloud Service Forms {#custom-fonts-cloud-service-sdk}

1. Démarrez votre environnement de développement local.
1. Accédez au dossier `<aem install directory>/crx-quickstart/install`.
1. Placez le `<jar file contaning custom fonts and relevant deployment code>.jar` dans le dossier d’installation. Si vous ne disposez pas du fichier .jar, effectuez les étapes répertoriées dans la section [Ajout de polices personnalisées à votre environnement Forms as a Cloud Service](#custom-fonts-cloud-service) pour générer le fichier.
1. Exécution de l’[environnement du SDK basé sur le docker](setup-local-development-environment.md#docker-microservices)


   >[!NOTE]
   >
   >Chaque fois que vous déployez un fichier .jar de polices personnalisées mis à jour dans un environnement de développement local, redémarrez l’environnement du SDK basé sur le docker.

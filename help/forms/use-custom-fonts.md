---
title: 'Utilisation de polices personnalisées '
description: 'Utilisation de polices personnalisées '
source-git-commit: 0bfd75e517e03110d58575b21551d1d553fa36bf
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---


# Utilisation de polices personnalisées

**La documentation sur les communications des Cloud Service est en version bêta.**

Vous pouvez utiliser Forms as a Cloud Service Communications pour combiner un modèle XDP, un document de PDF basé sur XDP ou un formulaire Acrobat (AcroForm) avec des données XML afin de générer des documents de PDF. Vous pouvez utiliser des polices incluses dans les polices Cloud Service ou personnalisées (polices approuvées par l’organisation) pour effectuer le rendu des documents de PDF générés. Vous pouvez utiliser le projet de développement Cloud Service pour ajouter des polices personnalisées à votre environnement de Cloud Service.

## Comportement des documents PDF

Vous pouvez [incorporer une police](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) à un document de PDF. Lorsqu’une police est incorporée, le document du PDF apparaît (Looks) identique sur toutes les plateformes. Il utilisait la police incorporée pour garantir une apparence cohérente. Lorsqu’une police n’est pas incorporée, son rendu dépend des paramètres de rendu du client de visionneuse de PDF. Si la police est disponible sur l’ordinateur client, le PDF utilise la police spécifiée, sinon le PDF est rendu avec une police de secours.

## Ajout de polices personnalisées à votre environnement Forms as a Cloud Service {#custom-fonts-cloud-service}

Pour ajouter des polices personnalisées à votre environnement de Cloud Service :

1. Configurez et ouvrez le [projet de développement local](setup-local-development-environment.md). Vous pouvez utiliser n’importe quel IDE de votre choix.
1. Dans la structure de dossiers de niveau supérieur du projet, créez un dossier(module) pour enregistrer les polices personnalisées et ajouter des polices personnalisées au dossier. Par exemple, fonts/src/main/resources
   ![Dossier Polices](assets/fonts.png)

1. Ouvrez le fichier pom.xml du module des polices du projet de développement.
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

1. (Facultatif) Ouvrez l’invite de commande, accédez au dossier du projet local, puis exécutez la commande ci-dessous. La commande regroupe les polices dans un fichier .jar avec les informations pertinentes. Vous pouvez utiliser le fichier .jar pour ajouter des polices personnalisées à un environnement de développement local du Cloud Service Forms.

   ```shell
   mvn clean install
   ```

## Ajout de polices personnalisées à votre environnement de développement Forms Cloud Service local {#custom-fonts-cloud-service-sdk}

1. Démarrez votre environnement de développement local.
1. Accédez à [crx-repository]\install folder
1. Placez le fichier .jar contenant les polices personnalisées et le code de déploiement approprié dans le dossier d’installation. Si vous ne disposez pas du fichier .jar, effectuez les étapes répertoriées dans [Ajout de polices personnalisées à votre environnement Forms as a Cloud Service](#custom-fonts-cloud-service) pour générer le fichier.
1. Exécutez la variable [environnement du SDK docker](setup-local-development-environment.md#docker-microservices)


   >[!NOTE]
   >
   >Chaque fois que vous déployez un fichier .jar de polices personnalisées mis à jour dans l’environnement de déploiement local, redémarrez l’environnement du SDK Docker.
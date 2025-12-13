---
title: Comment préremplir des champs de formulaire adaptatif ?
description: En utilisant des données existantes pour préremplir les champs d’un formulaire adaptatif, les utilisateurs et utilisatrices peuvent préremplir les informations de base dans un formulaire en se connectant avec leurs profils sociaux.
topic-tags: develop
feature: Adaptive Forms, Foundation Components
exl-id: e2a87233-a0d5-48f0-b883-915fe56f105f
role: User, Developer
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '2044'
ht-degree: 93%

---

# Préremplissage des champs de formulaires adaptatifs{#prefill-adaptive-form-fields}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/prepopulate-adaptive-form-fields.html) |
| AEM as a Cloud Service | Cet article |

## Présentation {#introduction}

Vous pouvez préremplir les champs d’un formulaire adaptatif à l’aide de données existantes. Lorsqu’un utilisateur ouvre un formulaire, les valeurs de ces champs sont préremplies. Pour préremplir les données utilisateur dans un formulaire adaptatif, définissez-les sous la forme d’un fichier XML/JSON prérempli au format respectant la structure de données de préremplissage des formulaires adaptatifs.

## Applicabilité et cas d’utilisation

### Assurance

## AEM Forms peut-il préremplir les données de demande d’assurance ?

Oui. AEM Forms prend en charge le préremplissage des champs de formulaire à l’aide de sources de données principales, ce qui permet aux assureurs de réutiliser les données de client ou de police existantes et de réduire la saisie manuelle.

## Structure des données de préremplissage {#the-prefill-structure}

Un formulaire adaptatif peut contenir un mélange de champs liés et non liés. Les champs liés sont ceux qui sont déplacés à partir de l’onglet Outil de recherche de contenu et qui contiennent une valeur de propriété `bindRef` non vide dans la boîte de dialogue de modification du champ. Les champs non liés sont déplacés directement à partir du navigateur de composant de Sidekick et possède une valeur `bindRef` vide.

Vous pouvez préremplir les champs liés et non liés d’un formulaire adaptatif. Les données de préremplissage contiennent les sections afBoundData et afUnBoundData pour préremplir les champs liés et non liés d’un formulaire adaptatif. La section `afBoundData` contient les données de préremplissage pour les champs liés et les panneaux. Ces données doivent être conformes au schéma de modèle de formulaire associé :

- Pour les formulaires adaptatifs utilisant le [modèle de formulaire XFA](#xfa-based-af), utilisez le code XML de préremplissage conforme au schéma de données du modèle XFA.
- Pour les formulaires adaptatifs utilisant le [schéma XML](#xml-schema-af), utilisez le code XML de préremplissage compatible avec la structure du schéma XML.
- Pour les formulaires adaptatifs utilisant le [schéma JSON](#json-schema-based-adaptive-forms), utilisez le code JSON de préremplissage compatible avec le schéma JSON.
- Pour les formulaires adaptatifs utilisant le schéma FDM, utilisez le code JSON de préremplissage compatible avec le schéma FDM.
- Pour les formulaires adaptatifs [sans modèle de formulaire](#adaptive-form-with-no-form-model), il n’existe aucune donnée liée. Chaque champ est un champ non lié qui est prérempli à l’aide du code XML non lié.

### Exemple de structure XML de préremplissage {#sample-prefill-xml-structure}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<afData>
  <afBoundData>
     <employeeData>
        .
     </employeeData>
  </afBoundData>

  <afUnboundData>
    <data>
      <textbox>Hello World</textbox>
         .
         .
      <numericbox>12</numericbox>
         .
         .
    </data>
  </afUnboundData>
</afData>
```

### Exemple de structure JSON de préremplissage {#sample-prefill-json-structure}

```javascript
{
   "afBoundData": {
      "employeeData": { }
   },
   "afUnboundData": {
      "data": {
         "textbox": "Hello World",
         "numericbox": "12"
      }
   }
}
```

Pour les champs liés avec le même bindref ou les champs non liés portant le même nom, les données spécifiées dans la balise XML ou l’objet JSON sont insérées dans tous les champs. Par exemple, deux champs d’un formulaire sont mappés au nom `textbox` dans les données de préremplissage. Pendant l’exécution, si la première zone de texte contient « A », « A » est automatiquement inséré dans la deuxième zone de texte. On appelle cette opération liaison dynamique de champs de formulaires adaptatifs.

### Formulaire adaptatif utilisant le modèle de formulaire XFA {#xfa-based-af}

La structure du code XML de préremplissage et du code XML envoyé pour les formulaires adaptatifs basés sur XFA se présente comme suit :

- **Structure XML de préremplissage** : le code XML de préremplissage du formulaire adaptatif basé sur XFA doit être conforme au schéma de données du modèle de formulaire XFA. Pour préremplir des champs non liés, placez la structure XML de préremplissage dans la balise `/afData/afBoundData`.

- **Structure XML envoyée** : si aucun code XML de préremplissage n’est utilisé, le code XML envoyé contient des données pour les champs liés et non liés dans la balise wrapper `afData`. Si du code XML de préremplissage est utilisé, le code XML envoyé possède la même structure que celui-ci. Si le code XML de préremplissage commence par la balise racine `afData`, le code XML de sortie possède également le même format. Si le code XML de préremplissage ne dispose pas du wrapper `afData/afBoundData` et commence plutôt directement par la balise racine du schéma telle que `employeeData`, le code XML envoyé commence également par la balise `employeeData`.

Prefill-Submit-Data-ContentPackage.zip

[Obtenir le fichier](assets/prefill-submit-data-contentpackage.zip)
Exemple de données contenant un préremplissage et de données envoyées

### Formulaires adaptatifs basés sur un schéma XML  {#xml-schema-af}

La structure du code XML de préremplissage et du code XML envoyé pour les formulaires adaptatifs basés sur le schéma XML se présente comme suit :

- **Structure XML de préremplissage** : le code XML de préremplissage doit être conforme au schéma XML associé. Pour préremplir des champs non liés, placez la structure XML de préremplissage dans la balise /afData/afBoundData.
- **Structure XML envoyée** : si aucun code XML de préremplissage n’est utilisé, le code XML envoyé contient des données pour les champs liés et non liés dans la balise wrapper `afData`. Si du code XML de préremplissage est utilisé, le code XML envoyé possède la même structure que celui-ci. Si le code XML de préremplissage commence par la balise racine `afData`, le code XML de sortie possède également le même format. Si le code XML de préremplissage ne dispose pas du wrapper `afData/afBoundData` et commence plutôt directement par la balise racine du schéma telle que `employeeData`, le code XML envoyé commence également par la balise `employeeData`.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema targetNamespace="https://adobe.com/sample.xsd"
            xmlns="https://adobe.com/sample.xsd"
            xmlns:xs="https://www.w3.org/2001/XMLSchema">

    <xs:element name="sample" type="SampleType"/>

    <xs:complexType name="SampleType">
        <xs:sequence>
            <xs:element name="noOfProjectsAssigned" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:schema>
```

Pour les champs dont le modèle est le schéma XML, les données sont remplies dans la balise `afBoundData`, comme illustré dans l’exemple de code XML ci-dessous. Il peut servir à préremplir un formulaire adaptatif avec un ou plusieurs champs de texte non liés.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <textbox>Ignorance is bliss :) </textbox>
    </data>
  </afUnboundData>
  <afBoundData>
    <data>
      <noOfProjectsAssigned>twelve</noOfProjectsAssigned>
    </data>
  </afBoundData>
</afData>
```

>[!NOTE]
>
>Il est recommandé de ne pas utiliser de champs non liés dans les panneaux liés (panneaux avec une valeur `bindRef` non vide qui ont été créés en faisant glisser des composants depuis le Sidekick ou l’onglet Sources de données). Cela peut entraîner la perte de données de ces champs non liés. En outre, il est recommandé que les noms des champs soient uniques dans le formulaire, en particulier pour les champs non liés.

#### Exemple sans wrapper afData et afBoundData {#an-example-without-afdata-and-afbounddata-wrapper}

```xml
<?xml version="1.0" encoding="UTF-8"?><config>
 <assignmentDetails descriptionOfAssignment="Some Science Project" durationOfAssignment="34" financeRelatedProject="1" name="Lisa" numberOfMentees="1"/>
 <assignmentDetails descriptionOfAssignment="Kidding, right?" durationOfAssignment="4" financeRelatedProject="1" name="House" numberOfMentees="3"/>
</config>
```

### Formulaires adaptatifs basés sur un schéma JSON {#json-schema-based-adaptive-forms}

Pour les formulaires adaptatifs basés sur le schéma JSON, la structure du code JSON de préremplissage et du code JSON envoyé est décrite ci-dessous. Pour plus d’informations, reportez-vous à la section [Création de formulaires adaptatifs à l’aide d’un schéma JSON](adaptive-form-json-schema-form-model.md).

- **Structure du préremplissage JSON** : le préremplissage JSON doit être conforme au schéma JSON associé. Il peut éventuellement être encapsulé dans l’objet /afData/afBoundData si vous souhaitez préremplir aussi des champs non liés.
- **Structure JSON envoyée** : si aucun code JSON de préremplissage n’est utilisé, le code JSON envoyé contient des données pour les champs liés et non liés dans la balise wrapper afData. Si le code JSON de préremplissage est utilisé, le code JSON envoyé possède la même structure que celui-ci. Si le code JSON de préremplissage commence par l’objet racine afData, le code JSON de sortie possède également le même format. Si le code JSON de préremplissage ne dispose pas du wrapper afData/afBoundData et commence plutôt directement par l’objet racine du schéma tel que l’utilisateur, le code JSON envoyé commence également par l’objet utilisateur.

```json
{
  "id": "https://some.site.somewhere/entry-schema#",
  "$schema": "https://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "address": {
      "type": "object",
      "properties": {
        "name": {
          "type": "string"
        },
        "age": {
          "type": "integer"
        }
      }
    }
  }
}
```

Pour les champs qui utilisent le modèle de schéma JSON, les données sont préremplies dans l’objet afBoundData, comme illustré dans l’exemple JSON ci-dessous. Il peut servir à préremplir un formulaire adaptatif avec un ou plusieurs champs de texte non liés. Voici un exemple de données avec le wrapper `afData/afBoundData` :

```json
{
  "afData": {
    "afUnboundData": {
      "data": { "textbox": "Ignorance is bliss :) " }
    },
    "afBoundData": {
      "data": { {
   "user": {
    "address": {
     "city": "Noida",
     "country": "India"
}}}}}}}
```

Voici un exemple sans le wrapper `afData/afBoundData` :

```json
{
  "user": {
    "address": {
      "city": "Noida",
      "country": "India"
    }
  }
}
```

>[!NOTE]
>
> L’utilisation de champs non liés dans les panneaux liés (panneaux avec une valeur bindRef non vides qui ont été créés en faisant glisser des composants du Sidekick ou de l’onglet Sources de données) **n’est pas** recommandée car elle peut entraîner une perte de données des champs non liés. Il est recommandé d’utiliser des noms de champ uniques dans le formulaire, notamment pour les champs non liés.
>

### Formulaire adaptatif sans modèle de formulaire {#adaptive-form-with-no-form-model}

Pour les formulaires adaptatifs sans modèle de formulaire, les données de tous les champs se trouveront sous l’onglet `<data>` de la balise `<afUnboundData> tag`.

Prenez également en compte les points suivants :

Les balises XML des données utilisateur envoyées pour différents champs sont générées avec le nom des champs. Par conséquent, les noms des champs doivent être uniques.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <radiobutton>2</radiobutton>
      <repeatable_panel_no_form_model>
        <numericbox>12</numericbox>
      </repeatable_panel_no_form_model>
      <repeatable_panel_no_form_model>
        <numericbox>21</numericbox>
      </repeatable_panel_no_form_model>
      <checkbox>2</checkbox>
      <textbox>Nopes</textbox>
    </data>
  </afUnboundData>
  <afBoundData/>
</afData>
```

## Configuration du service de préremplissage {#configuring-prefill-service-using-configuration-manager}

Utilisez la propriété `alloweddataFileLocations` de la **Configuration du service de préremplissage par défaut** pour définir l’emplacement des fichiers de données ou une regex (expression régulière) pour l’emplacement des fichiers de données.

Le fichier JSON suivant affiche un exemple :

```JSON
  {
  "alloweddataFileLocations": "`file:///C:/Users/public/Document/Prefill/.*`"
  }
```

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.

>[!NOTE]
>
> - Par défaut, le préremplissage est autorisé via les fichiers crx pour tous les types de formulaires adaptatifs (XSD, XDP, JSON, FDM et non basé sur un modèle de formulaire). Le préremplissage est autorisé uniquement avec les fichiers XML et JSON.
> - Le protocole crx s’occupe de la sécurité des données préremplies et par conséquent, est activé par défaut. Le préremplissage par le biais d’autres protocoles à l’aide de l’expression regex peut entraîner une vulnérabilité. Dans la configuration, spécifiez une configuration d’URL sécurisée pour protéger vos données.

## Cas étrange des panneaux répétables {#the-curious-case-of-repeatable-panels}

En règle générale, les champs liés (schéma de formulaire) et non liés sont créés dans un même formulaire adaptatif. Les éléments suivants constituent cependant quelques exceptions lorsque les liaisons sont répétables :

- Les panneaux répétables non liés ne sont pas pris en charge pour les formulaires adaptatifs utilisant le modèle de formulaire XFA, XSD, le schéma JSON ou le schéma FDM.
- N’utilisez pas de champs non liés dans les panneaux répétables liés.

>[!NOTE]
>
> En règle générale, ne mélangez pas les champs liés et non liés s’ils sont croisés dans des données renseignées par l’utilisateur dans des champs non liés. Si possible, vous devez modifier le schéma ou le modèle de formulaire XFA et ajouter une entrée pour les champs non liés pour qu’ils deviennent également liés et que ses données soient disponibles comme tout autre champ dans les données envoyées.

## Protocoles pris en charge pour le préremplissage des données utilisateur {#supported-protocols-for-prefilling-user-data}

Les formulaires adaptatifs peuvent être préremplis avec des données d’utilisateur au format de données de préremplies via les protocoles suivants lorsqu’ils sont configurés avec une regex valide :

### Le protocole crx://  {#the-crx-protocol}

```javascript
http
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=crx:///tmp/fd/af/myassets/sample.xml
```

Le nœud spécifié doit posséder une propriété nommée `jcr:data` et contenir les données.

### Protocole file://  {#the-file-protocol-nbsp}

```javascript
https://`servername`/content/forms/af/someAF.html?wcmmode=disabled&dataRef=file:///C:/Users/form-user/Downloads/somesamplexml.xml
```

Le fichier référencé doit se trouver sur le même serveur.

### Protocole https://  {#the-http-protocol}

```javascript
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=https://servername/somesamplexmlfile.xml
```

### Protocole service://  {#the-service-protocol}

```javascript
https://`servername`/content/forms/af/abc.html?wcmmode=disabled&dataRef=service://[SERVICE_NAME]/[IDENTIFIER]
```

- SERVICE_NAME fait référence au nom du service de préremplissage OSGI. Consultez [Créer et exécuter un service de préremplissage](prepopulate-adaptive-form-fields.md#create-and-run-a-prefill-service).
- IDENTIFIER fait référence à toutes les métadonnées requises par le service de préremplissage OSGI pour récupérer les données de préremplissage. Un identifiant à la personne connectée est un exemple de métadonnées qui pourraient être utilisées.

>[!NOTE]
>
> La transmission des paramètres d’authentification n’est pas prise en charge.

### Définition de l’attribut data dans slingRequest {#setting-data-attribute-in-slingrequest}

Vous pouvez également définir l’attribut `data` dans `slingRequest`, où l’attribut `data` correspond à une chaîne contenant des balises XML ou JSON, comme illustré dans l’exemple de code ci-après (exemple pour XML) :

```javascript
<%
           String dataXML="<afData>" +
                            "<afUnboundData>" +
                                "<data>" +
                                    "<first_name>"+ "Tyler" + "</first_name>" +
                                    "<last_name>"+ "Durden " + "</last_name>" +
                                    "<gender>"+ "Male" + "</gender>" +
                                    "<location>"+ "Texas" + "</location>" +
                                    "</data>" +
                            "</afUnboundData>" +
                        "</afData>";
        slingRequest.setAttribute("data", dataXML);
%>
```

Vous pouvez écrire une chaîne XML ou JSON simple contenant toutes les données et la définir dans slingRequest. Cette opération peut facilement être effectuée dans le JSP de rendu pour tout composant que vous souhaitez inclure dans la page où vous pouvez définir l’attribut data slingRequest.

Imaginons que vous souhaitez une conception spécifique pour votre page avec un type spécifique d’en-tête. Pour obtenir ce résultat, vous pouvez écrire votre propre fichier `header.jsp` à inclure dans votre composant de page et définir l’attribut.`data`

Prenons un autre bon exemple dans lequel vous souhaitez préremplir les données à la connexion par le biais de comptes de réseau social tels que Facebook, Twitter ou LinkedIn. Dans ce cas, vous pouvez inclure un JSP simple dans `header.jsp` qui récupère les données du compte d’utilisateur et définit le paramètre data.

prefill-page component.zip

[Obtenir le fichier](assets/prefill-page-component.zip)
Exemple de prefill.jsp dans le composant de page

## [!DNL AEM Forms] service de préremplissage personnalisé  {#aem-forms-custom-prefill-service}

Vous pouvez utiliser le service de préremplissage personnalisé pour les scénarios, où vous lisez en permanence des données à partir d’une source prédéfinie. Le service de préremplissage lit des données à partir des sources de données définies et préremplit les champs du formulaire adaptatif avec le contenu du fichier de données de préremplissage. Il vous permet également d’associer de manière permanente des données de préremplissage à un formulaire adaptatif.

### Création et exécution d’un service de préremplissage {#create-and-run-a-prefill-service}

Le service de préremplissage est un service OSGi et fait partie du bundle OSGi. Vous créez le bundle OSGi, vous le chargez et l’installez sur les bundles [!DNL AEM Forms]. Avant de débuter la création du bundle :

- [Téléchargement du  [!DNL AEM Forms] SDK client](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr)
- Téléchargement du package standard

- Placez le fichier de données (données de préremplissage) dans le référentiel crx. Vous pouvez placer le fichier à tout emplacement dans le dossier \contents du référentiel crx.

[Obtenir le fichier](assets/prefill-sumbit-xmlsandcontentpackage.zip)

#### Création d’un service de préremplissage {#create-a-prefill-service}

Le package standard (exemple de package de services de préremplissage) contient un exemple d’implémentation du service de préremplissage d’[!DNL AEM Forms]. Ouvrez le package standard dans un éditeur de code. Par exemple, ouvrez le projet standard dans Eclipse pour le modifier. Après avoir ouvert le package standard dans un éditeur de code, procédez comme suit pour créer le service.

1. Ouvrez le fichier src\main\java\com\adobe\test\Prefill.java pour le modifier.
1. Dans le code, définissez la valeur de :

   - `nodePath:` la variable de chemin de nœud pointant vers l’emplacement du référentiel crx contient le chemin du fichier (de préremplissage) de données. Par exemple, /content/prefilldata.xml
   - `label:` le paramètre label spécifie le nom d’affichage du service. Par exemple, service de préremplissage par défaut

1. Enregistrez et fermez le fichier `Prefill.java`.
1. Ajoutez le package `AEM Forms Client SDK` sur le chemin de génération du projet standard.
1. Compilez le projet et créez le fichier .jar pour le bundle.

#### Démarrage et utilisation du service de préremplissage {#start-and-use-the-prefill-service}

Pour démarrer le service de préremplissage, chargez le fichier JAR dans la console web d’[!DNL AEM Forms] et activez le service. Désormais, le démarrage du service s’affiche dans l’éditeur de formulaires adaptatifs. Pour associer un service de préremplissage à un formulaire adaptatif :

1. Ouvrez le formulaire adaptatif dans l’éditeur de formulaires et ouvrez le panneau des propriétés du conteneur de formulaires.
1. Dans la console des propriétés, accédez au conteneur d’[!DNL AEM Forms] > De base > Service de préremplissage.
1. Sélectionnez le service de préremplissage par défaut et cliquez sur **[!UICONTROL Enregistrer]**. Le service est associé au formulaire.

<!-- ## Prepopulate data at client {#prefill-at-client}

When you prefill an Adaptive Form, the [!DNL AEM Forms] server merges data with an Adaptive Form and delivers the filled form to you. By default, the data merge action takes place at the server.

You can configure the [!DNL AEM Forms] server to perform the data merge action at the client instead of the server. It significantly reduces the time required to prefill and render Adaptive Forms. By default, the feature is disabled. You can enable it from the Configuration Manager or command line.

* To enable or disable from configuration manager:
  1. Open AEM Configuration Manager.
  1. Locate and open the Adaptive Form and Interactive Communication Web Channel Configuration
  1. Enable the Configuration.af.clientside.datamerge.enabled.name option
* To enable or disable from the command line:
  * To enable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=true \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

  * To disable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=false \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

   To take full advantage of the prepopulate data at client option, update your prefill service to return [FileAttachmentMap](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) and [CustomContext](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) -->
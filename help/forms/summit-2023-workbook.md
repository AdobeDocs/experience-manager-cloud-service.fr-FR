---
title: Créer des formulaire attrayants à l’aide des composants principaux et découplés
seo-title: Build Engaging Forms Using Core Components and Headless
description: Créer des formulaire attrayants à l’aide des composants principaux et découplés
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
exl-id: e1eb0812-c92e-4a18-aabb-5a70b9e6fc7d
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '3358'
ht-degree: 99%

---

# Créer des formulaire attrayants à l’aide des composants principaux et découplés

## Présentation de l’atelier

Dans cet atelier pratique, vous allez apprendre :

Comment utiliser AEM Forms pour créer facilement des formulaires adaptatifs à l’aide des derniers composants principaux conformes à AEM Sites, activer les expériences de capture de données omnicanal en fournissant les formulaires adaptatifs sous forme de formulaires découplés sur le web, les appareils mobiles et les chats. Vous allez également découvrir les bonnes pratiques en matière de style, de personnalisation et de développement front-end.

## Principaux points à retenir

* **Agilité professionnelle** : en tant qu’utilisateur professionnel ou utilisatrice professionnelle, je peux facilement créer une expérience de formulaire pour plusieurs canaux.

* **Puissance du développeur front-end** : en tant que développeur ou développeuse front-end, je peux contrôler l’expérience de l’utilisateur final ou de l’utilisatrice finale à l’aide de formulaires découplés.

* **Vitesse du développeur** : en tant que développeur ou développeuse, je peux personnaliser facilement et systématiquement les composants Sites et Forms.

## Prérequis


+++Sandbox AEM Forms as Cloud Service



<table>
        <thead>
            <tr><th>ID de l’atelier</th><th>URL de l’instance de création</th><th>URL de l’instance de publication</th></tr>           
        </thead>
        <tbody>
            <tr><td>L716001</td><td>https://author-p105303-e986623.adobeaemcloud.com</td><td>https://publish-p105303-e986623.adobeaemcloud.com</td></tr><tr><td>L716002</td><td>https://author-p106405-e993047.adobeaemcloud.com</td><td>https://publish-p106405-e993047.adobeaemcloud.com</td></tr><tr><td>L716003</td><td>https://author-p106406-e993049.adobeaemcloud.com</td><td>https://publish-p106406-e993049.adobeaemcloud.com</td></tr><tr><td>L716004</td><td>https://author-p106398-e993114.adobeaemcloud.com</td><td>https://publish-p106398-e993114.adobeaemcloud.com</td></tr><tr><td>L716005</td><td>https://author-p106407-e993048.adobeaemcloud.com</td><td>https://publish-p106407-e993048.adobeaemcloud.com</td></tr><tr><td>L716006</td><td>https://author-p106408-e993155.adobeaemcloud.com</td><td>https://publish-p106408-e993155.adobeaemcloud.com</td></tr><tr><td>L716007</td><td>https://author-p106343-e993067.adobeaemcloud.com</td><td>https://publish-p106343-e993067.adobeaemcloud.com</td></tr><tr><td>L716008</td><td>https://author-p106399-e993108.adobeaemcloud.com</td><td>https://publish-p106399-e993108.adobeaemcloud.com</td></tr><tr><td>L716009</td><td>https://author-p106344-e993064.adobeaemcloud.com</td><td>https://publish-p106344-e993064.adobeaemcloud.com</td></tr><tr><td>L716010</td><td>https://author-p106409-e993051.adobeaemcloud.com</td><td>https://publish-p106409-e993051.adobeaemcloud.com</td></tr><tr><td>L716011</td><td>https://author-p106345-e993060.adobeaemcloud.com</td><td>https://publish-p106345-e993060.adobeaemcloud.com</td></tr><tr><td>L716012</td><td>https://author-p106346-e993061.adobeaemcloud.com</td><td>https://publish-p106346-e993061.adobeaemcloud.com</td></tr><tr><td>L716013</td><td>https://author-p106410-e993153.adobeaemcloud.com</td><td>https://publish-p106410-e993153.adobeaemcloud.com</td></tr><tr><td>L716014</td><td>https://author-p106502-e993073.adobeaemcloud.com</td><td>https://publish-p106502-e993073.adobeaemcloud.com</td></tr><tr><td>L716015</td><td>https://author-p106401-e993112.adobeaemcloud.com</td><td>https://publish-p106401-e993112.adobeaemcloud.com</td></tr><tr><td>L716016</td><td>https://author-p106452-e993115.adobeaemcloud.com</td><td>https://publish-p106452-e993115.adobeaemcloud.com</td></tr><tr><td>L716017</td><td>https://author-p106453-e993113.adobeaemcloud.com</td><td>https://publish-p106453-e993113.adobeaemcloud.com</td></tr><tr><td>L716018</td><td>https://author-p106411-e993050.adobeaemcloud.com</td><td>https://publish-p106411-e993050.adobeaemcloud.com</td></tr><tr><td>L716019</td><td>https://author-p106454-e993116.adobeaemcloud.com</td><td>https://publish-p106454-e993116.adobeaemcloud.com</td></tr><tr><td>L716020</td><td>https://author-p106347-e993063.adobeaemcloud.com</td><td>https://publish-p106347-e993063.adobeaemcloud.com</td></tr><tr><td>L716021</td><td>https://author-p106455-e993109.adobeaemcloud.com</td><td>https://publish-p106455-e993109.adobeaemcloud.com</td></tr><tr><td>L716022</td><td>https://author-p106456-e993110.adobeaemcloud.com</td><td>https://publish-p106456-e993110.adobeaemcloud.com</td></tr><tr><td>L716023</td><td>https://author-p106466-e993291.adobeaemcloud.com</td><td>https://publish-p106466-e993291.adobeaemcloud.com</td></tr><tr><td>L716024</td><td>https://author-p106413-e993156.adobeaemcloud.com</td><td>https://publish-p106413-e993156.adobeaemcloud.com</td></tr><tr><td>L716025</td><td>https://author-p106348-e993066.adobeaemcloud.com</td><td>https://publish-p106348-e993066.adobeaemcloud.com</td></tr><tr><td>L716026</td><td>https://author-p106414-e993154.adobeaemcloud.com</td><td>https://publish-p106414-e993154.adobeaemcloud.com</td></tr><tr><td>L716027</td><td>https://author-p106349-e993065.adobeaemcloud.com</td><td>https://publish-p106349-e993065.adobeaemcloud.com</td></tr><tr><td>L716028</td><td>https://author-p106415-e993152.adobeaemcloud.com</td><td>https://publish-p106415-e993152.adobeaemcloud.com</td></tr><tr><td>L716029</td><td>https://author-p106350-e993068.adobeaemcloud.com</td><td>https://publish-p106350-e993068.adobeaemcloud.com</td></tr><tr><td>L716030</td><td>https://author-p106351-e993062.adobeaemcloud.com</td><td>https://publish-p106351-e993062.adobeaemcloud.com</td></tr><tr><td>L716031</td><td>https://author-p106417-e993158.adobeaemcloud.com</td><td>https://publish-p106417-e993158.adobeaemcloud.com</td></tr><tr><td>L716032</td><td>https://author-p106418-e993159.adobeaemcloud.com</td><td>https://publish-p106418-e993159.adobeaemcloud.com</td></tr><tr><td>L716033</td><td>https://author-p106503-e993080.adobeaemcloud.com</td><td>https://publish-p106503-e993080.adobeaemcloud.com</td></tr><tr><td>L716034</td><td>https://author-p106457-e993125.adobeaemcloud.com</td><td>https://publish-p106457-e993125.adobeaemcloud.com</td></tr><tr><td>L716035</td><td>https://author-p106504-e993081.adobeaemcloud.com</td><td>https://publish-p106504-e993081.adobeaemcloud.com</td></tr><tr><td>L716036</td><td>https://author-p106458-e993120.adobeaemcloud.com</td><td>https://publish-p106458-e993120.adobeaemcloud.com</td></tr><tr><td>L716037</td><td>https://author-p106419-e993160.adobeaemcloud.com</td><td>https://publish-p106419-e993160.adobeaemcloud.com</td></tr><tr><td>L716038</td><td>https://author-p106420-e993162.adobeaemcloud.com</td><td>https://publish-p106420-e993162.adobeaemcloud.com</td></tr><tr><td>L716039</td><td>https://author-p106517-e993235.adobeaemcloud.com</td><td>https://publish-p106517-e993235.adobeaemcloud.com</td></tr><tr><td>L716040</td><td>https://author-p106506-e993079.adobeaemcloud.com</td><td>https://publish-p106506-e993079.adobeaemcloud.com</td></tr><tr><td>L716041</td><td>https://author-p106507-e993074.adobeaemcloud.com</td><td>https://publish-p106507-e993074.adobeaemcloud.com</td></tr><tr><td>L716042</td><td>https://author-p106508-e993075.adobeaemcloud.com</td><td>https://publish-p106508-e993075.adobeaemcloud.com</td></tr><tr><td>L716043</td><td>https://author-p106421-e993163.adobeaemcloud.com</td><td>https://publish-p106421-e993163.adobeaemcloud.com</td></tr><tr><td>L716044</td><td>https://author-p106459-e993121.adobeaemcloud.com</td><td>https://publish-p106459-e993121.adobeaemcloud.com</td></tr><tr><td>L716045</td><td>https://author-p106467-e993292.adobeaemcloud.com</td><td>https://publish-p106467-e993292.adobeaemcloud.com</td></tr><tr><td>L716046</td><td>https://author-p106518-e993234.adobeaemcloud.com</td><td>https://publish-p106518-e993234.adobeaemcloud.com</td></tr><tr><td>L716047</td><td>https://author-p106511-e993076.adobeaemcloud.com</td><td>https://publish-p106511-e993076.adobeaemcloud.com</td></tr><tr><td>L716048</td><td>https://author-p106512-e993077.adobeaemcloud.com</td><td>https://publish-p106512-e993077.adobeaemcloud.com</td></tr><tr><td>L716049</td><td>https://author-p106460-e993124.adobeaemcloud.com</td><td>https://publish-p106460-e993124.adobeaemcloud.com</td></tr><tr><td>L716050</td><td>https://author-p106519-e993237.adobeaemcloud.com</td><td>https://publish-p106519-e993237.adobeaemcloud.com</td></tr><tr><td>L716051</td><td>https://author-p106513-e993084.adobeaemcloud.com</td><td>https://publish-p106513-e993084.adobeaemcloud.com</td></tr><tr><td>L716052</td><td>https://author-p106461-e993122.adobeaemcloud.com</td><td>https://publish-p106461-e993122.adobeaemcloud.com</td></tr><tr><td>L716053</td><td>https://author-p106514-e993082.adobeaemcloud.com</td><td>https://publish-p106514-e993082.adobeaemcloud.com</td></tr><tr><td>L716054</td><td>https://author-p106462-e993123.adobeaemcloud.com</td><td>https://publish-p106462-e993123.adobeaemcloud.com</td></tr><tr><td>L716055</td><td>https://author-p106463-e993127.adobeaemcloud.com</td><td>https://publish-p106463-e993127.adobeaemcloud.com</td></tr><tr><td>L716056</td><td>https://author-p106515-e993083.adobeaemcloud.com</td><td>https://publish-p106515-e993083.adobeaemcloud.com</td></tr><tr><td>L716057</td><td>https://author-p106464-e993126.adobeaemcloud.com</td><td>https://publish-p106464-e993126.adobeaemcloud.com</td></tr><tr><td>L716058</td><td>https://author-p106520-e993236.adobeaemcloud.com</td><td>https://publish-p106520-e993236.adobeaemcloud.com</td></tr><tr><td>L716059</td><td>https://author-p106423-e993161.adobeaemcloud.com</td><td>https://publish-p106423-e993161.adobeaemcloud.com</td></tr><tr><td>L716060</td><td>https://author-p106516-e993078.adobeaemcloud.com</td><td>https://publish-p106516-e993078.adobeaemcloud.com</td></tr><tr><td>L716061</td><td>https://author-p106521-e993240.adobeaemcloud.com</td><td>https://publish-p106521-e993240.adobeaemcloud.com</td></tr><tr><td>L716062</td><td>https://author-p106424-e993308.adobeaemcloud.com</td><td>https://publish-p106424-e993308.adobeaemcloud.com</td></tr><tr><td>L716063</td><td>https://author-p106468-e993295.adobeaemcloud.com</td><td>https://publish-p106468-e993295.adobeaemcloud.com</td></tr><tr><td>L716064</td><td>https://author-p106425-e993309.adobeaemcloud.com</td><td>https://publish-p106425-e993309.adobeaemcloud.com</td></tr><tr><td>L716065</td><td>https://author-p106426-e993314.adobeaemcloud.com</td><td>https://publish-p106426-e993314.adobeaemcloud.com</td></tr><tr><td>L716066</td><td>https://author-p106469-e993293.adobeaemcloud.com</td><td>https://publish-p106469-e993293.adobeaemcloud.com</td></tr><tr><td>L716067</td><td>https://author-p106522-e993238.adobeaemcloud.com</td><td>https://publish-p106522-e993238.adobeaemcloud.com</td></tr><tr><td>L716068</td><td>https://author-p106470-e993299.adobeaemcloud.com</td><td>https://publish-p106470-e993299.adobeaemcloud.com</td></tr><tr><td>L716069</td><td>https://author-p106427-e993311.adobeaemcloud.com</td><td>https://publish-p106427-e993311.adobeaemcloud.com</td></tr><tr><td>L716070</td><td>https://author-p106428-e993310.adobeaemcloud.com</td><td>https://publish-p106428-e993310.adobeaemcloud.com</td></tr><tr><td>L716071</td><td>https://author-p106471-e993298.adobeaemcloud.com</td><td>https://publish-p106471-e993298.adobeaemcloud.com</td></tr><tr><td>L716072</td><td>https://author-p106429-e993315.adobeaemcloud.com</td><td>https://publish-p106429-e993315.adobeaemcloud.com</td></tr><tr><td>L716073</td><td>https://author-p106523-e993239.adobeaemcloud.com</td><td>https://publish-p106523-e993239.adobeaemcloud.com</td></tr><tr><td>L716074</td><td>https://author-p106472-e993300.adobeaemcloud.com</td><td>https://publish-p106472-e993300.adobeaemcloud.com</td></tr><tr><td>L716075</td><td>https://author-p106430-e993312.adobeaemcloud.com</td><td>https://publish-p106430-e993312.adobeaemcloud.com</td></tr><tr><td>L716076</td><td>https://author-p106524-e993241.adobeaemcloud.com</td><td>https://publish-p106524-e993241.adobeaemcloud.com</td></tr><tr><td>L716077</td><td>https://author-p106431-e993313.adobeaemcloud.com</td><td>https://publish-p106431-e993313.adobeaemcloud.com</td></tr><tr><td>L716078</td><td>https://author-p106473-e993294.adobeaemcloud.com</td><td>https://publish-p106473-e993294.adobeaemcloud.com</td></tr><tr><td>L716079</td><td>https://author-p106474-e993297.adobeaemcloud.com</td><td>https://publish-p106474-e993297.adobeaemcloud.com</td></tr><tr><td>L716080</td><td>https://author-p106475-e993296.adobeaemcloud.com</td><td>https://publish-p106475-e993296.adobeaemcloud.com</td></tr><tr><td>L716081</td><td>https://author-p106476-e993353.adobeaemcloud.com</td><td>https://publish-p106476-e993353.adobeaemcloud.com</td></tr><tr><td>L716082</td><td>https://author-p106525-e993247.adobeaemcloud.com</td><td>https://publish-p106525-e993247.adobeaemcloud.com</td></tr><tr><td>L716083</td><td>https://author-p106526-e993244.adobeaemcloud.com</td><td>https://publish-p106526-e993244.adobeaemcloud.com</td></tr><tr><td>L716084</td><td>https://author-p106527-e993243.adobeaemcloud.com</td><td>https://publish-p106527-e993243.adobeaemcloud.com</td></tr><tr><td>L716085</td><td>https://author-p106477-e993356.adobeaemcloud.com</td><td>https://publish-p106477-e993356.adobeaemcloud.com</td></tr><tr><td>L716086</td><td>https://author-p106478-e993355.adobeaemcloud.com</td><td>https://publish-p106478-e993355.adobeaemcloud.com</td></tr><tr><td>L716087</td><td>https://author-p106528-e993245.adobeaemcloud.com</td><td>https://publish-p106528-e993245.adobeaemcloud.com</td></tr><tr><td>L716088</td><td>https://author-p106432-e993316.adobeaemcloud.com</td><td>https://publish-p106432-e993316.adobeaemcloud.com</td></tr><tr><td>L716089</td><td>https://author-p106529-e993242.adobeaemcloud.com</td><td>https://publish-p106529-e993242.adobeaemcloud.com</td></tr><tr><td>L716090</td><td>https://author-p106436-e993320.adobeaemcloud.com</td><td>https://publish-p106436-e993320.adobeaemcloud.com</td></tr><tr><td>L716091</td><td>https://author-p106480-e993301.adobeaemcloud.com</td><td>https://publish-p106480-e993301.adobeaemcloud.com</td></tr><tr><td>L716092</td><td>https://author-p106530-e993246.adobeaemcloud.com</td><td>https://publish-p106530-e993246.adobeaemcloud.com</td></tr><tr><td>L716093</td><td>https://author-p106481-e993352.adobeaemcloud.com</td><td>https://publish-p106481-e993352.adobeaemcloud.com</td></tr><tr><td>L716094</td><td>https://author-p106482-e993354.adobeaemcloud.com</td><td>https://publish-p106482-e993354.adobeaemcloud.com</td></tr><tr><td>L716095</td><td>https://author-p106531-e993248.adobeaemcloud.com</td><td>https://publish-p106531-e993248.adobeaemcloud.com</td></tr><tr><td>L716096</td><td>https://author-p106483-e993357.adobeaemcloud.com</td><td>https://publish-p106483-e993357.adobeaemcloud.com</td></tr><tr><td>L716097</td><td>https://author-p106433-e993318.adobeaemcloud.com</td><td>https://publish-p106433-e993318.adobeaemcloud.com</td></tr><tr><td>L716098</td><td>https://author-p106532-e993249.adobeaemcloud.com</td><td>https://publish-p106532-e993249.adobeaemcloud.com</td></tr><tr><td>L716099</td><td>https://author-p106434-e993317.adobeaemcloud.com</td><td>https://publish-p106434-e993317.adobeaemcloud.com</td></tr><tr><td>L716100</td><td>https://author-p106435-e993319.adobeaemcloud.com</td><td>https://publish-p106435-e993319.adobeaemcloud.com</td></tr>
        </tbody>
</table>

+++

## Leçon 1

### Objectif

Familiarisez-vous avec l’environnement d’AEM Forms as a Cloud Service.

### Contexte de la leçon

Dans cette leçon, vous vous familiarisez avec l’environnement d’AEM Forms as a Cloud Service en naviguant dans l’interface utilisateur.

### Exercice

1. Ouvrez votre navigateur et saisissez l’URL de l’environnement de création de Cloud Service.

1. Connectez-vous à l’environnement de création de Cloud Service. Les informations de connexion de votre environnement de création sont partagées avec vous au cours du laboratoire.

1. Une fois la connexion établie, accédez à l’interface utilisateur d’AEM Forms. Cliquez sur **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. Cliquez sur **Formulaires &amp; Documents**. Ignorez les fenêtres contextuelles liées aux préférences ou aux informations.

   ![](/help/forms/assets/screenshot2028113929.png)

   Tous les formulaires disponibles sont affichés.

   ![](/help/forms/assets/screenshot2028114029.png)

## Leçon 2

### Objectif

Créez un formulaire adaptatif à l’aide des derniers composants principaux, puis configurez et soumettez le formulaire.

### Contexte de la leçon

Dans cette leçon, en tant qu’utilisatrice ou utilisateur professionnel, vous allez créer un formulaire adaptatif pour plusieurs canaux tels que le web, les appareils mobiles et les chats à l’aide de la création de formulaires adaptatifs avec des composants principaux standards prêts à l’emploi pour la capture de données.

### Exercice

1. Créez un point d’entrée d’envoi pour le formulaire :

   1. Ouvrez <https://requestbin.com/> dans un nouvel onglet du navigateur.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. Cliquez sur **Créer un répertoire bin public** et copiez l’URL du point d’entrée.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. Créez un formulaire adaptatif à l’aide de l’interface de l’assistant :

   1. Dans l’onglet du navigateur utilisé dans la leçon 1, accédez à l’interface web d’AEM Forms as Cloud Service, puis à Formulaires et Documents.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. Appuyez sur **Créer** et sélectionnez Formulaire adaptatif.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. Sélectionnez le modèle **vierge avec composants principaux** à partir de l’écran de sélection des modèles, comme illustré ci-dessous :
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Cliquez sur l’onglet **Style** et sélectionnez le thème **wknd-theme** comme illustré ci-dessous :
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Cliquez sur l’onglet **Envoi** et sélectionnez la carte **Envoyer vers le point d’entrée REST**, puis spécifiez le répertoire bin public dans le champ
      **URL de la requête POST** comme illustré ci-dessous :
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Cliquez sur **Créer**. Indiquez un nom et un titre pour votre formulaire. Par exemple : **contacteznous**. Cliquez sur **Créer**.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. L’éditeur de formulaire adaptatif s’ouvre. Ignorez les fenêtres contextuelles ou les boîtes de dialogue concernant les préférences ou les informations. Cliquez sur l’explorateur de composants sur le rail de gauche et ajoutez le composant **Pied de page** au bas du formulaire vierge.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. L’en-tête fait partie du modèle de formulaire adaptatif. Il permet de fournir facilement un en-tête/pied de page cohérent à tous les formulaires adaptatifs. Vous pouvez également décider qu’il continue à être modifiable dans le formulaire, comme pour le composant Pied de page de l’étape suivante.

   1. Ajoutez un composant **Titre** au milieu du formulaire.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. Ajoutez un composant **Entrée de texte** après celui de titre.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. Ajoutez un composant **Entrée numérique**.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. Ajoutez un composant **Bouton Envoyer** au formulaire.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. Cliquez sur le composant **Titre** pour que le **menu contextuel** s’affiche. Cliquez sur l’**icône Modifier** dans le menu pour modifier le libellé.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Saisissez `Contact Us` comme texte de titre.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. Cliquez sur le composant **Entrée de texte** pour afficher le menu contextuel. Cliquez sur l’**icône Modifier** dans le menu pour modifier le libellé.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Saisissez **Nom complet** comme libellé du champ.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. Cliquez sur le composant **Entrée de nombre** pour afficher le menu contextuel. Cliquez sur l’**Icône Modifier** dans le menu pour modifier le libellé.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. Saisissez le **Numéro de téléphone** comme libellé du champ.
      ![](/help/forms/assets/screenshot2028123829.png)


1. Ajoutez des validations au formulaire :

   1. Cliquez sur le composant **Numéro de téléphone** pour afficher le menu contextuel. Cliquez sur l’**icône Clé à molette** dans le menu pour configurer le champ.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. Ouvrez l’**onglet Validations**, marquez le champ comme **Obligatoire**, puis cliquez sur **Terminé**. Le message de réussite s’affiche.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. Cliquez sur **Aperçu** pour prévisualiser le formulaire du point de vue de l’utilisateur final ou de l’utilisatrice finale.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. Remplissez le formulaire avec des données factices.
      ![](/help/forms/assets/screenshot2028125629.png)

   1. Envoyer le formulaire
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Dans l’onglet Bin de requêtes, vérifiez les données envoyées.
      ![](/help/forms/assets/screenshot2028125829.png)

À présent, pour les besoins de l’exercice restant, utilisez un formulaire d’enregistrement précréé.

1. Ouvrez l’interface de gestion d’AEM Forms, par exemple : `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`, puis sélectionnez le formulaire d’enregistrement.

   ![](/help/forms/assets/screenshot2028115529.png)

1. Cliquez sur **Publier**.

   ![](/help/forms/assets/screenshot2028115629.png)

   Le message de réussite s’affiche.

   ![](/help/forms/assets/screenshot2028115729.png)

   L’URL de publication du formulaire est semblable à `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. Pour afficher le formulaire publié, remplacez l’ID de programme (pXXXXXX) et l’ID d’environnement (eXXXXXX) dans l’URL ci-dessus par les ID de votre 
environnement.

## Leçon 3

### Objectif

Mise à jour des styles à l’aide des bonnes pratiques de développement front-end.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprendrez comment mettre facilement à jour le style du formulaire adaptatif créé précédemment.

### Exercice

Configurez le référentiel local du thème :

1. Ouvrez l’invite de commande ou un shell avec les droits d’administrateur :

   ![](/help/forms/assets/screenshot2028115829.png)

1. Dans l’invite de commande, utilisez la commande suivante pour accéder au dossier **c:\git**.

   ```Shell
   cd c:\git
   ```

1. Utilisez la commande suivante pour cloner le code frontal du thème :

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Utilisez la commande suivante dans l’ordre indiqué pour accéder au répertoire **aem-forms-theme-canvas** et ouvrez Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. Sélectionnez **Approbation des auteurs de tous les fichiers du dossier parent** et cliquez sur **Oui, je fais confiance aux auteurs**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication Cloud Service, renommez le fichier `env_template`.  Pour renommer le fichier, cliquez avec le bouton droit de la souris **env_template** et sélectionnez la variable **Renommer** .

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. Définissez les valeurs suivantes pour les variables dans le fichier .env et enregistrez le fichier :

   * **AEM_URL** : spécifiez votre environnement de publication Cloud Service. Par exemple, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM** : spécifiez le chemin du formulaire. Par exemple, si le chemin du formulaire est `/content/forms/af/registration`, la valeur de cette variable sera `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Si vous recevez un message vous demandant de mettre à jour npm via la commande `npm notice Run npm nstall -g npm@9.6.0`, ignorez-le.
   > * N’exécutez pas d’autres commandes npm, sauf si cela est indiqué dans le classeur.

1. Exécutez maintenant la commande suivante pour prévisualiser le formulaire.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   Une fois la commande ci-dessus exécutée, attendez le message `webpack compiled`. Le formulaire s’affiche dans un onglet du navigateur.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm run live` pendant plus de 3 à 4 minutes, modifiez `localhost` dans l’URL du navigateur avec 127.0.0.1 et cliquez sur **Entrée**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Dans Visual Studio Code, ouvrez le fichier `PROJECT\src\site\_variables.scss`. Vous remarquerez que la couleur `$error` est une nuance de rouge.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Dans le navigateur, envoyez le formulaire pour afficher la couleur rouge dans le champ **Prénom**.

   ![](/help/forms/assets/screenshot2028120829.png)

1. Définissez la couleur **$error** sur **#5736eb** et enregistrez le fichier.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Actualisez le navigateur et envoyez le formulaire. Vous remarquerez que la couleur d’erreur du champ Prénom a été modifiée en conséquence.

   ![](/help/forms/assets/screenshot2028121129.png)

1. Dans l’invite de commande, appuyez sur **Ctrl+C**, saisissez **Y**, puis appuyez sur la touche **Entrée** pour arrêter le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.
1. Fermez les fenêtres Visual Studio Code et Invite de commande.

## Leçon 4

### Objectif

Effectuez le rendu du formulaire sur des interfaces web/mobile et d’autres interfaces en tant que formulaire découplé.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprendrez à effectuer le rendu du formulaire adaptatif créé précédemment en tant que formulaire découplé à l’aide du framework de conception React Spectrum.

### Exercice

Configurez le référentiel local à l’aide du projet de démarrage React :

1. Ouvrez l’invite de commande à l’aide des droits d’administration.

   ![](/help/forms/assets/screenshot2028115829.png)

1. Dans l’invite de commande, utilisez la commande suivante pour accéder au dossier **c:\git**.

   ```Shell
   cd c:\git
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage react du formulaire adaptatif :

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. Utilisez les commandes suivantes dans l’ordre indiqué pour accéder au répertoire **react-starter-kit-aem-headless-forms** et ouvrez Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   La fenêtre Visual Studio Code s’ouvre.

   ![](/help/forms/assets/screenshot2028117429.png)

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication de service cloud :

1. Renommez le fichier env_template en fichier .env. Pour renommer, cliquez avec le bouton droit de la souris sur le fichier **env_template** et sélectionnez l’option **Renommer**.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. Définissez les valeurs suivantes pour les variables du fichier .env. Après avoir mis à jour les variables, enregistrez le fichier.

   * **AEM_URL** : spécifiez l’URL de l’environnement de publication du service cloud. Par exemple, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH** : spécifiez le chemin d’accès au formulaire adaptatif créé dans la leçon précédente. Par exemple, `/content/forms/af/registration/`

     ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Ouvrez la fenêtre de commande, vérifiez que vous vous trouvez dans le répertoire react-starter-kit-aem-headless-forms, puis exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   La commande ci-dessus lance un serveur de développement local qui effectue le rendu de la définition de formulaire récupérée à partir d’AEM de manière déouplée à l’aide de la bibliothèque front-end react-spectrum.

   >[!NOTE]
   >
   > 
   > Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm start` pendant plus de 3 à 4 minutes, remplacez `localhost` dans l’URL du navigateur par 127.0.0.1 et appuyez sur **Entrée**.

   ![](/help/forms/assets/screenshot2028118229.png)

Vérifions l’exécution des règles dans ce formulaire découplé :

1. Sélectionnez l’option **Cocher la case pour recevoir 5 % de réduction**. L’option suivante d’utilisation de la carte de crédit est désactivée.

   ![](/help/forms/assets/screenshot2028126229.png)

1. Décochez l’option **Cocher la case pour recevoir 5 % de réduction** pour activer l’option de carte de crédit.

   ![](/help/forms/assets/screenshot2028126329.png)

Modifions le formulaire sur le serveur en tant qu’utilisateur professionnel et affichons les modifications répercutées automatiquement dans le formulaire découplé.

1. Ouvrez l’interface de gestion d’AEM Forms dans le navigateur.
\
1. Sélectionnez le formulaire d’**enregistrement** et cliquez sur **Modifier.** Cette action ouvre le formulaire dans l’éditeur de formulaires adaptatifs.

   ![](/help/forms/assets/screenshot2028118529.png)

1. Sélectionnez le champ **Numéro de téléphone** et cliquez sur l’**icône Modifier (icône de crayon)** dans la barre d’outils. Si la barre d’outils contextuelle ne s’affiche pas, basculez en mode d’édition en cliquant sur le bouton **Modifier** en haut à droite, à gauche du bouton **Aperçu**.

   ![](/help/forms/assets/screenshot2028119629.png)

1. Remplacez le libellé par Numéro de mobile. Cliquez sur n’importe quel espace vide du formulaire pour enregistrer les modifications apportées au formulaire.

   ![](/help/forms/assets/screenshot2028119729.png)

Publions maintenant le formulaire mis à jour pour propager les modifications dans l’environnement de publication.

1. Dans l’onglet de l’interface de gestion d’AEM Forms, sélectionnez le formulaire d’enregistrement, puis cliquez sur **Dépublier**. Si vous ne voyez pas le bouton **Dépublier**, passez à l’étape 3 pour publier directement les modifications.

   ![](/help/forms/assets/screenshot2028119829.png)

1. Cliquez sur **Dépublier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. Une fois le navigateur actualisé, sélectionnez le formulaire d’enregistrement et cliquez sur **Publier**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. Cliquez sur **Publier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Actualisez l’onglet du navigateur avec le formulaire découplé affiché. Notez que le libellé Numéro de téléphone a été remplacé par Numéro mobile.

   ![](/help/forms/assets/screenshot2028120529.png)

1. Ouvrez la fenêtre d’invite de commande utilisée pour démarrer le projet **react-starter-kit-aem-headless-forms**, appuyez sur **Ctrl+C**, puis
saisissez **Y** et appuyez sur la touche Entrée pour terminer le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.

1. Fermez les fenêtres Visual Studio Code et Invite de commande.


## Leçon 5

### Objectif

Effectuez le rendu du formulaire en tant que formulaire découplé à l’aide de l’interface utilisateur Material Google.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprenez à effectuer le rendu du formulaire adaptatif créé précédemment en tant que formulaire découplé à l’aide de l’interface utilisateur Material Google.

### Exercice

Configurez le référentiel local à l’aide du projet de démarrage de l’interface utilisateur Material :

1. Ouvrez l’invite de commande à l’aide des droits d’administration.

   ![](/help/forms/assets/screenshot2028115829.png)


1. Dans l’invite de commande, utilisez la commande suivante pour accéder au dossier **c:\git** :

   ```Shell
   cd c:\git
   ```

1. Exécutez les commandes suivantes dans l’ordre indiqué pour créer un dossier nommé mui et accédez au dossier mui à l’aide des commandes suivantes :

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage react du formulaire adaptatif :

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. Utilisez la commande suivante dans l’ordre indiqué pour accéder au dossier **react-starter-kit-aem-headless-forms**, puis ouvrez le code dans Visual Studio Code :

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication de service cloud :

1. Renommez le fichier **env_template** en fichier **.env**. Pour renommer, cliquez avec le bouton droit de la souris sur le fichier **env_template**, puis sélectionnez **Renommer**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. Définissez les valeurs suivantes pour les variables du fichier .env. Après avoir mis à jour les variables, enregistrez le fichier. Appuyez sur **Ctrl + S** pour enregistrer le fichier.

   * **AEM_URL** : spécifiez l’URL de l’environnement de publication Cloud Service.

   * **AEM_FORM_PATH** : spécifiez le chemin d’accès au formulaire adaptatif créé dans la leçon précédente. Par exemple, /content/forms/af/registration/

     ![](/help/forms/assets/screenshot2028126929.png)

1. Ouvrez la fenêtre de commande, assurez-vous que vous êtes au répertoire **react-starter-kit-aem-headless-forms**, puis exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   La commande démarre un serveur de développement local et effectue le rendu de la définition de formulaire récupérée à partir d’AEM de façon découplée à l’aide de
la bibliothèque frontend de l’interface utilisateur Material Google.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm start` pendant plus de 3 à 4 minutes, modifiez `localhost` dans l’URL du navigateur par 127.0.0.1 et appuyez sur **Entrée**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. Pour évaluer l’exécution de la même logique commercial dans ce rendu de formulaire :

   Sélectionnez **Cocher la case pour recevoir 5 % de réduction**. L’option suivante **Souhaitez-vous demander le formulaire de carte de crédit d’entreprise We.Finance ?** se désactive.

   ![](/help/forms/assets/screenshot2028127329.png)

## Leçon 6

### Objectif

Créez un autre aspect du formulaire découplé à l’aide des variantes de composants de l’interface utilisateur Material.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprenez à créer une représentation alternative de différents composants à l’aide de l’interface utilisateur Material pour le formulaire adaptatif créé précédemment par l’utilisatrice ou l’utilisateur professionnel.

### Exercice

Mettez à jour la variante des composants dans le projet découplé. Pour modifier la variante du composant de saisie de texte de l’interface utilisateur Material en `OutlinedInput` :

1. Dans Visual Code, accédez au composant de saisie de texte en ouvrant le fichier `index.tsx` à l’emplacement `src/components/textinput/index.tsx`.

1. Ajoutez `//` au début de la ligne de code 103. Cela convertit la ligne en commentaire.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Ajoutez ce qui suit à la ligne 104 pour utiliser une autre variante du composant, puis enregistrez le fichier. Appuyez sur **CTRL + S** pour enregistrer le fichier.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   Il est essentiel d’utiliser les majuscules correctement pour la variante « OutlinedInput » pour éviter l’échec de la compilation. La compilation de l’environnement de développement local commence automatiquement dans l’invite de commande. Patientez jusqu’à ce que le message suivant s’affiche.

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Actualisez le navigateur, s’il ne s’actualise pas automatiquement, pour voir le composant Entrée de texte utilisez une autre variante.

   ![](/help/forms/assets/screenshot2028127729.png)


   Cette modification se produit pour les utilisatrices et utilisateurs finaux sans modification de la définition de formulaire sur le serveur AEM Forms et est spécifique
au canal découplé en cours de traitement. Par exemple, le canal Web dans cet atelier.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Fermez les fenêtres Visual Studio Code et Invite de commande.

## Questions fréquentes

+++ L’assistant de formulaire adaptatif est-il accessible au public ?

Oui, il est disponible avec AEM Forms as a Cloud Service.

+++


+++ Les composants principaux sont-ils accessibles au public ?

Oui, les composants principaux de formulaires adaptatifs sont disponibles avec AEM Forms as a Cloud Service.

+++

+++ Les formulaires découplés sont-ils accessibles au public ?

Oui, les formulaires découplés sont disponibles avec AEM Forms as a Cloud Service.

+++

+++ Les formulaires découplés requièrent-ils une licence distincte ?

Non, les formulaires découplés utilisent la même mesure de valeur de licence et le même nombre d’envois de formulaire.

+++

+++ Les composants principaux et les formulaires découplés sont-ils disponibles avec AEM 6.5 Forms ?

Oui, les composants principaux des formulaires adaptatifs et les formulaires découplés sont disponibles avec AEM Forms 6.5 Service Pack 16 et ses versions ultérieures.

+++


## Étapes suivantes

Maintenant que vous avez appris à créer des formulaires adaptatifs et à les diffuser sur plusieurs canaux à l’aide de formulaires découplés, vous devez essayer de mettre en œuvre vos nouvelles compétences. Amusez-vous et allez de l’avant en créant et en proposant des expériences de capture de données exceptionnelles à vos utilisatrices et utilisateurs finaux, où qu’ils et elles se trouvent, et à grande échelle !

## Ressources

* [Présentation des composants principaux des formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr)

* [Création d’un formulaire adaptatif à l’aide des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=fr)

* [Mise à jour de la mise en forme pour le formulaire adaptatif basé sur les composants principaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=fr)

* [Formulaires adaptatifs découplés](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr)

* [Utilisation du kit de démarrage Headless React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=fr)

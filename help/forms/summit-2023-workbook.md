---
title: Création d’un Forms d’engagement à l’aide des composants principaux et sans affichage
seo-title: Build Engaging Forms Using Core Components and Headless
description: Création d’un Forms d’engagement à l’aide des composants principaux et sans affichage
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: a4d46fd14805bf68a40ffdbee9d2e5fcfdee2f95
workflow-type: tm+mt
source-wordcount: '4625'
ht-degree: 0%

---


# Création d’un Forms d’engagement à l’aide des composants principaux et sans affichage

## Présentation de l’atelier

Dans ce laboratoire pratique, vous apprenez :

Comment utiliser AEM Forms pour créer facilement des formulaires adaptatifs à l’aide des derniers composants principaux cohérents avec AEM Sites, activer les expériences de capture de données omnicanal en fournissant les formulaires adaptatifs sous forme de formulaires sans interface sur le web, les appareils mobiles et les conversations. Vous découvrez également les bonnes pratiques en matière de style, de personnalisations et de développement frontal.

## Principales acquisitions

* **Agilité commerciale**: En tant qu’utilisateur professionnel, je peux facilement créer une expérience de formulaire pour plusieurs canaux.

* **Puissance du développeur front-end**: En tant que développeur front-end, je peux contrôler l’expérience de l’utilisateur final à l’aide de formulaires sans interface.

* **Vitesse du développeur**: En tant que développeur, je peux personnaliser facilement et systématiquement les composants Sites et Forms.

## Prérequis


+++AEM Forms as Cloud Service sandbox


    &lt;table>
    &lt;thead>
    &lt;tr>&lt;th>name&lt;/th>&lt;th>username&lt;/th>&lt;th>Author instance URL&lt;/th>&lt;th>Publish Instance URL&lt;/th>&lt;/tr>
    &lt;/thead>
    &lt;tbody>
    &lt;tr>&lt;td>L716001&lt;/td>&lt;td>L716+001@summitlab.us&lt;/td>&lt;td>https://author-p105303-e986623.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p105303-e986623.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716002&lt;/td>&lt;td>L716+002@summitlab.us&lt;/td>&lt;td>https://author-p106405-e993047.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106405-e993047.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716003&lt;/td>&lt;td>L716+003@summitlab.us&lt;/td>&lt;td>https://author-p106406-e993049.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106406-e993049.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716004&lt;/td>&lt;td>L716+004@summitlab.us&lt;/td>&lt;td>https://author-p106398-e993114.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106398-e993114.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716005&lt;/td>&lt;td>L716+005@summitlab.us&lt;/td>&lt;td>https://author-p106407-e993048.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106407-e993048.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716006&lt;/td>&lt;td>L716+006@summitlab.us&lt;/td>&lt;td>https://author-p106408-e993155.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106408-e993155.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716007&lt;/td>&lt;td>L716+007@summitlab.us&lt;/td>&lt;td>https://author-p106343-e993067.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106343-e993067.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716008&lt;/td>&lt;td>L716+008@summitlab.us&lt;/td>&lt;td>https://author-p106399-e993108.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106399-e993108.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716009&lt;/td>&lt;td>L716+009@summitlab.us&lt;/td>&lt;td>https://author-p106344-e993064.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106344-e993064.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716010&lt;/td>&lt;td>L716+010@summitlab.us&lt;/td>&lt;td>https://author-p106409-e993051.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106409-e993051.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716011&lt;/td>&lt;td>L716+011@summitlab.us&lt;/td>&lt;td>https://author-p106345-e993060.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106345-e993060.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716012&lt;/td>&lt;td>L716+012@summitlab.us&lt;/td>&lt;td>https://author-p106346-e993061.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106346-e993061.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716013&lt;/td>&lt;td>L716+013@summitlab.us&lt;/td>&lt;td>https://author-p106410-e993153.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106410-e993153.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716014&lt;/td>&lt;td>L716+014@summitlab.us&lt;/td>&lt;td>https://author-p106502-e993073.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106502-e993073.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716015&lt;/td>&lt;td>L716+015@summitlab.us&lt;/td>&lt;td>https://author-p106401-e993112.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106401-e993112.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716016&lt;/td>&lt;td>L716+016@summitlab.us&lt;/td>&lt;td>https://author-p106452-e993115.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106452-e993115.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716017&lt;/td>&lt;td>L716+017@summitlab.us&lt;/td>&lt;td>https://author-p106453-e993113.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106453-e993113.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716018&lt;/td>&lt;td>L716+018@summitlab.us&lt;/td>&lt;td>https://author-p106411-e993050.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106411-e993050.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716019&lt;/td>&lt;td>L716+019@summitlab.us&lt;/td>&lt;td>https://author-p106454-e993116.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106454-e993116.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716020&lt;/td>&lt;td>L716+020@summitlab.us&lt;/td>&lt;td>https://author-p106347-e993063.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106347-e993063.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716021&lt;/td>&lt;td>L716+021@summitlab.us&lt;/td>&lt;td>https://author-p106455-e993109.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106455-e993109.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716022&lt;/td>&lt;td>L716+022@summitlab.us&lt;/td>&lt;td>https://author-p106456-e993110.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106456-e993110.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716023&lt;/td>&lt;td>L716+023@summitlab.us&lt;/td>&lt;td>https://author-p106466-e993291.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106466-e993291.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716024&lt;/td>&lt;td>L716+024@summitlab.us&lt;/td>&lt;td>https://author-p106413-e993156.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106413-e993156.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716025&lt;/td>&lt;td>L716+025@summitlab.us&lt;/td>&lt;td>https://author-p106348-e993066.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106348-e993066.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716026&lt;/td>&lt;td>L716+026@summitlab.us&lt;/td>&lt;td>https://author-p106414-e993154.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106414-e993154.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716027&lt;/td>&lt;td>L716+027@summitlab.us&lt;/td>&lt;td>https://author-p106349-e993065.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106349-e993065.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716028&lt;/td>&lt;td>L716+028@summitlab.us&lt;/td>&lt;td>https://author-p106415-e993152.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106415-e993152.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716029&lt;/td>&lt;td>L716+029@summitlab.us&lt;/td>&lt;td>https://author-p106350-e993068.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106350-e993068.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716030&lt;/td>&lt;td>L716+030@summitlab.us&lt;/td>&lt;td>https://author-p106351-e993062.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106351-e993062.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716031&lt;/td>&lt;td>L716+031@summitlab.us&lt;/td>&lt;td>https://author-p106417-e993158.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106417-e993158.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716032&lt;/td>&lt;td>L716+032@summitlab.us&lt;/td>&lt;td>https://author-p106418-e993159.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106418-e993159.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716033&lt;/td>&lt;td>L716+033@summitlab.us&lt;/td>&lt;td>https://author-p106503-e993080.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106503-e993080.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716034&lt;/td>&lt;td>L716+034@summitlab.us&lt;/td>&lt;td>https://author-p106457-e993125.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106457-e993125.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716035&lt;/td>&lt;td>L716+035@summitlab.us&lt;/td>&lt;td>https://author-p106504-e993081.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106504-e993081.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716036&lt;/td>&lt;td>L716+036@summitlab.us&lt;/td>&lt;td>https://author-p106458-e993120.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106458-e993120.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716037&lt;/td>&lt;td>L716+037@summitlab.us&lt;/td>&lt;td>https://author-p106419-e993160.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106419-e993160.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716038&lt;/td>&lt;td>L716+038@summitlab.us&lt;/td>&lt;td>https://author-p106420-e993162.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106420-e993162.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716039&lt;/td>&lt;td>L716+039@summitlab.us&lt;/td>&lt;td>https://author-p106517-e993235.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106517-e993235.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716040&lt;/td>&lt;td>L716+040@summitlab.us&lt;/td>&lt;td>https://author-p106506-e993079.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106506-e993079.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716041&lt;/td>&lt;td>L716+041@summitlab.us&lt;/td>&lt;td>https://author-p106507-e993074.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106507-e993074.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716042&lt;/td>&lt;td>L716+042@summitlab.us&lt;/td>&lt;td>https://author-p106508-e993075.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106508-e993075.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716043&lt;/td>&lt;td>L716+043@summitlab.us&lt;/td>&lt;td>https://author-p106421-e993163.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106421-e993163.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716044&lt;/td>&lt;td>L716+044@summitlab.us&lt;/td>&lt;td>https://author-p106459-e993121.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106459-e993121.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716045&lt;/td>&lt;td>L716+045@summitlab.us&lt;/td>&lt;td>https://author-p106467-e993292.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106467-e993292.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716046&lt;/td>&lt;td>L716+046@summitlab.us&lt;/td>&lt;td>https://author-p106518-e993234.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106518-e993234.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716047&lt;/td>&lt;td>L716+047@summitlab.us&lt;/td>&lt;td>https://author-p106511-e993076.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106511-e993076.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716048&lt;/td>&lt;td>L716+048@summitlab.us&lt;/td>&lt;td>https://author-p106512-e993077.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106512-e993077.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716049&lt;/td>&lt;td>L716+049@summitlab.us&lt;/td>&lt;td>https://author-p106460-e993124.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106460-e993124.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716050&lt;/td>&lt;td>L716+050@summitlab.us&lt;/td>&lt;td>https://author-p106519-e993237.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106519-e993237.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716051&lt;/td>&lt;td>L716+051@summitlab.us&lt;/td>&lt;td>https://author-p106513-e993084.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106513-e993084.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716052&lt;/td>&lt;td>L716+052@summitlab.us&lt;/td>&lt;td>https://author-p106461-e993122.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106461-e993122.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716053&lt;/td>&lt;td>L716+053@summitlab.us&lt;/td>&lt;td>https://author-p106514-e993082.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106514-e993082.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716054&lt;/td>&lt;td>L716+054@summitlab.us&lt;/td>&lt;td>https://author-p106462-e993123.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106462-e993123.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716055&lt;/td>&lt;td>L716+055@summitlab.us&lt;/td>&lt;td>https://author-p106463-e993127.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106463-e993127.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716056&lt;/td>&lt;td>L716+056@summitlab.us&lt;/td>&lt;td>https://author-p106515-e993083.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106515-e993083.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716057&lt;/td>&lt;td>L716+057@summitlab.us&lt;/td>&lt;td>https://author-p106464-e993126.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106464-e993126.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716058&lt;/td>&lt;td>L716+058@summitlab.us&lt;/td>&lt;td>https://author-p106520-e993236.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106520-e993236.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716059&lt;/td>&lt;td>L716+059@summitlab.us&lt;/td>&lt;td>https://author-p106423-e993161.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106423-e993161.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716060&lt;/td>&lt;td>L716+060@summitlab.us&lt;/td>&lt;td>https://author-p106516-e993078.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106516-e993078.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716061&lt;/td>&lt;td>L716+061@summitlab.us&lt;/td>&lt;td>https://author-p106521-e993240.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106521-e993240.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716062&lt;/td>&lt;td>L716+062@summitlab.us&lt;/td>&lt;td>https://author-p106424-e993308.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106424-e993308.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716063&lt;/td>&lt;td>L716+063@summitlab.us&lt;/td>&lt;td>https://author-p106468-e993295.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106468-e993295.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716064&lt;/td>&lt;td>L716+064@summitlab.us&lt;/td>&lt;td>https://author-p106425-e993309.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106425-e993309.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716065&lt;/td>&lt;td>L716+065@summitlab.us&lt;/td>&lt;td>https://author-p106426-e993314.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106426-e993314.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716066&lt;/td>&lt;td>L716+066@summitlab.us&lt;/td>&lt;td>https://author-p106469-e993293.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106469-e993293.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716067&lt;/td>&lt;td>L716+067@summitlab.us&lt;/td>&lt;td>https://author-p106522-e993238.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106522-e993238.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716068&lt;/td>&lt;td>L716+068@summitlab.us&lt;/td>&lt;td>https://author-p106470-e993299.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106470-e993299.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716069&lt;/td>&lt;td>L716+069@summitlab.us&lt;/td>&lt;td>https://author-p106427-e993311.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106427-e993311.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716070&lt;/td>&lt;td>L716+070@summitlab.us&lt;/td>&lt;td>https://author-p106428-e993310.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106428-e993310.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716071&lt;/td>&lt;td>L716+071@summitlab.us&lt;/td>&lt;td>https://author-p106471-e993298.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106471-e993298.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716072&lt;/td>&lt;td>L716+072@summitlab.us&lt;/td>&lt;td>https://author-p106429-e993315.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106429-e993315.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716073&lt;/td>&lt;td>L716+073@summitlab.us&lt;/td>&lt;td>https://author-p106523-e993239.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106523-e993239.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716074&lt;/td>&lt;td>L716+074@summitlab.us&lt;/td>&lt;td>https://author-p106472-e993300.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106472-e993300.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716075&lt;/td>&lt;td>L716+075@summitlab.us&lt;/td>&lt;td>https://author-p106430-e993312.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106430-e993312.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716076&lt;/td>&lt;td>L716+076@summitlab.us&lt;/td>&lt;td>https://author-p106524-e993241.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106524-e993241.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716077&lt;/td>&lt;td>L716+077@summitlab.us&lt;/td>&lt;td>https://author-p106431-e993313.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106431-e993313.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716078&lt;/td>&lt;td>L716+078@summitlab.us&lt;/td>&lt;td>https://author-p106473-e993294.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106473-e993294.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716079&lt;/td>&lt;td>L716+079@summitlab.us&lt;/td>&lt;td>https://author-p106474-e993297.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106474-e993297.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716080&lt;/td>&lt;td>L716+080@summitlab.us&lt;/td>&lt;td>https://author-p106475-e993296.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106475-e993296.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716081&lt;/td>&lt;td>L716+081@summitlab.us&lt;/td>&lt;td>https://author-p106476-e993353.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106476-e993353.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716082&lt;/td>&lt;td>L716+082@summitlab.us&lt;/td>&lt;td>https://author-p106525-e993247.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106525-e993247.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716083&lt;/td>&lt;td>L716+083@summitlab.us&lt;/td>&lt;td>https://author-p106526-e993244.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106526-e993244.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716084&lt;/td>&lt;td>L716+084@summitlab.us&lt;/td>&lt;td>https://author-p106527-e993243.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106527-e993243.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716085&lt;/td>&lt;td>L716+085@summitlab.us&lt;/td>&lt;td>https://author-p106477-e993356.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106477-e993356.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716086&lt;/td>&lt;td>L716+086@summitlab.us&lt;/td>&lt;td>https://author-p106478-e993355.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106478-e993355.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716087&lt;/td>&lt;td>L716+087@summitlab.us&lt;/td>&lt;td>https://author-p106528-e993245.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106528-e993245.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716088&lt;/td>&lt;td>L716+088@summitlab.us&lt;/td>&lt;td>https://author-p106432-e993316.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106432-e993316.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716089&lt;/td>&lt;td>L716+089@summitlab.us&lt;/td>&lt;td>https://author-p106529-e993242.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106529-e993242.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716090&lt;/td>&lt;td>L716+090@summitlab.us&lt;/td>&lt;td>https://author-p106436-e993320.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106436-e993320.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716091&lt;/td>&lt;td>L716+091@summitlab.us&lt;/td>&lt;td>https://author-p106480-e993301.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106480-e993301.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716092&lt;/td>&lt;td>L716+092@summitlab.us&lt;/td>&lt;td>https://author-p106530-e993246.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106530-e993246.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716093&lt;/td>&lt;td>L716+093@summitlab.us&lt;/td>&lt;td>https://author-p106481-e993352.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106481-e993352.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716094&lt;/td>&lt;td>L716+094@summitlab.us&lt;/td>&lt;td>https://author-p106482-e993354.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106482-e993354.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716095&lt;/td>&lt;td>L716+095@summitlab.us&lt;/td>&lt;td>https://author-p106531-e993248.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106531-e993248.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716096&lt;/td>&lt;td>L716+096@summitlab.us&lt;/td>&lt;td>https://author-p106483-e993357.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106483-e993357.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716097&lt;/td>&lt;td>L716+097@summitlab.us&lt;/td>&lt;td>https://author-p106433-e993318.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106433-e993318.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716098&lt;/td>&lt;td>L716+098@summitlab.us&lt;/td>&lt;td>https://author-p106532-e993249.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106532-e993249.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716099&lt;/td>&lt;td>L716+099@summitlab.us&lt;/td>&lt;td>https://author-p106434-e993317.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106434-e993317.adobeaemcloud.com&lt;/td>&lt;/tr>&lt;tr>&lt;td>L716100&lt;/td>&lt;td>L716+100@summitlab.us&lt;/td>&lt;td>https://author-p106435-e993319.adobeaemcloud.com&lt;/td>&lt;td>https://publish-p106435-e993319.adobeaemcloud.com&lt;/td>&lt;/tr>
    &lt;/tbody>
    &lt;/table>

+++

## Leçon 1

### Objectif

Familiarisez-vous avec l’environnement as a Cloud Service d’AEM Forms.

### Contexte de la leçon

Dans cette leçon, vous vous familiarisez avec l’environnement as a Cloud Service d’AEM Forms en naviguant dans l’interface utilisateur.

### Exercice

1. Ouvrez votre navigateur et saisissez l’URL de l’environnement de création du Cloud Service. Par exemple :
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Connectez-vous à l’environnement de création du Cloud Service en fonction des informations d’identification partagées. Par exemple : Nom d’utilisateur : [L716+001@summitlab.us](mailto:L716%2B001@summitlab.us)
Mot de passe : 
**Adobe123 !**

1. Une fois connecté, accédez à l’interface utilisateur d’AEM Forms. Cliquez sur **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. Cliquez sur **Forms et documents**. Ignorer les fenêtres contextuelles liées aux préférences ou aux informations.

   ![](/help/forms/assets/screenshot2028113929.png)

   Tous les formulaires disponibles sont affichés.

   ![](/help/forms/assets/screenshot2028114029.png)

## Leçon 2

### Objectif

Créez un formulaire adaptatif à l’aide des derniers composants principaux, configurez et envoyez le formulaire.

### Contexte de la leçon

Dans cette leçon, en tant qu’utilisateur professionnel, vous allez créer un formulaire adaptatif pour plusieurs canaux tels que le web, les appareils mobiles et les conversations à l’aide de la création de formulaires adaptatifs avec des composants principaux standard prêts à l’emploi pour la capture de données.

### Exercice

1. Créez un point de fin d’envoi pour le formulaire :

   1. Ouvrir <https://requestbin.com/> dans un nouvel onglet du navigateur.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. Cliquez sur **Création d’une classe publique** et copiez l’URL du point de terminaison .
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. Créez un formulaire adaptatif à l’aide de l’interface de l’assistant :

   1. Dans l’onglet du navigateur utilisé dans la leçon 1, accédez à l’interface web d’AEM Forms as Cloud Service et accédez à Forms et documents.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. Cliquez sur **Créer** et sélectionnez Formulaire adaptatif.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. Sélectionnez la **Vierge avec composants principaux** modèle à partir de l’écran de sélection de modèle, comme illustré ci-dessous :
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Cliquez sur le bouton **Style** et sélectionnez l’option **wknd-theme** comme illustré ci-dessous :
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Cliquez sur le bouton **Envoi** et sélectionnez l’option **Envoyer vers le point de fin REST** et spécifiez la corbeille publique dans la
      **URL de la demande du POST** comme illustré ci-dessous :
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Cliquez sur **Créer**. Indiquez un nom et un titre pour votre formulaire. Par exemple : **contactus**. Cliquez sur **Créer**.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. L’éditeur de formulaire adaptatif s’ouvre. Ignorer les fenêtres contextuelles ou les boîtes de dialogue pour les préférences ou les informations. Cliquez sur l’explorateur de composants sur le rail de gauche et ajoutez le **Pied de page** au bas du formulaire vierge.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. L’en-tête fait partie du modèle de formulaire adaptatif. Il permet de fournir facilement un en-tête/pied de page cohérent à tous les formulaires adaptatifs. Vous pouvez également choisir de le conserver modifiable dans le formulaire, comme pour le composant Pied de page de l’étape suivante.

   1. Ajouter un **Titre** au milieu du formulaire.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. Ajouter un **Entrée de texte** après le composant de titre.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. Ajouter un **Entrée numérique** composant.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. Ajouter un **Bouton Envoyer** du formulaire.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. Cliquez sur le bouton **Titre** pour que **menu contextuel** s’affiche. Cliquez sur le bouton **Icône Modifier** dans le menu pour modifier le libellé.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Entrée `Contact Us` comme texte de titre.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. Cliquez sur le bouton **Entrée de texte** pour afficher le menu contextuel. Cliquez sur le bouton **Icône Modifier** dans le menu pour modifier le libellé.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Entrée **Nom complet** comme libellé du champ.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. Cliquez sur le bouton **Entrée numérique** pour afficher le menu contextuel. Cliquez sur le bouton **Icône Modifier** dans le menu pour modifier le libellé.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. Saisissez le **Numéro de téléphone** comme libellé du champ.
      ![](/help/forms/assets/screenshot2028123829.png)


1. Ajouter des validations au formulaire :

   1. Cliquez sur le bouton **Numéro de téléphone** pour afficher le menu contextuel. Cliquez sur le bouton **Icône Forme** dans le menu pour configurer le champ.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. Ouvrez le **onglet validations**, marquez le champ **Obligatoire**, puis cliquez sur **Terminé**. Le message de réussite s’affiche.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. Cliquez sur **Aperçu** pour prévisualiser le formulaire du point de vue de l’utilisateur final.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. Remplissez le formulaire avec les données factices.
      ![](/help/forms/assets/screenshot2028125629.png)

   1. Envoyer le formulaire
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Dans l’onglet Panier de demandes, vérifiez les données envoyées.
      ![](/help/forms/assets/screenshot2028125829.png)

Maintenant, pour les besoins de l’exercice restant, utilisez un formulaire d’enregistrement précréé.

1. Ouvrez l’interface de gestion d’AEM Forms, par exemple : `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`, puis sélectionnez le formulaire d’enregistrement.

   ![](/help/forms/assets/screenshot2028115529.png)

1. Cliquez sur **Publier**. 

   ![](/help/forms/assets/screenshot2028115629.png)

   Le message de réussite s’affiche.

   ![](/help/forms/assets/screenshot2028115729.png)

   L’URL de publication du formulaire est similaire à `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. Pour afficher le formulaire publié, remplacez l’ID de programme (pXXXXXX) et l’ID d’environnement (eXXXX) dans l’URL ci-dessus par les ID de votre environnement.

## Leçon 3

### Objectif

Mettez à jour les styles à l’aide des bonnes pratiques de développement frontal.

### Contexte de la leçon

Dans cette leçon, en tant que développeur front-end, vous découvrez comment mettre facilement à jour le style du formulaire adaptatif créé précédemment.

### Exercice

Configurez le référentiel local du thème :

1. Ouvrez l’invite de commande ou un shell avec les droits d’administrateur :

   ![](/help/forms/assets/screenshot2028115829.png)

1. Dans l’invite de commande, utilisez la commande suivante pour accéder à **c:\git** folder

   ```Shell
   cd c:\git
   ```

1. Utilisez la commande suivante pour cloner le code frontal du thème :

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Pour accéder à la fonction **aem-forms-theme-canvas** et ouvrez Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. Sélectionner **Approbation des auteurs de tous les fichiers du dossier parent** et cliquez sur **Oui, je fais confiance aux auteurs.**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication de service cloud, renommez la variable `env_template` fichier .  Pour renommer le fichier, cliquez avec le bouton droit de la souris **env_template** et sélectionnez la variable **Renommer** .

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. Définissez les valeurs suivantes pour les variables du fichier .env et enregistrez le fichier :

   * **AEM_URL**: Spécifiez votre environnement de publication de service cloud. Par exemple, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: Spécifiez le chemin du formulaire. Par exemple, si le chemin du formulaire est `/content/forms/af/registration`, la valeur de cette variable serait `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. Dans la fenêtre d’invite de commande, exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Si vous recevez un message vous demandant de mettre à jour npm via le `npm notice Run npm nstall -g npm@9.6.0`, ignorez le message.
   > * N’exécutez pas d’autres commandes npm, sauf si vous y avez été invité.


1. Exécutez maintenant la commande suivante pour prévisualiser le formulaire.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   Une fois la commande ci-dessus exécutée, attendez la `webpack compiled` message. Le formulaire s’affiche dans un onglet de navigateur.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la fonction `npm run live` pendant plus de 3 à 4 minutes, modifiez `localhost` dans l’URL du navigateur à 127.0.0.1 et accédez à **Entrée**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Dans Visual Studio Code, ouvrez la `PROJECT\src\site\_variables.scss` fichier . Remarquez la variable `$error` la couleur est un nuage de ROUGE.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Dans le navigateur, envoyez le formulaire pour afficher la couleur rouge dans le **Prénom** champ .

   ![](/help/forms/assets/screenshot2028120829.png)

1. Définissez la variable **$error** couleur à **#5736eb** et enregistrez le fichier.

   ![](/help/forms/assets/screenshot2028120729.png)

1. Actualisez le navigateur et envoyez le formulaire. La couleur d’erreur du champ du prénom a été modifiée en conséquence.

   ![](/help/forms/assets/screenshot2028121129.png)

1. Dans l’invite de commande, appuyez sur **Ctrl+C**, saisissez **Y**, puis appuyez sur **Entrée** clé pour arrêter le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.
1. Fermez les fenêtres Code Visual Studio et Invite de commande .

## Leçon 4

### Objectif

Effectuez le rendu du formulaire sur des interfaces web/mobile et d’autres interfaces en tant que formulaire sans titre.

### Contexte de la leçon

Dans cette leçon, en tant que développeur front-end, vous apprendrez comment rendre le formulaire adaptatif créé précédemment en tant que formulaire sans tête à l’aide de la structure de conception du spectre de réaction.

### Exercice

Configurez le référentiel local à l’aide du projet de démarrage de la réaction :

1. Ouvrez l’invite de commande à l’aide des droits d’administrateur.

   ![](/help/forms/assets/screenshot2028115829.png)

1. Dans l’invite de commande, utilisez la commande suivante pour accéder à **c:\git** folder

   ```Shell
   cd c:\git
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage de la réaction du formulaire adaptatif :

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. Pour accéder à la fonction **response-starter-kit-aem-headless-forms** et ouvrez Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   La fenêtre Visual Studio Code s’ouvre.

   ![](/help/forms/assets/screenshot2028117429.png)

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication de service cloud :

1. Renommez le fichier env_template en fichier .env. Pour renommer, cliquez avec le bouton droit de la souris **env_template** et sélectionnez la variable **Renommer** .

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. Définissez les valeurs suivantes pour les variables du fichier .env . Après la mise à jour des variables, enregistrez le fichier.

   * **AEM_URL**: Spécifiez l’URL de l’environnement de publication du service cloud. Par exemple, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: Spécifiez le chemin d’accès au formulaire adaptatif créé dans la leçon précédente. Par exemple, `/content/forms/af/registration/`

      ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Ouvrez la fenêtre de commande, vérifiez que vous vous trouvez dans le répertoire response-starter-kit-aem-headless-forms, puis exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. Dans la fenêtre d’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   La commande ci-dessus lance un serveur de développement local qui rend la définition de formulaire récupérée à partir d’AEM sans interface à l’aide de la bibliothèque frontale du spectre de réaction.

   >[!NOTE]
   >
   > 
   > Si un écran vierge s’affiche dans le navigateur après l’exécution de la fonction `npm start` pendant plus de 3 à 4 minutes, modifiez `localhost` dans l’URL du navigateur à 127.0.0.1 et accédez à **Entrée**.

   ![](/help/forms/assets/screenshot2028118229.png)

Vérifions l&#39;exécution des règles sous cette forme sans tête :

1. Sélectionnez la **Cochez la case pour recevoir 5 % de réduction.** . L’option suivante permettant d’appliquer la carte de crédit est désactivée.

   ![](/help/forms/assets/screenshot2028126229.png)

1. Décocher **Cochez la case pour recevoir 5 % de réduction.** pour activer l’option de carte de crédit.

   ![](/help/forms/assets/screenshot2028126329.png)

Apportons des modifications au formulaire sur le serveur en tant qu’utilisateur professionnel et affichons automatiquement les modifications répercutées dans le formulaire sans en-tête.

1. Ouvrez l’interface de gestion d’AEM Forms dans le navigateur. Par exemple : [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Sélectionnez la **enregistrement** formulaire et clic **Modifier.** Il ouvre le formulaire dans l’éditeur de formulaires adaptatifs.

   ![](/help/forms/assets/screenshot2028118529.png)

1. Sélectionnez la **Numéro de téléphone** et cliquez sur le champ **Icône Modifier (icône de crayon)** dans la barre d’outils. Si la barre d’outils contextuelle ne s’affiche pas, basculez en mode d’édition en cliquant sur **Modifier** bouton en haut à droite, de gauche à **Aperçu** bouton .

   ![](/help/forms/assets/screenshot2028119629.png)

1. Remplacez le libellé par Numéro de mobile. Cliquez sur n’importe quel espace vide du formulaire pour enregistrer les modifications apportées au formulaire.

   ![](/help/forms/assets/screenshot2028119729.png)

Publions le formulaire mis à jour pour propager les modifications dans l’environnement de publication.

1. Dans l’onglet de l’interface de gestion d’AEM Forms, sélectionnez le formulaire d’enregistrement, puis cliquez sur **Annuler la publication**. Si vous ne voyez pas l’événement **Annuler la publication** , passez à l’étape 3 pour publier directement les modifications.

   ![](/help/forms/assets/screenshot2028119829.png)

1. Cliquez sur **Dépublier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. Une fois le navigateur actualisé, sélectionnez le formulaire d’enregistrement et cliquez sur **Publier**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. Cliquez sur **Publier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Actualisez l’onglet du navigateur avec le formulaire sans en-tête affiché. Notez que le libellé du numéro de téléphone a été remplacé par Numéro mobile.

   ![](/help/forms/assets/screenshot2028120529.png)

1. Ouvrez la fenêtre d’invite de commande utilisée pour démarrer la fonction **response-starter-kit-aem-headless-forms** projet, appuyez sur **Ctrl+C**, puis saisissez **Y** et appuyez sur la touche Entrée pour arrêter le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.

1. Fermez les fenêtres Code Visual Studio et Invite de commande .


## Leçon 5

### Objectif

Rendu du formulaire en tant que formulaire sans titre à l’aide de l’interface utilisateur Google Matériau

### Contexte de la leçon

Dans cette leçon, en tant que développeur front-end, vous apprenez à effectuer le rendu du formulaire adaptatif créé précédemment en tant que formulaire sans interface utilisateur Google Matériau.

### Exercice

Configurez le référentiel local à l’aide du projet de démarrage de l’interface utilisateur matérielle :

1. Ouvrez l’invite de commande à l’aide des droits d’administrateur.

   ![](/help/forms/assets/screenshot2028115829.png)


1. Dans l’invite de commande, utilisez la commande suivante pour accéder à **c:\git** folder:

   ```Shell
   cd c:\git
   ```

1. Exécutez les commandes suivantes dans l’ordre indiqué pour créer un dossier nommé mui et accédez au dossier mui à l’aide des commandes suivantes :

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage de la réaction du formulaire adaptatif :

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. Pour accéder à la fonction **response-starter-kit-aem-headless-forms** et ouvrez le code dans Visual Studio Code :

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication de service cloud :

1. Renommez la variable **env_template** vers **.env** fichier . Pour renommer, cliquez avec le bouton droit de la souris **env_template** et sélectionnez **Renommer**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. Définissez les valeurs suivantes pour les variables du fichier .env . Après la mise à jour des variables, enregistrez le fichier. Utilisez la variable **Ctrl + S** changer de combinaison pour enregistrer le fichier.

   * **AEM_URL**: Spécifiez l’URL de l’environnement de publication du service cloud. Par exemple : [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: Spécifiez le chemin d’accès au formulaire adaptatif créé dans la leçon précédente. Par exemple, /content/forms/af/registration/

      ![](/help/forms/assets/screenshot2028126929.png)

1. Ouvrez la fenêtre de commande, assurez-vous que vous êtes à l’emplacement **response-starter-kit-aem-headless-forms** et exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. Dans la fenêtre d’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   La commande permet de lancer un serveur de développement local et de rendre la définition de formulaire récupérée à partir d’AEM sans interface à l’aide de la bibliothèque frontale de l’interface utilisateur de Google Matériau.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la fonction `npm start` pendant plus de 3 à 4 minutes, modifiez `localhost` dans l’URL du navigateur à 127.0.0.1 et accédez à **Entrée**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. Pour évaluer l’exécution de la même logique métier dans ce rendu de formulaire :

   Sélectionner **Cochez la case pour recevoir 5 % de réduction.**. Option suivante **Souhaitez-vous demander le formulaire de carte de crédit d’entreprise We.Finance ?** est désactivé.

   ![](/help/forms/assets/screenshot2028127329.png)

## Leçon 6

### Objectif

Créez un autre aspect du formulaire sans tête à l’aide des variantes de composants de l’interface utilisateur matérielle.

### Contexte de la leçon

Dans cette leçon, en tant que développeur front-end, vous apprendrez à créer une représentation alternative de différents composants à l’aide de l’interface utilisateur matérielle pour le formulaire adaptatif créé précédemment par l’utilisateur chargé de la conception de parcours.

### Exercice

Mettez à jour la variante des composants dans le projet sans interface utilisateur. Pour modifier la variante du composant de saisie de texte de l’interface utilisateur matérielle en `OutlinedInput`:

1. Dans le code visuel, accédez au composant de saisie de texte en ouvrant le `index.tsx` fichier à l’emplacement `src/components/textinput/index.tsx`.

1. Ajouter `//` au début de la ligne de code 103. Elle convertit la ligne en commentaire.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Ajoutez ce qui suit à la ligne 104 pour utiliser une autre variante du composant et enregistrez le fichier. Utilisez la variable **Ctrl + S** changer de combinaison pour enregistrer le fichier.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   Il est essentiel d&#39;utiliser une mise en majuscules correcte pour la variante &#39;OutinedInput&#39; sinon la compilation échouerait. La compilation de l’environnement de développement local commence automatiquement dans l’invite de commande. Patientez jusqu’à ce que le message suivant s’affiche

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Actualisez le navigateur, s’il ne s’actualise pas automatiquement, pour voir le composant de saisie de texte utiliser une autre variante.

   ![](/help/forms/assets/screenshot2028127729.png)


   Cette modification se produit pour les utilisateurs finaux sans modification de la définition de formulaire sur le serveur AEM Forms et est spécifique au canal sans interface en cours de traitement. Par exemple, le canal web dans ce laboratoire.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Fermez Visual Studio Code et invite de commande Windows.

## Questions fréquentes

+++ L’assistant de formulaire adaptatif est-il disponible publiquement ?

Oui, il est disponible avec AEM Forms en tant que Cloud Service.

+++


+++ Les composants principaux sont-ils disponibles publiquement ?

Oui, les composants principaux de Forms adaptatif sont disponibles avec AEM Forms en tant que Cloud Service.

+++

+++ Les formulaires sans affichage sont-ils disponibles publiquement ?

Oui, les formulaires sans affichage sont disponibles avec AEM Forms en tant que Cloud Service.

+++

+++ Les formulaires sans affichage requièrent-ils une licence distincte ?

Non, les formulaires sans affichage utilisent la même mesure de valeur de licence, le même nombre d’envois de formulaire.

+++

+++ Les composants principaux et les formulaires sans affichage sont-ils disponibles avec AEM 6.5 Forms ?

Oui, les composants principaux des formulaires adaptatifs et les formulaires sans en-tête sont disponibles avec AEM Forms 6.5 Service Pack 16 et versions ultérieures.

+++


## Étapes suivantes

Maintenant que vous avez appris à créer des formulaires adaptatifs et à les diffuser sur plusieurs canaux à l’aide de formulaires sans interface, vous devez essayer de mettre en oeuvre vos nouvelles compétences. Amusez-vous et allez de l’avant en créant et en proposant des expériences de capture de données exceptionnelles à vos utilisateurs finaux, où ils sont, à grande échelle !

## Ressources

* [Présentation des composants principaux de formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [Créer un formulaire adaptatif à l’aide des composants principaux](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [Mise à jour de la mise en forme pour le formulaire adaptatif basé sur les composants principaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Formulaires adaptatifs sans affichage](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Utilisation du kit de démarrage React sans tête](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)



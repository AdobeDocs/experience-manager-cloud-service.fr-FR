---
title: Créer une intégration d’API
description: Utilisez des expressions de formulaires adaptatifs pour ajouter la validation et le calcul automatiques ainsi que pour activer ou désactiver la visibilité d’une section.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 7%

---


# Créer une intégration d’API

Dans ce tutoriel, 2 intégrations d’API sont créées

- GetAllCountries retourne une liste de pays
- GetChildren - Renvoie les enfants immédiats du pays ou de l’État représenté par l’ID de nom d’utilisateur

## GetAllCountries - Configuration de l&#39;intégration de l&#39;API

- Configuration de l’intégration de l’API

   - Nom d’affichage : GetAllCountries → un libellé pour cette API dans votre système.

   - URL de l’API : `https://secure.geonames.org/countryInfoJSON` - point d’entrée que vous appelez.

   - Méthode HTTP : GET - vous effectuez une requête GET simple.

   - Type de contenu : JSON - la réponse est attendue au format JSON.

- Options :

   - Chiffrement requis non coché - aucune couche de chiffrement au-delà de HTTPS.

   - Exécuter sur le client coché - l’appel est exécuté à partir du client/navigateur, et non côté serveur.
- Type d’authentification
   - Aucune : l’API GeoNames ne nécessite pas de clés OAuth ou API dans les en-têtes.
- Entrée:
   - La section input définit ce qui est envoyé dans l’API
   - **username** → type : String, envoyé dans la Requête, par défaut : gbedekar.
   - Chaque requête ajoute ?username=gbedekar à l’URL
- Sortie
   - La sortie définit les champs de la réponse JSON à extraire et à utiliser.
La réponse GeoNames se présente comme suit :

  ![réponse-json](assets/geonames-data.png)
   - Deux champs mappés à partir du tableau geonames :

     geonames[*].geonameId → en tant que nombre

     geonames[*].countryName → en tant que chaîne

     Le [*] signifie qu’il se répète pour chaque pays du tableau.



![obtenir-tous-les-pays &#x200B;](assets/api-integration.png)


## GetChildren

Elle demande des GeoNames pour les enfants immédiats de l’emplacement dont geonamesId est transmis en tant que paramètre de requête

- Configuration de l’intégration de l’API

   - Nom d’affichage : GetAllCountries → un libellé pour cette API dans votre système.

   - URL de l’API : `https://secure.geonames.org/children` → point d’entrée que vous appelez.

   - Méthode HTTP : GET → vous effectuez une requête GET simple.

   - Type de contenu : une réponse de → JSON est attendue au format JSON.

- Options :

   - Chiffrement requis non coché → aucune couche de chiffrement au-delà de HTTPS.

   - Exécuter sur le client coché → l’appel est exécuté à partir du client/navigateur, et non côté serveur.
- Type d’authentification
   - Aucune : l’API GeoNames ne nécessite pas de clés OAuth ou API dans les en-têtes.
- Entrée:
   - Définit ce qui est envoyé dans l’API
   - **username** → type : String, envoyé dans la Requête, par défaut : gbedekar.
   - Chaque requête ajoute ?username=gbedekar à l’URL
   - **geonameId** -> type : chaîne. Renvoie les enfants du pays/état représenté par le geonameId
   - **type** =>chaîne. La définition de sur json renvoie la réponse au format JSON.
- Sortie
   - Définit les champs de la réponse JSON à extraire et à utiliser.
La réponse GeoNames se présente comme suit :

  ![réponse-json](assets/child-elements-data.png)
   - Deux champs mappés à partir du tableau geonames :

     geonames[*].geonameId → en tant que nombre

     geonames[*].name → en tant que chaîne

     Le [*] signifie qu’il se répète pour chaque pays du tableau.


![get-children](assets/get-children-api-integration.png)

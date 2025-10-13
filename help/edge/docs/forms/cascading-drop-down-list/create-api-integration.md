---
title: Créer une intégration d’API
description: Créez 2 intégrations d’API avec deux API Geonames.
feature: Edge Delivery Services
role: User
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: ht
source-wordcount: '393'
ht-degree: 100%

---


# Créer une intégration d’API

Dans ce tutoriel, 2 intégrations d’API sont créées :

- GetAllCountries retourne une liste de pays.
- GetChildren renvoie les enfants immédiats du pays ou de l’État représenté par le geonameId.

## GetAllCountries : configuration de l’intégration d’API

- Configuration d’intégration d’API

   - Nom d’affichage : GetAllCountries → libellé de cette API dans votre système.

   - URL de l’API : `https://secure.geonames.org/countryInfoJSON` – point d’entrée que vous appelez.

   - Méthode HTTP : GET – vous effectuez une requête GET simple.

   - Type de contenu : JSON – la réponse est attendue au format JSON.

- Options :

   - Chiffrement requis non vérifié – aucune couche de chiffrement au-delà de HTTPS.

   - Exécution au niveau du client ou de la cliente vérifiée – l’appel est exécuté à partir du client, de la cliente, ou du navigateur, et non côté serveur.
- Type d’authentification
   - Aucun : l’API GeoNames ne nécessite pas de clés OAuth ou API dans les en-têtes.
- Entrée :
   - La section Entrée définit ce qui est envoyé dans l’API.
   - **nom d’utilisateur ou d’utilisatrice** → type : chaîne, envoyé dans la requête, par défaut : gbedekar.
   - Chaque requête ajoute ?username=gbedekar à l’URL
- Sortie
   - La sortie définit les champs de la réponse JSON à extraire et à utiliser.
La réponse GeoNames se présente comme suit :

  ![json-response](assets/geonames-data.png)
   - Deux champs mappés à partir du tableau geonames :

     geonames[*].geonameId → de type nombre

     geonames[*].countryName → de type chaîne

     [*] indique une répétition pour chaque pays du tableau.



![get-all-countries](assets/api-integration.png)


## GetChildren

Cela interroge GeoNames pour obtenir les enfants immédiats de l’emplacement dont le geonamesId est transmis en tant que paramètre de requête.

- Configuration d’intégration d’API

   - Nom d’affichage : GetAllCountries → libellé de cette API dans votre système.

   - URL de l’API : `https://secure.geonames.org/children` → point d’entrée que vous appelez.

   - Méthode HTTP : GET → vous effectuez une requête GET simple.

   - Type de contenu : JSON → la réponse est attendue au format JSON.

- Options :

   - Chiffrement requis non vérifié → aucune couche de chiffrement au-delà de HTTPS.

   - Exécution au niveau du client ou de la cliente vérifiée → l’appel est exécuté à partir du client, de la cliente, ou du navigateur, et non côté serveur.
- Type d’authentification
   - Aucun : l’API GeoNames ne nécessite pas de clés OAuth ou API dans les en-têtes.
- Entrée :
   - Définit ce qui est envoyé dans l’API
   - **nom d’utilisateur ou d’utilisatrice** → type : chaîne, envoyé dans la requête, par défaut : gbedekar.
   - Chaque requête ajoute ?username=gbedekar à l’URL
   - **geonameId** → type : chaîne. Renvoie les enfants du pays ou de l’État représenté par le geonameId
   - **Type** → chaîne. La définition sur JSON renvoie la réponse au format JSON.
- Sortie
   - Définit les champs de la réponse JSON à extraire et à utiliser.
La réponse GeoNames se présente comme suit :

  ![json-response](assets/child-elements-data.png)
   - Deux champs mappés à partir du tableau geonames :

     geonames[*].geonameId → de type nombre

     geonames[*].name → de type chaîne

     [*] indique une répétition pour chaque pays du tableau.


![get-children](assets/get-children-api-integration.png)

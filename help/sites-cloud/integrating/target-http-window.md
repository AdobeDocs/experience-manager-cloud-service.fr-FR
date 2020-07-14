---
title: Adobe de la fenêtre HTTP de la Cible AEM
description: 'Adobe de la fenêtre HTTP de la Cible AEM '
translation-type: tm+mt
source-git-commit: c193b38718622cd2e960a8e8833c2d295822dc33
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 4%

---


# Présentation {#introduction}

Cette page décrit les paramètres configurables présents dans la fenêtre HTTP Adobe AEM Cible.

## Paramètres {#parameters}

![Cible HTTP](assets/httpwindow.png "FenêtreCible HTTP Fenêtre")

La fenêtre contient les paramètres configurables suivants :

| Paramètre | Description |
|---|---|
| URL de l’API Adobe Target | URL de l’API d’Adobe Target. |
| Activer l’URL absolue | Détermine si la partie hôte de l’URL ou l’URL complète est utilisée. Cochez la case si vous souhaitez utiliser l’URL complète (complète). Par défaut, la case à cocher est désactivée. |
| Délai de connexion | Délai d’expiration (en millisecondes) jusqu’à ce qu’une connexion soit établie. La valeur par défaut est de 6 000 millisecondes. La valeur 0 est interprétée comme un délai d’expiration infini. |
| Dépassement de délai du socket | Délai (en millisecondes) d’attente des données ou période d’inactivité maximale entre deux paquets de données consécutifs. La valeur par défaut est de 3 000 millisecondes. |
| URL de Recommandations Adobe Target Remplacer le jeton Regex | Contrôle le jeton dans l’URL du point de terminaison de l’Adobe Target qui doit être remplacé pour pointer vers l’URL de l’API Recommandations de Cibles. |
| Adobe Target de l’URL de Recommandations Remplacer par un jeton | Remplacement de l’expression regex décrite dans le paramètre ci-dessus. Par conséquent, l’URL résultante pointe vers l’API Recommandations de Cibles. |

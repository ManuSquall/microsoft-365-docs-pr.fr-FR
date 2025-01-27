---
title: Gestion de la configuration de Pertinence dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MOE150
- MET150
ms.assetid: fd6be6d3-2e8d-449d-9851-03ab7546e6aa
ROBOTS: NOINDEX, NOFOLLOW
description: Lisez les recommandations pour configurer l’entraînement Pertinence dans Advanced eDiscovery pour qu’il note les fichiers selon leur pertinence et génère des résultats.
ms.openlocfilehash: 8ba09babc91f233514cd0195c3e1da08b07ccb3c
ms.sourcegitcommit: 222fb7fe2b26dde3d8591b61cc02113d6135012c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49760208"
---
# <a name="manage-relevance-setup-in-advanced-ediscovery-classic"></a>Gestion de la configuration de Pertinence dans Advanced eDiscovery (classique)

> [!NOTE]
> Pour utiliser Advanced eDiscovery, votre organisation doit souscrire un abonnement Office 365 E3 avec le module complémentaire Conformité avancée ou un abonnement E5. Si vous ne disposez pas d’un abonnement et que vous souhaitez essayer Advanced eDiscovery, vous pouvez vous [inscrire pour utiliser une version d’évaluation d’Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 La technologie Pertinence d’Advanced eDiscovery emploie des logiciels utilisés par des experts pour noter les fichiers selon leur pertinence. Elle peut être utilisée dans les processus d’évaluation rapide des cas, de sélection et de révision des échantillons de fichier. 
  
 Advanced eDiscovery comprend des composants adaptés à l’entraînement Pertinence et à l’étiquetage des fichiers liés à un cas. Il collecte des informations sur les échantillons de fichiers pertinents et non pertinents entraînés pour noter chaque fichier selon leur pertinence, puis il génère des résultats qui peuvent servir pendant et après le processus de révision des fichiers. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>Conseils de configuration de l’entraînement Pertinence

 Dans Advanced eDiscovery, dans la fenêtre **Cas**, sélectionnez un cas et cliquez sur **Atteindre le cas**. Cliquez sur **Pertinence** \> **Installation de Pertinence**. Suivez ces conseils pour configurer Pertinence. 
  
- **Étiquetage** : l’efficacité du processus d’entraînement itératif Pertinence dépend de la capacité de l’expert à étiqueter les échantillons de fichier avec précision et cohérence.

- **Sujets des cas** :
  
  - Pour chaque sujet, faites appel au même expert tout au long de l’entraînement Pertinence. Plusieurs experts ne peuvent pas étiqueter le même sujet en même temps.
  
  - Déterminez si chaque groupe de fichiers est pertinent par rapport à un sujet spécifique.

  - Si un sujet est défini de façon trop générale, Advanced eDiscovery peut générer un nombre excessif de fichiers non pertinents. Si un sujet est défini de façon trop restrictive, le processus d’entraînement Pertinence peut durer plus longtemps. 

  - À chaque cycle d’entraînement Pertinence, Advanced eDiscovery se concentre sur un seul sujet actif et des exemples de résultats temporaires sont affichés.

  - Dans un scénario à sujets multiples, le mode Échantillonnage permet de sélectionner des sujets à inclure dans le processus. Les sujets marqués « Inactif » ne sont pas traités tant que le mode Échantillonnage n’est pas modifié. Un sujet peut apparaître « Inactif » ou « Actif » pour un seul expert.

  - Advanced eDiscovery peut servir à générer des fichiers de privilège des candidats. Configurez un autre sujet selon son privilège. Si possible, entraînez et sélectionnez les fichiers selon leur pertinence, puis entraînez les fichiers selon leur privilège parmi les fichiers sélectionnés uniquement (rechargez les fichiers sélectionnés dans un cas distinct). 

  - Vous pouvez uniquement effectuer un traitement par lots si aucun échantillon n’est ouvert (quand vous cliquez sur Traitement par lots, une liste d’utilisateurs contenant des échantillons ouverts s’affiche). Un administrateur peut « fermer » les échantillons d’autres utilisateurs (seulement si ces utilisateurs ne sont pas en train d’étiqueter ces échantillons), en utilisant l’utilitaire « Modifier la pertinence » avec l’option « Tous les échantillons des utilisateurs ».

- **Métadonnées** : Advanced eDiscovery se concentre sur le contenu. Il ne tient pas compte des métadonnées dans les critères de pertinence.

- **Richesse** : si la richesse d’un sujet est inférieure à 3 % après évaluation, prévoyez d’alimenter l’entraînement Pertinence avec des fichiers pertinents et non pertinents connus.

- **Taille de fichier** : les fichiers volumineux (plus de 5 242 880 caractères de texte extrait) sont ignorés dans Pertinence. Ces fichiers ne participent pas au processus d’entraînement Pertinence et ne reçoivent pas de note de pertinence après le traitement par lots. Les fichiers de plus de 5 Mo peuvent être inclus dans le jeu d’évaluation.

## <a name="setting-up-case-issues"></a>Configuration des sujets des cas

Les paramètres décrits dans cette section sont disponibles dans Advanced eDiscovery **Pertinence** \> **Configuration de Pertinence**.
  
- Les sujets doivent être affectés à un utilisateur qui entraînera les fichiers.

- Les fichiers importés doivent ensuite être ajoutés au chargement en cours de traitement.

- Définissez et organisez les sujets attentivement, car cela peut influer sur les résultats de l’entraînement Pertinence.

Une fois les paramètres définis, le réviseur-expert peut commencer à entraîner les fichiers dans l’onglet **Pertinence**.

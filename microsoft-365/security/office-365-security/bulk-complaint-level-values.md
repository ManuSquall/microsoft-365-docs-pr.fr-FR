---
title: Valeurs de niveau de réclamation en bloc, expéditeurs de courrier indésirable, niveaux BCL, fonctionnement de BCL, indices BCL, courrier indésirable, en-tête de courrier indésirable, filtrage du courrier en nombre
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/23/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Les vers de publipostage en bloc ont des modèles d'envoi différents, ainsi que des pratiques de création de contenu et d'acquisition de liste variées. Certains sont de bons vers de publipostage en bloc et envoient des messages désirés comportant un contenu pertinent à leurs abonnés. Ces messages entraînent peu de réclamations de la part des destinataires. D'autres vers de publipostage en bloc envoient des messages non sollicités qui s'apparentent fortement à du courrier indésirable et entraînent de nombreuses réclamations de la part des destinataires. Pour distinguer ces types de vers de publipostage en bloc, une évaluation BCL (Bulk Complaint Level) est réalisée sur les messages qui en proviennent. Les évaluations BCL vont de 1 à 9 selon la probabilité de réclamations dues au ver de publipostage en bloc. Un expéditeur disposant d'une évaluation BCL de 9 peut entraîner un grand nombre de réclamations de la part des destinataires, tandis qu'un autre expéditeur ayant une évaluation BCL de 3 n'en générera probablement pas beaucoup. Microsoft utilise des sources internes et tierces pour identifier le courrier en masse et déterminer l'évaluation BCL appropriée. Cette évaluation est présentée dans l'en-tête X-Microsoft-Antispam de chaque message. Pour plus d'informations sur cet en-tête de message, voir En-têtes de messages anti-courrier indésirable.
ms.openlocfilehash: 9fa3549aab6f6c2a9f0c6efb0915a6a4f25eb810
ms.sourcegitcommit: 1162d676b036449ea4220de8a6642165190e3398
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37079464"
---
# <a name="bulk-complaint-level-values"></a>Valeurs BCL

Les vers de publipostage en bloc ont des modèles d'envoi différents, ainsi que des pratiques de création de contenu et d'acquisition de liste variées. Certains sont de bons vers de publipostage en bloc et envoient des messages désirés comportant un contenu pertinent à leurs abonnés. Ces messages entraînent peu de réclamations de la part des destinataires. D'autres vers de publipostage en bloc envoient des messages non sollicités qui s'apparentent fortement à du courrier indésirable et entraînent de nombreuses réclamations de la part des destinataires. Pour distinguer ces types de vers de publipostage en bloc, une évaluation BCL (Bulk Complaint Level) est réalisée sur les messages qui en proviennent. Les évaluations BCL vont de 1 à 9 selon la probabilité de réclamations dues au ver de publipostage en bloc. Un expéditeur disposant d'une évaluation BCL de 9 peut entraîner un grand nombre de réclamations de la part des destinataires, tandis qu'un autre expéditeur ayant une évaluation BCL de 3 n'en générera probablement pas beaucoup. Microsoft utilise des sources internes et tierces pour identifier le courrier en masse et déterminer l'évaluation BCL appropriée. Cette évaluation est présentée dans l'en-tête **X-Microsoft-Antispam** de chaque message. Pour plus d'informations sur cet en-tête de message, voir [En-têtes de messages anti-courrier indésirable](anti-spam-message-headers.md).

Dans la mesure où un expéditeur de courrier en nombre avec une note de 9 est susceptible de générer des plaintes, le BCL par défaut est 7. Cela signifie que les courriers en masse seront acceptés jusqu’à ce que le niveau de réclamation de 7 et que le courrier ne soit accepté par la suite. Plus le taux est faible, moins le courrier en masse est accepté. Si vos utilisateurs sont, et que leur travail est, confidentiel à envoyer du courrier en nombre et que votre BCL est défini sur 4, aucun courrier en masse avec une BCL plus élevée ne sera accepté.
  
Vous pouvez vous servir des valeurs BCL pour définir le niveau de filtrage en bloc souhaité pour votre organisation en suivant les étapes décrites dans la rubrique [Configuration de vos stratégies de filtrage du courrier indésirable](configure-your-spam-filter-policies.md).
  
D'autres valeurs BCL sont ajoutées et seront incluses ici à l'avenir. Le tableau suivant répertorie et décrit les valeurs BCL actuellement utilisées.
  
|||
|:-----|:-----|
|**Valeur BCL** <br/> |**Description** <br/> |
|0  <br/> |Le message ne provient pas d'un expéditeur en bloc.  <br/> |
|1, 2, 3  <br/> |Le message provient d'un expéditeur en bloc qui génère peu de réclamations.  <br/> |
|4, 5, 6, 7  <br/> |Le message provient d'un expéditeur en bloc qui génère un nombre moyen de réclamations.  <br/> |
|8, 9  <br/> |Le message provient d'un expéditeur en bloc qui génère un grand nombre de réclamations  <br/> |
   


---
title: Promouvoir votre environnement Microsoft 365 Defender d’évaluation en production, Microsoft 365 Defender évaluation, essayer une évaluation, conserver une évaluation, évaluation de production
description: Utilisez cet article pour promouvoir vos evals de MDI, MDO, MDE et MCAS dans votre environnement en Microsoft 365 Defender ou M365D.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 3204a5453e3b441e2899a347df6d9e5a6cca2808
ms.sourcegitcommit: bef7bd019531317d083c1125f7d339750c450b2f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2021
ms.locfileid: "53588124"
---
# <a name="promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>Promouvoir votre environnement d Microsoft 365 Defender d’évaluation vers la production

**S’applique à :**
- Microsoft 365 Defender

Pour promouvoir votre environnement Microsoft 365 Defender d’évaluation vers la production, achetez d’abord la licence nécessaire. Suivez les étapes de la procédure de création de l’environnement [eval](eval-create-eval-environment.md) et achetez la licence Office 365 E5 (au lieu de sélectionner Démarrer l’essai gratuit).

Ensuite, terminez toute configuration supplémentaire et développez vos groupes pilotes jusqu’à ce qu’ils atteignent la production complète. 

## <a name="microsoft-defender-for-identity"></a>Microsoft Defender pour l’identité
Defender for Identity ne nécessite aucune configuration supplémentaire. Assurez-vous simplement que vous avez acheté les licences nécessaires et installé le capteur sur tous vos contrôleurs de domaine Active Directory et serveurs AD FS (Active Directory Federation Services). 

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365
Après avoir correctement évalué ou piloté MDO, il peut être promu dans l’ensemble de votre environnement de production.
1. Achetez et provisionez les licences nécessaires et attribuez-les à vos utilisateurs de production.
2. Ré-exécutez les configurations de stratégie de base recommandées (standard ou strict) sur votre domaine de messagerie de production ou sur des groupes d’utilisateurs spécifiques.
3. Vous pouvez éventuellement créer et configurer des stratégies MDO personnalisées par rapport à votre domaine de messagerie de production ou à des groupes d’utilisateurs.  Toutefois, n’oubliez pas que les stratégies de référence attribuées seront toujours prioritaires sur les stratégies personnalisées.
4. Mettez à jour l’enregistrement MX public pour votre domaine de messagerie de production afin qu’il soit résolu directement dans EOP.
5. Désactivez toutes les passerelles SMTP tierces et désactivez ou supprimez les connecteurs EXO associés à ce relais.

## <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison
Pour promouvoir l’environnement d’évaluation de Microsoft Defender for Endpoint d’un pilote à un environnement de production, il vous suffit d’intégrer davantage de points de terminaison au service à l’aide de l’un des outils et [méthodes pris en charge.](../defender-endpoint/onboard-configure.md)

Utilisez les instructions générales suivantes pour intégrer davantage d’appareils à Microsoft Defender pour endpoint. 

1. Vérifiez que l’appareil remplit les [conditions minimales requises.](../defender-endpoint/minimum-requirements.md)
2. En fonction de l’appareil, suivez les étapes de configuration fournies dans la section d’intégration du portail Defender for Endpoint.
3. Utilisez l’outil de gestion et la méthode de déploiement appropriés pour vos appareils.
4.  Exécutez un test de détection pour vérifier que les appareils sont correctement intégrés et qu’ils font des rapports au service.

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security
Microsoft Cloud App Security ne nécessite aucune configuration supplémentaire. Assurez-vous simplement que vous avez acheté les licences nécessaires. Si vous avez étendue le déploiement à certains groupes d’utilisateurs, augmentez l’étendue de ces groupes jusqu’à ce que vous atteignez l’échelle de production. 

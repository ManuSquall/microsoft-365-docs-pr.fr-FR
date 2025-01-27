---
title: Répondre aux menaces web dans Microsoft Defender pour le point de terminaison
description: Répondre aux alertes liées aux sites web malveillants et indésirables. Comprendre comment la protection contre les menaces web informe les utilisateurs finaux par le biais de leurs navigateurs web et Windows notifications
keywords: protection web, protection contre les menaces web, navigation web, alertes, réponse, sécurité, hameçonnage, programme malveillant, attaque, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web, notifications, utilisateurs finaux, notifications Windows, page de blocage,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 110b379863b4c6e23c947c56faf831e136231237
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51688476"
---
# <a name="respond-to-web-threats"></a>Répondre aux menaces web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

La protection web dans Microsoft Defender pour point de terminaison vous permet d’examiner et de répondre efficacement aux alertes liées aux sites web et sites web malveillants dans votre liste d’indicateurs personnalisés.

## <a name="view-web-threat-alerts"></a>Afficher les alertes contre les menaces web
Microsoft Defender pour le point de terminaison génère les [alertes suivantes](manage-alerts.md) pour les activités web malveillantes ou suspectes :
- **Connexion suspecte bloquée** par la protection réseau : cette alerte est générée lorsqu’une  tentative d’accès à un site web malveillant ou à un site web dans votre liste d’indicateurs personnalisés est arrêtée par la protection réseau en *mode* blocage
- **Connexion suspecte** détectée par la protection réseau : cette alerte est générée lorsqu’une tentative d’accès à un site web malveillant ou à un site web dans votre liste d’indicateurs personnalisés est détectée par la protection réseau en mode *audit* uniquement

Chaque alerte fournit les informations suivantes : 
- Appareil qui a tenté d’accéder au site web bloqué
- Application ou programme utilisé pour envoyer la demande web
- URL ou URL malveillante dans la liste des indicateurs personnalisés
- Actions recommandées pour les répondeurs

![Image d’une alerte liée à la protection contre les menaces web](images/wtp-alert.png)

>[!Note]
>Pour réduire le volume d’alertes, Microsoft Defender pour point de terminaison consolide les détections de menaces web pour le même domaine sur le même appareil chaque jour en une seule alerte. Une seule alerte est générée et comptabilisée dans le rapport [de protection web.](web-protection-monitoring.md)

## <a name="inspect-website-details"></a>Inspecter les détails du site web
Vous pouvez approfondir l’analyse en sélectionnant l’URL ou le domaine du site web dans l’alerte. Une page sur cette URL ou ce domaine particulier s’ouvre avec différentes informations, notamment :
- Appareils qui ont tenté d’accéder au site web
- Incidents et alertes liés au site web
- Fréquence d’utilisation du site web dans les événements de votre organisation

    ![Image de la page de détails de l’entité de domaine ou d’URL](images/wtp-website-details.png)

[En savoir plus sur les pages d’URL ou d’entité de domaine](investigate-domain.md)

## <a name="inspect-the-device"></a>Inspecter l’appareil
Vous pouvez également vérifier l’appareil qui a tenté d’accéder à une URL bloquée. La sélection du nom de l’appareil sur la page d’alerte ouvre une page avec des informations complètes sur l’appareil.

[En savoir plus sur les pages d’entité d’appareil](investigate-machines.md)

## <a name="web-browser-and-windows-notifications-for-end-users"></a>Navigateur web et notifications Windows pour les utilisateurs finaux

Avec la protection web dans Microsoft Defender pour le point de terminaison, vos utilisateurs finaux ne pourront pas visiter des sites web malveillants ou indésirables à l’aide de Microsoft Edge ou d’autres navigateurs. Étant donné que le blocage est effectué par la [protection](network-protection.md)réseau, une erreur générique s’est produite à partir du navigateur web. Ils voient également une notification de Windows.

![Image de Microsoft Edge montrant une erreur 403 et la menace web de notification Windows bloqué ](images/wtp-browser-blocking-page.png)
 *sur Microsoft Edge*

![Image du navigateur web Chrome affichant un avertissement de connexion sécurisée et la menace web de notification Windows bloquée ](images/wtp-chrome-browser-blocking-page.png)
 *sur Chrome*

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Filtrage du contenu web](web-content-filtering.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)

---
title: Examiner microsoft Defender pour les alertes de point de terminaison
description: Utilisez les options d’examen pour obtenir des détails sur les alertes qui affectent votre réseau, ce qu’elles signifient et comment les résoudre.
keywords: examiner, examen, appareils, périphérique, file d’attente des alertes, tableau de bord, adresse IP, fichier, soumettre, envois, analyse approfondie, chronologie, recherche, domaine, URL, IP
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 8b3b864e716957c24893d2097249440b0a90f10a
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186100"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Examiner les alertes dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigatealerts-abovefoldlink) 

Examinez les alertes qui affectent votre réseau, comprenez ce qu’elles signifient et comment les résoudre.

Sélectionnez une alerte dans la file d’attente des alertes pour aller à la page d’alerte. Cet affichage contient le titre de l’alerte, les ressources affectées, le volet latéral détails et l’article sur l’alerte.

Dans la page d’alerte, commencez votre enquête en sélectionnant les biens affectés ou l’une des entités sous l’arborescence de l’article de l’alerte. Le volet d’informations se remplit automatiquement avec d’autres informations sur ce que vous avez sélectionné. Pour voir le type d’informations que vous pouvez afficher ici, lisez Les alertes de [révision dans Microsoft Defender pour le point de terminaison.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/review-alerts)

## <a name="investigate-using-the-alert-story"></a>Examiner l’utilisation de l’article d’alerte

L’article d’alerte explique pourquoi l’alerte a été déclenchée, les événements connexes qui se sont produits avant et après, ainsi que d’autres entités associées.

Les entités sont cliquables et chaque entité qui n’est pas une alerte peut être étendue à l’aide de l’icône développer sur le côté droit de la carte de cette entité. L’entité en cours d’utilisation est indiquée par une bande bleue sur le côté gauche de la carte de cette entité, avec l’alerte dans le titre en cours de mise au point au premier abord.

Développez les entités pour afficher les détails en un coup d’œil. La sélection d’une entité basculera le contexte du volet d’informations sur cette entité et vous permettra de passer en revue d’autres informations, ainsi que de gérer cette entité. La sélection *de...* à droite de la carte d’entité révélera toutes les actions disponibles pour cette entité. Ces mêmes actions apparaissent dans le volet d’informations lorsque cette entité est en focus.

> [!NOTE]
> La section de l’article sur l’alerte peut contenir plusieurs alertes, avec des alertes supplémentaires liées à la même arborescence d’exécution apparaissant avant ou après l’alerte que vous avez sélectionnée.

![Exemple d’un article d’alerte avec une alerte en focus et des cartes étendues](images/alert-story-tree.png)

## <a name="take-action-from-the-details-pane"></a>Action à partir du volet d’informations

Une fois que vous avez sélectionné une entité d’intérêt, le volet d’informations change pour afficher les informations sur le  type d’entité sélectionné, les informations historiques lorsqu’elle est disponible et propose aux contrôles d’agir sur cette entité directement à partir de la page d’alerte.

Une fois que vous avez terminé d’examiner, revenir à l’alerte que vous avez commencée, marquez l’état de l’alerte comme résolu et classez-le comme alerte **False** ou **Alerte True**.  La classification des alertes permet d’affiner cette fonctionnalité pour fournir plus d’alertes vraies et moins de fausses alertes.

Si vous la classez comme une alerte réelle, vous pouvez également sélectionner une détermination, comme illustré dans l’image ci-dessous.

![Extrait du volet d’informations avec une alerte résolue et la liste de détermination étendue](images/alert-details-resolved-true.png)

Si vous rencontrez une fausse alerte avec une application métier, créez une règle de suppression pour éviter ce type d’alerte à l’avenir.

![actions et classification dans le volet d’informations avec la règle de suppression mise en évidence](images/alert-false-suppression-rule.png)

> [!TIP]
> Si vous rencontrez des problèmes non décrits ci-dessus, utilisez le bouton pour fournir des commentaires ou 🙂 ouvrir un ticket de support.


## <a name="related-topics"></a>Voir aussi
- [Afficher et organiser la file d’attente des alertes de Microsoft Defender pour les points de terminaison](alerts-queue.md)
- [Gérer les alertes microsoft Defender pour les points de terminaison](manage-alerts.md)
- [Examiner un fichier associé à une alerte Defender for Endpoint](investigate-files.md)
- [Examiner les appareils dans la liste Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Defender for Endpoint](investigate-ip.md)
- [Examiner un domaine associé à une alerte Defender for Endpoint](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Defender for Endpoint](investigate-user.md)



---
title: Visitez le centre de mise en œuvre pour voir les actions de correction
description: Utiliser le centre de gestion des actions pour afficher les détails et les résultats à la suite d’un examen automatisé
keywords: action, centre, autoir, automatisé, examen, réponse, correction
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.date: 01/28/2021
ms.technology: mde
ms.openlocfilehash: cc806678bbb5ac19f7c4e035efb52b6ba7d1edb1
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52844909"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Visitez le centre de mise en œuvre pour voir les actions de correction

Pendant et après un examen automatisé, les actions de correction des détections de menaces sont identifiées. Selon la menace particulière et la façon dont [Microsoft Defender pour le](/windows/security/threat-protection) point de terminaison est configuré pour votre organisation, certaines actions de correction sont prises automatiquement et d’autres nécessitent une approbation. Si vous faites partie de l’équipe des opérations de sécurité de votre organisation, vous pouvez afficher les [actions](manage-auto-investigation.md#remediation-actions) de correction en attente et terminées dans le centre **de actions.** 


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="new-a-unified-action-center"></a>(NOUVEAU!) Un centre de l’action unifié


Nous sommes heureux d’annoncer un nouveau centre de travail unifié ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) )!

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Centre de Microsoft 365 de sécurité":::

Le tableau suivant compare le nouveau centre de l’action unifié au centre de l’action précédent.

|Nouveau centre de l’action unifié  |Centre de l’action précédent  |
|---------|---------|
|Répertorie les actions en attente et terminées pour les appareils et le courrier électronique dans un seul emplacement <br/>([Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) plus Microsoft Defender pour [Office 365](/microsoft-365/security/office-365-security/office-365-atp))|Répertorie les actions en attente et terminées pour les appareils <br/> ([Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) uniquement)   |
|Se trouve à l’emplacement :<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Se trouve à l’emplacement :<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| Dans le centre Microsoft 365 de sécurité, sélectionnez **Centre de sécurité.** <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Navigation vers le centre de sécurité dans le centre de Microsoft 365 de sécurité"::: | In the Centre de sécurité Microsoft Defender, choose **Automated investigations** Action  >  **center**. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Navigation vers le centre de l’action à partir du Centre de sécurité Microsoft Defender":::  |

Le centre de mise en œuvre unifié regroupe les actions de correction dans Defender pour Endpoint et Defender pour Office 365. Il définit un langage commun pour toutes les actions de correction et fournit une expérience d’examen unifiée. 

Vous pouvez utiliser le centre de l’action unifiée si vous avez les autorisations appropriées et un ou plusieurs des abonnements suivants :
- [Defender pour le point de terminaison](microsoft-defender-endpoint.md)
- [Defender pour Office 365](/microsoft-365/security/office-365-security/office-365-atp)
- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection) 

> [!TIP]
> Pour plus d’informations, voir [Requirements](/microsoft-365/security/mtp/prerequisites).

## <a name="using-the-action-center"></a>Utilisation du centre de l’action

Pour obtenir le centre de l’action unifiée dans le centre de sécurité Microsoft 365 amélioré :
1. Go to the Microsoft 365 security center ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.
2. Dans le volet de navigation, sélectionnez **Centre de l’action.** 

Lorsque vous visitez le centre de l’action, vous voyez deux onglets : **Actions en attente et** **Historique.** Le tableau suivant récapitule ce que vous verrez sur chaque onglet :

|Tab  |Description  |
|---------|---------|
|**Pending**     | Affiche une liste d’actions qui nécessitent une attention particulière. Vous pouvez approuver ou rejeter des actions une par une, ou sélectionner plusieurs actions si elles ont le même type d’action (telles que le fichier **de mise en quarantaine).** <br/>**CONSEIL**: veillez à examiner et à approuver [(ou rejeter)](manage-auto-investigation.md) les actions en attente dès que possible afin que vos enquêtes automatisées se terminent en temps voulu. |
|**Historique**     | Sert de journal d’audit pour les actions qui ont été entreprises, telles que : <br/>- Mesures correctives prises suite à des enquêtes automatisées <br>- Actions de correction approuvées par votre équipe des opérations de sécurité  <br/>- Commandes qui ont été exécutés et actions de correction appliquées pendant les sessions Live Response  <br/>- Mesures correctives prises par les fonctionnalités de protection contre les menaces dans Antivirus Microsoft Defender  <p>Fournit un moyen d’annuler certaines actions (voir [Annuler les actions terminées).](manage-auto-investigation.md#undo-completed-actions)       |

Vous pouvez personnaliser, trier, filtrer et exporter des données dans le centre de gestion de l’action.

:::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Colonnes et filtres dans le centre de l’action":::

- Sélectionnez un en-tête de colonne pour trier les éléments par ordre croissant ou décroit.
- Utilisez le filtre de période pour afficher les données du jour, de la semaine, des 30 ou 6 derniers mois.
- Choisissez les colonnes que vous souhaitez afficher.
- Spécifiez le nombre d’éléments à inclure sur chaque page de données.
- Utilisez des filtres pour afficher uniquement les éléments que vous souhaitez voir.
- Sélectionnez **Exporter** pour exporter les résultats vers .csv fichier. 

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et approuver des actions de correction](manage-auto-investigation.md)
- [Consultez le guide interactif : Examiner et corriger les menaces avec Microsoft Defender pour le point de terminaison](https://aka.ms/MDATP-IR-Interactive-Guide)
 
## <a name="see-also"></a>Voir aussi

- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)

---
title: Méthodes et propriétés des activités de correction
description: La réponse d’API contient les & gestion des vulnérabilités de correction des menaces créées dans votre client. Vous pouvez demander toutes les activités de correction, une seule activité de correction ou des informations sur les appareils exposés pour une tâche de correction sélectionnée.
keywords: api, correction, api de correction, obtenir, tâches de correction, méthodes de correction, propriétés de correction,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 67009961ecc3755b5af21b2e773bc817ea46bec0
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769232"
---
# <a name="remediation-activity-methods-and-properties"></a>Méthodes et propriétés des activités de correction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

La réponse de l’API [contient les & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)de correction des menaces qui ont été   créées dans votre client.  

## <a name="methods"></a>Méthodes

Méthode | Type de données | Description
:---|:---|:---
[Répertorier toutes les activités de correction](get-remediation-all-activities.md) | Collection d’examens | Retourne des informations sur toutes les activités de correction.
[Répertorier les appareils exposés d’une activité de correction](get-remediation-exposed-devices-activities.md) | Entité Investigation | Retourne des informations sur les appareils exposés pour l’activité de correction spécifiée.
[Obtenir une activité de correction par son ID](get-remediation-one-activity.md) | Entité Investigation | Renvoie des informations pour l’activité de correction spécifiée.

En savoir plus sur [les activités de correction.](tvm-remediation.md)

## <a name="properties"></a>Propriétés

ID de propriété | Type de données | Description
:---|:---|:---
category | String | Catégorie de l’activité de correction (configuration logicielle/sécurité)
completerEmail | String | Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son courrier électronique
completerId | String | Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son ID d’objet
completionMethod | String | Une activité de correction peut être effectuée « automatiquement » (si tous les appareils sont corrigés) ou « manuellement » par une personne qui sélectionne « marquer comme terminé ».
createdOn | Date/heure | Heure de création de cette activité de correction
description | String | Description de cette activité de correction
dueOn | Date/heure | Date d’échéance définie par le créateur pour cette activité de correction
fixedDevices |  | Nombre d’appareils qui ont été corrigés
id | String | ID de cette activité de correction
nameId | String | Nom du produit associé
priorité | String | Priorité définie par le créateur pour cette activité de correction (Haute\Moyenne\Faible)
productId | String | ID de produit associé
productivityImpactRemediationType | String | Quelques modifications de configuration peuvent être demandées uniquement pour les appareils sans impact sur l’utilisateur. Cette valeur indique la sélection entre « tous les appareils exposés » ou « uniquement les appareils sans impact sur l’utilisateur ».
rbacGroupNames | String | Noms de groupes d’appareils associés
recommendedProgram | String | Programme recommandé pour la mise à niveau vers
recommendedVendor | String | Fournisseur recommandé pour la mise à niveau vers
recommendedVersion | String | Version recommandée pour la mise à jour/mise à niveau vers
relatedComponent | String | Composant connexe de cette activité de correction (similaire au composant associé pour une recommandation de sécurité)
requesterEmail | String | Adresse de messagerie du créateur
requesterId | String | ID d’objet Creator
requesterNotes | String | Notes (texte libre) ajoutées par le créateur pour cette activité de correction
scid | String | SCID de la recommandation de sécurité associée
status | String | État de l’activité de correction (actif/terminé)
statusLastModifiedOn | Date/heure | Date de mise à jour du champ d’état
targetDevices | Entier long | Nombre d’appareils exposés pour qui cette correction s’applique
title | String | Titre de cette activité de correction
type | String | Type de correction
vendorId | String | Nom du fournisseur associé

## <a name="see-also"></a>Voir aussi

- [Obtenir une activité de correction par son ID](get-remediation-one-activity.md)

- [Répertorier toutes les activités de correction](get-remediation-all-activities.md)

- [Répertorier les appareils exposés d’une activité de correction](get-remediation-exposed-devices-activities.md)

- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)

- [Vulnérabilités de votre organisation](tvm-weaknesses.md)

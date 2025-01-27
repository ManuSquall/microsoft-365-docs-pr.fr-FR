---
title: Créer des notifications pour les activités de correspondance de données exactes
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: En savoir plus sur la création des notifications pour les activités de correspondance de données exactes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: da00c43ae9ba5b129129027df16f49ef80b8757d
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "53288166"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>Créer des notifications pour les activités de correspondance de données exactes

Lorsque vous [Créer des types d’informations sensibles personnalisés à l’aide de la correspondance de données exacte (EDM)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) le [journal d’audit](search-the-audit-log-in-security-and-compliance.md#requirements-to-search-the-audit-log)crée un certain nombre d'activités. Vous pouvez utiliser la cmdlet PowerShell [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) pour créer des notifications qui vous avertiront de l’événement :

- CreateSchema
- EditSchema
- RemoveSchema
- UploadDataFailed
- UploadDataCompleted

## <a name="pre-requisites"></a>Conditions préalables

Le compte que vous utilisez doit être l’un des suivants :

- un administrateur général
- administrateur de conformité
- Administrateur Exchange Online

Pour en avoir plus sur les autorisations DLP, consultez la section[Autorisations](data-loss-prevention-policies.md#permissions).

La classification EDM est incluse dans ces abonnements

- Office 365 E5
- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Microsoft E5/A5 Information Protection et gouvernance

Si vous souhaitez en savoir plus les licences DLP, consultez la rubrique [Instructions relatives aux licences Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>Configurer les notifications pour les activités EDM

1. Se connecter à l’interface [PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell) 

2. Exécutez la cmdlet `New-ProtectionAlert` à l’aide de l’activité pour laquelle vous souhaitez créer la notification.  Par exemple, si vous souhaitez être averti de l'exécution de l'action **UploadDataCompleted**, exécutez

```powershell
New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <***address to send  notification to***> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
```

pour l’action **UploadDataFailed** vous pouvez exécuter

```powershell
New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <***SMTP address to send notification to***> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
```

## <a name="related-articles"></a>Articles connexes

- [Créer des types d’informations sensibles personnalisés à l’aide de la correspondance de données exacte (EDM)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)
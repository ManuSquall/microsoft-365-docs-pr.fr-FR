---
title: Étendre la couverture de recherche avancée avec les bons paramètres
description: Vérifiez les paramètres d’audit sur les appareils Windows et d’autres paramètres pour vous assurer que vous obtenez les données les plus complètes dans le cadre d’un recherche avancée
keywords: advanced hunting, incident, pivot, entity, audit settings, user account management, security group management, threat hunting, cyber threat hunting, search, query, telemetry, Microsoft 365, Microsoft Threat Protection
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: eaa0068fe52119bfd9dc2381b253b259cb8df907
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51062086"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Étendre la couverture de recherche avancée avec les bons paramètres

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[La recherche](advanced-hunting-overview.md) avancée repose sur des données provenant de différentes sources, notamment vos appareils, vos espaces de travail Office 365, Azure AD et Microsoft Defender pour l’identité. Pour obtenir les données les plus complètes possibles, assurez-vous que vous avez les paramètres corrects dans les sources de données correspondantes.

## <a name="advanced-security-auditing-on-windows-devices"></a>Audit de sécurité avancée sur les appareils Windows
Activer ces paramètres d’audit avancés pour vous assurer que vous obtenez des données sur les activités sur vos appareils, notamment la gestion des comptes local, la gestion des groupes de sécurité locaux et la création de services.

| Data | Description | Table schema | Procédure de configuration |
| --- | --- | --- | --- |
| Gestion des comptes | Événements capturés en tant que différentes valeurs indiquant la création, la suppression et d’autres activités liées `ActionType` au compte | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [auditer la gestion des comptes d’utilisateurs](/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Gestion des groupes de sécurité | Événements capturés en tant que différentes valeurs indiquant la création d’un groupe de `ActionType` sécurité local et d’autres activités de gestion des groupes locaux | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [auditer la gestion des groupes de sécurité](/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Installation du service | Événements capturés `ActionType` avec la valeur , indiquant `ServiceInstalled` qu’un service a été créé | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Déployer une stratégie d’audit de sécurité avancée : [auditer l’extension du système de sécurité](/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [En savoir plus sur les stratégies d’audit de sécurité avancées](/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>Capteur Microsoft Defender pour l’identité sur le contrôleur de domaine
Si vous exécutez Active Directory en local, vous devez installer le capteur Microsoft Defender pour l’identité sur le contrôleur de domaine pour obtenir des données pour Microsoft Defender pour l’identité. Lorsqu’elles sont installées et configurées correctement, ces données sont également intégrées au recherche avancée via Microsoft Defender for Identity et fournissent une image plus globale des informations d’identité et des événements de votre réseau. Ces données améliorent également la capacité de Microsoft Defender pour l’identité à générer des alertes pertinentes qui sont également couvertes par le recherche avancée. 

| Data | Description | Table schema | Procédure de configuration |
| --- | --- | --- | --- |
| Contrôleur de domaine | Données provenant d’Active Directory local envoyées à Microsoft Defender pour l’identité, enrichissant les informations d’identité, telles que les détails du compte, l’activité d’accès et les requêtes Active Directory | Plusieurs tables, y [compris IdentityInfo,](advanced-hunting-identityinfo-table.md) [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)et [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)  | - [Installer le capteur Microsoft Defender pour l’identité](/azure-advanced-threat-protection/install-atp-step4)<br>- [Activer les événements Windows pertinents](/azure-advanced-threat-protection/configure-event-collection) |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
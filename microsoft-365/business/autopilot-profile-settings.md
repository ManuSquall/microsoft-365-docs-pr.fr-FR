---
title: À propos des paramètres du profil AutoPilot
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
f1_keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: Les profils AutoPilot vous aident à contrôler Windows l’installation des appareils des utilisateurs. Les profils contiennent des paramètres par défaut et facultatifs comme ignorer l’installation de Cortana.
ms.openlocfilehash: 86f8718131f0a0b93e18e65e39e02e7d65aded1a
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51578504"
---
# <a name="about-autopilot-profile-settings"></a>À propos des paramètres du profil AutoPilot

## <a name="autopilot-profile-settings"></a>Paramètres de profil AutoPilot

Vous pouvez utiliser les profils AutoPilot pour contrôler la Windows sur les appareils des utilisateurs. Les profils contiennent les paramètres suivants.
  
 **Fonctionnalités autoPilot par défaut (obligatoires) qui sont définies automatiquement :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer l’inscription de Cortana, OneDrive et OEM  <br/> |Ignore l’installation d’applications grand public telles que Cortana et les OneDrive. L’utilisateur de l’appareil peut les installer ultérieurement tant que l’utilisateur est un administrateur local sur l’appareil. L’inscription du fabricant d’origine est ignorée, car l’appareil sera géré par Microsoft 365 Business Premium.  <br/> |
|Expérience de signature avec la marque de votre entreprise  <br/> |Si votre entreprise dispose d’une marque Ajouter votre marque à [Microsoft 365 page](../admin/setup/customize-sign-in-page.md)de Microsoft 365, l’utilisateur de l’appareil reçoit cette expérience lors de la signature.  <br/> |
|Inscription automatique mdm avec des comptes AAD configurés.  <br/> |L’identité de l’utilisateur est gérée par Azure Active Directory et les utilisateurs se connectent à Windows et Microsoft 365 avec leurs informations d Microsoft 365 Business Premium personnelles.  <br/> |
   
 **Paramètres facultatifs :**
  
|**Paramètre**|**Description**|
|:-----|:-----|
|Ignorer les paramètres de confidentialité (par défaut)  <br/> |Si cette option est définie sur **On,** l’utilisateur de l’appareil ne verra pas le contrat de licence de l’appareil et Windows lors de sa première se connecté.  <br/> |
|Ne pas autoriser l’utilisateur à devenir l’administrateur local  <br/> |Si cette option est définie sur **Activé,** l’utilisateur de l’appareil ne pourra pas installer d’applications personnelles, telles que Cortana.<br/> |

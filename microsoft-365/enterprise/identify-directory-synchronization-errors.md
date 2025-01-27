---
title: Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Découvrez comment afficher les erreurs de synchronisation d’annuaires et les correctifs possibles dans Microsoft 365 centre d’administration.
ms.openlocfilehash: 76717fc158aa0cee47f784919f19a295378bbd5b
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50907503"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365

Vous pouvez afficher les erreurs de synchronisation d’annuaires dans Microsoft 365'administration centrale. Seules les erreurs de l’objet User sont affichées. Pour afficher les erreurs avec PowerShell, voir [Identifier les objets avec DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Afficher les erreurs de synchronisation d’annuaires dans Microsoft 365'administration centrale

Pour afficher les erreurs dans le centre d Microsoft 365'administration:
  
1. Connectez-vous au [centre Microsoft 365'administration](https://admin.microsoft.com) avec un compte d’administrateur général. 
    
2. Dans  la page d’accueil, vous verrez la carte de **gestion utilisateur.** 
    
    ![La carte de gestion des utilisateurs dans le centre d Microsoft 365'administration](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. Sur la carte, sélectionnez **Erreurs de** synchronisation sous **Azure AD Connecter** pour voir les erreurs dans la page Erreurs de synchronisation **d’annuaires.**   
    
    ![Exemple de page d’erreurs de synchronisation d’annuaires](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Choisissez l’une des erreurs pour afficher le volet d’informations avec des informations sur l’erreur et des conseils sur la façon de la corriger.

   ![Exemple des détails d’une erreur de synchronisation d’annuaires](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Après l’affichage, voir [résoudre les problèmes liés à](fix-problems-with-directory-synchronization.md) la synchronisation d’annuaires pour Microsoft 365 résoudre les problèmes identifiés.
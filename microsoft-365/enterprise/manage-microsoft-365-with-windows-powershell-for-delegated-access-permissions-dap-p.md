---
title: Gérer les Microsoft 365 avec Windows PowerShell pour les partenaires DAP
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Comment les partenaires de syndication et de fournisseur de solutions Cloud (CSP) peuvent utiliser Windows PowerShell pour gérer Microsoft 365 clients.
ms.openlocfilehash: 352a9a01414b94a1593de6a734151b687524fe7d
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50909525"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>Comment gérer les Microsoft 365 avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les partenaires avec autorisation d'accès délégué sont les partenaires de syndication et fournisseurs de solutions cloud. De nombreux fournisseurs sont des fournisseurs de réseau ou de télécommunication. Ils regroupent Microsoft 365 abonnements dans leurs offres de services. Lorsqu’ils vendent un abonnement Microsoft 365, ils se voient automatiquement accorder des autorisations Administrer de la part de (AOBO) sur les locations du client afin de pouvoir administrer ces locations et en rendre compte. Ces tâches sont difficiles à effectuer dans le centre d Microsoft 365'administration. Il est beaucoup plus facile d’utiliser PowerShell pour Microsoft 365 effectuer des tâches administratives telles que :
- List all the customer **TenantIds** and their domains 
- Identifier tous les utilisateurs d’une location client et leurs licences attribuées
> [!NOTE]
> Certaines tâches administratives peuvent uniquement être réalisées dans PowerShell.

Les articles suivants montrent comment les partenaires de syndication et de CSP utilisent PowerShell pour administrer les locations de leurs clients :
  
- [Gérer Microsoft 365 clients avec Windows PowerShell pour les partenaires avec autorisations d’accès délégué](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [Ajout d'un domaine à la location d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
- [Récupération des données des rapports du locataire d'un client avec Windows PowerShell pour les partenaires avec autorisation d'accès délégué](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)

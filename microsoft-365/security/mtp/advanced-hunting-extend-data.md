---
title: Étendre la couverture de la chasse avancée avec les paramètres corrects
description: Vérifier les paramètres d’audit sur les appareils Windows et d’autres paramètres pour vous aider à obtenir les données les plus complètes dans la recherche avancée
keywords: chasse avancée, incident, tableau croisé dynamique, entité, paramètres d’audit, gestion des comptes d’utilisateur, gestion des groupes de sécurité, recherche des menaces, recherche dans les menaces informatiques, recherche, requête, télémétrie, Microsoft 365, protection contre les menaces de Microsoft
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 9c1b9c1853d80d818d97084e2668d3b12b6da0e6
ms.sourcegitcommit: 1b83b6bcacb997324bc4be355deba6daf319591d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46503215"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a><span data-ttu-id="cfed2-104">Étendre la couverture de la chasse avancée avec les paramètres corrects</span><span class="sxs-lookup"><span data-stu-id="cfed2-104">Extend advanced hunting coverage with the right settings</span></span>

<span data-ttu-id="cfed2-105">**S’applique à :**</span><span class="sxs-lookup"><span data-stu-id="cfed2-105">**Applies to:**</span></span>
- <span data-ttu-id="cfed2-106">Protection Microsoft contre les menaces</span><span class="sxs-lookup"><span data-stu-id="cfed2-106">Microsoft Threat Protection</span></span>

<span data-ttu-id="cfed2-107">La [chasse avancée](advanced-hunting-overview.md) repose sur les données provenant de différentes sources, notamment vos appareils, vos espaces de travail Office 365, Azure ad et Azure ATP.</span><span class="sxs-lookup"><span data-stu-id="cfed2-107">[Advanced hunting](advanced-hunting-overview.md) relies on data coming from various sources, including your devices, your Office 365 workspaces, Azure AD, and Azure ATP.</span></span> <span data-ttu-id="cfed2-108">Pour obtenir les données les plus complètes possible, vérifiez que vous disposez des paramètres corrects dans les sources de données correspondantes.</span><span class="sxs-lookup"><span data-stu-id="cfed2-108">To get the most comprehensive data possible, ensure that you have the correct settings in the corresponding data sources.</span></span>

## <a name="advanced-security-auditing-on-windows-devices"></a><span data-ttu-id="cfed2-109">Audit de sécurité avancé sur les appareils Windows</span><span class="sxs-lookup"><span data-stu-id="cfed2-109">Advanced security auditing on Windows devices</span></span>
<span data-ttu-id="cfed2-110">Activez ces paramètres d’audit avancés pour vous assurer que vous obtenez des données sur les activités de vos appareils, notamment la gestion des comptes locaux, la gestion des groupes de sécurité locaux et la création de services.</span><span class="sxs-lookup"><span data-stu-id="cfed2-110">Turn on these advanced auditing settings to ensure you get data about activities on your devices, including local account management, local security group management, and service creation.</span></span>

| <span data-ttu-id="cfed2-111">Data</span><span class="sxs-lookup"><span data-stu-id="cfed2-111">Data</span></span> | <span data-ttu-id="cfed2-112">Description</span><span class="sxs-lookup"><span data-stu-id="cfed2-112">Description</span></span> | <span data-ttu-id="cfed2-113">Table de schéma</span><span class="sxs-lookup"><span data-stu-id="cfed2-113">Schema table</span></span> | <span data-ttu-id="cfed2-114">Procédure de configuration</span><span class="sxs-lookup"><span data-stu-id="cfed2-114">How to configure</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="cfed2-115">Gestion des comptes</span><span class="sxs-lookup"><span data-stu-id="cfed2-115">Account management</span></span> | <span data-ttu-id="cfed2-116">Événements capturés sous la forme de différentes `ActionType` valeurs indiquant la création, la suppression et d’autres activités liées au compte local</span><span class="sxs-lookup"><span data-stu-id="cfed2-116">Events captured as various `ActionType` values indicating local account creation, deletion, and other account-related activities</span></span> | [<span data-ttu-id="cfed2-117">DeviceEvents</span><span class="sxs-lookup"><span data-stu-id="cfed2-117">DeviceEvents</span></span>](advanced-hunting-deviceevents-table.md) | <span data-ttu-id="cfed2-118">-Déployer une stratégie d’audit de sécurité avancée : [audit User Account Management](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-user-account-management)</span><span class="sxs-lookup"><span data-stu-id="cfed2-118">- Deploy an advanced security audit policy: [Audit User Account Management](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-user-account-management)</span></span><br> <span data-ttu-id="cfed2-119">- [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)</span><span class="sxs-lookup"><span data-stu-id="cfed2-119">- [Learn about advanced security audit policies](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)</span></span> |
| <span data-ttu-id="cfed2-120">Gestion des groupes de sécurité</span><span class="sxs-lookup"><span data-stu-id="cfed2-120">Security group management</span></span> | <span data-ttu-id="cfed2-121">Événements capturés sous la forme de différentes `ActionType` valeurs indiquant la création du groupe de sécurité local et d’autres activités de gestion des groupes locaux</span><span class="sxs-lookup"><span data-stu-id="cfed2-121">Events captured as various `ActionType` values indicating local security group creation and other local group management activities</span></span> | [<span data-ttu-id="cfed2-122">DeviceEvents</span><span class="sxs-lookup"><span data-stu-id="cfed2-122">DeviceEvents</span></span>](advanced-hunting-deviceevents-table.md) | <span data-ttu-id="cfed2-123">-Déployer une stratégie d’audit de sécurité avancée : [gestion des groupes de sécurité d’audit](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-group-management)</span><span class="sxs-lookup"><span data-stu-id="cfed2-123">- Deploy an advanced security audit policy: [Audit Security Group Management](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-group-management)</span></span><br> <span data-ttu-id="cfed2-124">- [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)</span><span class="sxs-lookup"><span data-stu-id="cfed2-124">- [Learn about advanced security audit policies](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)</span></span> |
| <span data-ttu-id="cfed2-125">Installation de service</span><span class="sxs-lookup"><span data-stu-id="cfed2-125">Service installation</span></span> | <span data-ttu-id="cfed2-126">Événements capturés avec la `ActionType` valeur `ServiceInstalled` , indiquant qu’un service a été créé</span><span class="sxs-lookup"><span data-stu-id="cfed2-126">Events captured with the `ActionType` value `ServiceInstalled`, indicating that a service has been created</span></span> | [<span data-ttu-id="cfed2-127">DeviceEvents</span><span class="sxs-lookup"><span data-stu-id="cfed2-127">DeviceEvents</span></span>](advanced-hunting-deviceevents-table.md) | <span data-ttu-id="cfed2-128">-Déployer une stratégie d’audit de sécurité avancée : [audit Security System extension](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-system-extension)</span><span class="sxs-lookup"><span data-stu-id="cfed2-128">- Deploy an advanced security audit policy: [Audit Security System Extension](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-system-extension)</span></span><br> <span data-ttu-id="cfed2-129">- [En savoir plus sur les stratégies d’audit de sécurité avancées](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)</span><span class="sxs-lookup"><span data-stu-id="cfed2-129">- [Learn about advanced security audit policies](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)</span></span> |

## <a name="azure-atp-sensor-on-the-domain-controller"></a><span data-ttu-id="cfed2-130">Capteur DAV Azure sur le contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="cfed2-130">Azure ATP sensor on the domain controller</span></span>
<span data-ttu-id="cfed2-131">Si vous exécutez Active Directory sur site, vous devez installer le capteur DAV Azure sur le contrôleur de domaine pour obtenir des données pour Azure ATP.</span><span class="sxs-lookup"><span data-stu-id="cfed2-131">If you're running Active Directory on premises, you need to install the Azure ATP sensor on the domain controller to get data for Azure ATP.</span></span> <span data-ttu-id="cfed2-132">Une fois installée et correctement configurée, ces données sont également intégrées dans Azure ATP et fournissent une image plus holistique des informations d’identité et des événements de votre réseau.</span><span class="sxs-lookup"><span data-stu-id="cfed2-132">When installed and properly configured, this data also feeds into advanced hunting through Azure ATP and provides a more holistic picture of identity information and events in your network.</span></span> <span data-ttu-id="cfed2-133">Ces données améliorent également la capacité d’Azure ATP à générer des alertes pertinentes qui sont également couvertes par la chasse avancée.</span><span class="sxs-lookup"><span data-stu-id="cfed2-133">This data also enhances the ability of Azure ATP to generate relevant alerts that are also covered by advanced hunting.</span></span> 

| <span data-ttu-id="cfed2-134">Data</span><span class="sxs-lookup"><span data-stu-id="cfed2-134">Data</span></span> | <span data-ttu-id="cfed2-135">Description</span><span class="sxs-lookup"><span data-stu-id="cfed2-135">Description</span></span> | <span data-ttu-id="cfed2-136">Table de schéma</span><span class="sxs-lookup"><span data-stu-id="cfed2-136">Schema table</span></span> | <span data-ttu-id="cfed2-137">Procédure de configuration</span><span class="sxs-lookup"><span data-stu-id="cfed2-137">How to configure</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="cfed2-138">Contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="cfed2-138">Domain controller</span></span> | <span data-ttu-id="cfed2-139">Données provenant d’Active Directory en local envoyées à Azure ATP, enrichiant les informations d’identité, telles que les détails du compte, l’activité d’ouverture de session et les requêtes Active Directory</span><span class="sxs-lookup"><span data-stu-id="cfed2-139">Data from on-premises Active Directory sent to Azure ATP, enriching identity-related information, such as account details, logon activity, and Active Directory queries</span></span> | <span data-ttu-id="cfed2-140">Plusieurs tables, y compris [IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)et [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)</span><span class="sxs-lookup"><span data-stu-id="cfed2-140">Multiple tables, including [IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md), and [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)</span></span>  | [<span data-ttu-id="cfed2-141">Installer le capteur ATP Azure</span><span class="sxs-lookup"><span data-stu-id="cfed2-141">Install the Azure ATP sensor</span></span>](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step4)|

## <a name="related-topics"></a><span data-ttu-id="cfed2-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfed2-142">Related topics</span></span>
- [<span data-ttu-id="cfed2-143">Vue d’ensemble du repérage avancé</span><span class="sxs-lookup"><span data-stu-id="cfed2-143">Advanced hunting overview</span></span>](advanced-hunting-overview.md)
- [<span data-ttu-id="cfed2-144">Comprendre le schéma</span><span class="sxs-lookup"><span data-stu-id="cfed2-144">Understand the schema</span></span>](advanced-hunting-schema-tables.md)
---
title: Table IdentityDirectoryEvents dans le schéma de chasse avancé
description: En savoir plus sur le contrôleur de domaine et les événements Active Directory dans la table IdentityDirectoryEvents du schéma de chasse avancé
keywords: recherche avancée, recherche de menace, recherche de menace informatique, protection de Microsoft contre les menaces, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, IdentityDirectoryEvents, contrôleur de domaine, Active Directory, Azure ATP, identités
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
ms.openlocfilehash: 1a65a8e78dfa09bc0a417669a1efd35320e261da
ms.sourcegitcommit: 445b249a6f0420b32e49742fd7744006c7090b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "46798782"
---
# <a name="identitydirectoryevents"></a><span data-ttu-id="42db6-104">IdentityDirectoryEvents</span><span class="sxs-lookup"><span data-stu-id="42db6-104">IdentityDirectoryEvents</span></span>

<span data-ttu-id="42db6-105">**S’applique à :**</span><span class="sxs-lookup"><span data-stu-id="42db6-105">**Applies to:**</span></span>
- <span data-ttu-id="42db6-106">Protection Microsoft contre les menaces</span><span class="sxs-lookup"><span data-stu-id="42db6-106">Microsoft Threat Protection</span></span>

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

<span data-ttu-id="42db6-107">Le `IdentityDirectoryEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des événements impliquant un contrôleur de domaine local exécutant Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="42db6-107">The `IdentityDirectoryEvents` table in the [advanced hunting](advanced-hunting-overview.md) schema contains events involving an on-premises domain controller running Active Directory (AD).</span></span> <span data-ttu-id="42db6-108">Ce tableau capture différents événements liés à l’identité, tels que les modifications de mot de passe, l’expiration du mot de passe et les modifications de nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="42db6-108">This table captures various identity-related events, like password changes, password expiration, and user principal name (UPN) changes.</span></span> <span data-ttu-id="42db6-109">Il capture également les événements système sur le contrôleur de domaine, comme la planification des tâches et l’activité PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42db6-109">It also captures system events on the domain controller, like scheduling of tasks and PowerShell activity.</span></span> <span data-ttu-id="42db6-110">Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.</span><span class="sxs-lookup"><span data-stu-id="42db6-110">Use this reference to construct queries that return information from this table.</span></span>

>[!TIP]
> <span data-ttu-id="42db6-111">Pour plus d’informations sur les types d’événements ( `ActionType` valeurs) pris en charge par un tableau, utilisez la [référence de schéma intégrée](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) disponible dans le centre de sécurité.</span><span class="sxs-lookup"><span data-stu-id="42db6-111">For detailed information about the events types (`ActionType` values) supported by a table, use the [built-in schema reference](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) available in the security center.</span></span>

<span data-ttu-id="42db6-112">Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).</span><span class="sxs-lookup"><span data-stu-id="42db6-112">For information on other tables in the advanced hunting schema, [see the advanced hunting reference](advanced-hunting-schema-tables.md).</span></span>

| <span data-ttu-id="42db6-113">Nom de colonne</span><span class="sxs-lookup"><span data-stu-id="42db6-113">Column name</span></span> | <span data-ttu-id="42db6-114">Type de données</span><span class="sxs-lookup"><span data-stu-id="42db6-114">Data type</span></span> | <span data-ttu-id="42db6-115">Description</span><span class="sxs-lookup"><span data-stu-id="42db6-115">Description</span></span> |
|-------------|-----------|-------------|
| `Timestamp` | <span data-ttu-id="42db6-116">DateHeure</span><span class="sxs-lookup"><span data-stu-id="42db6-116">datetime</span></span> | <span data-ttu-id="42db6-117">Date et heure d’enregistrement de l’événement</span><span class="sxs-lookup"><span data-stu-id="42db6-117">Date and time when the event was recorded</span></span> |
| `ActionType` | <span data-ttu-id="42db6-118">string</span><span class="sxs-lookup"><span data-stu-id="42db6-118">string</span></span> | <span data-ttu-id="42db6-119">Type d’activité qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="42db6-119">Type of activity that triggered the event.</span></span> <span data-ttu-id="42db6-120">Pour plus d’informations, consultez la [référence de schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) .</span><span class="sxs-lookup"><span data-stu-id="42db6-120">See the [in-portal schema reference](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) for details</span></span> |
| `Application` | <span data-ttu-id="42db6-121">string</span><span class="sxs-lookup"><span data-stu-id="42db6-121">string</span></span> | <span data-ttu-id="42db6-122">Application qui a effectué l’action enregistrée</span><span class="sxs-lookup"><span data-stu-id="42db6-122">Application that performed the recorded action</span></span> |
| `TargetAccountUpn` | <span data-ttu-id="42db6-123">string</span><span class="sxs-lookup"><span data-stu-id="42db6-123">string</span></span> | <span data-ttu-id="42db6-124">Nom d’utilisateur principal (UPN) du compte auquel l’action enregistrée a été appliquée</span><span class="sxs-lookup"><span data-stu-id="42db6-124">User principal name (UPN) of the account that the recorded action was applied to</span></span> |
| `TargetAccountDisplayName` | <span data-ttu-id="42db6-125">string</span><span class="sxs-lookup"><span data-stu-id="42db6-125">string</span></span> | <span data-ttu-id="42db6-126">Nom d’affichage du compte auquel l’action enregistrée a été appliquée</span><span class="sxs-lookup"><span data-stu-id="42db6-126">Display name of the account that the recorded action was applied to</span></span> |
| `TargetDeviceName` | <span data-ttu-id="42db6-127">string</span><span class="sxs-lookup"><span data-stu-id="42db6-127">string</span></span> | <span data-ttu-id="42db6-128">Nom de domaine complet (FQDN) de l’appareil sur lequel l’action enregistrée a été appliquée.</span><span class="sxs-lookup"><span data-stu-id="42db6-128">Fully qualified domain name (FQDN) of the device that the recorded action was applied to</span></span> |
| `DestinationDeviceName` | <span data-ttu-id="42db6-129">string</span><span class="sxs-lookup"><span data-stu-id="42db6-129">string</span></span> | <span data-ttu-id="42db6-130">Nom de l’appareil exécutant l’application serveur qui a traité l’action enregistrée.</span><span class="sxs-lookup"><span data-stu-id="42db6-130">Name of the device running the server application that processed the recorded action</span></span> |
| `DestinationIPAddress` | <span data-ttu-id="42db6-131">string</span><span class="sxs-lookup"><span data-stu-id="42db6-131">string</span></span> | <span data-ttu-id="42db6-132">Adresse IP de l’appareil exécutant l’application serveur qui a traité l’action enregistrée</span><span class="sxs-lookup"><span data-stu-id="42db6-132">IP address of the device running the server application that processed the recorded action</span></span> |
| `DestinationPort` | <span data-ttu-id="42db6-133">string</span><span class="sxs-lookup"><span data-stu-id="42db6-133">string</span></span> | <span data-ttu-id="42db6-134">Port de destination de l’activité</span><span class="sxs-lookup"><span data-stu-id="42db6-134">Destination port of the activity</span></span> |
| `Protocol` | <span data-ttu-id="42db6-135">string</span><span class="sxs-lookup"><span data-stu-id="42db6-135">string</span></span> | <span data-ttu-id="42db6-136">Protocole utilisé pendant la communication</span><span class="sxs-lookup"><span data-stu-id="42db6-136">Protocol used during the communication</span></span> |
| `AccountName` | <span data-ttu-id="42db6-137">string</span><span class="sxs-lookup"><span data-stu-id="42db6-137">string</span></span> | <span data-ttu-id="42db6-138">Nom d’utilisateur du compte</span><span class="sxs-lookup"><span data-stu-id="42db6-138">User name of the account</span></span> |
| `AccountDomain` | <span data-ttu-id="42db6-139">string</span><span class="sxs-lookup"><span data-stu-id="42db6-139">string</span></span> | <span data-ttu-id="42db6-140">Domaine du compte</span><span class="sxs-lookup"><span data-stu-id="42db6-140">Domain of the account</span></span> |
| `AccountUpn` | <span data-ttu-id="42db6-141">string</span><span class="sxs-lookup"><span data-stu-id="42db6-141">string</span></span> | <span data-ttu-id="42db6-142">Nom d’utilisateur principal (UPN) du compte</span><span class="sxs-lookup"><span data-stu-id="42db6-142">User principal name (UPN) of the account</span></span> |
| `AccountSid` | <span data-ttu-id="42db6-143">string</span><span class="sxs-lookup"><span data-stu-id="42db6-143">string</span></span> | <span data-ttu-id="42db6-144">Identificateur de sécurité (SID) du compte</span><span class="sxs-lookup"><span data-stu-id="42db6-144">Security Identifier (SID) of the account</span></span> |
| `AccountObjectId` | <span data-ttu-id="42db6-145">string</span><span class="sxs-lookup"><span data-stu-id="42db6-145">string</span></span> | <span data-ttu-id="42db6-146">Identificateur unique du compte dans Azure AD</span><span class="sxs-lookup"><span data-stu-id="42db6-146">Unique identifier for the account in Azure AD</span></span> |
| `AccountDisplayName` | <span data-ttu-id="42db6-147">string</span><span class="sxs-lookup"><span data-stu-id="42db6-147">string</span></span> | <span data-ttu-id="42db6-148">Nom de l’utilisateur du compte affiché dans le carnet d’adresses.</span><span class="sxs-lookup"><span data-stu-id="42db6-148">Name of the account user displayed in the address book.</span></span> <span data-ttu-id="42db6-149">Il s’agit généralement d’une combinaison d’un nom donné, d’une initiation au milieu et d’un nom de famille ou nom.</span><span class="sxs-lookup"><span data-stu-id="42db6-149">Typically a combination of a given or first name, a middle initiation, and a last name or surname.</span></span> |
| `DeviceName` | <span data-ttu-id="42db6-150">string</span><span class="sxs-lookup"><span data-stu-id="42db6-150">string</span></span> | <span data-ttu-id="42db6-151">Nom de domaine complet (FQDN) du périphérique</span><span class="sxs-lookup"><span data-stu-id="42db6-151">Fully qualified domain name (FQDN) of the device</span></span> |
| `IPAddress` | <span data-ttu-id="42db6-152">string</span><span class="sxs-lookup"><span data-stu-id="42db6-152">string</span></span> | <span data-ttu-id="42db6-153">Adresse IP attribuée au périphérique lors de la communication</span><span class="sxs-lookup"><span data-stu-id="42db6-153">IP address assigned to the device during communication</span></span> |
| `Port` | <span data-ttu-id="42db6-154">string</span><span class="sxs-lookup"><span data-stu-id="42db6-154">string</span></span> | <span data-ttu-id="42db6-155">Port TCP utilisé pendant la communication</span><span class="sxs-lookup"><span data-stu-id="42db6-155">TCP port used during communication</span></span> |
| `Location` | <span data-ttu-id="42db6-156">string</span><span class="sxs-lookup"><span data-stu-id="42db6-156">string</span></span> | <span data-ttu-id="42db6-157">Ville, pays ou autre emplacement géographique associé à l’événement</span><span class="sxs-lookup"><span data-stu-id="42db6-157">City, country, or other geographic location associated with the event</span></span> |
| `ISP` | <span data-ttu-id="42db6-158">string</span><span class="sxs-lookup"><span data-stu-id="42db6-158">string</span></span> | <span data-ttu-id="42db6-159">Fournisseur de services Internet associé à l’adresse IP</span><span class="sxs-lookup"><span data-stu-id="42db6-159">Internet service provider associated with the IP address</span></span> |
| `ReportId` | <span data-ttu-id="42db6-160">long</span><span class="sxs-lookup"><span data-stu-id="42db6-160">long</span></span> | <span data-ttu-id="42db6-161">Identificateur unique de l’événement</span><span class="sxs-lookup"><span data-stu-id="42db6-161">Unique identifier for the event</span></span> |
| `AdditionalFields` | <span data-ttu-id="42db6-162">string</span><span class="sxs-lookup"><span data-stu-id="42db6-162">string</span></span> | <span data-ttu-id="42db6-163">Informations supplémentaires sur l’entité ou l’événement</span><span class="sxs-lookup"><span data-stu-id="42db6-163">Additional information about the entity or event</span></span> |

## <a name="related-topics"></a><span data-ttu-id="42db6-164">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="42db6-164">Related topics</span></span>
- [<span data-ttu-id="42db6-165">Vue d’ensemble du repérage avancé</span><span class="sxs-lookup"><span data-stu-id="42db6-165">Advanced hunting overview</span></span>](advanced-hunting-overview.md)
- [<span data-ttu-id="42db6-166">Apprendre le langage de requête</span><span class="sxs-lookup"><span data-stu-id="42db6-166">Learn the query language</span></span>](advanced-hunting-query-language.md)
- [<span data-ttu-id="42db6-167">Utiliser des requêtes partagées</span><span class="sxs-lookup"><span data-stu-id="42db6-167">Use shared queries</span></span>](advanced-hunting-shared-queries.md)
- [<span data-ttu-id="42db6-168">Rechercher sur les appareils, les emails, les applications et les identités</span><span class="sxs-lookup"><span data-stu-id="42db6-168">Hunt across devices, emails, apps, and identities</span></span>](advanced-hunting-query-emails-devices.md)
- [<span data-ttu-id="42db6-169">Comprendre le schéma</span><span class="sxs-lookup"><span data-stu-id="42db6-169">Understand the schema</span></span>](advanced-hunting-schema-tables.md)
- [<span data-ttu-id="42db6-170">Appliquer les meilleures pratiques de requête</span><span class="sxs-lookup"><span data-stu-id="42db6-170">Apply query best practices</span></span>](advanced-hunting-best-practices.md)
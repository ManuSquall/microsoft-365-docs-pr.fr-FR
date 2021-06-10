---
title: Exporter l’évaluation des vulnérabilités logicielles par appareil
description: La réponse api est par appareil et contient les logiciels vulnérables installés sur vos appareils exposés, ainsi que les vulnérabilités connues dans ces produits logiciels. Cette table inclut également des informations sur le système d’exploitation, les ID CVE et sur la gravité des vulnérabilités.
keywords: api, api, évaluation d’exportation, évaluation par appareil, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités d’appareils, rapport de vulnérabilité d’appareil, évaluation de la configuration sécurisée, rapport de configuration sécurisé, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 849d1ab2bbc3b8f6d883d6041adda5fe4577741d
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "52789361"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a><span data-ttu-id="0b4d3-105">Exporter l’évaluation des vulnérabilités logicielles par appareil</span><span class="sxs-lookup"><span data-stu-id="0b4d3-105">Export software vulnerabilities assessment per device</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="0b4d3-106">**S’applique à :**</span><span class="sxs-lookup"><span data-stu-id="0b4d3-106">**Applies to:**</span></span>

- [<span data-ttu-id="0b4d3-107">Microsoft Defender pour point de terminaison</span><span class="sxs-lookup"><span data-stu-id="0b4d3-107">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [<span data-ttu-id="0b4d3-108">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="0b4d3-108">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="0b4d3-109">Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ?</span><span class="sxs-lookup"><span data-stu-id="0b4d3-109">Want to experience Microsoft Defender for Endpoint?</span></span> [<span data-ttu-id="0b4d3-110">Inscrivez-vous à un essai gratuit.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-110">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
<span data-ttu-id="0b4d3-111">Renvoie toutes les vulnérabilités logicielles connues et leurs détails pour tous les appareils, par appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-111">Returns all known software vulnerabilities and their details for all devices, on a per-device basis.</span></span>

<span data-ttu-id="0b4d3-112">Il existe différents appels d’API pour obtenir différents types de données.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-112">There are different API calls to get different types of data.</span></span> <span data-ttu-id="0b4d3-113">Étant donné que la quantité de données peut être importante, il existe deux façons de les récupérer :</span><span class="sxs-lookup"><span data-stu-id="0b4d3-113">Because the amount of data can be large, there are two ways it can be retrieved:</span></span>

- <span data-ttu-id="0b4d3-114">[Exporter l’évaluation des vulnérabilités logicielles OData](#1-export-software-vulnerabilities-assessment-odata)  L’API tire toutes les données de votre organisation en tant que réponses Json, en suivant le protocole OData.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-114">[Export software vulnerabilities assessment OData](#1-export-software-vulnerabilities-assessment-odata)  The API pulls all data in your organization as Json responses, following the OData protocol.</span></span> <span data-ttu-id="0b4d3-115">Cette méthode est la meilleure pour _les petites organisations avec moins de 100 Ko d’appareils._</span><span class="sxs-lookup"><span data-stu-id="0b4d3-115">This method is best for _small organizations with less than 100-K devices_.</span></span> <span data-ttu-id="0b4d3-116">La réponse est paginée, afin que vous pouvez utiliser le champ odata.nextLink de la réponse \@ pour récupérer les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-116">The response is paginated, so you can use the \@odata.nextLink field from the response to fetch the next results.</span></span>

- <span data-ttu-id="0b4d3-117">[Exporter l’évaluation des vulnérabilités logicielles via des fichiers](#2-export-software-vulnerabilities-assessment-via-files) Cette solution d’API permet d’tirer plus rapidement et de manière plus fiable des données plus volumineuses.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-117">[Export software vulnerabilities assessment via files](#2-export-software-vulnerabilities-assessment-via-files) This API solution enables pulling larger amounts of data faster and more reliably.</span></span> <span data-ttu-id="0b4d3-118">Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 K appareils.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-118">Therefore, it is recommended for large organizations, with more than 100-K devices.</span></span> <span data-ttu-id="0b4d3-119">Cette API tire toutes les données de votre organisation en tant que fichiers de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-119">This API pulls all data in your organization as download files.</span></span> <span data-ttu-id="0b4d3-120">La réponse contient des URL pour télécharger toutes les données à partir de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-120">The response contains URLs to download all the data from Azure Storage.</span></span> <span data-ttu-id="0b4d3-121">Cette API vous permet de télécharger toutes vos données à partir stockage Azure comme suit :</span><span class="sxs-lookup"><span data-stu-id="0b4d3-121">This API enables you to download all your data from Azure Storage as follows:</span></span>

  - <span data-ttu-id="0b4d3-122">Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-122">Call the API to get a list of download URLs with all your organization data.</span></span>

  - <span data-ttu-id="0b4d3-123">Téléchargez tous les fichiers à l’aide des URL de téléchargement et traiter les données comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-123">Download all the files using the download URLs and process the data as you like.</span></span>

<span data-ttu-id="0b4d3-124">Les données collectées (à l’aide _d’OData_ ou _via_ des fichiers) sont l’instantané actuel de l’état actuel et ne contiennent pas de données historiques.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-124">Data that is collected (using either _OData_ or _via files_) is the current snapshot of the current state, and does not contain historic data.</span></span> <span data-ttu-id="0b4d3-125">Pour collecter des données historiques, les clients doivent les enregistrer dans leurs propres stockages de données.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-125">In order to collect historic data, customers must save the data in their own data storages.</span></span>

> [!Note]
>
> <span data-ttu-id="0b4d3-126">Sauf indication contraire, toutes les méthodes \*\*\*\* d’évaluation d’exportation répertoriées sont l’exportation complète et par appareil **_(également_** appelé **_par appareil)._**</span><span class="sxs-lookup"><span data-stu-id="0b4d3-126">Unless indicated otherwise, all export assessment methods listed are **_full export_** and **_by device_** (also referred to as **_per device_**).</span></span>

## <a name="1-export-software-vulnerabilities-assessment-odata"></a><span data-ttu-id="0b4d3-127">1. Exporter l’évaluation des vulnérabilités logicielles (OData)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-127">1. Export software vulnerabilities assessment (OData)</span></span>

### <a name="11-api-method-description"></a><span data-ttu-id="0b4d3-128">1.1 Description de la méthode API</span><span class="sxs-lookup"><span data-stu-id="0b4d3-128">1.1 API method description</span></span>

<span data-ttu-id="0b4d3-129">Cette réponse API contient toutes les données des logiciels installés par appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-129">This API response contains all the data of installed software per device.</span></span> <span data-ttu-id="0b4d3-130">Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-130">Returns a table with an entry for every unique combination of DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.</span></span>

#### <a name="limitations"></a><span data-ttu-id="0b4d3-131">Limites</span><span class="sxs-lookup"><span data-stu-id="0b4d3-131">Limitations</span></span>

>- <span data-ttu-id="0b4d3-132">La taille maximale de page est de 200 000.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-132">Maximum page size is 200,000.</span></span>
>
>- <span data-ttu-id="0b4d3-133">Les limites de taux pour cette API sont de 30 appels par minute et de 1 000 appels par heure.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-133">Rate limitations for this API are 30 calls per minute and 1000 calls per hour.</span></span>

### <a name="12-permissions"></a><span data-ttu-id="0b4d3-134">1.2 Autorisations</span><span class="sxs-lookup"><span data-stu-id="0b4d3-134">1.2 Permissions</span></span>

<span data-ttu-id="0b4d3-135">L’une des autorisations suivantes est nécessaire pour appeler cette API.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-135">One of the following permissions is required to call this API.</span></span> <span data-ttu-id="0b4d3-136">Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-136">To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs for details.](apis-intro.md)</span></span>

<span data-ttu-id="0b4d3-137">Type d’autorisation</span><span class="sxs-lookup"><span data-stu-id="0b4d3-137">Permission type</span></span> | <span data-ttu-id="0b4d3-138">Autorisation</span><span class="sxs-lookup"><span data-stu-id="0b4d3-138">Permission</span></span> | <span data-ttu-id="0b4d3-139">Nom d’affichage de l’autorisation</span><span class="sxs-lookup"><span data-stu-id="0b4d3-139">Permission display name</span></span>
---|---|---
<span data-ttu-id="0b4d3-140">Application</span><span class="sxs-lookup"><span data-stu-id="0b4d3-140">Application</span></span> | <span data-ttu-id="0b4d3-141">Vulnerability.Read.All</span><span class="sxs-lookup"><span data-stu-id="0b4d3-141">Vulnerability.Read.All</span></span> | <span data-ttu-id="0b4d3-142">\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'</span><span class="sxs-lookup"><span data-stu-id="0b4d3-142">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>
<span data-ttu-id="0b4d3-143">Déléguée (compte professionnel ou scolaire)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-143">Delegated (work or school account)</span></span> | <span data-ttu-id="0b4d3-144">Vulnerability.Read</span><span class="sxs-lookup"><span data-stu-id="0b4d3-144">Vulnerability.Read</span></span> | <span data-ttu-id="0b4d3-145">\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'</span><span class="sxs-lookup"><span data-stu-id="0b4d3-145">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>

### <a name="13-url"></a><span data-ttu-id="0b4d3-146">1.3 URL</span><span class="sxs-lookup"><span data-stu-id="0b4d3-146">1.3 URL</span></span>

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a><span data-ttu-id="0b4d3-147">1.4 Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b4d3-147">1.4 Parameters</span></span>

- <span data-ttu-id="0b4d3-148">pageSize (valeur par défaut = 50 000) : nombre de résultats en réponse</span><span class="sxs-lookup"><span data-stu-id="0b4d3-148">pageSize (default = 50,000) – number of results in response</span></span>
- <span data-ttu-id="0b4d3-149">$top : nombre de résultats à renvoyer (ne retourne pas @odata.nextLink et, par conséquent, ne tire pas toutes les données)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-149">$top – number of results to return (doesn’t return @odata.nextLink and therefore doesn’t pull all the data)</span></span>

### <a name="15-properties"></a><span data-ttu-id="0b4d3-150">1.5 Propriétés</span><span class="sxs-lookup"><span data-stu-id="0b4d3-150">1.5 Properties</span></span>
>
>[!Note]
>
>- <span data-ttu-id="0b4d3-151">Chaque enregistrement représente environ 1 To de données.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-151">Each record is approximately 1KB of data.</span></span> <span data-ttu-id="0b4d3-152">Vous devez prendre cela en compte lors du choix du paramètre pageSize approprié pour vous.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-152">You should take this into account when choosing the correct pageSize parameter for you.</span></span>
>
>- <span data-ttu-id="0b4d3-153">Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-153">Some additional columns might be returned in the response.</span></span> <span data-ttu-id="0b4d3-154">Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-154">These columns are temporary and might be removed, please use only the documented columns.</span></span>
>
>- <span data-ttu-id="0b4d3-155">Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique, par ID de propriété.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-155">The properties defined in the following table are listed alphabetically, by property ID.</span></span>  <span data-ttu-id="0b4d3-156">Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement renvoyée dans le même ordre que celui répertorié dans ce tableau.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-156">When running this API, the resulting output will not necessarily be returned in the same order listed in this table.</span></span>
>

<span data-ttu-id="0b4d3-157">Propriété (ID)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-157">Property (ID)</span></span> | <span data-ttu-id="0b4d3-158">Type de données</span><span class="sxs-lookup"><span data-stu-id="0b4d3-158">Data type</span></span> | <span data-ttu-id="0b4d3-159">Description</span><span class="sxs-lookup"><span data-stu-id="0b4d3-159">Description</span></span> | <span data-ttu-id="0b4d3-160">Exemple de valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0b4d3-160">Example of a returned value</span></span>
:---|:---|:---|:---
<span data-ttu-id="0b4d3-161">CveId</span><span class="sxs-lookup"><span data-stu-id="0b4d3-161">CveId</span></span> | <span data-ttu-id="0b4d3-162">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-162">string</span></span> | <span data-ttu-id="0b4d3-163">Identificateur unique affecté à la vulnérabilité de sécurité sous le système CVE (Common Vulnerabilities and Exposures).</span><span class="sxs-lookup"><span data-stu-id="0b4d3-163">Unique identifier assigned to the security vulnerability under the Common Vulnerabilities and Exposures (CVE) system.</span></span> | <span data-ttu-id="0b4d3-164">CVE-2020-15992</span><span class="sxs-lookup"><span data-stu-id="0b4d3-164">CVE-2020-15992</span></span>
<span data-ttu-id="0b4d3-165">CvssScore</span><span class="sxs-lookup"><span data-stu-id="0b4d3-165">CvssScore</span></span> | <span data-ttu-id="0b4d3-166">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-166">string</span></span> | <span data-ttu-id="0b4d3-167">Score CVSS de la CVE.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-167">The CVSS score of the CVE.</span></span> | <span data-ttu-id="0b4d3-168">6.2</span><span class="sxs-lookup"><span data-stu-id="0b4d3-168">6.2</span></span>
<span data-ttu-id="0b4d3-169">DeviceId</span><span class="sxs-lookup"><span data-stu-id="0b4d3-169">DeviceId</span></span> | <span data-ttu-id="0b4d3-170">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-170">string</span></span> | <span data-ttu-id="0b4d3-171">Identificateur unique de l’appareil dans le service.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-171">Unique identifier for the device in the service.</span></span> | <span data-ttu-id="0b4d3-172">9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1</span><span class="sxs-lookup"><span data-stu-id="0b4d3-172">9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1</span></span>
<span data-ttu-id="0b4d3-173">DeviceName</span><span class="sxs-lookup"><span data-stu-id="0b4d3-173">DeviceName</span></span> | <span data-ttu-id="0b4d3-174">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-174">string</span></span> | <span data-ttu-id="0b4d3-175">Nom de domaine complet (FQDN) de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-175">Fully qualified domain name (FQDN) of the device.</span></span> | <span data-ttu-id="0b4d3-176">johnlaptop.europe.contoso.com</span><span class="sxs-lookup"><span data-stu-id="0b4d3-176">johnlaptop.europe.contoso.com</span></span>
<span data-ttu-id="0b4d3-177">DiskPaths</span><span class="sxs-lookup"><span data-stu-id="0b4d3-177">DiskPaths</span></span>  | <span data-ttu-id="0b4d3-178">Chaîne de \[ tableau\]</span><span class="sxs-lookup"><span data-stu-id="0b4d3-178">Array\[string\]</span></span> | <span data-ttu-id="0b4d3-179">Preuve disque que le produit est installé sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-179">Disk evidence that the product is installed on the device.</span></span> | <span data-ttu-id="0b4d3-180">[ « C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe » ]</span><span class="sxs-lookup"><span data-stu-id="0b4d3-180">[ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]</span></span>
<span data-ttu-id="0b4d3-181">ExploitabilityLevel</span><span class="sxs-lookup"><span data-stu-id="0b4d3-181">ExploitabilityLevel</span></span> | <span data-ttu-id="0b4d3-182">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-182">string</span></span> | <span data-ttu-id="0b4d3-183">Le niveau d’exploitabilité de cette vulnérabilité (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-183">The exploitability level of this vulnerability (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)</span></span> | <span data-ttu-id="0b4d3-184">ExploitIsInKit</span><span class="sxs-lookup"><span data-stu-id="0b4d3-184">ExploitIsInKit</span></span>
<span data-ttu-id="0b4d3-185">FirstSeenTimestamp</span><span class="sxs-lookup"><span data-stu-id="0b4d3-185">FirstSeenTimestamp</span></span> | <span data-ttu-id="0b4d3-186">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-186">string</span></span> | <span data-ttu-id="0b4d3-187">Première fois que la CVE de ce produit a été vue sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-187">First time the CVE of this product was seen on the device.</span></span> | <span data-ttu-id="0b4d3-188">2020-11-03 10:13:34.8476880</span><span class="sxs-lookup"><span data-stu-id="0b4d3-188">2020-11-03 10:13:34.8476880</span></span>
<span data-ttu-id="0b4d3-189">ID</span><span class="sxs-lookup"><span data-stu-id="0b4d3-189">Id</span></span> | <span data-ttu-id="0b4d3-190">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-190">string</span></span> | <span data-ttu-id="0b4d3-191">Identificateur unique de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-191">Unique identifier for the record.</span></span> | <span data-ttu-id="0b4d3-192">123ABG55_573AG&mnp!</span><span class="sxs-lookup"><span data-stu-id="0b4d3-192">123ABG55_573AG&mnp!</span></span>
<span data-ttu-id="0b4d3-193">LastSeenTimestamp</span><span class="sxs-lookup"><span data-stu-id="0b4d3-193">LastSeenTimestamp</span></span> | <span data-ttu-id="0b4d3-194">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-194">string</span></span> | <span data-ttu-id="0b4d3-195">Dernière fois que la CVE a été vue sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-195">Last time the CVE was seen on the device.</span></span> | <span data-ttu-id="0b4d3-196">2020-11-03 10:13:34.8476880</span><span class="sxs-lookup"><span data-stu-id="0b4d3-196">2020-11-03 10:13:34.8476880</span></span>
<span data-ttu-id="0b4d3-197">OSPlatform</span><span class="sxs-lookup"><span data-stu-id="0b4d3-197">OSPlatform</span></span> | <span data-ttu-id="0b4d3-198">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-198">string</span></span> | <span data-ttu-id="0b4d3-199">Plateforme du système d’exploitation en cours d’exécution sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-199">Platform of the operating system running on the device.</span></span> <span data-ttu-id="0b4d3-200">Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-200">This indicates specific operating systems, including variations within the same family, such as Windows 10 and Windows 7.</span></span> <span data-ttu-id="0b4d3-201">Pour plus d’informations, voir les systèmes d’exploitation et les plateformes pris en charge par tvm.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-201">See tvm supported operating systems and platforms for details.</span></span> | <span data-ttu-id="0b4d3-202">Windows 10</span><span class="sxs-lookup"><span data-stu-id="0b4d3-202">Windows10</span></span>
<span data-ttu-id="0b4d3-203">RbacGroupName</span><span class="sxs-lookup"><span data-stu-id="0b4d3-203">RbacGroupName</span></span>  | <span data-ttu-id="0b4d3-204">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-204">string</span></span> | <span data-ttu-id="0b4d3-205">Groupe de contrôle d’accès basé sur un rôle (RBAC).</span><span class="sxs-lookup"><span data-stu-id="0b4d3-205">The role-based access control (RBAC) group.</span></span> <span data-ttu-id="0b4d3-206">Si cet appareil n’est affecté à aucun groupe RBAC, la valeur sera « Unassigned ».</span><span class="sxs-lookup"><span data-stu-id="0b4d3-206">If this device is not assigned to any RBAC group, the value will be “Unassigned.”</span></span> <span data-ttu-id="0b4d3-207">Si l’organisation ne contient aucun groupe RBAC, la valeur sera « None ».</span><span class="sxs-lookup"><span data-stu-id="0b4d3-207">If the organization doesn’t contain any RBAC groups, the value will be “None.”</span></span> | <span data-ttu-id="0b4d3-208">Serveurs</span><span class="sxs-lookup"><span data-stu-id="0b4d3-208">Servers</span></span>
<span data-ttu-id="0b4d3-209">RecommendationReference</span><span class="sxs-lookup"><span data-stu-id="0b4d3-209">RecommendationReference</span></span> | <span data-ttu-id="0b4d3-210">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-210">string</span></span> | <span data-ttu-id="0b4d3-211">Référence à l’ID de recommandation associé à ce logiciel.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-211">A reference to the recommendation ID related to this software.</span></span> | <span data-ttu-id="0b4d3-212">va-_-microsoft-_-silverlight</span><span class="sxs-lookup"><span data-stu-id="0b4d3-212">va-_-microsoft-_-silverlight</span></span>
<span data-ttu-id="0b4d3-213">RecommendedSecurityUpdate (facultatif)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-213">RecommendedSecurityUpdate (optional)</span></span> | <span data-ttu-id="0b4d3-214">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-214">string</span></span> | <span data-ttu-id="0b4d3-215">Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-215">Name or description of the security update provided by the software vendor to address the vulnerability.</span></span> | <span data-ttu-id="0b4d3-216">Mises à jour de sécurité d’avril 2020</span><span class="sxs-lookup"><span data-stu-id="0b4d3-216">April 2020 Security Updates</span></span>
<span data-ttu-id="0b4d3-217">RecommendedSecurityUpdateId (facultatif)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-217">RecommendedSecurityUpdateId (optional)</span></span> | <span data-ttu-id="0b4d3-218">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-218">string</span></span> | <span data-ttu-id="0b4d3-219">Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou de conseils correspondants</span><span class="sxs-lookup"><span data-stu-id="0b4d3-219">Identifier of the applicable security updates or identifier for the corresponding guidance or knowledge base (KB) articles</span></span> | <span data-ttu-id="0b4d3-220">4550961</span><span class="sxs-lookup"><span data-stu-id="0b4d3-220">4550961</span></span>
<span data-ttu-id="0b4d3-221">RegistryPaths</span><span class="sxs-lookup"><span data-stu-id="0b4d3-221">RegistryPaths</span></span>  | <span data-ttu-id="0b4d3-222">Chaîne de \[ tableau\]</span><span class="sxs-lookup"><span data-stu-id="0b4d3-222">Array\[string\]</span></span> | <span data-ttu-id="0b4d3-223">Preuve dans le Registre que le produit est installé sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-223">Registry evidence that the product is installed in the device.</span></span> | <span data-ttu-id="0b4d3-224">[ « HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight » ]</span><span class="sxs-lookup"><span data-stu-id="0b4d3-224">[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]</span></span>
<span data-ttu-id="0b4d3-225">SoftwareName</span><span class="sxs-lookup"><span data-stu-id="0b4d3-225">SoftwareName</span></span> | <span data-ttu-id="0b4d3-226">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-226">string</span></span> | <span data-ttu-id="0b4d3-227">Nom du produit logiciel.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-227">Name of the software product.</span></span> | <span data-ttu-id="0b4d3-228">chrome</span><span class="sxs-lookup"><span data-stu-id="0b4d3-228">chrome</span></span>
<span data-ttu-id="0b4d3-229">SoftwareVendor</span><span class="sxs-lookup"><span data-stu-id="0b4d3-229">SoftwareVendor</span></span> | <span data-ttu-id="0b4d3-230">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-230">string</span></span> | <span data-ttu-id="0b4d3-231">Nom du fournisseur de logiciels.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-231">Name of the software vendor.</span></span> | <span data-ttu-id="0b4d3-232">google</span><span class="sxs-lookup"><span data-stu-id="0b4d3-232">google</span></span>
<span data-ttu-id="0b4d3-233">SoftwareVersion</span><span class="sxs-lookup"><span data-stu-id="0b4d3-233">SoftwareVersion</span></span> | <span data-ttu-id="0b4d3-234">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-234">string</span></span> | <span data-ttu-id="0b4d3-235">Numéro de version du produit logiciel.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-235">Version number of the software product.</span></span> | <span data-ttu-id="0b4d3-236">81.0.4044.138</span><span class="sxs-lookup"><span data-stu-id="0b4d3-236">81.0.4044.138</span></span>
<span data-ttu-id="0b4d3-237">VulnerabilitySeverityLevel</span><span class="sxs-lookup"><span data-stu-id="0b4d3-237">VulnerabilitySeverityLevel</span></span>  | <span data-ttu-id="0b4d3-238">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-238">string</span></span> | <span data-ttu-id="0b4d3-239">Niveau de gravité affecté à la vulnérabilité de sécurité en fonction du score CVSS et des facteurs dynamiques influencés par le paysage des menaces.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-239">Severity level assigned to the security vulnerability based on the CVSS score and dynamic factors influenced by the threat landscape.</span></span> | <span data-ttu-id="0b4d3-240">Moyenne</span><span class="sxs-lookup"><span data-stu-id="0b4d3-240">Medium</span></span>

### <a name="16-examples"></a><span data-ttu-id="0b4d3-241">1.6 Exemples</span><span class="sxs-lookup"><span data-stu-id="0b4d3-241">1.6 Examples</span></span>

#### <a name="161-request-example"></a><span data-ttu-id="0b4d3-242">1.6.1 Exemple de requête</span><span class="sxs-lookup"><span data-stu-id="0b4d3-242">1.6.1 Request example</span></span>

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a><span data-ttu-id="0b4d3-243">1.6.2 Exemple de réponse</span><span class="sxs-lookup"><span data-stu-id="0b4d3-243">1.6.2 Response example</span></span>

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetVulnerability)",
    "value": [
        {
            "id": "00044f612345baf759462dbe6db733b6a9c59ab4_edge_10.0.17763.1637__",
            "deviceId": "00044f612345daf756462bde6bd733b9a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d089e79bdfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "edge",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-edge"
        },
        {
            "id": "00044f912345baf756462bde6db733b9a9c56ad4_.net_framework_4.0.0.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e79bdfa178eabfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-.net_framework"
        },
        {
            "id": "00044f912345baf756462dbe6db733d6a9c59ab4_system_center_2012_endpoint_protection_4.10.209.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eed80b089e79bdfa178eadfa25e8be6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection"
        },
        {
            "id": "00044f612345bdaf759462dbe6bd733b6a9c59ab4_onedrive_20.245.1206.2__",
            "deviceId": "00044f91234daf759492dbe6bd733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_189663d45612eed224b2be2f5ea3142729e63f16a.DomainPII_21eed80b086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.245.1206.2",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2944539346-1310925172-2349113062-1001\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive"
        },
        {
            "id": "00044f912345daf759462bde6db733b6a9c56ab4_windows_10_10.0.17763.1637__",
            "deviceId": "00044f912345daf756462dbe6db733d6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eeb224d2be2f5ea3142729e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-windows_10"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a><span data-ttu-id="0b4d3-244">2. Exporter l’évaluation des vulnérabilités logicielles (via des fichiers)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-244">2. Export software vulnerabilities assessment (via files)</span></span>

### <a name="21-api-method-description"></a><span data-ttu-id="0b4d3-245">2.1 Description de la méthode API</span><span class="sxs-lookup"><span data-stu-id="0b4d3-245">2.1 API method description</span></span>

<span data-ttu-id="0b4d3-246">Cette réponse API contient toutes les données des logiciels installés par appareil.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-246">This API response contains all the data of installed software per device.</span></span> <span data-ttu-id="0b4d3-247">Renvoie un tableau avec une entrée pour chaque combinaison unique de DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-247">Returns a table with an entry for every unique combination of DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.</span></span>

#### <a name="212-limitations"></a><span data-ttu-id="0b4d3-248">2.1.2 Limitations</span><span class="sxs-lookup"><span data-stu-id="0b4d3-248">2.1.2 Limitations</span></span>

<span data-ttu-id="0b4d3-249">Les limites de taux pour cette API sont de 5 appels par minute et de 20 appels par heure.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-249">Rate limitations for this API are 5 calls per minute and 20 calls per hour.</span></span>

### <a name="22-permissions"></a><span data-ttu-id="0b4d3-250">2.2 Autorisations</span><span class="sxs-lookup"><span data-stu-id="0b4d3-250">2.2 Permissions</span></span>

<span data-ttu-id="0b4d3-251">L’une des autorisations suivantes est nécessaire pour appeler cette API.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-251">One of the following permissions is required to call this API.</span></span> <span data-ttu-id="0b4d3-252">Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-252">To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs for details](apis-intro.md).</span></span>

<span data-ttu-id="0b4d3-253">Type d’autorisation</span><span class="sxs-lookup"><span data-stu-id="0b4d3-253">Permission type</span></span> | <span data-ttu-id="0b4d3-254">Autorisation</span><span class="sxs-lookup"><span data-stu-id="0b4d3-254">Permission</span></span> | <span data-ttu-id="0b4d3-255">Nom d’affichage de l’autorisation</span><span class="sxs-lookup"><span data-stu-id="0b4d3-255">Permission display name</span></span>
---|---|---
<span data-ttu-id="0b4d3-256">Application</span><span class="sxs-lookup"><span data-stu-id="0b4d3-256">Application</span></span> | <span data-ttu-id="0b4d3-257">Vulnerability.Read.All</span><span class="sxs-lookup"><span data-stu-id="0b4d3-257">Vulnerability.Read.All</span></span> | <span data-ttu-id="0b4d3-258">\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'</span><span class="sxs-lookup"><span data-stu-id="0b4d3-258">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>
<span data-ttu-id="0b4d3-259">Déléguée (compte professionnel ou scolaire)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-259">Delegated (work or school account)</span></span> | <span data-ttu-id="0b4d3-260">Vulnerability.Read</span><span class="sxs-lookup"><span data-stu-id="0b4d3-260">Vulnerability.Read</span></span> | <span data-ttu-id="0b4d3-261">\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'</span><span class="sxs-lookup"><span data-stu-id="0b4d3-261">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>

### <a name="23-url"></a><span data-ttu-id="0b4d3-262">2.3 URL</span><span class="sxs-lookup"><span data-stu-id="0b4d3-262">2.3 URL</span></span>

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a><span data-ttu-id="0b4d3-263">2.4 Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b4d3-263">2.4 Parameters</span></span>

- <span data-ttu-id="0b4d3-264">sasValidHours : nombre d’heures de validité des URL de téléchargement (maximum 24 heures)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-264">sasValidHours – The number of hours that the download URLs will be valid for (Maximum 24 hours)</span></span>

### <a name="25-properties"></a><span data-ttu-id="0b4d3-265">2.5 Propriétés</span><span class="sxs-lookup"><span data-stu-id="0b4d3-265">2.5 Properties</span></span>

>[!Note]
>
>- <span data-ttu-id="0b4d3-266">Les fichiers sont compressés gzip & au format Json multiligne.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-266">The files are gzip compressed & in multiline Json format.</span></span>
>
>- <span data-ttu-id="0b4d3-267">Les URL de téléchargement ne sont valides que pendant 3 heures . Sinon, vous pouvez utiliser le paramètre.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-267">The download URLs are only valid for 3 hours; otherwise you can use the parameter.</span></span>
>
>- <span data-ttu-id="0b4d3-268">Pour une vitesse de téléchargement maximale de vos données, vous pouvez vous assurer que vous téléchargez à partir de la même région Azure que vos données résident.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-268">For maximum download speed of your data, you can make sure you are downloading from the same Azure region that your data resides.</span></span>
>

>[!Note]
>
>- <span data-ttu-id="0b4d3-269">Chaque enregistrement représente environ 1 To de données.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-269">Each record is approximately 1KB of data.</span></span> <span data-ttu-id="0b4d3-270">Vous devez prendre cela en compte lors du choix du paramètre pageSize approprié pour vous.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-270">You should take this into account when choosing the correct pageSize parameter for you.</span></span>
>
>- <span data-ttu-id="0b4d3-271">Certaines colonnes supplémentaires peuvent être renvoyées dans la réponse.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-271">Some additional columns might be returned in the response.</span></span> <span data-ttu-id="0b4d3-272">Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-272">These columns are temporary and might be removed, please use only the documented columns.</span></span>
>

<span data-ttu-id="0b4d3-273">Propriété (ID)</span><span class="sxs-lookup"><span data-stu-id="0b4d3-273">Property (ID)</span></span> | <span data-ttu-id="0b4d3-274">Type de données</span><span class="sxs-lookup"><span data-stu-id="0b4d3-274">Data type</span></span> | <span data-ttu-id="0b4d3-275">Description</span><span class="sxs-lookup"><span data-stu-id="0b4d3-275">Description</span></span> | <span data-ttu-id="0b4d3-276">Exemple de valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0b4d3-276">Example of a returned value</span></span>
:---|:---|:---|:---
<span data-ttu-id="0b4d3-277">Exporter des fichiers</span><span class="sxs-lookup"><span data-stu-id="0b4d3-277">Export files</span></span> | <span data-ttu-id="0b4d3-278">chaîne de \[ tableau\]</span><span class="sxs-lookup"><span data-stu-id="0b4d3-278">array\[string\]</span></span>  | <span data-ttu-id="0b4d3-279">Liste des URL de téléchargement pour les fichiers qui contiennent la capture instantanée actuelle de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-279">A list of download URLs for files holding the current snapshot of the organization.</span></span> | <span data-ttu-id="0b4d3-280">[  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]</span><span class="sxs-lookup"><span data-stu-id="0b4d3-280">[  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]</span></span>
<span data-ttu-id="0b4d3-281">GeneratedTime</span><span class="sxs-lookup"><span data-stu-id="0b4d3-281">GeneratedTime</span></span> | <span data-ttu-id="0b4d3-282">string</span><span class="sxs-lookup"><span data-stu-id="0b4d3-282">string</span></span> | <span data-ttu-id="0b4d3-283">Heure de la générer.</span><span class="sxs-lookup"><span data-stu-id="0b4d3-283">The time that the export was generated.</span></span> | <span data-ttu-id="0b4d3-284">2021-05-20T08:00:00Z</span><span class="sxs-lookup"><span data-stu-id="0b4d3-284">2021-05-20T08:00:00Z</span></span>

### <a name="26-examples"></a><span data-ttu-id="0b4d3-285">2.6 Exemples</span><span class="sxs-lookup"><span data-stu-id="0b4d3-285">2.6 Examples</span></span>

#### <a name="261-request-example"></a><span data-ttu-id="0b4d3-286">2.6.1 Exemple de requête</span><span class="sxs-lookup"><span data-stu-id="0b4d3-286">2.6.1 Request example</span></span>

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a><span data-ttu-id="0b4d3-287">2.6.2 Exemple de réponse</span><span class="sxs-lookup"><span data-stu-id="0b4d3-287">2.6.2 Response example</span></span>

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c002.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a><span data-ttu-id="0b4d3-288">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b4d3-288">See also</span></span>

- [<span data-ttu-id="0b4d3-289">Exporter les méthodes et propriétés d’évaluation par appareil</span><span class="sxs-lookup"><span data-stu-id="0b4d3-289">Export assessment methods and properties per device</span></span>](get-assessment-methods-properties.md)

- [<span data-ttu-id="0b4d3-290">Exporter l’évaluation de la configuration sécurisée par appareil</span><span class="sxs-lookup"><span data-stu-id="0b4d3-290">Export secure configuration assessment per device</span></span>](get-assessment-secure-config.md)

- [<span data-ttu-id="0b4d3-291">Exporter l’évaluation de l’inventaire logiciel par appareil</span><span class="sxs-lookup"><span data-stu-id="0b4d3-291">Export software inventory assessment per device</span></span>](get-assessment-software-inventory.md)

<span data-ttu-id="0b4d3-292">Autres associés</span><span class="sxs-lookup"><span data-stu-id="0b4d3-292">Other related</span></span>

- [<span data-ttu-id="0b4d3-293">Menaces basées sur les risques & gestion des vulnérabilités</span><span class="sxs-lookup"><span data-stu-id="0b4d3-293">Risk-based threat & vulnerability management</span></span>](next-gen-threat-and-vuln-mgt.md)

- [<span data-ttu-id="0b4d3-294">Vulnérabilités de votre organisation</span><span class="sxs-lookup"><span data-stu-id="0b4d3-294">Vulnerabilities in your organization</span></span>](tvm-weaknesses.md)
---
title: API Obtenir un objet MachineAction
description: Découvrez comment utiliser l’API Obtenir MachineAction pour récupérer une action ordinateur spécifique par son ID dans Microsoft Defender pour le point de terminaison.
keywords: api, api de graphique, api pris en charge, objet machineaction
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: dcb00d0d2afc7f873ea9c4afa3174ac46babf879
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52770780"
---
# <a name="get-machineaction-api"></a>API Obtenir machineAction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>Description de l’API
Récupère [l’action de l’ordinateur spécifique](machineaction.md) par son ID.


## <a name="limitations"></a>Limites
1. Les limites de taux pour cette API sont de 100 appels par minute et de 1 500 appels par heure.


## <a name="permissions"></a>Autorisations
L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour en savoir plus, notamment sur le choix des autorisations, voir [Utiliser Defender pour les API de point de terminaison](apis-intro.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage de l’autorisation
:---|:---|:---
Application |   Machine.Read.All |  « Lire tous les profils d’ordinateur »
Application |   Machine.ReadWrite.All | « Lire et écrire toutes les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire) | Machine.Read | « Lire les informations sur l’ordinateur »
Déléguée (compte professionnel ou scolaire) | Machine.ReadWrite | « Lire et écrire des informations sur l’ordinateur »

>[!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>- L’utilisateur doit avoir au moins l’autorisation de rôle suivante : « Afficher les données » (voir Créer et gérer des rôles [pour](user-roles.md) plus d’informations)

## <a name="http-request"></a>Requête HTTP
```
GET https://api.securitycenter.microsoft.com/api/machineactions/{id}
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Vide

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie le code de réponse 200, Ok avec une [entité Action](machineaction.md) de l’ordinateur. Si l’entité d’action de l’ordinateur avec l’ID spécifié est in trouvée - 404 - In trouvé.

## <a name="example"></a>Exemple

**Demande**

Voici un exemple de demande.

```
GET https://api.securitycenter.microsoft.com/api/machineactions/2e9da30d-27f6-4208-81f2-9cd3d67893ba
```

**Réponse**

Voici un exemple de réponse.


```
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions/$entity",
    "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
    "type": "Isolate",
    "scope": "Selective",
    "requestor": "Analyst@TestPrd.onmicrosoft.com",
    "requestorComment": "test for docs",
    "status": "Succeeded",
    "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
    "computerDnsName": "desktop-test",
    "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
    "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
    "relatedFileInfo": null
}


```

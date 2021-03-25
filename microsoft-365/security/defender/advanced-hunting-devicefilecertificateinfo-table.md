---
title: Table DeviceFileCertificateInfo dans le schéma de recherche avancé
description: En savoir plus sur les informations de signature de fichier dans la table DeviceFileCertificateInfo du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, digital signature, certificate, file signing, DeviceFileCertificateInfo
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
ms.openlocfilehash: 00e10c84c4bcb20f2e018bf05033b5b2235fd9ae
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063537"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le `DeviceFileCertificateInfo` tableau du schéma de [recherche](advanced-hunting-overview.md) avancée contient des informations sur les certificats de signature de fichiers. Ce tableau utilise les données obtenues à partir des activités de vérification de certificat effectuées régulièrement sur les fichiers sur les points de terminaison.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `IsSigned` | booléen | Indique si le fichier est signé |
| `SignatureType` | string | Indique si les informations de signature ont été lues en tant que contenu incorporé dans le fichier lui-même ou lues à partir d’un fichier catalogue externe |
| `Signer` | string | Informations sur le signataire du fichier |
| `SignerHash` | string | Valeur de hachage unique identifiant le signataire |
| `Issuer` | string | Informations sur l’autorité de certification émettrice |
| `IssuerHash` | string | Valeur de hachage unique identifiant l’autorité de certification émettrice |
| `CertificateSerialNumber` | string | Identificateur du certificat propre à l’autorité de certification émettrice |
| `CrlDistributionPointUrls` | string |  Tableau JSON répertoriant les URL des partages réseau qui contiennent des certificats et des listes de révocation de certificats (CRL) |
| `CertificateCreationTime` | DateHeure | Date et heure de création du certificat |
| `CertificateExpirationTime` | DateHeure | Date et heure d’expiration du certificat |
| `CertificateCountersignatureTime` | DateHeure | Date et heure de contre-signature du certificat |
| `IsTrusted` | booléen | Indique si le fichier est approuvé en fonction des résultats de la fonction WinVerifyTrust, qui recherche des informations de certificat racine inconnues, des signatures non valides, des certificats révoqués et d’autres attributs douteux |
| `IsRootSignerMicrosoft` | booléen | Indique si le signataire du certificat racine est Microsoft |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. | 

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
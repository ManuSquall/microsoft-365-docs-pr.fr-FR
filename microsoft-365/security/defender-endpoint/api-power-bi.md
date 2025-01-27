---
title: Connexion des API Microsoft Defender for Endpoint Power BI
ms.reviewer: ''
description: Créez un rapport Power Business Intelligence (BI) sur les API Microsoft Defender for Endpoint.
keywords: api, api pris en charge, Power BI, rapports
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.openlocfilehash: 23d9d61644b4c9adad69a5e467e49ca2b1d92413
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "53290230"
---
# <a name="create-custom-reports-using-power-bi"></a>Créer des rapports personnalisés à l’aide Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Dans cette section, vous allez apprendre à créer un Power BI sur les API Defender for Endpoint.

Le premier exemple montre comment connecter des Power BI à l’API de recherche avancée et le deuxième exemple illustre une connexion à nos API OData, telles que les actions de l’ordinateur ou les alertes.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>Connecter Power BI à l’API de recherche avancée

- Ouvrez Microsoft Power BI

- Click **Get Data** Blank  >  **Query**

  ![Image de création d’une requête vide](images/power-bi-create-blank-query.png)

- Cliquez sur **Éditeur avancé**

  ![Image de l’éditeur avancé ouvert](images/power-bi-open-advanced-editor.png)

- Copiez le texte ci-dessous et collez-le dans l’éditeur :

```
    let
        AdvancedHuntingQuery = "DeviceEvents | where ActionType contains 'Anti' | limit 20",

        HuntingUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries",

        Response = Json.Document(Web.Contents(HuntingUrl, [Query=[key=AdvancedHuntingQuery]])),

        TypeMap = #table(
            { "Type", "PowerBiType" },
            {
                { "Double",   Double.Type },
                { "Int64",    Int64.Type },
                { "Int32",    Int32.Type },
                { "Int16",    Int16.Type },
                { "UInt64",   Number.Type },
                { "UInt32",   Number.Type },
                { "UInt16",   Number.Type },
                { "Byte",     Byte.Type },
                { "Single",   Single.Type },
                { "Decimal",  Decimal.Type },
                { "TimeSpan", Duration.Type },
                { "DateTime", DateTimeZone.Type },
                { "String",   Text.Type },
                { "Boolean",  Logical.Type },
                { "SByte",    Logical.Type },
                { "Guid",     Text.Type }
            }),

        Schema = Table.FromRecords(Response[Schema]),
        TypedSchema = Table.Join(Table.SelectColumns(Schema, {"Name", "Type"}), {"Type"}, TypeMap , {"Type"}),
        Results = Response[Results],
        Rows = Table.FromRecords(Results, Schema[Name]),
        Table = Table.TransformColumnTypes(Rows, Table.ToList(TypedSchema, (c) => {c{0}, c{2}}))

    in Table
```

- Cliquez sur **Terminé**

- Cliquez sur **Modifier les informations d’identification**

    ![Image de modification des informations d’identification0](images/power-bi-edit-credentials.png)

- Sélectionner un **compte d’organisation**  >  **pour se connecter**

    ![Image de l’ensemble des informations d’identification1](images/power-bi-set-credentials-organizational.png)

- Entrez vos informations d’identification et attendez d’être connexion

- Cliquez **sur Connecter**

    ![Image de l’ensemble des informations d’identification2](images/power-bi-set-credentials-organizational-cont.png)

- À présent, les résultats de votre requête s’affichent en tant que table et vous pouvez commencer à créer des visualisations au-dessus de celui-ci !

- Vous pouvez dupliquer cette table, la renommer et modifier la requête de recherche avancée à l’intérieur pour obtenir les données que vous souhaitez.

## <a name="connect-power-bi-to-odata-apis"></a>Connecter Power BI aux API OData

- La seule différence par rapport à l’exemple ci-dessus est la requête à l’intérieur de l’éditeur.

- Copiez le texte ci-dessous et collez-le dans l’éditeur pour tirer toutes les **actions de** l’ordinateur de votre organisation :

```
    let

        Query = "MachineActions",

        Source = OData.Feed("https://api.securitycenter.microsoft.com/api/" & Query, null, [Implementation="2.0", MoreColumns=true])
    in
        Source
```

- Vous pouvez faire de même pour les alertes et les **ordinateurs.** 
- Vous pouvez également utiliser des requêtes OData pour les filtres de requêtes, voir [Utilisation de requêtes OData](exposed-apis-odata-samples.md)

## <a name="power-bi-dashboard-samples-in-github"></a>Power BI exemples de tableau de bord dans GitHub

Pour plus d’informations, [voir Power BI modèles de rapport.](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI)

## <a name="sample-reports"></a>Exemples de rapports

Affichez les exemples de rapport microsoft Defender pour Power BI de point de terminaison. Pour plus d’informations, voir [Parcourir les exemples de code.](/samples/browse/?products=mdatp)

## <a name="related-topics"></a>Voir aussi

- [API Defender pour les points de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Utilisation des requêtes OData](exposed-apis-odata-samples.md)

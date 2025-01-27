---
title: Modifier le schéma de correspondance des données exactes pour utiliser la correspondance configurable
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment modifier un schéma EDM pour utiliser une correspondance configurable.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7d470b986d4a94206935efb832deec7171f8e404
ms.sourcegitcommit: 05f40904f8278f53643efa76a907968b5c662d9a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52114192"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>Modifier le schéma de correspondance des données exactes pour utiliser la correspondance configurable

La classification EDM (Exact Data Match) vous permet de créer des types d’informations sensibles personnalisés qui font référence à des valeurs exactes dans une base de données d’informations sensibles. Lorsque vous devez autoriser les variantes d’une chaîne exacte, vous pouvez utiliser une *correspondance configurable* pour indiquer à Microsoft 365 d’ignorer la casse et certains séparateurs. 

> [!IMPORTANT]
> Utilisez cette procédure pour modifier un schéma EDM et un fichier de données existants.

1. Désinstallez **EdmUploadAgent.exe** de l’ordinateur que vous utilisez pour vous connecter à Microsoft 365 afin de charger les fichiers de données et le modèle EDM.

2. Téléchargez le fichier **EdmUploadAgent.exe** approprié pour votre abonnement en utilisant les liens ci-dessous :
    - [Commercial + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) : pour la plupart des clients commerciaux
    - [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) : conçu spécifiquement pour les abonnés cloud du secteur public haute sécurité
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) : conçu spécifiquement pour les clients cloud du Department of Defense américain

3. Autorisez l’agent de chargement EDM, ouvrez la fenêtre Invite de commandes (en tant qu’administrateur), puis exécutez la commande suivante :

   `EdmUploadAgent.exe /Authorize`

4. Si vous n’avez pas de copie actuelle du schéma existant, vous devez en télécharger une. Exécutez la commande suivante :

    `EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]`

5. Personnalisez le schéma de sorte que chaque colonne utilise « caseInsensitive » et/ou « ignoredDelimiters ».  La valeur par défaut de « caseInsensitive » est « false » et « ignoredDelimiters » est une chaîne vide. 

> [!NOTE]
> Le type d’informations sensibles personnalisé sous-jacent ou le type d’informations sensibles intégré utilisé pour détecter le modèle regex général doivent prendre en charge la détection des entrées de variantes indiquées avec ignoredDelimiters. Par exemple, le type d’informations sensibles intégré Numéro de sécurité sociale (SSN) américain permet de détecter les variantes des données qui incluent des tirets, des espaces ou une absence d’espace entre les numéros groupés qui composent le numéro de sécurité sociale. Par conséquent, les seuls délimiteurs pertinents à inclure dans ignoredDelimiters EDM pour les données SSN sont : les tirets et les espaces.

Voici un exemple de schéma qui simule la correspondance non sensible à la casse en créant les colonnes supplémentaires nécessaires pour identifier les variations de casse dans les données sensibles.

```xml
<EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
  <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
           <Field name="PolicyNumber" searchable="true" />
           <Field name="PolicyNumberLowerCase" searchable="true" />
           <Field name="PolicyNumberUpperCase" searchable="true" />
           <Field name="PolicyNumberCapitalLetters" searchable="true" />
  </DataStore>
</EdmSchema>
```

Dans l’exemple ci-dessus, les variantes de la colonne d’origine `PolicyNumber` ne sont plus nécessaires si `caseInsensitive` et `ignoredDelimiters` sont ajoutés.

Pour mettre à jour ce schéma de façon à ce qu’EDM utilise la correspondance configurable, utilisez les indicateurs `caseInsensitive` et `ignoredDelimiters`.  Cela se présente comme suit :

```xml
<EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
  <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
         <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
  </DataStore>
</EdmSchema>
```

L’indicateur `ignoredDelimiters` prend en charge tous les caractères non alphanumériques. Voici quelques exemples :
- \.
- \-
- \/
- \_
- \*
- \^
- \#
- \!
- \?
- \[
- \]
- \{
- \}
- \\
- \~
- \;

L’indicateur `ignoredDelimiters` ne prend pas en charge :
- Les caractères 0 à 9
- A-Z
- a-z
- \"
- \,

6. Connectez-vous au Centre de sécurité et conformité en utilisant la procédure [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

> [!NOTE]
> Si votre organisation a configuré une [Clé client pour Microsoft 365 au niveau du client (préversion publique)](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview), la correspondance exacte des données utilisera automatiquement sa fonctionnalité de chiffrement. Cette offre est disponible uniquement pour les clients sous licence E5 dans le cloud commercial.

7. Mettez à jour votre schéma en exécutant ces applets de commande une par une :

`$edmSchemaXml=Get-Content .\\edm.xml -Encoding Byte -ReadCount 0`

`Set-DlpEdmSchema -FileData $edmSchemaXml -Confirm:$true`

8. Si nécessaire, mettez à jour le fichier de données pour qu’il corresponde à la nouvelle version du schéma.

> [!TIP]
> Si vous le souhaitez, vous pouvez exécuter une validation par rapport à votre fichier CSV avant de charger en exécutant :
>
>`EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
>
>Pour plus d’informations sur tous les paramètres pris en charge par EdmUploadAgent.exe
>
> `EdmUploadAgent.exe /?`

9. Ouvrez la fenêtre Invite de commandes (en tant qu’administrateur), puis exécutez la commande suivante pour hacher et charger vos données sensibles :

    `EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]`


## <a name="related-articles"></a>Articles connexes

- [Créer un type d’informations sensibles personnalisé à l’aide d’une classification de correspondance exacte des données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Types d’informations sensibles personnalisés](./sensitive-information-type-learn-about.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Microsoft Cloud App Security](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
---
title: Ajouter des données d’un jeu à réviser à un autre
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment sélectionner des documents à partir d’un ensemble de révision et les utiliser individuellement dans un autre ensemble dans Advanced eDiscovery cas.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: e03cd042ac11c36838e712ccd945bc249b849f43
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285178"
---
# <a name="add-data-to-a-review-set-from-another-review-set"></a>Ajouter des données à partir d’un groupe de révision à un autre groupe de révision.

Dans certains cas, il peut être nécessaire de sélectionner des documents à partir d’un ensemble de révision et de les utiliser individuellement dans un autre ensemble de révision. Cette fonctionnalité est particulièrement utile si vous avez éliminé du contenu dans un ensemble de révision et que vous voulez exécuter des analyses sur le sous-ensemble de données.

Suivez le flux de travail de cet article pour ajouter du contenu d’un jeu à réviser à un autre.

## <a name="create-a-review-set"></a>Créer un jeu à réviser

Avant de commencer, vous devez créer un jeu à réviser pour ajouter les données.  Un nouvel ensemble de révision peut être ajouté sous l’onglet **Ensembles de révision** du cas. Pour plus d’informations, [voir Créer un jeu à réviser.](managing-review-sets.md#create-a-review-set)

## <a name="step-1-identify-content-to-add-to-another-review-set"></a>Étape 1 : Identifier le contenu à ajouter à un autre jeu à réviser

Vous pouvez ajouter du contenu d’un ensemble de révision à un autre en sélectionnant des documents spécifiques dans l’ensemble de révision source ou en sélectionnant tous les éléments renvoyés par la requête de révision. Si vous ajoutez des éléments sélectionnés, sélectionnez les éléments, **sélectionnez Action,** puis sélectionnez Ajouter **à un autre jeu à réviser.**

![Ajouter à un autre jeu à réviser dans le menu Action](../media/64f2a4d4-eba3-4ab3-a3ba-d519feea3142.png)

## <a name="step-2-specify-options-for-adding-to-another-review-set"></a>Étape 2 : Spécifier les options d’ajout à un autre jeu à réviser

Dans la page **volante** Ajouter à un autre jeu à réviser, choisissez le jeu à réviser à ajouter aux éléments. Indiquez si vous souhaitez **ajouter tous les résultats de recherche** ou les éléments **sélectionnés.**   Des informations supplémentaires fournissent des options pour inclure toutes les métadonnées à partir des éléments et s’il faut inclure les balises (en sélectionnant la case à cocher Étiquettes) à partir du jeu de révision source lorsque les documents sont ajoutés au nouveau jeu à réviser.   

![Options d’ajout de données à un autre jeu à réviser](../media/6440ee44-68fd-44d7-b43a-3a477345525c.png)

Une fois que vous avez cliqué sur **OK,** un nouveau travail (nommé **Ajout** de données à un autre jeu à réviser) est créé pour ajouter le contenu à un autre jeu à réviser. Vous pouvez aller dans l’onglet **Travaux** et surveiller la progression de ce travail. Pour plus d’informations, voir [Gérer les travaux.](managing-jobs-ediscovery20.md)

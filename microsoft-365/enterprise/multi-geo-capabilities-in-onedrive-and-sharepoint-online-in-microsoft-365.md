---
title: Fonctionnalités multi-géographiques OneDrive et SharePoint Online
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Étendez votre présence Microsoft 365 à plusieurs régions géographiques grâce aux fonctionnalités multi-géographiques dans OneDrive Online.
ms.openlocfilehash: 8f42b071abef0602304f1a468190c33700fe3e82
ms.sourcegitcommit: 321610fd312e5c54ae8a757a71ab0c9fd2f1ac03
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48995908"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Fonctionnalités multi-géographiques OneDrive et SharePoint Online

Les fonctionnalités Multi-Géo dans OneDrive et SharePoint Online permettent de contrôler les ressources partagées telles que les sites d’équipe SharePoint et les boîtes aux lettres de groupe Microsoft 365 stockées au repos dans un pays ou une région.

Chaque utilisateur, une boîte aux lettres de groupe et un site SharePoint ont un emplacement recommandé de données (PDL) qui indique l’emplacement géographique où les données connexes sont stockées. Les donnée personnelle des utilisateurs (boîte aux lettres Exchange et OneDrive), ainsi que les sites de Groupes Microsoft 365 ou SharePoint qu’ils créent peuvent être stockées dans l’emplacement spécifié géographique pour répondre aux exigences de résidence de données. Vous pouvez[spécifier des différents administrateurs pour chaque emplacement géo](add-a-sharepoint-geo-admin.md).

Les utilisateurs profitent d’une expérience transparente lors de l’utilisation des services Microsoft 365, y compris les applications Office, OneDrive et Recherche. Voir [Expérience utilisateur dans un environnement multigéographique](multi-geo-user-experience.md) pour plus de détails.

## <a name="onedrive"></a>OneDrive

Le OneDrive de chaque utilisateur peut être configuré dans ou [déplacé par un administrateur](move-onedrive-between-geo-locations.md) vers un emplacement satellite conformément aux PDL de l’utilisateur. Les fichiers personnels sont alors conservés dans cet emplacement géo, même s’ils peuvent être partagés avec des utilisateurs dans d’autres emplacements géo.

## <a name="sharepoint-sites-and-groups"></a>Sites et groupes SharePoint

La gestion de la fonctionnalité géo multiple est disponible via le Centre d’administration SharePoint. Vous trouverez des informations détaillées dans le [ billet de blog correspondant](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Lorsqu’un utilisateur crée un site connecté à un groupe SharePoint dans un environnement multigéographique, leur PDL permet de déterminer l’emplacement géo où le site et sa boîte aux lettres de groupe associés sont créés. (Si une valeur PDL de l’utilisateur n’a pas été définie ou a été définie sur l’emplacement géo qui n’a pas été configuré comme un emplacement satellite, puis le site et la boîte aux lettres sont créés dans l’emplacement central.)

Les services Microsoft 365 autre qu’ Exchange, OneDrive et SharePoint ne sont pas multi-géographiques. Toutefois, les Groupes Microsoft 365 créés par ces services sont marqués avec PDL de l’application de création et leur boîte aux lettres de groupe Exchange et le Site de groupe O365 SharePoint fournis dans le géo correspondant. 

## <a name="managing-the-multi-geo-environment"></a>Gestion de l’environnement multi-Géo

Configurer et gérer votre environnement multi-géographique sont effectués via le Centre d’Administration SharePoint. 

![Capture d’écran de la page emplacements géo dans le Centre d’Administration SharePoint](../media/sharepoint-multi-geo-admin-center.png)

(Certaines actions, telles que le déplacement d’un site SharePoint ou un site OneDrive nécessitent Microsoft PowerShell).

## <a name="see-also"></a>Voir aussi

[Multi-Geo dans les groupes SharePoint et Microsoft 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Administration d’un environnement multi-géographique](administering-a-multi-geo-environment.md)

[Quotas de stockage SharePoint dans des environnements multi-géographiques](sharepoint-multi-geo-storage-quota.md)

[Administration des boîtes aux lettres Exchange Online dans un environnement multi-géographique](administering-exchange-online-multi-geo.md)

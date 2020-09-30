---
title: Balisage d’image dans SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: Priority
description: Présentation du balisage d’image dans SharePoint Syntex
ms.openlocfilehash: 38b9ad6823aa5f63a4ddec87bab7fec52a37f163
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295899"
---
# <a name="image-tagging-in-sharepoint-syntex"></a>Balisage d’image dans SharePoint Syntex

Par défaut, le balisage de base des images est activé pour SharePoint et OneDrive. Les images chargées dans l’un des emplacements sont automatiquement analysées et des balises valables sont appliquées, le cas échéant, à partir d’une liste de 37 balises de base. Les utilisateurs peuvent trouver des images en effectuant une recherche sur les balises d’images.

Lorsqu’un utilisateur charge une image, le processus de balisage s’exécute automatiquement. Si une image est modifiée, le processus de balisage s’exécute à nouveau pour la mise à jour des balises.

Les utilisateurs disposant d’autorisations sur le fichier image peuvent consulter et modifier les balises dans le volet d’informations sur le fichier ou dans la page des résultats de la recherche. Une fois qu’un utilisateur modifie les balises d’une image, le système n’effectue plus le balisage automatique sur cette image, même dans le cas où elle est modifiée.

Si vous désactivez l’option de balisage, les images ne seront plus marquées automatiquement. Les balises existantes ne seront pas supprimées.

## <a name="configure-image-tagging"></a>Configurer le balisage d’image

Vous pouvez configurer le balisage d’images dans le Centre d’administration Microsoft 365.  

Pour activer ou désactiver le balisage d’images

1. Dans le Centre d’administration Microsoft 365, cliquez sur **Configuration**.

2. Sous **Connaissances organisationnelles**, cliquez sur **Automatiser la compréhension de contenu**.

3. Cliquez sur **Gérer**.

4. Sous l’onglet **Balisage d'image**, cliquez sur **Modifier**.

5. Choisissez d’autoriser le **Balisage d’image** ou de le **Désactiver**.

6. Cliquez sur **Enregistrer**.

    ![Capture d’écran du contrôle de balisage d’image](../media/content-understanding/sharepoint-syntex-image-tagging-control.png)

## <a name="see-also"></a>Voir aussi

[Configurer la compréhension de contenu](set-up-content-understanding.md)
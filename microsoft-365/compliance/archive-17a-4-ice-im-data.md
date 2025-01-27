---
title: Configurer un connecteur pour archiver les données ICE Connecter Chat dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Découvrez comment configurer et utiliser un connecteur ICE 17a-4 ICE Connecter Chat DataParser pour importer et archiver des données ICE Connecter Chat dans Microsoft 365.
ms.openlocfilehash: 2c9eb6524e4f5e131603b5998d215e0b2d8111d3
ms.sourcegitcommit: 778103d20a2b4c43e524aa436775764d8d8d4c33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2021
ms.locfileid: "53097138"
---
# <a name="set-up-a-connector-to-archive-ice-connect-chat-data-preview"></a>Configurer un connecteur pour archiver les données ICE Connecter Chat (aperçu)

Utilisez [ice DataParser](https://www.17a-4.com/ice-dataparser/) de 17a-4 LLC pour importer et archiver des données de ICE Connecter Chat vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. DataParser inclut un connecteur ICE Chat configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur ICE DataParser convertit les données ICE Connecter Chat au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs Microsoft 365.

Une fois les données ICE Connecter Chat stockées dans les boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur ICE DataParser pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-ice-chat-data"></a>Vue d’ensemble de l’archivage des données ICE Chat

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver les données ICE Connecter Chat dans Microsoft 365.

![Flux de travail d’archivage pour ICE Connecter données de conversation 17a-4](../media/ICEChatDataParserConnectorWorkflow.png)

1. Votre organisation travaille avec 17a-4 pour configurer l’analyseur de données ICE.

2. Régulièrement, les éléments ICE Connecter Chat sont collectés par DataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur ICE DataParser que vous créez dans le Centre de conformité Microsoft 365 se connecte à DataParser et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier du dossier Boîte de réception nommé **ICE DataParser** est créé dans les boîtes aux lettres utilisateur et les éléments ICE Connecter Chat sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément ICE Connecter Chat contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [17a-4 LLC.](https://www.17a-4.com/contact/) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur ICE DataParser à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-an-ice-dataparser-connector"></a>Étape 1 : Configurer un connecteur ICE DataParser

La première étape consiste à accéder à la page Connecteurs de données dans le Centre de conformité Microsoft 365 et à créer un connecteur 17a-4 pour les données ICE Connecter Chat.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **ICE DataParser**.

2. Dans la page de description du produit **ICE DataParser,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte 17a-4 et complétez les étapes de l’Assistant Connexion ICE DataParser.

## <a name="step-2-configure-the-ice-dataparser-connector"></a>Étape 2 : Configurer le connecteur ICE DataParser

Travaillez avec la prise en charge 17a-4 pour configurer le connecteur ICE DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Ma cartographier les utilisateurs

Le connecteur ICE DataParser mase automatiquement les utilisateurs à leurs adresses Microsoft 365 courrier avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-ice-dataparser-connector"></a>Étape 4 : Surveiller le connecteur ICE DataParser

Après avoir créé un connecteur ICE DataParser, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur ICE DataParser que vous avez créé pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.

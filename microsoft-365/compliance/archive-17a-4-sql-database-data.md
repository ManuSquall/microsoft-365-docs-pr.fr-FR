---
title: Configurer un connecteur pour archiver des SQL de données dans Microsoft 365
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
description: Découvrez comment configurer et utiliser un connecteur DataParser 17a-4 SQL pour importer et archiver SQL données dans Microsoft 365.
ms.openlocfilehash: 51fd433ad072ba5afe0b314d7b61041728337240
ms.sourcegitcommit: 410f6e1c6cf53c3d9013b89d6e0b40a050ee9cad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53137666"
---
# <a name="set-up-a-connector-to-archive-sql-data-preview"></a>Configurer un connecteur pour archiver les SQL données (aperçu)

Utilisez la [SQL DataParser](https://www.17a-4.com/sql-dataparser/) de 17a-4 LLC pour importer et archiver des données à partir d’une base de données SQL vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. DataParser inclut un connecteur SQL configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le SQL DataParser convertit les données SQL au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs Microsoft 365.

Une fois SQL données stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d SQL pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-sql-data"></a>Vue d’ensemble de l’archivage SQL données

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver SQL données dans Microsoft 365.

![Flux de travail d’archivage pour SQL données 17a-4](../media/SQLDatabaseDataParserConnectorWorkflow.png)

1. Votre organisation travaille en 17a-4 pour configurer l’analyseur de SQL données.

2. Régulièrement, les SQL sont collectés par DataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le SQL DataParser que vous créez dans le Centre de conformité Microsoft 365 se connecte à DataParser et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier du dossier Boîte de réception nommé **SQL DataParser** est créé dans les boîtes aux lettres utilisateur et les éléments SQL sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque SQL contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [17a-4 LLC.](https://www.17a-4.com/contact/) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur DataParser SQL à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres à l’Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-a-sql-dataparser-connector"></a>Étape 1 : Configurer un connecteur DataParser SQL’analyseur de données

La première étape consiste à accéder à la page Connecteurs de données dans le Centre de conformité Microsoft 365 et à créer un connecteur 17a-4 pour SQL données.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **SQL DataParser**.

2. Dans la page SQL description du produit **DataParser,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte 17a-4 et complétez les étapes de l SQL de connexion DataParser.

## <a name="step-2-configure-the-sql-dataparser-connector"></a>Étape 2 : Configurer le connecteur SQL DataParser

Travaillez avec la prise en charge 17a-4 pour configurer SQL connecteur DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Ma cartographier les utilisateurs

Le SQL DataParser masique automatiquement les utilisateurs à leurs adresses Microsoft 365 courrier avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-sql-dataparser-connector"></a>Étape 4 : Surveiller le connecteur SQL DataParser

Après avoir créé un SQL DataParser, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur DataParser SQL que vous avez créé pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.

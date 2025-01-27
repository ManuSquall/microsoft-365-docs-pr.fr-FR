---
title: Utiliser les API Microsoft Defender pour les points de terminaison
ms.reviewer: ''
description: Découvrez comment concevoir une application Windows pour obtenir un accès par programme à Microsoft Defender pour Endpoint sans utilisateur.
keywords: api, api de graphique, api pris en charge, acteur, alertes, appareil, utilisateur, domaine, ip, fichier, recherche avancée, requête
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
ms.openlocfilehash: 876dddf7a68b9844dea6a30ff4ebbbe3c2b75b69
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52844547"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>Utiliser les API Microsoft Defender pour les points de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Cette page explique comment créer une application pour obtenir l’accès par programme à Defender for Endpoint pour le compte d’un utilisateur.

Si vous avez besoin d’un accès par programmation à Microsoft Defender pour endpoint sans utilisateur, reportez-vous à Access Microsoft Defender pour Endpoint avec le [contexte de l’application.](exposed-apis-create-app-webapp.md)

Si vous n’êtes pas sûr de l’accès dont vous avez besoin, lisez la [page Introduction.](apis-intro.md)

Microsoft Defender pour point de terminaison expose la plupart de ses données et actions par le biais d’un ensemble d’API par programme. Ces API vous permettront d’automatiser les flux de travail et d’innover en fonction des fonctionnalités de Microsoft Defender for Endpoint. L’accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, [voir code d’autorisation OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

En règle générale, vous devez suivre les étapes suivantes pour utiliser les API :
- Créer une application AAD
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Defender for Endpoint

Cette page explique comment créer une application AAD, obtenir un jeton d’accès à Microsoft Defender pour le point de terminaison et valider le jeton.

>[!NOTE]
> Lorsque vous accédez à l’API Microsoft Defender for Endpoint pour le compte d’un utilisateur, vous avez besoin des autorisations d’application et d’utilisateur correctes.
> Si vous n’êtes pas familiarisé avec les autorisations utilisateur sur Microsoft Defender pour le point de terminaison, voir Gérer l’accès au portail à l’aide du contrôle [d’accès basé sur les rôles.](rbac.md)

>[!TIP]
> Si vous avez l’autorisation d’effectuer une action dans le portail, vous avez l’autorisation d’effectuer l’action dans l’API.

## <a name="create-an-app"></a>Créer une application

1. Connectez-vous [à Azure](https://portal.azure.com) avec un compte d’utilisateur ayant le **rôle Administrateur** général.

2. Accédez à **Azure Active Directory**  >  **Inscription de l’application Nouvelle**  >  **inscription.** 

   ![Image de la Microsoft Azure et de la navigation vers l’inscription de l’application](images/atp-azure-new-app2.png)

3. Lorsque la page **Inscrire une application** s’affiche, saisissez les informations d’inscription de votre application :

   - **Nom** : saisissez un nom d’application cohérent qui s’affichera pour les utilisateurs de l’application.
   - **Types de compte pris en charge** : sélectionnez les comptes à prendre en charge par l’application.

       | Types de comptes pris en charge | Description |
       |-------------------------|-------------|
       | **Comptes dans cet annuaire organisationnel uniquement** | Sélectionnez cette option si vous générez une application métier. Cette option n’est pas disponible si vous n’inscrivez pas l’application dans un annuaire.<br><br>Cette option s’applique à un compte Azure AD à locataire unique seulement.<br><br>Il s’agit de l’option par défaut, sauf si vous inscrivez l’application hors d’un annuaire. Dans les cas où l’application est inscrite hors d’un annuaire, l’option par défaut est comptes mutualisés Azure AD et comptes Microsoft personnels. |
       | **Comptes dans un annuaire organisationnel** | Sélectionnez cette option si vous souhaitez cibler tous les clients professionnels et éducatifs.<br><br>Cette option s’applique à un compte Azure AD multi-locataire seulement.<br><br>Si vous avez inscrit l’application comme compte Azure AD à locataire unique seulement, vous pouvez le mettre à jour vers un compte Azure AD multi-locataire et inversement via le panneau **Authentification**. |
       | **Comptes dans un annuaire organisationnel et comptes personnels Microsoft** | Sélectionnez cette option pour cibler l’ensemble le plus large de clients.<br><br>Cette option s’applique à des comptes Microsoft personnels et Azure AD multi-locataires.<br><br>Si vous avez inscrit l’application comme comptes Microsoft personnels et Azure AD multi-locataires, vous ne pouvez pas modifier cela dans l’interface utilisateur. Vous devez utiliser l’éditeur de manifeste de l’application pour modifier les types de compte pris en charge. |

   - **URI de redirection (facultatif)**  : sélectionnez le type d’application que vous créez, **Web** ou **Client public (mobile et bureau)**, puis entrez l’URI de redirection (ou URL de réponse).
       - Pour les applications web, indiquez l’URL de base de votre application. Par exemple, `http://localhost:31544` peut être l’URL d’une application web en cours d’exécution sur votre ordinateur local. Les utilisateurs peuvent utiliser cette URL pour se connecter à une application web cliente.
       - Pour les applications de client public, indiquez l’URI utilisé par Azure AD pour renvoyer les réponses de jeton. Entrez une valeur spécifique de votre application, par exemple, `myapp://auth`.

     Pour accéder à des exemples spécifiques aux applications web ou natives, consultez les [Guides de démarrage rapides](/azure/active-directory/develop/#quickstarts).

     Lorsque vous avez terminé, sélectionnez **Inscrire**.

4. Autorisez votre application à accéder à Microsoft Defender pour le point de terminaison et à lui attribuer l’autorisation « Lire les alertes » :

    - Dans la page de votre application, sélectionnez **Autorisations api** Ajouter des API d’autorisation que mon  >    >   organisation utilise > type **WindowsDefenderATP** et sélectionnez **sur WindowsDefenderATP**.

    - **Remarque**: *WindowsDefenderATP* n’apparaît pas dans la liste d’origine. Commencez à écrire son nom dans la zone de texte pour l’voir apparaître.

      ![ajouter une autorisation](images/add-permission.png)

    - Choose **Delegated permissions**  >  **Alert.Read** > select **Add permissions**

      ![autorisations d’application](images/application-permissions-public-client.png)

    - **Remarque importante**: sélectionnez les autorisations pertinentes. Les alertes de lecture ne sont qu’un exemple.

      Par exemple,

      - Pour [exécuter des requêtes avancées,](run-advanced-query-api.md)sélectionnez l’autorisation « Exécuter des requêtes avancées »
      - Pour [isoler un appareil, sélectionnez](isolate-machine.md)l’autorisation « Isoler l’ordinateur »
      - Pour déterminer l’autorisation qui vous est nécessaire, consultez la section **Autorisations** dans l’API que vous souhaitez appeler.

    - Sélectionner **Accorder le consentement**

      **Remarque**: chaque fois que vous ajoutez une autorisation, vous devez sélectionner l’autorisation **Accorder le consentement** pour que la nouvelle autorisation prenne effet.

      ![Image de l’octroi d’autorisations](images/grant-consent.png)

6. Notez votre ID d’application et votre ID de client :

   - Dans la page de votre application, allez à **Vue d’ensemble** et copiez les informations suivantes :

   ![Image de l’ID d’application créé](images/app-and-tenant-ids.png)


## <a name="get-an-access-token"></a>Obtenir un jeton d’accès

Pour plus d’informations sur les jetons AAD, voir [le didacticiel Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="using-c"></a>Utilisation de C #

- Copiez/collez la classe ci-dessous dans votre application.
- Utilisez **la méthode AcquireUserTokenAsync** avec votre ID d’application, ID de client, nom d’utilisateur et mot de passe pour acquérir un jeton.

    ```csharp
    namespace WindowsDefenderATP
    {
        using System.Net.Http;
        using System.Text;
        using System.Threading.Tasks;
        using Newtonsoft.Json.Linq;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            private const string WdatpResourceId = "https://api.securitycenter.microsoft.com";

            public static async Task<string> AcquireUserTokenAsync(string username, string password, string appId, string tenantId)
            {
                using (var httpClient = new HttpClient())
                {
                    var urlEncodedBody = $"resource={WdatpResourceId}&client_id={appId}&grant_type=password&username={username}&password={password}";

                    var stringContent = new StringContent(urlEncodedBody, Encoding.UTF8, "application/x-www-form-urlencoded");

                    using (var response = await httpClient.PostAsync($"{Authority}/{tenantId}/oauth2/token", stringContent).ConfigureAwait(false))
                    {
                        response.EnsureSuccessStatusCode();

                        var json = await response.Content.ReadAsStringAsync().ConfigureAwait(false);

                        var jObject = JObject.Parse(json);

                        return jObject["access_token"].Value<string>();
                    }
                }
            }
        }
    }
    ```

## <a name="validate-the-token"></a>Valider le jeton

Vérifiez que vous avez reçu un jeton correct :
- Copier/coller dans [JWT](https://jwt.ms) le jeton obtenu à l’étape précédente afin de le décoder
- Valider que vous obtenez une revendication « scp » avec les autorisations d’application souhaitées
- Dans la capture d’écran ci-dessous, vous pouvez voir un jeton décodé acquis à partir de l’application dans le didacticiel :

![Image de validation de jeton](images/nativeapp-decoded-token.png)

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Utiliser le jeton pour accéder à l’API Microsoft Defender for Endpoint

- Choisissez l’API que vous souhaitez utiliser - API [Microsoft Defender pour point de terminaison prise en charge](exposed-apis-list.md)
- Définissez l’en-tête Authorization dans la requête HTTP que vous envoyez à « Bearer {token} » (le porteur est le schéma d’autorisation)
- Le délai d’expiration du jeton est de 1 heure (vous pouvez envoyer plusieurs demandes avec le même jeton)

- Exemple d’envoi d’une demande pour obtenir une liste d’alertes à **l’aide C#** 

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Voir aussi
- [API Microsoft Defender pour point de terminaison](exposed-apis-list.md)
- [Accéder à Microsoft Defender pour le point de terminaison avec le contexte de l’application](exposed-apis-create-app-webapp.md)

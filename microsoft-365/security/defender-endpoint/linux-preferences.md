---
title: Définir des préférences pour Microsoft Defender ATP pour Linux
ms.reviewer: ''
description: Décrit comment configurer Microsoft Defender ATP pour Linux dans les entreprises.
keywords: microsoft, defender, atp, linux, installation, déployer, désinstallation, casque, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ed28d3b5b7bafaea2d72b7a8c45f66bf69033bc2
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51187792"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-for-linux"></a>Définir des préférences pour Microsoft Defender pour le point de terminaison pour Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

>[!IMPORTANT]
>Cette rubrique contient des instructions sur la façon de définir des préférences pour Defender pour Endpoint pour Linux dans les environnements d’entreprise. Si vous souhaitez configurer le produit sur un appareil à partir de la ligne de commande, consultez [Ressources.](linux-resources.md#configure-from-the-command-line)

Dans les environnements d’entreprise, Defender pour Point de terminaison pour Linux peut être géré via un profil de configuration. Ce profil est déployé à partir de l’outil de gestion de votre choix. Les préférences gérées par l’entreprise prévalent sur les préférences définies localement sur l’appareil. En d’autres termes, les utilisateurs de votre entreprise ne peuvent pas modifier les préférences définies par le biais de ce profil de configuration.

Cet article décrit la structure de ce profil (y compris un profil recommandé que vous pouvez utiliser pour commencer) et des instructions sur la façon de déployer le profil.

## <a name="configuration-profile-structure"></a>Structure de profil de configuration

Le profil de configuration est un fichier .json qui se compose d’entrées identifiées par une clé (qui indique le nom de la préférence), suivi d’une valeur, qui dépend de la nature de la préférence. Les valeurs peuvent être simples, telles qu’une valeur numérique, ou complexes, telles qu’une liste imbriée de préférences.

En règle générale, vous utilisez un outil de gestion de la configuration pour pousser un fichier avec le nom ```mdatp_managed.json``` à l’emplacement ```/etc/opt/microsoft/mdatp/managed/``` .

Le niveau supérieur du profil de configuration inclut les préférences et entrées à l’échelle du produit pour les sous-catégories du produit, qui sont expliquées plus en détail dans les sections suivantes.

### <a name="antivirus-engine-preferences"></a>Préférences du moteur antivirus

La *section antivirusEngine* du profil de configuration est utilisée pour gérer les préférences du composant antivirus du produit.

|||
|:---|:---|
| **Clé** | antivirusEngine |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

#### <a name="enable--disable-real-time-protection"></a>Activer/désactiver la protection en temps réel

Détermine si la protection en temps réel (analyser les fichiers à mesure qu’ils sont accessibles) est activée ou non.

|||
|:---|:---|
| **Clé** | enableRealTimeProtection |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | true (par défaut) <br/> false |

#### <a name="enable--disable-passive-mode"></a>Activer/désactiver le mode passif

Détermine si le moteur antivirus s’exécute en mode passif ou non. En mode passif :
- La protection en temps réel est désactivée.
- L’analyse à la demande est désactivée.
- La correction automatique des menaces est désactivée.
- Les mises à jour de l’intelligence de la sécurité sont allumées.
- L’icône du menu État est masquée.

|||
|:---|:---|
| **Clé** | passiveMode |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | false (par défaut) <br/> true |
| **Comments** | Disponible dans Defender pour Endpoint version 100.67.60 ou supérieure. |

#### <a name="exclusion-merge-policy"></a>Stratégie de fusion d’exclusion

Spécifie la stratégie de fusion pour les exclusions. Il peut s’agit d’une combinaison d’exclusions définies par l’administrateur et d’exclusions définies par l’utilisateur ( ) ou uniquement `merge` d’exclusions définies par l’administrateur ( `admin_only` ). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres exclusions.

|||
|:---|:---|
| **Clé** | exclusionsMergePolicy |
| **Type de données** | Chaîne |
| **Valeurs possibles** | merge (par défaut) <br/> admin_only |
| **Comments** | Disponible dans Defender pour Endpoint version 100.83.73 ou supérieure. |

#### <a name="scan-exclusions"></a>Analyser les exclusions

Entités exclues de l’analyse. Les exclusions peuvent être spécifiées par des chemins d’accès complets, des extensions ou des noms de fichiers.

|||
|:---|:---|
| **Clé** | exclusions |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

**Type d’exclusion**

Spécifie le type de contenu exclu de l’analyse.

|||
|:---|:---|
| **Clé** | $type |
| **Type de données** | Chaîne |
| **Valeurs possibles** | excludedPath <br/> excludedFileExtension <br/> excludedFileName |

**Chemin d’accès au contenu exclu**

Utilisé pour exclure le contenu de l’analyse par chemin d’accès complet au fichier.

|||
|:---|:---|
| **Clé** | chemin |
| **Type de données** | Chaîne |
| **Valeurs possibles** | chemins d’accès valides |
| **Comments** | Applicable uniquement si *$type* est *excluPath* |

**Type de chemin d’accès (fichier/répertoire)**

Indique si la propriété *du chemin d’accès* fait référence à un fichier ou un répertoire. 

|||
|:---|:---|
| **Clé** | isDirectory |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | false (par défaut) <br/> true |
| **Comments** | Applicable uniquement si *$type* est *excluPath* |

**Extension de fichier exclue de l’analyse**

Utilisé pour exclure le contenu de l’analyse par extension de fichier.

|||
|:---|:---|
| **Clé** | extension |
| **Type de données** | Chaîne |
| **Valeurs possibles** | extensions de fichier valides |
| **Comments** | Applicable uniquement si *$type* est *excluFileExtension* |

**Processus exclu de l’analyse**

Spécifie un processus pour lequel toute l’activité de fichier est exclue de l’analyse. Le processus peut être spécifié par son nom (par exemple) ou son chemin `cat` d’accès complet (par exemple, `/bin/cat` ).

|||
|:---|:---|
| **Clé** | nom |
| **Type de données** | Chaîne |
| **Valeurs possibles** | n’importe quelle chaîne |
| **Comments** | Applicable uniquement *si $type* est *excluFileName* |

#### <a name="allowed-threats"></a>Menaces autorisées

Liste des menaces (identifiées par leur nom) qui ne sont pas bloquées par le produit et sont autorisées à s’exécuter.

|||
|:---|:---|
| **Clé** | allowedThreats |
| **Type de données** | Tableau de chaînes |

#### <a name="disallowed-threat-actions"></a>Actions contre les menaces nonallées

Limite les actions que l’utilisateur local d’un appareil peut prendre lorsque des menaces sont détectées. Les actions incluses dans cette liste ne sont pas affichées dans l’interface utilisateur.

|||
|:---|:---|
| **Clé** | disallowedThreatActions |
| **Type de données** | Tableau de chaînes |
| **Valeurs possibles** | autoriser (empêche les utilisateurs d’autoriser les menaces) <br/> restaurer (empêche les utilisateurs de restaurer les menaces de la quarantaine) |
| **Comments** | Disponible dans Defender pour Endpoint version 100.83.73 ou supérieure. |

#### <a name="threat-type-settings"></a>Paramètres du type de menace

La *préférence threatTypeSettings dans* le moteur antivirus est utilisée pour contrôler la façon dont certains types de menaces sont gérés par le produit.

|||
|:---|:---|
| **Clé** | threatTypeSettings |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

**Type de menace**

Type de menace pour lequel le comportement est configuré.

|||
|:---|:---|
| **Clé** | clé |
| **Type de données** | Chaîne |
| **Valeurs possibles** | potentially_unwanted_application <br/> archive_bomb |

**Mesures à prendre**

Action à prendre en cas de menace du type spécifié dans la section précédente. Peut être :

- **Audit**: l’appareil n’est pas protégé contre ce type de menace, mais une entrée sur la menace est enregistrée.
- **Bloquer**: l’appareil est protégé contre ce type de menace et vous êtes averti dans la console de sécurité.
- **Off**: l’appareil n’est pas protégé contre ce type de menace et rien n’est enregistré.

|||
|:---|:---|
| **Clé** | valeur |
| **Type de données** | Chaîne |
| **Valeurs possibles** | audit (par défaut) <br/> block <br/> off |

#### <a name="threat-type-settings-merge-policy"></a>Stratégie de fusion des paramètres du type de menace

Spécifie la stratégie de fusion pour les paramètres de type de menace. Il peut s’agit d’une combinaison de paramètres définis par l’administrateur et de paramètres définis par l’utilisateur ( ) ou uniquement de `merge` paramètres définis par l’administrateur ( `admin_only` ). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres paramètres pour différents types de menaces.

|||
|:---|:---|
| **Clé** | threatTypeSettingsMergePolicy |
| **Type de données** | Chaîne |
| **Valeurs possibles** | merge (par défaut) <br/> admin_only |
| **Comments** | Disponible dans Defender pour Endpoint version 100.83.73 ou supérieure. |

#### <a name="antivirus-scan-history-retention-in-days"></a>Conservation de l’historique d’analyse antivirus (en jours)

Spécifiez le nombre de jours pendant combien de jours les résultats sont conservés dans l’historique d’analyse sur l’appareil. Les anciens résultats d’analyse sont supprimés de l’historique. Anciens fichiers mis en quarantaine qui sont également supprimés du disque.

|||
|:---|:---|
| **Clé** | scanResultsRetentionDays |
| **Type de données** | Chaîne |
| **Valeurs possibles** | 90 (valeur par défaut). Les valeurs autorisées sont de 1 jour à 180 jours. |
| **Comments** | Disponible dans Defender pour Endpoint version 101.04.76 ou supérieure. |

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Nombre maximal d’éléments dans l’historique d’analyse antivirus

Spécifiez le nombre maximal d’entrées à conserver dans l’historique d’analyse. Les entrées incluent toutes les analyses à la demande effectuées dans le passé et toutes les détections antivirus.

|||
|:---|:---|
| **Clé** | scanHistoryMaximumItems |
| **Type de données** | Chaîne |
| **Valeurs possibles** | 10000 (valeur par défaut). Les valeurs autorisées sont de 5 000 à 15 000 éléments. |
| **Comments** | Disponible dans Defender pour Endpoint version 101.04.76 ou supérieure. |

### <a name="cloud-delivered-protection-preferences"></a>Préférences de protection dans le cloud

*L’entrée cloudService* dans le profil de configuration est utilisée pour configurer la fonctionnalité de protection pilotée par le cloud du produit.

|||
|:---|:---|
| **Clé** | cloudService |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

#### <a name="enable--disable-cloud-delivered-protection"></a>Activer/désactiver la protection cloud

Détermine si la protection cloud est activée ou non sur l’appareil. Pour améliorer la sécurité de vos services, nous vous recommandons de maintenir cette fonctionnalité allumée.

|||
|:---|:---|
| **Clé** | activé |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | true (par défaut) <br/> false |

#### <a name="diagnostic-collection-level"></a>Niveau de collecte de diagnostics

Les données de diagnostic sont utilisées pour sécuriser et mettre à jour Defender for Endpoint, détecter, diagnostiquer et résoudre les problèmes, ainsi que pour améliorer les produits. Ce paramètre détermine le niveau de diagnostics envoyés par le produit à Microsoft.

|||
|:---|:---|
| **Clé** | diagnosticLevel |
| **Type de données** | Chaîne |
| **Valeurs possibles** | facultatif (par défaut) <br/> obligatoire |

#### <a name="enable--disable-automatic-sample-submissions"></a>Activer/désactiver les envois automatiques d’échantillons

Détermine si des échantillons suspects (susceptibles de contenir des menaces) sont envoyés à Microsoft. Il existe trois niveaux pour contrôler l’envoi d’échantillons :

- **Aucun**: aucun échantillon suspect n’est envoyé à Microsoft.
- **Sécurisé**: seuls les échantillons suspects qui ne contiennent pas d’informations d’identification personnelle (PII) sont envoyés automatiquement. Il s’agit de la valeur par défaut pour ce paramètre.
- **Tous**: tous les échantillons suspects sont envoyés à Microsoft.

|||
|:---|:---|
| **Clé** | automaticSampleSubmissionConsent |
| **Type de données** | Chaîne |
| **Valeurs possibles** | aucune <br/> safe (par défaut) <br/> all |

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Activer/désactiver les mises à jour automatiques de l’intelligence de sécurité

Détermine si les mises à jour d’informations de sécurité sont installées automatiquement :

|||
|:---|:---|
| **Clé** | automaticDefinitionUpdateEnabled |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | true (par défaut) <br/> false |

## <a name="recommended-configuration-profile"></a>Profil de configuration recommandé

Pour commencer, nous recommandons le profil de configuration suivant pour votre entreprise afin de tirer parti de toutes les fonctionnalités de protection que Defender pour Endpoint fournit.

Le profil de configuration suivant :

- Activer la protection en temps réel (RTP)
- Spécifiez la façon dont les types de menaces suivants sont gérés :
  - **Les applications potentiellement indésirables (PUA)** sont bloquées
  - **Les archives** archivées (fichier avec un taux de compression élevé) sont auditées dans les journaux du produit
- Activer les mises à jour automatiques des informations de sécurité
- Activer la protection cloud
- Activer l’envoi automatique d’échantillons au `safe` niveau

### <a name="sample-profile"></a>Exemple de profil

```JSON
{
   "antivirusEngine":{
      "enableRealTimeProtection":true,
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "automaticDefinitionUpdateEnabled":true,
      "automaticSampleSubmissionConsent":"safe",
      "enabled":true
   }
}
```

## <a name="full-configuration-profile-example"></a>Exemple de profil de configuration complète

Le profil de configuration suivant contient des entrées pour tous les paramètres décrits dans ce document et peut être utilisé pour des scénarios plus avancés où vous souhaitez contrôler davantage le produit.

### <a name="full-profile"></a>Profil complet

```JSON
{
   "antivirusEngine":{
      "enableRealTimeProtection":true,
      "passiveMode":false,
      "exclusionsMergePolicy":"merge",
      "exclusions":[
         {
            "$type":"excludedPath",
            "isDirectory":false,
            "path":"/var/log/system.log"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/home"
         },
         {
            "$type":"excludedFileExtension",
            "extension":"pdf"
         },
         {
            "$type":"excludedFileName",
            "name":"cat"
         }
      ],
      "allowedThreats":[
         "EICAR-Test-File (not a virus)"
      ],
      "disallowedThreatActions":[
         "allow",
         "restore"
      ],
      "threatTypeSettingsMergePolicy":"merge",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "enabled":true,
      "diagnosticLevel":"optional",
      "automaticSampleSubmissionConsent":"safe",
      "automaticDefinitionUpdateEnabled":true
   }
}
```

## <a name="configuration-profile-validation"></a>Validation du profil de configuration

Le profil de configuration doit être un fichier au format JSON valide. Il existe un certain nombre d’outils qui peuvent être utilisés pour vérifier cela. Par exemple, si vous avez `python` installé sur votre appareil :

```bash
python -m json.tool mdatp_managed.json
```

Si le JSON est bien formé, la commande ci-dessus le renvoie au Terminal et renvoie un code de sortie de `0` . Sinon, une erreur qui décrit le problème s’affiche et la commande renvoie un code de sortie de `1` .

## <a name="configuration-profile-deployment"></a>Déploiement de profil de configuration

Une fois que vous avez créé le profil de configuration pour votre entreprise, vous pouvez le déployer via l’outil de gestion que votre entreprise utilise. Defender pour le point de terminaison pour Linux lit la configuration gérée à partir du *fichier /etc/opt/microsoft/mdatp/managed/mdatp_managed.json.*
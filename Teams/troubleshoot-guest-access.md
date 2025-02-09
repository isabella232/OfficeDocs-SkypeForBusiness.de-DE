---
title: Behandeln von Problemen mit Gastzugriff in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: corbinm
search.appverid: MET150
description: Hier erhalten Sie Hilfe bei der Problembehandlung und dem Lösen von Problemen mit dem Gastzugriff in Microsoft Teams.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
appliesto:
- Microsoft Teams
ms.openlocfilehash: 5b539116fb5e81156a56c5f73146b92eea898765
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58600930"
---
# <a name="troubleshoot-problems-with-guest-access-in-microsoft-teams"></a>Behandeln von Problemen mit Gastzugriff in Microsoft Teams

- Wenn Sie wissen möchten, ob wir über Ihr Problem wissen, lesen Sie [Support Teams in Ihrer Organisation](/MicrosoftTeams/troubleshoot/teams-welcome).
- Wenn Sie nach Support für aktuelle Probleme mit dem Gastzugriff in Teams suchen möchten, wechseln Sie zu [Problembehandlung für Microsoft Teams](/MicrosoftTeams/troubleshoot/).
- Gäste sind Personen außerhalb Ihrer Organisation. Wenn sich eine Person in Ihrer Organisation befindet (beispielsweise ihre Mitarbeiter, Auftragnehmer oder Agenten vor Ort), können Sie nicht als Gäste hinzugefügt werden. Das gleiche gilt für Ihre Partner.
- Informationen zu geplanten neuen oder aktualisierten Funktionen für den Gastzugriff finden Sie in der [Microsoft Teams-Roadmap](https://aka.ms/teamsroadmap).
- Teilen Sie uns auf der [Microsoft Teams-UserVoice](https://aka.ms/TeamsUserVoice)-Website Ihre Wünsche mit.

[!INCLUDE [uservoice-disclaimer-note](includes/uservoice-disclaimer-note.md)]

## <a name="if-your-guests-are-seeing-license-errors"></a>Wenn Ihre Gäste Lizenzfehler sehen

Für den Gastzugriff in Microsoft Teams wird Azure Active Directory (Azure AD) Business-to-Business (B2B) und dessen Lizenzierungsmodell genutzt. Der Gastzugang ist in allen Abonnements von Microsoft 365 Business Standard, Office 365 Enterprise und Office 365 Education enthalten. Eine zusätzliche Microsoft 365- oder Office 365-Lizenz ist nicht erforderlich.

> [!NOTE]
> Teams für den Home-Mandanten eines Gasts aktiviert sein, damit sich Gäste anmelden und Teams als Gast bei einem anderen Mandanten (Ressourcen) verwenden können.

Wenn Lizenzierungsfehler angezeigt werden, lesen Sie unbedingt das Abrechnungsmodell für externe Azure AD-Identitäten, um die Lizenzierungsanforderungen zu ermitteln, die Ihre Anforderungen an Gastzugriff in Ihrer Organisation erfüllen. [](/azure/active-directory/external-identities/external-identities-pricing)

- Gastlizenzen werden für die einladende Organisation gezählt. Denken Sie daran, wenn Sie die Anzahl der benötigten Lizenzen berechnen.
- Lizenzen werden für Ihre Organisation gezählt, unabhängig davon, ob die eingeladenen Gäste aus einer Microsoft 365 Organisation stammen oder ihre persönlichen E-Mail-Adressen verwenden.

## <a name="support-for-b2b-user-types"></a>Unterstützung von B2B-Benutzertypen

Derzeit unterstützt Teams nur die Gastbenutzer vom Typ "Zustand 1" und "Zustand 2" [gemäß der Definition durch Azure B2B](/azure/active-directory/b2b/user-properties).

## <a name="related-topics"></a>Verwandte Themen

[Gastzugriff in Teams](guest-access.md)

[Teams-Problembehandlung](/MicrosoftTeams/troubleshoot/teams)
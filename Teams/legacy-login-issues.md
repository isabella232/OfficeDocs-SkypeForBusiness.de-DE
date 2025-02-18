---
title: Probleme beim Empfang von Nachrichten und Anrufen auf älteren Systemen in Teams
ms.reviewer: ''
author: cichur
ms.author: v-cichur
manager: serdars
ms.date: 05/29/2020
ms.topic: troubleshooting
ms.service: msteams
audience: admin
ms.collection:
- M365-collaboration
search.appverid: MET150
f1.keywords:
- NOCSH
description: Behandeln von Problemen im Zusammenhang mit dem Empfang von Nachrichten und Anrufen auf älteren Systemen
appliesto:
- Microsoft Teams
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 002354418c06980600f5cebef035b8480d0f1bef
ms.sourcegitcommit: 97c2faab08ec9b8fc9967827883308733ec162ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "58235000"
---
# <a name="issues-receiving-messages-and-calls-on-legacy-systems"></a>Probleme beim Empfang von Nachrichten und Anrufen auf älteren Systemen

Benutzer haben möglicherweise Probleme beim Empfang von Nachrichten oder Anrufen, wenn sie ältere Versionen von Teams oder sich mit anderen Anwendungen angemeldet haben.

## <a name="legacy-adu-setups"></a>Legacy-ADU-Setups

 Wenn Benutzer bei einem in eine Domäne eingebundenen Computer angemeldet sind und **Sie nicht möchten, dass ihre Benutzernamen im Anmeldebildschirm von Microsoft Teams vorab ausgefüllt werden**, können Administratoren die folgende Windows-Registrierung so einrichten, dass das Vorab-Ausfüllen des Benutzernamens (UPN) deaktiviert ist:

  Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\Teams<br/>
  SkipUpnPrefill(REG_DWORD)<br/>
  0x00000001 (1)

> [!NOTE]
> Das Überspringen oder Ignorieren des Vorab-Ausfüllens von Benutzernamen ist für Benutzernamen, die in „.local“ oder „.corp“ enden, standardmäßig aktiviert, daher müssen Sie keinen Registrierungsschlüssel festlegen, um diese zu deaktivieren.

Weitere [Informationen finden Sie unter Microsoft Teams moderne Authentifizierung](sign-in-teams.md) bei einem Konto anmelden.

## <a name="skype-token-revocation"></a>Skype Tokensperr

Beim Ändern/Zurücksetzen eines Kennworts empfangen ältere Clients bis zu einer Stunde lang keine Nachrichten und Anrufe. Um dieses Problem zu beheben, starten Sie die App neu, oder wechseln Sie zu neueren Clients.


## <a name="related-topics"></a>Verwandte Themen

[Teams-Problembehandlung](/MicrosoftTeams/troubleshoot/teams)
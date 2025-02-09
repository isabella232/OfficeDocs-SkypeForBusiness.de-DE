---
title: PowerShell-Skript zum Testen von Direct Routing Session Border Controller-Verbindungen
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: article
ms.reviewer: filippse
ms.service: msteams
audience: admin
description: Verwenden Sie dieses PowerShell-Skriptbeispiel zum Testen von Direct Routing Session Border Controller-Verbindungen in Microsoft Teams.
ms.localizationpriority: medium
search.appverid: MET150
ms.collection:
- M365-voice
f1.keywords:
- NOCSH
appliesto:
- Microsoft Teams
ms.openlocfilehash: 1258f85219e5ce6c00f8db5dac3a5233ce2c0717
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58627097"
---
# <a name="powershell-script-to-test-direct-routing-session-border-controller-connections"></a>PowerShell-Skript zum Testen von Direct Routing Session Border Controller-Verbindungen

Der SIP-Tester-Client ist ein PowerShell-Beispielskript, das Sie zum Testen von SBC-Verbindungen (Direct Routing Session Border Controller) in Microsoft Teams. Mit diesem Skript werden die Grundlegenden Funktionen eines SIP-Trunks (Session Initiation Protocol) mit Direct-Routing vom Kunden gekoppelt.

Das Skript übermittelt einen SIP-Test an den Testläufer, wartet auf das Ergebnis und stellt es dann in einem lesbaren Format vor. Mit diesem Skript können Sie die folgenden Szenarien testen:

- Ausgehende und eingehende Anrufe
- Gleichzeitiges Klingeln
- Medieneskalation
- Transfer mit Weisungsüberweisung

## <a name="download-the-script-and-documentation"></a>Herunterladen des Skripts und der Dokumentation

Laden Sie das [Clientskript und die Dokumentation für SIP-Tester herunter.](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/sip-tester-client/siptesterclient.zip?raw=true)

  > [!NOTE]
  > Sip Tester-Clientskript unterstützt nur adal.ps Version 3.19.8.1. Wenn eine neuere Version des adal.ps wird ein Fehler zurückgegeben.
  
  

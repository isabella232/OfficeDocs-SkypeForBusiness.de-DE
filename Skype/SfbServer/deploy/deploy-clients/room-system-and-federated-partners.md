---
title: Skype Raumsystem und Skype for Business Verbundpartner
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 1cc20323-ecba-4e87-a861-e54193e64cf0
description: In diesem Thema erfahren Sie, wie Sie Skype Raumsystem für Skype for Business Verbundpartner einrichten.
ms.openlocfilehash: 2f0a44538839fd6c722021f806bd8623f0c210ec
ms.sourcegitcommit: 556fffc96729150efcc04cd5d6069c402012421e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2021
ms.locfileid: "58620511"
---
# <a name="skype-room-system-and-skype-for-business-federated-partners"></a>Skype Raumsystem und Skype for Business Verbundpartner
 
In diesem Thema erfahren Sie, wie Sie Skype Raumsystem für Skype for Business Verbundpartner einrichten.
  
## <a name="skype-room-system-and-skype-for-business-federated-partners"></a>Skype Raumsystem und Skype for Business Verbundpartner

Skype Room System basiert auf dem Link "Skype for Business Besprechung teilnehmen" in der Kalenderbesprechungsanfrage. Der Verknüpfungslink befindet sich in der Regel im Textkörper einer Besprechungsanfrage. Skype Raumsystem hängt jedoch davon ab, ob dieser Link in den MAPI-Eigenschaften der Nachricht vorhanden ist. Wenn diese Besprechungsanfrage an Remoteorganisationen (Skype for Business Verbundpartner) gesendet wird, zeigt das Skype Raumsystem der Remoteorganisation standardmäßig nicht den Link zur Besprechungsteilnahme im Kalender an. Tatsächlich können alle Outlook Benutzer in der Remoteorganisation nicht mit einem Rechtsklick auf das Kalenderelement oder aus der Besprechungserinnerung an der Skype for Business Besprechung teilnehmen. Sie müssen die Besprechungseinladung öffnen und im Textkörper der Nachricht auf "An Skype for Business Besprechung teilnehmen" klicken. 
  
Der Grund für diese Einschränkung ist, dass Outlook und Microsoft Exchange keine spezielle Methode zum Verpacken von Informationen zum Senden von Nachrichten über das Internet verwenden. Diese Methode, die als Transport Neutral Encapsulation Format (TNEF) bezeichnet wird, ist standardmäßig für Nachrichten deaktiviert, die extern von einer Exchange Organisation gesendet werden. Damit ein Besprechungsbeitrittslink auf einem Remote-Skype Room System angezeigt wird, muss die sendende Organisation TNEF mithilfe des folgenden Befehls aktivieren:
  
```powershell
New-RemoteDomain -DomainName Contoso.com -Name Contoso
Set-RemoteDomain -Identity Contoso -TNEFEnabled $true
```

Nachdem TNEF für die Remoteorganisation aktiviert wurde, werden nachrichten, die über das Internet an die Organisation gesendet werden, als Anlage im TNEF-Format gesendet. Wenn TNEF aktiviert ist, kann Skype Room System, wenn eine Skype for Business Besprechungsanfrage an den Skype for Business Verbundpartner gesendet wird, die Teilnahme an Skype for Business Besprechung rendern, und Remotebenutzer können an Skype for Business Besprechungen teilnehmen. 

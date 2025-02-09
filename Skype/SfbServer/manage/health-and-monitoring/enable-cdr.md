---
title: Aktivieren der Aufzeichnung von Kommunikationsdatensätzen in Skype for Business Server
ms.reviewer: ''
ms.author: v-cichur
author: cichur
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 3b28e432-596f-45a5-a070-577d6fa748d9
description: 'Zusammenfassung: Erfahren Sie, wie Sie Kommunikationsdatensätze (KDS) in Skype for Business Server aktivieren.'
ms.openlocfilehash: 51c2dcd1f1ecf77647ded6dbbc41ea9cdc2c13d8
ms.sourcegitcommit: efd56988b22189dface73c156f6f8738f273fa61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2021
ms.locfileid: "60014559"
---
# <a name="enable-call-detail-recording-in-skype-for-business-server"></a>Aktivieren der Aufzeichnung von Kommunikationsdatensätzen in Skype for Business Server

**Zusammenfassung:** Erfahren Sie, wie Sie KDS-Datensätze (Call Detail Recording) in Skype for Business Server aktivieren.

Bei der Aufzeichnung von Kommunikationsdatensätzen werden Nutzungs- und Diagnoseinformationen über Peer-zu-Peer-Aktivitäten aufgezeichnet, z. B. Chat, VoIP-Anrufe (Voice over Internet Protocol), Anwendungsfreigabe, Dateiübertragung und Besprechungen. Anhand der Nutzungsdaten kann die Rendite berechnet werden, und die Diagnosedaten können zur Problembehandlung bei Peer-zu-Peer-Aktivitäten und Besprechungen eingesetzt werden.

Verwenden Sie das folgende Verfahren, um die Aufzeichnung von Kommunikationsdatensätzen (KDS) in der gesamten Organisation oder für jeden Standort in Ihrer Organisation zu aktivieren.

> [!NOTE]
> Zur Aktivierung von KDS müssen Sie die Überwachung und eine Überwachungsdatenbank konfigurieren. Ausführliche Informationen finden Sie unter [Deploying Monitoring](/previous-versions/office/lync-server-2013/lync-server-2013-deploying-monitoring).

### <a name="to-enable-cdr-with-skype-for-business-server-control-panel"></a>So aktivieren Sie KDS mit Skype for Business Server Systemsteuerung

1.  Melden Sie sich über ein Benutzerkonto, das Mitglied der Gruppe "RTCUniversalServerAdmins" ist (oder über gleichwertige Benutzerrechte verfügt) oder der Rolle "CsServerAdministrator" oder "CsAdministrator" zugewiesen ist, bei jedem Computer an, der sich im Netzwerk befindet, in dem Sie Skype for Business Server bereitgestellt haben.

2. Öffnen Sie ein Browserfenster, und geben Sie dann die Admin-URL ein, um die Skype for Business Server Systemsteuerung zu öffnen.

3. Klicken Sie in der linken Navigationsleiste auf **Überwachung und Archivierung** und dann auf **Aufzeichnung von Kommunikationsdatensätzen**.

4. Klicken Sie auf der Seite **Aufzeichnung von Kommunikationsdatensätzen** in der Tabelle auf den geeigneten Standort, klicken Sie auf **Aktion** und anschließend auf **KDS aktivieren**.

    > [!NOTE]
    > KDS ist standardmäßig aktiviert.

## <a name="enabling-cdr-by-using-windows-powershell-cmdlets"></a>Aktivieren von KDS mithilfe Windows PowerShell Cmdlets

Sie können KDS mithilfe von Windows PowerShell und dem Cmdlet **"Set-CsCdrConfiguration"** aktivieren. Sie können dieses Cmdlet entweder über die Skype for Business Server-Verwaltungsshell oder über eine Remotesitzung von Windows PowerShell ausführen. Ausführliche Informationen zur Verwendung von Remote-Windows PowerShell zum Herstellen einer Verbindung mit Skype for Business Server finden Sie unter [Microsoft Lync Remote PowerShell Administration.](https://blog.insideo365.com/2011/08/remote-lync-powershell-administration/) Der Vorgang ist in Skype for Business Server identisch.

### <a name="to-enable-cdr-for-a-single-location"></a>So aktivieren Sie KDS für einen einzelnen Standort

 Sie können KDS aktivieren, indem Sie den Parameter EnableCDR auf True ($True) setzen.

  ```PowerShell
  Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $True
  ```

### <a name="to-disable-cdr-for-a-single-location"></a>So deaktivieren Sie KDS für einen einzelnen Standort

 Sie können KDS deaktivieren, indem Sie den Parameter EnableCDR auf False ($False) setzen. Durch das Deaktivieren von KDS wird die Überwachung nicht deinstalliert. Die Erfassung und Speicherung von KDS-Daten wird angehalten.

  ```PowerShell
  Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False
  ```

### <a name="to-use-a-single-command-to-enable-cdr-in-multiple-locations"></a>So verwenden Sie einen einzelnen Befehl zum Aktivieren von KDS an mehreren Standorten

 Mit diesem Befehl wird KDS für alle derzeit in der Organisation verwendeten KDS-Einstellungen aktiviert.

  ```PowerShell
  Get-CsCdrConfiguration | Set-CsCdrConfiguration -EnableCDR $True
  ```

Weitere Informationen finden Sie im Hilfethema zum [Cmdlet "Set-CsCdrConfiguration".](/powershell/module/skype/set-cscdrconfiguration?view=skype-ps)

## <a name="see-also"></a>Weitere Informationen

[Planen der Überwachung](/previous-versions/office/lync-server-2013/lync-server-2013-planning-for-monitoring)

[Bereitstellen des Monitoring Servers](/previous-versions/office/lync-server-2013/lync-server-2013-deploying-monitoring)